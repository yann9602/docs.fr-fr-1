---
title: "Comment : grouper des éléments dans un contrôle ListView Windows Forms"
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
helpviewer_keywords:
- ListView control [Windows Forms], grouping items
- lists [Windows Forms], grouping items
- grouping
- list views [Windows Forms], grouping items
- groups
- groups [Windows Forms], in Windows Forms controls
ms.assetid: 610416a1-8da4-436c-af19-5f19e654769b
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c22134513c2c6a3ff2bc621e68f546b7bcc93ba9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-group-items-in-a-windows-forms-listview-control"></a><span data-ttu-id="b1036-102">Comment : grouper des éléments dans un contrôle ListView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b1036-102">How to: Group Items in a Windows Forms ListView Control</span></span>
<span data-ttu-id="b1036-103">Avec la fonctionnalité de regroupement du <xref:System.Windows.Forms.ListView> (contrôle), vous pouvez afficher des jeux d’éléments liés dans les groupes.</span><span class="sxs-lookup"><span data-stu-id="b1036-103">With the grouping feature of the <xref:System.Windows.Forms.ListView> control, you can display related sets of items in groups.</span></span> <span data-ttu-id="b1036-104">Ces groupes sont séparés sur l’écran par des en-têtes de groupe horizontal qui contiennent les titres de groupe.</span><span class="sxs-lookup"><span data-stu-id="b1036-104">These groups are separated on the screen by horizontal group headers that contain the group titles.</span></span> <span data-ttu-id="b1036-105">Vous pouvez utiliser <xref:System.Windows.Forms.ListView> groupes pour faciliter la navigation dans les longues listes en regroupant les éléments par ordre alphabétique, par date, ou par tout autre regroupement logique.</span><span class="sxs-lookup"><span data-stu-id="b1036-105">You can use <xref:System.Windows.Forms.ListView> groups to make navigating large lists easier by grouping items alphabetically, by date, or by any other logical grouping.</span></span> <span data-ttu-id="b1036-106">L’illustration suivante montre certains éléments groupés.</span><span class="sxs-lookup"><span data-stu-id="b1036-106">The following image shows some grouped items.</span></span>  
  
 <span data-ttu-id="b1036-107">![Groupes ListView](../../../../docs/framework/winforms/controls/media/listviewgroups.gif "ListViewGroups")</span><span class="sxs-lookup"><span data-stu-id="b1036-107">![ListView Groups](../../../../docs/framework/winforms/controls/media/listviewgroups.gif "ListViewGroups")</span></span>  
<span data-ttu-id="b1036-108">Éléments ListView regroupés</span><span class="sxs-lookup"><span data-stu-id="b1036-108">ListView grouped items</span></span>  
  
 <span data-ttu-id="b1036-109">Pour activer le regroupement, vous devez d’abord créer un ou plusieurs groupes dans le concepteur ou par programme.</span><span class="sxs-lookup"><span data-stu-id="b1036-109">To enable grouping, you must first create one or more groups either in the designer or programmatically.</span></span> <span data-ttu-id="b1036-110">Après avoir défini un groupe, vous pouvez affecter <xref:System.Windows.Forms.ListView> éléments à des groupes.</span><span class="sxs-lookup"><span data-stu-id="b1036-110">After a group has been defined, you can assign <xref:System.Windows.Forms.ListView> items to groups.</span></span> <span data-ttu-id="b1036-111">Vous pouvez également déplacer des éléments d’un groupe à un autre par programmation.</span><span class="sxs-lookup"><span data-stu-id="b1036-111">You can also move items from one group to another programmatically.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b1036-112"><xref:System.Windows.Forms.ListView>les groupes sont disponibles uniquement sur [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] lorsque votre application appelle la <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> (méthode).</span><span class="sxs-lookup"><span data-stu-id="b1036-112"><xref:System.Windows.Forms.ListView> groups are available only on [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] when your application calls the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="b1036-113">Sur les systèmes d’exploitation antérieurs, tout code concernant les groupes n’a aucun effet et les groupes n’apparaîtront pas.</span><span class="sxs-lookup"><span data-stu-id="b1036-113">On earlier operating systems, any code relating to groups has no effect and the groups will not appear.</span></span> <span data-ttu-id="b1036-114">Pour plus d'informations, consultez <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b1036-114">For more information, see <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>.</span></span>  
  
