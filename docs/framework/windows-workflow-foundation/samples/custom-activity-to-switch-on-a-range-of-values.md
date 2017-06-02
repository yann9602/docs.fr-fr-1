---
title: "Activit&#233; personnalis&#233;e pour commuter une plage de valeurs | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 441e0a17-421f-430c-ba97-59e4cc6c88e3
caps.latest.revision: 10
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 10
---
# Activit&#233; personnalis&#233;e pour commuter une plage de valeurs
Cet exemple montre comment créer une activité personnalisée qui étend l'utilisation d'un <xref:System.Activities.Statements.Switch%601>.Une instruction <xref:System.Activities.Statements.Switch%601> classique autorise la commutation basée sur une valeur unique.Mais dans certains scénarios d'application professionnelle, la commutation d'une activité est basée sur une plage de valeurs.Par exemple, une activité peut exécuter une action lorsque la valeur de commutation est comprise entre 1 et 5, une autre action lorsque la valeur est comprise entre 6 et 10, et une action par défaut pour toutes les autres valeurs.Cette activité personnalisée permet exactement ce scénario.  
  
## Activité SwitchRange  
 L'activité `SwitchRange` planifie une activité enfant lorsque la valeur de résultat de son expression est comprise dans la plage de l'un de ses `Cases`.  
  
 L'exemple de code suivant est une activité personnalisée qui commute en fonction d'une plage de valeurs.  
  
```csharp  
  
public sealed class SwitchRange<T> : NativeActivity where T : IComparable  
{  
   [RequiredArgument]  
   [DefaultValue(null)]  
   public InArgument<T> Expression { get; set; }  
  
   public IList<CaseRange<T>> Cases  
  
   [DefaultValue(null)]  
   public Activity Default { get; set; }}  
}  
```  
  
|||  
|-|-|  
|Propriété|Description|  
|Expression|Il s'agit de l'expression à évaluer et à comparer par rapport aux plages spécifiées dans la liste Cases.Le résultat de l'expression est de type T.|  
|Cases|Chaque cas se compose d'une plage \(From et To\) et d'une activité \(Body\).L'expression est évaluée et comparée par rapport aux plages.Si le résultat de l'expression est compris dans la plage de l'un des cas, l'activité correspondante est exécutée.|  
|Default|Activité qui est exécutée lorsque aucune correspondance n'est obtenue pour le cas.Lorsque la valeur définie est `null`, aucune action n'est entreprise.|  
  
## Classe CaseRange  
 La classe `CaseRange` représente une plage dans une activité `SwitchRange`.Chaque instance de `CaseRange` contient une plage \(composée d'un `From` et d'un `To`\) et une activité `Body` qui est planifiée si l'expression dans `SwitchRange` est évaluée dans la plage.  
  
 L'exemple de code suivant est la définition de la classe `CaseRange`.  
  
```  
  
public class CaseRange<T> where T : IComparable  
{  
    public T From { get; set; }  
  
    public T To { get; set; }  
  
    public Activity Action { get; set; }  
}  
```  
  
> [!NOTE]
>  Les deux classes `CaseRange` et `SwitchRange`, qui sont définies dans l'exemple, sont des classes génériques pouvant fonctionner avec n'importe quel type qui implémente `IComparable`, comme la classe <xref:System.Activities.Statements.Switch%601>.  
  
## Utilisation de l'exemple  
 L'exemple de code suivant illustre l'utilisation de l'activité `SwitchRange`.  
  
```csharp  
  
Activity SwitchRange = new SwitchRange<int>  
{  
    Expression = new InArgument<int>(value),  
    Cases =   
    {  
        new CaseRange<int>                      
        {  
            From = 1,  
            To = 5,  
            Action = new WriteLine  
            {  
                Text = "Case 1-5 selected",  
            }  
        },  
        new CaseRange<int>  
        {  
            From = 6,  
            To = 10,  
            Action = new WriteLine  
            {  
                Text = "Case 6-10 selected",  
            }  
        }  
    },  
    Default = new WriteLine { Text = "Default Case selected" }  
};  
```  
  
#### Pour utiliser cet exemple  
  
1.  À l'aide de [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], ouvrez le fichier solution SwitchRange.sln.  
  
2.  Pour générer la solution, appuyez sur Ctrl\+Maj\+B.  
  
3.  Pour exécuter la solution, appuyez sur Ctrl\+F5.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur.Recherchez le répertoire \(par défaut\) suivant avant de continuer.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n'existe pas, rendez\-vous sur la page \(éventuellement en anglais\) des [exemples Windows Communication Foundation \(WCF\) et Windows Workflow Foundation \(WF\) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\SwitchRange`  
  
## Voir aussi