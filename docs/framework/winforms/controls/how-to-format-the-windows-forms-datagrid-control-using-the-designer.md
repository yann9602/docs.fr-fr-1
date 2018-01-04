---
title: "Comment : mettre en forme le contrôle DataGrid Windows Forms à l'aide du concepteur"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- columns [Windows Forms], DataGrid controls
- colors [Windows Forms], applying to DataGrid controls
- DataGrid control [Windows Forms], formatting
- DataGrid control [Windows Forms], default styles
- tables [Windows Forms], formatting in DataGrid control
- formatting [Windows Forms]
ms.assetid: 533b9814-6124-49dc-9fda-085f1502609f
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9c9c82044e7136f05d64a20fb24ee0b209742caf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-format-the-windows-forms-datagrid-control-using-the-designer"></a>Comment : mettre en forme le contrôle DataGrid Windows Forms à l'aide du concepteur
> [!NOTE]
>  Le contrôle <xref:System.Windows.Forms.DataGridView> remplace le contrôle <xref:System.Windows.Forms.DataGrid> et lui ajoute des fonctionnalités ; toutefois, le contrôle <xref:System.Windows.Forms.DataGrid> est conservé pour la compatibilité descendante et l'utilisation future si tel est votre choix. Pour plus d’informations, consultez [Différences entre les contrôles DataGridView et DataGrid Windows Forms](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Appliquant différentes couleurs aux différentes parties d’un <xref:System.Windows.Forms.DataGrid> contrôle permettent de rendre les informations qu’elle contient plus facile à lire et interpréter. Couleur peut être appliquée en lignes et colonnes. Lignes et colonnes peuvent également être masquées ou affichées à votre convenance.  
  
 Il existe trois aspects essentiels de la mise en forme la <xref:System.Windows.Forms.DataGrid> contrôle :  
  
-   Vous pouvez définir des propriétés pour établir un style par défaut dans lequel les données sont affichées.  
  
-   À partir de cette base, vous pouvez ensuite personnaliser la façon de que certaines tables sont affichées au moment de l’exécution.  
  
