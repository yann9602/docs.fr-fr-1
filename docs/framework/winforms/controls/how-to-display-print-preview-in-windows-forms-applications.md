---
title: "Comment&#160;: afficher l&#39;aper&#231;u avant impression dans les applications Windows Forms | Microsoft Docs"
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
  - "exemples (Windows Forms), aperçu avant impression"
  - "aperçu avant impression, afficher"
  - "imprimer (Windows Forms), aperçu avant impression"
ms.assetid: e394134c-0886-4517-bd8d-edc4a3749eb5
caps.latest.revision: 19
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 19
---
# Comment&#160;: afficher l&#39;aper&#231;u avant impression dans les applications Windows Forms
Vous pouvez utiliser le contrôle <xref:System.Windows.Forms.PrintPreviewDialog> pour permettre aux utilisateurs d'afficher un document, souvent avant qu'il ne soit imprimé.  
  
 Pour ce faire, vous devez spécifier une instance de la classe <xref:System.Drawing.Printing.PrintDocument> ; il s'agit du document à imprimer.  Pour plus d'informations sur l'utilisation de l'aperçu avant impression avec le composant <xref:System.Drawing.Printing.PrintDocument>, consultez [Comment : imprimer dans les Windows Forms en utilisant l'aperçu avant impression](../../../../docs/framework/winforms/advanced/how-to-print-in-windows-forms-using-print-preview.md).  
  
> [!NOTE]
>  Pour utiliser le contrôle <xref:System.Windows.Forms.PrintPreviewDialog> au moment de l'exécution, une imprimante doit être installée sur les ordinateurs des utilisateurs, localement ou via un réseau, car il s'agit de l'un des critères utilisés par le composant <xref:System.Windows.Forms.PrintPreviewDialog> pour déterminer l'apparence du document une fois imprimé.  
  
 Le contrôle <xref:System.Windows.Forms.PrintPreviewDialog> utilise la classe <xref:System.Drawing.Printing.PrinterSettings>.  En outre, le contrôle <xref:System.Windows.Forms.PrintPreviewDialog> utilise la classe <xref:System.Drawing.Printing.PageSettings>, tout comme le composant <xref:System.Windows.Forms.PrintPreviewDialog>.  Le document d'impression spécifié dans la propriété <xref:System.Windows.Forms.PrintPreviewControl.Document%2A> du contrôle <xref:System.Windows.Forms.PrintPreviewDialog> fait référence aux instances à la fois de la classe <xref:System.Drawing.Printing.PrinterSettings> et de la classe <xref:System.Drawing.Printing.PageSettings>, utilisées pour afficher le document dans la fenêtre d'aperçu.  
  
### Pour afficher des pages à l'aide du contrôle PrintPreviewDialog  
  
-   Utilisez la méthode <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> pour afficher la boîte de dialogue, en indiquant le composant <xref:System.Drawing.Printing.PrintDocument> à utiliser.  
  
     Dans l'exemple de code ci\-dessous, le gestionnaire d'événements <xref:System.Windows.Forms.Control.Click> du contrôle <xref:System.Windows.Forms.Button> ouvre une instance du contrôle <xref:System.Windows.Forms.PrintPreviewDialog>.  Le document d'impression est spécifié dans la propriété <xref:System.Windows.Forms.PrintDialog.Document%2A>.  Dans l'exemple ci\-dessous, aucun document d'impression n'est spécifié.  
  
     Cet exemple nécessite que votre formulaire contienne un contrôle <xref:System.Windows.Forms.Button>, un composant <xref:System.Drawing.Printing.PrintDocument> nommé `myDocument` et un contrôle <xref:System.Windows.Forms.PrintPreviewDialog>.  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, _  
       ByVal e As System.EventArgs) Handles Button1.Click  
       ' The print document 'myDocument' used below  
       ' is merely for an example.  
       ' You will have to specify your own print document.  
       PrintPreviewDialog1.Document = myDocument  
       PrintPreviewDialog1.ShowDialog()  
    End Sub  
  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       // The print document 'myDocument' used below  
       // is merely for an example.  
       // You will have to specify your own print document.  
       printPreviewDialog1.Document = myDocument;  
       printPreviewDialog1.ShowDialog();  
    }  
  
    ```  
  
    ```cpp  
    private:  
       void button1_Click(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          // The print document 'myDocument' used below  
          // is merely for an example.  
          // You will have to specify your own print document.  
          printPreviewDialog1->Document = myDocument;  
          printPreviewDialog1->ShowDialog();  
       }  
    ```  
  
     \([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]\) Placez le code suivant dans le constructeur du formulaire pour inscrire le gestionnaire d'événements.  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
  
    ```  
  
    ```cpp  
    this->button1->Click += gcnew  
       System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## Voir aussi  
 [PrintDocument, composant](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md)   
 [PrintPreviewDialog, contrôle](../../../../docs/framework/winforms/controls/printpreviewdialog-control-windows-forms.md)   
 [Prise en charge de l'impression dans les Windows Forms](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)   
 [Windows Forms](../../../../docs/framework/winforms/index.md)