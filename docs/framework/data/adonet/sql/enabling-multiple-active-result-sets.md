---
title: "Activation des ensembles de r&#233;sultats actifs multiples (MARS) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 576079e4-debe-4ab5-9204-fcbe2ca7a5e2
caps.latest.revision: 6
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 6
---
# Activation des ensembles de r&#233;sultats actifs multiples (MARS)
MARS est une fonction qui opère avec SQL Server pour permettre l'exécution de plusieurs lots sur une seule connexion.  Lorsque MARS est activé pour une utilisation avec SQL Server, chaque objet de commande utilisé ajoute une session à la connexion.  
  
> [!NOTE]
>  Une session MARS unique ouvre une connexion logique qu'utilisera la fonction MARS, puis une connexion logique pour chaque commande active.  
  
## Activation et désactivation de MARS dans la chaîne de connexion  
  
> [!NOTE]
>  Les chaînes de connexion suivantes utilisent l'exemple de base de données **AdventureWorks** inclus avec SQL Server.  Les chaînes de connexion fournies supposent que la base de données est installée sur un serveur nommé MSSQL1.  Si nécessaire, modifiez la chaîne de connexion en fonction de votre environnement.  
  
 La fonction MARS est désactivée par défaut.  Vous pouvez l'activer en ajoutant la paire de mots clés « MultipleActiveResultSets\=True » à votre chaîne de connexion. "  True » est la seule valeur valide pour l'activation de MARS.  L'exemple suivant montre comment se connecter à une instance de SQL Server et comment spécifier que MARS doit être activé.  
  
```vb  
Dim connectionString As String = "Data Source=MSSQL1;" & _  
    "Initial Catalog=AdventureWorks;Integrated Security=SSPI;" & _  
    "MultipleActiveResultSets=True"  
```  
  
```csharp  
string connectionString = "Data Source=MSSQL1;" +   
    "Initial Catalog=AdventureWorks;Integrated Security=SSPI;" +  
    "MultipleActiveResultSets=True";  
```  
  
 Vous pouvez désactiver MARS en ajoutant la paire de mots clés « MultipleActiveResultSets\=False » à votre chaîne de connexion. "  False » est la seule valeur valide pour la désactivation de MARS.  La chaîne de connexion suivante montre comment désactiver MARS.  
  
```vb  
Dim connectionString As String = "Data Source=MSSQL1;" & _  
    "Initial Catalog=AdventureWorks;Integrated Security=SSPI;" & _  
    "MultipleActiveResultSets=False"  
```  
  
```csharp  
string connectionString = "Data Source=MSSQL1;" +   
    "Initial Catalog=AdventureWorks;Integrated Security=SSPI;" +  
    "MultipleActiveResultSets=False";  
```  
  
## Considérations particulières en relation avec l'utilisation de MARS  
 En général, les applications existantes ne nécessitent aucune modification pour utiliser une connexion de type MARS.  Toutefois, si vous souhaitez utiliser des fonctions MARS dans vos applications, vous devez comprendre les considérations particulières suivantes.  
  
### Entrelacement d'instructions  
 Les opérations MARS s'exécutent de façon synchrone sur le serveur.  L'entrelacement des instructions SELECT et BULK INSERT est autorisé.  Toutefois, les instructions DML \(Data Manipulation Language\) et DDL \(Data Definition Language\) s'exécutent de manière atomique.  Toute instruction tentant de s'exécuter alors qu'un lot atomique est en cours d'exécution est bloquée.  L'exécution en parallèle au niveau du serveur n'est pas une fonction MARS.  
  
 Si deux lots sont soumis dans le cadre d'une connexion MARS, l'un deux contenant une instruction SELECT et l'autre contenant une instruction DML, l'exécution de l'instruction DML peut commencer à l'intérieur de l'instruction SELECT.  Toutefois, l'instruction DML doit être exécutée entièrement avant que l'instruction SELECT puisse progresser.  Si les deux instructions s'exécutent dans le cadre de la même transaction, toute modification opérée par une instruction DML après que l'exécution de l'instruction SELECT a commencé est invisible pour l'opération de lecture.  
  
 Une instruction WAITFOR à l'intérieur d'une instruction SELECT ne génère pas la transaction lorsqu'elle est en attente, c'est\-à\-dire, jusqu'à ce que la première ligne soit produite.  Cela implique qu'aucun autre lot ne peut s'exécuter dans le cadre de la même connexion tant qu'une instruction WAITFOR est en attente.  
  
