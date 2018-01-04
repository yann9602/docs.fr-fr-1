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
ms.workload: dotnet
ms.openlocfilehash: a2066ccce28138cfecf4e0b4574d45783a9ba4ca
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-an-expander-with-a-scrollviewer"></a><span data-ttu-id="4a3b8-102">Comment : créer un Expander avec un ScrollViewer</span><span class="sxs-lookup"><span data-stu-id="4a3b8-102">How to: Create an Expander with a ScrollViewer</span></span>
<span data-ttu-id="4a3b8-103">Cet exemple montre comment créer un <xref:System.Windows.Controls.Expander> contrôle qui contient un contenu complexe, par exemple une image et du texte.</span><span class="sxs-lookup"><span data-stu-id="4a3b8-103">This example shows how to create an <xref:System.Windows.Controls.Expander> control that contains complex content, such as an image and text.</span></span> <span data-ttu-id="4a3b8-104">L’exemple joint également le contenu de la <xref:System.Windows.Controls.Expander> dans un <xref:System.Windows.Controls.ScrollViewer> contrôle.</span><span class="sxs-lookup"><span data-stu-id="4a3b8-104">The example also encloses the content of the <xref:System.Windows.Controls.Expander> in a <xref:System.Windows.Controls.ScrollViewer> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4a3b8-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="4a3b8-105">Example</span></span>  
 <span data-ttu-id="4a3b8-106">L’exemple suivant montre comment créer un <xref:System.Windows.Controls.Expander>.</span><span class="sxs-lookup"><span data-stu-id="4a3b8-106">The following example shows how to create an <xref:System.Windows.Controls.Expander>.</span></span> <span data-ttu-id="4a3b8-107">L’exemple utilise un <xref:System.Windows.Controls.Primitives.BulletDecorator> contrôle, qui contient une image et du texte, afin de définir la <xref:System.Windows.Controls.HeaderedContentControl.Header%2A>.</span><span class="sxs-lookup"><span data-stu-id="4a3b8-107">The example uses a <xref:System.Windows.Controls.Primitives.BulletDecorator> control, which contains an image and text, in order to define the <xref:System.Windows.Controls.HeaderedContentControl.Header%2A>.</span></span> <span data-ttu-id="4a3b8-108">A <xref:System.Windows.Controls.ScrollViewer> contrôle fournit une méthode pour faire défiler le contenu développé.</span><span class="sxs-lookup"><span data-stu-id="4a3b8-108">A <xref:System.Windows.Controls.ScrollViewer> control provides a method for scrolling the expanded content.</span></span>  
  
 <span data-ttu-id="4a3b8-109">Notez que l’exemple définit le <xref:System.Windows.FrameworkElement.Height%2A> propriété sur le <xref:System.Windows.Controls.ScrollViewer> au lieu de sur le contenu.</span><span class="sxs-lookup"><span data-stu-id="4a3b8-109">Note that the example sets the <xref:System.Windows.FrameworkElement.Height%2A> property on the <xref:System.Windows.Controls.ScrollViewer> instead of on the content.</span></span> <span data-ttu-id="4a3b8-110">Si le <xref:System.Windows.FrameworkElement.Height%2A> est défini sur le contenu, le <xref:System.Windows.Controls.ScrollViewer> n’autorise pas l’utilisateur de faire défiler le contenu.</span><span class="sxs-lookup"><span data-stu-id="4a3b8-110">If the <xref:System.Windows.FrameworkElement.Height%2A> is set on the content, the <xref:System.Windows.Controls.ScrollViewer> does not allow the user to scroll the content.</span></span> <span data-ttu-id="4a3b8-111">Le <xref:System.Windows.FrameworkElement.Width%2A> propriété est définie sur le <xref:System.Windows.Controls.Expander> contrôle et si ce paramètre s’applique à la <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> et au contenu développé.</span><span class="sxs-lookup"><span data-stu-id="4a3b8-111">The <xref:System.Windows.FrameworkElement.Width%2A> property is set on the <xref:System.Windows.Controls.Expander> control and this setting applies to the <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> and the expanded content.</span></span>  
  
 [!code-xaml[ExpanderRichContent#CreateExpander](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpanderRichContent/CSharp/Window1.xaml#createexpander)]  
  
 [!code-csharp[ExpanderRichContent#CreateExpanderCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpanderRichContent/CSharp/Window1.xaml.cs#createexpandercode)]  
  
## <a name="see-also"></a><span data-ttu-id="4a3b8-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4a3b8-112">See Also</span></span>  
 <xref:System.Windows.Controls.Expander>  
 [<span data-ttu-id="4a3b8-113">Vue d'ensemble de l'Expandeur</span><span class="sxs-lookup"><span data-stu-id="4a3b8-113">Expander Overview</span></span>](../../../../docs/framework/wpf/controls/expander-overview.md)  
 [<span data-ttu-id="4a3b8-114">Rubriques de guide pratique</span><span class="sxs-lookup"><span data-stu-id="4a3b8-114">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/expander-how-to-topics.md)
