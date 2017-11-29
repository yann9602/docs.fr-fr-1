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
ms.openlocfilehash: e1ec1b0236aab0f4ac61cb58d4fe006d17594e17
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-attach-a-shortcut-menu-to-a-treenode-using-the-designer"></a>Comment : attacher un menu contextuel à un TreeNode à l’aide du concepteur
Windows Forms <xref:System.Windows.Forms.TreeView> contrôle affiche une hiérarchie de nœuds, semblables aux fichiers et dossiers affichés dans le volet gauche de la fonctionnalité de l’Explorateur Windows dans les systèmes d’exploitation Windows. En définissant le <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> propriété, vous pouvez fournir opérations contextuelles à l’utilisateur lorsque leur droit le <xref:System.Windows.Forms.TreeView> contrôle. En associant un <xref:System.Windows.Forms.ContextMenuStrip> composant avec une personne <xref:System.Windows.Forms.TreeNode> éléments, vous pouvez ajouter un niveau personnalisé de fonctionnalités de menu contextuel à votre <xref:System.Windows.Forms.TreeView> contrôles.  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-associate-a-shortcut-menu-with-a-treenode-at-design-time"></a>Pour associer un menu contextuel à un TreeNode au moment du design  
  
1.  Ajouter un <xref:System.Windows.Forms.TreeView> le contrôle à votre formulaire, puis ajouter des nœuds à la <xref:System.Windows.Forms.TreeView> en fonction des besoins. Pour plus d’informations, consultez [Comment : ajouter et supprimer des nœuds avec le contrôle TreeView Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md).  
  
2.  Ajouter un <xref:System.Windows.Forms.ContextMenuStrip> à votre formulaire, puis ajoutez des éléments de menu au menu contextuel qui représentent des opérations au niveau du nœud vous souhaitez rendre disponible au moment de l’exécution. Pour plus d’informations, consultez [Comment : ajouter des éléments de Menu à un ContextMenuStrip](../../../../docs/framework/winforms/controls/how-to-add-menu-items-to-a-contextmenustrip.md).  
  
3.  Rouvrez le **TreeNode** boîte de dialogue pour le <xref:System.Windows.Forms.TreeView> contrôle, sélectionnez le nœud à modifier et définir son <xref:System.Windows.Forms.ContextMenuStrip> propriété dans le menu contextuel que vous avez ajouté.  
  
4.  Lorsque cette propriété est définie, le menu contextuel s’affichera lorsque vous cliquez sur le nœud.  
  
     En outre, vous souhaitez écrire du code pour gérer les <xref:System.Windows.Forms.ToolStripItem.Click> événements pour ces éléments de menu.  
  
## <a name="see-also"></a>Voir aussi  
 [TreeView, contrôle](../../../../docs/framework/winforms/controls/treeview-control-windows-forms.md)  
 [Vue d’ensemble du contrôle TreeView](../../../../docs/framework/winforms/controls/treeview-control-overview-windows-forms.md)  
 [ContextMenuStrip, contrôle](../../../../docs/framework/winforms/controls/contextmenustrip-control.md)
