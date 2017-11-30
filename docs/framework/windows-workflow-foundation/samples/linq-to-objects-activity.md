---
title: "Activité LINQ to Objects"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 403c82e8-7f2b-42f6-93cd-95c35bc76ead
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9f34189c8f9911b09017056b22611d27df25c10e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="linq-to-objects-activity"></a><span data-ttu-id="69002-102">Activité LINQ to Objects</span><span class="sxs-lookup"><span data-stu-id="69002-102">LINQ to Objects Activity</span></span>
<span data-ttu-id="69002-103">Cet exemple montre comment créer une activité pour utiliser LINQ to Objects pour interroger des éléments d’une collection.</span><span class="sxs-lookup"><span data-stu-id="69002-103">This sample demonstrates how to create an activity to use LINQ to Objects to query elements in a collection.</span></span>  
  
## <a name="activity-details-for-findincollection"></a><span data-ttu-id="69002-104">Détails de l'activité pour FindInCollection</span><span class="sxs-lookup"><span data-stu-id="69002-104">Activity Details for FindInCollection</span></span>  
 <span data-ttu-id="69002-105">Cette activité permet aux utilisateurs d'interroger des éléments de collections en mémoire à l'aide de LINQ to Objects.</span><span class="sxs-lookup"><span data-stu-id="69002-105">This activity allows users to query elements from collections in memory using LINQ to Objects.</span></span> <span data-ttu-id="69002-106">Vous devez fournir un prédicat LINQ sous la forme d'une expression lambda pour filtrer les résultats.</span><span class="sxs-lookup"><span data-stu-id="69002-106">You must provide a LINQ predicate in the form of a lambda expression to filter the results.</span></span> <span data-ttu-id="69002-107">Cette activité peut être utilisée conjointement avec des activités <xref:System.Activities.Statements.AddToCollection%601>.</span><span class="sxs-lookup"><span data-stu-id="69002-107">This activity can be used in conjunction with <xref:System.Activities.Statements.AddToCollection%601> activities.</span></span>  
  
 <span data-ttu-id="69002-108">Le tableau suivant décrit en détail les propriétés et valeurs de retour pour l'activité.</span><span class="sxs-lookup"><span data-stu-id="69002-108">The following table details the property and return values for the activity.</span></span>  
  
|<span data-ttu-id="69002-109">Propriété ou valeur de retour</span><span class="sxs-lookup"><span data-stu-id="69002-109">Property or Return Value</span></span>|<span data-ttu-id="69002-110">Description</span><span class="sxs-lookup"><span data-stu-id="69002-110">Description</span></span>|  
|------------------------------|-----------------|  
|<span data-ttu-id="69002-111">Propriété `Collection`</span><span class="sxs-lookup"><span data-stu-id="69002-111">`Collection` property</span></span>|<span data-ttu-id="69002-112">Propriété requise qui spécifie la collection source.</span><span class="sxs-lookup"><span data-stu-id="69002-112">A required property that specifies the source collection.</span></span>|  
|<span data-ttu-id="69002-113">Propriété `Predicate`</span><span class="sxs-lookup"><span data-stu-id="69002-113">`Predicate` property</span></span>|<span data-ttu-id="69002-114">Propriété requise qui spécifie le filtre pour la collection sous la forme d'une expression lambda.</span><span class="sxs-lookup"><span data-stu-id="69002-114">A required property that specifies the filter for the collection in the form of a lambda expression.</span></span>|  
|<span data-ttu-id="69002-115">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="69002-115">Return Value</span></span>|<span data-ttu-id="69002-116">Collection filtrée.</span><span class="sxs-lookup"><span data-stu-id="69002-116">The filtered collection.</span></span>|  
  
## <a name="code-sample-that-uses-the-custom-activity"></a><span data-ttu-id="69002-117">Exemple de code qui utilise l'activité personnalisée</span><span class="sxs-lookup"><span data-stu-id="69002-117">Code Sample that uses the Custom Activity</span></span>  
 <span data-ttu-id="69002-118">L'exemple de code suivant utilise l'activité personnalisée `FindInCollection` pour rechercher toutes les lignes d'une collection d'employés qui ont une propriété `Role` ayant la valeur `Manager` et la propriété `Location` ayant la valeur `Redmond`.</span><span class="sxs-lookup"><span data-stu-id="69002-118">The following code example uses the `FindInCollection` custom activity to find all rows in a collection of employees that have a `Role` property set to `Manager` and the `Location` property set to `Redmond`.</span></span>  
  
