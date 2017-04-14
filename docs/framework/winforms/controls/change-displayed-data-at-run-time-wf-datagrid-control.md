---
title: "Comment&#160;: modifier des donn&#233;es affich&#233;es dans le contr&#244;le DataGrid Windows Forms au moment de l&#39;ex&#233;cution | Microsoft Docs"
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
  - "cellules, changer les valeurs de cellules DataGrid"
  - "DataGrid (contrôle Windows Forms), liaison de données"
  - "DataGrid (contrôle Windows Forms), modifier dynamiquement au moment de l'exécution"
ms.assetid: 0c7a6d00-30de-416e-8223-0a81ddb4c1f8
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# Comment&#160;: modifier des donn&#233;es affich&#233;es dans le contr&#244;le DataGrid Windows Forms au moment de l&#39;ex&#233;cution
> [!NOTE]
>  Le contrôle <xref:System.Windows.Forms.DataGridView> remplace le contrôle <xref:System.Windows.Forms.DataGrid> et lui ajoute des fonctionnalités ; toutefois, le contrôle <xref:System.Windows.Forms.DataGrid> est conservé pour la compatibilité descendante et l'utilisation future si tel est votre choix.  Pour plus d'informations, consultez [Différences entre les contrôles DataGridView et DataGrid Windows Forms](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Après avoir généré un contrôle <xref:System.Windows.Forms.DataGrid> Windows Forms à l'aide des fonctionnalités de design, vous pouvez modifier dynamiquement certains éléments de l'objet <xref:System.Data.DataSet> de la grille au moment de l'exécution.  Vous pouvez, par exemple, modifier certaines valeurs de la table ou changer la source de données liée au contrôle <xref:System.Windows.Forms.DataGrid>.  Les modifications apportées aux valeurs individuelles sont effectuées par le biais de l'objet <xref:System.Data.DataSet> et non du contrôle <xref:System.Windows.Forms.DataGrid>.  
  
### Pour modifier les données par programme  
  
1.  Spécifiez une table de l'objet <xref:System.Data.DataSet> ainsi que la ligne et le champ souhaités, et attribuez la nouvelle valeur à la cellule.  
  
    > [!NOTE]
    >  Pour spécifier la première table de <xref:System.Data.DataSet> ou la première ligne de la table, indiquez 0.  
  
     L'exemple suivant montre comment modifier la seconde entrée de la première ligne de la première table d'un groupe de données en cliquant sur `Button1`.  <xref:System.Data.DataSet> \(`ds`\) et les tables \(`0` et`1`\) ont été créés au préalable.  
  
    ```vb  
    Protected Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
       ds.tables(0).rows(0)(1) = "NewEntry"  
    End Sub  
  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       ds.Tables[0].Rows[0][1]="NewEntry";  
    }  
  
    ```  
  
    ```cpp  
    private:   
       void button1_Click(System::Object^ sender, System::EventArgs^ e)  
       {  
          dataSet1->Tables[0]->Rows[0][1] = "NewEntry";  
       }  
    ```  
  
     \([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]\) Placez le code suivant dans le constructeur du formulaire pour inscrire le gestionnaire d'événements.  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
  
    ```  
  
    ```cpp  
    this->button1->Click +=  
       gcnew System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
     Au moment de l'exécution, vous pouvez utiliser la méthode <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> pour lier le contrôle <xref:System.Windows.Forms.DataGrid> à une autre source de données.  Par exemple, vous pouvez avoir plusieurs contrôles de données [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] connectés chacun à une base de données différente.  
  
### Pour modifier la source de données par programme  
  
1.  Attribuez à la méthode <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> le nom de la source de données et de la table à lier.  
  
     L'exemple suivant montre comment utiliser la méthode <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> pour remplacer la source de données par un contrôle de données [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] \(adoPubsAuthors\) connecté à la table Authors de la base de données Pubs.  
  
    ```vb  
    Private Sub ResetSource()  
       DataGrid1.SetDataBinding(adoPubsAuthors, "Authors")  
    End Sub  
  
    ```  
  
    ```csharp  
    private void ResetSource()  
    {  
       DataGrid1.SetDataBinding(adoPubsAuthors, "Authors");  
    }  
  
    ```  
  
    ```cpp  
    private:  
       void ResetSource()  
       {  
          dataGrid1->SetDataBinding(adoPubsAuthors, "Authors");  
       }  
    ```  
  
## Voir aussi  
 [Datasets ADO.NET](../../../../docs/framework/data/adonet/ado-net-datasets.md)   
 [Comment : supprimer ou masquer des colonnes dans le contrôle DataGrid Windows Forms](../../../../docs/framework/winforms/controls/how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)   
 [Comment  : ajouter des tables et des colonnes au contrôle DataGrid Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)   
 [Comment : lier le contrôle DataGrid Windows Forms à une source de données](../../../../docs/framework/winforms/controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)