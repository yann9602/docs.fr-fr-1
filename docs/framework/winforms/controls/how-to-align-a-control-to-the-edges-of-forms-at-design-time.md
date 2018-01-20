---
title: "Comment : aligner un contrôle sur les bords des formulaires au moment du design"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- custom controls [Windows Forms], docking using designer
- Dock property [Windows Forms], aligning controls (using designer)
ms.assetid: 51f08998-5e3b-4330-be58-a4edd0eb60f4
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1232f1f091412017e22f29d529bf7c76b32a4b6d
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-align-a-control-to-the-edges-of-forms-at-design-time"></a><span data-ttu-id="718b6-102">Comment : aligner un contrôle sur les bords des formulaires au moment du design</span><span class="sxs-lookup"><span data-stu-id="718b6-102">How to: Align a Control to the Edges of Forms at Design Time</span></span>
<span data-ttu-id="718b6-103">Vous pouvez aligner un contrôle sur le bord de vos formulaires en définissant le <xref:System.Windows.Forms.Control.Dock%2A>.</span><span class="sxs-lookup"><span data-stu-id="718b6-103">You can make your control align to the edge of your forms by setting the <xref:System.Windows.Forms.Control.Dock%2A>.</span></span> <span data-ttu-id="718b6-104">Cette propriété désigne l’emplacement de votre contrôle dans le formulaire.</span><span class="sxs-lookup"><span data-stu-id="718b6-104">This property designates where your control resides in the form.</span></span> <span data-ttu-id="718b6-105">La propriété <xref:System.Windows.Forms.Control.Dock%2A> peut avoir les valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="718b6-105">The <xref:System.Windows.Forms.Control.Dock%2A> property can be set to the following values:</span></span>  
  
