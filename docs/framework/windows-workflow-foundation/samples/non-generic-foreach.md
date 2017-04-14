---
title: "ForEach non g&#233;n&#233;rique | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 576cd07a-d58d-4536-b514-77bad60bff38
caps.latest.revision: 12
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 12
---
# ForEach non g&#233;n&#233;rique
[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] fournit, dans sa boîte à outils, un ensemble d'activités de flux de contrôle, notamment <xref:System.Activities.Statements.ForEach%601>, qui permet l'itération au sein des collections <xref:System.Collections.IEnumerable%601>.  
  
 <xref:System.Activities.Statements.ForEach%601> requiert que sa propriété <xref:System.Activities.Statements.ForEach%601.Values%2A> soit de type <xref:System.Collections.IEnumerable%601>.  Cela empêche les utilisateurs d'itérer au sein des structures de données qui implémentent l'interface <xref:System.Collections.IEnumerable%601> \(par exemple, <xref:System.Collections.ArrayList>\).  La version non générique de <xref:System.Activities.Statements.ForEach%601> passe outre cette spécification, aux dépens d'un runtime plus complexe afin de garantir la compatibilité des types des valeurs dans la collection.  
  
 Cet exemple montre comment implémenter une activité <xref:System.Activities.Statements.ForEach%601> non générique et son concepteur.  Cette activité peut être utilisée pour itérer au sein de <xref:System.Collections.ArrayList>.  
  
## Activité ForEach  
 L'instruction C\#\/VB `foreach` énumère les éléments d'une collection, exécutant une instruction incorporée pour chaque élément de la collection.  Les activités [!INCLUDE[wf1](../../../../includes/wf1-md.md)] équivalentes de `foreach` sont <xref:System.Activities.Statements.ForEach%601> et <xref:System.Activities.Statements.ParallelForEach%601>.  L'activité <xref:System.Activities.Statements.ForEach%601> contient une liste de valeurs et un corps.  Au moment de l'exécution, la liste fait l'objet d'une itération et le corps est exécuté pour chaque valeur de la liste.  
  
 Dans la plupart des cas, la version générique de l'activité doit être la solution par défaut, car elle couvre la plupart des scénarios dans lesquels elle est utilisée, et fournit la vérification des types au moment de la compilation.  La version non générique peut être utilisée pour itérer au sein de types qui implémentent l'interface <xref:System.Collections.IEnumerable> non générique.  
  
## Définition de classes  
 L'exemple de code suivant illustre la définition d'une activité `ForEach` non générique.  
  
```  
[ContentProperty("Body")]  
public class ForEach : NativeActivity  
{  
    [RequiredArgument]  
    [DefaultValue(null)]  
    InArgument<IEnumerable> Values { get; set; }  
  
    [DefaultValue(null)]  
    [DependsOn("Values")]  
    ActivityAction<object> Body { get; set; }   
}  
```  
  
 Body \(facultatif\)  
 <xref:System.Activities.ActivityAction> de type <xref:System.Object>, qui est exécuté pour chaque élément de la collection.  Chaque élément individuel est passé dans le corps \(Body\) via sa propriété `Argument`.  
  
 Values \(facultatif\)  
 Collection des éléments sur lesquels est effectuée l'itération.  La vérification que tous les éléments de la collection sont de types compatibles est effectuée au moment de l'exécution.  
  
## Exemple d'utilisation de ForEach  
 Le code suivant montre comment utiliser l'activité ForEach dans une application.  
  
```  
string[] names = { "bill", "steve", "ray" };  
  
DelegateInArgument<object> iterationVariable = new DelegateInArgument<object>() { Name = "iterationVariable" };  
  
Activity sampleUsage =  
    new ForEach  
    {  
       Values = new InArgument<IEnumerable>(c=> names),  
       Body = new ActivityAction<object>   
       {                          
           Argument = iterationVariable,  
           Handler = new WriteLine  
           {  
               Text = new InArgument<string>(env => string.Format("Hello {0}",                                                               iterationVariable.Get(env)))  
           }  
       }  
   };  
```  
  
|Condition|Message|Gravité|Type d'exception|  
|---------------|-------------|-------------|----------------------|  
|La valeur est `null`|La valeur d'un argument d'activité 'Values' requis n'a pas été fournie.|Erreur|<xref:System.InvalidOperationException>|  
  
## Concepteur ForEach  
 Le concepteur d'activités de l'exemple est semblable, en apparence, au concepteur fourni pour l'activité <xref:System.Activities.Statements.ForEach%601> intégrée.  Le concepteur s'affiche dans la boîte à outils dans la catégorie **Exemples**, **Activités non génériques**.  Le concepteur est nommé **ForEachWithBodyFactory** dans la boîte à outils, car l'activité expose un <xref:System.Activities.Presentation.IActivityTemplateFactory> dans la boîte à outils, ce qui crée l'activité avec un <xref:System.Activities.ActivityAction> correctement configuré.  
  
```  
public sealed class ForEachWithBodyFactory : IActivityTemplateFactory  
{  
    public Activity Create(DependencyObject target)  
    {  
        return new Microsoft.Samples.Activities.Statements.ForEach()  
        {  
            Body = new ActivityAction<object>()  
            {  
                Argument = new DelegateInArgument<object>()  
                {  
                    Name = "item"  
                }  
            }  
        };  
    }  
}  
```  
  
#### Pour exécuter cet exemple  
  
1.  Définissez le projet de votre choix comme projet de démarrage de la solution :  
  
    1.  **CodeTestClient** indique comment utiliser l'activité à l'aide du code.  
  
    2.  **DesignerTestClient** indique comment utiliser l'activité dans le concepteur.  
  
2.  Générez et exécutez le projet.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur.  Recherchez le répertoire \(par défaut\) suivant avant de continuer.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n'existe pas, accédez à la page des [exemples Windows Communication Foundation \(WCF\) et Windows Workflow Foundation \(WF\) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].  Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\NonGenericForEach`