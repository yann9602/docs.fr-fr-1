---
title: LINQ to SQL, exemple
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5f39db9e-0e62-42c9-8c98-bb8b54cec98c
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6c05520dccdbf0677569d7fc64f55795e0ddb79b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="linq-to-sql-sample"></a><span data-ttu-id="7fdcb-102">LINQ to SQL, exemple</span><span class="sxs-lookup"><span data-stu-id="7fdcb-102">LINQ to SQL Sample</span></span>
<span data-ttu-id="7fdcb-103">Cet exemple montre comment créer une activité pour utiliser des entités de requêtes LINQ to SQL de tables dans des bases de données SQL Server.</span><span class="sxs-lookup"><span data-stu-id="7fdcb-103">This sample demonstrates how to create an activity to use LINQ to SQL query entities from tables in SQL Server databases.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="7fdcb-104">Les exemples [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="7fdcb-104">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] samples may already be installed on your machine.</span></span> <span data-ttu-id="7fdcb-105">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="7fdcb-105">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\Samples\WCFWFCardspace`  
>   
>  <span data-ttu-id="7fdcb-106">Si ce répertoire n'existe pas, cliquez sur le lien de téléchargement de l'exemple situé en haut de cette page.</span><span class="sxs-lookup"><span data-stu-id="7fdcb-106">If this directory does not exist, click the download sample link at the top of this page.</span></span> <span data-ttu-id="7fdcb-107">Notez que ce lien télécharge et installe tous les exemples [!INCLUDE[wf1](../../../../includes/wf1-md.md)], [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] et [!INCLUDE[infocard](../../../../includes/infocard-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7fdcb-107">Note that this link downloads and installs all of the [!INCLUDE[wf1](../../../../includes/wf1-md.md)], [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], and [!INCLUDE[infocard](../../../../includes/infocard-md.md)] samples.</span></span> <span data-ttu-id="7fdcb-108">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="7fdcb-108">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\Samples\WCFWFCardSpace\WF\Scenario\ActivityLibrary\Linq\LinqToSql`  
  
## <a name="activity-details-for-findinsqltable"></a><span data-ttu-id="7fdcb-109">Détails de l'activité pour FindInSqlTable</span><span class="sxs-lookup"><span data-stu-id="7fdcb-109">Activity details for FindInSqlTable</span></span>  
 <span data-ttu-id="7fdcb-110">Cette activité permet aux utilisateurs d'interroger des entités de tables dans une base de données à l'aide de LINQ to SQL.</span><span class="sxs-lookup"><span data-stu-id="7fdcb-110">This activity allows users to query entities from tables in a database using LINQ to SQL.</span></span> <span data-ttu-id="7fdcb-111">Les utilisateurs de l'activité peuvent également fournir un prédicat LINQ sous la forme d'une expression lambda pour filtrer les résultats.</span><span class="sxs-lookup"><span data-stu-id="7fdcb-111">Users of the activity can also provide a LINQ predicate in the form of a lambda expression to filter the results.</span></span> <span data-ttu-id="7fdcb-112">Si aucun prédicat n'est fourni, la totalité de la table est retournée.</span><span class="sxs-lookup"><span data-stu-id="7fdcb-112">If no predicate is provided, the entire table is returned.</span></span> <span data-ttu-id="7fdcb-113">Le tableau suivant décrit en détail les propriétés et valeurs de retour pour l'activité.</span><span class="sxs-lookup"><span data-stu-id="7fdcb-113">The following table details the property and return values for the activity.</span></span>  
  
|<span data-ttu-id="7fdcb-114">Propriété ou valeur de retour</span><span class="sxs-lookup"><span data-stu-id="7fdcb-114">Property or Return Value</span></span>|<span data-ttu-id="7fdcb-115">Description</span><span class="sxs-lookup"><span data-stu-id="7fdcb-115">Description</span></span>|  
|------------------------------|-----------------|  
|<span data-ttu-id="7fdcb-116">Propriété `Collection`</span><span class="sxs-lookup"><span data-stu-id="7fdcb-116">`Collection` property</span></span>|<span data-ttu-id="7fdcb-117">Propriété requise qui spécifie la collection source.</span><span class="sxs-lookup"><span data-stu-id="7fdcb-117">A required property that specifies the source collection.</span></span>|  
|<span data-ttu-id="7fdcb-118">Propriété `Predicate`</span><span class="sxs-lookup"><span data-stu-id="7fdcb-118">`Predicate` property</span></span>|<span data-ttu-id="7fdcb-119">Propriété requise qui spécifie le filtre pour la collection sous la forme d'une expression lambda.</span><span class="sxs-lookup"><span data-stu-id="7fdcb-119">A required property that specifies the filter for the collection in the form of a lambda expression.</span></span>|  
|<span data-ttu-id="7fdcb-120">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="7fdcb-120">Return Value</span></span>|<span data-ttu-id="7fdcb-121">Collection filtrée.</span><span class="sxs-lookup"><span data-stu-id="7fdcb-121">The filtered collection.</span></span>|  
  
## <a name="code-sample-that-uses-the-custom-activity"></a><span data-ttu-id="7fdcb-122">Exemple de code qui utilise l'activité personnalisée</span><span class="sxs-lookup"><span data-stu-id="7fdcb-122">Code Sample that uses the Custom Activity</span></span>  
 <span data-ttu-id="7fdcb-123">L'exemple de code suivant utilise l'activité personnalisée `FindInSqlTable` pour rechercher toutes les lignes d'une table SQL Server nommée `Employee` où la colonne `Role` est égale à `SDE`.</span><span class="sxs-lookup"><span data-stu-id="7fdcb-123">The following code example uses the `FindInSqlTable` custom activity to find all rows in a SQL Server table named `Employee` where the `Role` column is equal to `SDE`.</span></span>  
  
