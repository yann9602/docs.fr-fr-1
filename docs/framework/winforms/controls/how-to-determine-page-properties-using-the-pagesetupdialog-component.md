---
title: "Comment&#160;: d&#233;terminer les propri&#233;t&#233;s de la page &#224; l&#39;aide du composant PageSetupDialog | Microsoft Docs"
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
  - "propriétés de la page"
  - "mise en page"
  - "PageSetupDialog (composant)"
ms.assetid: 6dae05bc-c0fd-4357-bb93-841a1631d98f
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# Comment&#160;: d&#233;terminer les propri&#233;t&#233;s de la page &#224; l&#39;aide du composant PageSetupDialog
Le composant [PageSetupDialog](../../../../docs/framework/winforms/controls/pagesetupdialog-component-windows-forms.md) présente des options de disposition, de format du papier et d’autres choix de mise en page à l’utilisateur pour un document.  
  
 Vous devez spécifier une instance de la classe <xref:System.Drawing.Printing.PrintDocument> ; il s’agit du document à imprimer. De plus, les utilisateurs doivent avoir une imprimante installée sur leur ordinateur, localement ou sur un réseau, car c’est en partie comme cela que le composant <xref:System.Windows.Forms.PageSetupDialog> détermine les choix de mise en page présentés à l’utilisateur.  
  
 L’interaction entre le composant <xref:System.Windows.Forms.PageSetupDialog> et la classe <xref:System.Drawing.Printing.PageSettings> constitue l’un des aspects importants de son utilisation. La classe <xref:System.Drawing.Printing.PageSettings> sert à spécifier des paramètres qui modifient la façon dont une page est imprimée, comme l’orientation du papier, le format de la page et les marges. Chacun de ces paramètres est représenté en tant que propriété de la classe <xref:System.Drawing.Printing.PageSettings>. La classe <xref:System.Windows.Forms.PageSetupDialog> modifie ces valeurs de propriétés pour une instance donnée de la classe <xref:System.Drawing.Printing.PageSettings> associée au document \(et représentée en tant que propriété <xref:System.Drawing.Printing.PrintDocument.DefaultPageSettings%2A>\).  
  
### Pour définir les propriétés de la page à l’aide du composant PageSetupDialog  
  
1.  Utilisez la méthode <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> pour afficher la boîte de dialogue, en spécifiant le <xref:System.Drawing.Printing.PrintDocument> à utiliser.  
  
     Dans l’exemple ci\-dessous, le gestionnaire d’événements <xref:System.Windows.Forms.Control.Click> du contrôle <xref:System.Windows.Forms.Button> ouvre une instance du composant <xref:System.Windows.Forms.PageSetupDialog>. Un document existant est spécifié dans la propriété <xref:System.Windows.Forms.PageSetupDialog.Document%2A>, et sa propriété <xref:System.Drawing.Printing.PageSettings.Color%2A?displayProperty=fullName> prend la valeur `false`.  
  
     L’exemple part du principe que votre formulaire contient un contrôle <xref:System.Windows.Forms.Button>, un composant <xref:System.Drawing.Printing.PrintDocument> nommé `myDocument`, et un composant <xref:System.Windows.Forms.PageSetupDialog>.  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, _  
    ByVal e As System.EventArgs) Handles Button1.Click  
       ' The print document 'myDocument' used below  
       ' is merely for an example.  
       'You will have to specify your own print document.  
       PageSetupDialog1.Document = myDocument  
       ' Sets the print document's color setting to false,  
       ' so that the page will not be printed in color.  
       PageSetupDialog1.Document.DefaultPageSettings.Color = False  
       PageSetupDialog1.ShowDialog()  
    End Sub  
  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       // The print document 'myDocument' used below  
       // is merely for an example.  
       // You will have to specify your own print document.  
       pageSetupDialog1.Document = myDocument;  
       // Sets the print document's color setting to false,  
       // so that the page will not be printed in color.  
       pageSetupDialog1.Document.DefaultPageSettings.Color = false;  
       pageSetupDialog1.ShowDialog();  
    }  
  
    ```  
  
    ```cpp  
    private:  
       System::Void button1_Click(System::Object ^  sender,  
          System::EventArgs ^  e)  
       {  
          // The print document 'myDocument' used below  
          // is merely for an example.  
          // You will have to specify your own print document.  
          pageSetupDialog1->Document = myDocument;  
          // Sets the print document's color setting to false,  
          // so that the page will not be printed in color.  
          pageSetupDialog1->Document->DefaultPageSettings->Color = false;  
          pageSetupDialog1->ShowDialog();  
       }  
    ```  
  
     \([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] et [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]\) Placez le code suivant dans le constructeur du formulaire pour inscrire le gestionnaire d'événements.  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
  
    ```  
  
    ```cpp  
    this->button1->Click += gcnew   
       System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## Voir aussi  
 <xref:System.Windows.Forms.PageSetupDialog>   
 [Comment : créer des travaux d'impression Windows Forms standard](../../../../docs/framework/winforms/advanced/how-to-create-standard-windows-forms-print-jobs.md)   
 [PageSetupDialog, composant](../../../../docs/framework/winforms/controls/pagesetupdialog-component-windows-forms.md)