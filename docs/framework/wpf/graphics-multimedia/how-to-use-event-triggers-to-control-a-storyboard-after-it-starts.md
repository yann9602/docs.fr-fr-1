---
title: "Comment&#160;: utiliser des d&#233;clencheurs d&#39;&#233;v&#233;nements pour contr&#244;ler un storyboard apr&#232;s son d&#233;marrage | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "déclencheurs d'événements, contrôler les storyboards"
  - "Animations, contrôler après le démarrage"
  - "déclencheurs, contrôler les storyboards"
ms.assetid: 3b115594-6a93-4972-b24d-61aa16f1c15f
caps.latest.revision: 17
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 17
---
# Comment&#160;: utiliser des d&#233;clencheurs d&#39;&#233;v&#233;nements pour contr&#244;ler un storyboard apr&#232;s son d&#233;marrage
Cet exemple montre comment contrôler un <xref:System.Windows.Media.Animation.Storyboard> après son démarrage.  Pour démarrer un <xref:System.Windows.Media.Animation.Storyboard> avec [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], utilisez <xref:System.Windows.Media.Animation.BeginStoryboard> qui distribue les animations aux objets et aux propriétés qu'ils animent, puis démarre le storyboard.  Si vous donnez un nom à <xref:System.Windows.Media.Animation.BeginStoryboard> en spécifiant sa propriété <xref:System.Windows.Media.Animation.BeginStoryboard.Name%2A>, vous en faites un storyboard contrôlable.  Vous pouvez ensuite contrôler interactivement le storyboard après son démarrage.  
  
 Utilisez les actions de storyboard suivantes avec des objets <xref:System.Windows.EventTrigger> pour contrôler un storyboard.  
  
-   <xref:System.Windows.Media.Animation.PauseStoryboard> : suspend le storyboard.  
  
-   <xref:System.Windows.Media.Animation.ResumeStoryboard> : reprend un storyboard suspendu.  
  
-   <xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio> : modifie la vitesse du storyboard.  
  
-   <xref:System.Windows.Media.Animation.SkipStoryboardToFill> : fait avancer un storyboard à la fin de sa période de remplissage, le cas échéant.  
  
-   <xref:System.Windows.Media.Animation.StopStoryboard> : arrête le storyboard.  
  
-   <xref:System.Windows.Media.Animation.RemoveStoryboard> : supprime le storyboard, en libérant des ressources.  
  
## Exemple  
 L'exemple suivant utilise des actions de storyboard contrôlable pour contrôler interactivement un storyboard.  
  
 **Remarque :** pour obtenir un exemple de contrôle d'un storyboard à l'aide de code, consultez [Contrôler un storyboard après son démarrage à l'aide de ses méthodes interactives](../../../../docs/framework/wpf/graphics-multimedia/how-to-control-a-storyboard-after-it-starts.md).  
  
 [!code-xml[timingbehaviors_snip#ControlStoryboardExampleUsingWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/ControlStoryboardExample.xaml#controlstoryboardexampleusingwholepage)]  
  
 Pour obtenir des exemples supplémentaires, consultez [Galerie d'exemples d'animation](http://go.microsoft.com/fwlink/?LinkID=159969).  
  
## Voir aussi  
 <xref:System.Windows.Media.Animation.ResumeStoryboard>   
 <xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>   
 <xref:System.Windows.Media.Animation.SkipStoryboardToFill>   
 <xref:System.Windows.Media.Animation.PauseStoryboard>   
 <xref:System.Windows.Media.Animation.StopStoryboard>   
 <xref:System.Windows.Media.Animation.SeekStoryboard>   
 [Contrôler un storyboard après son démarrage à l'aide de ses méthodes interactives](../../../../docs/framework/wpf/graphics-multimedia/how-to-control-a-storyboard-after-it-starts.md)   
 [Vue d'ensemble de l'animation](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)   
 [Vue d'ensemble des storyboards](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)