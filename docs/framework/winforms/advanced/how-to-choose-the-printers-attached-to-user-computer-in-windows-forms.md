---
title: "Comment : choisir les imprimantes connectées à un utilisateur &#39; ordinateur s dans les Windows Forms"
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
- printing [Windows Forms], choosing printers
- printers [Windows Forms], choosing
ms.assetid: 63c1172b-2931-4ac0-953f-37f629494bbf
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ec334ff65095e11855d706f445fda1d4b7ea1472
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-choose-the-printers-attached-to-a-user39s-computer-in-windows-forms"></a>Comment : choisir les imprimantes connectées à un utilisateur &#39; ordinateur s dans les Windows Forms
Souvent, les utilisateurs souhaitent choisir une imprimante autre que l’imprimante par défaut. Vous pouvez permettre aux utilisateurs de choisir une imprimante parmi celles installées actuellement à l’aide du composant <xref:System.Windows.Forms.PrintDialog> . Par le biais du composant <xref:System.Windows.Forms.PrintDialog> , le <xref:System.Windows.Forms.DialogResult> du composant <xref:System.Windows.Forms.PrintDialog> est capturé et utilisé pour sélectionner l’imprimante.  
  
 Dans la procédure suivante, un fichier texte est sélectionné pour impression vers l’imprimante par défaut. La classe <xref:System.Windows.Forms.PrintDialog> est ensuite instanciée.  
  
### <a name="to-choose-a-printer-and-then-print-a-file"></a>Pour choisir une imprimante, puis imprimer un fichier  
  
1.  Sélectionnez l’imprimante à utiliser à l’aide de la <xref:System.Windows.Forms.PrintDialog> composant.  
  
     Dans l’exemple de code suivant, deux événements sont gérés. Dans la première, un <xref:System.Windows.Forms.Button> du contrôle <xref:System.Windows.Forms.Control.Click> événement, le <xref:System.Windows.Forms.PrintDialog> classe est instanciée et l’imprimante sélectionnée par l’utilisateur est capturée dans le <xref:System.Windows.Forms.DialogResult> propriété.  
  
     Dans le second événement, le <xref:System.Drawing.Printing.PrintDocument.PrintPage> l’événement de la <xref:System.Drawing.Printing.PrintDocument> composant, un exemple de document est imprimée sur l’imprimante spécifiée.  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As Object, ByVal e As System.EventArgs) Handles Button1.Click  
       Dim PrintDialog1 As New PrintDialog()  
       PrintDialog1.Document = PrintDocument1  
       Dim result As DialogResult = PrintDialog1.ShowDialog()  
  
       If (result = DialogResult.OK) Then  
         PrintDocument1.Print()  
       End If   
  
    End Sub  
  
    Private Sub PrintDocument1_PrintPage(ByVal sender As Object, ByVal e As System.Drawing.Printing.PrintPageEventArgs) Handles PrintDocument1.PrintPage  
       e.Graphics.FillRectangle(Brushes.Red, New Rectangle(500, 500, 500, 500))          
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       PrintDialog printDialog1 = new PrintDialog();  
       printDialog1.Document = printDocument1;  
       DialogResult result = printDialog1.ShowDialog();  
       if (result == DialogResult.OK)  
       {  
          printDocument1.Print();  
       }  
    }  
  
    private void printDocument1_PrintPage(object sender,   
    System.Drawing.Printing.PrintPageEventArgs e)  
    {  
       e.Graphics.FillRectangle(Brushes.Red,   
         new Rectangle(500, 500, 500, 500));  
    }  
    ```  
  
    ```cpp  
    private:  
       void button1_Click(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          PrintDialog ^ printDialog1 = gcnew PrintDialog();  
          printDialog1->Document = printDocument1;  
          System::Windows::Forms::DialogResult result =   
             printDialog1->ShowDialog();  
          if (result == DialogResult::OK)  
          {  
             printDocument1->Print();  
          }  
       }  
    private:  
       void printDocument1_PrintPage(System::Object ^ sender,  
          System::Drawing::Printing::PrintPageEventArgs ^ e)  
       {  
          e->Graphics->FillRectangle(Brushes::Red,  
             Rectangle(500, 500, 500, 500));  
       }  
    ```  
  
     ([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] et [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Placez le code suivant dans le constructeur du formulaire pour inscrire le gestionnaire d'événements.  
  
    ```csharp  
    this.printDocument1.PrintPage += new  
       System.Drawing.Printing.PrintPageEventHandler  
       (this.printDocument1_PrintPage);  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->printDocument1->PrintPage += gcnew  
       System::Drawing::Printing::PrintPageEventHandler  
       (this, &Form1::printDocument1_PrintPage);  
    this->button1->Click += gcnew  
       System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Prise en charge de l’impression dans les Windows Forms](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)
