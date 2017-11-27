---
title: "Comment : ajouter la gestion de classe d'un événement routé"
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
- routed events [WPF], class handlers
- task_core_add_class_handling_routed_properties [WPF]
- class handlers [WPF], routed events
ms.assetid: 15b7b06c-9112-4ee5-b30a-65d10c5c5df6
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: abbbdce0ca12c4d8bdd12f616bf49c3d6f66f441
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-add-class-handling-for-a-routed-event"></a>Comment : ajouter la gestion de classe d'un événement routé
Les événements routés peuvent être gérés par les gestionnaires de classe ou les gestionnaires d’instance sur un nœud donné de l’itinéraire. Gestionnaires de classe sont appelés tout d’abord et peuvent être utilisés par les implémentations de classe pour supprimer des événements à partir de la gestion de l’instance ou d’introduire d’autres comportements spécifiques des événements sur les événements qui sont détenus par les classes de base. Cet exemple illustre deux techniques étroitement liées pour l’implémentation des gestionnaires de classe.  
  
## <a name="example"></a>Exemple  
 Cet exemple utilise une classe personnalisée basée sur le <xref:System.Windows.Controls.Canvas> Panneau de configuration. Le principe de base de l’application est que la classe personnalisée introduit des comportements sur ses éléments enfants, y compris l’interception des que clics de n’importe quel bouton gauche de la souris et leur marquage comme gérés, avant de la classe d’élément enfant ou d’instances sur ce dernier sera appelé.  
  
 Le <xref:System.Windows.UIElement> classe expose une méthode virtuelle qui permet la gestion de classe sur le <xref:System.Windows.UIElement.PreviewMouseLeftButtonDown> événement, en substituant simplement l’événement. Il s’agit de la façon la plus simple pour implémenter la gestion de classe si cette méthode virtuelle est disponible quelque part dans la hiérarchie de votre classe. Le code suivant illustre la <xref:System.Windows.UIElement.OnPreviewMouseLeftButtonDown%2A> mise en œuvre dans le « MyEditContainer » qui est dérivé de <xref:System.Windows.Controls.Canvas>. L’implémentation marque l’événement comme géré dans les arguments, puis ajoute du code pour permettre à l’élément source à une modification visible de base.  
  
 [!code-csharp[ClassHandling#OnStarClassHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ClassHandling/CSharp/SDKSampleLibrary/class1.cs#onstarclasshandler)]
 [!code-vb[ClassHandling#OnStarClassHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ClassHandling/visualbasic/sdksamplelibrary/class1.vb#onstarclasshandler)]  
  
 Si aucun élément virtuel n’est disponible sur les classes de base ou pour cette méthode particulière, la gestion de classe peut être ajoutée directement à l’aide d’une méthode utilitaire de la <xref:System.Windows.EventManager> (classe), <xref:System.Windows.EventManager.RegisterClassHandler%2A>. Cette méthode doit uniquement être appelée au sein de l’initialisation statique des classes qui ajoutent la gestion de classe. Cet exemple ajoute un autre gestionnaire pour <xref:System.Windows.UIElement.PreviewMouseLeftButtonDown> , et dans ce cas la classe inscrite correspond à la classe personnalisée. En revanche, lorsque vous utilisez les méthodes virtuelles, la classe inscrite correspond réellement le <xref:System.Windows.UIElement> classe de base. Dans les cas où des classes de base et les sous-classes inscrivent la gestion de classe, les gestionnaires de sous-classes sont appelées au préalable. Le comportement de l’application serait que ce gestionnaire affiche tout d’abord sa boîte de message et ensuite le changement dans le Gestionnaire de la méthode virtuelle sont affiché.  
  
 [!code-csharp[ClassHandling#StaticAndRegisterClassHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ClassHandling/CSharp/SDKSampleLibrary/class1.cs#staticandregisterclasshandler)]
 [!code-vb[ClassHandling#StaticAndRegisterClassHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ClassHandling/visualbasic/sdksamplelibrary/class1.vb#staticandregisterclasshandler)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.EventManager>  
 [Marquage des événements routés comme gérés et gestion de classe](../../../../docs/framework/wpf/advanced/marking-routed-events-as-handled-and-class-handling.md)  
 [Gérer un événement routé](../../../../docs/framework/wpf/advanced/how-to-handle-a-routed-event.md)  
 [Vue d’ensemble des événements routés](../../../../docs/framework/wpf/advanced/routed-events-overview.md)
