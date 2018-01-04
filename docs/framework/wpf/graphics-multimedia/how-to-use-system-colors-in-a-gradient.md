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
ms.workload: dotnet
ms.openlocfilehash: acf0f2c63e0b176f28d611183aab1abecc8f1678
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-system-colors-in-a-gradient"></a><span data-ttu-id="e8f16-102">Comment : utiliser des couleurs système dans un dégradé</span><span class="sxs-lookup"><span data-stu-id="e8f16-102">How to: Use System Colors in a Gradient</span></span>
<span data-ttu-id="e8f16-103">Pour utiliser une couleur système dans un dégradé, vous utilisez la  *\<SystemColor >*couleur et  *\<SystemColor >*ColorKey des propriétés statiques de la <xref:System.Windows.SystemColors> classe pour obtenir un référence à la couleur, où  *\<SystemColor >* est le nom de la couleur système souhaitée.</span><span class="sxs-lookup"><span data-stu-id="e8f16-103">To use a system color in a gradient, you use the *\<SystemColor>*Color and *\<SystemColor>*ColorKey static properties of the <xref:System.Windows.SystemColors> class to obtain a reference to the color, where *\<SystemColor>* is the name of the desired system color.</span></span> <span data-ttu-id="e8f16-104">Utilisez le  *\<SystemColor >*ColorKey propriétés lorsque vous souhaitez créer une référence dynamique qui met à jour automatiquement en tant que les modifications de thème du système.</span><span class="sxs-lookup"><span data-stu-id="e8f16-104">Use the *\<SystemColor>*ColorKey properties when you want to create a dynamic reference that updates automatically as the system theme changes.</span></span> <span data-ttu-id="e8f16-105">Sinon, utilisez le  *\<SystemColor >*propriétés de couleur.</span><span class="sxs-lookup"><span data-stu-id="e8f16-105">Otherwise, use the *\<SystemColor>*Color properties.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e8f16-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="e8f16-106">Example</span></span>  
 <span data-ttu-id="e8f16-107">L’exemple suivant utilise des ressources de couleurs système dynamiques pour créer un dégradé.</span><span class="sxs-lookup"><span data-stu-id="e8f16-107">The following example uses dynamic system color resources to create a gradient.</span></span>  
  
 [!code-xaml[brushsamples_snip#GraphicsMMDynamicSystemColorGradientExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/DynamicSystemColorExample.xaml#graphicsmmdynamicsystemcolorgradientexamplewholepage)]  
  
 <span data-ttu-id="e8f16-108">L’exemple suivant utilise des ressources de couleurs système statiques pour créer un dégradé.</span><span class="sxs-lookup"><span data-stu-id="e8f16-108">The next example uses static system color resources to create a gradient.</span></span>  
  
 [!code-xaml[brushsamples_snip#GraphicsMMStaticSystemColorGradientExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/StaticSystemColorExample.xaml#graphicsmmstaticsystemcolorgradientexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="e8f16-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e8f16-109">See Also</span></span>  
 <xref:System.Windows.SystemColors>  
 [<span data-ttu-id="e8f16-110">Peindre une zone avec un pinceau système</span><span class="sxs-lookup"><span data-stu-id="e8f16-110">Paint an Area with a System Brush</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)  
 [<span data-ttu-id="e8f16-111">Vue d’ensemble de la peinture avec des couleurs unies ou des dégradés</span><span class="sxs-lookup"><span data-stu-id="e8f16-111">Painting with Solid Colors and Gradients Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)