### Cache de session MARS  
 Lors de l'ouverture d'une connexion alors que MARS est activé, une session logique est créée, qui ajoute une charge supplémentaire.  Afin de minimiser la charge et d'améliorer les performances, **SqlClient** met en cache la session MARS à l'intérieur d'une connexion.  Le cache contient au maximum 10 sessions MARS.  L'utilisateur ne peut pas modifier cette valeur.  Si la limite de session est atteinte, une nouvelle session est créée sans qu'aucune erreur ne soit générée.  Le cache et les sessions qu'il contient sont valables pour une connexion ; ils ne sont pas partagés entre plusieurs connexions.  En cas d'abandon d'une session, cette dernière retourne au pool, à moins que la limite supérieure du pool ne soit atteinte.  Si le pool de caches est plein, la session est fermée.  Les sessions MARS n'expirent pas.  Elles ne sont nettoyées qu'en cas de suppression de l'objet de connexion.  Le cache de session MARS n'est pas préchargé.  Il est chargé lorsque l'application demande des sessions supplémentaires.  
  
### Sécurité des threads  
 Les opérations MARS ne sont pas thread\-safe.  
  
### Regroupement de connexions  
 Les connexions de type MARS sont regroupées comme toute autre connexion.  Si une application ouvre deux connexions, l'une avec MARS activé et l'autre avec MARS désactivé, les deux connexions se trouvent dans des pools séparés.  Pour plus d'informations, consultez [Regroupement de connexions SQL Server \(ADO.NET\)](../../../../../docs/framework/data/adonet/sql-server-connection-pooling.md).  
  
### Environnement d'exécution par lots SQL Server  
 Lors de l'ouverture d'une connexion, un environnement par défaut est défini.  Cet environnement est ensuite copié dans une session MARS logique.  
  
 L'environnement d'exécution par lots inclut les composants suivants :  
  
-   Options définies \(par exemple, ANSI\_NULLS, DATE\_FORMAT, LANGUAGE, TEXTSIZE\)  
  
-   Contexte de sécurité \(rôle d'utilisateur\/d'application\)  
  
-   Contexte de base de données \(base de données actuelle\)  
  
-   Variables d'état d'exécution \(par exemple, @@ERROR, @@ROWCOUNT, @@FETCH\_STATUS @@IDENTITY\)  
  
-   Tables temporaires de niveau supérieur  
  
 Avec MARS, un environnement d'exécution par défaut est associé à une connexion.  Chaque nouveau lot qui commence à s'exécuter dans le cadre d'une connexion donnée reçoit une copie de l'environnement par défaut.  Chaque fois qu'un code est exécuté dans le cadre d'un lot donné, toutes les modifications apportées à l'environnement sont étendues au lot spécifique.  Quand une exécution se termine, les paramètres d'exécution sont copiés dans l'environnement par défaut.  Si un seul lot émet plusieurs commandes à exécuter de façon séquentielle dans le cadre de la même transaction, la sémantique est la même que celle exposée par les connexions impliquant des clients ou serveurs antérieurs.  
  
### Exécution en parallèle  
 MARS n'est pas conçu pour supprimer toutes les exigences de connexions multiples dans une application.  Si une application a besoin d'une véritable exécution en parallèle de commandes par rapport à un serveur, il convient d'utiliser plusieurs connexions.  
  
 Observez par exemple le scénario suivant.  Deux objets de commande sont créés, l'un pour le traitement d'un ensemble de résultats et un autre pour la mise à jour de données ; ils partagent une connexion commune via MARS.  Dans ce scénario, le `Transaction`.`Commit` échoue lors de la mise à jour jusqu'à ce que tous les résultats aient été lus sur le premier objet de commande, en générant l'exception suivante :  
  
 Message : contexte de transaction utilisé par une autre session.  
  
 Source : fournisseur de données .Net SqlClient  
  
 Attendu : \(null\)  
  
 Reçu : System.Data.SqlClient.SqlException  
  
 Il existe trois options pour gérer ce scénario :  
  
1.  Démarrez la transaction après la création du lecteur, de façon à ce qu'il ne fasse pas partie de la transaction.  Chaque mise à jour devient alors sa propre transaction.  
  
2.  Validez tout le travail une fois le lecteur fermé.  Cela permet l'exécution d'un lot substantiel de mises à jour.  
  
3.  N'utilisez pas MARS ; utilisez plutôt une connexion distincte pour chaque objet de commande comme vous l'auriez fait avant MARS.  
  
### Détection de la prise en charge de MARS  
 Une application peut contrôler la prise en charge de MARS en lisant la valeur `SqlConnection.ServerVersion`.  Le nombre majeur doit être de 9 pour SQL Server 2005 et 10 pour SQL Server 2008.  
  
## Voir aussi  
 [Ensembles de résultats actifs multiples \(MARS\)](../../../../../docs/framework/data/adonet/sql/multiple-active-result-sets-mars.md)   
 [Fournisseurs managés ADO.NET et Centre de développement de DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)