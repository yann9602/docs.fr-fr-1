---
title: "Comment : afficher les barres de défilement dans le contrôle RichTextBox Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- text boxes [Windows Forms], displaying scroll bars
- scroll bars [Windows Forms], displaying in controls
- RichTextBox control [Windows Forms], displaying scroll bars
ms.assetid: cdeb42e1-86e8-410c-ba46-18aec264ef5f
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4645e502544072cbc6268ae07e054ea5450d9c5c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-display-scroll-bars-in-the-windows-forms-richtextbox-control"></a><span data-ttu-id="8f594-102">Comment : afficher les barres de défilement dans le contrôle RichTextBox Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8f594-102">How to: Display Scroll Bars in the Windows Forms RichTextBox Control</span></span>
<span data-ttu-id="8f594-103">Par défaut, Windows Forms <xref:System.Windows.Forms.RichTextBox> contrôle affiche des barres de défilement horizontale et verticale si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="8f594-103">By default, the Windows Forms <xref:System.Windows.Forms.RichTextBox> control displays horizontal and vertical scroll bars as necessary.</span></span> <span data-ttu-id="8f594-104">Il existe sept valeurs possibles pour le <xref:System.Windows.Forms.RichTextBox.ScrollBars%2A> propriété de la <xref:System.Windows.Forms.RichTextBox> contrôle, qui sont décrites dans le tableau ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="8f594-104">There are seven possible values for the <xref:System.Windows.Forms.RichTextBox.ScrollBars%2A> property of the <xref:System.Windows.Forms.RichTextBox> control, which are described in the table below.</span></span>  
  
### <a name="to-display-scroll-bars-in-a-richtextbox-control"></a><span data-ttu-id="8f594-105">Pour afficher les barres de défilement dans un contrôle RichTextBox</span><span class="sxs-lookup"><span data-stu-id="8f594-105">To display scroll bars in a RichTextBox control</span></span>  
  
1.  <span data-ttu-id="8f594-106">Affectez à la propriété <xref:System.Windows.Forms.RichTextBox.Multiline%2A> la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="8f594-106">Set the <xref:System.Windows.Forms.RichTextBox.Multiline%2A> property to `true`.</span></span> <span data-ttu-id="8f594-107">Aucun type de barre de défilement, y compris horizontal, n’affiche si le <xref:System.Windows.Forms.RichTextBox.Multiline%2A> est définie sur `false`.</span><span class="sxs-lookup"><span data-stu-id="8f594-107">No type of scroll bar, including horizontal, will display if the <xref:System.Windows.Forms.RichTextBox.Multiline%2A> property is set to `false`.</span></span>  
  
2.  <span data-ttu-id="8f594-108">Définir le <xref:System.Windows.Forms.RichTextBox.ScrollBars%2A> propriété une valeur appropriée de la <xref:System.Windows.Forms.RichTextBoxScrollBars> énumération.</span><span class="sxs-lookup"><span data-stu-id="8f594-108">Set the <xref:System.Windows.Forms.RichTextBox.ScrollBars%2A> property to an appropriate value of the <xref:System.Windows.Forms.RichTextBoxScrollBars> enumeration.</span></span>  
  
    |<span data-ttu-id="8f594-109">Value</span><span class="sxs-lookup"><span data-stu-id="8f594-109">Value</span></span>|<span data-ttu-id="8f594-110">Description</span><span class="sxs-lookup"><span data-stu-id="8f594-110">Description</span></span>|  
    |-----------|-----------------|  
    |<span data-ttu-id="8f594-111"><xref:System.Windows.Forms.RichTextBoxScrollBars.Both> (par défaut)</span><span class="sxs-lookup"><span data-stu-id="8f594-111"><xref:System.Windows.Forms.RichTextBoxScrollBars.Both> (default)</span></span>|<span data-ttu-id="8f594-112">Affiche des barres de défilement horizontal ou vertical, ou les deux, uniquement lorsque le texte dépasse la largeur ou la longueur du contrôle.</span><span class="sxs-lookup"><span data-stu-id="8f594-112">Displays horizontal or vertical scroll bars, or both, only when text exceeds the width or length of the control.</span></span>|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.None>|<span data-ttu-id="8f594-113">N’affiche jamais de n’importe quel type de barre de défilement.</span><span class="sxs-lookup"><span data-stu-id="8f594-113">Never displays any type of scroll bar.</span></span>|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.Horizontal>|<span data-ttu-id="8f594-114">Affiche une uniquement lorsque le texte dépasse la largeur du contrôle de barre de défilement horizontal.</span><span class="sxs-lookup"><span data-stu-id="8f594-114">Displays a horizontal scroll bar only when the text exceeds the width of the control.</span></span> <span data-ttu-id="8f594-115">(Pour ce faire, le <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> propriété doit être définie sur `false`.)</span><span class="sxs-lookup"><span data-stu-id="8f594-115">(For this to occur, the <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> property must be set to `false`.)</span></span>|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.Vertical>|<span data-ttu-id="8f594-116">Affiche une uniquement lorsque le texte dépasse la hauteur du contrôle de barre de défilement verticale.</span><span class="sxs-lookup"><span data-stu-id="8f594-116">Displays a vertical scroll bar only when the text exceeds the height of the control.</span></span>|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.ForcedHorizontal>|<span data-ttu-id="8f594-117">Lorsque la barre de défilement horizontale d’affiche le <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> est définie sur `false`.</span><span class="sxs-lookup"><span data-stu-id="8f594-117">Displays a horizontal scroll bar when the <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> property is set to `false`.</span></span> <span data-ttu-id="8f594-118">La barre de défilement apparaît grisée lorsque le texte ne dépasse pas la largeur du contrôle.</span><span class="sxs-lookup"><span data-stu-id="8f594-118">The scroll bar appears dimmed when text does not exceed the width of the control.</span></span>|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.ForcedVertical>|<span data-ttu-id="8f594-119">Affiche toujours une barre de défilement verticale.</span><span class="sxs-lookup"><span data-stu-id="8f594-119">Always displays a vertical scroll bar.</span></span> <span data-ttu-id="8f594-120">La barre de défilement apparaît grisée lorsque le texte ne dépasse pas la longueur du contrôle.</span><span class="sxs-lookup"><span data-stu-id="8f594-120">The scroll bar appears dimmed when text does not exceed the length of the control.</span></span>|  
    |<xref:System.Windows.Forms.RichTextBoxScrollBars.ForcedBoth>|<span data-ttu-id="8f594-121">Affiche toujours une barre de défilement verticale.</span><span class="sxs-lookup"><span data-stu-id="8f594-121">Always displays a vertical scrollbar.</span></span> <span data-ttu-id="8f594-122">Lorsque la barre de défilement horizontale d’affiche le <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> est définie sur `false`.</span><span class="sxs-lookup"><span data-stu-id="8f594-122">Displays a horizontal scroll bar when the <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> property is set to `false`.</span></span> <span data-ttu-id="8f594-123">Les barres de défilement sont estompées lorsque le texte ne dépasse pas la largeur ou la longueur du contrôle.</span><span class="sxs-lookup"><span data-stu-id="8f594-123">The scroll bars appear grayed when text does not exceed the width or length of the control.</span></span>|  
  
