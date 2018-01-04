---
title: "Comment : afficher des lignes multiples dans le contrôle TextBox Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- newline
- end of line
- ScrollBars property [Windows Forms], in TextBox control
- CRLF
- MultiLine property in TextBox control
- line-feed
- TextBox control [Windows Forms], viewing multiple lines
- carriage return
ms.assetid: 43173201-0b74-4067-a472-605029ca5f35
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5dca8d0f869702dee50bf851a2099317c45aa842
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-view-multiple-lines-in-the-windows-forms-textbox-control"></a><span data-ttu-id="47e71-102">Comment : afficher des lignes multiples dans le contrôle TextBox Windows Forms</span><span class="sxs-lookup"><span data-stu-id="47e71-102">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>
<span data-ttu-id="47e71-103">Par défaut, Windows Forms <xref:System.Windows.Forms.TextBox> contrôle affiche une ligne unique de texte et n’affiche pas de barres de défilement.</span><span class="sxs-lookup"><span data-stu-id="47e71-103">By default, the Windows Forms <xref:System.Windows.Forms.TextBox> control displays a single line of text and does not display scroll bars.</span></span> <span data-ttu-id="47e71-104">Si le texte est plus long que l’espace disponible, seule une partie du texte est visible.</span><span class="sxs-lookup"><span data-stu-id="47e71-104">If the text is longer than the available space, only part of the text is visible.</span></span> <span data-ttu-id="47e71-105">Vous pouvez modifier ce comportement par défaut en définissant le <xref:System.Windows.Forms.TextBox.Multiline%2A>, <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A>, et <xref:System.Windows.Forms.TextBox.ScrollBars%2A> valeurs appropriées aux propriétés.</span><span class="sxs-lookup"><span data-stu-id="47e71-105">You can change this default behavior by setting the <xref:System.Windows.Forms.TextBox.Multiline%2A>, <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A>, and <xref:System.Windows.Forms.TextBox.ScrollBars%2A> properties to appropriate values.</span></span>  
  
### <a name="to-display-a-carriage-return-in-the-textbox-control"></a><span data-ttu-id="47e71-106">Pour afficher un retour chariot dans le contrôle de zone de texte</span><span class="sxs-lookup"><span data-stu-id="47e71-106">To display a carriage return in the TextBox control</span></span>  
  
-   <span data-ttu-id="47e71-107">Pour afficher un retour chariot dans une ligne multi <xref:System.Windows.Forms.TextBox>, utilisez le <xref:System.Environment.NewLine%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="47e71-107">To display a carriage return in a multi-line <xref:System.Windows.Forms.TextBox>, use the <xref:System.Environment.NewLine%2A> property.</span></span>  
  
     <span data-ttu-id="47e71-108">N’oubliez pas que l’interprétation des caractères d’échappement (\\) est spécifique au langage.</span><span class="sxs-lookup"><span data-stu-id="47e71-108">Be aware that the interpretation of escape characters (\\) is language-specific.</span></span> <span data-ttu-id="47e71-109">Visual Basic utilise `Chr$(13) & Chr$(10)` pour la combinaison de caractères de saut de ligne et de retour chariot.</span><span class="sxs-lookup"><span data-stu-id="47e71-109">Visual Basic uses `Chr$(13) & Chr$(10)` for the carriage return and linefeed character combination.</span></span>  
  
### <a name="to-view-multiple-lines-in-the-textbox-control"></a><span data-ttu-id="47e71-110">Pour afficher plusieurs lignes dans le contrôle de zone de texte</span><span class="sxs-lookup"><span data-stu-id="47e71-110">To view multiple lines in the TextBox control</span></span>  
  
1.  <span data-ttu-id="47e71-111">Affectez à la propriété <xref:System.Windows.Forms.TextBox.Multiline%2A> la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="47e71-111">Set the <xref:System.Windows.Forms.TextBox.Multiline%2A> property to `true`.</span></span> <span data-ttu-id="47e71-112">Si <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> est `true` (la valeur par défaut), puis le texte du contrôle apparaîtra comme un ou plusieurs paragraphes ; sinon, il apparaîtra sous forme de liste dans laquelle certaines lignes peuvent être tronquées à la périphérie du contrôle.</span><span class="sxs-lookup"><span data-stu-id="47e71-112">If <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> is `true` (the default), then the text in the control will appear as one or more paragraphs; otherwise it will appear as a list, in which some lines may be clipped at the edge of the control.</span></span>  
  
