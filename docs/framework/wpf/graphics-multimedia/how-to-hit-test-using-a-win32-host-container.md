---
title: "Comment : effectuer un test de positionnement à l'aide d'un conteneur hôte Win32"
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
- hit tests [WPF], using Win32 host containers
- visual objects [WPF], hit tests on
- Win32 host containers [WPF], hit tests using
ms.assetid: 9491f7f3-d8ba-4573-a888-2f064d1349dc
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9a5cb77a53cbb106593b70d618bab67ef816e901
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-hit-test-using-a-win32-host-container"></a>Comment : effectuer un test de positionnement à l'aide d'un conteneur hôte Win32
Vous pouvez créer des objets visuels dans un [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] fenêtre en fournissant un hôte de conteneur de fenêtre pour les objets visuels. Pour assurer la gestion des événements des objets visuels du conteneur, vous devez traiter les messages transmis à la boucle de filtre de messages du conteneur de fenêtre hôte. Reportez-vous à [didacticiel : hébergeant des objets dans une Application Win32 Visual](../../../../docs/framework/wpf/graphics-multimedia/tutorial-hosting-visual-objects-in-a-win32-application.md) pour plus d’informations sur l’hébergement d’objets visuels dans un [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] fenêtre.  
  
## <a name="example"></a>Exemple  
 Le code suivant montre comment définir des gestionnaires d’événements de souris pour un [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] fenêtre qui est utilisé comme un conteneur d’hôte pour des objets visuels.  
  
 [!code-csharp[VisualsHitTesting#103](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#103)]
 [!code-vb[VisualsHitTesting#103](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#103)]  
  
 L’exemple suivant montre comment configurer un test de positionnement en réponse à intercepter des événements de souris spécifiques.  
  
 [!code-csharp[VisualsHitTesting#104](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyCircle.cs#104)]
 [!code-vb[VisualsHitTesting#104](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyCircle.vb#104)]  
  
 Le <xref:System.Windows.Interop.HwndSource> présente [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] de contenu dans un [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] fenêtre. La valeur de la <xref:System.Windows.Interop.HwndSource.RootVisual%2A> propriété de la <xref:System.Windows.Interop.HwndSource> objet représente le nœud supérieur dans la hiérarchie d’arborescence d’éléments visuels.  
  
 Pour l’exemple complet sur le test de positionnement des objets à l’aide d’un conteneur hôte Win32, consultez [Test de positionnement avec interopérabilité Win32, exemple](http://go.microsoft.com/fwlink/?LinkID=159995).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Interop.HwndSource>  
 [Test de positionnement dans la couche visuelle](../../../../docs/framework/wpf/graphics-multimedia/hit-testing-in-the-visual-layer.md)  
 [Didacticiel : hébergement d’objets visuels dans une application Win32](../../../../docs/framework/wpf/graphics-multimedia/tutorial-hosting-visual-objects-in-a-win32-application.md)