-   Enfin, vous pouvez modifier les colonnes qui sont affichées dans la grille de données, ainsi que les couleurs et autres mises en forme qui est affiché.  
  
 En guise d’étape initiale dans une grille de données de mise en forme, vous pouvez définir les propriétés de la <xref:System.Windows.Forms.DataGrid> lui-même. Ces options de couleur et le format forment une base à partir de laquelle vous pouvez ensuite modifier selon les tables et les colonnes affichées.  
  
 La procédure suivante requiert un **Application Windows** projet avec un formulaire contenant un <xref:System.Windows.Forms.DataGrid> contrôle. Pour plus d’informations sur la configuration d’un tel projet, consultez [Comment : créer un projet d’Application Windows](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa) et [Comment : ajouter des contrôles aux Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md). Dans [!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)], le <xref:System.Windows.Forms.DataGrid> contrôle n’est pas dans le **boîte à outils** par défaut. Pour plus d’informations, consultez [Comment : ajouter des éléments à la boîte à outils](http://msdn.microsoft.com/en-us/458e119e-17fe-450b-b889-e31c128bd7e0).  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-establish-a-default-style-for-the-datagrid-control"></a>Pour établir un style par défaut pour le contrôle DataGrid  
  
1.  Sélectionnez le contrôle <xref:System.Windows.Forms.DataGrid>.  
  
2.  Dans le **propriétés** fenêtre, définissez les propriétés suivantes, selon le cas.  
  
    |Propriété|Description|  
    |--------------|-----------------|  
    |<xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A>|Le `BackColor` propriété définit la couleur des lignes paires de la grille. Lorsque vous définissez le <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> sur une couleur différente, chaque ligne est définie sur cette nouvelle couleur (lignes 1, 3, 5 et ainsi de suite).|  
    |<xref:System.Windows.Forms.DataGrid.BackColor%2A>|La couleur d’arrière-plan des lignes paires de la grille (lignes 0, 2, 4, 6 et ainsi de suite).|  
    |<xref:System.Windows.Forms.DataGrid.BackgroundColor%2A>|Alors que le <xref:System.Windows.Forms.DataGrid.BackColor%2A> et <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> propriétés détermine la couleur des lignes dans la grille, le <xref:System.Windows.Forms.DataGrid.BackgroundColor%2A> propriété détermine la couleur de la zone en dehors de la zone de ligne, qui est visible uniquement lorsque vous faites défiler la grille vers le bas, ou si seules quelques lignes sont contenus dans la grille.|  
    |<xref:System.Windows.Forms.DataGrid.BorderStyle%2A>|Style de bordure de la grille, parmi les <xref:System.Windows.Forms.BorderStyle> valeurs d’énumération.|  
    |<xref:System.Windows.Forms.DataGrid.CaptionBackColor%2A>|La couleur d’arrière-plan de la légende de la fenêtre de la grille qui s’affiche juste au-dessus de la grille.|  
    |<xref:System.Windows.Forms.DataGrid.CaptionFont%2A>|La police de la légende en haut de la grille.|  
    |<xref:System.Windows.Forms.DataGrid.CaptionForeColor%2A>|La couleur d’arrière-plan de la légende de la fenêtre de la grille.|  
    |<xref:System.Windows.Forms.Control.Font%2A>|La police utilisée pour afficher le texte dans la grille.|  
    |<xref:System.Windows.Forms.DataGrid.ForeColor%2A>|La couleur de la police utilisée par les données dans les lignes de la grille de données.|  
    |<xref:System.Windows.Forms.DataGrid.GridLineColor%2A>|La couleur du quadrillage de la grille de données.|  
    |<xref:System.Windows.Forms.DataGrid.GridLineStyle%2A>|Le style des lignes séparant les cellules de la grille, parmi les <xref:System.Windows.Forms.DataGridLineStyle> valeurs d’énumération.|  
    |<xref:System.Windows.Forms.DataGrid.HeaderBackColor%2A>|La couleur d’arrière-plan des en-têtes de ligne et colonne.|  
    |<xref:System.Windows.Forms.DataGrid.HeaderFont%2A>|La police utilisée pour les en-têtes de colonne.|  
    |<xref:System.Windows.Forms.DataGrid.HeaderForeColor%2A>|La couleur de premier plan des en-têtes de colonnes de la grille, y compris le texte d’en-tête de colonne et le signe plus (+) et le signe moins (-) glyphes développer et réduire les lignes lorsque plusieurs tables connexes sont affichés.|  
    |<xref:System.Windows.Forms.DataGrid.LinkColor%2A>|La couleur du texte de tous les liens dans la grille de données, y compris des liens vers les tables enfants, le nom de la relation et ainsi de suite.|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsBackColor%2A>|Dans une table enfant, il s’agit de la couleur d’arrière-plan des lignes parentes.|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsForeColor%2A>|Dans une table enfant, il s’agit de la couleur de premier plan des lignes parentes.|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsLabelStyle%2A>|Détermine si les noms de table et de colonne sont affichées dans la ligne parente, à l’aide de la <xref:System.Windows.Forms.DataGridParentRowsLabelStyle> énumération.|  
    |<xref:System.Windows.Forms.DataGrid.PreferredColumnWidth%2A>|Largeur par défaut (en pixels) des colonnes de la grille. Définissez cette propriété avant de réinitialiser le <xref:System.Windows.Forms.DataGrid.DataSource%2A> et <xref:System.Windows.Forms.DataGrid.DataMember%2A> propriétés (soit séparément, ou via le <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> méthode), ou la propriété n’a aucun effet.<br /><br /> La propriété ne peut pas être définie sur une valeur inférieure à 0.|  
    |<xref:System.Windows.Forms.DataGrid.PreferredRowHeight%2A>|La hauteur de ligne (en pixels) des lignes dans la grille. Définissez cette propriété avant de réinitialiser le <xref:System.Windows.Forms.DataGrid.DataSource%2A> et <xref:System.Windows.Forms.DataGrid.DataMember%2A> propriétés (soit séparément, ou via le <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> méthode), ou la propriété n’a aucun effet.<br /><br /> La propriété ne peut pas être définie sur une valeur inférieure à 0.|  
    |<xref:System.Windows.Forms.DataGrid.RowHeaderWidth%2A>|La largeur des en-têtes de lignes de la grille.|  
    |<xref:System.Windows.Forms.DataGrid.SelectionBackColor%2A>|Lorsqu’une ligne ou une cellule est sélectionnée, il s’agit de la couleur d’arrière-plan.|  
    |<xref:System.Windows.Forms.DataGrid.SelectionForeColor%2A>|Lorsqu’une ligne ou une cellule est sélectionnée, il s’agit de la couleur de premier plan.|  
  
    > [!NOTE]
    >  Lorsque vous personnalisez les couleurs des contrôles, il est possible rendre le contrôle inaccessible en raison de la couleur est mal choisie (par exemple, rouge et vert). Utiliser les couleurs disponibles sur le **couleurs système** palette pour éviter ce problème.  
  
     La procédure suivante requiert un <xref:System.Windows.Forms.DataGrid> contrôle lié à une table de données. Pour plus d’informations, consultez [Comment : lier le contrôle DataGrid Windows Forms à une Source de données](../../../../docs/framework/winforms/controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md).  
  
### <a name="to-set-the-table-and-column-style-of-a-data-table-at-design-time"></a>Pour définir le style de table et de colonne d’une table de données au moment du design  
  
1.  Sélectionnez le <xref:System.Windows.Forms.DataGrid> contrôle de votre formulaire.  
  
2.  Dans le **propriétés** fenêtre, sélectionnez le <xref:System.Windows.Forms.DataGrid.TableStyles%2A> propriété et cliquez sur le **points de suspension** (![capture d’écran de VisualStudioEllipsesButton] (../../../../docs/framework/winforms/media/vbellipsesbutton.png " vbEllipsesButton")) bouton.  
  
3.  Dans le **éditeur de collections DataGridTableStyle** boîte de dialogue, cliquez sur **ajouter** pour ajouter un style de table à la collection.  
  
     Avec la **éditeur de collections DataGridTableStyle**, vous pouvez ajouter et supprimer les styles de tableau, définir l’affichage des propriétés de disposition et de jeu le mappage de nom pour les styles de table.  
  
4.  Définir le <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> propriété le nom de mappage pour chaque style de table.  
  
     Le nom de mappage est utilisé pour spécifier le style de table doit être utilisé avec la table.  
  
5.  Dans le **éditeur de collections DataGridTableStyle**, sélectionnez le <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> propriété et cliquez sur le bouton de sélection (![capture d’écran de VisualStudioEllipsesButton](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton ")).  
  
6.  Dans le **éditeur de collections DataGridColumnStyle** boîte de dialogue zone, ajouter des styles de colonne pour le style de table que vous avez créé.  
  
     Avec la **éditeur de collections DataGridColumnStyle**, vous pouvez ajouter et supprimer des styles de colonne, définir les propriétés d’affichage et de disposition et définir le nom de mappage et les chaînes de mise en forme des colonnes de données.  
  
    > [!NOTE]
    >  Pour plus d’informations sur la mise en forme des chaînes, consultez [mise en forme des Types](../../../../docs/standard/base-types/formatting-types.md).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.GridTableStylesCollection>  
 <xref:System.Windows.Forms.GridColumnStylesCollection>  
 <xref:System.Windows.Forms.DataGrid>  
 [Guide pratique pour supprimer ou masquer des colonnes dans le contrôle DataGrid Windows Forms](../../../../docs/framework/winforms/controls/how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)  
 [DataGrid, contrôle](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)