3.  <span data-ttu-id="8f594-124">Affectez à la propriété <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> une valeur appropriée.</span><span class="sxs-lookup"><span data-stu-id="8f594-124">Set the <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> property to an appropriate value.</span></span>  
  
    |<span data-ttu-id="8f594-125">Value</span><span class="sxs-lookup"><span data-stu-id="8f594-125">Value</span></span>|<span data-ttu-id="8f594-126">Description</span><span class="sxs-lookup"><span data-stu-id="8f594-126">Description</span></span>|  
    |-----------|-----------------|  
    |`false`|<span data-ttu-id="8f594-127">Texte dans le contrôle n’est pas ajustée automatiquement pour s’ajuster à la largeur du contrôle, donc il défilera vers la droite jusqu'à ce qu’un saut de ligne est atteinte.</span><span class="sxs-lookup"><span data-stu-id="8f594-127">Text in the control is not automatically adjusted to fit the width of the control, so it will scroll to the right until a line break is reached.</span></span> <span data-ttu-id="8f594-128">Utilisez cette valeur si vous avez choisi les barres de défilement horizontale ou les deux, ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="8f594-128">Use this value if you chose horizontal scroll bars or both, above.</span></span>|  
    |<span data-ttu-id="8f594-129">`true` (par défaut)</span><span class="sxs-lookup"><span data-stu-id="8f594-129">`true` (default)</span></span>|<span data-ttu-id="8f594-130">Texte dans le contrôle est automatiquement ajustée pour s’ajuster à la largeur du contrôle.</span><span class="sxs-lookup"><span data-stu-id="8f594-130">Text in the control is automatically adjusted to fit the width of the control.</span></span> <span data-ttu-id="8f594-131">La barre de défilement horizontal n’apparaître pas.</span><span class="sxs-lookup"><span data-stu-id="8f594-131">The horizontal scrollbar will not appear.</span></span> <span data-ttu-id="8f594-132">Utilisez cette valeur si vous avez choisi les barres de défilement vertical ou none, ci-dessus, pour afficher un ou plusieurs paragraphes.</span><span class="sxs-lookup"><span data-stu-id="8f594-132">Use this value if you chose vertical scroll bars or none, above, to display one or more paragraphs.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8f594-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8f594-133">See Also</span></span>  
 <xref:System.Windows.Forms.RichTextBoxScrollBars>  
 <xref:System.Windows.Forms.RichTextBox>  
 [<span data-ttu-id="8f594-134">RichTextBox, contrôle</span><span class="sxs-lookup"><span data-stu-id="8f594-134">RichTextBox Control</span></span>](../../../../docs/framework/winforms/controls/richtextbox-control-windows-forms.md)  
 [<span data-ttu-id="8f594-135">Contrôles à utiliser dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8f594-135">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