```csharp  
new FindInSqlTable<Employee>   
{  
    ConnectionString = @"Data Source=.\SQLExpress;Initial Catalog=LinqToSqlSample;Integrated Security=True",                          
    Predicate = new LambdaValue<Func<Employee, bool>>(c => new Func<Employee, bool>(emp => emp.Role.Equals("SDE"))),  
    Result = new OutArgument<IList<Employee>>(employees)  
},  
```  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="7fdcb-124">Pour utiliser cet exemple</span><span class="sxs-lookup"><span data-stu-id="7fdcb-124">To use this sample</span></span>  
  
1.  <span data-ttu-id="7fdcb-125">Ouvrez une invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="7fdcb-125">Open a command prompt.</span></span>  
  
2.  <span data-ttu-id="7fdcb-126">Accédez au dossier qui contient cet exemple.</span><span class="sxs-lookup"><span data-stu-id="7fdcb-126">Navigate to the folder that contains this sample.</span></span>  
  
3.  <span data-ttu-id="7fdcb-127">Exécutez le fichier de commandes Setup.cmd.</span><span class="sxs-lookup"><span data-stu-id="7fdcb-127">Run the Setup.cmd command file.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="7fdcb-128">Le script Setup.cmd tente d'installer l'exemple de base de données sur votre ordinateur local SQL Server Express.</span><span class="sxs-lookup"><span data-stu-id="7fdcb-128">The Setup.cmd script attempts to install the sample database in your local machine SQL Server Express.</span></span> <span data-ttu-id="7fdcb-129">Si vous voulez l'installer dans une autre instance SQL Server, modifiez Setup.cmd.</span><span class="sxs-lookup"><span data-stu-id="7fdcb-129">If you want to install it in other SQL server instance, edit Setup.cmd.</span></span>  
  
     <span data-ttu-id="7fdcb-130">Le script Setup.cmd effectue les actions suivantes :</span><span class="sxs-lookup"><span data-stu-id="7fdcb-130">The Setup.cmd script does the following actions.:</span></span>  
  
    -   <span data-ttu-id="7fdcb-131">Crée une base de données appelée LinqToSqlSample.</span><span class="sxs-lookup"><span data-stu-id="7fdcb-131">Creates a database called LinqToSqlSample.</span></span>  
  
    -   <span data-ttu-id="7fdcb-132">Crée une table Roles.</span><span class="sxs-lookup"><span data-stu-id="7fdcb-132">Creates a Roles table.</span></span>  
  
    -   <span data-ttu-id="7fdcb-133">Crée une table Employees.</span><span class="sxs-lookup"><span data-stu-id="7fdcb-133">Creates an Employees table.</span></span>  
  
    -   <span data-ttu-id="7fdcb-134">Insère 3 enregistrements dans la table Roles.</span><span class="sxs-lookup"><span data-stu-id="7fdcb-134">Inserts 3 records into the Roles table.</span></span>  
  
    -   <span data-ttu-id="7fdcb-135">Insère 12 enregistrements dans la table Employees.</span><span class="sxs-lookup"><span data-stu-id="7fdcb-135">Inserts 12 records into the Employees table.</span></span>  
  
4.  <span data-ttu-id="7fdcb-136">À l'aide de [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], ouvrez le fichier solution LinqToSQL.sln.</span><span class="sxs-lookup"><span data-stu-id="7fdcb-136">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the LinqToSQL.sln solution file.</span></span>  
  
5.  <span data-ttu-id="7fdcb-137">Pour générer la solution, appuyez sur Ctrl+Maj+B.</span><span class="sxs-lookup"><span data-stu-id="7fdcb-137">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
6.  <span data-ttu-id="7fdcb-138">Pour exécuter la solution, appuyez sur F5.</span><span class="sxs-lookup"><span data-stu-id="7fdcb-138">To run the solution, press F5.</span></span>  
  
#### <a name="to-uninstall-the-linqtosql-sample-database"></a><span data-ttu-id="7fdcb-139">Pour désinstaller l'exemple de base de données LinqToSql</span><span class="sxs-lookup"><span data-stu-id="7fdcb-139">To uninstall the LinqToSql sample database</span></span>  
  
1.  <span data-ttu-id="7fdcb-140">Ouvrez une invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="7fdcb-140">Open a command prompt.</span></span>  
  
2.  <span data-ttu-id="7fdcb-141">Accédez au dossier qui contient cet exemple.</span><span class="sxs-lookup"><span data-stu-id="7fdcb-141">Navigate to the folder that contains this sample.</span></span>  
  
3.  <span data-ttu-id="7fdcb-142">Exécutez le fichier de commandes Cleanup.cmd.</span><span class="sxs-lookup"><span data-stu-id="7fdcb-142">Run the Cleanup.cmd command file.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="7fdcb-143">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="7fdcb-143">The samples may already be installed on your machine.</span></span> <span data-ttu-id="7fdcb-144">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="7fdcb-144">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="7fdcb-145">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="7fdcb-145">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7fdcb-146">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="7fdcb-146">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\Liiinq\LinqToSql`  
  
## <a name="see-also"></a><span data-ttu-id="7fdcb-147">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7fdcb-147">See Also</span></span>  
 [<span data-ttu-id="7fdcb-148">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="7fdcb-148">LINQ to SQL</span></span>](http://go.microsoft.com/fwlink/?LinkId=150376)  
 [<span data-ttu-id="7fdcb-149">Mise en route (LINQ to SQL)</span><span class="sxs-lookup"><span data-stu-id="7fdcb-149">Getting Started (LINQ to SQL)</span></span>](http://go.microsoft.com/fwlink/?LinkId=150377)
