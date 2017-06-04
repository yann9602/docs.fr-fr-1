---
title: "Comment&#160;: cr&#233;er un &#233;v&#233;nement rout&#233; personnalis&#233; | Microsoft Docs"
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
  - "créer, événements routés"
  - "événements, router"
  - "événements routés, créer"
ms.assetid: b79f459a-1c3f-4045-b2d4-1659cc8eaa3c
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# Comment&#160;: cr&#233;er un &#233;v&#233;nement rout&#233; personnalis&#233;
Pour que votre événement personnalisé prenne en charge [le routage d'événement](GTMT), vous devez enregistrer un <xref:System.Windows.RoutedEvent> à l'aide de la méthode <xref:System.Windows.EventManager.RegisterRoutedEvent%2A>.  Cet exemple montre les principes de base de la création d'un événement routé personnalisé.  
  
## Exemple  
 Comme illustré dans l'exemple suivant, enregistrez d'abord un <xref:System.Windows.RoutedEvent> à l'aide de la méthode <xref:System.Windows.EventManager.RegisterRoutedEvent%2A>.  Par convention, le nom de champ statique <xref:System.Windows.RoutedEvent> doit se terminer par le suffixe ***Event***.  Dans cet exemple, l'événement porte le nom `Tap` et la stratégie de routage de l'événement est <xref:System.Windows.RoutingStrategy>.  Après l'appel d'inscription, vous pouvez fournir des accesseurs d'événement [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] ajout\/suppression pour l'événement.  
  
 Notez que même si, dans cet exemple, l'événement est déclenché au moyen de la méthode virtuelle `OnTap`, la manière dont vous déclenchez votre événement ou dont votre événement répond aux modifications dépend de vos besoins.  
  
 Notez également que cet exemple implémente fondamentalement toute une sous\-classe de <xref:System.Windows.Controls.Button> ; cette sous\-classe est construite comme un assembly distinct, puis est instanciée comme une classe personnalisée d'une page [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] distincte.  Pour illustrer le concept, les contrôles sous\-classés peuvent être insérés dans des arborescences composées d'autres contrôles. Dans cette situation, les événements personnalisés de ces contrôles ont exactement les mêmes fonctionnalités de routage d'événements que tout élément [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] natif.  
  
 [!code-csharp[RoutedEventCustom#CustomClass](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventCustom/CSharp/SDKSampleLibrary/class1.cs#customclass)]
 [!code-vb[RoutedEventCustom#CustomClass](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventCustom/VB/SDKSampleLibrary/Class1.vb#customclass)]  
  
 [!code-xml[RoutedEventCustom#Page](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventCustom/CSharp/RoutedEventCustomApp/default.xaml#page)]  
  
 Les événements de tunneling sont créés de la même manière, mais avec <xref:System.Windows.RoutedEvent.RoutingStrategy%2A> ayant la valeur <xref:System.Windows.RoutingStrategy> dans l'appel d'inscription.  Par convention, les événements de tunneling dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sont précédés du préfixe « Preview ».  
  
 Pour voir un exemple du fonctionnement des événements de propagation, consultez [Gérer un événement routé](../../../../docs/framework/wpf/advanced/how-to-handle-a-routed-event.md).  
  
## Voir aussi  
 [Vue d'ensemble des événements routés](../../../../docs/framework/wpf/advanced/routed-events-overview.md)   
 [Vue d'ensemble des entrées](../../../../docs/framework/wpf/advanced/input-overview.md)   
 [Vue d'ensemble de la création de contrôles](../../../../docs/framework/wpf/controls/control-authoring-overview.md)