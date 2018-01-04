---
title: "Comment : lier des données au contrôle DataGridView Windows Forms à l'aide du concepteur"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms controls, binding to a data source
- data sources [Windows Forms], binding to Windows Forms controls
- DataGridView control [Windows Forms], data binding
ms.assetid: f4f46009-cec2-441b-8668-6b5af057558b
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a31b407360467f37c2e60b1a3f4f4c72e80e13a1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-bind-data-to-the-windows-forms-datagridview-control-using-the-designer"></a>Comment : lier des données au contrôle DataGridView Windows Forms à l'aide du concepteur
Vous pouvez utiliser le concepteur pour connecter un <xref:System.Windows.Forms.DataGridView> contrôle aux sources de données de plusieurs types différents, y compris les bases de données, des objets métier ou des services Web. Lorsque vous liez le contrôle à une source de données à l’aide du concepteur, le contrôle est automatiquement lié à un <xref:System.Windows.Forms.BindingSource> composant qui représente la source de données. En outre, les colonnes sont générées automatiquement dans le contrôle pour faire correspondre les informations de schéma fournies par la source de données.  
  
 Après avoir généré les colonnes, vous pouvez les modifier pour répondre à vos besoins. Par exemple, vous pouvez supprimer ou masquer des colonnes qui ne vous intéressent pas dans l’affichage, vous pouvez réorganiser les colonnes, ou vous pouvez modifier les types de colonnes. Pour plus d’informations sur la modification des colonnes, consultez les rubriques répertoriées dans la section Voir aussi.  
  
 Vous pouvez également lier plusieurs <xref:System.Windows.Forms.DataGridView> contrôles dans les tables liées pour créer des relations maître/détail. Dans cette configuration, un contrôle affiche une table parent et un autre contrôle affiche uniquement les lignes d’une table enfant qui sont liées à la ligne actuelle dans la table parent. Pour plus d’informations, consultez la page [Comment : afficher des données connexes dans une application Windows Forms](http://msdn.microsoft.com/library/60b1f1ec-6257-42ab-83f0-06d54ed364fd).  
  
 La procédure suivante requiert un **Application Windows** projet avec un formulaire qui contient un <xref:System.Windows.Forms.DataGridView> ou les deux contrôles pour une relation maître/détail. Pour plus d’informations sur le démarrage d’un tel projet, consultez les pages [Comment : créer un projet d’application Windows](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa) et [Comment : ajouter des contrôles à des Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-bind-the-control-to-a-data-source"></a>Pour lier le contrôle à une source de données  
  
1.  Cliquez sur le glyphe de balise active (![glyphe de balise active](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) dans le coin supérieur droit de la <xref:System.Windows.Forms.DataGridView> contrôle.  
  
2.  Cliquez sur la flèche déroulante correspondant à l’option **Choisir la Source de données**.  
  
3.  Si votre projet ne dispose pas déjà d’une source de données, cliquez **Ajouter la source de données projet** et suivez les étapes indiquées par l’Assistant.  
  
     Pour plus d’informations, consultez la page [Assistant Configuration de source de données](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f). Votre nouvelle source de données s’affiche dans la liste déroulante **Choisir la source de données**. Si votre nouvelle source de données contient un seul membre, comme une table de base de données unique, le contrôle est automatiquement lié à ce membre. Sinon, passez à l'étape suivante.  
  
4.  Développez les nœuds **Autres sources de données** et **Sources de données du projet** si cela n’est pas déjà fait, puis sélectionnez la source de données à laquelle lier le contrôle.  
  
5.  Si votre source de données contient plusieurs membres, par exemple si vous avez créé un <xref:System.Data.DataSet?displayProperty=nameWithType> qui contient plusieurs tables, développez la source de données, puis sélectionnez le membre spécifique à lier.  
  
6.  Pour créer une relation maître/détail, dans le **choisir la Source de données** une seconde fenêtre déroulante <xref:System.Windows.Forms.DataGridView> contrôler, développez le <xref:System.Windows.Forms.BindingSource> créé pour la table parente, puis sélectionnez la table enfant connexe dans la liste indiqué.  
  
    > [!NOTE]
    >  Si votre projet a déjà une source de données, vous pouvez également utiliser la fenêtre **Sources de données** pour créer un formulaire de données. Pour plus d’informations, consultez la page [Fenêtre Sources de données](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.BindingSource>  
 <xref:System.Windows.Forms.DataGridView.DataMember%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType>  
 [Guide pratique pour établir une connexion à des données d’une base de données](http://msdn.microsoft.com/library/6c56e54e-8834-4297-85aa-cc1a443ba556)  
 [Guide pratique pour ajouter et supprimer des colonnes dans le contrôle DataGridView Windows Forms à l'aide du concepteur](../../../../docs/framework/winforms/controls/add-and-remove-columns-in-the-datagrid-using-the-designer.md)  
 [Guide pratique pour modifier l'ordre des colonnes dans le contrôle DataGridView Windows Forms à l'aide du concepteur](../../../../docs/framework/winforms/controls/change-the-order-of-columns-in-the-datagrid-using-the-designer.md)  
 [Guide pratique pour modifier le type d’une colonne DataGridView Windows Forms à l’aide du concepteur](../../../../docs/framework/winforms/controls/change-the-type-of-a-wf-datagridview-column-using-the-designer.md)  
 [Guide pratique pour figer les colonnes du contrôle DataGridView Windows Forms à l'aide du concepteur](../../../../docs/framework/winforms/controls/freeze-columns-in-the-datagrid-using-the-designer.md)  
 [Guide pratique pour masquer les colonnes du contrôle DataGridView Windows Forms à l'aide du concepteur](../../../../docs/framework/winforms/controls/hide-columns-in-the-datagrid-using-the-designer.md)  
 [Guide pratique pour définir une colonne en lecture seule dans le contrôle DataGridView Windows Forms à l'aide du concepteur](../../../../docs/framework/winforms/controls/make-columns-read-only-in-the-datagrid-using-the-designer.md)  
 [Comment : créer un projet d’Application Windows](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa)  
 [Comment : ajouter des contrôles à des Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)  
 [Fenêtre Sources de données](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)  
 [Guide pratique pour afficher des données connexes dans une application Windows Forms](http://msdn.microsoft.com/library/60b1f1ec-6257-42ab-83f0-06d54ed364fd)
