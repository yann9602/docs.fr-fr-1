---
title: "Comment&#160;: choisir les imprimantes connect&#233;es &#224; l&#39;ordinateur d&#39;un utilisateur dans Windows Forms | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "impression (Windows Forms), choix d’imprimantes"
  - "imprimantes, choix"
ms.assetid: 63c1172b-2931-4ac0-953f-37f629494bbf
caps.latest.revision: 19
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 19
---
# Comment&#160;: choisir les imprimantes connect&#233;es &#224; l&#39;ordinateur d&#39;un utilisateur dans Windows Forms
Souvent, les utilisateurs souhaitent choisir une imprimante autre que l’imprimante par défaut. Vous pouvez permettre aux utilisateurs de choisir une imprimante parmi celles installées actuellement à l’aide du composant <xref:System.Windows.Forms.PrintDialog>. Par le biais du composant <xref:System.Windows.Forms.PrintDialog>, le <xref:System.Windows.Forms.DialogResult> du composant <xref:System.Windows.Forms.PrintDialog> est capturé et utilisé pour sélectionner l’imprimante.  
  
 Dans la procédure suivante, un fichier texte est sélectionné pour impression vers l’imprimante par défaut. La classe <xref:System.Windows.Forms.PrintDialog> est ensuite instanciée.  
  
### Pour choisir une imprimante, puis imprimer un fichier  
  
1.  Sélectionnez l’imprimante à utiliser à l’aide du composant <xref:System.Windows.Forms.PrintDialog>**.**  
  
     Dans l’exemple de code suivant, deux événements sont gérés. Dans le premier, l’événement <xref:System.Windows.Forms.Control.Click> d’un contrôle <xref:System.Windows.Forms.Button>, la classe <xref:System.Windows.Forms.PrintDialog>est instanciée et l’imprimante sélectionnée par l’utilisateur est capturée dans la propriété <xref:System.Windows.Forms.DialogResult>**.**  
  
     Dans le second événement, l’événement <xref:System.Drawing.Printing.PrintDocument.PrintPage> du composant <xref:System.Drawing.Printing.PrintDocument>**, un exemple de document est imprimé sur l’imprimante spécifiée.**  
  
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
  
     \([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] et [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]\) Placez le code suivant dans le constructeur du formulaire pour inscrire le gestionnaire d'événements.  
  
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
  
## Voir aussi  
 [Prise en charge de l'impression dans les Windows Forms](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)