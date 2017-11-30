---
title: "Procédure pas à pas : utilisation de BatchBlock et de BatchedJoinBlock pour améliorer l'efficacité"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Task Parallel Library, dataflows
- TPL dataflow library, improving efficiency
ms.assetid: 5beb4983-80c2-4f60-8c51-a07f9fd94cb3
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: bc74b4acc5b29395c05e7c8302caefeb51718282
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="walkthrough-using-batchblock-and-batchedjoinblock-to-improve-efficiency"></a>Procédure pas à pas : utilisation de BatchBlock et de BatchedJoinBlock pour améliorer l'efficacité
La bibliothèque de flux de données TPL fournit le <xref:System.Threading.Tasks.Dataflow.BatchBlock%601?displayProperty=nameWithType> et <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602?displayProperty=nameWithType> classes afin que vous pouvez recevoir et mémoires tampons de données à partir d’une ou plusieurs sources et propager ces données en mémoire tampon comme une collection. Ce mécanisme de traitement par lot est utile lorsque vous collectez des données à partir d’une ou plusieurs sources et puis traitez plusieurs éléments de données en tant que lot. Par exemple, considérez une application qui utilise des flux de données pour insérer des enregistrements dans une base de données. Cette opération peut être plus efficace si plusieurs éléments sont insérés en même temps au lieu d’un à la fois séquentiellement. Ce document décrit comment utiliser la <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> classe afin d’améliorer l’efficacité de ces opérations d’insertion. Elle décrit également comment utiliser la <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> classe afin de capturer les résultats et toutes les exceptions qui se produisent lorsque le programme lit à partir d’une base de données.  
  
> [!TIP]
>  La bibliothèque de flux de données TPL (espace de noms <xref:System.Threading.Tasks.Dataflow?displayProperty=nameWithType>) n'est pas distribuée avec le [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]. Pour installer l'espace de noms <xref:System.Threading.Tasks.Dataflow>, ouvrez votre projet dans [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], dans le menu Projet choisissez **Gérer les packages NuGet**, puis recherchez en ligne le package `Microsoft.Tpl.Dataflow`.  
  
## <a name="prerequisites"></a>Conditions préalables  
  
1.  Lisez la section de blocs de jointure de la [flux de données](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md) avant de commencer cette procédure pas à pas de document.  
  
2.  Assurez-vous que vous disposez d’une copie de la base de données Northwind, Northwind.sdf, disponible sur votre ordinateur. Ce fichier se trouve généralement dans le dossier % programme Files%\Microsoft SQL Server Compact Edition\v3.5\Samples\\.  
  
    > [!IMPORTANT]
    >  Dans certaines versions de Windows, vous ne pouvez pas vous connecter à Northwind.sdf si [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] est en cours d’exécution en mode non-administrateur. Pour vous connecter à Northwind.sdf, démarrer [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] ou un [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] invite de commandes dans le **exécuter en tant qu’administrateur** mode.  
  
 Cette procédure pas à pas contient les sections suivantes :  
  
