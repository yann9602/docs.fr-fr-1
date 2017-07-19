---
title: "Walkthrough: Using BatchBlock and BatchedJoinBlock to Improve Efficiency | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Task Parallel Library, dataflows"
  - "TPL dataflow library, improving efficiency"
ms.assetid: 5beb4983-80c2-4f60-8c51-a07f9fd94cb3
caps.latest.revision: 8
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 8
---
# Walkthrough: Using BatchBlock and BatchedJoinBlock to Improve Efficiency
La bibliothèque de flux de données TPL fournit les classes <xref:System.Threading.Tasks.Dataflow.BatchBlock%601?displayProperty=fullName> et <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602?displayProperty=fullName> afin de pouvoir recevoir et mettre en mémoire tampon des données d'une ou de plusieurs sources puis de propager ces données mise en mémoire tampon en une seule collection.  Ce mécanisme de traitement par lot est utile lorsque vous collectez des données d'une ou de plusieurs sources puis traitez plusieurs éléments de données en lot.  Par exemple, prenez une application qui utilise le flux de données pour insérer des enregistrements dans une base de données.  Cette opération peut être plus efficace si plusieurs éléments sont insérés simultanément au lieu de un à un séquentiellement.  Ce document décrit comment utiliser la classe <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> afin d'améliorer l'efficacité de telles opérations d'insertion dans une base de données.  Il décrit également comment utiliser la classe <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> afin d'enregistrer les résultats et toute exception qui se produit lorsque le programme lit une base de données.  
  
> [!TIP]
>  La bibliothèque de flux de données de TPL \(espace de noms<xref:System.Threading.Tasks.Dataflow?displayProperty=fullName> \) n'est pas distribuée avec [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].  Pour installer l'espace de noms <xref:System.Threading.Tasks.Dataflow>, ouvrez votre projet dans [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], choisissez **Gérer les packages NuGet** dans le menu Projet, puis recherchez en ligne le package `Microsoft.Tpl.Dataflow`.  
  
## Composants requis  
  
1.  Lisez la section Joindre des Blocs dans le document [Flux de données](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md) avant de démarrer ce tutoriel.  
  
2.  Vérifiez que vous avez une copie de la base de données Northwind, Northwind.sdf, disponible sur votre ordinateur.  Ce fichier se trouve généralement dans le dossier %Program Files%\\Microsoft SQL Server Compact Edition\\v3.5\\samples \\.  
  
    > [!IMPORTANT]
    >  Dans certaines versions de Windows, vous ne pouvez pas vous connecter à Northwind.sdf si [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] ne s'exécute pas en mode administrateur.  Pour se connecter à Northwind.sdf, démarrez [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] ou une invite de commandes [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] en mode **Exécuter en tant qu’administrateur**.  
  
 Cette procédure pas\-à\-pas contient les sections suivantes :  
  
