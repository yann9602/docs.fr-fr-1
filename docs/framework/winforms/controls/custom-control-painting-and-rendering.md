---
title: "Peinture et rendu personnalisés des contrôles"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- custom controls [Windows Forms], rendering
- custom controls [Windows Forms], painting
- user controls [Windows Forms], painting
ms.assetid: a09dbf76-0966-4cbf-a66a-2083ba98e068
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: babf3d235f4cca61ad6d0e5fdc4e6b6146c7d060
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2017
---
# <a name="custom-control-painting-and-rendering"></a><span data-ttu-id="047e2-102">Peinture et rendu personnalisés des contrôles</span><span class="sxs-lookup"><span data-stu-id="047e2-102">Custom Control Painting and Rendering</span></span>
<span data-ttu-id="047e2-103">La peinture personnalisée des contrôles est une des nombreuses tâches compliquées facilitées par le .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="047e2-103">Custom painting of controls is one of the many complicated tasks made easy by the .NET Framework.</span></span> <span data-ttu-id="047e2-104">Lorsque vous créez un contrôle personnalisé, vous disposez de nombreuses options d’apparence de graphique de votre contrôle.</span><span class="sxs-lookup"><span data-stu-id="047e2-104">When authoring a custom control, you have many options regarding your control's graphical appearance.</span></span> <span data-ttu-id="047e2-105">Si vous êtes en train de créer un contrôle qui hérite de la `Control`, vous devez fournir le code qui permet à votre contrôle afficher sa représentation sous forme graphique.</span><span class="sxs-lookup"><span data-stu-id="047e2-105">If you are authoring a control that inherits from the `Control`, you must provide code that allows your control to render its graphical representation.</span></span> <span data-ttu-id="047e2-106">Si vous créez un contrôle utilisateur en héritant de la `UserControl`, ou sur l’un des contrôles Windows Forms, vous pouvez substituer la représentation graphique standard et fournir votre propre code graphique.</span><span class="sxs-lookup"><span data-stu-id="047e2-106">If you are creating a user control by inheriting from the `UserControl`, or are inheriting from one of the Windows Forms controls, you may override the standard graphical representation and provide your own graphics code.</span></span> <span data-ttu-id="047e2-107">Si vous souhaitez fournir un rendu personnalisé pour les contrôles constitutifs d’un `UserControl` vous êtes en train de créer, vos options sont plus limitées, mais toujours autorisant un large éventail de possibilités de graphiques pour vos applications et de contrôles.</span><span class="sxs-lookup"><span data-stu-id="047e2-107">If you want to provide custom rendering for the constituent controls of a `UserControl` you are authoring, your options become more limited, but still allow a wide range of graphical possibilities for your controls and applications.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="047e2-108">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="047e2-108">In This Section</span></span>  
 [<span data-ttu-id="047e2-109">Rendu d'un contrôle Windows Forms</span><span class="sxs-lookup"><span data-stu-id="047e2-109">Rendering a Windows Forms Control</span></span>](../../../../docs/framework/winforms/controls/rendering-a-windows-forms-control.md)  
 <span data-ttu-id="047e2-110">Montre comment programmer la logique qui affiche un contrôle.</span><span class="sxs-lookup"><span data-stu-id="047e2-110">Shows how to program the logic that displays a control.</span></span>  
  
 [<span data-ttu-id="047e2-111">Contrôles dessinés par l’utilisateur</span><span class="sxs-lookup"><span data-stu-id="047e2-111">User-Drawn Controls</span></span>](../../../../docs/framework/winforms/controls/user-drawn-controls.md)  
 <span data-ttu-id="047e2-112">Donne une vue d’ensemble des étapes impliquées dans l’écriture et la substitution de code de rendu de votre contrôle.</span><span class="sxs-lookup"><span data-stu-id="047e2-112">Gives an overview of the steps involved in writing and overriding rendering code for your control.</span></span>  
  
 [<span data-ttu-id="047e2-113">Contrôles constitutifs</span><span class="sxs-lookup"><span data-stu-id="047e2-113">Constituent Controls</span></span>](../../../../docs/framework/winforms/controls/constituent-controls.md)  
 <span data-ttu-id="047e2-114">Décrit comment implémenter le code de rendu personnalisé pour les contrôles constitutifs dans vos contrôles utilisateur et les formulaires.</span><span class="sxs-lookup"><span data-stu-id="047e2-114">Describes how to implement custom rendering code for constituent controls in your user controls and forms.</span></span>  
  
 [<span data-ttu-id="047e2-115">Guide pratique pour rendre votre contrôle invisible au moment de l'exécution</span><span class="sxs-lookup"><span data-stu-id="047e2-115">How to: Make Your Control Invisible at Run Time</span></span>](../../../../docs/framework/winforms/controls/how-to-make-your-control-invisible-at-run-time.md)  
 <span data-ttu-id="047e2-116">Montre comment utiliser le <xref:System.Windows.Forms.Control.Visible%2A> propriété à masquer et afficher un contrôle.</span><span class="sxs-lookup"><span data-stu-id="047e2-116">Shows how to use the <xref:System.Windows.Forms.Control.Visible%2A> property to hide and show a control.</span></span>  
  
 [<span data-ttu-id="047e2-117">Guide pratique pour affecter un arrière-plan transparent à votre contrôle</span><span class="sxs-lookup"><span data-stu-id="047e2-117">How to: Give Your Control a Transparent Background</span></span>](../../../../docs/framework/winforms/controls/how-to-give-your-control-a-transparent-background.md)  
 <span data-ttu-id="047e2-118">Montre comment utiliser la <xref:System.Windows.Forms.Control.SetStyle%2A> méthode pour créer une couleur d’arrière-plan qui est opaque, transparente ou partiellement transparente.</span><span class="sxs-lookup"><span data-stu-id="047e2-118">Shows how to use the <xref:System.Windows.Forms.Control.SetStyle%2A> method to create a background color that is opaque, transparent, or partially transparent.</span></span>  
  
 [<span data-ttu-id="047e2-119">Rendu des contrôles avec les styles visuels</span><span class="sxs-lookup"><span data-stu-id="047e2-119">Rendering Controls with Visual Styles</span></span>](../../../../docs/framework/winforms/controls/rendering-controls-with-visual-styles.md)  
 <span data-ttu-id="047e2-120">Montre comment restituer les contrôles à l’aide de styles visuels dans les systèmes d’exploitation qui les prennent en charge.</span><span class="sxs-lookup"><span data-stu-id="047e2-120">Shows how to render controls using visual styles in operating systems that support them.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="047e2-121">Référence</span><span class="sxs-lookup"><span data-stu-id="047e2-121">Reference</span></span>  
 <xref:System.Windows.Forms.Control>  
 <span data-ttu-id="047e2-122">Décrit cette classe et propose des liens vers tous ses membres.</span><span class="sxs-lookup"><span data-stu-id="047e2-122">Describes this class and has links to all of its members.</span></span>  
  
 <xref:System.Windows.Forms.UserControl>  
 <span data-ttu-id="047e2-123">Décrit cette classe et propose des liens vers tous ses membres.</span><span class="sxs-lookup"><span data-stu-id="047e2-123">Describes this class and has links to all of its members.</span></span>  
  
 <xref:System.Windows.Forms.Control.OnPaint%2A>  
 <span data-ttu-id="047e2-124">Décrit cette méthode.</span><span class="sxs-lookup"><span data-stu-id="047e2-124">Describes this method.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="047e2-125">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="047e2-125">Related Sections</span></span>  
 [<span data-ttu-id="047e2-126">Guide pratique pour créer des objets graphiques pour le dessin</span><span class="sxs-lookup"><span data-stu-id="047e2-126">How to: Create Graphics Objects for Drawing</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)  
 <span data-ttu-id="047e2-127">Introduit [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] fonctionnalités graphiques à partir d’un point de vue et donne de liens Visual Studio pour plus d’informations.</span><span class="sxs-lookup"><span data-stu-id="047e2-127">Introduces [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] graphics functionality from a Visual Studio perspective and gives links to more information.</span></span>  
  
 [<span data-ttu-id="047e2-128">Variétés de contrôles personnalisés</span><span class="sxs-lookup"><span data-stu-id="047e2-128">Varieties of Custom Controls</span></span>](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)  
 <span data-ttu-id="047e2-129">Décrit les types de contrôles personnalisés, que vous pouvez créer.</span><span class="sxs-lookup"><span data-stu-id="047e2-129">Describes the kinds of custom controls you can author.</span></span>
