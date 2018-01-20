---
title: "Comment : ajouter et supprimer des nœuds avec le contrôle TreeView Windows Forms à l’aide du concepteur"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- examples [Windows Forms], TreeView control
- TreeView control [Windows Forms], removing nodes
- tree nodes in TreeView control
- TreeView control [Windows Forms], adding nodes
ms.assetid: 35bf1750-045e-4ec5-97cb-b47b0dbdaa2c
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 067c36daef9649ee9a5da7945aa0202fb684b830
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control-using-the-designer"></a>Comment : ajouter et supprimer des nœuds avec le contrôle TreeView Windows Forms à l’aide du concepteur
Étant donné que le Windows Forms <xref:System.Windows.Forms.TreeView> contrôle affiche les nœuds de manière hiérarchique, lors de l’ajout d’un nœud, vous devez faire attention à ce qui est son nœud parent.  
  
 La procédure suivante requiert un **Application Windows** projet avec un formulaire contenant un <xref:System.Windows.Forms.TreeView> contrôle. Pour plus d’informations sur la configuration d’un tel projet, consultez [Comment : créer un projet d’Application Windows](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) et [Comment : ajouter des contrôles aux Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-add-or-remove-nodes-in-the-designer"></a>Pour ajouter ou supprimer des nœuds dans le Concepteur  
  
1.  Sélectionnez le contrôle <xref:System.Windows.Forms.TreeView>.  
  
2.  Dans le **propriétés** fenêtre, cliquez sur le **points de suspension** (![capture d’écran de VisualStudioEllipsesButton](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) situé en regard le <xref:System.Windows.Forms.TreeView.Nodes%2A> propriété.  
  
     Le **Éditeur TreeNode** s’affiche.  
  
3.  Pour ajouter des nœuds, un nœud racine doit exister. s’il n’existe pas, vous devez d’abord ajouter une racine en cliquant sur le **ajouter la racine** bouton. Vous pouvez ensuite ajouter des nœuds enfants en sélectionnant la racine ou un autre nœud en cliquant sur le **ajouter un enfant** bouton.  
  
4.  Pour supprimer un nœud, sélectionnez le nœud à supprimer, puis cliquez sur le **supprimer** bouton.  
  
## <a name="see-also"></a>Voir aussi  
 [TreeView, contrôle](../../../../docs/framework/winforms/controls/treeview-control-windows-forms.md)  
 [Vue d’ensemble du contrôle TreeView](../../../../docs/framework/winforms/controls/treeview-control-overview-windows-forms.md)  
 [Guide pratique pour définir des icônes pour le contrôle TreeView Windows Forms](../../../../docs/framework/winforms/controls/how-to-set-icons-for-the-windows-forms-treeview-control.md)  
 [Guide pratique pour itérer au sein de tous les nœuds d’un contrôle TreeView Windows Forms](../../../../docs/framework/winforms/controls/how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)  
 [Guide pratique pour identifier le nœud de TreeView sur lequel un clic est effectué](../../../../docs/framework/winforms/controls/how-to-determine-which-treeview-node-was-clicked-windows-forms.md)  
 [Guide pratique pour ajouter des informations personnalisées à un contrôle TreeView ou ListView (Windows Forms)](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)
