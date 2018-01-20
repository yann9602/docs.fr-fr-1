---
title: "Comment : regrouper des éléments dans un contrôle ListView Windows Forms à l'aide du concepteur"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ListView control [Windows Forms], grouping items
- grouping
- groups [Windows Forms], in Windows Forms controls
ms.assetid: 8b615000-69d9-4c64-acaf-b54fa09b69e3
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f5e86ecdad66c9e58d691b18126c1fbf782e3130
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-group-items-in-a-windows-forms-listview-control-using-the-designer"></a><span data-ttu-id="43100-102">Comment : regrouper des éléments dans un contrôle ListView Windows Forms à l'aide du concepteur</span><span class="sxs-lookup"><span data-stu-id="43100-102">How to: Group Items in a Windows Forms ListView Control Using the Designer</span></span>
<span data-ttu-id="43100-103">La fonctionnalité de regroupement du <xref:System.Windows.Forms.ListView> contrôle permet de vous permettent d’afficher des jeux d’éléments liés dans les groupes.</span><span class="sxs-lookup"><span data-stu-id="43100-103">The grouping feature of the <xref:System.Windows.Forms.ListView> control enables you to display related sets of items in groups.</span></span> <span data-ttu-id="43100-104">Ces groupes sont séparés sur l’écran par des en-têtes de groupe horizontal qui contiennent les titres de groupe.</span><span class="sxs-lookup"><span data-stu-id="43100-104">These groups are separated on the screen by horizontal group headers that contain the group titles.</span></span> <span data-ttu-id="43100-105">Vous pouvez utiliser <xref:System.Windows.Forms.ListView> groupes pour faciliter la navigation dans les longues listes en regroupant les éléments par ordre alphabétique, par date, ou par tout autre regroupement logique.</span><span class="sxs-lookup"><span data-stu-id="43100-105">You can use <xref:System.Windows.Forms.ListView> groups to make navigating large lists easier by grouping items alphabetically, by date, or by any other logical grouping.</span></span> <span data-ttu-id="43100-106">L’illustration suivante montre certains éléments groupés.</span><span class="sxs-lookup"><span data-stu-id="43100-106">The following image shows some grouped items.</span></span>  
  
 <span data-ttu-id="43100-107">![Groupes ListView](../../../../docs/framework/winforms/controls/media/listviewgroups.gif "ListViewGroups")</span><span class="sxs-lookup"><span data-stu-id="43100-107">![ListView Groups](../../../../docs/framework/winforms/controls/media/listviewgroups.gif "ListViewGroups")</span></span>  
  
 <span data-ttu-id="43100-108">La procédure suivante requiert un **Application Windows** projet avec un formulaire contenant un <xref:System.Windows.Forms.ListView> contrôle.</span><span class="sxs-lookup"><span data-stu-id="43100-108">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.ListView> control.</span></span> <span data-ttu-id="43100-109">Pour plus d’informations sur la configuration d’un tel projet, consultez [Comment : créer un projet d’Application Windows](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) et [Comment : ajouter des contrôles aux Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="43100-109">For information about setting up such a project, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) and [How to: Add Controls to Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span></span>  
  
 <span data-ttu-id="43100-110">Pour activer le regroupement, vous devez d’abord créer un ou plusieurs <xref:System.Windows.Forms.ListViewGroup> objets dans le concepteur ou par programme.</span><span class="sxs-lookup"><span data-stu-id="43100-110">To enable grouping, you must first create one or more <xref:System.Windows.Forms.ListViewGroup> objects either in the designer or programmatically.</span></span> <span data-ttu-id="43100-111">Une fois qu’un groupe a été défini, vous pouvez assigner des éléments à ce dernier.</span><span class="sxs-lookup"><span data-stu-id="43100-111">Once a group has been defined, you can assign items to it.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="43100-112"><xref:System.Windows.Forms.ListView>les groupes sont disponibles uniquement sur [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] lorsque votre application appelle la <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> (méthode).</span><span class="sxs-lookup"><span data-stu-id="43100-112"><xref:System.Windows.Forms.ListView> groups are available only on [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] when your application calls the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="43100-113">Sur les systèmes d’exploitation antérieurs, tout code concernant les groupes n’a aucun effet et les groupes n’apparaîtront pas.</span><span class="sxs-lookup"><span data-stu-id="43100-113">On earlier operating systems, any code relating to groups has no effect and the groups will not appear.</span></span> <span data-ttu-id="43100-114">Pour plus d'informations, consultez <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="43100-114">For more information, see <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>.</span></span>  
>   
>  <span data-ttu-id="43100-115">Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.</span><span class="sxs-lookup"><span data-stu-id="43100-115">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="43100-116">Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** .</span><span class="sxs-lookup"><span data-stu-id="43100-116">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="43100-117">Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="43100-117">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-add-or-remove-groups-in-the-designer"></a><span data-ttu-id="43100-118">Pour ajouter ou supprimer des groupes dans le Concepteur</span><span class="sxs-lookup"><span data-stu-id="43100-118">To add or remove groups in the designer</span></span>  
  
1.  <span data-ttu-id="43100-119">Dans le **propriétés** fenêtre, cliquez sur le **points de suspension** (![capture d’écran de VisualStudioEllipsesButton](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) situé en regard le <xref:System.Windows.Forms.ListView.Groups%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="43100-119">In the **Properties** window, click the **Ellipsis** (![VisualStudioEllipsesButton screenshot](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) button next to the <xref:System.Windows.Forms.ListView.Groups%2A> property.</span></span>  
  
     <span data-ttu-id="43100-120">Le **éditeur de collections ListViewGroup** s’affiche.</span><span class="sxs-lookup"><span data-stu-id="43100-120">The **ListViewGroup Collection Editor** appears.</span></span>  
  
2.  <span data-ttu-id="43100-121">Pour ajouter un groupe, cliquez sur le **ajouter** bouton.</span><span class="sxs-lookup"><span data-stu-id="43100-121">To add a group, click the **Add** button.</span></span> <span data-ttu-id="43100-122">Vous pouvez ensuite définir les propriétés du nouveau groupe, tel que le <xref:System.Windows.Forms.ListViewGroup.Header%2A> et <xref:System.Windows.Forms.ListViewGroup.HeaderAlignment%2A> propriétés.</span><span class="sxs-lookup"><span data-stu-id="43100-122">You can then set properties of the new group, such as the <xref:System.Windows.Forms.ListViewGroup.Header%2A> and <xref:System.Windows.Forms.ListViewGroup.HeaderAlignment%2A> properties.</span></span> <span data-ttu-id="43100-123">Pour supprimer un groupe, sélectionnez-la et cliquez sur le **supprimer** bouton.</span><span class="sxs-lookup"><span data-stu-id="43100-123">To remove a group, select it and click the **Remove** button.</span></span>  
  
### <a name="to-assign-items-to-groups-in-the-designer"></a><span data-ttu-id="43100-124">Pour affecter des éléments aux groupes dans le Concepteur</span><span class="sxs-lookup"><span data-stu-id="43100-124">To assign items to groups in the designer</span></span>  
  
1.  <span data-ttu-id="43100-125">Dans le **propriétés** fenêtre, cliquez sur le **points de suspension** (![capture d’écran de VisualStudioEllipsesButton](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) situé en regard le <xref:System.Windows.Forms.ListView.Items%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="43100-125">In the **Properties** window, click the **Ellipsis** (![VisualStudioEllipsesButton screenshot](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) button next to the <xref:System.Windows.Forms.ListView.Items%2A> property.</span></span>  
  
     <span data-ttu-id="43100-126">Le **éditeur de collections ListViewItem** s’affiche.</span><span class="sxs-lookup"><span data-stu-id="43100-126">The **ListViewItem Collection Editor** appears.</span></span>  
  
2.  <span data-ttu-id="43100-127">Pour ajouter un nouvel élément, cliquez sur le **ajouter** bouton.</span><span class="sxs-lookup"><span data-stu-id="43100-127">To add a new item, click the **Add** button.</span></span> <span data-ttu-id="43100-128">Vous pouvez ensuite définir les propriétés du nouvel élément, telles que la <xref:System.Windows.Forms.ListViewItem.Text%2A> et <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A> propriétés.</span><span class="sxs-lookup"><span data-stu-id="43100-128">You can then set properties of the new item, such as the <xref:System.Windows.Forms.ListViewItem.Text%2A> and <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A> properties.</span></span>  
  
3.  <span data-ttu-id="43100-129">Sélectionnez le <xref:System.Windows.Forms.ListViewItem.Group%2A> propriété et choisissez un groupe dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="43100-129">Select the <xref:System.Windows.Forms.ListViewItem.Group%2A> property and choose a group from the drop-down list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43100-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="43100-130">See Also</span></span>  
 <xref:System.Windows.Forms.ListView>  
 <xref:System.Windows.Forms.ListView.Groups%2A>  
 <xref:System.Windows.Forms.ListViewGroup>  
 [<span data-ttu-id="43100-131">Contrôle ListView</span><span class="sxs-lookup"><span data-stu-id="43100-131">ListView Control</span></span>](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)  
 [<span data-ttu-id="43100-132">Vue d’ensemble du contrôle ListView</span><span class="sxs-lookup"><span data-stu-id="43100-132">ListView Control Overview</span></span>](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)  
 [<span data-ttu-id="43100-133">Fonctionnalités de Windows XP et contrôles Windows Forms</span><span class="sxs-lookup"><span data-stu-id="43100-133">Windows XP Features and Windows Forms Controls</span></span>](http://msdn.microsoft.com/library/bc7fab94-fce9-4bf1-a8ad-a5837c91c3c0)  
 [<span data-ttu-id="43100-134">Guide pratique pour ajouter et supprimer des éléments avec le contrôle ListView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="43100-134">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
