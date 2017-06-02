---
title: "Comment&#160;: cr&#233;er des listes ma&#238;tres/d&#233;tails avec le contr&#244;le DataGrid Windows Forms | Microsoft Docs"
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
  - "DataGrid (contrôle Windows Forms), listes maître/détails"
  - "listes maître/détails"
  - "tables connexes, afficher dans le contrôle DataGrid"
ms.assetid: 20388c6a-94f9-4d96-be18-8c200491247f
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# Comment&#160;: cr&#233;er des listes ma&#238;tres/d&#233;tails avec le contr&#244;le DataGrid Windows Forms
> [!NOTE]
>  Le contrôle <xref:System.Windows.Forms.DataGridView> remplace le contrôle <xref:System.Windows.Forms.DataGrid> et lui ajoute des fonctionnalités ; toutefois, le contrôle <xref:System.Windows.Forms.DataGrid> est conservé pour la compatibilité descendante et l'utilisation future si tel est votre choix.  Pour plus d'informations, consultez [Différences entre les contrôles DataGridView et DataGrid Windows Forms](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Si votre <xref:System.Data.DataSet> contient une série de tables connexes, vous pouvez utiliser deux contrôles <xref:System.Windows.Forms.DataGrid> pour afficher les données dans un format maître\/détail.  Le premier contrôle <xref:System.Windows.Forms.DataGrid> est désigné comme grille principale et le second comme grille détaillée.  Lorsque vous sélectionnez une entrée dans la liste maître, toutes les entrées enfants connexes s'affichent dans la liste détails.  Par exemple, si votre <xref:System.Data.DataSet> contient une table Customers et une table connexe Orders, vous spécifiez la table Customers comme grille principale et la table Orders comme grille détaillée.  Lorsqu'un client est sélectionné dans la grille principale, toutes les commandes qui lui sont associées dans la table Orders s'affichent dans la grille détaillée.  
  
### Pour définir une relation maître\/détail par programme  
  
1.  Créez deux contrôles <xref:System.Windows.Forms.DataGrid> et définissez leurs propriétés.  
  
2.  Ajoutez des tables au groupe de données.  
  
3.  Déclarez une variable de type <xref:System.Data.DataRelation> pour représenter la relation à créer.  
  
4.  Instanciez la relation en spécifiant son nom et en indiquant la table, la colonne et l'élément devant lier les deux tables.  
  
5.  Ajoutez la relation à la collection <xref:System.Data.DataSet.Relations%2A> de l'objet <xref:System.Data.DataSet>.  
  
6.  Utilisez la méthode <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> de <xref:System.Windows.Forms.DataGrid> pour lier chacune des grilles à <xref:System.Data.DataSet>.  
  
     L'exemple suivant montre comment définir une relation maître\/détail entre les tables Customers et Orders dans un <xref:System.Data.DataSet>\(`ds`\) préalablement généré.  
  
    ```vb  
    Dim myDataRelation As DataRelation  
    myDataRelation = New DataRelation _  
       ("CustOrd", ds.Tables("Customers").Columns("CustomerID"), _  
       ds.Tables("Orders").Columns("CustomerID"))  
    ' Add the relation to the DataSet.  
    ds.Relations.Add(myDataRelation)  
    GridOrders.SetDataBinding(ds, "Customers")  
    GridDetails.SetDataBinding(ds, "Customers.CustOrd")  
  
    ```  
  
    ```csharp  
    DataRelation myDataRelation;  
    myDataRelation = new DataRelation("CustOrd", ds.Tables["Customers"].Columns["CustomerID"], ds.Tables["Orders"].Columns["CustomerID"]);  
    // Add the relation to the DataSet.  
    ds.Relations.Add(myDataRelation);  
    GridOrders.SetDataBinding(ds,"Customers");  
    GridDetails.SetDataBinding(ds,"Customers.CustOrd");  
  
    ```  
  
    ```cpp  
    DataRelation^ myDataRelation;  
    myDataRelation = gcnew DataRelation("CustOrd",  
       ds->Tables["Customers"]->Columns["CustomerID"],  
       ds->Tables["Orders"]->Columns["CustomerID"]);  
    // Add the relation to the DataSet.  
    ds->Relations->Add(myDataRelation);  
    GridOrders->SetDataBinding(ds, "Customers");  
    GridDetails->SetDataBinding(ds, "Customers.CustOrd");  
    ```  
  
## Voir aussi  
 [DataGrid, contrôle](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)   
 [Vue d'ensemble du contrôle DataGrid](../../../../docs/framework/winforms/controls/datagrid-control-overview-windows-forms.md)   
 [Comment : lier le contrôle DataGrid Windows Forms à une source de données](../../../../docs/framework/winforms/controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)