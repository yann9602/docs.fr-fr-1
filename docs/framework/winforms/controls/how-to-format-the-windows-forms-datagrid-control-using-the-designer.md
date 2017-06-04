---
title: "Comment&#160;: mettre en forme le contr&#244;le DataGrid Windows Forms &#224; l&#39;aide du concepteur | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "couleurs, appliquer aux contrôles DataGrid"
  - "colonnes (Windows Forms), contrôles DataGrid"
  - "DataGrid (contrôle Windows Forms), styles par défaut"
  - "DataGrid (contrôle Windows Forms), mettre en forme"
  - "mettre en forme (Windows Forms)"
  - "tables (Windows Forms), mettre en forme dans le contrôle DataGrid"
ms.assetid: 533b9814-6124-49dc-9fda-085f1502609f
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# Comment&#160;: mettre en forme le contr&#244;le DataGrid Windows Forms &#224; l&#39;aide du concepteur
> [!NOTE]
>  Le contrôle <xref:System.Windows.Forms.DataGridView> remplace le contrôle <xref:System.Windows.Forms.DataGrid> et lui ajoute des fonctionnalités ; toutefois, le contrôle <xref:System.Windows.Forms.DataGrid> est conservé pour la compatibilité descendante et l'utilisation future si tel est votre choix.  Pour plus d'informations, consultez [Différences entre les contrôles DataGridView et DataGrid Windows Forms](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 L'application de différentes couleurs aux parties d'un contrôle <xref:System.Windows.Forms.DataGrid> peut faciliter la lecture et l'interprétation des informations.  La couleur peut être appliquée aux lignes et aux colonnes.  Les lignes et les colonnes peuvent également être masquées ou affichées, selon vos besoins.  
  
 La mise en forme du contrôle <xref:System.Windows.Forms.DataGrid> présente trois aspects essentiels :  
  
-   Vous pouvez définir des propriétés pour établir un style par défaut dans lequel les données seront affichées.  
  
-   À partir de cette base, vous pouvez ensuite personnaliser la façon dont certaines tables sont affichées lors de l'exécution.  
  
-   Enfin, vous pouvez modifier les colonnes qui sont affichées dans la grille de données, ainsi que les couleurs et autres éléments de mise en forme affichés.  
  
 La première étape de la mise en forme d'une grille de données consiste à définir les propriétés de <xref:System.Windows.Forms.DataGrid>.  Le choix de la couleur et de la mise en forme constitue une base à partir de laquelle vous pouvez apporter des modifications en fonction des tables et des colonnes de données affichées.  
  
 La procédure suivante requiert un projet d'**application Windows** avec un formulaire qui contient un contrôle <xref:System.Windows.Forms.DataGrid>.  Pour plus d'informations sur la configuration d'un tel projet, consultez [How to: Create a Windows Application Project](http://msdn.microsoft.com/fr-fr/b2f93fed-c635-4705-8d0e-cf079a264efa) et [Comment : ajouter des contrôles à des Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  Dans [!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)], par défaut, le contrôle <xref:System.Windows.Forms.DataGrid> ne se trouve pas dans la **boîte à outils**.  Pour plus d'informations, consultez [How to: Add Items to the Toolbox](http://msdn.microsoft.com/fr-fr/458e119e-17fe-450b-b889-e31c128bd7e0).  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.  Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils**.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### Pour établir un style par défaut pour le contrôle DataGrid  
  
1.  Sélectionnez le contrôle <xref:System.Windows.Forms.DataGrid>.  
  
2.  Dans la fenêtre **Propriétés**, définissez les propriétés suivantes, si nécessaire.  
  
    |Propriété|Description|  
    |---------------|-----------------|  
    |<xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A>|La propriété `BackColor` définit la couleur des lignes paires de la grille.  Lorsque vous affectez une couleur différente à la propriété <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A>, cette couleur est affectée à une ligne sur deux \(lignes 1, 3, 5, etc.\).|  
    |<xref:System.Windows.Forms.DataGrid.BackColor%2A>|Couleur d'arrière\-plan des lignes paires de la grille \(lignes 0, 2, 4, 6, etc.\).|  
    |<xref:System.Windows.Forms.DataGrid.BackgroundColor%2A>|Tandis que les propriétés <xref:System.Windows.Forms.DataGrid.BackColor%2A> et <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> déterminent la couleur des lignes de la grille, la propriété <xref:System.Windows.Forms.DataGrid.BackgroundColor%2A> détermine la couleur de la zone en dehors de la zone de lignes, laquelle est visible uniquement lorsque vous faites défiler la grille vers le bas ou lorsque cette dernière contient seulement quelques lignes.|  
    |<xref:System.Windows.Forms.DataGrid.BorderStyle%2A>|Style de bordure de la grille, parmi les valeurs <xref:System.Windows.Forms.BorderStyle> proposées.|  
    |<xref:System.Windows.Forms.DataGrid.CaptionBackColor%2A>|Couleur d'arrière\-plan du titre de la fenêtre de la grille, qui s'affiche juste au\-dessus de la grille.|  
    |<xref:System.Windows.Forms.DataGrid.CaptionFont%2A>|Police du titre situé au\-dessus de la grille.|  
    |<xref:System.Windows.Forms.DataGrid.CaptionForeColor%2A>|Couleur d'arrière\-plan du titre de la fenêtre de la grille.|  
    |<xref:System.Windows.Forms.Control.Font%2A>|Police utilisée pour afficher le texte de la grille.|  
    |<xref:System.Windows.Forms.DataGrid.ForeColor%2A>|Couleur de la police utilisée par les données des lignes de la grille.|  
    |<xref:System.Windows.Forms.DataGrid.GridLineColor%2A>|Couleur des lignes de la grille de données.|  
    |<xref:System.Windows.Forms.DataGrid.GridLineStyle%2A>|Style des lignes séparant les cellules de la grille, parmi les valeurs <xref:System.Windows.Forms.DataGridLineStyle> proposées.|  
    |<xref:System.Windows.Forms.DataGrid.HeaderBackColor%2A>|Couleur d'arrière\-plan des en\-têtes de ligne et de colonne.|  
    |<xref:System.Windows.Forms.DataGrid.HeaderFont%2A>|Police utilisée pour les en\-têtes de colonne.|  
    |<xref:System.Windows.Forms.DataGrid.HeaderForeColor%2A>|Couleur de premier plan des en\-têtes de colonne de la grille, comprenant le texte de l'en\-tête de colonne et les symboles \+ \(plus\) et \- \(moins\) qui permettent de développer et de réduire les lignes lorsque plusieurs tables connexes sont affichées.|  
    |<xref:System.Windows.Forms.DataGrid.LinkColor%2A>|Couleur du texte de tous les liens de la grille de données, notamment les liens vers les tables enfant, le nom des relations, etc.|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsBackColor%2A>|Dans une table enfant, il s'agit de la couleur d'arrière\-plan des lignes parentes.|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsForeColor%2A>|Dans une table enfant, il s'agit de la couleur de premier plan des lignes parentes.|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsLabelStyle%2A>|Détermine si les noms des tables et des colonnes s'affichent dans la ligne parente, par le biais de l'énumération <xref:System.Windows.Forms.DataGridParentRowsLabelStyle>.|  
    |<xref:System.Windows.Forms.DataGrid.PreferredColumnWidth%2A>|Largeur par défaut \(en pixels\) des colonnes de la grille.  Définissez cette propriété avant de réinitialiser les propriétés <xref:System.Windows.Forms.DataGrid.DataSource%2A> et <xref:System.Windows.Forms.DataGrid.DataMember%2A> \(séparément ou via la méthode <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A>\) ; sinon, la propriété n'aura pas d'effet.<br /><br /> La propriété ne peut pas avoir une valeur inférieure à 0.|  
    |<xref:System.Windows.Forms.DataGrid.PreferredRowHeight%2A>|Hauteur \(en pixels\) des lignes de la grille.  Définissez cette propriété avant de réinitialiser les propriétés <xref:System.Windows.Forms.DataGrid.DataSource%2A> et <xref:System.Windows.Forms.DataGrid.DataMember%2A> \(séparément ou via la méthode <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A>\) ; sinon, la propriété n'aura pas d'effet.<br /><br /> La propriété ne peut pas avoir une valeur inférieure à 0.|  
    |<xref:System.Windows.Forms.DataGrid.RowHeaderWidth%2A>|Largeur des en\-têtes de ligne de la grille.|  
    |<xref:System.Windows.Forms.DataGrid.SelectionBackColor%2A>|Lorsqu'une ligne ou une cellule est sélectionnée, il s'agit de la couleur d'arrière\-plan.|  
    |<xref:System.Windows.Forms.DataGrid.SelectionForeColor%2A>|Lorsqu'une ligne ou une cellule est sélectionnée, il s'agit de la couleur de premier plan.|  
  
    > [!NOTE]
    >  Lorsque vous personnalisez les couleurs des contrôles, une couleur mal choisie \(par exemple, rouge et vert\) peut rendre le contrôle inaccessible.  Utilisez les couleurs de la palette **Couleurs système** afin d'éviter ce problème.  
  
     La procédure suivante requiert un contrôle <xref:System.Windows.Forms.DataGrid> lié à une table de données.  Pour plus d'informations, consultez [Comment : lier le contrôle DataGrid Windows Forms à une source de données](../../../../docs/framework/winforms/controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md).  
  
### Pour définir le style de table et de colonne d'une table de données au moment du design  
  
1.  Sélectionnez le contrôle <xref:System.Windows.Forms.DataGrid> sur votre formulaire.  
  
2.  Dans la fenêtre **Propriétés**, sélectionnez la propriété <xref:System.Windows.Forms.DataGrid.TableStyles%2A>, puis cliquez sur le **bouton de sélection** \(![Capture d'écran VisualStudioEllipsesButton](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")\).  
  
3.  Dans la boîte de dialogue **Éditeur de collections DataGridTableStyle**, cliquez sur **Ajouter** pour ajouter un style de table à la collection.  
  
     Dans l'**éditeur de collections DataGridTableStyle**, vous pouvez ajouter et supprimer des styles de table, définir les propriétés d'affichage et de mise en forme, ainsi que définir le nom de mappage des styles de table.  
  
4.  Affectez à la propriété <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> le nom du mappage de chaque style de table.  
  
     Le nom de mappage est utilisé pour spécifier quel style de table doit être utilisé avec quelle table.  
  
5.  Dans l'**éditeur de collections DataGridTableStyle**, sélectionnez la propriété <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A>, puis cliquez sur le bouton de sélection \(![Capture d'écran VisualStudioEllipsesButton](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")\).  
  
6.  Dans la boîte de dialogue **Éditeur de collections DataGridTableStyle**, ajoutez des styles de colonne au style de table que vous avez créé.  
  
     Dans l'**éditeur de collections DataGridTableStyle**, vous pouvez ajouter et supprimer des styles de colonne, définir les propriétés d'affichage et de mise en forme, ainsi que définir le nom de mappage et les chaînes de mise en forme des colonnes de données.  
  
    > [!NOTE]
    >  Pour plus d'informations sur la mise en forme des chaînes, consultez [Mise en forme des types](../../../../docs/standard/base-types/formatting-types.md).  
  
## Voir aussi  
 <xref:System.Windows.Forms.GridTableStylesCollection>   
 <xref:System.Windows.Forms.GridColumnStylesCollection>   
 <xref:System.Windows.Forms.DataGrid>   
 [Comment : supprimer ou masquer des colonnes dans le contrôle DataGrid Windows Forms](../../../../docs/framework/winforms/controls/how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)   
 [DataGrid, contrôle](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)