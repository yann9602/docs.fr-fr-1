---
title: "Comment : positionner des contrôles dans des Windows Forms"
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
f1_keywords:
- Location
- Location.Y
- Location.X
helpviewer_keywords:
- controls [Windows Forms]
- controls [Windows Forms], moving
- snaplines
- controls [Windows Forms], positioning
ms.assetid: 4693977e-34a4-4f19-8221-68c3120c2b2b
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9ff1096e6397f4422e0fbf6400a87041cfac6470
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-position-controls-on-windows-forms"></a><span data-ttu-id="7ad61-102">Comment : positionner des contrôles dans des Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7ad61-102">How to: Position Controls on Windows Forms</span></span>
<span data-ttu-id="7ad61-103">Pour positionner les contrôles, utilisez le Concepteur Windows Forms ou spécifiez le <xref:System.Windows.Forms.Control.Location%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="7ad61-103">To position controls, use the Windows Forms Designer, or specify the <xref:System.Windows.Forms.Control.Location%2A> property.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7ad61-104">Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.</span><span class="sxs-lookup"><span data-stu-id="7ad61-104">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="7ad61-105">Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** .</span><span class="sxs-lookup"><span data-stu-id="7ad61-105">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="7ad61-106">Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="7ad61-106">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-position-a-control-on-the-design-surface-of-the-windows-forms-designer"></a><span data-ttu-id="7ad61-107">Pour positionner un contrôle sur l’aire de conception du Concepteur Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7ad61-107">To position a control on the design surface of the Windows Forms Designer</span></span>  
  
-   <span data-ttu-id="7ad61-108">Faites glisser le contrôle vers l’emplacement approprié avec la souris.</span><span class="sxs-lookup"><span data-stu-id="7ad61-108">Drag the control to the appropriate location with the mouse.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="7ad61-109">Sélectionnez le contrôle et les déplacer avec la flèche de clés pour la positionner plus précisément.</span><span class="sxs-lookup"><span data-stu-id="7ad61-109">Select the control and move it with the ARROW keys to position it more precisely.</span></span> <span data-ttu-id="7ad61-110">En outre, *les lignes d’alignement* vous aident à placer les contrôles avec précision sur votre formulaire.</span><span class="sxs-lookup"><span data-stu-id="7ad61-110">Also, *snaplines* assist you in placing controls precisely on your form.</span></span> <span data-ttu-id="7ad61-111">Pour plus d’informations, consultez [procédure pas à pas : organisation des contrôles dans les Windows Forms à l’aide des lignes d’alignement](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).</span><span class="sxs-lookup"><span data-stu-id="7ad61-111">For more information, see [Walkthrough: Arranging Controls on Windows Forms Using Snaplines](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).</span></span>  
  
### <a name="to-position-a-control-using-the-properties-window"></a><span data-ttu-id="7ad61-112">Pour positionner un contrôle à l’aide de la fenêtre Propriétés</span><span class="sxs-lookup"><span data-stu-id="7ad61-112">To position a control using the Properties window</span></span>  
  
1.  <span data-ttu-id="7ad61-113">Cliquez sur le contrôle que vous souhaitez positionner.</span><span class="sxs-lookup"><span data-stu-id="7ad61-113">Click the control you want to position.</span></span>  
  
2.  <span data-ttu-id="7ad61-114">Dans le **propriétés** fenêtre et les valeurs de type pour le <xref:System.Windows.Forms.Control.Location%2A> propriété, séparée par une virgule, pour positionner le contrôle dans son conteneur.</span><span class="sxs-lookup"><span data-stu-id="7ad61-114">In the **Properties** window, type values for the <xref:System.Windows.Forms.Control.Location%2A> property, separated by a comma, to position the control within its container.</span></span>  
  
     <span data-ttu-id="7ad61-115">Le premier nombre (X) est la distance entre la bordure gauche du conteneur ; le deuxième nombre (Y) est la distance entre le bord supérieur de la zone de conteneur, en pixels.</span><span class="sxs-lookup"><span data-stu-id="7ad61-115">The first number (X) is the distance from the left border of the container; the second number (Y) is the distance from the upper border of the container area, measured in pixels.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="7ad61-116">Vous pouvez développer la <xref:System.Windows.Forms.Control.Location%2A> propriété permettant de taper le **X** et **Y** valeurs individuellement.</span><span class="sxs-lookup"><span data-stu-id="7ad61-116">You can expand the <xref:System.Windows.Forms.Control.Location%2A> property to type the **X** and **Y** values individually.</span></span>  
  
### <a name="to-position-a-control-programmatically"></a><span data-ttu-id="7ad61-117">Pour positionner un contrôle par programmation</span><span class="sxs-lookup"><span data-stu-id="7ad61-117">To position a control programmatically</span></span>  
  
