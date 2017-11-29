---
title: "Comment : animer l'opacité d'un élément ou d'un pinceau"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- opacity [WPF], animating
- animation [WPF], Opacity property
ms.assetid: 572af23b-39dd-48d1-9db5-4bca56a4b3d3
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 808d29292e176af8d3af1fc0f4a02c48ee05ea35
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-animate-the-opacity-of-an-element-or-brush"></a><span data-ttu-id="ea3cf-102">Comment : animer l'opacité d'un élément ou d'un pinceau</span><span class="sxs-lookup"><span data-stu-id="ea3cf-102">How to: Animate the Opacity of an Element or Brush</span></span>
<span data-ttu-id="ea3cf-103">Pour rendre un élément d’infrastructure apparaître et disparaître, vous pouvez animer ses <xref:System.Windows.UIElement.Opacity%2A> propriété, ou vous pouvez animer la <xref:System.Windows.Media.Brush.Opacity%2A> propriété de la <xref:System.Windows.Media.Brush> (ou pinceaux) utilisé pour peindre.</span><span class="sxs-lookup"><span data-stu-id="ea3cf-103">To make a framework element fade in and out of view, you can animate its <xref:System.Windows.UIElement.Opacity%2A> property or you can animate the <xref:System.Windows.Media.Brush.Opacity%2A> property of the <xref:System.Windows.Media.Brush> (or brushes) used to paint it.</span></span> <span data-ttu-id="ea3cf-104">Animation opacité de l’élément rend et ses enfants apparaître et disparaître, mais animer le pinceau utilisé pour peindre l’élément vous permet d’être plus sélectif sur la partie de l’élément en fondu.</span><span class="sxs-lookup"><span data-stu-id="ea3cf-104">Animating the element's opacity makes it and its children fade in and out of view, but animating the brush used to paint the element enables you to be more selective about which portion of the element fades.</span></span> <span data-ttu-id="ea3cf-105">Par exemple, vous pouvez animer l’opacité d’un pinceau utilisé pour peindre l’arrière-plan d’un bouton.</span><span class="sxs-lookup"><span data-stu-id="ea3cf-105">For example, you could animate the opacity of a brush used to paint a button's background.</span></span> <span data-ttu-id="ea3cf-106">Cela entraînerait l’arrière-plan du bouton à la disparition en fondu de vue, tout en laissant son texte complètement opaque.</span><span class="sxs-lookup"><span data-stu-id="ea3cf-106">This would cause the button's background to fade in and out of view, while leaving its text fully opaque.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ea3cf-107">Animation le <xref:System.Windows.Media.Brush.Opacity%2A> d’un <xref:System.Windows.Media.Brush> offre des avantages de performances sur l’animation le <xref:System.Windows.UIElement.Opacity%2A> propriété d’un élément.</span><span class="sxs-lookup"><span data-stu-id="ea3cf-107">Animating the <xref:System.Windows.Media.Brush.Opacity%2A> of a <xref:System.Windows.Media.Brush> provides performance benefits over animating the <xref:System.Windows.UIElement.Opacity%2A> property of an element.</span></span>  
  
 <span data-ttu-id="ea3cf-108">Dans l’exemple suivant, deux boutons sont animés de sorte qu’elles disparaissent et.</span><span class="sxs-lookup"><span data-stu-id="ea3cf-108">In the following example, two buttons are animated so that they fade in and out of view.</span></span> <span data-ttu-id="ea3cf-109">L’opacité de la première <xref:System.Windows.Controls.Button> est animée de `1.0` à `0.0` sur un <xref:System.Windows.Media.Animation.Timeline.Duration%2A> de cinq secondes.</span><span class="sxs-lookup"><span data-stu-id="ea3cf-109">The Opacity of the first <xref:System.Windows.Controls.Button> is animated from `1.0` to `0.0` over a <xref:System.Windows.Media.Animation.Timeline.Duration%2A> of five seconds.</span></span> <span data-ttu-id="ea3cf-110">Le deuxième bouton est également animé, mais l’opacité de SolidColorBrush utilisé pour peindre son <xref:System.Windows.Controls.Control.Background%2A> est animée au lieu de l’opacité du bouton entier.</span><span class="sxs-lookup"><span data-stu-id="ea3cf-110">The second button is also animated, but the Opacity of the SolidColorBrush used to paint its <xref:System.Windows.Controls.Control.Background%2A> is animated rather than the opacity of the entire button.</span></span> <span data-ttu-id="ea3cf-111">Lorsque l’exemple est exécuté, le premier bouton atténue complètement, et pendant que l’arrière-plan du deuxième bouton en fondu et.</span><span class="sxs-lookup"><span data-stu-id="ea3cf-111">When the example is run, the first button completely fades in and out of view, while only the background of the second button fades in and out of view.</span></span> <span data-ttu-id="ea3cf-112">Son texte et sa bordure restent entièrement opaques.</span><span class="sxs-lookup"><span data-stu-id="ea3cf-112">Its text and border remain fully opaque.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ea3cf-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="ea3cf-113">Example</span></span>  
 [!code-xaml[timingbehaviors_snip#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/OpacityAnimationExample.xaml#10)]  
  
 <span data-ttu-id="ea3cf-114">Code a été omis de cet exemple.</span><span class="sxs-lookup"><span data-stu-id="ea3cf-114">Code has been omitted from this example.</span></span> <span data-ttu-id="ea3cf-115">L’exemple complet montre également comment animer l’opacité d’un <xref:System.Windows.Media.Color> au sein d’un <xref:System.Windows.Media.LinearGradientBrush>.</span><span class="sxs-lookup"><span data-stu-id="ea3cf-115">The full sample also shows how to animate the opacity of a <xref:System.Windows.Media.Color> within a <xref:System.Windows.Media.LinearGradientBrush>.</span></span>  <span data-ttu-id="ea3cf-116">Pour l’exemple complet, consultez la [animation de l’opacité d’un élément, exemple](http://go.microsoft.com/fwlink/?LinkID=159968).</span><span class="sxs-lookup"><span data-stu-id="ea3cf-116">For the full sample, see the [Animating the Opacity of an Element Sample](http://go.microsoft.com/fwlink/?LinkID=159968).</span></span>
