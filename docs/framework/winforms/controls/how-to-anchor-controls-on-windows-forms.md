---
title: "Comment : ancrer des contrôles aux Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Anchor property [Windows Forms], enabling resizable forms
- Windows Forms controls, screen resolutions
- resizing forms [Windows Forms]
- Windows Forms controls, size
- screen resolution and control display
- controls [Windows Forms], anchoring
- forms [Windows Forms], resizing
- Windows Forms, resizing
- controls [Windows Forms], positioning
ms.assetid: 59ea914f-fbd3-427a-80fe-decd02f7ae6d
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7fcc672dea63bc74980b4829129f530de9cc72ec
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-anchor-controls-on-windows-forms"></a><span data-ttu-id="ce2b6-102">Comment : ancrer des contrôles aux Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ce2b6-102">How to: Anchor Controls on Windows Forms</span></span>
<span data-ttu-id="ce2b6-103">Si vous concevez un formulaire de l’utilisateur peut redimensionner au moment de l’exécution, les contrôles sur votre formulaire doivent redimensionner et repositionner correctement.</span><span class="sxs-lookup"><span data-stu-id="ce2b6-103">If you are designing a form that the user can resize at run time, the controls on your form should resize and reposition properly.</span></span> <span data-ttu-id="ce2b6-104">Pour redimensionner dynamiquement les contrôles dans le formulaire, vous pouvez utiliser le <xref:System.Windows.Forms.Control.Anchor%2A> propriété des contrôles Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="ce2b6-104">To resize controls dynamically with the form, you can use the <xref:System.Windows.Forms.Control.Anchor%2A> property of Windows Forms controls.</span></span> <span data-ttu-id="ce2b6-105">Le <xref:System.Windows.Forms.Control.Anchor%2A> propriété définit la position d’ancrage d’un pour le contrôle.</span><span class="sxs-lookup"><span data-stu-id="ce2b6-105">The <xref:System.Windows.Forms.Control.Anchor%2A> property defines an anchor position for the control.</span></span> <span data-ttu-id="ce2b6-106">Lorsqu’un contrôle est ancré à un formulaire et le formulaire est redimensionné, le contrôle gère la distance entre le contrôle et les positions d’ancrage.</span><span class="sxs-lookup"><span data-stu-id="ce2b6-106">When a control is anchored to a form and the form is resized, the control maintains the distance between the control and the anchor positions.</span></span> <span data-ttu-id="ce2b6-107">Par exemple, si vous avez un <xref:System.Windows.Forms.TextBox> contrôle est ancré à la gauche, droite et inférieure du formulaire, comme le formulaire est redimensionné, le <xref:System.Windows.Forms.TextBox> contrôle est redimensionné horizontalement pour qu’il conserve la même distance des bords droit et gauche de l’écran.</span><span class="sxs-lookup"><span data-stu-id="ce2b6-107">For example, if you have a <xref:System.Windows.Forms.TextBox> control that is anchored to the left, right, and bottom edges of the form, as the form is resized, the <xref:System.Windows.Forms.TextBox> control resizes horizontally so that it maintains the same distance from the right and left sides of the form.</span></span> <span data-ttu-id="ce2b6-108">En outre, le contrôle se positionne verticalement afin que son emplacement est toujours la même distance entre le bord inférieur de l’écran.</span><span class="sxs-lookup"><span data-stu-id="ce2b6-108">In addition, the control positions itself vertically so that its location is always the same distance from the bottom edge of the form.</span></span> <span data-ttu-id="ce2b6-109">Si un contrôle n’est pas ancré et le formulaire est redimensionné, la position du contrôle par rapport aux bords du formulaire est modifiée.</span><span class="sxs-lookup"><span data-stu-id="ce2b6-109">If a control is not anchored and the form is resized, the position of the control relative to the edges of the form is changed.</span></span>  
  
 <span data-ttu-id="ce2b6-110">Le <xref:System.Windows.Forms.Control.Anchor%2A> propriété interagit avec le <xref:System.Windows.Forms.Control.AutoSize%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="ce2b6-110">The <xref:System.Windows.Forms.Control.Anchor%2A> property interacts with the <xref:System.Windows.Forms.Control.AutoSize%2A> property.</span></span> <span data-ttu-id="ce2b6-111">Pour plus d’informations, consultez [vue d’ensemble de la propriété AutoSize](../../../../docs/framework/winforms/controls/autosize-property-overview.md).</span><span class="sxs-lookup"><span data-stu-id="ce2b6-111">For more information, see [AutoSize Property Overview](../../../../docs/framework/winforms/controls/autosize-property-overview.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ce2b6-112">Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.</span><span class="sxs-lookup"><span data-stu-id="ce2b6-112">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="ce2b6-113">Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** .</span><span class="sxs-lookup"><span data-stu-id="ce2b6-113">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="ce2b6-114">Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="ce2b6-114">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-anchor-a-control-on-a-form"></a><span data-ttu-id="ce2b6-115">Pour ancrer un contrôle sur un formulaire</span><span class="sxs-lookup"><span data-stu-id="ce2b6-115">To anchor a control on a form</span></span>  
  
1.  <span data-ttu-id="ce2b6-116">Sélectionnez le contrôle que vous souhaitez ancrer.</span><span class="sxs-lookup"><span data-stu-id="ce2b6-116">Select the control you want to anchor.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ce2b6-117">Vous pouvez ancrer plusieurs contrôles simultanément en appuyant sur la touche CTRL ENFONCÉE, en cliquant sur chaque contrôle pour le sélectionner, puis en suivant le reste de cette procédure.</span><span class="sxs-lookup"><span data-stu-id="ce2b6-117">You can anchor multiple controls simultaneously by pressing the CTRL key, clicking each control to select it, and then following the rest of this procedure.</span></span>  
  
2.  <span data-ttu-id="ce2b6-118">Dans le **propriétés** fenêtre, cliquez sur la flèche située à droite de la <xref:System.Windows.Forms.Control.Anchor%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="ce2b6-118">In the **Properties** window, click the arrow to the right of the <xref:System.Windows.Forms.Control.Anchor%2A> property.</span></span>  
  
     <span data-ttu-id="ce2b6-119">Un éditeur s’affiche qui indique une croix.</span><span class="sxs-lookup"><span data-stu-id="ce2b6-119">An editor is displayed that shows a cross.</span></span>  
  
3.  <span data-ttu-id="ce2b6-120">Pour définir un point d’ancrage, cliquez sur le coin supérieur gauche, droite ou section inférieure de la croix.</span><span class="sxs-lookup"><span data-stu-id="ce2b6-120">To set an anchor, click the top, left, right, or bottom section of the cross.</span></span>  
  
     <span data-ttu-id="ce2b6-121">Les contrôles sont ancrés vers le haut et gauche par défaut.</span><span class="sxs-lookup"><span data-stu-id="ce2b6-121">Controls are anchored to the top and left by default.</span></span>  
  
4.  <span data-ttu-id="ce2b6-122">Pour effacer un côté du contrôle qui a été ancré, cliquez sur cette branche de la croix.</span><span class="sxs-lookup"><span data-stu-id="ce2b6-122">To clear a side of the control that has been anchored, click that arm of the cross.</span></span>  
  
5.  <span data-ttu-id="ce2b6-123">Pour fermer la <xref:System.Windows.Forms.Control.Anchor%2A> éditeur de propriétés, cliquez sur le <xref:System.Windows.Forms.Control.Anchor%2A> nom de la propriété à nouveau.</span><span class="sxs-lookup"><span data-stu-id="ce2b6-123">To close the <xref:System.Windows.Forms.Control.Anchor%2A> property editor, click the <xref:System.Windows.Forms.Control.Anchor%2A> property name again.</span></span>  
  
 <span data-ttu-id="ce2b6-124">Lorsque votre formulaire est affiché au moment de l’exécution, le contrôle est redimensionné pour rester à la même distance entre le bord de l’écran.</span><span class="sxs-lookup"><span data-stu-id="ce2b6-124">When your form is displayed at run time, the control resizes to remain positioned at the same distance from the edge of the form.</span></span> <span data-ttu-id="ce2b6-125">La distance entre le bord ancré reste toujours la même que la distance définie lorsque le contrôle se trouve dans le Concepteur Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="ce2b6-125">The distance from the anchored edge always remains the same as the distance defined when the control is positioned in the Windows Forms Designer.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ce2b6-126">Certains contrôles, tels que le <xref:System.Windows.Forms.ComboBox> , possèdent une limite de hauteur.</span><span class="sxs-lookup"><span data-stu-id="ce2b6-126">Certain controls, such as the <xref:System.Windows.Forms.ComboBox> control, have a limit to their height.</span></span> <span data-ttu-id="ce2b6-127">Ancrer le contrôle vers le bas de sa forme ou un conteneur ne peut pas forcer le contrôle dépasse sa limite de hauteur.</span><span class="sxs-lookup"><span data-stu-id="ce2b6-127">Anchoring the control to the bottom of its form or container cannot force the control to exceed its height limit.</span></span>  
  
 <span data-ttu-id="ce2b6-128">Les contrôles hérités doivent être `Protected` pour pouvoir être ancrés.</span><span class="sxs-lookup"><span data-stu-id="ce2b6-128">Inherited controls must be `Protected` to be able to be anchored.</span></span> <span data-ttu-id="ce2b6-129">Pour modifier le niveau d’accès d’un contrôle, définissez son `Modifiers` propriété dans le **propriétés** fenêtre.</span><span class="sxs-lookup"><span data-stu-id="ce2b6-129">To change the access level of a control, set its `Modifiers` property in the **Properties** window.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce2b6-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ce2b6-130">See Also</span></span>  
 [<span data-ttu-id="ce2b6-131">Contrôles Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ce2b6-131">Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/index.md)  
 [<span data-ttu-id="ce2b6-132">Disposition des contrôles dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ce2b6-132">Arranging Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)  
 [<span data-ttu-id="ce2b6-133">Vue d’ensemble de la propriété AutoSize</span><span class="sxs-lookup"><span data-stu-id="ce2b6-133">AutoSize Property Overview</span></span>](../../../../docs/framework/winforms/controls/autosize-property-overview.md)  
 [<span data-ttu-id="ce2b6-134">Guide pratique pour fixer des contrôles sur des Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ce2b6-134">How to: Dock Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-dock-controls-on-windows-forms.md)  
 [<span data-ttu-id="ce2b6-135">Procédure pas à pas : organisation des contrôles dans les Windows Forms à l’aide d’un FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="ce2b6-135">Walkthrough: Arranging Controls on Windows Forms Using a FlowLayoutPanel</span></span>](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)  
 [<span data-ttu-id="ce2b6-136">Procédure pas à pas : organisation des contrôles dans les Windows Forms à l’aide d’un TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="ce2b6-136">Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel</span></span>](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)  
 [<span data-ttu-id="ce2b6-137">Procédure pas à pas : disposition des contrôles Windows Forms avec les propriétés Padding, Margins et AutoSize</span><span class="sxs-lookup"><span data-stu-id="ce2b6-137">Walkthrough: Laying Out Windows Forms Controls with Padding, Margins, and the AutoSize Property</span></span>](../../../../docs/framework/winforms/controls/windows-forms-controls-padding-autosize.md)
