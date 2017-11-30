---
title: "Comment : utiliser des couleurs système dans un dégradé"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- gradients [WPF], system colors in
- system colors in gradients [WPF]
ms.assetid: 11942e7e-6300-4b50-8ed1-f50e8d20e7d2
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 105e22588f68d999811f5482342d53851a4d25eb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-system-colors-in-a-gradient"></a>Comment : utiliser des couleurs système dans un dégradé
Pour utiliser une couleur système dans un dégradé, vous utilisez la  *\<SystemColor >*couleur et  *\<SystemColor >*ColorKey des propriétés statiques de la <xref:System.Windows.SystemColors> classe pour obtenir un référence à la couleur, où  *\<SystemColor >* est le nom de la couleur système souhaitée. Utilisez le  *\<SystemColor >*ColorKey propriétés lorsque vous souhaitez créer une référence dynamique qui met à jour automatiquement en tant que les modifications de thème du système. Sinon, utilisez le  *\<SystemColor >*propriétés de couleur.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise des ressources de couleurs système dynamiques pour créer un dégradé.  
  
 [!code-xaml[brushsamples_snip#GraphicsMMDynamicSystemColorGradientExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/DynamicSystemColorExample.xaml#graphicsmmdynamicsystemcolorgradientexamplewholepage)]  
  
 L’exemple suivant utilise des ressources de couleurs système statiques pour créer un dégradé.  
  
 [!code-xaml[brushsamples_snip#GraphicsMMStaticSystemColorGradientExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/StaticSystemColorExample.xaml#graphicsmmstaticsystemcolorgradientexamplewholepage)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.SystemColors>  
 [Peindre une zone avec un pinceau système](../../../../docs/framework/wpf/graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)  
 [Vue d’ensemble de la peinture avec des couleurs unies ou des dégradés](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)
