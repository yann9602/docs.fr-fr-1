---
title: "Comment : mettre en forme le contrôle DataGrid Windows Forms"
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
- columns [Windows Forms], DataGrid control
- colors [Windows Forms], applying to DataGrid controls
- DataGrid control [Windows Forms], formatting
- columns [Windows Forms], formatting in DataGrid control
- DataGrid control [Windows Forms], default styles
- tables [Windows Forms], formatting in DataGrid control
- formatting [Windows Forms]
ms.assetid: a50fcc3b-8abf-47ec-9029-7f268af4ddb1
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8518fdcaca7ebed65d0923b9bc1fe1a6797b97c6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-format-the-windows-forms-datagrid-control"></a>Comment : mettre en forme le contrôle DataGrid Windows Forms
> [!NOTE]
>  Le contrôle <xref:System.Windows.Forms.DataGridView> remplace le contrôle <xref:System.Windows.Forms.DataGrid> et lui ajoute des fonctionnalités ; toutefois, le contrôle <xref:System.Windows.Forms.DataGrid> est conservé pour la compatibilité descendante et l'utilisation future si tel est votre choix. Pour plus d’informations, consultez [Différences entre les contrôles DataGridView et DataGrid Windows Forms](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Appliquant différentes couleurs aux différentes parties d’un <xref:System.Windows.Forms.DataGrid> contrôle permettent de rendre les informations qu’elle contient plus facile à lire et interpréter. Couleur peut être appliquée en lignes et colonnes. Lignes et colonnes peuvent également être masquées ou affichées à votre convenance.  
  
 Il existe trois aspects essentiels de la mise en forme la <xref:System.Windows.Forms.DataGrid> contrôle. Vous pouvez définir des propriétés pour établir un style par défaut dans lequel les données sont affichées. À partir de cette base, vous pouvez ensuite personnaliser la façon de que certaines tables sont affichées au moment de l’exécution. Enfin, vous pouvez modifier les colonnes qui sont affichées dans la grille de données, ainsi que les couleurs et autres mises en forme qui est affiché.  
  
 En guise d’étape initiale dans une grille de données de mise en forme, vous pouvez définir les propriétés de la <xref:System.Windows.Forms.DataGrid> lui-même. Ces options de couleur et le format forment une base à partir de laquelle vous pouvez ensuite modifier selon les tables et les colonnes affichées.  
  
### <a name="to-establish-a-default-style-for-the-datagrid-control"></a>Pour établir un style par défaut pour le contrôle DataGrid  
  
1.  Selon le cas, définissez les propriétés suivantes :  
  
    |Propriété|Description|  
    |--------------|-----------------|  
    |<xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A>|Le <xref:System.Windows.Forms.DataGrid.BackColor%2A> propriété définit la couleur des lignes paires de la grille. Lorsque vous définissez le <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> sur une couleur différente, chaque ligne est définie sur cette nouvelle couleur (lignes 1, 3, 5 et ainsi de suite).|  
    |<xref:System.Windows.Forms.DataGrid.BackColor%2A>|La couleur d’arrière-plan des lignes paires de la grille (lignes 0, 2, 4, 6 et ainsi de suite).|  
    |<xref:System.Windows.Forms.DataGrid.BackgroundColor%2A>|Alors que le <xref:System.Windows.Forms.DataGrid.BackColor%2A> et <xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A> propriétés détermine la couleur des lignes dans la grille, le <xref:System.Windows.Forms.DataGrid.BackgroundColor%2A> propriété détermine la couleur de la zone en dehors, laquelle est visible uniquement lorsque vous faites défiler la grille vers le bas, ou si seules quelques lignes sont contenues dans la grille.|  
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
    |<xref:System.Windows.Forms.DataGrid.HeaderForeColor%2A>|La couleur de premier plan des en-têtes de colonnes de la grille, y compris le texte d’en-tête de colonne et les glyphes plus/moins (pour développer les lignes lorsque plusieurs tables connexes sont affichées).|  
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
    >  Gardez à l’esprit, lorsque vous personnalisez les couleurs des contrôles, qu’il est possible rendre le contrôle inaccessible en raison de la couleur est mal choisie (par exemple, rouge et vert). Utiliser les couleurs disponibles sur le **couleurs système** palette pour éviter ce problème.  
  
     Les procédures suivantes supposent que votre formulaire comporte un <xref:System.Windows.Forms.DataGrid> contrôle lié à une table de données. Pour plus d’informations, consultez [de liaison du contrôle DataGrid Windows Forms à une Source de données](../../../../docs/framework/winforms/controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md).  
  
### <a name="to-set-the-table-and-column-style-of-a-data-table-programmatically"></a>Pour définir le style de table et de colonne d’une table de données par programmation  
  
1.  Créer un nouveau style de table et définissez ses propriétés.  
  
2.  Créer un style de colonne et définissez ses propriétés.  
  
3.  Ajoutez le style de colonne à la collection de styles de colonne du style de table.  
  
4.  Ajouter la table à la collection de styles de la grille de données.  
  
5.  Dans l’exemple ci-dessous, créez une instance d’un nouveau <xref:System.Windows.Forms.DataGridTableStyle> et définir son <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> propriété.  
  
6.  Créer une nouvelle instance d’un **GridColumnStyle** et définir son **DataGridTableStyle** (et d’autres propriétés de disposition et d’affichage).  
  
7.  Répétez les étapes 2 à 6 pour chaque style de colonne que vous souhaitez créer.  
  
     L’exemple suivant illustre comment un <xref:System.Windows.Forms.DataGridTextBoxColumn> est créée, car un nom doit être affiché dans la colonne. En outre, vous ajoutez le style de colonne à la <xref:System.Windows.Forms.GridColumnStylesCollection> du style du tableau, et que vous ajoutez le style de table à la <xref:System.Windows.Forms.GridTableStylesCollection> de la grille de données.  
  
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
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.GridTableStylesCollection>  
 <xref:System.Windows.Forms.GridColumnStylesCollection>  
 <xref:System.Windows.Forms.DataGrid>  
 [Guide pratique pour supprimer ou masquer des colonnes dans le contrôle DataGrid Windows Forms](../../../../docs/framework/winforms/controls/how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)  
 [DataGrid, contrôle](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)
