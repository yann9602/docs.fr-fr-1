---
title: "Didacticiel : hébergement d'objets visuels dans une application Win32"
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
- visual objects in Win32 code [WPF]
- Win32 code [WPF], visual objects in
- hosting [WPF], visual objects in Win32 code
ms.assetid: f0e1600c-3217-43d5-875d-1864fa7fe628
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 47402194e3588699625249848c96d58b37059138
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="tutorial-hosting-visual-objects-in-a-win32-application"></a>Didacticiel : hébergement d'objets visuels dans une application Win32
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] propose un environnement de création d'applications élaboré. Toutefois, lorsque vous avez beaucoup investi [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] code, il peut être plus efficace d’ajouter [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fonctionnalités à votre application plutôt que de réécrire votre code. Pour fournir la prise en charge de [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] et [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sous-systèmes graphiques utilisés simultanément dans une application, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fournit un mécanisme pour l’hébergement des objets dans un [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] fenêtre.  
  
 Ce didacticiel décrit comment écrire un exemple d’application, [Test de positionnement avec interopérabilité Win32, exemple](http://go.microsoft.com/fwlink/?LinkID=159995), qui héberge [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] objets visuels dans un [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] fenêtre.  
  

  
<a name="requirements"></a>   
## <a name="requirements"></a>Spécifications  
 Ce didacticiel suppose que vous avez des connaissances de base en matière de programmation [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] et [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]. Pour une introduction à [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] de programmation, consultez [procédure pas à pas : Ma première application de bureau WPF](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md). Pour obtenir une présentation [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] de programmation, consultez un des nombreux livres sur l’objet, en particulier *programmation Windows* de Charles Petzold.  
  
> [!NOTE]
>  Ce didacticiel comprend plusieurs exemples de code tirés de l'exemple associé. Cependant, pour une meilleure lecture, il n'inclut pas la totalité de l'exemple de code. Pour l’exemple de code complet, consultez [Test de positionnement avec interopérabilité Win32, exemple](http://go.microsoft.com/fwlink/?LinkID=159995).  
  
<a name="creating_the_host_win32_window"></a>   
## <a name="creating-the-host-win32-window"></a>Création de la fenêtre Win32 hôte  
 La clé d’hébergement [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] des objets dans une [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] fenêtre est la <xref:System.Windows.Interop.HwndSource> classe. Cette classe encapsule le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] des objets dans une [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] fenêtre, ce qui permet à incorporer dans vos [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] comme une fenêtre enfant.  
  
 L’exemple suivant montre le code permettant de créer le <xref:System.Windows.Interop.HwndSource> de l’objet en tant que la [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] fenêtre de conteneur pour les objets visuels. Pour définir le style de fenêtre, de position et d’autres paramètres pour le [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] fenêtre, utilisez la <xref:System.Windows.Interop.HwndSourceParameters> objet.  
  
 [!code-csharp[VisualsHitTesting#101](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#101)]
 [!code-vb[VisualsHitTesting#101](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#101)]  
  
> [!NOTE]
>  La valeur de la <xref:System.Windows.Interop.HwndSourceParameters.ExtendedWindowStyle%2A> propriété ne peut pas être définie sur WS_EX_TRANSPARENT. Cela signifie que l’hôte [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] fenêtre ne peut pas être transparent. Pour cette raison, la couleur d’arrière-plan de l’hôte [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] est définie sur la même couleur d’arrière-plan que sa fenêtre parente.  
  
<a name="adding_visual_objects_to_the_host_win32_window"></a>   
## <a name="adding-visual-objects-to-the-host-win32-window"></a>Ajout d’objets visuels à la fenêtre Win32 hôte  
 Une fois que vous avez créé un hôte [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] fenêtre de conteneur pour les objets visuels, vous pouvez ajouter des objets visuels à celui-ci. Vous devez vous assurer que toutes les transformations des objets visuels, telles que les animations, ne pas s’étendent au-delà des limites de l’ordinateur hôte [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] fenêtre du rectangle englobant.  
  
 L’exemple suivant montre le code permettant de créer le <xref:System.Windows.Interop.HwndSource> de l’objet et ajouter des objets visuels.  
  
> [!NOTE]
>  Le <xref:System.Windows.Interop.HwndSource.RootVisual%2A> propriété de la <xref:System.Windows.Interop.HwndSource> objet est défini pour le premier objet visuel ajouté à l’hôte [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] fenêtre. L’objet visuel racine définit le nœud supérieur de l’arborescence des objets visuels. Tous les objets visuels suivants ajoutés à l’hôte [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] fenêtre sont ajoutés en tant qu’objets enfants.  
  
 [!code-csharp[VisualsHitTesting#100](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#100)]
 [!code-vb[VisualsHitTesting#100](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#100)]  
  
<a name="implementing_the_win32_message_filter"></a>   
## <a name="implementing-the-win32-message-filter"></a>Implémentation du filtre de messages Win32  
 L’hôte [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] fenêtre pour les objets visuels nécessite une procédure de filtre de messages de fenêtre pour traiter les messages sont envoyés à la fenêtre à partir de la file d’attente de l’application. La procédure de fenêtre reçoit des messages à partir de la [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] système. Ces messages peuvent être des messages de gestion de fenêtre ou des messages de saisie. Vous pouvez choisir de gérer un message dans votre procédure de fenêtre ou de transférer le message au système de traitement par défaut.  
  
 Le <xref:System.Windows.Interop.HwndSource> objet que vous avez défini comme parent pour les objets visuels doit faire référence à la procédure de filtre de messages de fenêtre vous fournissez. Lorsque vous créez le <xref:System.Windows.Interop.HwndSource> de l’objet, définissez le <xref:System.Windows.Interop.HwndSourceParameters.HwndSourceHook%2A> propriété pour faire référence à la procédure de fenêtre.  
  
 [!code-csharp[VisualsHitTesting#102](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#102)]
 [!code-vb[VisualsHitTesting#102](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#102)]  
  
 L’exemple suivant montre le code permettant de gérer les messages lorsque les boutons gauche et droit de la souris sont relâchés. Position d’accès de la valeur de coordonnée de la souris se trouve dans la valeur de le `lParam` paramètre.  
  
 [!code-csharp[VisualsHitTesting#103](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#103)]
 [!code-vb[VisualsHitTesting#103](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#103)]  
  
<a name="processing_the_win32_messages"></a>   
## <a name="processing-the-win32-messages"></a>Traitement des messages Win32  
 Le code dans l’exemple suivant montre comment un test de positionnement est effectué par rapport à la hiérarchie d’objets visuels contenue dans l’hôte [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] fenêtre. Vous pouvez identifier si un point se trouve dans la géométrie d’un objet visuel, à l’aide de la <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> méthode pour spécifier l’objet visuel racine et la valeur de la coordonnée pour le test de positionnement. Dans ce cas, l’objet visuel racine est la valeur de la <xref:System.Windows.Interop.HwndSource.RootVisual%2A> propriété de la <xref:System.Windows.Interop.HwndSource> objet.  
  
 [!code-csharp[VisualsHitTesting#104](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyCircle.cs#104)]
 [!code-vb[VisualsHitTesting#104](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyCircle.vb#104)]  
  
 Pour plus d’informations sur le test de positionnement par rapport aux objets visuels, consultez [d’accès au test dans la couche visuelle](../../../../docs/framework/wpf/graphics-multimedia/hit-testing-in-the-visual-layer.md).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Interop.HwndSource>  
 [Test de positionnement avec interopérabilité Win32, exemple](http://go.microsoft.com/fwlink/?LinkID=159995)  
 [Test de positionnement dans la couche visuelle](../../../../docs/framework/wpf/graphics-multimedia/hit-testing-in-the-visual-layer.md)
