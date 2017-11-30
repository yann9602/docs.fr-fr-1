---
title: "Utilisation de contrôles WPF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms Designer [Windows Forms], interoperability with WPF
- interoperability [WPF]
ms.assetid: 03c85dce-26ad-44cd-bc1d-8e0cb56de096
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a6fe8fb972f8080bbffeed5db2063d8c0484aec4
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2017
---
# <a name="using-wpf-controls"></a><span data-ttu-id="27034-102">Utilisation de contrôles WPF</span><span class="sxs-lookup"><span data-stu-id="27034-102">Using WPF Controls</span></span>
<span data-ttu-id="27034-103">Vous pouvez utiliser des contrôles Windows Presentation Foundation (WPF) dans vos applications Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="27034-103">You can use Windows Presentation Foundation (WPF) controls in your Windows Forms-based applications.</span></span> <span data-ttu-id="27034-104">Bien que ces deux technologies d’affichage différentes, elles interagissent sans heurts.</span><span class="sxs-lookup"><span data-stu-id="27034-104">Although these are two different view technologies, they interoperate smoothly.</span></span>  
  
 <span data-ttu-id="27034-105">Le Concepteur Windows Forms fournit un environnement de conception visuelle pour l’hébergement de contrôles Windows Presentation Foundation.</span><span class="sxs-lookup"><span data-stu-id="27034-105">The Windows Forms Designer provides a visual design environment for hosting Windows Presentation Foundation controls.</span></span> <span data-ttu-id="27034-106">Un contrôle WPF est hébergé par un contrôle Windows Forms spécial nommé <xref:System.Windows.Forms.Integration.ElementHost>.</span><span class="sxs-lookup"><span data-stu-id="27034-106">A WPF control is hosted by a special Windows Forms control that is named <xref:System.Windows.Forms.Integration.ElementHost>.</span></span> <span data-ttu-id="27034-107">Ce contrôle permet le contrôle WPF de participer à la disposition du formulaire et de recevoir des messages de clavier et souris.</span><span class="sxs-lookup"><span data-stu-id="27034-107">This control enables the WPF control to participate in the form's layout and to receive keyboard and mouse messages.</span></span> <span data-ttu-id="27034-108">Au moment du design, vous pouvez organiser les <xref:System.Windows.Forms.Integration.ElementHost> contrôler tout comme vous le feriez pour n’importe quel contrôle Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="27034-108">At design time, you can arrange the <xref:System.Windows.Forms.Integration.ElementHost> control just as you would any Windows Forms control.</span></span>  
  
 <span data-ttu-id="27034-109">Vous pouvez également utiliser des contrôles Windows Forms dans vos applications WPF.</span><span class="sxs-lookup"><span data-stu-id="27034-109">You can also use Windows Forms controls in your WPF-based applications.</span></span> <span data-ttu-id="27034-110">Pour plus d’informations, consultez [Concepteur WPF](http://msdn.microsoft.com/en-us/c6c65214-8411-4e16-b254-163ed4099c26).</span><span class="sxs-lookup"><span data-stu-id="27034-110">For more information, see [WPF Designer](http://msdn.microsoft.com/en-us/c6c65214-8411-4e16-b254-163ed4099c26).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="27034-111">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="27034-111">In This Section</span></span>  
 [<span data-ttu-id="27034-112">Guide pratique pour copier et coller un contrôle ElementHost au moment du design</span><span class="sxs-lookup"><span data-stu-id="27034-112">How to: Copy and Paste an ElementHost Control at Design Time</span></span>](../../../../docs/framework/winforms/advanced/how-to-copy-and-paste-an-elementhost-control-at-design-time.md)  
 <span data-ttu-id="27034-113">Montre comment copier un contrôle Windows Presentation Foundation sur un Windows Form.</span><span class="sxs-lookup"><span data-stu-id="27034-113">Shows how to copy a Windows Presentation Foundation control on a Windows Form.</span></span>  
  
 [<span data-ttu-id="27034-114">Procédure pas à pas : réorganisation du contenu WPF sur les Windows Forms au moment du design</span><span class="sxs-lookup"><span data-stu-id="27034-114">Walkthrough: Arranging WPF Content on Windows Forms at Design Time</span></span>](../../../../docs/framework/winforms/advanced/walkthrough-arranging-wpf-content-on-windows-forms-at-design-time.md)  
 <span data-ttu-id="27034-115">Montre comment utiliser les fonctionnalités de disposition Windows Forms, telles que l’ancrage et les lignes d’alignement, pour organiser les contrôles Windows Presentation Foundation.</span><span class="sxs-lookup"><span data-stu-id="27034-115">Shows how to use the Windows Forms layout features, such as anchoring and snaplines, to arrange Windows Presentation Foundation controls.</span></span>  
  
 [<span data-ttu-id="27034-116">Procédure pas à pas : modification des propriétés d'un élément WPF hébergé au moment du design</span><span class="sxs-lookup"><span data-stu-id="27034-116">Walkthrough: Changing Properties of a Hosted WPF Element at Design Time</span></span>](../../../../docs/framework/winforms/advanced/walkthrough-changing-properties-of-a-hosted-wpf-element-at-design-time.md)  
 <span data-ttu-id="27034-117">Affiche le workflow entre le Concepteur Windows Forms et le [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)] pour modifier des propriétés sur les contrôles WPF.</span><span class="sxs-lookup"><span data-stu-id="27034-117">Shows the workflow between the Windows Forms Designer and the [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)] for changing properties on WPF controls.</span></span>  
  
 [<span data-ttu-id="27034-118">Procédure pas à pas : création de contenu WPF sur les Windows Forms au moment du design</span><span class="sxs-lookup"><span data-stu-id="27034-118">Walkthrough: Creating New WPF Content on Windows Forms at Design Time</span></span>](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md)  
 <span data-ttu-id="27034-119">Montre comment créer un contrôle Windows Presentation Foundation pour une utilisation dans vos applications Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="27034-119">Shows how to create a Windows Presentation Foundation control for use in your Windows Forms-based applications.</span></span>  
  
 [<span data-ttu-id="27034-120">Procédure pas à pas : copier-coller d'un contrôle ElementHost dans d'autres Windows Forms</span><span class="sxs-lookup"><span data-stu-id="27034-120">Walkthrough: Copying and Pasting an ElementHost Control into Separate Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/copy--paste-an-elementhost-control-into-forms.md)  
 <span data-ttu-id="27034-121">Montre comment copier un contrôle Windows Presentation Foundation à partir d’un Windows Form à un autre.</span><span class="sxs-lookup"><span data-stu-id="27034-121">Shows how to copy a Windows Presentation Foundation control from one Windows Form to another.</span></span>  
  
 [<span data-ttu-id="27034-122">Procédure pas à pas : assignation du contenu WPF sur les Windows Forms au moment du design</span><span class="sxs-lookup"><span data-stu-id="27034-122">Walkthrough: Assigning WPF Content on Windows Forms at Design Time</span></span>](../../../../docs/framework/winforms/advanced/walkthrough-assigning-wpf-content-on-windows-forms-at-design-time.md)  
 <span data-ttu-id="27034-123">Montre comment sélectionner les types de contrôles Windows Presentation Foundation que vous souhaitez afficher sur votre formulaire.</span><span class="sxs-lookup"><span data-stu-id="27034-123">Shows how to select the Windows Presentation Foundation control types you want to display on your form.</span></span>  
  
 [<span data-ttu-id="27034-124">Procédure pas à pas : application de styles au contenu WPF</span><span class="sxs-lookup"><span data-stu-id="27034-124">Walkthrough: Styling WPF Content</span></span>](../../../../docs/framework/winforms/advanced/walkthrough-styling-wpf-content.md)  
 <span data-ttu-id="27034-125">Affiche le workflow entre le Concepteur Windows Forms et le [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)] pour appliquer des styles à des contrôles Windows Presentation Foundation.</span><span class="sxs-lookup"><span data-stu-id="27034-125">Shows the workflow between the Windows Forms Designer and the [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)] for applying styles to Windows Presentation Foundation controls.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="27034-126">Référence</span><span class="sxs-lookup"><span data-stu-id="27034-126">Reference</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <span data-ttu-id="27034-127">Décrit une classe que vous pouvez utiliser pour héberger des contrôles Windows Presentation Foundation dans vos applications Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="27034-127">Describes a class which you can use to host Windows Presentation Foundation controls in your Windows Forms-based applications.</span></span>  
  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 <span data-ttu-id="27034-128">Décrit une classe que vous pouvez utiliser pour héberger des contrôles Windows Forms dans votre application Windows Presentation Foundation.</span><span class="sxs-lookup"><span data-stu-id="27034-128">Describes a class which you can use to host Windows Forms controls in your Windows Presentation Foundation-based application.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="27034-129">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="27034-129">Related Sections</span></span>  
 [<span data-ttu-id="27034-130">Migration et interopérabilité</span><span class="sxs-lookup"><span data-stu-id="27034-130">Migration and Interoperability</span></span>](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)  
 <span data-ttu-id="27034-131">Décrit l’interopérabilité entre les technologies Windows Presentation Foundation et Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="27034-131">Describes interoperation between the Windows Presentation Foundation and Windows Forms technologies.</span></span>  
  
 [<span data-ttu-id="27034-132">Concepteur WPF</span><span class="sxs-lookup"><span data-stu-id="27034-132">WPF Designer</span></span>](http://msdn.microsoft.com/en-us/c6c65214-8411-4e16-b254-163ed4099c26)  
 <span data-ttu-id="27034-133">Explique comment concevoir des contrôles Windows Presentation Foundation dans [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)].</span><span class="sxs-lookup"><span data-stu-id="27034-133">Describes how to design Windows Presentation Foundation controls in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)].</span></span>
