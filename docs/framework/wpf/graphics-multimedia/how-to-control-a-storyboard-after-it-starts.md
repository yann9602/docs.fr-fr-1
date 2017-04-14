---
title: "Comment&#160;: contr&#244;ler un storyboard apr&#232;s son d&#233;marrage | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Animations, contrôler après le démarrage"
ms.assetid: 040f13f0-69f9-4ab5-be2b-079f4f80c7c0
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# Comment&#160;: contr&#244;ler un storyboard apr&#232;s son d&#233;marrage
Cet exemple indique comment utiliser le code pour contrôler un <xref:System.Windows.Media.Animation.Storyboard> après son démarrage.  Pour contrôler une table de montage séquentiel en langage [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], utilisez les objets <xref:System.Windows.Trigger> et <xref:System.Windows.TriggerAction>. Pour obtenir un exemple, consultez [Utiliser des déclencheurs d'événements pour contrôler un storyboard après son démarrage](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md).  
  
 Pour démarrer une table de montage séquentiel, vous utilisez sa méthode <xref:System.Windows.Media.Animation.Storyboard.Begin%2A>, qui distribue les animations de la table de montage séquentiel aux propriétés animées et démarre la table de montage séquentiel.  
  
 Pour pouvoir contrôler une table de montage séquentiel, vous utilisez la méthode <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> et spécifiez la valeur **true** comme deuxième paramètre.  Vous pouvez ensuite utiliser les méthodes interactives de la table de montage séquentiel pour suspendre, reprendre, rechercher, arrêter, accélérer ou ralentir la table de montage séquentiel, ou encore pour l'avancer à sa période de remplissage.  La liste ci\-dessous répertorie les méthodes interactives de la table de montage séquentiel :  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Pause%2A> : suspend le storyboard.  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Resume%2A> : reprend un storyboard suspendu.  
  
-   <xref:System.Windows.Media.Animation.Storyboard.SetSpeedRatio%2A> : définit la vitesse interactive de la table de montage séquentiel.  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> : recherche la table de montage séquentiel à partir de l'emplacement spécifié.  
  
-   <xref:System.Windows.Media.Animation.Storyboard.SeekAlignedToLastTick%2A> : recherche la table de montage séquentiel jusqu'à l'emplacement spécifié.  Contrairement à la méthode <xref:System.Windows.Media.Animation.Storyboard.Seek%2A>, cette opération est traitée avant le battement suivant.  
  
-   <xref:System.Windows.Media.Animation.Storyboard.SkipToFill%2A> : fait avancer la table de montage séquentiel à la fin de sa période de remplissage, le cas échéant.  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Stop%2A> : arrête le storyboard.  
  
 Dans l'exemple suivant, plusieurs méthodes de table de montage séquentiel sont utilisées pour contrôler une table de montage séquentiel de manière interactive.  
  
 **Remarque :** pour obtenir un exemple de contrôle d'une table de montage séquentiel à l'aide de déclencheurs en langage [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], consultez [Utiliser des déclencheurs d'événements pour contrôler un storyboard après son démarrage](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md).  
  
## Exemple  
 [!code-csharp[timingbehaviors_procedural_snip#ControlStoryboardExampleUsingWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/ControlStoryboardExample.cs#controlstoryboardexampleusingwholepage)]
 [!code-vb[timingbehaviors_procedural_snip#ControlStoryboardExampleUsingWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/controlstoryboardexample.vb#controlstoryboardexampleusingwholepage)]  
  
## Voir aussi  
 [Utiliser des déclencheurs d'événements pour contrôler un storyboard après son démarrage](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md)