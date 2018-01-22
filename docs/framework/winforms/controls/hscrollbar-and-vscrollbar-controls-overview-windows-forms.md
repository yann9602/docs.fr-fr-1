---
title: "Vue d'ensemble des contrôles HScrollBar et VScrollBar (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- HScrollBar
- VScrollBar
helpviewer_keywords:
- ScrollBar control [Windows Forms]
- HScrollBar control [Windows Forms], about HScrollBar
- VScrollBar control [Windows Forms], about VScrollBar control
- ScrollBar control [Windows Forms], about ScrollBar control
- scroll bars [Windows Forms], about scroll bars
ms.assetid: 8b307679-1cae-41d8-99aa-3d1efd207cd6
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8fbdb3778959d1691200cde49e485d8a63c6e645
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="hscrollbar-and-vscrollbar-controls-overview-windows-forms"></a><span data-ttu-id="53c05-102">Vue d'ensemble des contrôles HScrollBar et VScrollBar (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="53c05-102">HScrollBar and VScrollBar Controls Overview (Windows Forms)</span></span>
<span data-ttu-id="53c05-103">Windows Forms <xref:System.Windows.Forms.ScrollBar> contrôles sont utilisés pour fournir une navigation facile dans une longue liste d’éléments ou une grande quantité d’informations en faisant défiler horizontalement ou verticalement dans une application ou un contrôle.</span><span class="sxs-lookup"><span data-stu-id="53c05-103">Windows Forms <xref:System.Windows.Forms.ScrollBar> controls are used to provide easy navigation through a long list of items or a large amount of information by scrolling either horizontally or vertically within an application or control.</span></span> <span data-ttu-id="53c05-104">Barres de défilement sont un élément courant de l’interface Windows, afin que la <xref:System.Windows.Forms.ScrollBar> contrôle est souvent utilisé avec des contrôles qui ne dérivent pas de la <xref:System.Windows.Forms.ScrollableControl> classe.</span><span class="sxs-lookup"><span data-stu-id="53c05-104">Scroll bars are a common element of the Windows interface, so the <xref:System.Windows.Forms.ScrollBar> control is often used with controls that do not derive from the <xref:System.Windows.Forms.ScrollableControl> class.</span></span> <span data-ttu-id="53c05-105">De même, de nombreux développeurs choisissent d’incorporer le <xref:System.Windows.Forms.ScrollBar> contrôler lors de la création de leurs propres contrôles utilisateur.</span><span class="sxs-lookup"><span data-stu-id="53c05-105">Similarly, many developers choose to incorporate the <xref:System.Windows.Forms.ScrollBar> control when authoring their own user controls.</span></span>  
  
 <span data-ttu-id="53c05-106">Le <xref:System.Windows.Forms.HScrollBar> (horizontale) et <xref:System.Windows.Forms.VScrollBar> contrôles (verticales) fonctionnent indépendamment des autres contrôles et ont leur propre ensemble de méthodes, propriétés et événements.</span><span class="sxs-lookup"><span data-stu-id="53c05-106">The <xref:System.Windows.Forms.HScrollBar> (horizontal) and <xref:System.Windows.Forms.VScrollBar> (vertical) controls operate independently from other controls and have their own set of events, properties, and methods.</span></span> <span data-ttu-id="53c05-107"><xref:System.Windows.Forms.ScrollBar>les contrôles ne sont pas le même que les barres de défilement intégrées qui sont attachés à des zones de texte, zones de liste, zones de liste déroulante ou formulaires MDI (le <xref:System.Windows.Forms.TextBox> contrôle a un <xref:System.Windows.Forms.TextBox.ScrollBars%2A> propriété pour afficher ou masquer les barres de défilement qui sont attachés au contrôle).</span><span class="sxs-lookup"><span data-stu-id="53c05-107"><xref:System.Windows.Forms.ScrollBar> controls are not the same as the built-in scroll bars that are attached to text boxes, list boxes, combo boxes, or MDI forms (the <xref:System.Windows.Forms.TextBox> control has a <xref:System.Windows.Forms.TextBox.ScrollBars%2A> property to show or hide scroll bars that are attached to the control).</span></span>  
  
 <span data-ttu-id="53c05-108">Le <xref:System.Windows.Forms.ScrollBar> contrôles utilisent le <xref:System.Windows.Forms.ScrollBar.Scroll> événement pour surveiller le mouvement de la case de défilement (parfois appelé curseur) le long de la barre de défilement.</span><span class="sxs-lookup"><span data-stu-id="53c05-108">The <xref:System.Windows.Forms.ScrollBar> controls use the <xref:System.Windows.Forms.ScrollBar.Scroll> event to monitor the movement of the scroll box (sometimes referred to as the thumb) along the scroll bar.</span></span> <span data-ttu-id="53c05-109">À l’aide de la <xref:System.Windows.Forms.ScrollBar.Scroll> événement fournit l’accès à la valeur de barre de défilement pendant qu’il est glissé.</span><span class="sxs-lookup"><span data-stu-id="53c05-109">Using the <xref:System.Windows.Forms.ScrollBar.Scroll> event provides access to the scroll bar value as it is being dragged.</span></span>  
  
