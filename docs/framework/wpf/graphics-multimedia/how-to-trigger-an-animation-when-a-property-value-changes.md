---
title: "Comment&#160;: d&#233;clencher une animation en cas de modification d&#39;une valeur de propri&#233;t&#233; | Microsoft Docs"
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
  - "animation, démarrer quand les valeurs de propriétés changent"
  - "Animations, démarrer quand les valeurs de propriétés changent"
  - "déclencher une animation"
ms.assetid: 12399c21-0300-4f4f-9e3a-d92d9907e5f5
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# Comment&#160;: d&#233;clencher une animation en cas de modification d&#39;une valeur de propri&#233;t&#233;
Cet exemple indique comment utiliser un <xref:System.Windows.Trigger> pour démarrer un <xref:System.Windows.Media.Animation.Storyboard> lorsqu'une valeur de propriété change.  Vous pouvez utiliser un <xref:System.Windows.Trigger> dans <xref:System.Windows.Style>, <xref:System.Windows.Controls.ControlTemplate> ou <xref:System.Windows.DataTemplate>.  
  
## Exemple  
 L'exemple suivant utilise un <xref:System.Windows.Trigger> pour animer le <xref:System.Windows.UIElement.Opacity%2A> d'un <xref:System.Windows.Controls.Button> lorsque sa propriété <xref:System.Windows.UIElement.IsMouseOver%2A> prend la valeur `true`.  
  
 [!code-xml[AnimatePropertyStoryboards#PropertyTriggerExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/AnimatePropertyStoryboards/XAML/PropertyTriggerExample.xaml#propertytriggerexample)]  
  
 Les animations appliquées par les objets de propriété <xref:System.Windows.Trigger> se comportent d'une façon plus complexe que les animations <xref:System.Windows.EventTrigger> ou les animations démarrées à l'aide des méthodes <xref:System.Windows.Media.Animation.Storyboard>.  Elles "procèdent au transfert" avec les animations définies par d'autres objets <xref:System.Windows.Trigger>, mais composent avec des <xref:System.Windows.EventTrigger> et des animations déclenchées par méthode.  
  
## Voir aussi  
 <xref:System.Windows.Trigger>   
 [Vue d'ensemble des techniques d'animation de propriétés](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)   
 [Vue d'ensemble des storyboards](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)