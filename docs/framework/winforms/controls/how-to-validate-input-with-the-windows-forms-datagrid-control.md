---
title: "Comment&#160;: valider les entr&#233;es &#224; l&#39;aide du contr&#244;le DataGrid Windows Forms | Microsoft Docs"
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
  - "DataGrid (contrôle Windows Forms), exemples"
  - "DataGrid (contrôle Windows Forms), valider une entrée"
  - "exemples (Windows Forms), DataGrid (contrôle)"
  - "entrée d'utilisateur, valider"
  - "validation, entrée d'utilisateur"
ms.assetid: f1e9c3a0-d0a1-4893-a615-b4b0db046c63
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# Comment&#160;: valider les entr&#233;es &#224; l&#39;aide du contr&#244;le DataGrid Windows Forms
> [!NOTE]
>  Le contrôle <xref:System.Windows.Forms.DataGridView> remplace le contrôle <xref:System.Windows.Forms.DataGrid> et lui ajoute des fonctionnalités ; toutefois, le contrôle <xref:System.Windows.Forms.DataGrid> est conservé pour la compatibilité descendante et l'utilisation future si tel est votre choix.  Pour plus d'informations, consultez [Différences entre les contrôles DataGridView et DataGrid Windows Forms](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Deux types de validation d'entrées sont disponibles pour le contrôle <xref:System.Windows.Forms.DataGrid> Windows Forms.  Si l'utilisateur tente d'entrer une valeur dont le type n'est pas accepté par la cellule, par exemple une chaîne dans un entier, cette nouvelle valeur invalide est remplacée par l'ancienne valeur.  Ce type de validation d'entrée s'effectue automatiquement et ne peut pas être personnalisé.  
  
 Le second type de validation d'entrée permet de refuser des données qui ne peuvent pas être acceptées, par exemple une valeur 0 dans un champ devant contenir une valeur supérieure ou égale à 1, ou une chaîne inappropriée.  Pour cela, il fait écrire dans le groupe de données un gestionnaire d'événements pour l'événement <xref:System.Data.DataTable.ColumnChanging> ou <xref:System.Data.DataTable.RowChanging>.  L'exemple ci\-dessous utilise l'événement <xref:System.Data.DataTable.ColumnChanging> car l'entrée de la valeur inacceptable n'est pas autorisée dans la colonne « Product ».  Vous pouvez utiliser l'événement <xref:System.Data.DataTable.RowChanging> pour vérifier que la valeur d'une colonne « End Date » est postérieure à celle d'une colonne « Start Date » dans une même ligne.  
  
### Pour valider des entrées d'utilisateur  
  
1.  Écrivez du code pour gérer l'événement <xref:System.Data.DataTable.ColumnChanging> de la table appropriée.  Si une entrée incorrecte est détectée, appelez la méthode <xref:System.Data.DataRow.SetColumnError%2A> de l'objet <xref:System.Data.DataRow>.  
  
    ```vb  
    Private Sub Customers_ColumnChanging(ByVal sender As Object, _  
    ByVal e As System.Data.DataColumnChangeEventArgs)  
       ' Only check for errors in the Product column  
       If (e.Column.ColumnName.Equals("Product")) Then  
          ' Do not allow "Automobile" as a product.  
          If CType(e.ProposedValue, String) = "Automobile" Then  
             Dim badValue As Object = e.ProposedValue  
             e.ProposedValue = "Bad Data"  
             e.Row.RowError = "The Product column contians an error"  
             e.Row.SetColumnError(e.Column, "Product cannot be " & _  
             CType(badValue, String))  
          End If  
       End If  
    End Sub  
  
    ```  
  
    ```csharp  
    //Handle column changing events on the Customers table  
    private void Customers_ColumnChanging(object sender, System.Data.DataColumnChangeEventArgs e) {  
  
       //Only check for errors in the Product column  
       if (e.Column.ColumnName.Equals("Product")) {  
  
          //Do not allow "Automobile" as a product  
          if (e.ProposedValue.Equals("Automobile")) {  
             object badValue = e.ProposedValue;  
             e.ProposedValue = "Bad Data";  
             e.Row.RowError = "The Product column contains an error";  
             e.Row.SetColumnError(e.Column, "Product cannot be " + badValue);  
          }  
       }  
    }  
  
    ```  
  
2.  Connectez le gestionnaire d'événements à l'événement.  
  
     Placez le code suivant dans l'événement <xref:System.Windows.Forms.Form.Load> du formulaire ou dans son constructeur.  
  
    ```vb  
    ' Assumes the grid is bound to a dataset called customersDataSet1  
    ' with a table called Customers.  
    ' Put this code in the form's Load event or its constructor.  
    AddHandler customersDataSet1.Tables("Customers").ColumnChanging, AddressOf Customers_ColumnChanging  
  
    ```  
  
    ```csharp  
    // Assumes the grid is bound to a dataset called customersDataSet1  
    // with a table called Customers.  
    // Put this code in the form's Load event or its constructor.  
    customersDataSet1.Tables["Customers"].ColumnChanging += new DataColumnChangeEventHandler(this.Customers_ColumnChanging);  
  
    ```  
  
## Voir aussi  
 <xref:System.Windows.Forms.DataGrid>   
 <xref:System.Data.DataTable.ColumnChanging>   
 <xref:System.Data.DataRow.SetColumnError%2A>   
 [DataGrid, contrôle](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)