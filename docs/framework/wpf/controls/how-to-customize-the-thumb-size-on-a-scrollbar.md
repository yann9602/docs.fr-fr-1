---
title: "Comment : personnaliser la taille du curseur sur une barre de défilement"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ScrollBar control [WPF]
- customizing thumb size [WPF]
- thumb size [WPF]
ms.assetid: fa32b866-5ca1-4e73-85e7-2ac64b80d194
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c550aa425eedf4b434e061f05326bf6a6de91f9d
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-customize-the-thumb-size-on-a-scrollbar"></a><span data-ttu-id="b4de7-102">Comment : personnaliser la taille du curseur sur une barre de défilement</span><span class="sxs-lookup"><span data-stu-id="b4de7-102">How to: Customize the Thumb Size on a ScrollBar</span></span>
<span data-ttu-id="b4de7-103">Cette rubrique explique comment définir la <xref:System.Windows.Controls.Primitives.Thumb> d’un <xref:System.Windows.Controls.Primitives.ScrollBar> à une taille fixe et comment spécifier une taille minimale pour le <xref:System.Windows.Controls.Primitives.Thumb> d’un <xref:System.Windows.Controls.Primitives.ScrollBar>.</span><span class="sxs-lookup"><span data-stu-id="b4de7-103">This topic explains how to set the <xref:System.Windows.Controls.Primitives.Thumb> of a <xref:System.Windows.Controls.Primitives.ScrollBar> to a fixed size and how to specify a minimum size for the <xref:System.Windows.Controls.Primitives.Thumb> of a <xref:System.Windows.Controls.Primitives.ScrollBar>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b4de7-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="b4de7-104">Example</span></span>  
  
## <a name="description"></a><span data-ttu-id="b4de7-105">Description</span><span class="sxs-lookup"><span data-stu-id="b4de7-105">Description</span></span>  
 <span data-ttu-id="b4de7-106">L’exemple suivant crée un <xref:System.Windows.Controls.Primitives.ScrollBar> qui a un <xref:System.Windows.Controls.Primitives.Thumb> avec une taille fixe.</span><span class="sxs-lookup"><span data-stu-id="b4de7-106">The following example creates a <xref:System.Windows.Controls.Primitives.ScrollBar> that has a <xref:System.Windows.Controls.Primitives.Thumb> with a fixed size.</span></span> <span data-ttu-id="b4de7-107">L’exemple définit le <xref:System.Windows.Controls.Primitives.Track.ViewportSize%2A> propriété de la <xref:System.Windows.Controls.Primitives.Thumb> à <xref:System.Double.NaN> et définit la hauteur de la <xref:System.Windows.Controls.Primitives.Thumb>.</span><span class="sxs-lookup"><span data-stu-id="b4de7-107">The example sets the <xref:System.Windows.Controls.Primitives.Track.ViewportSize%2A> property of the <xref:System.Windows.Controls.Primitives.Thumb> to <xref:System.Double.NaN> and sets the height of the <xref:System.Windows.Controls.Primitives.Thumb>.</span></span>  <span data-ttu-id="b4de7-108">Pour créer une horizontale <xref:System.Windows.Controls.Primitives.ScrollBar> avec un <xref:System.Windows.Controls.Primitives.Thumb> qui a une largeur fixe, définissez la largeur de la <xref:System.Windows.Controls.Primitives.Thumb>.</span><span class="sxs-lookup"><span data-stu-id="b4de7-108">To create a horizontal <xref:System.Windows.Controls.Primitives.ScrollBar> with a <xref:System.Windows.Controls.Primitives.Thumb> that has a fixed width, set the width of the <xref:System.Windows.Controls.Primitives.Thumb>.</span></span>  
  
## <a name="code"></a><span data-ttu-id="b4de7-109">Code</span><span class="sxs-lookup"><span data-stu-id="b4de7-109">Code</span></span>  
 [!code-xaml[ScrollBarCustomThumbSize#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ScrollBarCustomThumbSize/CS/Window1.xaml#1)]  
  
## <a name="description"></a><span data-ttu-id="b4de7-110">Description</span><span class="sxs-lookup"><span data-stu-id="b4de7-110">Description</span></span>  
 <span data-ttu-id="b4de7-111">L’exemple suivant crée un <xref:System.Windows.Controls.Primitives.ScrollBar> qui a un <xref:System.Windows.Controls.Primitives.Thumb> avec une taille minimale.</span><span class="sxs-lookup"><span data-stu-id="b4de7-111">The following example creates a <xref:System.Windows.Controls.Primitives.ScrollBar> that has a <xref:System.Windows.Controls.Primitives.Thumb> with a minimum size.</span></span> <span data-ttu-id="b4de7-112">L’exemple définit la valeur de <xref:System.Windows.SystemParameters.VerticalScrollBarButtonHeightKey%2A>.</span><span class="sxs-lookup"><span data-stu-id="b4de7-112">The example sets the value of <xref:System.Windows.SystemParameters.VerticalScrollBarButtonHeightKey%2A>.</span></span> <span data-ttu-id="b4de7-113">Pour créer une horizontale <xref:System.Windows.Controls.Primitives.ScrollBar> avec un <xref:System.Windows.Controls.Primitives.Thumb> qui a une largeur minimum, définissez la <xref:System.Windows.SystemParameters.HorizontalScrollBarButtonWidthKey%2A>.</span><span class="sxs-lookup"><span data-stu-id="b4de7-113">To create a horizontal <xref:System.Windows.Controls.Primitives.ScrollBar> with a <xref:System.Windows.Controls.Primitives.Thumb> that has a minimum width, set the <xref:System.Windows.SystemParameters.HorizontalScrollBarButtonWidthKey%2A>.</span></span>  
  
## <a name="code"></a><span data-ttu-id="b4de7-114">Code</span><span class="sxs-lookup"><span data-stu-id="b4de7-114">Code</span></span>  
 [!code-xaml[ScrollBarCustomThumbSize#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ScrollBarCustomThumbSize/CS/Window1.xaml#2)]  
  
## <a name="see-also"></a><span data-ttu-id="b4de7-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b4de7-115">See Also</span></span>  
 [<span data-ttu-id="b4de7-116">Styles et modèles ScrollBar</span><span class="sxs-lookup"><span data-stu-id="b4de7-116">ScrollBar Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/scrollbar-styles-and-templates.md)
