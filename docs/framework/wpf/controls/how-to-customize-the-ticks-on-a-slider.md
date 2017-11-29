---
title: "Comment : personnaliser les graduations sur un curseur"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- TickBar [WPF]
- Slider control [WPF], creating with TickBar
ms.assetid: 4fa694f2-a620-4b15-be78-5f4286f89361
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5d266d85e10ca8e77cd32338096cf3a3b761c188
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-customize-the-ticks-on-a-slider"></a><span data-ttu-id="02261-102">Comment : personnaliser les graduations sur un curseur</span><span class="sxs-lookup"><span data-stu-id="02261-102">How to: Customize the Ticks on a Slider</span></span>
<span data-ttu-id="02261-103">Cet exemple montre comment créer un <xref:System.Windows.Controls.Slider> contrôle qui a des graduations.</span><span class="sxs-lookup"><span data-stu-id="02261-103">This example shows how to create a <xref:System.Windows.Controls.Slider> control that has tick marks.</span></span>  
  
## <a name="example"></a><span data-ttu-id="02261-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="02261-104">Example</span></span>  
 <span data-ttu-id="02261-105">Le <xref:System.Windows.Controls.Primitives.TickBar> s’affiche lorsque vous définissez la <xref:System.Windows.Controls.Slider.TickPlacement%2A> propriété à une valeur autre que <xref:System.Windows.Controls.Primitives.TickPlacement.None>, qui est la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="02261-105">The <xref:System.Windows.Controls.Primitives.TickBar> displays when you set the <xref:System.Windows.Controls.Slider.TickPlacement%2A> property to a value other than <xref:System.Windows.Controls.Primitives.TickPlacement.None>, which is the default value.</span></span>  
  
 <span data-ttu-id="02261-106">L’exemple suivant montre comment créer un <xref:System.Windows.Controls.Slider> avec un <xref:System.Windows.Controls.Primitives.TickBar> affiche les marques de graduation.</span><span class="sxs-lookup"><span data-stu-id="02261-106">The following example shows how to create a <xref:System.Windows.Controls.Slider> with a <xref:System.Windows.Controls.Primitives.TickBar> that displays tick marks.</span></span> <span data-ttu-id="02261-107">Le <xref:System.Windows.Controls.Slider.TickPlacement%2A> et <xref:System.Windows.Controls.Slider.TickFrequency%2A> propriétés définissent l’emplacement des graduations et l’intervalle entre eux.</span><span class="sxs-lookup"><span data-stu-id="02261-107">The <xref:System.Windows.Controls.Slider.TickPlacement%2A> and <xref:System.Windows.Controls.Slider.TickFrequency%2A> properties define the location of the tick marks and the interval between them.</span></span> <span data-ttu-id="02261-108">Lorsque vous déplacez le <xref:System.Windows.Controls.Primitives.Thumb>, info-bulles affichent la valeur de la <xref:System.Windows.Controls.Slider>.</span><span class="sxs-lookup"><span data-stu-id="02261-108">When you move the <xref:System.Windows.Controls.Primitives.Thumb>, tooltips display the value of the <xref:System.Windows.Controls.Slider>.</span></span> <span data-ttu-id="02261-109">Le <xref:System.Windows.Controls.Slider.AutoToolTipPlacement%2A> propriété définit où les info-bulles s’affichent.</span><span class="sxs-lookup"><span data-stu-id="02261-109">The <xref:System.Windows.Controls.Slider.AutoToolTipPlacement%2A> property defines where the tooltips occur.</span></span> <span data-ttu-id="02261-110">Le <xref:System.Windows.Controls.Primitives.Thumb> mouvements correspondent à l’emplacement des graduations car <xref:System.Windows.Controls.Slider.IsSnapToTickEnabled%2A> a la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="02261-110">The <xref:System.Windows.Controls.Primitives.Thumb> movements correspond to the location of the tick marks because <xref:System.Windows.Controls.Slider.IsSnapToTickEnabled%2A> is set to `true`.</span></span>  
  
 <span data-ttu-id="02261-111">L’exemple suivant montre comment utiliser le <xref:System.Windows.Controls.Slider.Ticks%2A> propriété pour créer des graduations le long de la <xref:System.Windows.Controls.Slider> à intervalles irréguliers.</span><span class="sxs-lookup"><span data-stu-id="02261-111">The following example shows how to use the <xref:System.Windows.Controls.Slider.Ticks%2A> property to create tick marks along the <xref:System.Windows.Controls.Slider> at irregular intervals.</span></span>  
  
 [!code-xaml[Slider#4](../../../../samples/snippets/xaml/VS_Snippets_Wpf/Slider/xaml/window1.xaml#4)]  
  
## <a name="see-also"></a><span data-ttu-id="02261-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="02261-112">See Also</span></span>  
 <xref:System.Windows.Controls.Slider>  
 <xref:System.Windows.Controls.Primitives.TickBar>  
 <xref:System.Windows.Controls.Slider.TickPlacement%2A>  
 [<span data-ttu-id="02261-113">Rubriques Comment</span><span class="sxs-lookup"><span data-stu-id="02261-113">Slider How-to Topics</span></span>](http://msdn.microsoft.com/en-us/534be86c-afb2-425d-8186-631278a9925e)