2.  <span data-ttu-id="47e71-113">Affectez à la propriété <xref:System.Windows.Forms.TextBox.ScrollBars%2A> une valeur appropriée.</span><span class="sxs-lookup"><span data-stu-id="47e71-113">Set the <xref:System.Windows.Forms.TextBox.ScrollBars%2A> property to an appropriate value.</span></span>  
  
    |<span data-ttu-id="47e71-114">Value</span><span class="sxs-lookup"><span data-stu-id="47e71-114">Value</span></span>|<span data-ttu-id="47e71-115">Description</span><span class="sxs-lookup"><span data-stu-id="47e71-115">Description</span></span>|  
    |-----------|-----------------|  
    |<xref:System.Windows.Forms.ScrollBars.None>|<span data-ttu-id="47e71-116">Utilisez cette valeur si le texte est un paragraphe qui correspond presque toujours le contrôle.</span><span class="sxs-lookup"><span data-stu-id="47e71-116">Use this value if the text will be a paragraph that almost always fits the control.</span></span> <span data-ttu-id="47e71-117">L’utilisateur peut utiliser le pointeur de la souris pour vous déplacer dans le contrôle si le texte est trop long à afficher à la fois.</span><span class="sxs-lookup"><span data-stu-id="47e71-117">The user can use the mouse pointer to move around inside the control if the text is too long to display all at once.</span></span>|  
    |<xref:System.Windows.Forms.ScrollBars.Horizontal>|<span data-ttu-id="47e71-118">Utilisez cette valeur si vous souhaitez afficher une liste de lignes, dont certaines peuvent être plus longue que la largeur de la <xref:System.Windows.Forms.TextBox> contrôle.</span><span class="sxs-lookup"><span data-stu-id="47e71-118">Use this value if you want to display a list of lines, some of which may be longer than the width of the <xref:System.Windows.Forms.TextBox> control.</span></span>|  
    |<xref:System.Windows.Forms.ScrollBars.Both>|<span data-ttu-id="47e71-119">Utilisez cette valeur si la liste peut être plus longue que la hauteur du contrôle.</span><span class="sxs-lookup"><span data-stu-id="47e71-119">Use this value if the list may be longer than the height of the control.</span></span>|  
  
3.  <span data-ttu-id="47e71-120">Affectez à la propriété <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> une valeur appropriée.</span><span class="sxs-lookup"><span data-stu-id="47e71-120">Set the <xref:System.Windows.Forms.TextBoxBase.WordWrap%2A> property to an appropriate value.</span></span>  
  
    |<span data-ttu-id="47e71-121">Value</span><span class="sxs-lookup"><span data-stu-id="47e71-121">Value</span></span>|<span data-ttu-id="47e71-122">Description</span><span class="sxs-lookup"><span data-stu-id="47e71-122">Description</span></span>|  
    |-----------|-----------------|  
    |`false`|<span data-ttu-id="47e71-123">Texte dans le contrôle ne sera pas automatiquement encapsulé, donc il défilera vers la droite jusqu'à ce qu’un saut de ligne est atteinte.</span><span class="sxs-lookup"><span data-stu-id="47e71-123">Text in the control will not automatically be wrapped, so it will scroll to the right until a line break is reached.</span></span> <span data-ttu-id="47e71-124">Utilisez cette valeur si vous avez choisi <xref:System.Windows.Forms.ScrollBars.Horizontal> les barres de défilement ou <xref:System.Windows.Forms.ScrollBars.Both>, ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="47e71-124">Use this value if you chose <xref:System.Windows.Forms.ScrollBars.Horizontal> scroll bars or <xref:System.Windows.Forms.ScrollBars.Both>, above.</span></span>|  
    |<span data-ttu-id="47e71-125">`true` (par défaut)</span><span class="sxs-lookup"><span data-stu-id="47e71-125">`true` (default)</span></span>|<span data-ttu-id="47e71-126">La barre de défilement horizontal n’apparaître pas.</span><span class="sxs-lookup"><span data-stu-id="47e71-126">The horizontal scrollbar will not appear.</span></span> <span data-ttu-id="47e71-127">Utilisez cette valeur si vous avez choisi <xref:System.Windows.Forms.ScrollBars.Vertical> les barres de défilement ou <xref:System.Windows.Forms.ScrollBars.None>ci-dessus, pour afficher un ou plusieurs paragraphes.</span><span class="sxs-lookup"><span data-stu-id="47e71-127">Use this value if you chose <xref:System.Windows.Forms.ScrollBars.Vertical> scroll bars or <xref:System.Windows.Forms.ScrollBars.None>, above, to display one or more paragraphs.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="47e71-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="47e71-128">See Also</span></span>  
 <xref:System.Windows.Forms.TextBox>  
 [<span data-ttu-id="47e71-129">Vue d’ensemble du contrôle TextBox</span><span class="sxs-lookup"><span data-stu-id="47e71-129">TextBox Control Overview</span></span>](../../../../docs/framework/winforms/controls/textbox-control-overview-windows-forms.md)  
 [<span data-ttu-id="47e71-130">Guide pratique pour contrôler le point d’insertion dans un contrôle TextBox Windows Forms</span><span class="sxs-lookup"><span data-stu-id="47e71-130">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)  
 [<span data-ttu-id="47e71-131">Guide pratique pour créer une zone de texte pour mot de passe avec le contrôle TextBox Windows Forms</span><span class="sxs-lookup"><span data-stu-id="47e71-131">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)  
 [<span data-ttu-id="47e71-132">Guide pratique pour créer une zone de texte en lecture seule</span><span class="sxs-lookup"><span data-stu-id="47e71-132">How to: Create a Read-Only Text Box</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-read-only-text-box-windows-forms.md)  
 [<span data-ttu-id="47e71-133">Guide pratique pour insérer des guillemets dans une chaîne</span><span class="sxs-lookup"><span data-stu-id="47e71-133">How to: Put Quotation Marks in a String</span></span>](../../../../docs/framework/winforms/controls/how-to-put-quotation-marks-in-a-string-windows-forms.md)  
 [<span data-ttu-id="47e71-134">Guide pratique pour sélectionner du texte dans le contrôle TextBox Windows Forms</span><span class="sxs-lookup"><span data-stu-id="47e71-134">How to: Select Text in the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-select-text-in-the-windows-forms-textbox-control.md)  
 [<span data-ttu-id="47e71-135">TextBox, contrôle</span><span class="sxs-lookup"><span data-stu-id="47e71-135">TextBox Control</span></span>](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)
