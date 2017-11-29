---
title: "Comment : créer un événement routé personnalisé"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- routed events [WPF], creating
- events [WPF], routing
ms.assetid: b79f459a-1c3f-4045-b2d4-1659cc8eaa3c
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e901242b265e0012f9ad65d9eaab89b1b63b40ac
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-custom-routed-event"></a>Comment : créer un événement routé personnalisé
Pour votre événement personnalisé prendre en charge le routage des événements, vous devez inscrire un <xref:System.Windows.RoutedEvent> à l’aide de la <xref:System.Windows.EventManager.RegisterRoutedEvent%2A> (méthode). Cet exemple montre les principes de base de la création d’un événement routé personnalisé.  
  
## <a name="example"></a>Exemple  
 Comme indiqué dans l’exemple suivant, vous inscrivez tout d’abord un <xref:System.Windows.RoutedEvent> à l’aide de la <xref:System.Windows.EventManager.RegisterRoutedEvent%2A> (méthode). Par convention, le <xref:System.Windows.RoutedEvent> nom de champ statique doit se terminer par le suffixe ***événement***. Dans cet exemple, le nom de l’événement est `Tap` et la stratégie de routage de l’événement est <xref:System.Windows.RoutingStrategy.Bubble>. Après l’appel d’inscription, vous pouvez fournir des accesseurs d’événement de [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] add et remove pour l’événement.  
  
 Notez que, même si l’événement est déclenché au moyen de la méthode virtuelle `OnTap` dans cet exemple, la manière dont vous déclenchez votre événement ou dont votre événement répond aux modifications dépend de vos besoins.  
  
 Notez également que cet exemple implémente fondamentalement toute une sous-classe de <xref:System.Windows.Controls.Button>; cette sous-classe est construite comme un assembly distinct, puis est instanciée comme une classe personnalisée sur un séparé [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] page. Pour illustrer le concept, les contrôles sous-classés peuvent être insérés dans des arborescences composées d’autres contrôles. Dans cette situation, les événements personnalisés de ces contrôles ont exactement les mêmes fonctionnalités de routage d’événement que tout élément [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] natif.  
  
 [!code-csharp[RoutedEventCustom#CustomClass](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventCustom/CSharp/SDKSampleLibrary/class1.cs#customclass)]
 [!code-vb[RoutedEventCustom#CustomClass](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventCustom/VB/SDKSampleLibrary/Class1.vb#customclass)]  
  
 [!code-xaml[RoutedEventCustom#Page](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventCustom/CSharp/RoutedEventCustomApp/default.xaml#page)]  
  
 Les événements de tunneling sont créés de la même manière, mais avec <xref:System.Windows.RoutedEvent.RoutingStrategy%2A> la valeur <xref:System.Windows.RoutingStrategy.Tunnel> dans l’appel d’inscription. Par convention, les événements de tunneling dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sont précédés du préfixe « Preview ».  
  
 Pour voir un exemple du fonctionnement des événements de propagation, consultez [Guide pratique pour gérer un événement routé](../../../../docs/framework/wpf/advanced/how-to-handle-a-routed-event.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble des événements routés](../../../../docs/framework/wpf/advanced/routed-events-overview.md)  
 [Vue d’ensemble des entrées](../../../../docs/framework/wpf/advanced/input-overview.md)  
 [Vue d’ensemble de la création de contrôles](../../../../docs/framework/wpf/controls/control-authoring-overview.md)