## <a name="value-property"></a><span data-ttu-id="53c05-110">Propriété Value</span><span class="sxs-lookup"><span data-stu-id="53c05-110">Value Property</span></span>  
 <span data-ttu-id="53c05-111">Le <xref:System.Windows.Forms.ScrollBar.Value%2A> propriété (c'est-à-dire, par défaut, 0) est un `integer` valeur correspondant à la position de la case de défilement dans la barre de défilement.</span><span class="sxs-lookup"><span data-stu-id="53c05-111">The <xref:System.Windows.Forms.ScrollBar.Value%2A> property (which, by default, is 0) is an `integer` value corresponding to the position of the scroll box in the scroll bar.</span></span> <span data-ttu-id="53c05-112">Lorsque le déplacement du curseur est à la valeur minimale, il le déplace à la position la plus à gauche (pour les barres de défilement horizontale) ou à la position supérieure (pour les barres de défilement verticale).</span><span class="sxs-lookup"><span data-stu-id="53c05-112">When the scroll box position is at the minimum value, it moves to the left-most position (for horizontal scroll bars) or the top position (for vertical scroll bars).</span></span> <span data-ttu-id="53c05-113">Lorsque la case de défilement est à la valeur maximale, le défilement se place à la plus à droite ou bas.</span><span class="sxs-lookup"><span data-stu-id="53c05-113">When the scroll box is at the maximum value, the scroll box moves to the right-most or bottom position.</span></span> <span data-ttu-id="53c05-114">De même, une valeur à mi-chemin entre le bas et haut de gamme place la pointe de la case de défilement au milieu de la barre de défilement.</span><span class="sxs-lookup"><span data-stu-id="53c05-114">Similarly, a value halfway between the bottom and top of the range places the leading edge of the scroll box in the middle of the scroll bar.</span></span>  
  
 <span data-ttu-id="53c05-115">En plus de modifier la valeur de barre de défilement à l’aide de clics de souris, un utilisateur peut également faire glisser la case de défilement à n’importe quel point le long de la barre.</span><span class="sxs-lookup"><span data-stu-id="53c05-115">In addition to using mouse clicks to change the scroll bar value, a user can also drag the scroll box to any point along the bar.</span></span> <span data-ttu-id="53c05-116">La valeur résultante dépend de la position du curseur de défilement, mais il est toujours dans la plage de la <xref:System.Windows.Forms.ScrollBar.Minimum%2A> à <xref:System.Windows.Forms.ScrollBar.Maximum%2A> propriétés définies par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="53c05-116">The resulting value depends on the position of the scroll box, but it is always within the range of the <xref:System.Windows.Forms.ScrollBar.Minimum%2A> to <xref:System.Windows.Forms.ScrollBar.Maximum%2A> properties set by the user.</span></span>  
  
## <a name="largechange-and-smallchange-properties"></a><span data-ttu-id="53c05-117">Propriétés LargeChange et SmallChange</span><span class="sxs-lookup"><span data-stu-id="53c05-117">LargeChange and SmallChange Properties</span></span>  
 <span data-ttu-id="53c05-118">Lorsque l’utilisateur appuie sur la touche PG. préc ou Pg. suiv ou clique dans la piste de barre de défilement de chaque côté de la case de défilement, le <xref:System.Windows.Forms.ScrollBar.Value%2A> des modifications de propriété en fonction de la valeur définie dans le <xref:System.Windows.Forms.ScrollBar.LargeChange%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="53c05-118">When the user presses the PAGE UP or PAGE DOWN key or clicks in the scroll bar track on either side of the scroll box, the <xref:System.Windows.Forms.ScrollBar.Value%2A> property changes according to the value set in the <xref:System.Windows.Forms.ScrollBar.LargeChange%2A> property.</span></span>  
  
 <span data-ttu-id="53c05-119">Lorsque l’utilisateur appuie sur l’une de la flèche de touches ou clique sur un des boutons de la barre de défilement, le <xref:System.Windows.Forms.ScrollBar.Value%2A> des modifications de propriété en fonction de la valeur définie dans le <xref:System.Windows.Forms.ScrollBar.SmallChange%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="53c05-119">When the user presses one of the arrow keys or clicks one of the scroll bar buttons, the <xref:System.Windows.Forms.ScrollBar.Value%2A> property changes according to the value set in the <xref:System.Windows.Forms.ScrollBar.SmallChange%2A> property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53c05-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="53c05-120">See Also</span></span>  
 <xref:System.Windows.Forms.HScrollBar>  
 <xref:System.Windows.Forms.VScrollBar>  
 [<span data-ttu-id="53c05-121">Ajouts dans les Windows Forms pour le .NET Framework 2.0</span><span class="sxs-lookup"><span data-stu-id="53c05-121">Additions to Windows Forms for the .NET Framework 2.0</span></span>](http://msdn.microsoft.com/library/c61a923d-3d6a-4c8c-820c-e94c83f3f9a8)  
 [<span data-ttu-id="53c05-122">Contrôles à utiliser dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="53c05-122">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
