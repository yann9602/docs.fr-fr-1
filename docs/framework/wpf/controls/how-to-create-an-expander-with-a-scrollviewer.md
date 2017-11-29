---
title: "Comment : créer un Expander avec un ScrollViewer"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [WPF], Expander
- ScrollViewer control [WPF], with Expander control
- Expander control [WPF], creating
- controls [WPF], ScrollViewer
ms.assetid: 2ad124d2-2406-4157-aaf2-64e067298f01
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 817fb8d04e680335aff726db84cdfb9630b4cdf4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-an-expander-with-a-scrollviewer"></a><span data-ttu-id="5e7c6-102">Comment : créer un Expander avec un ScrollViewer</span><span class="sxs-lookup"><span data-stu-id="5e7c6-102">How to: Create an Expander with a ScrollViewer</span></span>
<span data-ttu-id="5e7c6-103">Cet exemple montre comment créer un <xref:System.Windows.Controls.Expander> contrôle qui contient un contenu complexe, par exemple une image et du texte.</span><span class="sxs-lookup"><span data-stu-id="5e7c6-103">This example shows how to create an <xref:System.Windows.Controls.Expander> control that contains complex content, such as an image and text.</span></span> <span data-ttu-id="5e7c6-104">L’exemple joint également le contenu de la <xref:System.Windows.Controls.Expander> dans un <xref:System.Windows.Controls.ScrollViewer> contrôle.</span><span class="sxs-lookup"><span data-stu-id="5e7c6-104">The example also encloses the content of the <xref:System.Windows.Controls.Expander> in a <xref:System.Windows.Controls.ScrollViewer> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5e7c6-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="5e7c6-105">Example</span></span>  
 <span data-ttu-id="5e7c6-106">L’exemple suivant montre comment créer un <xref:System.Windows.Controls.Expander>.</span><span class="sxs-lookup"><span data-stu-id="5e7c6-106">The following example shows how to create an <xref:System.Windows.Controls.Expander>.</span></span> <span data-ttu-id="5e7c6-107">L’exemple utilise un <xref:System.Windows.Controls.Primitives.BulletDecorator> contrôle, qui contient une image et du texte, afin de définir la <xref:System.Windows.Controls.HeaderedContentControl.Header%2A>.</span><span class="sxs-lookup"><span data-stu-id="5e7c6-107">The example uses a <xref:System.Windows.Controls.Primitives.BulletDecorator> control, which contains an image and text, in order to define the <xref:System.Windows.Controls.HeaderedContentControl.Header%2A>.</span></span> <span data-ttu-id="5e7c6-108">A <xref:System.Windows.Controls.ScrollViewer> contrôle fournit une méthode pour faire défiler le contenu développé.</span><span class="sxs-lookup"><span data-stu-id="5e7c6-108">A <xref:System.Windows.Controls.ScrollViewer> control provides a method for scrolling the expanded content.</span></span>  
  
 <span data-ttu-id="5e7c6-109">Notez que l’exemple définit le <xref:System.Windows.FrameworkElement.Height%2A> propriété sur le <xref:System.Windows.Controls.ScrollViewer> au lieu de sur le contenu.</span><span class="sxs-lookup"><span data-stu-id="5e7c6-109">Note that the example sets the <xref:System.Windows.FrameworkElement.Height%2A> property on the <xref:System.Windows.Controls.ScrollViewer> instead of on the content.</span></span> <span data-ttu-id="5e7c6-110">Si le <xref:System.Windows.FrameworkElement.Height%2A> est défini sur le contenu, le <xref:System.Windows.Controls.ScrollViewer> n’autorise pas l’utilisateur de faire défiler le contenu.</span><span class="sxs-lookup"><span data-stu-id="5e7c6-110">If the <xref:System.Windows.FrameworkElement.Height%2A> is set on the content, the <xref:System.Windows.Controls.ScrollViewer> does not allow the user to scroll the content.</span></span> <span data-ttu-id="5e7c6-111">Le <xref:System.Windows.FrameworkElement.Width%2A> propriété est définie sur le <xref:System.Windows.Controls.Expander> contrôle et si ce paramètre s’applique à la <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> et au contenu développé.</span><span class="sxs-lookup"><span data-stu-id="5e7c6-111">The <xref:System.Windows.FrameworkElement.Width%2A> property is set on the <xref:System.Windows.Controls.Expander> control and this setting applies to the <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> and the expanded content.</span></span>  
  
 [!code-xaml[ExpanderRichContent#CreateExpander](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpanderRichContent/CSharp/Window1.xaml#createexpander)]  
  
 [!code-csharp[ExpanderRichContent#CreateExpanderCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpanderRichContent/CSharp/Window1.xaml.cs#createexpandercode)]  
  
## <a name="see-also"></a><span data-ttu-id="5e7c6-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5e7c6-112">See Also</span></span>  
 <xref:System.Windows.Controls.Expander>  
 [<span data-ttu-id="5e7c6-113">Vue d'ensemble de l'Expandeur</span><span class="sxs-lookup"><span data-stu-id="5e7c6-113">Expander Overview</span></span>](../../../../docs/framework/wpf/controls/expander-overview.md)  
 [<span data-ttu-id="5e7c6-114">Rubriques de guide pratique</span><span class="sxs-lookup"><span data-stu-id="5e7c6-114">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/expander-how-to-topics.md)
