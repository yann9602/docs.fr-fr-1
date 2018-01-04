---
title: "Comment : animer un Popup"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Popup control [WPF], animating
- animation [WPF], Popup controls
ms.assetid: acaa2a0a-6137-4efd-9cd1-75ece222e390
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: dd79b29849510f40034dd0e2f1d9668c9b742929
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-animate-a-popup"></a><span data-ttu-id="8f062-102">Comment : animer un Popup</span><span class="sxs-lookup"><span data-stu-id="8f062-102">How to: Animate a Popup</span></span>
<span data-ttu-id="8f062-103">Cet exemple montre deux façons d’animer un <xref:System.Windows.Controls.Primitives.Popup> contrôle.</span><span class="sxs-lookup"><span data-stu-id="8f062-103">This example shows two ways to animate a <xref:System.Windows.Controls.Primitives.Popup> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8f062-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="8f062-104">Example</span></span>  
 <span data-ttu-id="8f062-105">L’exemple suivant définit la <xref:System.Windows.Controls.Primitives.PopupAnimation> à une valeur de propriété <xref:System.Windows.Controls.Primitives.PopupAnimation.Slide>, ce qui entraîne la <xref:System.Windows.Controls.Primitives.Popup> à « diapositive in » lorsqu’il s’affiche.</span><span class="sxs-lookup"><span data-stu-id="8f062-105">The following example sets the <xref:System.Windows.Controls.Primitives.PopupAnimation> property to a value of <xref:System.Windows.Controls.Primitives.PopupAnimation.Slide>, which causes the <xref:System.Windows.Controls.Primitives.Popup> to "slide-in" when it appears.</span></span>  
  
 <span data-ttu-id="8f062-106">Pour faire pivoter le <xref:System.Windows.Controls.Primitives.Popup>, cet exemple affecte un <xref:System.Windows.Media.RotateTransform> à la <xref:System.Windows.UIElement.RenderTransform%2A> propriété sur le <xref:System.Windows.Controls.Canvas>, qui est l’élément enfant de la <xref:System.Windows.Controls.Primitives.Popup>.</span><span class="sxs-lookup"><span data-stu-id="8f062-106">In order to rotate the <xref:System.Windows.Controls.Primitives.Popup>, this example assigns a <xref:System.Windows.Media.RotateTransform> to the <xref:System.Windows.UIElement.RenderTransform%2A> property on the <xref:System.Windows.Controls.Canvas>, which is the child element of the <xref:System.Windows.Controls.Primitives.Popup>.</span></span>  
  
 <span data-ttu-id="8f062-107">Pour la transformation fonctionne correctement, l’exemple doit définir le <xref:System.Windows.Controls.Primitives.Popup.AllowsTransparency%2A> propriété `true`.</span><span class="sxs-lookup"><span data-stu-id="8f062-107">For the transform to work correctly, the example must set the <xref:System.Windows.Controls.Primitives.Popup.AllowsTransparency%2A> property to `true`.</span></span> <span data-ttu-id="8f062-108">En outre, le <xref:System.Windows.FrameworkElement.Margin%2A> sur la <xref:System.Windows.Controls.Canvas> le contenu doit spécifier suffisamment d’espace pour le <xref:System.Windows.Controls.Primitives.Popup> pour faire pivoter.</span><span class="sxs-lookup"><span data-stu-id="8f062-108">In addition, the <xref:System.Windows.FrameworkElement.Margin%2A> on the <xref:System.Windows.Controls.Canvas> content must specify enough space for the <xref:System.Windows.Controls.Primitives.Popup> to rotate.</span></span>  
  
 [!code-xaml[AnimatedPopup#RotateTransform2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AnimatedPopup/CS/Window1.xaml#rotatetransform2)]  
  
 <span data-ttu-id="8f062-109">L’exemple suivant montre comment un <xref:System.Windows.Controls.Primitives.ButtonBase.Click> événement qui se produit lorsqu’un <xref:System.Windows.Controls.Button> est activé, les déclencheurs le <xref:System.Windows.Media.Animation.Storyboard> qui démarre l’animation.</span><span class="sxs-lookup"><span data-stu-id="8f062-109">The following example shows how a <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event, which occurs when a <xref:System.Windows.Controls.Button> is clicked, triggers the <xref:System.Windows.Media.Animation.Storyboard> that starts the animation.</span></span>  
  
 [!code-xaml[AnimatedPopup#RotateTransform1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AnimatedPopup/CS/Window1.xaml#rotatetransform1)]  
  
## <a name="see-also"></a><span data-ttu-id="8f062-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8f062-110">See Also</span></span>  
 <xref:System.Windows.UIElement.RenderTransform%2A>  
 <xref:System.Windows.Controls.Primitives.BulletDecorator>  
 <xref:System.Windows.Media.RotateTransform>  
 <xref:System.Windows.Media.Animation.Storyboard>  
 <xref:System.Windows.Controls.Primitives.Popup>  
 [<span data-ttu-id="8f062-111">Rubriques de guide pratique</span><span class="sxs-lookup"><span data-stu-id="8f062-111">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/popup-how-to-topics.md)  
 [<span data-ttu-id="8f062-112">Vue d’ensemble de Popup</span><span class="sxs-lookup"><span data-stu-id="8f062-112">Popup Overview</span></span>](../../../../docs/framework/wpf/controls/popup-overview.md)