1.  <span data-ttu-id="7ad61-118">Définir le <xref:System.Windows.Forms.Control.Location%2A> propriété du contrôle à un <xref:System.Drawing.Point>.</span><span class="sxs-lookup"><span data-stu-id="7ad61-118">Set the <xref:System.Windows.Forms.Control.Location%2A> property of the control to a <xref:System.Drawing.Point>.</span></span>  
  
    ```vb  
    Button1.Location = New Point(100, 100)  
    ```  
  
    ```csharp  
    button1.Location = new Point(100, 100);  
    ```  
  
    ```cpp  
    button1->Location = Point(100, 100);  
    ```  
  
2.  <span data-ttu-id="7ad61-119">Modifiez la coordonnée X de l’emplacement du contrôle à l’aide de la <xref:System.Windows.Forms.Control.Left%2A> sous-propriété.</span><span class="sxs-lookup"><span data-stu-id="7ad61-119">Change the X coordinate of the control's location using the <xref:System.Windows.Forms.Control.Left%2A> subproperty.</span></span>  
  
    ```vb  
    Button1.Left = 300  
    ```  
  
    ```csharp  
    button1.Left = 300;  
    ```  
  
    ```cpp  
    button1->Left = 300;  
    ```  
  
### <a name="to-increment-a-controls-location-programmatically"></a><span data-ttu-id="7ad61-120">Pour incrémenter l’emplacement d’un contrôle par programmation</span><span class="sxs-lookup"><span data-stu-id="7ad61-120">To increment a control's location programmatically</span></span>  
  
1.  <span data-ttu-id="7ad61-121">Définir le <xref:System.Windows.Forms.Control.Left%2A> sous-propriété pour incrémenter la coordonnée X du contrôle.</span><span class="sxs-lookup"><span data-stu-id="7ad61-121">Set the <xref:System.Windows.Forms.Control.Left%2A> subproperty to increment the X coordinate of the control.</span></span>  
  
    ```vb  
    Button1.Left += 200  
    ```  
  
    ```csharp  
    button1.Left += 200;  
    ```  
  
    ```cpp  
    button1->Left += 200;  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="7ad61-122">Utilisez le <xref:System.Windows.Forms.Control.Location%2A> propriété à définir d’un contrôle X et Y place simultanément.</span><span class="sxs-lookup"><span data-stu-id="7ad61-122">Use the <xref:System.Windows.Forms.Control.Location%2A> property to set a control's X and Y positions simultaneously.</span></span> <span data-ttu-id="7ad61-123">Pour définir une position individuellement, utilisez du contrôle <xref:System.Windows.Forms.Control.Left%2A> (**X**) ou <xref:System.Windows.Forms.Control.Top%2A> (**Y**) sous-propriété.</span><span class="sxs-lookup"><span data-stu-id="7ad61-123">To set a position individually, use the control's <xref:System.Windows.Forms.Control.Left%2A> (**X**) or <xref:System.Windows.Forms.Control.Top%2A> (**Y**) subproperty.</span></span> <span data-ttu-id="7ad61-124">N’essayez pas de définir implicitement les coordonnées X et Y de la <xref:System.Drawing.Point> structure qui représente la position du bouton, car cette structure contient une copie des coordonnées du bouton.</span><span class="sxs-lookup"><span data-stu-id="7ad61-124">Do not try to implicitly set the X and Y coordinates of the <xref:System.Drawing.Point> structure that represents the button's location, because this structure contains a copy of the button's coordinates.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ad61-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7ad61-125">See Also</span></span>  
 [<span data-ttu-id="7ad61-126">Contrôles Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7ad61-126">Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/index.md)  
 [<span data-ttu-id="7ad61-127">Procédure pas à pas : organisation des contrôles dans les Windows Forms à l’aide des lignes d’alignement</span><span class="sxs-lookup"><span data-stu-id="7ad61-127">Walkthrough: Arranging Controls on Windows Forms Using Snaplines</span></span>](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)  
 [<span data-ttu-id="7ad61-128">Procédure pas à pas : organisation des contrôles dans les Windows Forms à l’aide d’un TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="7ad61-128">Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel</span></span>](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)  
 [<span data-ttu-id="7ad61-129">Procédure pas à pas : organisation des contrôles dans les Windows Forms à l’aide d’un FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="7ad61-129">Walkthrough: Arranging Controls on Windows Forms Using a FlowLayoutPanel</span></span>](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)  
 [<span data-ttu-id="7ad61-130">Disposition des contrôles dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7ad61-130">Arranging Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)  
 [<span data-ttu-id="7ad61-131">Création d'étiquettes et de raccourcis pour les contrôles Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7ad61-131">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)  
 [<span data-ttu-id="7ad61-132">Contrôles à utiliser dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7ad61-132">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 [<span data-ttu-id="7ad61-133">Classement par fonction des contrôles Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7ad61-133">Windows Forms Controls by Function</span></span>](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)  
 [<span data-ttu-id="7ad61-134">Comment : définir l’emplacement de l’écran des Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7ad61-134">How to: Set the Screen Location of Windows Forms</span></span>](http://msdn.microsoft.com/en-us/cb023ab7-dea7-4284-9aa6-8c03c59b60c6)
