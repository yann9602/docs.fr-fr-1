---
title: "Comment : afficher l’aperçu avant impression dans les applications Windows Forms"
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
- print preview [Windows Forms], displaying
- printing [Windows Forms], print preview
- examples [Windows Forms], print preview
ms.assetid: e394134c-0886-4517-bd8d-edc4a3749eb5
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2567a564b5769abd91d34696c1a94c21ad2913ce
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-display-print-preview-in-windows-forms-applications"></a>Comment : afficher l’aperçu avant impression dans les applications Windows Forms
Vous pouvez utiliser la <xref:System.Windows.Forms.PrintPreviewDialog> contrôle pour permettre aux utilisateurs d’afficher un document, souvent avant qu’il soit à imprimer.  
  
 Pour ce faire, vous devez spécifier une instance de la <xref:System.Drawing.Printing.PrintDocument> classe ; il s’agit du document à imprimer. Pour plus d’informations sur l’utilisation de l’aperçu avant impression avec le <xref:System.Drawing.Printing.PrintDocument> composant, consultez [Comment : imprimer dans les Windows Forms à l’aide d’Aperçu avant impression](../../../../docs/framework/winforms/advanced/how-to-print-in-windows-forms-using-print-preview.md).  
  
> [!NOTE]
>  Pour utiliser le <xref:System.Windows.Forms.PrintPreviewDialog> contrôle au moment de l’exécution, les utilisateurs doivent disposer d’imprimante installée sur son ordinateur, localement ou via un réseau, car il s’agit en partie la <xref:System.Windows.Forms.PrintPreviewDialog> composant détermine à quoi ressemblera un document lors de l’impression.  
  
 Le <xref:System.Windows.Forms.PrintPreviewDialog> de contrôles utilise la <xref:System.Drawing.Printing.PrinterSettings> classe. En outre, le <xref:System.Windows.Forms.PrintPreviewDialog> de contrôles utilise la <xref:System.Drawing.Printing.PageSettings> (classe), tout comme le <xref:System.Windows.Forms.PrintPreviewDialog> du composant. Le document d’impression spécifié dans le <xref:System.Windows.Forms.PrintPreviewDialog> du contrôle <xref:System.Windows.Forms.PrintPreviewControl.Document%2A> propriété fait référence à des instances de la <xref:System.Drawing.Printing.PrinterSettings> et <xref:System.Drawing.Printing.PageSettings> classes et ils sont utilisés pour afficher le document dans la fenêtre d’aperçu.  
  
### <a name="to-view-pages-using-the-printpreviewdialog-control"></a>Pour afficher des pages à l’aide du contrôle PrintPreviewDialog  
  
-   Utilisez la méthode <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> pour afficher la boîte de dialogue, en spécifiant le <xref:System.Drawing.Printing.PrintDocument> à utiliser.  
  
     Dans l’exemple de code suivant, le <xref:System.Windows.Forms.Button> du contrôle <xref:System.Windows.Forms.Control.Click> Gestionnaire d’événements ouvre une instance de la <xref:System.Windows.Forms.PrintPreviewDialog> contrôle. Le document d’impression est spécifié dans le <xref:System.Windows.Forms.PrintDialog.Document%2A> propriété. Dans l’exemple ci-dessous, aucun document d’impression n’est spécifié.  
  
     L’exemple suppose que votre formulaire contient un <xref:System.Windows.Forms.Button> (contrôle), un <xref:System.Drawing.Printing.PrintDocument> composant nommé `myDocument`et un <xref:System.Windows.Forms.PrintPreviewDialog> contrôle.  
  
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
  
     ([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Placez le code suivant dans le constructeur du formulaire pour inscrire le gestionnaire d’événements.  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click += gcnew  
       System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Composant PrintDocument](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md)  
 [PrintPreviewDialog, contrôle](../../../../docs/framework/winforms/controls/printpreviewdialog-control-windows-forms.md)  
 [Prise en charge de l’impression dans les Windows Forms](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)  
 [Windows Forms](../../../../docs/framework/winforms/index.md)
