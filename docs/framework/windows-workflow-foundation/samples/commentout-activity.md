---
title: "Activité CommentOut"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 340204c3-f827-45fb-870e-55e2ac457ca5
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e66d1383c42310c2f61b0b3059cb8b347ad55a15
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="commentout-activity"></a>Activité CommentOut
Cet exemple montre comment écrire une activité personnalisée qui supprime d’autres activités du chemin d’exécution, en les transformant en fait en commentaire.  
  
## <a name="the-commentout-activity"></a>Activité CommentOut  
 Pour atteindre son objectif, l'activité CommentOut dérive de la classe de base <xref:System.Activities.CodeActivity> et implémente une méthode <xref:System.Activities.CodeActivity.Execute%2A> vide.  
  
```  
protected override void Execute(CodeActivityContext context)  
{  
}  
```  
  
 La classe est déclarée comme indiqué dans l'exemple suivant.  
  
```  
[Designer(typeof(CommentOutDesigner))]  
[ContentProperty("Body")]  
public sealed class CommentOut : CodeActivity  
```  
  
 L'attribut `Designer` spécifie la classe qui implémente l'interface graphique de l'activité au moment du design. L'attribut `ContentProperty` déclare que la propriété `"Body"` peut être ignorée dans la représentation XAML d'une instance de cette activité.  
  
```  
<Border x:Uid="Border_1" BorderThickness ="1">  
    <sad:WorkflowItemPresenter   
    x:Uid="sad:WorkflowItemPresenter_1" AutomationProperties.AutomationId="Body" Item="{Binding Path=ModelItem.Body, Mode=TwoWay}"  
    AllowedItemType="{x:Type sa:Activity}"  
    HintText="Drop activity here"   
    Margin="5,5,5,5" />  
</Border>  
```  
  
 Dans la classe de concepteur, le XAML est utilisé pour créer une représentation visuelle personnalisée de l'activité. <xref:System.Activities.Presentation.WorkflowItemPresenter> est une classe qui fournit l'éditeur visuel.  
  
 Une seule activité peut être supprimée sur la surface de l'activité `CommentOut`. Si vous voulez ajouter plusieurs activités à cette surface, faites-y d'abord glisser une activité de séquence.  
  
#### <a name="to-use-this-sample"></a>Pour utiliser cet exemple  
  
1.  Ouvrez CommentOut.sln dans [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Compilez la solution en appuyant sur CTRL+MAJ+B.  
  
3.  Démarrez l'exemple sans débogage en appuyant sur CTRL+F5.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\CommentOut`
