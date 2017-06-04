---
title: "Architecture Windows Workflow | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1d4c6495-d64a-46d0-896a-3a01fac90aa9
caps.latest.revision: 20
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 20
---
# Architecture Windows Workflow
[!INCLUDE[wf](../../../includes/wf-md.md)] élève le niveau d'abstraction pour le développement d'applications interactives à durée d'exécution longue.Les unités de travail sont encapsulées comme activités.Les activités s'exécutent dans un environnement qui fournit les fonctions suivantes : contrôle de flux, gestion des exceptions, propagation d'erreur, persistance des données d'état, chargement et déchargement de flux de travail en cours depuis la mémoire, suivi et flux de transaction.  
  
## Architecture des activités  
 Les activités sont développées comme types CLR qui dérivent soit des objets <xref:System.Activities.Activity>, <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity> ou <xref:System.Activities.NativeActivity>, soit de leurs variantes <xref:System.Activities.Activity%601>, <xref:System.Activities.CodeActivity%601>, <xref:System.Activities.AsyncCodeActivity%601> ou <xref:System.Activities.NativeActivity%601>, qui retournent une valeur.En développant des activités qui dérivent de l'objet <xref:System.Activities.Activity>, l'utilisateur peut assembler des activités préexistantes pour créer rapidement des unités de travail qui s'exécutent dans l'environnement de workflow.L'objet <xref:System.Activities.CodeActivity> permet quant à lui de créer la logique d'exécution en code managé, en utilisant l'objet <xref:System.Activities.CodeActivityContext> principalement pour accéder aux arguments d'activité.<xref:System.Activities.AsyncCodeActivity> est semblable à <xref:System.Activities.CodeActivity>, mais peut être utilisé pour implémenter des tâches asynchrones.En développant des activités qui dérivent de l'objet <xref:System.Activities.NativeActivity>, les utilisateurs peuvent accéder au runtime via l'objet <xref:System.Activities.NativeActivityContext> pour des fonctionnalités telles que la planification d'activités enfants, la création de signets, l'appel de travail asynchrone, l'enregistrement de transactions, etc.  
  
 La création d'activités qui dérivent de l'objet <xref:System.Activities.Activity> est déclarative et ces activités peuvent être créées en XAML.Dans l'exemple suivant, une activité appelée `Prompt` est créée à l'aide d'autres activités pour le corps d'exécution.  
  
```  
<Activity x:Class='Prompt'  
  xmlns:x='http://schemas.microsoft.com/winfx/2006/xaml'  
    xmlns:z='http://schemas.microsoft.com/netfx/2008/xaml/schema'  
xmlns:my='clr-namespace:XAMLActivityDefinition;assembly=XAMLActivityDefinition'  
xmlns:s="clr-namespace:System;assembly=mscorlib"  
xmlns="http://schemas.microsoft.com/2009/workflow">  
<z:SchemaType.Members>  
    <z:SchemaType.SchemaProperty Name='Text' Type=' InArgument(s:String)' />  
  <z:SchemaType.SchemaProperty Name='Response' Type='OutArgument(s:String)' />  
</z:SchemaType.Members>  
  <Sequence>  
    <my:WriteLine Text='[Text]' />  
    <my:ReadLine BookmarkName='r1' Result='[Response]' />  
  </Sequence>  
</Activity>  
```  
  
## Contexte de l'activité  
 <xref:System.Activities.ActivityContext> est l'interface de l'auteur d'activité avec l'exécution du workflow. Elle permet d'accéder aux nombreuses fonctionnalités du runtime.L'exemple suivant consiste à définir une activité qui utilise le contexte d'exécution pour créer un signet \(mécanisme qui permet à une activité d'enregistrer un point de continuation dans son exécution qui peut être reprise par un hôte passant des données dans l'activité\).  
  
 [!code-csharp[CFX_WorkflowApplicationExample#15](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#15)]  
  
## Cycle de vie des activités  
 À l'origine, l'instance d'une activité est à l'état <xref:System.Activities.ActivityInstanceState>.À moins que des exceptions ne soient rencontrées, elle conserve cet état jusqu'à ce que l'exécution de toutes les activités enfants, ainsi que tout autre travail en attente \(objets <xref:System.Activities.Bookmark>, par exemple\) soient terminés, auquel cas elle passe à l'état <xref:System.Activities.ActivityInstanceState>.Le parent d'une instance d'activité peut demander qu'un enfant soit annulé. Si l'enfant est en mesure d'être annulé, il se termine et passe à l'état <xref:System.Activities.ActivityInstanceState>.Si une exception est levée lors de l'exécution, le runtime passe l'activité à l'état <xref:System.Activities.ActivityInstanceState> et propage l'exception en haut de la chaîne parente d'activités.Voici les trois états d'achèvement d'une activité :  
  
-   **Fermé :** l'activité a terminé son travail et s'est arrêtée.  
  
-   **Annulé :** l'activité a abandonné normalement son travail et s'est arrêtée.Le travail n'est pas restauré explicitement lorsque cet état est entré.  
  
-   **Faulted :** l'activité a rencontré une erreur et s'est arrêtée sans terminer son travail.  
  
 Les activités restent à l'état <xref:System.Activities.ActivityInstanceState> lorsqu'elles sont rendues persistantes ou sont déchargées.