-   [Création de l'application console](#creating)  
  
-   [Définition de la classe employé](#employeeClass)  
  
-   [Définition des Opérations sur la base de données des employés](#operations)  
  
-   [Ajouter des Données Employé à la bases de données sans utiliser de mise en mémoire tampon](#nonBuffering)  
  
-   [Utiliser la mise en mémoire tampon pour ajouter des données des employés à la base de données](#buffering)  
  
-   [Utilisation de la jointure mise en mémoire tampon pour lire les données des employés de la base de données](#bufferedJoin)  
  
-   [Exemple complet](#complete)  
  
<a name="creating"></a>   
## Création de l'application console  
  
<a name="consoleApp"></a>   
1.  Créez un projet d'**Application Console** Visual Basic ou Visual C\# dans [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].  Dans ce document, le projet est nommé `DataflowBatchDatabase`.  
  
2.  Dans votre projet, ajoutez une référence à System.Data.SqlServerCe.dll et une référence à System.Threading.Tasks.Dataflow.dll.  
  
3.  Vérifiez que Form1.cs \(Form1.vb pour [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]\) contient `using` \(`Imports` dans les instructions [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]\).  
  
     [!code-csharp[TPLDataflow_BatchDatabase#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#1)]
     [!code-vb[TPLDataflow_BatchDatabase#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#1)]  
  
4.  Ajoutez les membres de données suivants à la classe `Program` :  
  
     [!code-csharp[TPLDataflow_BatchDatabase#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#2)]
     [!code-vb[TPLDataflow_BatchDatabase#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#2)]  
  
<a name="employeeClass"></a>   
## Définition de la classe employé  
 Ajoutez la classe `Employee` à la classe `Program`.  
  
 [!code-csharp[TPLDataflow_BatchDatabase#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#3)]
 [!code-vb[TPLDataflow_BatchDatabase#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#3)]  
  
 La classe `Employee` contient trois propriétés nommées `EmployeeID`, `LastName` et `FirstName`.  Ces propriétés correspondent aux colonnes `Employee ID`, `Last Name`, et `First Name` du tableau `Employees` dans la base de données Northwind.  Pour cette démonstration, la classe `Employee` définit également la méthode `Random`, qui crée un objet `Employee` avec des valeurs aléatoires pour ses propriétés.  
  
<a name="operations"></a>   
## Définition des Opérations sur la base de données des employés  
 Ajoutez les méthodes `InsertEmployees`, `GetEmployeeCount` et `GetEmployeeID` à la classe `Program`.  
  
 [!code-csharp[TPLDataflow_BatchDatabase#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#4)]
 [!code-vb[TPLDataflow_BatchDatabase#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#4)]  
  
 La méthode `InsertEmployees` ajoute de nouvelles informations sur les employés à la base de données.  La méthode `GetEmployeeCount` extrait le nombre d'entrées du tableau `Employees`.  La méthode `GetEmployeeID` extrait l'identificateur du premier employé qui a le nom fourni.  Chacune de ces méthodes a une chaîne de connexion vers la base de données Northwind et utilise cette fonctionnalité dans l'espace de noms `System.Data.SqlServerCe` pour communiquer avec la base de données.  
  
<a name="nonBuffering"></a>   
## Ajouter des Données Employé à la bases de données sans utiliser de mise en mémoire tampon  
 Ajoutez les méthodes `AddEmployees` et `PostRandomEmployees` à la classe `Program`.  
  
 [!code-csharp[TPLDataflow_BatchDatabase#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#5)]
 [!code-vb[TPLDataflow_BatchDatabase#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#5)]  
  
 La méthode `AddEmployees` ajoute des données d'employés aléatoires à la base de données en utilisant un flux de données.  Elle crée un objet <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> qui appelle la méthode `InsertEmployees` pour ajouter une entrée employé à la base de données.  La méthode `AddEmployees` appelle ensuite la méthode `PostRandomEmployees` pour publier plusieurs objets `Employee` à l'objet <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>.  La méthode `AddEmployees` attend ensuite que toutes les opérations d'insertion se terminent.  
  
<a name="buffering"></a>   
## Utiliser la mise en mémoire tampon pour ajouter des données des employés à la base de données  
 Ajoutez la méthode `AddEmployeesBatched` à la classe `Program`.  
  
 [!code-csharp[TPLDataflow_BatchDatabase#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#6)]
 [!code-vb[TPLDataflow_BatchDatabase#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#6)]  
  
 Cette méthode est semblable à `AddEmployees`, excepté qu'elle utilise également la classe <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> pour mettre plusieurs objets `Employee` en mémoire tampon avant d'envoyer ces objets à l'objet <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>.  La classe <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> propage plusieurs éléments en collection, et donc l'objet <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> est modifié pour agir sur un tableau d'objets `Employee`.  Comme dans la méthode `AddEmployees`, `AddEmployeesBatched` appelle la méthode `PostRandomEmployees` pour publier plusieurs objets `Employee` ; toutefois, `AddEmployeesBatched` publie ces objets à l'objet <xref:System.Threading.Tasks.Dataflow.BatchBlock%601>.  La méthode `AddEmployeesBatched`  attend aussi que toutes les opérations d'insertion se terminent.  
  
<a name="bufferedJoin"></a>   
## Utilisation de la jointure mise en mémoire tampon pour lire les données des employés de la base de données  
 Ajoutez la méthode `GetRandomEmployees` à la classe `Program`.  
  
 [!code-csharp[TPLDataflow_BatchDatabase#7](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#7)]
 [!code-vb[TPLDataflow_BatchDatabase#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#7)]  
  
 Cette méthode affiche des informations sur les employés aléatoires dans la console.  Elle crée plusieurs objets `Employee` aléatoires et appelle la méthode `GetEmployeeID` pour récupérer l'identificateur unique pour chaque objet.  Puisque la méthode `GetEmployeeID` lève une exception si aucun employé ne correspond aux prénoms et nom de famille donnés, la méthode `GetRandomEmployees` utilise la classe <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> afin de stocker des objets `Employee` pour les appels réussis à `GetEmployeeID` et des objets <xref:System.Exception?displayProperty=fullName> pour les appels qui échouent.  L'objet <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> de cet exemple agit sur un objet <xref:System.Tuple%602> qui gère une liste d'objets `Employee` et une liste d'objets <xref:System.Exception>.  L'objet <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> propage ces données lorsque la somme d' `Employee` et des nombres reçus d'objet <xref:System.Exception> est égale à la taille du lot.  
  
<a name="complete"></a>   
## Exemple complet  
 L'exemple suivant montre le code complet.  La méthode `Main` compare le temps requis pour effectuer des insertions par lots dans la base de données et le temps requis pour effectuer des insertions non par lots dans la base de données.  Elle montre également l'utilisation de la jointure mise en mémoire tampon pour lire des données d'employés depuis la base de données et pour enregistrer également des erreurs.  
  
 [!code-csharp[TPLDataflow_BatchDatabase#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#100)]
 [!code-vb[TPLDataflow_BatchDatabase#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#100)]  
  
## Voir aussi  
 [Flux de données](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)