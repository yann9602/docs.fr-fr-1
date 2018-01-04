---
title: "Boîtes de dialogue dans les Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- dialog boxes [Windows Forms], Windows Forms
- Windows Forms dialog boxes
- dialogs [Windows Forms], using in Windows Forms
ms.assetid: d43d022b-451b-490d-9386-dc79d98fbf8a
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b8f493013744ffa7819d4cb554f794d9a591a371
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="dialog-boxes-in-windows-forms"></a><span data-ttu-id="204e2-102">Boîtes de dialogue dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="204e2-102">Dialog Boxes in Windows Forms</span></span>
<span data-ttu-id="204e2-103">Les boîtes de dialogue servent à interagir avec l'utilisateur et à récupérer des informations.</span><span class="sxs-lookup"><span data-stu-id="204e2-103">Dialog boxes are used to interact with the user and retrieve information.</span></span> <span data-ttu-id="204e2-104">En termes simples, une boîte de dialogue est un formulaire dont la propriété d'énumération <xref:System.Windows.Forms.FormBorderStyle> a la valeur `FixedDialog`.</span><span class="sxs-lookup"><span data-stu-id="204e2-104">In simple terms, a dialog box is a form with its <xref:System.Windows.Forms.FormBorderStyle> enumeration property set to `FixedDialog`.</span></span> <span data-ttu-id="204e2-105">Vous pouvez construire vos propres boîtes de dialogue personnalisées à l'aide du Concepteur Windows Forms dans [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].</span><span class="sxs-lookup"><span data-stu-id="204e2-105">You can construct your own custom dialog boxes by using the Windows Forms Designer in [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].</span></span> <span data-ttu-id="204e2-106">Ajoutez des contrôles tels que `Label`, `Textbox` et `Button` pour personnaliser les boîtes de dialogue en fonction de vos besoins spécifiques.</span><span class="sxs-lookup"><span data-stu-id="204e2-106">Add controls such as `Label`, `Textbox`, and `Button` to customize dialog boxes to your specific needs.</span></span> <span data-ttu-id="204e2-107">Le [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] inclut également des boîtes de dialogue prédéfinies, telles que **ouvrir le fichier** et boîtes de message, vous pouvez adapter à vos propres applications.</span><span class="sxs-lookup"><span data-stu-id="204e2-107">The [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] also includes predefined dialog boxes, such as **File Open** and message boxes, which you can adapt for your own applications.</span></span> <span data-ttu-id="204e2-108">Pour plus d’informations, consultez [composants et contrôles de boîte de dialogue](../../../docs/framework/winforms/controls/dialog-box-controls-and-components-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="204e2-108">For more information, see [Dialog-Box Controls and Components](../../../docs/framework/winforms/controls/dialog-box-controls-and-components-windows-forms.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="204e2-109">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="204e2-109">In This Section</span></span>  
 [<span data-ttu-id="204e2-110">Guide pratique pour afficher des boîtes de dialogue pour les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="204e2-110">How to: Display Dialog Boxes for Windows Forms</span></span>](../../../docs/framework/winforms/how-to-display-dialog-boxes-for-windows-forms.md)  
 <span data-ttu-id="204e2-111">Explique comment afficher des boîtes de dialogue.</span><span class="sxs-lookup"><span data-stu-id="204e2-111">Gives directions for showing dialog boxes.</span></span>  
  
-   <span data-ttu-id="204e2-112">[Comment : récupérer des informations de boîte de dialogue sélective à l’aide de plusieurs propriétés](http://msdn.microsoft.com/library/56taefba\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="204e2-112">[How to: Retrieve Dialog Box Information Selectively Using Multiple Properties](http://msdn.microsoft.com/library/56taefba\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="204e2-113">[Comment : récupérer les informations du formulaire Parent d’une boîte de dialogue](http://msdn.microsoft.com/library/k70t19bb\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="204e2-113">[How to: Retrieve Information from the Parent Form of a Dialog Box](http://msdn.microsoft.com/library/k70t19bb\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="204e2-114">[Entrée d’utilisateur aux boîtes de dialogue](http://msdn.microsoft.com/library/1s9ws53w\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="204e2-114">[User Input to Dialog Boxes](http://msdn.microsoft.com/library/1s9ws53w\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="204e2-115">[Comment : récupérer le résultat des boîtes de dialogue](http://msdn.microsoft.com/library/40x40td1\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="204e2-115">[How to: Retrieve the Result for Dialog Boxes](http://msdn.microsoft.com/library/40x40td1\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="204e2-116">[Procédure pas à pas : Récupération des informations de boîte de dialogue collectivement à l’aide d’objets](http://msdn.microsoft.com/library/cakx2hdw\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="204e2-116">[Walkthrough: Retrieving Dialog Box Information Collectively Using Objects](http://msdn.microsoft.com/library/cakx2hdw\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="204e2-117">[Comment : fermer les boîtes de dialogue et conserver l’entrée d’utilisateur](http://msdn.microsoft.com/library/65ad5907\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="204e2-117">[How to: Close Dialog Boxes and Retain User Input](http://msdn.microsoft.com/library/65ad5907\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="204e2-118">[Comment : créer des boîtes de dialogue au moment du Design](http://msdn.microsoft.com/library/55cz5x2c\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="204e2-118">[How to: Create Dialog Boxes at Design Time](http://msdn.microsoft.com/library/55cz5x2c\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="204e2-119">[Comment : afficher des boîtes de Message](http://msdn.microsoft.com/library/3tt9e94f\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="204e2-119">[How to: Display Message Boxes](http://msdn.microsoft.com/library/3tt9e94f\(v=vs.110\))</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="204e2-120">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="204e2-120">Related Sections</span></span>  
 [<span data-ttu-id="204e2-121">Contrôles et composants de boîte de dialogue</span><span class="sxs-lookup"><span data-stu-id="204e2-121">Dialog-Box Controls and Components</span></span>](../../../docs/framework/winforms/controls/dialog-box-controls-and-components-windows-forms.md)  
 <span data-ttu-id="204e2-122">Répertorie les contrôles de boîtes de dialogue prédéfinis.</span><span class="sxs-lookup"><span data-stu-id="204e2-122">Lists the predefined dialog box controls.</span></span>  
  
 [<span data-ttu-id="204e2-123">Modification de l'apparence des Windows Forms</span><span class="sxs-lookup"><span data-stu-id="204e2-123">Changing the Appearance of Windows Forms</span></span>](../../../docs/framework/winforms/changing-the-appearance-of-windows-forms.md)  
 <span data-ttu-id="204e2-124">Contient des liens vers des rubriques qui montrent comment modifier l’apparence des applications Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="204e2-124">Contains links to topics that describe how to change the appearance of Windows Forms applications.</span></span>  
  
 [<span data-ttu-id="204e2-125">Vue d’ensemble du contrôle TabControl</span><span class="sxs-lookup"><span data-stu-id="204e2-125">TabControl Control Overview</span></span>](../../../docs/framework/winforms/controls/tabcontrol-control-overview-windows-forms.md)  
 <span data-ttu-id="204e2-126">Explique comment insérer le contrôle d'onglet dans une boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="204e2-126">Explains how you incorporate the tab control into a dialog box.</span></span>
