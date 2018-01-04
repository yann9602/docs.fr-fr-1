---
title: "Comment : lier le contrôle DataGrid Windows Forms à une source de données à l'aide du concepteur"
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
helpviewer_keywords:
- datasets [Windows Forms], binding to DataGrid control
- data binding [Windows Forms], DataGrid control
- DataGrid control [Windows Forms], data binding
- Windows Forms controls, data binding
- bound controls [Windows Forms]
ms.assetid: 4e96e3d0-b1cc-4de1-8774-bc9970ec4554
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9e0bde96442e09ee33a63cecd56a4cd6e2cf19a9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-bind-the-windows-forms-datagrid-control-to-a-data-source-using-the-designer"></a>Comment : lier le contrôle DataGrid Windows Forms à une source de données à l'aide du concepteur
> [!NOTE]
>  Le contrôle <xref:System.Windows.Forms.DataGridView> remplace le contrôle <xref:System.Windows.Forms.DataGrid> et lui ajoute des fonctionnalités ; toutefois, le contrôle <xref:System.Windows.Forms.DataGrid> est conservé pour la compatibilité descendante et l'utilisation future si tel est votre choix. Pour plus d’informations, consultez [Différences entre les contrôles DataGridView et DataGrid Windows Forms](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Windows Forms <xref:System.Windows.Forms.DataGrid> contrôle est spécialement conçu pour afficher des informations à partir d’une source de données. Vous liez le contrôle au moment du design en définissant le <xref:System.Windows.Forms.DataGrid.DataSource%2A> et <xref:System.Windows.Forms.DataGrid.DataMember%2A> propriétés, ou au moment de l’exécution en appelant le <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> (méthode). Bien que vous pouvez afficher des données à partir de diverses sources de données, les sources les plus courantes sont les vues de données et des jeux de données.  
  
 Si la source de données est disponible au moment du design, par exemple, si le formulaire contient une instance d’un dataset ou une vue de données, vous pouvez lier la grille à la source de données au moment du design. Vous pouvez ensuite afficher un aperçu l’aspect qu’aura les données dans la grille.  
  
 Vous pouvez également lier la grille par programme, au moment de l’exécution. Cela est utile lorsque vous souhaitez définir une source de données en fonction des informations que vous obtenez au moment de l’exécution. Par exemple, l’application peut permettre à l’utilisateur spécifiez le nom d’une table à afficher. Il est également nécessaire dans les situations où la source de données n’existe pas au moment du design. Cela inclut les sources de données telles que des tableaux, les collections, les datasets non typés et lecteurs de données.  
  
 La procédure suivante requiert un **Application Windows** projet avec un formulaire contenant un <xref:System.Windows.Forms.DataGrid> contrôle. Pour plus d’informations sur la configuration d’un tel projet, consultez [Comment : créer un projet d’Application Windows](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa) et [Comment : ajouter des contrôles aux Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md). Dans [!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)], le <xref:System.Windows.Forms.DataGrid> contrôle n’est pas dans le **boîte à outils** par défaut. Pour plus d’informations sur son ajout, consultez [Comment : ajouter des éléments à la boîte à outils](http://msdn.microsoft.com/en-us/458e119e-17fe-450b-b889-e31c128bd7e0). Par ailleurs, dans [!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)], vous pouvez utiliser la **des Sources de données** fenêtre pour la liaison de données au moment du design. Pour plus d’informations, consultez [lier des contrôles aux données dans Visual Studio](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio).  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-data-bind-the-datagrid-control-to-a-single-table-in-the-designer"></a>À lier aux données du contrôle DataGrid à une table dans le Concepteur  
  
1.  Valeur du contrôle <xref:System.Windows.Forms.DataGrid.DataSource%2A> propriété à l’objet qui contient les éléments de données que vous voulez lier.  
  
2.  Si la source de données est un jeu de données, définissez la <xref:System.Windows.Forms.DataGrid.DataMember%2A> propriété le nom de la table à lier.  
  
3.  Si la source de données est un jeu de données ou une vue de données basée sur une table de dataset, ajoutez le code au formulaire pour remplir le dataset.  
  
     Le code exact que vous utilisez dépend où le jeu de données obtient des données. Si le jeu de données est rempli directement à partir d’une base de données, vous appelez généralement la `Fill` méthode d’un adaptateur de données, comme dans l’exemple de code suivant, qui remplit un dataset nommé `DsCategories1`:  
  
    ```vb  
    sqlDataAdapter1.Fill(DsCategories1)  
    ```  
  
    ```csharp  
    sqlDataAdapter1.Fill(DsCategories1);  
    ```  
  
    ```cpp  
    sqlDataAdapter1->Fill(dsCategories1);  
    ```  
  
4.  (Facultatif) Ajoutez les styles de table approprié et les styles de colonne à la grille.  
  
     S’il n’y a aucun style de tableau, vous verrez la table, mais avec la mise en forme minimale et toutes les colonnes visibles.  
  
### <a name="to-data-bind-the-datagrid-control-to-multiple-tables-in-a-dataset-in-the-designer"></a>À lier aux données du contrôle DataGrid à plusieurs tables dans un jeu de données dans le Concepteur  
  
1.  Valeur du contrôle <xref:System.Windows.Forms.DataGrid.DataSource%2A> propriété à l’objet qui contient les éléments de données que vous voulez lier.  
  
2.  Si le jeu de données contient des tables associées (autrement dit, si elle contient un objet de relation), affectez le <xref:System.Windows.Forms.DataGrid.DataMember%2A> propriété le nom de la table parente.  
  
3.  Écrire du code pour remplir le dataset.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble du contrôle DataGrid](../../../../docs/framework/winforms/controls/datagrid-control-overview-windows-forms.md)  
 [Guide pratique pour ajouter des tables et des colonnes au contrôle DataGrid Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)  
 [DataGrid, contrôle](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)  
 [Liaison de données Windows Forms](../../../../docs/framework/winforms/windows-forms-data-binding.md)  
 [Accès aux données dans Visual Studio](/visualstudio/data-tools/accessing-data-in-visual-studio)