### <a name="to-add-groups"></a><span data-ttu-id="b1036-115">Pour ajouter des groupes</span><span class="sxs-lookup"><span data-stu-id="b1036-115">To add groups</span></span>  
  
1.  <span data-ttu-id="b1036-116">Utilisez la méthode <xref:System.Windows.Forms.ListViewGroupCollection.Add%2A> de la collection <xref:System.Windows.Forms.ListView.Groups%2A>.</span><span class="sxs-lookup"><span data-stu-id="b1036-116">Use the <xref:System.Windows.Forms.ListViewGroupCollection.Add%2A> method of the <xref:System.Windows.Forms.ListView.Groups%2A> collection.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#21)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#21)]  
  
### <a name="to-remove-groups"></a><span data-ttu-id="b1036-117">Pour supprimer des groupes</span><span class="sxs-lookup"><span data-stu-id="b1036-117">To remove groups</span></span>  
  
1.  <span data-ttu-id="b1036-118">Utilisez le <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> ou <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> méthode de la <xref:System.Windows.Forms.ListView.Groups%2A> collection.</span><span class="sxs-lookup"><span data-stu-id="b1036-118">Use the <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> or <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> method of the <xref:System.Windows.Forms.ListView.Groups%2A> collection.</span></span>  
  
     <span data-ttu-id="b1036-119">Le <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> méthode supprime un groupe unique ; le <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> méthode supprime tous les groupes de la liste.</span><span class="sxs-lookup"><span data-stu-id="b1036-119">The <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> method removes a single group; the <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> method removes all groups from the list.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b1036-120">Suppression d’un groupe ne supprime pas les éléments dans ce groupe.</span><span class="sxs-lookup"><span data-stu-id="b1036-120">Removing a group does not remove the items within that group.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#22](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#22)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#22](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#22)]  
  
### <a name="to-assign-items-to-groups-or-move-items-between-groups"></a><span data-ttu-id="b1036-121">Pour assigner des éléments aux groupes ou déplacer des éléments entre les groupes</span><span class="sxs-lookup"><span data-stu-id="b1036-121">To assign items to groups or move items between groups</span></span>  
  
1.  <span data-ttu-id="b1036-122">Définir le <xref:System.Windows.Forms.ListViewItem.Group%2A?displayProperty=nameWithType> propriété des éléments individuels.</span><span class="sxs-lookup"><span data-stu-id="b1036-122">Set the <xref:System.Windows.Forms.ListViewItem.Group%2A?displayProperty=nameWithType> property of individual items.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#23](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#23)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#23](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#23)]  
  
## <a name="see-also"></a><span data-ttu-id="b1036-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b1036-123">See Also</span></span>  
 <xref:System.Windows.Forms.ListView>  
 <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.ListViewGroup>  
 [<span data-ttu-id="b1036-124">Contrôle ListView</span><span class="sxs-lookup"><span data-stu-id="b1036-124">ListView Control</span></span>](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)  
 [<span data-ttu-id="b1036-125">Vue d’ensemble du contrôle ListView</span><span class="sxs-lookup"><span data-stu-id="b1036-125">ListView Control Overview</span></span>](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)  
 [<span data-ttu-id="b1036-126">Fonctionnalités de Windows XP et contrôles Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b1036-126">Windows XP Features and Windows Forms Controls</span></span>](http://msdn.microsoft.com/en-us/bc7fab94-fce9-4bf1-a8ad-a5837c91c3c0)  
 [<span data-ttu-id="b1036-127">Guide pratique pour ajouter et supprimer des éléments avec le contrôle ListView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b1036-127">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
