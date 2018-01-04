---
title: "Comment : ajouter des colonnes au contrôle ListView Windows Forms à l'aide du concepteur"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ListView control [Windows Forms], adding column headers
- columns [Windows Forms], adding to ListView controls
ms.assetid: 5b1a8b4d-587e-479a-95c1-f9b90884f13a
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bb249ba360ebaf9ed6a2b799ec4ebcccff9f8d58
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-columns-to-the-windows-forms-listview-control-using-the-designer"></a>Comment : ajouter des colonnes au contrôle ListView Windows Forms à l'aide du concepteur
Windows Forms <xref:System.Windows.Forms.ListView> contrôle peut afficher plusieurs colonnes pour chaque liste élément lors de la **détails** vue. Vous pouvez utiliser les colonnes pour afficher plusieurs types d’informations sur chaque élément de liste. Par exemple, une liste de fichiers peut afficher le nom de fichier, type de fichier, taille et date de que dernière modification du fichier. Pour plus d’informations sur le remplissage des colonnes une fois qu’elles sont créées, consultez [Comment : afficher des sous-éléments en colonnes avec le contrôle ListView Windows Forms](../../../../docs/framework/winforms/controls/how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md).  
  
 La procédure suivante requiert un **Application Windows** projet avec un formulaire contenant un <xref:System.Windows.Forms.ListView> contrôle. Pour plus d’informations sur la configuration d’un tel projet, consultez [Comment : créer un projet d’Application Windows](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa) et [Comment : ajouter des contrôles aux Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-add-columns-in-the-designer"></a>Pour ajouter des colonnes dans le Concepteur  
  
1.  Dans le **propriétés** fenêtre, définissez du contrôle <xref:System.Windows.Forms.ListView.View%2A> propriété <xref:System.Windows.Forms.View.Details>.  
  
2.  Dans le **propriétés** fenêtre, cliquez sur le **points de suspension** bouton (![capture d’écran de VisualStudioEllipsesButton](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) à côté le <xref:System.Windows.Forms.ListView.Columns%2A> propriété.  
  
     Le **éditeur de Collection ColumnHeader** s’affiche.  
  
3.  Utilisez le **ajouter** bouton pour ajouter de nouvelles colonnes. Vous pouvez ensuite sélectionner l’en-tête de colonne et définir son texte (la légende de la colonne) ainsi que l’alignement du texte et la largeur.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble du contrôle ListView](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)  
 [Guide pratique pour ajouter et supprimer des éléments avec le contrôle ListView Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)  
 [Guide pratique pour afficher des sous-éléments en colonnes avec le contrôle ListView Windows Forms](../../../../docs/framework/winforms/controls/how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)  
 [Guide pratique pour afficher des icônes pour le contrôle ListView Windows Forms](../../../../docs/framework/winforms/controls/how-to-display-icons-for-the-windows-forms-listview-control.md)  
 [Guide pratique pour ajouter des informations personnalisées à un contrôle TreeView ou ListView (Windows Forms)](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)
