---
title: "Comment&#160;: lier le contr&#244;le DataGrid Windows Forms &#224; une source de donn&#233;es | Microsoft Docs"
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
  - "contrôles dépendants"
  - "contrôles dépendants, DataGrid (contrôle)"
  - "liaison de données, DataGrid (contrôle)"
  - "contrôles liés aux données, DataGrid"
  - "DataGrid (contrôle Windows Forms), liaison de données"
  - "groupes de données (Windows Forms), lier au contrôle DataGrid"
  - "contrôles Windows Forms, liaison de données"
ms.assetid: 128cdb07-dfd3-4d60-9d6a-902847667c36
caps.latest.revision: 17
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 17
---
# Comment&#160;: lier le contr&#244;le DataGrid Windows Forms &#224; une source de donn&#233;es
> [!NOTE]
>  Le contrôle <xref:System.Windows.Forms.DataGridView> remplace le contrôle <xref:System.Windows.Forms.DataGrid> et lui ajoute des fonctionnalités ; toutefois, le contrôle <xref:System.Windows.Forms.DataGrid> est conservé pour la compatibilité descendante et l'utilisation future si tel est votre choix.  Pour plus d'informations, consultez [Différences entre les contrôles DataGridView et DataGrid Windows Forms](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Le contrôle <xref:System.Windows.Forms.DataGrid> Windows Forms est spécialement conçu pour afficher des informations d'une source de données.  Vous liez le contrôle au moment de l'exécution en appelant la méthode <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A>.  Bien que vous puissiez afficher des données provenant d'un large éventail de sources de données, les sources les plus courantes sont les groupes de données et les vues de données.  
  
### Pour lier les données d'un contrôle DataGrid par programme  
  
1.  Écrivez le code servant à remplir le groupe de données.  
  
     Si la source est un groupe de données ou une vue de données basée sur une table de groupe de données, ajoutez au formulaire du code destiné à remplir le groupe de données.  
  
     Le code exact utilisé dépend de la provenance des données du groupe.  Si le groupe de données est rempli directement à partir d'une base de données, vous appelez en général la méthode `Fill`  d'un adaptateur de données, comme dans l'exemple suivant, qui remplit le groupe de données `DsCategories1` :  
  
    ```vb  
    sqlDataAdapter1.Fill(DsCategories1)  
  
    ```  
  
    ```csharp  
    sqlDataAdapter1.Fill(DsCategories1);  
  
    ```  
  
    ```cpp  
    sqlDataAdapter1->Fill(dsCategories1);  
    ```  
  
     Si le groupe de données est rempli via un service Web XML, vous créez en général une instance de ce service dans le code et appelez une de ses méthodes pour retourner un groupe de données.  Ensuite, vous fusionnez le groupe de données issu du service Web XML avec le groupe de données local.  L'exemple suivant montre comment créer une instance d'un service Web XML nommé `CategoriesService`, appeler sa méthode `GetCategories` et fusionner le groupe de données résultant dans un groupe de données local nommé `DsCategories1` :  
  
    ```vb  
    Dim ws As New MyProject.localhost.CategoriesService()  
    ws.Credentials = System.Net.CredentialCache.DefaultCredentials  
    DsCategories1.Merge(ws.GetCategories())  
  
    ```  
  
    ```csharp  
    MyProject.localhost.CategoriesService ws = new MyProject.localhost.CategoriesService();  
    ws.Credentials = System.Net.CredentialCache.DefaultCredentials;  
    DsCategories1.Merge(ws.GetCategories());  
  
    ```  
  
    ```cpp  
    MyProject::localhost::CategoriesService^ ws =   
       new MyProject::localhost::CategoriesService();  
    ws->Credentials = System::Net::CredentialCache::DefaultCredentials;  
    dsCategories1->Merge(ws->GetCategories());  
    ```  
  
2.  Appelez la méthode <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> du contrôle <xref:System.Windows.Forms.DataGrid>, en lui passant la source de données et une donnée membre.  Si vous devez passer explicitement une donnée membre, passez une chaîne vide.  
  
    > [!NOTE]
    >  Si vous liez la grille pour la première fois, vous pouvez définir les propriétés <xref:System.Windows.Forms.DataGrid.DataSource%2A> et <xref:System.Windows.Forms.DataGrid.DataMember%2A> du contrôle.  Toutefois, une fois ces propriétés définies, vous ne pouvez pas les réinitialiser.  Il est donc recommandé d'utiliser systématiquement la méthode <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A>.  
  
     L'exemple suivant montre comment effectuer la liaison par programme à la table Customers d'un groupe de données nommé `DsCustomers1` :  
  
    ```vb  
    DataGrid1.SetDataBinding(DsCustomers1, "Customers")  
  
    ```  
  
    ```csharp  
    DataGrid1.SetDataBinding(DsCustomers1, "Customers");  
  
    ```  
  
    ```cpp  
    dataGrid1->SetDataBinding(dsCustomers1, "Customers");  
    ```  
  
     Si la table Customers est la seule du groupe de données, vous pourriez également lier la grille comme suit :  
  
    ```vb  
    DataGrid1.SetDataBinding(DsCustomers1, "")  
  
    ```  
  
    ```csharp  
    DataGrid1.SetDataBinding(DsCustomers1, "");  
  
    ```  
  
    ```cpp  
    dataGrid1->SetDataBinding(dsCustomers1, "");  
    ```  
  
3.  \(Facultatif\) Ajoutez les styles de table et de colonne appropriés à la grille.  S'il n'existe pas de style de table, la table s'affichera avec une mise en forme minimale et toutes ses colonnes visibles.  
  
## Voir aussi  
 [Vue d'ensemble du contrôle DataGrid](../../../../docs/framework/winforms/controls/datagrid-control-overview-windows-forms.md)   
 [Comment  : ajouter des tables et des colonnes au contrôle DataGrid Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)   
 [DataGrid, contrôle](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)   
 [Liaison de données Windows Forms](../../../../docs/framework/winforms/windows-forms-data-binding.md)