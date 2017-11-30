---
title: "Comment : animer un objet à l'aide d'images clés"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- animation [WPF], objects with key frames
- key frames [WPF], animating objects with
ms.assetid: b1f15ba9-cac7-4cea-8699-5c6b55c05c5e
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 71feb0ecef7a6356c95b843fbc2657ad2e4a7996
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-animate-an-object-by-using-key-frames"></a><span data-ttu-id="7ca21-102">Comment : animer un objet à l'aide d'images clés</span><span class="sxs-lookup"><span data-stu-id="7ca21-102">How to: Animate an Object by Using Key Frames</span></span>
<span data-ttu-id="7ca21-103">Cet exemple montre comment animer un objet qui, dans cet exemple est la <xref:System.Windows.Controls.Page.Background%2A> propriété d’un <xref:System.Windows.Controls.Page> contrôle, à l’aide d’images clés.</span><span class="sxs-lookup"><span data-stu-id="7ca21-103">This example shows how to animate an object, which in this example is the <xref:System.Windows.Controls.Page.Background%2A> property of a <xref:System.Windows.Controls.Page> control, by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7ca21-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="7ca21-104">Example</span></span>  
 <span data-ttu-id="7ca21-105">L’exemple suivant utilise le <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> classe pour animer la couleur change pour la <xref:System.Windows.Controls.Page.Background%2A> propriété d’un <xref:System.Windows.Controls.Page> contrôle.</span><span class="sxs-lookup"><span data-stu-id="7ca21-105">The following example uses the <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> class to animate color changes for the <xref:System.Windows.Controls.Page.Background%2A> property of a <xref:System.Windows.Controls.Page> control.</span></span> <span data-ttu-id="7ca21-106">L’exemple d’animation modifie un pinceau d’arrière-plan à intervalles réguliers.</span><span class="sxs-lookup"><span data-stu-id="7ca21-106">The example animation changes to a different background brush at regular intervals.</span></span> <span data-ttu-id="7ca21-107">Cette animation utilise la <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> classe pour créer trois images clés différentes.</span><span class="sxs-lookup"><span data-stu-id="7ca21-107">This animation uses the <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> class to create three different key frames.</span></span> <span data-ttu-id="7ca21-108">L’animation utilise des images clés de la manière suivante :</span><span class="sxs-lookup"><span data-stu-id="7ca21-108">The animation uses key frames in the following manner:</span></span>  
  
1.  <span data-ttu-id="7ca21-109">À la fin de la première seconde, anime une instance de la <xref:System.Windows.Media.LinearGradientBrush> classe.</span><span class="sxs-lookup"><span data-stu-id="7ca21-109">At the end of the first second, animates an instance of the <xref:System.Windows.Media.LinearGradientBrush> class.</span></span> <span data-ttu-id="7ca21-110">Cette section de l’exemple applique un dégradé linéaire à la couleur d’arrière-plan afin que la couleur transitions de jaune orange rouge.</span><span class="sxs-lookup"><span data-stu-id="7ca21-110">This section of the example applies a linear gradient to the background color so that the color transitions from yellow to orange to red.</span></span>  
  
2.  <span data-ttu-id="7ca21-111">À la fin de la prochaine seconde, anime une instance de la <xref:System.Windows.Media.RadialGradientBrush> classe.</span><span class="sxs-lookup"><span data-stu-id="7ca21-111">At the end of the next second, animates an instance of the <xref:System.Windows.Media.RadialGradientBrush> class.</span></span> <span data-ttu-id="7ca21-112">Cette section de l’exemple applique un dégradé radial à la couleur d’arrière-plan afin que la couleur passe du blanc bleu noir.</span><span class="sxs-lookup"><span data-stu-id="7ca21-112">This section of the example applies a radial gradient to the background color so that the color transitions from white to blue to black.</span></span>  
  
3.  <span data-ttu-id="7ca21-113">À la fin de la troisième seconde, anime une instance de la <xref:System.Windows.Media.DrawingBrush> classe.</span><span class="sxs-lookup"><span data-stu-id="7ca21-113">At the end of the third second, animates an instance of the <xref:System.Windows.Media.DrawingBrush> class.</span></span> <span data-ttu-id="7ca21-114">Cette section de l’exemple applique un modèle de damier à l’arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="7ca21-114">This section of the example applies a checkerboard pattern to the background.</span></span>  
  
4.  <span data-ttu-id="7ca21-115">L’animation recommence et se répète indéfiniment.</span><span class="sxs-lookup"><span data-stu-id="7ca21-115">The animation begins again and repeats indefinitely.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7ca21-116"><xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame>est le seul type d’image clé que vous pouvez utiliser avec la <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> classe.</span><span class="sxs-lookup"><span data-stu-id="7ca21-116"><xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> is the only type of key frame that you can use with the <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> class.</span></span> <span data-ttu-id="7ca21-117">Images clés comme <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> créent des modifications soudaines dans les valeurs, autrement dit, les modifications de couleur dans cet exemple se produisent soudainement.</span><span class="sxs-lookup"><span data-stu-id="7ca21-117">Key frames like <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> create sudden changes in values, that is, the color changes in this example occur suddenly.</span></span>  
  
 [!code-xaml[keyframes_snip#ObjectAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/ObjectAnimationUsingKeyFramesExample.xaml#objectanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="7ca21-118">Pour l’exemple complet, consultez la page [Animation d’image clé, exemple](http://go.microsoft.com/fwlink/?LinkID=160012).</span><span class="sxs-lookup"><span data-stu-id="7ca21-118">For the complete sample, see [KeyFrame Animation Sample](http://go.microsoft.com/fwlink/?LinkID=160012).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ca21-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7ca21-119">See Also</span></span>  
 <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>  
 <xref:System.Windows.Controls.Page.Background%2A>  
 <xref:System.Windows.Controls.Page>  
 <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame>  
 <xref:System.Windows.Media.LinearGradientBrush>  
 <xref:System.Windows.Media.RadialGradientBrush>  
 <xref:System.Windows.Media.DrawingBrush>  
 [<span data-ttu-id="7ca21-120">Vue d'ensemble des animations d'image clé</span><span class="sxs-lookup"><span data-stu-id="7ca21-120">Key-Frame Animations Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [<span data-ttu-id="7ca21-121">Guides pratiques relatifs aux images clés</span><span class="sxs-lookup"><span data-stu-id="7ca21-121">Key-Frame How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)
