---
title: "Comment : attacher un menu contextuel à un TreeNode à l’aide du concepteur"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- shortcut menus [Windows Forms], attaching to TreeNodes
- TreeNode [Windows Forms], attaching a shortcut menu using Designer
ms.assetid: 8e45e184-1313-4f8f-90ff-2cd5789b2268
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3acc1a731fa584a17c8a96f8a02986a504cd302d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-attach-a-shortcut-menu-to-a-treenode-using-the-designer"></a><span data-ttu-id="3e761-102">Comment : attacher un menu contextuel à un TreeNode à l’aide du concepteur</span><span class="sxs-lookup"><span data-stu-id="3e761-102">How to: Attach a Shortcut Menu to a TreeNode Using the Designer</span></span>
<span data-ttu-id="3e761-103">Windows Forms <xref:System.Windows.Forms.TreeView> contrôle affiche une hiérarchie de nœuds, semblables aux fichiers et dossiers affichés dans le volet gauche de la fonctionnalité de l’Explorateur Windows dans les systèmes d’exploitation Windows.</span><span class="sxs-lookup"><span data-stu-id="3e761-103">The Windows Forms <xref:System.Windows.Forms.TreeView> control displays a hierarchy of nodes, similar to the files and folders displayed in the left pane of the Windows Explorer feature in Windows operating systems.</span></span> <span data-ttu-id="3e761-104">En définissant le <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> propriété, vous pouvez fournir opérations contextuelles à l’utilisateur lorsque leur droit le <xref:System.Windows.Forms.TreeView> contrôle.</span><span class="sxs-lookup"><span data-stu-id="3e761-104">By setting the <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> property, you can provide context-sensitive operations to the user when they right-click the <xref:System.Windows.Forms.TreeView> control.</span></span> <span data-ttu-id="3e761-105">En associant un <xref:System.Windows.Forms.ContextMenuStrip> composant avec une personne <xref:System.Windows.Forms.TreeNode> éléments, vous pouvez ajouter un niveau personnalisé de fonctionnalités de menu contextuel à votre <xref:System.Windows.Forms.TreeView> contrôles.</span><span class="sxs-lookup"><span data-stu-id="3e761-105">By associating a <xref:System.Windows.Forms.ContextMenuStrip> component with individual <xref:System.Windows.Forms.TreeNode> items, you can add a customized level of shortcut menu functionality to your <xref:System.Windows.Forms.TreeView> controls.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3e761-106">Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.</span><span class="sxs-lookup"><span data-stu-id="3e761-106">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="3e761-107">Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** .</span><span class="sxs-lookup"><span data-stu-id="3e761-107">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="3e761-108">Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="3e761-108">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-associate-a-shortcut-menu-with-a-treenode-at-design-time"></a><span data-ttu-id="3e761-109">Pour associer un menu contextuel à un TreeNode au moment du design</span><span class="sxs-lookup"><span data-stu-id="3e761-109">To associate a shortcut menu with a TreeNode at design time</span></span>  
  
1.  <span data-ttu-id="3e761-110">Ajouter un <xref:System.Windows.Forms.TreeView> le contrôle à votre formulaire, puis ajouter des nœuds à la <xref:System.Windows.Forms.TreeView> en fonction des besoins.</span><span class="sxs-lookup"><span data-stu-id="3e761-110">Add a <xref:System.Windows.Forms.TreeView> control to your form, and then add nodes to the <xref:System.Windows.Forms.TreeView> as needed.</span></span> <span data-ttu-id="3e761-111">Pour plus d’informations, consultez [Comment : ajouter et supprimer des nœuds avec le contrôle TreeView Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md).</span><span class="sxs-lookup"><span data-stu-id="3e761-111">For more information, see [How to: Add and Remove Nodes with the Windows Forms TreeView Control](../../../../docs/framework/winforms/controls/how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md).</span></span>  
  
2.  <span data-ttu-id="3e761-112">Ajouter un <xref:System.Windows.Forms.ContextMenuStrip> à votre formulaire, puis ajoutez des éléments de menu au menu contextuel qui représentent des opérations au niveau du nœud vous souhaitez rendre disponible au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="3e761-112">Add a <xref:System.Windows.Forms.ContextMenuStrip> component to your form, and then add menu items to the shortcut menu that represent node-level operations you wish to make available at run time.</span></span> <span data-ttu-id="3e761-113">Pour plus d’informations, consultez [Comment : ajouter des éléments de Menu à un ContextMenuStrip](../../../../docs/framework/winforms/controls/how-to-add-menu-items-to-a-contextmenustrip.md).</span><span class="sxs-lookup"><span data-stu-id="3e761-113">For more information, see [How to: Add Menu Items to a ContextMenuStrip](../../../../docs/framework/winforms/controls/how-to-add-menu-items-to-a-contextmenustrip.md).</span></span>  
  
3.  <span data-ttu-id="3e761-114">Rouvrez le **TreeNode** boîte de dialogue pour le <xref:System.Windows.Forms.TreeView> contrôle, sélectionnez le nœud à modifier et définir son <xref:System.Windows.Forms.ContextMenuStrip> propriété dans le menu contextuel que vous avez ajouté.</span><span class="sxs-lookup"><span data-stu-id="3e761-114">Reopen the **TreeNodeEditor** dialog box for the <xref:System.Windows.Forms.TreeView> control, select the node to edit, and set its <xref:System.Windows.Forms.ContextMenuStrip> property to the shortcut menu that you added.</span></span>  
  
4.  <span data-ttu-id="3e761-115">Lorsque cette propriété est définie, le menu contextuel s’affichera lorsque vous cliquez sur le nœud.</span><span class="sxs-lookup"><span data-stu-id="3e761-115">When this property is set, the shortcut menu will be displayed when you right-click the node.</span></span>  
  
     <span data-ttu-id="3e761-116">En outre, vous souhaitez écrire du code pour gérer les <xref:System.Windows.Forms.ToolStripItem.Click> événements pour ces éléments de menu.</span><span class="sxs-lookup"><span data-stu-id="3e761-116">Additionally, you will want to write code to handle the <xref:System.Windows.Forms.ToolStripItem.Click> events for these menu items.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e761-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3e761-117">See Also</span></span>  
 [<span data-ttu-id="3e761-118">TreeView, contrôle</span><span class="sxs-lookup"><span data-stu-id="3e761-118">TreeView Control</span></span>](../../../../docs/framework/winforms/controls/treeview-control-windows-forms.md)  
 [<span data-ttu-id="3e761-119">Vue d’ensemble du contrôle TreeView</span><span class="sxs-lookup"><span data-stu-id="3e761-119">TreeView Control Overview</span></span>](../../../../docs/framework/winforms/controls/treeview-control-overview-windows-forms.md)  
 [<span data-ttu-id="3e761-120">ContextMenuStrip, contrôle</span><span class="sxs-lookup"><span data-stu-id="3e761-120">ContextMenuStrip Control</span></span>](../../../../docs/framework/winforms/controls/contextmenustrip-control.md)
