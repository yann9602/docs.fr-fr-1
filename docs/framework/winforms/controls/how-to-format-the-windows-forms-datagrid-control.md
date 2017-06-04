---
title: "Comment&#160;: mettre en forme le contr&#244;le DataGrid Windows Forms | Microsoft Docs"
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
  - "colonnes (Windows Forms), DataGrid (contrôle)"
  - "colonnes (Windows Forms), mettre en forme dans le contrôle DataGrid"
  - "DataGrid (contrôle Windows Forms), styles par défaut"
  - "DataGrid (contrôle Windows Forms), mettre en forme"
  - "mettre en forme (Windows Forms)"
  - "tables (Windows Forms), mettre en forme dans le contrôle DataGrid"
ms.assetid: a50fcc3b-8abf-47ec-9029-7f268af4ddb1
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# Comment&#160;: mettre en forme le contr&#244;le DataGrid Windows Forms
> [!NOTE]
>  Le contrôle <xref:System.Windows.Forms.DataGridView> remplace le contrôle <xref:System.Windows.Forms.DataGrid> et lui ajoute des fonctionnalités ; toutefois, le contrôle <xref:System.Windows.Forms.DataGrid> est conservé pour la compatibilité descendante et l'utilisation future si tel est votre choix.  Pour plus d'informations, consultez [Différences entre les contrôles DataGridView et DataGrid Windows Forms](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 L'application de différentes couleurs aux parties d'un contrôle <xref:System.Windows.Forms.DataGrid> peut faciliter la lecture et l'interprétation des informations.  La couleur peut être appliquée aux lignes et aux colonnes.  Les lignes et les colonnes peuvent également être masquées ou affichées, selon vos besoins.  
  
 La mise en forme du contrôle <xref:System.Windows.Forms.DataGrid> présente trois aspects essentiels.  Vous pouvez définir des propriétés pour établir un style par défaut dans lequel les données seront affichées.  À partir de cette base, vous pouvez ensuite personnaliser la façon dont certaines tables sont affichées lors de l'exécution.  Enfin, vous pouvez modifier les colonnes qui sont affichées dans la grille de données, ainsi que les couleurs et autres éléments de mise en forme affichés.  
  
 La première étape de la mise en forme d'une grille de données consiste à définir les propriétés de <xref:System.Windows.Forms.DataGrid>.  Le choix de la couleur et de la mise en forme constitue une base à partir de laquelle vous pouvez apporter des modifications en fonction des tables et des colonnes de données affichées.  
  
### Pour établir un style par défaut pour le contrôle DataGrid  
  
1.  Définissez les propriétés suivantes selon vos besoins :  
  
    |Propriété|Description|  
    |---------------|-----------------|  
    |<xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A>|La propriété <xref:System.Windows.Forms.DataGrid.BackColor%2A> définit la couleur des lignes paires de la grille.  Lorsque vous affectez une couleur différente à la propriété <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A>, cette couleur est affectée à une ligne sur deux \(lignes 1, 3, 5, etc.\).|  
    |<xref:System.Windows.Forms.DataGrid.BackColor%2A>|Couleur d'arrière\-plan des lignes paires de la grille \(lignes 0, 2, 4, 6, etc.\).|  
    |<xref:System.Windows.Forms.DataGrid.BackgroundColor%2A>|Tandis que les propriétés <xref:System.Windows.Forms.DataGrid.BackColor%2A> et <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> déterminent la couleur des lignes de la grille, la propriété <xref:System.Windows.Forms.DataGrid.BackgroundColor%2A> détermine la couleur de la zone en dehors des lignes, laquelle est visible uniquement lorsque vous faites défiler la grille vers le bas ou lorsque celle\-ci contient seulement quelques lignes.|  
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
    |<xref:System.Windows.Forms.DataGrid.HeaderForeColor%2A>|Couleur de premier plan des en\-têtes de colonne de la grille, comprenant le texte de l'en\-tête et les symboles plus\/moins \(qui permettent de développer les lignes lorsque plusieurs tables liées sont affichées\).|  
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
    >  Lorsque vous personnalisez les couleurs des contrôles, n'oubliez pas que vous risquez de rendre le contrôle inaccessible si la couleur est mal choisie \(par exemple, rouge et vert\).  Utilisez les couleurs de la palette **Couleurs système** afin d'éviter ce problème.  
  
     Les procédures suivantes supposent que votre formulaire comporte un contrôle <xref:System.Windows.Forms.DataGrid> lié à une table de données.  Pour plus d'informations, consultez [Liaison du contrôle DataGrid Windows Forms à une source de données](../../../../docs/framework/winforms/controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md).  
  
### Pour définir le style de table et de colonne d'une table de données par programme  
  
1.  Créez un nouveau style de table et définissez ses propriétés.  
  
2.  Créez un style de colonne et définissez ses propriétés.  
  
3.  Ajoutez le style de colonne à la collection des styles de colonne du style de table.  
  
4.  Ajoutez le style de table à la collection des styles de table de la grille de données.  
  
5.  Dans l'exemple ci\-dessous, créez une instance d'un nouveau <xref:System.Windows.Forms.DataGridTableStyle> et définissez sa propriété <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A>.  
  
6.  Créez une nouvelle instance d'un style **GridColumnStyle** et définissez sa propriété **MappingName** \(ainsi que d'autres propriétés de mise en forme et d'affichage\).  
  
7.  Répétez les étapes 2 à 6 pour chacun des styles de colonne que vous souhaitez créer.  
  
     L'exemple suivant illustre la création d'un objet <xref:System.Windows.Forms.DataGridTextBoxColumn>, car un nom doit être affiché dans la colonne.  De plus, vous ajoutez le style de colonne à la collection <xref:System.Windows.Forms.GridColumnStylesCollection> du style de table et vous ajoutez le style de table à la collection <xref:System.Windows.Forms.GridTableStylesCollection> de la grille de données.  
  
    ```vb  
    Private Sub CreateAuthorFirstNameColumn()  
       ' Add a GridTableStyle and set the MappingName   
       ' to the name of the DataTable.  
       Dim TSAuthors As New DataGridTableStyle()  
       TSAuthors.MappingName = "Authors"  
  
       ' Add a GridColumnStyle and set the MappingName   
       ' to the name of a DataColumn in the DataTable.   
       ' Set the HeaderText and Width properties.   
       Dim TCFirstName As New DataGridTextBoxColumn()  
       TCFirstName.MappingName = "AV_FName"  
       TCFirstName.HeaderText = "First Name"  
       TCFirstName.Width = 75  
       TSAuthors.GridColumnStyles.Add(TCFirstName)  
  
       ' Add the DataGridTableStyle instance to   
       ' the GridTableStylesCollection.   
       myDataGrid.TableStyles.Add(TSAuthors)  
    End Sub  
  
    ```  
  
    ```csharp  
    private void addCustomDataTableStyle()  
    {  
       // Add a GridTableStyle and set the MappingName   
       // to the name of the DataTable.  
       DataGridTableStyle TSAuthors = new DataGridTableStyle();  
       TSAuthors.MappingName = "Authors";  
  
       // Add a GridColumnStyle and set the MappingName   
       // to the name of a DataColumn in the DataTable.   
       // Set the HeaderText and Width properties.   
       DataGridColumnStyle TCFirstName = new DataGridTextBoxColumn();  
       TCFirstName.MappingName = " AV_FName";  
       TCFirstName.HeaderText = "First Name";  
       TCFirstName.Width = 75;  
       TSAuthors.GridColumnStyles.Add(TCFirstName);  
  
       // Add the DataGridTableStyle instance to   
       // the GridTableStylesCollection.   
       dataGrid1.TableStyles.Add(TSAuthors);  
    }  
  
    ```  
  
    ```cpp  
    private:  
       void addCustomDataTableStyle()  
       {  
          // Add a GridTableStyle and set the MappingName   
          // to the name of the DataTable.  
          DataGridTableStyle^ TSAuthors = new DataGridTableStyle();  
          TSAuthors->MappingName = "Authors";  
  
          // Add a GridColumnStyle and set the MappingName   
          // to the name of a DataColumn in the DataTable.   
          // Set the HeaderText and Width properties.   
          DataGridColumnStyle^ TCFirstName = gcnew DataGridTextBoxColumn();  
          TCFirstName->MappingName = "AV_FName";  
          TCFirstName->HeaderText = "First Name";  
          TCFirstName->Width = 75;  
          TSAuthors->GridColumnStyles->Add(TCFirstName);  
  
          // Add the DataGridTableStyle instance to   
          // the GridTableStylesCollection.   
          dataGrid1->TableStyles->Add(TSAuthors);  
       }  
    ```  
  
## Voir aussi  
 <xref:System.Windows.Forms.GridTableStylesCollection>   
 <xref:System.Windows.Forms.GridColumnStylesCollection>   
 <xref:System.Windows.Forms.DataGrid>   
 [Comment : supprimer ou masquer des colonnes dans le contrôle DataGrid Windows Forms](../../../../docs/framework/winforms/controls/how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)   
 [DataGrid, contrôle](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)