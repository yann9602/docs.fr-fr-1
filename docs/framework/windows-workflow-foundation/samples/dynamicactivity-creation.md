---
title: "Création avec DynamicActivity"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d8ebe82f-98c8-4452-aed7-2c60a512b097
caps.latest.revision: "14"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4a579606bd3ee9d3f11669d59c6e7c9767b6eaf4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="dynamicactivity-creation"></a>Création avec DynamicActivity
Cet exemple montre deux façons différentes de créer une activité au moment de l'exécution à l'aide de l'activité <xref:System.Activities.DynamicActivity>.  
  
 Dans cet exemple, une activité est créée au moment de l'exécution avec un corps qui contient une activité <xref:System.Activities.Statements.Sequence> qui contient les activités <xref:System.Activities.Statements.ForEach%601> et <xref:System.Activities.Statements.Assign%601>. Une liste d'entrée d'entiers est passée dans l'activité et définie comme une propriété. L'activité <xref:System.Activities.Statements.ForEach%601> itère ensuite au sein de la liste de valeurs et l'accumule. Dans l'activité <xref:System.Activities.Statements.Assign%601>, la valeur moyenne est calculée en divisant l'accumulateur par le nombre d'éléments dans la liste et en l'affectant à la moyenne.  
  
 L'exemple illustre l'utilisation d'une activité <xref:System.Activities.DynamicActivity> qui transfère des variables comme arguments d'entrée et retourne des valeurs comme arguments de sortie. L'activité a un argument d'entrée nommé `Numbers` qui est une liste d'entiers. L'activité <xref:System.Activities.Statements.ForEach%601> itère au sein de la liste de valeurs et l'accumule. Dans l'activité <xref:System.Activities.Statements.Assign%601>, la valeur moyenne est calculée en divisant l'accumulateur par le nombre d'éléments dans la liste et en l'affectant à la moyenne. La moyenne est retournée comme un argument de sortie nommé `Average`.  
  
 Lorsque l'activité dynamique est créée par programmation, l'entrée et la sortie sont déclarées comme indiqué dans l'exemple de code suivant.  
  
```csharp  
DynamicActivity act = new DynamicActivity()  
{  
    DisplayName = "Find average",  
    Properties =   
    {  
        // Input argument  
        new DynamicActivityProperty  
        {  
            Name = "Numbers",  
            Type = typeof(InArgument<List<int>>),  
            Value = numbers  
        },  
        // Output argument  
        new DynamicActivityProperty  
        {  
            Name = "Average",  
            Type = typeof(OutArgument<double>),  
            Value = average  
        }  
    },  
};  
```  
  
 L'exemple de code suivant affiche la définition complète du `DynamicActivity` qui calcule la moyenne des valeurs dans une liste.  
  
```  
DynamicActivity act = new DynamicActivity()  
{  
    DisplayName = "Find average",  
    Properties =   
    {  
        // Input argument  
        new DynamicActivityProperty  
        {  
            Name = "Numbers",  
            Type = typeof(InArgument<List<int>>),  
            Value = numbers  
        },  
        // Output argument  
        new DynamicActivityProperty  
        {  
            Name = "Average",  
            Type = typeof(OutArgument<double>),  
            Value = average  
        }  
    },  
    Implementation = () =>  
        new Sequence  
        {  
            Variables = { result, accumulator },  
            Activities =  
            {  
                new ForEach<int>  
                {  
                    Values =  new ArgumentValue<IEnumerable<int>> { ArgumentName = "Numbers" },                                  
                    Body = new ActivityAction<int>  
                    {  
                        Argument = iterationVariable,  
                        Handler = new Assign<int>  
                        {  
                            To = accumulator,  
                            Value = new InArgument<int>(env => iterationVariable.Get(env) +  accumulator.Get(env))  
                        }  
                    }  
                },  
  
                // Calculate the average and assign to the output argument.  
                new Assign<double>  
                {  
                    To = new ArgumentReference<double> { ArgumentName = "Average" },  
                    Value = new InArgument<double>(env => accumulator.Get(env) / numbers.Get(env).Count<int>())  
                },  
            }  
        }  
};  
```  
  
 En cas de création en XAML, l'entrée et la sortie sont déclarées comme indiqué dans l'exemple suivant.  
  
```xml  
<Activity x:Class="Microsoft.Samples.DynamicActivityCreation.FindAverage"  
          xmlns="http://schemas.microsoft.com/netfx/2009/xaml/activities"  
          xmlns:scg="clr-namespace:System.Collections.Generic;assembly=mscorlib"  
          xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
  <x:Members>  
    <x:Property Name="Numbers" Type="InArgument(scg:List(x:Int32))" />  
    <x:Property Name="Average" Type="OutArgument(x:Double)" />  
  </x:Members>  
    ...  
    ...  
</Activity>  
```  
  
 Les données XAML peuvent être créées visuellement à l'aide du [!INCLUDE[wfd1](../../../../includes/wfd1-md.md)]. S’il est inclus dans un projet Visual Studio, veillez à définir « Action de génération » à « None » pour l’empêcher d’en cours de compilation. Les données XAML peuvent ensuite être chargées dynamiquement à l'aide de l'appel suivant.  
  
```  
Activity act2 = ActivityXamlServices.Load(@"FindAverage.xaml");  
```  
  
 L'instance <xref:System.Activities.DynamicActivity> créée par programmation ou par le biais du chargement d'un workflow XAML peut être utilisée comme indiqué dans l'exemple de code suivant. Notez que « acte » passé à la `WorkflowInvoker.Invoke` est le « acte » <xref:System.Activities.Activity> défini dans le premier exemple de code.  
  
```  
IDictionary<string, object> results = WorkflowInvoker.Invoke(act, new Dictionary<string, object> { { "Numbers", numbers } });  
  
Console.WriteLine("The average calculated using the code activity is = " + results["Average"]);  
```  
  
#### <a name="to-use-this-sample"></a>Pour utiliser cet exemple  
  
1.  À l'aide de [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], ouvrez le fichier solution DynamicActivityCreation.sln.  
  
2.  Pour générer la solution, appuyez sur Ctrl+Maj+B.  
  
3.  Pour exécuter la solution, appuyez sur Ctrl+F5.  
  
## <a name="command-line-arguments"></a>Arguments de la ligne de commande  
 Cet exemple accepte des arguments de ligne de commande. Les utilisateurs peuvent fournir une liste de nombres pour l'activité afin de calculer leur moyenne. La liste de nombres à utiliser est passée comme une liste de nombres séparés par un espace. Par exemple, pour calculer la moyenne de 5, 10 et 32, appelez l'exemple à l'aide de la ligne de commande suivante.  
  
 **DynamicActivityCreation 5 10 32**  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\DynamicActivity\DynamicActivityCreation`  
  
## <a name="see-also"></a>Voir aussi
