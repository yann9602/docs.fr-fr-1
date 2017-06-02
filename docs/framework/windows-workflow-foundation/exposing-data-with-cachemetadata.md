---
title: "Exposition de donn&#233;es avec CacheMetadata | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 34832f23-e93b-40e6-a80b-606a855a00d9
caps.latest.revision: 4
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# Exposition de donn&#233;es avec CacheMetadata
Avant d'exécuter une activité, le runtime du workflow obtient toutes les informations nécessaires sur l'activité afin de gérer son exécution.Le runtime de workflow obtient ces informations pendant l'exécution de la méthode <xref:System.Activities.Activity.CacheMetadata%2A>.L'implémentation par défaut de cette méthode fournit au runtime tous les arguments publics, variables et activités enfants exposés par l'activité lors de son exécution ; si l'activité a besoin de fournir plus d'informations au runtime \(telles que les membres privés ou les activités à planifier par l'activité\), cette méthode peut être substituée pour les fournir.  
  
## Comportement par défaut de CacheMetadata  
 L'implémentation par défaut de <xref:System.Activities.NativeActivity.CacheMetadata%2A> pour les activités qui dérivent de <xref:System.Activities.NativeActivity> traite les types de méthode suivants comme suit :  
  
-   <xref:System.Activities.InArgument%601>, <xref:System.Activities.OutArgument%601> ou <xref:System.Activities.InOutArgument%601> \(arguments génériques\) : ces arguments sont exposés au runtime comme des arguments dont le nom et le type correspondent au nom et au type de la propriété exposée, à la direction de l'argument approprié, et à certaines données de validation.  
  
-   <xref:System.Activities.Variable> ou une sous\-classe : ces membres sont exposés au runtime en tant que variables publiques.  
  
-   <xref:System.Activities.Activity> ou une sous\-classe : ces membres sont exposés au runtime en tant qu'activités enfants publiques.Le comportement par défaut peut être implémenté explicitement en appelant <xref:System.Activities.ActivityMetadata.AddImportedChild%2A>, en passant dans l'activité enfant.  
  
-   <xref:System.Activities.ActivityDelegate> ou une sous\-classe : ces membres sont exposés au runtime en tant que délégués publics.  
  
-   <xref:System.Collections.ICollection> de type <xref:System.Activities.Variable> : tous les éléments de la collection sont exposés au runtime en tant que variables publiques.  
  
-   <xref:System.Collections.ICollection> de type <xref:System.Activities.Activity> : tous les éléments de la collection sont exposés au runtime en tant qu'enfants publics.  
  
-   <xref:System.Collections.ICollection> de type <xref:System.Activities.ActivityDelegate> : tous les éléments de la collection sont exposés au runtime en tant que délégués publics.  
  
 Le <xref:System.Activities.Activity.CacheMetadata%2A> pour les activités qui dérivent de <xref:System.Activities.Activity>, <xref:System.Workflow.Activities.CodeActivity> et <xref:System.Activities.AsyncCodeActivity> fonctionnent également comme ci\-dessus, à l'exception des différences suivantes :  
  
-   Les classes qui dérivent de <xref:System.Activities.Activity> ne peuvent pas planifier des activités enfants ou des délégués, ces pourquoi ces membres sont exposés comme des enfants importés et des délégués ; les  
  
-   classes qui dérivent de <xref:System.Activities.CodeActivity> et <xref:System.Activities.AsyncCodeActivity> ne prennent pas en charge les variables, les enfants ou les délégués, c'est pourquoi seuls les arguments seront exposés.  
  
## Substitution de CacheMetadata pour fournir des informations au runtime  
 L'extrait de code suivant montre comment ajouter des informations sur les membres aux métadonnées d'une activité pendant l'exécution de la méthode <xref:System.Activities.Activity.CacheMetadata%2A>.Notez que la base de la méthode est appelée pour mettre en cache toutes les données publiques sur l'activité.  
  
```  
protected override void CacheMetadata(NativeActivityMetadata metadata)  
{      
    base.CacheMetadata(metadata);  
    metadata.AddImplementationChild(this._writeLine);  
    metadata.AddVariable(this._myVariable);  
    metadata.AddImplementationVariable(this._myImplementationVariable);  
  
    RuntimeArgument argument = new RuntimeArgument("MyArgument", ArgumentDirection.In, typeof(SomeType));  
    metadata.Bind(argument, this.SomeName);  
    metadata.AddArgument(argument);  
}  
  
```  
  
## Utilisation de CacheMetadata pour exposer les enfants de l'implémentation  
 Pour passer les données aux activités enfants qui doivent être planifiées par une activité à l'aide de variables, il est nécessaire d'ajouter les variables en tant que variables d'implémentation ; les valeurs des variables publiques ne peuvent pas être définies de cette façon.En effet, les activités sont conçues pour être exécutées plus comme des implémentations de fonctions \(qui ont des paramètres\), que comme des classes encapsulées \(qui ont des propriétés\).Toutefois, il existe des situations dans lesquelles les arguments doivent être définis explicitement, comme lors de l'utilisation de <xref:System.Activities.NativeActivityContext.ScheduleActivity%2A>, puisque l'activité planifiée n'a pas accès aux arguments de l'activité parent comme une activité enfant.  
  
 L'extrait de code suivant montre comment passer un argument d'une activité native à une activité planifiée à l'aide de <xref:System.Activities.Activity.CacheMetadata%2A>.  
  
```  
public sealed class ChildActivity : NativeActivity  
{  
    public WriteLine _writeLine;  
    public InArgument<string> Message { get; set; }  
    private Variable<string> MessageVariable { get; set; }  
    public ChildActivity()  
    {  
        MessageVariable = new Variable<string>();  
        _writeLine = new WriteLine  
        {  
            Text = new InArgument<string>(MessageVariable),  
        };  
    }  
    protected override void CacheMetadata(NativeActivityMetadata metadata)  
    {  
        base.CacheMetadata(metadata);  
        metadata.AddImplementationVariable(this.MessageVariable);  
        metadata.AddImplementationChild(this._writeLine);  
    }  
    protected override void Execute(NativeActivityContext context)  
    {  
        string configuredMessage = context.GetValue(Message);  
        context.SetValue(MessageVariable, configuredMessage);  
        context.ScheduleActivity(this._writeLine);  
    }  
}  
  
```