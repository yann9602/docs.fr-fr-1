---
title: "Comment&#160;: afficher des erreurs d&#39;un groupe de donn&#233;es &#224; l&#39;aide du composant ErrorProvider Windows Forms | Microsoft Docs"
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
  - "messages d'erreur, afficher dans les groupes de données"
  - "ErrorProvider (composant Windows Forms), erreurs des groupes de données"
  - "erreurs (Windows Forms), erreurs des groupes de données"
ms.assetid: cbae023f-d651-4210-bdea-bcc5f037e321
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# Comment&#160;: afficher des erreurs d&#39;un groupe de donn&#233;es &#224; l&#39;aide du composant ErrorProvider Windows Forms
Le composant <xref:System.Windows.Forms.ErrorProvider> Windows Forms permet d'afficher des erreurs présentes dans les colonnes d'un groupe de données ou d'une autre source de données.  Pour qu'un composant <xref:System.Windows.Forms.ErrorProvider> affiche des erreurs de données dans un formulaire, il n'a pas besoin d'être directement associé à un contrôle.  Une fois lié à une source de données, il peut afficher une icône d'erreur en regard de tout contrôle lié à la même source de données.  
  
> [!NOTE]
>  Si vous modifiez les propriétés <xref:System.Windows.Forms.ErrorProvider.DataSource%2A> et <xref:System.Windows.Forms.ErrorProvider.DataMember%2A> du fournisseur d'erreurs au moment de l'exécution, vous devez utiliser la méthode <xref:System.Windows.Forms.ErrorProvider.BindToDataAndErrors%2A> pour éviter les conflits.  
  
### Pour afficher des erreurs de données  
  
1.  Liez le composant à une colonne d'une table de données.  
  
    ```vb  
    ' Assumes existence of DataSet1, DataTable1  
    TextBox1.DataBindings.Add("Text", DataSet1, "Customers.Name")  
    ErrorProvider1.DataSource = DataSet1  
    ErrorProvider1.DataMember = "Customers"  
  
    ```  
  
    ```csharp  
    // Assumes existence of DataSet1, DataTable1  
    textBox1.DataBindings.Add("Text", DataSet1, "Customers.Name");  
    errorProvider1.DataSource = DataSet1;  
    errorProvider1.DataMember = "Customers";  
  
    ```  
  
2.  Affectez la propriété <xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A> au formulaire.  
  
    ```vb  
    ErrorProvider1.ContainerControl = Me  
  
    ```  
  
    ```csharp  
    errorProvider1.ContainerControl = this;  
  
    ```  
  
3.  Définissez la position de l'enregistrement en cours sur une ligne contenant une erreur de colonne.  
  
    ```vb  
    DataTable1.Rows(5).SetColumnError("Name", "Bad data in this row.")  
    Me.BindingContext(DataTable1).Position = 5  
  
    ```  
  
    ```csharp  
    DataTable1.Rows[5].SetColumnError("Name", "Bad data in this row.");  
    this.BindingContext [DataTable1].Position = 5;  
  
    ```  
  
## Voir aussi  
 [Vue d'ensemble du composant ErrorProvider](../../../../docs/framework/winforms/controls/errorprovider-component-overview-windows-forms.md)   
 [Comment : afficher des icônes d'erreur pour la validation de formulaire à l'aide du composant ErrorProvider Windows Forms](../../../../docs/framework/winforms/controls/display-error-icons-for-form-validation-with-wf-errorprovider.md)