```csharp  
// Find all program managers in Redmond in the employees collection.  
  
Activity wf = new FindInCollection<Employee>  
{  
    Collections = new LambdaValue<IEnumerable<Employee>>(c => employees),                
    Predicate = new LambdaValue<Func<Employee, bool>>(c => new Func<Employee, bool>(e => e.Role.Equals("Manager") && e.Location.Equals("Redmond")))  
};  
```  
  
 <span data-ttu-id="69002-119">Le code suivant montre comment créer un programme de workflow qui utilise l'activité FindInCollection personnalisée, <xref:System.Activities.Statements.AddToCollection%601> et les activités <xref:System.Activities.Statements.ForEach%601> pour remplir une collection avec des employés, rechercher tous les employés qui ont des rôles de développeur et qui se trouvent à Redmond, puis itérer au sein de la liste résultante.</span><span class="sxs-lookup"><span data-stu-id="69002-119">The following code shows how to create a workflow program that uses the custom FindInCollection activity, <xref:System.Activities.Statements.AddToCollection%601>, and <xref:System.Activities.Statements.ForEach%601> activities to populate a collection with employees, find all the employees that have developer roles and are located in Redmond, and then iterate through the resulting list.</span></span>  
  
```csharp  
// Create the Linq predicate for the find expression  
  
Func<Employee, bool> predicate = e => e.Role == "DEV" && e.Location.Equals("Redmond");  
  
// Create workflow program  
Activity sampleWorkflow = new Sequence  
{  
    Variables = { employees, devsFromRedmond },  
    Activities =  
    {  
        new Assign<IList<Employee>>  
        {  
            To = employees,  
            Value = new LambdaValue<IList<Employee>>(c => new List<Employee>())  
        },  
        new AddToCollection<Employee>  
        {  
            Collection = new InArgument<ICollection<Employee>>(employees),  
            Item =  new LambdaValue<Employee>(c => new Employee(1, "Employee 1", "DEV", "Redmond"))  
        },  
        new AddToCollection<Employee>  
        {  
            Collection = new InArgument<ICollection<Employee>>(employees),  
            Item =  new LambdaValue<Employee>(c => new Employee(2, "Employee 2", "DEV", "Redmond"))  
        },  
        new AddToCollection<Employee>  
        {  
            Collection = new InArgument<ICollection<Employee>>(employees),  
            Item =  new LambdaValue<Employee>(c => new Employee(3, "Employee 3", "PM", "Redmond"))  
        },  
        new AddToCollection<Employee>  
        {  
            Collection = new InArgument<ICollection<Employee>>(employees),  
            Item =  new LambdaValue<Employee>(c => new Employee(4, "Employee 4", "PM", "China"))  
        },  
        new FindInCollection<Employee>  
        {  
            Collections = new InArgument<IEnumerable<Employee>>(employees),  
            Predicate = new LambdaValue<Func<Employee, bool>>(c => predicate),  
            Result = new OutArgument<IList<Employee>>(devsFromRedmond)  
        },  
        new ForEach<Employee>  
        {  
            Values = new InArgument<IEnumerable<Employee>>(devsFromRedmond),  
            Body = new ActivityAction<Employee>  
            {  
                Argument = iterationVariable,  
                Handler = new WriteLine  
                {  
                    Text = new InArgument<string>(env => iterationVariable.Get(env).ToString())  
                }  
            }  
        }  
    }  
};  
```  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="69002-120">Pour utiliser cet exemple</span><span class="sxs-lookup"><span data-stu-id="69002-120">To use this sample</span></span>  
  
1.  <span data-ttu-id="69002-121">À l'aide de [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], ouvrez le fichier solution LinqToObjects.sln.</span><span class="sxs-lookup"><span data-stu-id="69002-121">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the LinqToObjects.sln solution file.</span></span>  
  
2.  <span data-ttu-id="69002-122">Pour générer la solution, appuyez sur Ctrl+Maj+B.</span><span class="sxs-lookup"><span data-stu-id="69002-122">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="69002-123">Pour exécuter la solution, appuyez sur F5.</span><span class="sxs-lookup"><span data-stu-id="69002-123">To run the solution, press F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="69002-124">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="69002-124">The samples may already be installed on your machine.</span></span> <span data-ttu-id="69002-125">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="69002-125">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="69002-126">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="69002-126">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="69002-127">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="69002-127">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\Linq\LinqToObjects`  
  
## <a name="see-also"></a><span data-ttu-id="69002-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="69002-128">See Also</span></span>  
 [<span data-ttu-id="69002-129">Expressions lambda (Guide de programmation c#)</span><span class="sxs-lookup"><span data-stu-id="69002-129">Lambda Expressions (C# Programming Guide)</span></span>](http://go.microsoft.com/fwlink/?LinkId=150381)  
 [<span data-ttu-id="69002-130">LINQ to Objects</span><span class="sxs-lookup"><span data-stu-id="69002-130">LINQ to Objects</span></span>](http://go.microsoft.com/fwlink/?LinkID=150380)