|<span data-ttu-id="718b6-106">Paramètre</span><span class="sxs-lookup"><span data-stu-id="718b6-106">Setting</span></span>|<span data-ttu-id="718b6-107">Effet sur le contrôle</span><span class="sxs-lookup"><span data-stu-id="718b6-107">Effect on your control</span></span>|  
|-------------|----------------------------|  
|<xref:System.Windows.Forms.DockStyle.Bottom>|<span data-ttu-id="718b6-108">S'ancre en bas du formulaire.</span><span class="sxs-lookup"><span data-stu-id="718b6-108">Docks to the bottom of the form.</span></span>|  
|<xref:System.Windows.Forms.DockStyle.Fill>|<span data-ttu-id="718b6-109">Remplit tout l'espace restant dans le formulaire.</span><span class="sxs-lookup"><span data-stu-id="718b6-109">Fills all remaining space in the form.</span></span>|  
|<xref:System.Windows.Forms.DockStyle.Left>|<span data-ttu-id="718b6-110">S'ancre sur le côté gauche du formulaire.</span><span class="sxs-lookup"><span data-stu-id="718b6-110">Docks to the left side of the form.</span></span>|  
|<xref:System.Windows.Forms.DockStyle.None>|<span data-ttu-id="718b6-111">Ne s’ancre nulle part et apparaît à l’emplacement spécifié par son <xref:System.Windows.Forms.Control.Location%2A>.</span><span class="sxs-lookup"><span data-stu-id="718b6-111">Does not dock anywhere, and it appears at the location specified by its <xref:System.Windows.Forms.Control.Location%2A>.</span></span>|  
|<xref:System.Windows.Forms.DockStyle.Right>|<span data-ttu-id="718b6-112">S'ancre sur le côté droit du formulaire.</span><span class="sxs-lookup"><span data-stu-id="718b6-112">Docks to the right side of the form.</span></span>|  
|<xref:System.Windows.Forms.DockStyle.Top>|<span data-ttu-id="718b6-113">S'ancre en haut du formulaire.</span><span class="sxs-lookup"><span data-stu-id="718b6-113">Docks to the top of the form.</span></span>|  
  
 <span data-ttu-id="718b6-114">Ces valeurs peuvent également être définies dans le code.</span><span class="sxs-lookup"><span data-stu-id="718b6-114">These values can also be set in code.</span></span> <span data-ttu-id="718b6-115">Pour plus d’informations, consultez [Comment : aligner un contrôle sur les bords des formulaires](../../../../docs/framework/winforms/controls/how-to-align-a-control-to-the-edges-of-forms.md).</span><span class="sxs-lookup"><span data-stu-id="718b6-115">For more information, see [How to: Align a Control to the Edges of Forms](../../../../docs/framework/winforms/controls/how-to-align-a-control-to-the-edges-of-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="718b6-116">Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.</span><span class="sxs-lookup"><span data-stu-id="718b6-116">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="718b6-117">Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** .</span><span class="sxs-lookup"><span data-stu-id="718b6-117">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="718b6-118">Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="718b6-118">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-set-the-dock-property-for-your-control-at-design-time"></a><span data-ttu-id="718b6-119">Pour définir la propriété Dock de votre contrôle au moment du design</span><span class="sxs-lookup"><span data-stu-id="718b6-119">To set the Dock property for your control at design time</span></span>  
  
1.  <span data-ttu-id="718b6-120">Dans le Concepteur Windows Forms, sélectionnez votre contrôle.</span><span class="sxs-lookup"><span data-stu-id="718b6-120">In the Windows Forms Designer, select your control.</span></span>  
  
2.  <span data-ttu-id="718b6-121">Dans le **propriétés** fenêtre, cliquez sur la liste déroulante située en regard du <xref:System.Windows.Forms.Control.Dock%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="718b6-121">In the **Properties** window, click the drop-down box next to the <xref:System.Windows.Forms.Control.Dock%2A> property.</span></span>  
  
     <span data-ttu-id="718b6-122">Une interface graphique représentant les six possible <xref:System.Windows.Forms.Control.Dock%2A> paramètres s’affiche.</span><span class="sxs-lookup"><span data-stu-id="718b6-122">A graphical interface representing the six possible <xref:System.Windows.Forms.Control.Dock%2A> settings is displayed.</span></span>  
  
3.  <span data-ttu-id="718b6-123">Choisissez le paramètre approprié.</span><span class="sxs-lookup"><span data-stu-id="718b6-123">Choose the appropriate setting.</span></span>  
  
4.  <span data-ttu-id="718b6-124">Votre contrôle s’ancre maintenant de la manière spécifiée par le paramètre.</span><span class="sxs-lookup"><span data-stu-id="718b6-124">Your control will now dock in the manner specified by the setting.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="718b6-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="718b6-125">See Also</span></span>  
 <xref:System.Windows.Forms.Control.Dock%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.Control.Anchor%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="718b6-126">Guide pratique pour aligner un contrôle sur les bords des formulaires</span><span class="sxs-lookup"><span data-stu-id="718b6-126">How to: Align a Control to the Edges of Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-align-a-control-to-the-edges-of-forms.md)  
 [<span data-ttu-id="718b6-127">Procédure pas à pas : organisation des contrôles dans les Windows Forms à l’aide des lignes d’alignement</span><span class="sxs-lookup"><span data-stu-id="718b6-127">Walkthrough: Arranging Controls on Windows Forms Using Snaplines</span></span>](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)  
 [<span data-ttu-id="718b6-128">Guide pratique pour ancrer des contrôles sur des Windows Forms</span><span class="sxs-lookup"><span data-stu-id="718b6-128">How to: Anchor Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-anchor-controls-on-windows-forms.md)  
 [<span data-ttu-id="718b6-129">Guide pratique pour ancrer et arrimer des contrôles enfants dans un contrôle TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="718b6-129">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)  
 [<span data-ttu-id="718b6-130">Guide pratique pour ancrer des contrôles enfants dans un contrôle FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="718b6-130">How to: Anchor and Dock Child Controls in a FlowLayoutPanel Control</span></span>](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control.md)  
 [<span data-ttu-id="718b6-131">Procédure pas à pas : organisation des contrôles dans les Windows Forms à l’aide d’un TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="718b6-131">Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel</span></span>](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)  
 [<span data-ttu-id="718b6-132">Procédure pas à pas : organisation des contrôles dans les Windows Forms à l’aide d’un FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="718b6-132">Walkthrough: Arranging Controls on Windows Forms Using a FlowLayoutPanel</span></span>](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)  
 [<span data-ttu-id="718b6-133">Développement de contrôles Windows Forms au moment du design</span><span class="sxs-lookup"><span data-stu-id="718b6-133">Developing Windows Forms Controls at Design Time</span></span>](../../../../docs/framework/winforms/controls/developing-windows-forms-controls-at-design-time.md)
