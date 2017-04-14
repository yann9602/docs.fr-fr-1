---
title: "Comment&#160;: supprimer ou masquer des colonnes dans le contr&#244;le DataGrid Windows Forms | Microsoft Docs"
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
  - "colonnes (Windows Forms), supprimer dans des grilles de données"
  - "colonnes (Windows Forms), masquer"
  - "grilles de données, supprimer des colonnes"
  - "grilles de données, masquer les colonnes"
  - "DataGrid (contrôle Windows Forms), supprimer des colonnes"
  - "DataGrid (contrôle Windows Forms), masquer les colonnes"
ms.assetid: bcd0dd96-6687-4c48-b0e1-d5287b93ac91
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# Comment&#160;: supprimer ou masquer des colonnes dans le contr&#244;le DataGrid Windows Forms
> [!NOTE]
>  Le contrôle <xref:System.Windows.Forms.DataGridView> remplace le contrôle <xref:System.Windows.Forms.DataGrid> et lui ajoute des fonctionnalités ; toutefois, le contrôle <xref:System.Windows.Forms.DataGrid> est conservé pour la compatibilité descendante et l'utilisation future si tel est votre choix.  Pour plus d'informations, consultez [Différences entre les contrôles DataGridView et DataGrid Windows Forms](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Vous pouvez masquer ou supprimer par programme des colonnes d'un contrôle <xref:System.Windows.Forms.DataGrid> Windows Forms au moyen des propriétés et méthodes des objets <xref:System.Windows.Forms.GridColumnStylesCollection> et <xref:System.Windows.Forms.DataGridColumnStyle> \(lesquels sont membres de la classe <xref:System.Windows.Forms.DataGridTableStyle>\).  
  
 Les colonnes supprimées ou masquées existent toujours dans la source de données à laquelle la grille est liée et sont toujours accessibles par programme.  Simplement, elles ne sont plus visibles dans la grille de données.  
  
> [!NOTE]
>  Si votre application n'accède pas à certaines colonnes de données et que vous ne souhaitez pas les afficher dans la grille de données, il n'est probablement pas nécessaire de les inclure dans la source de données à la première place.  
  
### Pour supprimer par programme une colonne du contrôle DataGrid  
  
1.  Dans la zone de déclarations de votre formulaire, déclarez une nouvelle instance de la classe <xref:System.Windows.Forms.DataGridTableStyle>.  
  
2.  Définissez la propriété <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A?displayProperty=fullName> sur la table à laquelle vous souhaitez appliquer le style dans votre source de données.  L'exemple suivant utilise la propriété <xref:System.Windows.Forms.DataGrid.DataMember%2A?displayProperty=fullName>, qu'il considère comme déjà définie.  
  
3.  Ajoutez le nouvel objet <xref:System.Windows.Forms.DataGridTableStyle> à la collection des styles de table de la grille de données.  
  
4.  Appelez la méthode <xref:System.Windows.Forms.GridColumnStylesCollection.RemoveAt%2A> de la collection <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> du contrôle <xref:System.Windows.Forms.DataGrid> en spécifiant l'index de la colonne à supprimer.  
  
    ```vb  
    ' Declare a new DataGridTableStyle in the  
    ' declarations area of your form.  
    Dim ts As DataGridTableStyle = New DataGridTableStyle()  
  
    Sub DeleteColumn()  
       ' Set the DataGridTableStyle.MappingName property  
       ' to the table in the data source to map to.  
       ts.MappingName = DataGrid1.DataMember  
  
       ' Add it to the datagrid's TableStyles collection  
       DataGrid1.TableStyles.Add(ts)  
  
       ' Delete the first column (index 0)  
       DataGrid1.TableStyles(0).GridColumnStyles.RemoveAt(0)  
    End Sub  
  
    ```  
  
    ```csharp  
    // Declare a new DataGridTableStyle in the  
    // declarations area of your form.  
    DataGridTableStyle ts = new DataGridTableStyle();  
  
    private void deleteColumn()  
    {  
       // Set the DataGridTableStyle.MappingName property  
       // to the table in the data source to map to.  
       ts.MappingName = dataGrid1.DataMember;  
  
       // Add it to the datagrid's TableStyles collection  
       dataGrid1.TableStyles.Add(ts);  
  
       // Delete the first column (index 0)  
       dataGrid1.TableStyles[0].GridColumnStyles.RemoveAt(0);  
    }  
    ```  
  
### Pour masquer par programme une colonne du contrôle DataGrid  
  
1.  Dans la zone de déclarations de votre formulaire, déclarez une nouvelle instance de la classe <xref:System.Windows.Forms.DataGridTableStyle>.  
  
2.  Définissez la propriété <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> de l'objet <xref:System.Windows.Forms.DataGridTableStyle> sur la table à laquelle vous souhaitez appliquer le style dans votre source de données.  Le code suivant utilise la propriété <xref:System.Windows.Forms.DataGrid.DataMember%2A?displayProperty=fullName>, qu'il considère comme déjà définie.  
  
3.  Ajoutez le nouvel objet <xref:System.Windows.Forms.DataGridTableStyle> à la collection des styles de table de la grille de données.  
  
4.  Masquez la colonne en affectant la valeur 0 à sa propriété `Width`  et en précisant l'index de la colonne à masquer.  
  
    ```vb  
    ' Declare a new DataGridTableStyle in the  
    ' declarations area of your form.  
    Dim ts As DataGridTableStyle = New DataGridTableStyle()  
  
    Sub HideColumn()  
       ' Set the DataGridTableStyle.MappingName property  
       ' to the table in the data source to map to.  
       ts.MappingName = DataGrid1.DataMember  
  
       ' Add it to the datagrid's TableStyles collection  
       DataGrid1.TableStyles.Add(ts)  
  
       ' Hide the first column (index 0)  
       DataGrid1.TableStyles(0).GridColumnStyles(0).Width = 0  
    End Sub  
  
    ```  
  
    ```csharp  
    // Declare a new DataGridTableStyle in the  
    // declarations area of your form.  
    DataGridTableStyle ts = new DataGridTableStyle();  
  
    private void hideColumn()  
    {  
       // Set the DataGridTableStyle.MappingName property  
       // to the table in the data source to map to.  
       ts.MappingName = dataGrid1.DataMember;  
  
       // Add it to the datagrid's TableStyles collection  
       dataGrid1.TableStyles.Add(ts);  
  
       // Hide the first column (index 0)  
       dataGrid1.TableStyles[0].GridColumnStyles[0].Width = 0;  
    }  
    ```  
  
## Voir aussi  
 [Comment : modifier des données affichées dans le contrôle DataGrid Windows Forms au moment de l'exécution](../../../../docs/framework/winforms/controls/change-displayed-data-at-run-time-wf-datagrid-control.md)   
 [Comment  : ajouter des tables et des colonnes au contrôle DataGrid Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)