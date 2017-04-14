---
title: "Comment&#160; : ajouter des tables et des colonnes au contr&#244;le DataGrid Windows Forms | Microsoft Docs"
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
  - "colonnes (Windows Forms), ajouter au contrôle DataGrid"
  - "DataGrid (contrôle Windows Forms), ajouter des tables et des colonnes"
  - "tables (Windows Forms), ajouter au contrôle DataGrid"
ms.assetid: 2fe661b9-aa06-49b9-a314-a0d3cbfdcb4d
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# Comment&#160; : ajouter des tables et des colonnes au contr&#244;le DataGrid Windows Forms
> [!NOTE]
>  Le contrôle <xref:System.Windows.Forms.DataGridView> remplace le contrôle <xref:System.Windows.Forms.DataGrid> et lui ajoute des fonctionnalités ; toutefois, le contrôle <xref:System.Windows.Forms.DataGrid> est conservé pour la compatibilité descendante et l'utilisation future si tel est votre choix.  Pour plus d'informations, consultez [Différences entre les contrôles DataGridView et DataGrid Windows Forms](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Vous pouvez afficher des données dans le contrôle <xref:System.Windows.Forms.DataGrid> Windows Forms, dans des tables et colonnes, en créant des objets **DataGridTableStyle** et en les ajoutant à l'objet **GridTableStylesCollection**, accessible par le biais de la propriété **TableStyles** du contrôle <xref:System.Windows.Forms.DataGrid>.  Chaque style de table affiche le contenu de toute table de données spécifiée dans la propriété **MappingName** de l'objet **DataGridTableStyle**.  Par défaut, un style de table sans style de colonne spécifié affiche toutes les colonnes de la table de données.  Vous pouvez restreindre les colonnes de la table affichées en ajoutant des objets **DataGridColumnStyle** à l'objet **GridColumnStylesCollection** accessible par la propriété **GridColumnStyles** de chaque objet **DataGridTableStyle**.  
  
### Pour ajouter une table et une colonne à un contrôle DataGrid par programme  
  
1.  Pour afficher des données dans la table, vous devez d'abord lier le contrôle <xref:System.Windows.Forms.DataGrid> à un groupe de données.  Pour plus d'informations, consultez [Comment : lier le contrôle DataGrid Windows Forms à une source de données](../../../../docs/framework/winforms/controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md).  
  
    > [!CAUTION]
    >  Lorsque vous spécifiez par programme des styles de colonne, vous devez créer systématiquement des objets **DataGridColumnStyle** et les ajouter à l'objet **GridColumnStylesCollection** avant d'ajouter les objets **DataGridTableStyle** à l'objet **GridTableStylesCollection**.  Lorsque vous ajoutez un objet **DataGridTableStyle** vide à la collection, les objets **DataGridColumnStyle** sont automatiquement générés.  Une exception est donc levée si vous tentez d'ajouter de nouveaux objets **DataGridColumnStyle** présentant des valeurs **MappingName** dupliquées avec celles de l'objet **GridColumnStylesCollection**.  
  
2.  Déclarez un nouveau style de table et définissez son nom de mappage.  
  
    ```vb  
    Dim ts1 As New DataGridTableStyle()  
    ts1.MappingName = "Customers"  
  
    ```  
  
    ```csharp  
    DataGridTableStyle ts1 = new DataGridTableStyle();  
    ts1.MappingName = "Customers";  
  
    ```  
  
    ```cpp  
    DataGridTableStyle* ts1 = new DataGridTableStyle();  
    ts1->MappingName = S"Customers";  
    ```  
  
3.  Déclarez un nouveau style de colonne et définissez son nom de mappage ainsi que ses autres propriétés.  
  
    ```vb  
    Dim myDataCol As New DataGridBoolColumn()  
    myDataCol.HeaderText = "My New Column"  
    myDataCol.MappingName = "Current"  
  
    ```  
  
    ```csharp  
    DataGridBoolColumn myDataCol = new DataGridBoolColumn();  
    myDataCol.HeaderText = "My New Column";  
    myDataCol.MappingName = "Current";  
  
    ```  
  
    ```cpp  
    DataGridBoolColumn^ myDataCol = gcnew DataGridBoolColumn();  
    myDataCol->HeaderText = "My New Column";  
    myDataCol->MappingName = "Current";  
    ```  
  
4.  Appelez la méthode **Add** de l'objet **GridColumnStylesCollection** pour ajouter la colonne au style de table.  
  
    ```vb  
    ts1.GridColumnStyles.Add(myDataCol)  
  
    ```  
  
    ```csharp  
    ts1.GridColumnStyles.Add(myDataCol);  
  
    ```  
  
    ```cpp  
    ts1->GridColumnStyles->Add(myDataCol);  
    ```  
  
5.  Appelez la méthode **Add** de l'objet **GridTableStylesCollection** pour ajouter la table à la grille de données.  
  
    ```vb  
    DataGrid1.TableStyles.Add(ts1)  
  
    ```  
  
    ```csharp  
    dataGrid1.TableStyles.Add(ts1);  
  
    ```  
  
    ```cpp  
    dataGrid1->TableStyles->Add(ts1);  
    ```  
  
## Voir aussi  
 [DataGrid, contrôle](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)   
 [Comment : supprimer ou masquer des colonnes dans le contrôle DataGrid Windows Forms](../../../../docs/framework/winforms/controls/how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)