---
title: "Comment : définir une icône pour un bouton ToolBar à l'aide du concepteur"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- toolbars [Windows Forms], adding icons to buttons
- examples [Windows Forms], toolbars
- images [Windows Forms], toolbar buttons
- buttons [Windows Forms], images
- icons [Windows Forms], toolbar buttons
- ToolBar control [Windows Forms], adding icons to buttons
ms.assetid: d848f38e-67f2-49d4-8e88-01c845c06c02
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 85be18b2cbb4e0fe729c335016fa8e7348f7be13
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-define-an-icon-for-a-toolbar-button-using-the-designer"></a><span data-ttu-id="6a98b-102">Comment : définir une icône pour un bouton ToolBar à l'aide du concepteur</span><span class="sxs-lookup"><span data-stu-id="6a98b-102">How to: Define an Icon for a ToolBar Button Using the Designer</span></span>
> [!NOTE]
>  <span data-ttu-id="6a98b-103">Le contrôle <xref:System.Windows.Forms.ToolStrip> remplace le contrôle <xref:System.Windows.Forms.ToolBar> et lui ajoute des fonctionnalités ; toutefois, le contrôle <xref:System.Windows.Forms.ToolBar> est conservé pour la compatibilité descendante et l'utilisation future si tel est votre choix.</span><span class="sxs-lookup"><span data-stu-id="6a98b-103">The <xref:System.Windows.Forms.ToolStrip> control replaces and adds functionality to the <xref:System.Windows.Forms.ToolBar> control; however, the <xref:System.Windows.Forms.ToolBar> control is retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="6a98b-104"><xref:System.Windows.Forms.ToolBar>boutons sont en mesure d’afficher des icônes pour faciliter l’identification par les utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="6a98b-104"><xref:System.Windows.Forms.ToolBar> buttons are able to display icons within them for easy identification by users.</span></span> <span data-ttu-id="6a98b-105">Pour cela ajouter des images à le <xref:System.Windows.Forms.ImageList> composant et en l’associant la <xref:System.Windows.Forms.ToolBar> contrôle.</span><span class="sxs-lookup"><span data-stu-id="6a98b-105">This is achieved through adding images to the <xref:System.Windows.Forms.ImageList> component and associating it with the <xref:System.Windows.Forms.ToolBar> control.</span></span>  
  
 <span data-ttu-id="6a98b-106">La procédure suivante requiert un **Application Windows** projet avec un formulaire contenant un <xref:System.Windows.Forms.ToolBar> contrôle et une <xref:System.Windows.Forms.ImageList> composant.</span><span class="sxs-lookup"><span data-stu-id="6a98b-106">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.ToolBar> control and an <xref:System.Windows.Forms.ImageList> component.</span></span> <span data-ttu-id="6a98b-107">Pour plus d’informations sur la configuration d’un tel projet, consultez [Comment : créer un projet d’Application Windows](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) et [Comment : ajouter des contrôles aux Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="6a98b-107">For information about setting up such a project, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) and [How to: Add Controls to Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6a98b-108">Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.</span><span class="sxs-lookup"><span data-stu-id="6a98b-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="6a98b-109">Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** .</span><span class="sxs-lookup"><span data-stu-id="6a98b-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="6a98b-110">Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="6a98b-110">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-set-an-icon-for-a-toolbar-button-at-design-time"></a><span data-ttu-id="6a98b-111">Pour définir une icône pour un bouton de barre d’outils au moment du design</span><span class="sxs-lookup"><span data-stu-id="6a98b-111">To set an icon for a toolbar button at design time</span></span>  
  
1.  <span data-ttu-id="6a98b-112">Ajouter des images à le <xref:System.Windows.Forms.ImageList> composant.</span><span class="sxs-lookup"><span data-stu-id="6a98b-112">Add images to the <xref:System.Windows.Forms.ImageList> component.</span></span> <span data-ttu-id="6a98b-113">Pour plus d’informations, consultez [Comment : ajouter ou supprimer des Images ImageList avec le concepteur](../../../../docs/framework/winforms/controls/how-to-add-or-remove-imagelist-images-with-the-designer.md).</span><span class="sxs-lookup"><span data-stu-id="6a98b-113">For more information, see [How to: Add or Remove ImageList Images with the Designer](../../../../docs/framework/winforms/controls/how-to-add-or-remove-imagelist-images-with-the-designer.md).</span></span>  
  
2.  <span data-ttu-id="6a98b-114">Sélectionnez le <xref:System.Windows.Forms.ToolBar> contrôle de votre formulaire.</span><span class="sxs-lookup"><span data-stu-id="6a98b-114">Select the <xref:System.Windows.Forms.ToolBar> control on your form.</span></span>  
  
3.  <span data-ttu-id="6a98b-115">Dans le **propriétés** , configurez la <xref:System.Windows.Forms.ToolBar> du contrôle <xref:System.Windows.Forms.ToolBar.ImageList%2A> propriété le <xref:System.Windows.Forms.ImageList> composant.</span><span class="sxs-lookup"><span data-stu-id="6a98b-115">In the **Properties** window, set the <xref:System.Windows.Forms.ToolBar> control's <xref:System.Windows.Forms.ToolBar.ImageList%2A> property to the <xref:System.Windows.Forms.ImageList> component.</span></span>  
  
4.  <span data-ttu-id="6a98b-116">Cliquez sur le <xref:System.Windows.Forms.ToolBar> du contrôle <xref:System.Windows.Forms.ToolBar.Buttons%2A> propriété à sélectionner, puis cliquez sur le bouton de sélection (![capture d’écran de VisualStudioEllipsesButton](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) pour ouvrir la **Éditeur de collections ToolBarButton**.</span><span class="sxs-lookup"><span data-stu-id="6a98b-116">Click the <xref:System.Windows.Forms.ToolBar> control's <xref:System.Windows.Forms.ToolBar.Buttons%2A> property to select it, and click the ellipsis (![VisualStudioEllipsesButton screenshot](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) button to open the **ToolBarButton Collection Editor**.</span></span>  
  
5.  <span data-ttu-id="6a98b-117">Utilisez le **ajouter** bouton pour ajouter des boutons à la <xref:System.Windows.Forms.ToolBar> contrôle.</span><span class="sxs-lookup"><span data-stu-id="6a98b-117">Use the **Add** button to add buttons to the <xref:System.Windows.Forms.ToolBar> control.</span></span>  
  
6.  <span data-ttu-id="6a98b-118">Dans le **propriétés** fenêtre qui s’affiche dans le volet situé à droite de la **éditeur de collections ToolBarButton**, définissez le <xref:System.Windows.Forms.ToolBarButton.ImageIndex%2A> propriété de chaque bouton de barre d’outils à une des valeurs dans la liste, qui est dessiné à partir des images que vous avez ajouté à la <xref:System.Windows.Forms.ImageList> composant.</span><span class="sxs-lookup"><span data-stu-id="6a98b-118">In the **Properties** window that appears in the pane on the right side of the **ToolBarButton Collection Editor**, set the <xref:System.Windows.Forms.ToolBarButton.ImageIndex%2A> property of each toolbar button to one of the values in the list, which is drawn from the images you added to the <xref:System.Windows.Forms.ImageList> component.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a98b-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6a98b-119">See Also</span></span>  
 <xref:System.Windows.Forms.ToolBar>  
 [<span data-ttu-id="6a98b-120">Guide pratique pour déclencher des événements de menu pour les boutons de barre d’outils</span><span class="sxs-lookup"><span data-stu-id="6a98b-120">How to: Trigger Menu Events for Toolbar Buttons</span></span>](../../../../docs/framework/winforms/controls/how-to-trigger-menu-events-for-toolbar-buttons.md)  
 [<span data-ttu-id="6a98b-121">ToolBar, contrôle</span><span class="sxs-lookup"><span data-stu-id="6a98b-121">ToolBar Control</span></span>](../../../../docs/framework/winforms/controls/toolbar-control-windows-forms.md)  
 [<span data-ttu-id="6a98b-122">ImageList, composant</span><span class="sxs-lookup"><span data-stu-id="6a98b-122">ImageList Component</span></span>](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md)
