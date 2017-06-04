---
title: "Activit&#233; LINQ to Objects | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 403c82e8-7f2b-42f6-93cd-95c35bc76ead
caps.latest.revision: 11
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 11
---
# Activit&#233; LINQ to Objects
Cet exemple montre comment créer une activité pour utiliser LINQ to Objects pour interroger des éléments d'une collection.  
  
## Détails de l'activité pour FindInCollection  
 Cette activité permet aux utilisateurs d'interroger des éléments de collections en mémoire à l'aide de LINQ to Objects.Vous devez fournir un prédicat LINQ sous la forme d'une expression lambda pour filtrer les résultats.Cette activité peut être utilisée conjointement avec des activités <xref:System.Activities.Statements.AddToCollection%601>.  
  
 Le tableau suivant décrit en détail les propriétés et valeurs de retour pour l'activité.  
  
|Propriété ou valeur de retour|Description|  
|-----------------------------------|-----------------|  
|Propriété `Collection`|Propriété requise qui spécifie la collection source.|  
|Propriété `Predicate`|Propriété requise qui spécifie le filtre pour la collection sous la forme d'une expression lambda.|  
|Valeur de retour|Collection filtrée.|  
  
## Exemple de code qui utilise l'activité personnalisée  
 L'exemple de code suivant utilise l'activité personnalisée `FindInCollection` pour rechercher toutes les lignes d'une collection d'employés qui ont une propriété `Role` ayant la valeur `Manager` et la propriété `Location` ayant la valeur `Redmond`.  
  
```csharp  
// Find all program managers in Redmond in the employees collection.  
  
Activity wf = new FindInCollection<Employee>  
{  
    Collections = new LambdaValue<IEnumerable<Employee>>(c => employees),                
    Predicate = new LambdaValue<Func<Employee, bool>>(c => new Func<Employee, bool>(e => e.Role.Equals("Manager") && e.Location.Equals("Redmond")))  
};  
  
```  
  
 Le code suivant montre comment créer un programme de workflow qui utilise l'activité FindInCollection personnalisée, <xref:System.Activities.Statements.AddToCollection%601> et les activités <xref:System.Activities.Statements.ForEach%601> pour remplir une collection avec des employés, rechercher tous les employés qui ont des rôles de développeur et qui se trouvent à Redmond, puis itérer au sein de la liste résultante.  
  
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
  
#### Pour utiliser cet exemple  
  
1.  À l'aide de [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], ouvrez le fichier solution LinqToObjects.sln.  
  
2.  Pour générer la solution, appuyez sur Ctrl\+Maj\+B.  
  
3.  Pour exécuter la solution, appuyez sur F5.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur.Recherchez le répertoire \(par défaut\) suivant avant de continuer.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n'existe pas, rendez\-vous sur la page \(éventuellement en anglais\) des [exemples Windows Communication Foundation \(WCF\) et Windows Workflow Foundation \(WF\) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\Linq\LinqToObjects`  
  
## Voir aussi  
 [Expressions lambda \(Guide de programmation C\#\)](http://go.microsoft.com/fwlink/?LinkId=150381)   
 [LINQ to Objects](http://go.microsoft.com/fwlink/?LinkID=150380)