-   [Création d’une Application Console](#creating)  
  
-   [Définition de la classe de l’employé](#employeeClass)  
  
-   [Définir les opérations de base de données d’employé](#operations)  
  
-   [Ajout de données de l’employé à la base de données sans utiliser la mise en mémoire tampon](#nonBuffering)  
  
-   [L’utilisation de la mise en mémoire tampon pour ajouter des données sur les employés à la base de données](#buffering)  
  
-   [À l’aide de la jointure mis en mémoire tampon pour lire des données sur les employés à partir de la base de données](#bufferedJoin)  
  
-   [Exemple complet](#complete)  
  
<a name="creating"></a>   
## <a name="creating-the-console-application"></a>Création d’une Application Console  
  
<a name="consoleApp"></a>   
1.  Dans [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], créez un Visual c# ou Visual Basic **Application Console** projet. Dans ce document, le projet est nommé `DataflowBatchDatabase`.  
  
2.  Dans votre projet, ajoutez une référence à System.Data.SqlServerCe.dll et une référence à System.Threading.Tasks.Dataflow.dll.  
  
3.  Vérifiez que Form1.cs (Form1.vb pour [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) contient le code suivant `using` (`Imports` dans [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) les instructions.  
  
     [!code-csharp[TPLDataflow_BatchDatabase#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#1)]
     [!code-vb[TPLDataflow_BatchDatabase#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#1)]  
  
4.  Ajoutez les membres de données suivants à la classe `Program`.  
  
     [!code-csharp[TPLDataflow_BatchDatabase#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#2)]
     [!code-vb[TPLDataflow_BatchDatabase#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#2)]  
  
<a name="employeeClass"></a>   
## <a name="defining-the-employee-class"></a>Définition de la classe de l’employé  
 Ajouter à la `Program` classe la `Employee` classe.  
  
 [!code-csharp[TPLDataflow_BatchDatabase#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#3)]
 [!code-vb[TPLDataflow_BatchDatabase#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#3)]  
  
 Le `Employee` classe contient trois propriétés, `EmployeeID`, `LastName`, et `FirstName`. Ces propriétés correspondent à la `Employee ID`, `Last Name`, et `First Name` colonnes dans le `Employees` table dans la base de données Northwind. Pour cette démonstration, le `Employee` classe définit également la `Random` (méthode), ce qui crée un `Employee` objet ayant des valeurs aléatoires pour ses propriétés.  
  
<a name="operations"></a>   
## <a name="defining-employee-database-operations"></a>Définir les opérations de base de données d’employé  
 Ajouter à la `Program` classe le `InsertEmployees`, `GetEmployeeCount`, et `GetEmployeeID` méthodes.  
  
 [!code-csharp[TPLDataflow_BatchDatabase#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#4)]
 [!code-vb[TPLDataflow_BatchDatabase#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#4)]  
  
 Le `InsertEmployees` méthode ajoute de nouveaux enregistrements d’employés à la base de données. Le `GetEmployeeCount` méthode récupère le nombre d’entrées dans le `Employees` table. Le `GetEmployeeID` méthode extrait l’identificateur du premier employé qui a le nom fourni. Chacune de ces méthodes prend une chaîne de connexion à la base de données Northwind et utilise des fonctionnalités dans le `System.Data.SqlServerCe` espace de noms pour communiquer avec la base de données.  
  
<a name="nonBuffering"></a>   
## <a name="adding-employee-data-to-the-database-without-using-buffering"></a>Ajout de données de l’employé à la base de données sans utiliser la mise en mémoire tampon  
 Ajouter à la `Program` classe le `AddEmployees` et `PostRandomEmployees` méthodes.  
  
 [!code-csharp[TPLDataflow_BatchDatabase#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#5)]
 [!code-vb[TPLDataflow_BatchDatabase#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#5)]  
  
 Le `AddEmployees` méthode ajoute des données d’employé aléatoires à la base de données à l’aide de flux de données. Il crée un <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> objet qui appelle la `InsertEmployees` méthode pour ajouter une entrée de l’employé dans la base de données. Le `AddEmployees` méthode appelle ensuite la `PostRandomEmployees` méthode à valider plusieurs `Employee` des objets sur le <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> objet. Le `AddEmployees` méthode puis attend que toutes les opérations à la fin d’insertion.  
  
<a name="buffering"></a>   
## <a name="using-buffering-to-add-employee-data-to-the-database"></a>L’utilisation de la mise en mémoire tampon pour ajouter des données sur les employés à la base de données  
 Ajouter à la `Program` classe le `AddEmployeesBatched` (méthode).  
  
 [!code-csharp[TPLDataflow_BatchDatabase#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#6)]
 [!code-vb[TPLDataflow_BatchDatabase#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#6)]  
  
 Cette méthode s’apparente à `AddEmployees`, sauf qu’elle utilise également le <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> classe dans la mémoire tampon plusieurs `Employee` objets avant d’envoyer ces objets vers le <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> objet. Étant donné que la <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> classe propage plusieurs éléments sous forme de collection, le <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> objet est modifié pour agir sur un tableau de `Employee` objets. Comme dans le `AddEmployees` (méthode), `AddEmployeesBatched` appelle la `PostRandomEmployees` méthode à valider plusieurs `Employee` objets ; Toutefois, `AddEmployeesBatched` publie ces objets à le <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> objet. Le `AddEmployeesBatched` méthode attend également pour toutes les opérations à la fin d’insertion.  
  
<a name="bufferedJoin"></a>   
## <a name="using-buffered-join-to-read-employee-data-from-the-database"></a>À l’aide de la jointure mis en mémoire tampon pour lire des données sur les employés à partir de la base de données  
 Ajouter à la `Program` classe le `GetRandomEmployees` (méthode).  
  
 [!code-csharp[TPLDataflow_BatchDatabase#7](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#7)]
 [!code-vb[TPLDataflow_BatchDatabase#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#7)]  
  
 Cette méthode imprime les informations sur les employés aléatoires dans la console. Il crée plusieurs aléatoire `Employee` objets et appelle le `GetEmployeeID` méthode pour récupérer l’identificateur unique pour chaque objet. Étant donné que la `GetEmployeeID` méthode lève une exception s’il n’existe aucune correspondance employé avec les noms de la première et dernières donnés, le `GetRandomEmployees` utilise le <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> classe pour stocker `Employee` objets pour un appel réussi à `GetEmployeeID` et <xref:System.Exception?displayProperty=nameWithType> objets pour les appels qui échouent. Le <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> objet dans cet exemple agit sur une <xref:System.Tuple%602> objet qui contient une liste de `Employee` objets et une liste de <xref:System.Exception> objets. Le <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> objet propage ces données lors de la somme de la réponse reçue `Employee` et <xref:System.Exception> nombre d’objets est égal à la taille de lot.  
  
<a name="complete"></a>   
## <a name="the-complete-example"></a>Exemple complet  
 L'exemple suivant montre le code complet. Le `Main` méthode compare le temps nécessaire pour effectuer des insertions de base de données par lot par rapport à la fois pour effectuer des insertions de la base de données non-batch. Il montre également l’utilisation d’une jointure mis en mémoire tampon pour lire des données sur les employés à partir de la base de données et également signaler des erreurs.  
  
 [!code-csharp[TPLDataflow_BatchDatabase#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#100)]
 [!code-vb[TPLDataflow_BatchDatabase#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#100)]  
  
## <a name="see-also"></a>Voir aussi  
 [Le flux de données](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
