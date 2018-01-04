---
title: "Comment : organiser les contrôles à l'aide des lignes d'alignement (SnapLines) et de la grille dans les Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: GridSize
helpviewer_keywords:
- snap to grid [Windows Forms], Windows Forms Designer
- Windows Forms, grid options in designer
- controls [Windows Forms], aligning
ms.assetid: bb54bce5-880f-4a36-af68-8cf92058dc1c
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7e3754df2930503e7e7a123ffdb4d4b787338c20
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-arrange-controls-with-snaplines-and-the-grid-in-windows-forms"></a><span data-ttu-id="395b1-102">Comment : organiser les contrôles à l'aide des lignes d'alignement (SnapLines) et de la grille dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="395b1-102">How to: Arrange Controls with Snaplines and the Grid in Windows Forms</span></span>
<span data-ttu-id="395b1-103">À l’aide des fonctionnalités de disposition [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)], vous pouvez déterminer précisément où les contrôles sont placés sur un formulaire.</span><span class="sxs-lookup"><span data-stu-id="395b1-103">Using the layout features of [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)], you can precisely direct where controls are placed on a form.</span></span> <span data-ttu-id="395b1-104">Les contrôles ajoutés à un formulaire ou déplacés sur un formulaire peuvent être alignés automatiquement pour les lignes et colonnes de grille du Concepteur Windows Forms, ou vous pouvez aligner des contrôles à l’aide de la fonctionnalité des lignes d’alignement.</span><span class="sxs-lookup"><span data-stu-id="395b1-104">Controls added to a form or moved on a form can be automatically aligned to the rows and columns of the Windows Forms Designer's grid, or you can align controls by using the snaplines feature.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="395b1-105">Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.</span><span class="sxs-lookup"><span data-stu-id="395b1-105">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="395b1-106">Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** .</span><span class="sxs-lookup"><span data-stu-id="395b1-106">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="395b1-107">Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="395b1-107">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-snap-all-controls-to-the-grid"></a><span data-ttu-id="395b1-108">Pour tous les contrôles à la grille d’alignement</span><span class="sxs-lookup"><span data-stu-id="395b1-108">To snap all controls to the grid</span></span>  
  
-   <span data-ttu-id="395b1-109">Sélectionnez le **SnapToGrid** en mode de mise en page dans le Concepteur Windows Forms **Options** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="395b1-109">Select the **SnapToGrid** layout mode in the Windows Forms Designer **Options** dialog box.</span></span>  
  
     <span data-ttu-id="395b1-110">Pour plus d’informations, consultez [général, Concepteur Windows Forms, boîte de dialogue Options](http://msdn.microsoft.com/en-us/8dd170af-72f0-4212-b04b-034ceee92834).</span><span class="sxs-lookup"><span data-stu-id="395b1-110">For more information, see [General, Windows Forms Designer, Options Dialog Box](http://msdn.microsoft.com/en-us/8dd170af-72f0-4212-b04b-034ceee92834).</span></span> <span data-ttu-id="395b1-111">Tous les contrôles s’alignent désormais sur les points de la grille.</span><span class="sxs-lookup"><span data-stu-id="395b1-111">All controls now align themselves along the points on the grid.</span></span>  
  
     <span data-ttu-id="395b1-112">Vous pouvez aligner des contrôles individuels à la grille en verrouillant en place.</span><span class="sxs-lookup"><span data-stu-id="395b1-112">You can snap individual controls to the grid by locking them in place.</span></span> <span data-ttu-id="395b1-113">Toutefois, pendant qu’ils sont verrouillés, ils ne peuvent pas être déplacés ou redimensionnés.</span><span class="sxs-lookup"><span data-stu-id="395b1-113">However, while they are locked, they cannot be moved or resized.</span></span> <span data-ttu-id="395b1-114">Pour plus d’informations sur le verrouillage des contrôles, consultez [Comment : verrouiller les contrôles aux Windows Forms](../../../../docs/framework/winforms/controls/how-to-lock-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="395b1-114">For more information about locking controls, see [How to: Lock Controls to Windows Forms](../../../../docs/framework/winforms/controls/how-to-lock-controls-to-windows-forms.md).</span></span>  
  
### <a name="to-align-controls-using-snaplines"></a><span data-ttu-id="395b1-115">Pour aligner des contrôles à l’aide des lignes d’alignement</span><span class="sxs-lookup"><span data-stu-id="395b1-115">To align controls using snaplines</span></span>  
  
-   <span data-ttu-id="395b1-116">Sélectionnez le **les lignes d’alignement** en mode de mise en page dans le Concepteur Windows Forms **Options** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="395b1-116">Select the **SnapLines** layout mode in the Windows Forms Designer **Options** dialog box.</span></span>  
  
     <span data-ttu-id="395b1-117">Pour plus d’informations, consultez [procédure pas à pas : organisation des contrôles dans les Windows Forms à l’aide des lignes d’alignement](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).</span><span class="sxs-lookup"><span data-stu-id="395b1-117">For more information, see [Walkthrough: Arranging Controls on Windows Forms Using Snaplines](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).</span></span> <span data-ttu-id="395b1-118">Vous pouvez maintenant utiliser les lignes d’alignement pour aligner et organiser les contrôles sur votre formulaire.</span><span class="sxs-lookup"><span data-stu-id="395b1-118">You can now use snaplines to align and arrange controls on your form.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="395b1-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="395b1-119">See Also</span></span>  
 [<span data-ttu-id="395b1-120">Général, Concepteur Windows Forms, boîte de dialogue Options</span><span class="sxs-lookup"><span data-stu-id="395b1-120">General, Windows Forms Designer, Options Dialog Box</span></span>](http://msdn.microsoft.com/en-us/8dd170af-72f0-4212-b04b-034ceee92834)  
 [<span data-ttu-id="395b1-121">Procédure pas à pas : organisation des contrôles dans les Windows Forms à l’aide des lignes d’alignement</span><span class="sxs-lookup"><span data-stu-id="395b1-121">Walkthrough: Arranging Controls on Windows Forms Using Snaplines</span></span>](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)  
 [<span data-ttu-id="395b1-122">Contrôles Windows Forms</span><span class="sxs-lookup"><span data-stu-id="395b1-122">Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/index.md)  
 [<span data-ttu-id="395b1-123">Comment : ajouter des contrôles à des Windows Forms</span><span class="sxs-lookup"><span data-stu-id="395b1-123">How to: Add Controls to Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)  
 [<span data-ttu-id="395b1-124">Disposition des contrôles dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="395b1-124">Arranging Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)  
 [<span data-ttu-id="395b1-125">Création d'étiquettes et de raccourcis pour les contrôles Windows Forms</span><span class="sxs-lookup"><span data-stu-id="395b1-125">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)  
 [<span data-ttu-id="395b1-126">Contrôles à utiliser dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="395b1-126">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 [<span data-ttu-id="395b1-127">Classement par fonction des contrôles Windows Forms</span><span class="sxs-lookup"><span data-stu-id="395b1-127">Windows Forms Controls by Function</span></span>](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)
