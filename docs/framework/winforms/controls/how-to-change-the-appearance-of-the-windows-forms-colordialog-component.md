---
title: "Comment : modifier l'apparence du composant ColorDialog Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- ColorDialog component [Windows Forms], examples
- ColorDialog component [Windows Forms], formatting appearance
- color dialog box [Windows Forms], configuring appearance
ms.assetid: bba4e262-1cd7-4f63-89cf-330a36f7b539
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 11edb1019b8fedde368d712ab27dd0954a2de50a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-change-the-appearance-of-the-windows-forms-colordialog-component"></a><span data-ttu-id="64fc1-102">Comment : modifier l'apparence du composant ColorDialog Windows Forms</span><span class="sxs-lookup"><span data-stu-id="64fc1-102">How to: Change the Appearance of the Windows Forms ColorDialog Component</span></span>
<span data-ttu-id="64fc1-103">Vous pouvez configurer l’apparence des Windows Forms <xref:System.Windows.Forms.ColorDialog> composant avec un nombre de ses propriétés.</span><span class="sxs-lookup"><span data-stu-id="64fc1-103">You can configure the appearance of the Windows Forms <xref:System.Windows.Forms.ColorDialog> component with a number of its properties.</span></span> <span data-ttu-id="64fc1-104">La boîte de dialogue comporte deux sections : une qui affiche les couleurs de base et un type qui autorise l’utilisateur à définir des couleurs personnalisées.</span><span class="sxs-lookup"><span data-stu-id="64fc1-104">The dialog box has two sections — one that shows basic colors and one that allows the user to define custom colors.</span></span>  
  
 <span data-ttu-id="64fc1-105">La plupart des propriétés de restreindre les couleurs de l’utilisateur peut sélectionner à partir de la boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="64fc1-105">Most of the properties restrict what colors the user can select from the dialog box.</span></span> <span data-ttu-id="64fc1-106">Si le <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A> est définie sur `true`, l’utilisateur est autorisé à définir des couleurs personnalisées.</span><span class="sxs-lookup"><span data-stu-id="64fc1-106">If the <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A> property is set to `true`, the user is allowed to define custom colors.</span></span> <span data-ttu-id="64fc1-107">Le <xref:System.Windows.Forms.ColorDialog.FullOpen%2A> propriété `true` si la boîte de dialogue est développée pour définir des couleurs personnalisées ; sinon, l’utilisateur doit cliquer un bouton « Définir les couleurs personnalisées ».</span><span class="sxs-lookup"><span data-stu-id="64fc1-107">The <xref:System.Windows.Forms.ColorDialog.FullOpen%2A> property is `true` if the dialog box is expanded to define custom colors; otherwise the user must click a "Define Custom Colors" button.</span></span> <span data-ttu-id="64fc1-108">Lorsque le <xref:System.Windows.Forms.ColorDialog.AnyColor%2A> est définie sur `true`, la boîte de dialogue affiche toutes les couleurs disponibles dans le jeu de couleurs de base.</span><span class="sxs-lookup"><span data-stu-id="64fc1-108">When the <xref:System.Windows.Forms.ColorDialog.AnyColor%2A> property is set to `true`, the dialog box displays all available colors in the set of basic colors.</span></span> <span data-ttu-id="64fc1-109">Si le <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A> est définie sur `true`, l’utilisateur ne peut pas sélectionner de couleurs tramées ; uniquement des couleurs unies peuvent être sélectionnées.</span><span class="sxs-lookup"><span data-stu-id="64fc1-109">If the <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A> property is set to `true`, the user cannot select dithered colors; only solid colors are available to select.</span></span>  
  
 <span data-ttu-id="64fc1-110">Si le <xref:System.Windows.Forms.ColorDialog.ShowHelp%2A> est définie sur `true`, un bouton d’aide s’affiche dans la boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="64fc1-110">If the <xref:System.Windows.Forms.ColorDialog.ShowHelp%2A> property is set to `true`, a Help button appears on the dialog box.</span></span> <span data-ttu-id="64fc1-111">Lorsque l’utilisateur clique sur le bouton aide, le <xref:System.Windows.Forms.ColorDialog> du composant <xref:System.Windows.Forms.CommonDialog.HelpRequest> événement est déclenché.</span><span class="sxs-lookup"><span data-stu-id="64fc1-111">When the user clicks the Help button, the <xref:System.Windows.Forms.ColorDialog> component's <xref:System.Windows.Forms.CommonDialog.HelpRequest> event is raised.</span></span>  
  
### <a name="to-configure-the-appearance-of-the-color-dialog-box"></a><span data-ttu-id="64fc1-112">Pour configurer l’apparence de la boîte de dialogue couleur</span><span class="sxs-lookup"><span data-stu-id="64fc1-112">To configure the appearance of the color dialog box</span></span>  
  
1.  <span data-ttu-id="64fc1-113">Définir le <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A>, <xref:System.Windows.Forms.ColorDialog.AnyColor%2A>, <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A>, et <xref:System.Windows.Forms.ColorDialog.ShowHelp%2A> propriétés aux valeurs souhaitées.</span><span class="sxs-lookup"><span data-stu-id="64fc1-113">Set the <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A>, <xref:System.Windows.Forms.ColorDialog.AnyColor%2A>, <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A>, and <xref:System.Windows.Forms.ColorDialog.ShowHelp%2A> properties to the desired values.</span></span>  
  
    ```vb  
    ColorDialog1.AllowFullOpen = True  
    ColorDialog1.AnyColor = True  
    ColorDialog1.SolidColorOnly = False  
    ColorDialog1.ShowHelp = True  
    ```  
  
    ```csharp  
    colorDialog1.AllowFullOpen = true;  
    colorDialog1.AnyColor = true;  
    colorDialog1.SolidColorOnly = false;  
    colorDialog1.ShowHelp = true;  
    ```  
  
    ```cpp  
    colorDialog1->AllowFullOpen = true;  
    colorDialog1->AnyColor = true;  
    colorDialog1->SolidColorOnly = false;  
    colorDialog1->ShowHelp = true;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="64fc1-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="64fc1-114">See Also</span></span>  
 <xref:System.Windows.Forms.ColorDialog>  
 [<span data-ttu-id="64fc1-115">ColorDialog, composant</span><span class="sxs-lookup"><span data-stu-id="64fc1-115">ColorDialog Component</span></span>](../../../../docs/framework/winforms/controls/colordialog-component-windows-forms.md)  
 [<span data-ttu-id="64fc1-116">Vue d’ensemble du composant ColorDialog</span><span class="sxs-lookup"><span data-stu-id="64fc1-116">ColorDialog Component Overview</span></span>](../../../../docs/framework/winforms/controls/colordialog-component-overview-windows-forms.md)
