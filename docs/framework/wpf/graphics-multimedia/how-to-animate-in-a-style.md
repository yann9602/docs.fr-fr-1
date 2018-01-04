---
title: "Comment : animer dans un style"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- animation [WPF], properties [WPF], within styles
- styles [WPF], animating properties within
ms.assetid: 6a791f3d-6b1f-4972-a2f9-35880bcfd954
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2aabe24b77a9016b5b8119646c80ea84eb73acb9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-animate-in-a-style"></a><span data-ttu-id="7d0df-102">Comment : animer dans un style</span><span class="sxs-lookup"><span data-stu-id="7d0df-102">How to: Animate in a Style</span></span>
<span data-ttu-id="7d0df-103">Cet exemple montre comment animer des propriétés dans un style.</span><span class="sxs-lookup"><span data-stu-id="7d0df-103">This example shows how to animate properties within a style.</span></span> <span data-ttu-id="7d0df-104">Lors de l’animation dans un style, seul l’élément framework pour laquelle le style est défini peut être directement ciblé.</span><span class="sxs-lookup"><span data-stu-id="7d0df-104">When animating within a style, only the framework element for which the style is defined can be targeted directly.</span></span> <span data-ttu-id="7d0df-105">Pour cibler un objet freezable, vous devez « point vers le bas » à partir d’une propriété de l’élément style.</span><span class="sxs-lookup"><span data-stu-id="7d0df-105">To target a freezable object, you must "dot down" from a property of the styled element.</span></span>  
  
 <span data-ttu-id="7d0df-106">Dans l’exemple suivant, plusieurs animations sont définies dans un style et appliquées à un <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="7d0df-106">In the following example, several animations are defined within a style and applied to a <xref:System.Windows.Controls.Button>.</span></span> <span data-ttu-id="7d0df-107">Lorsque l’utilisateur déplace la souris sur le bouton, il passe d’opaque à partiellement transparent et vice à nouveau, à plusieurs reprises.</span><span class="sxs-lookup"><span data-stu-id="7d0df-107">When the user moves the mouse over the button, it fades from opaque to partially translucent and back again, repeatedly.</span></span> <span data-ttu-id="7d0df-108">Lorsque l’utilisateur déplace la souris hors du bouton, il est complètement opaque.</span><span class="sxs-lookup"><span data-stu-id="7d0df-108">When the user moves the mouse off the button, it becomes completely opaque.</span></span> <span data-ttu-id="7d0df-109">Lorsque le bouton est activé, sa couleur d’arrière-plan passe d’orange à blanc et vice versa.</span><span class="sxs-lookup"><span data-stu-id="7d0df-109">When the button is clicked, its background color changes from orange to white and back again.</span></span> <span data-ttu-id="7d0df-110">Étant donné que la <xref:System.Windows.Media.SolidColorBrush> utilisé pour peindre le bouton ne peut pas être ciblé directement, il est accessible par pointillage au bas à partir du bouton <xref:System.Windows.Controls.Control.Background%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="7d0df-110">Because the <xref:System.Windows.Media.SolidColorBrush> used to paint the button can't be targeted directly, it is accessed by dotting down from the button's <xref:System.Windows.Controls.Control.Background%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7d0df-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="7d0df-111">Example</span></span>  
 [!code-xaml[timingbehaviors_snip#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/StyleStoryboardsExample.xaml#21)]  
  
 <span data-ttu-id="7d0df-112">Notez que lors de l’animation dans un style, il est possible de cibler des objets qui n’existent pas.</span><span class="sxs-lookup"><span data-stu-id="7d0df-112">Note that when animating within a style, it's possible to target objects that don't exist.</span></span> <span data-ttu-id="7d0df-113">Par exemple, supposons que votre style utilise un <xref:System.Windows.Media.SolidColorBrush> pour définir la propriété d’arrière-plan d’un bouton, mais à un moment donné le style est remplacé et l’arrière-plan du bouton est défini avec un <xref:System.Windows.Media.LinearGradientBrush>.</span><span class="sxs-lookup"><span data-stu-id="7d0df-113">For example, suppose your style uses a <xref:System.Windows.Media.SolidColorBrush> to set a Button's background property, but at some point the style is overridden and the button's background is set with a <xref:System.Windows.Media.LinearGradientBrush>.</span></span>  <span data-ttu-id="7d0df-114">Lors de la tentative animer la <xref:System.Windows.Media.SolidColorBrush> ne lève pas d’exception ; l’animation échouera en mode silencieux.</span><span class="sxs-lookup"><span data-stu-id="7d0df-114">Trying to animate the <xref:System.Windows.Media.SolidColorBrush> won't throw an exception; the animation will simply fail silently.</span></span>  
  
 <span data-ttu-id="7d0df-115">Pour plus d’informations sur le plan conceptuel de la syntaxe de ciblage, consultez le [Storyboards Overview](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md).</span><span class="sxs-lookup"><span data-stu-id="7d0df-115">Fore more information about storyboard targeting syntax, see the [Storyboards Overview](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md).</span></span> <span data-ttu-id="7d0df-116">Pour plus d’informations sur l’animation, consultez le [vue d’ensemble de l’Animation](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="7d0df-116">For more information about animation, see the [Animation Overview](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).</span></span> <span data-ttu-id="7d0df-117">Pour plus d’informations sur les styles, consultez le [styles et modèles](../../../../docs/framework/wpf/controls/styling-and-templating.md).</span><span class="sxs-lookup"><span data-stu-id="7d0df-117">For more information about styles, see the [Styling and Templating](../../../../docs/framework/wpf/controls/styling-and-templating.md).</span></span>
