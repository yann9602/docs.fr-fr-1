---
title: "Vue d’ensemble du contrôle TreeView (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: TreeView
helpviewer_keywords: TreeView control [Windows Forms], about TreeView control
ms.assetid: 0ece823a-9508-478a-bbdb-7d7c3bae51d5
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9bbe8549268c2b67b67184966e938f7d62b766a1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="treeview-control-overview-windows-forms"></a>Vue d’ensemble du contrôle TreeView (Windows Forms)
Avec le contrôle Windows Forms <xref:System.Windows.Forms.TreeView>, vous pouvez présenter une hiérarchie de nœuds aux utilisateurs, un peu comme les fichiers et dossiers sont affichés dans le volet gauche de l'Explorateur Windows du système d'exploitation Windows. Chaque nœud dans l’arborescence peut contenir d’autres nœuds, appelés *nœuds enfants*. Vous pouvez afficher les nœuds parents ou les nœuds qui contiennent des nœuds enfants, sous forme développée ou réduite. Vous pouvez également afficher une arborescence avec des cases à cocher en regard des nœuds en affectant la valeur `true` à la propriété <xref:System.Windows.Forms.TreeView.CheckBoxes%2A> de l'arborescence. Vous pouvez ensuite sélectionner ou désélectionner des nœuds par programmation en affectant la valeur `true` ou `false` à la propriété <xref:System.Windows.Forms.TreeNode.Checked%2A> du nœud.  
  
## <a name="key-properties"></a>Propriétés principales  
 Les principales propriétés du contrôle <xref:System.Windows.Forms.TreeView> sont <xref:System.Windows.Forms.TreeView.Nodes%2A> et <xref:System.Windows.Forms.TreeView.SelectedNode%2A>. La propriété <xref:System.Windows.Forms.TreeView.Nodes%2A> contient la liste des nœuds de niveau supérieur dans l'arborescence. La propriété <xref:System.Windows.Forms.TreeView.SelectedNode%2A> définit le nœud actuellement sélectionné. Vous pouvez afficher des icônes en regard des nœuds. Le contrôle utilise des images du <xref:System.Windows.Forms.ImageList> nommé dans la propriété <xref:System.Windows.Forms.TreeView.ImageList%2A> de l'arborescence. La propriété <xref:System.Windows.Forms.TreeView.ImageIndex%2A> définit l'image par défaut pour les nœuds dans l'arborescence. Pour plus d’informations sur l’affichage des images, consultez [Comment : définir des icônes pour le contrôle TreeView Windows Forms](../../../../docs/framework/winforms/controls/how-to-set-icons-for-the-windows-forms-treeview-control.md). Si vous utilisez [!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)], vous avez accès à une grande bibliothèque d'images standard que vous pouvez utiliser avec le contrôle <xref:System.Windows.Forms.TreeView>.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.TreeView>  
 [TreeView, contrôle](../../../../docs/framework/winforms/controls/treeview-control-windows-forms.md)  
 [Guide pratique pour définir des icônes pour le contrôle TreeView Windows Forms](../../../../docs/framework/winforms/controls/how-to-set-icons-for-the-windows-forms-treeview-control.md)  
 [Guide pratique pour ajouter et supprimer des nœuds avec le contrôle TreeView Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md)  
 [Guide pratique pour itérer au sein de tous les nœuds d’un contrôle TreeView Windows Forms](../../../../docs/framework/winforms/controls/how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)  
 [Guide pratique pour identifier le nœud de TreeView sur lequel un clic est effectué](../../../../docs/framework/winforms/controls/how-to-determine-which-treeview-node-was-clicked-windows-forms.md)  
 [Guide pratique pour ajouter des informations personnalisées à un contrôle TreeView ou ListView (Windows Forms)](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)
