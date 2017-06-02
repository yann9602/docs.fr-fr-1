---
title: "Comment&#160;: afficher une liste de polices &#224; l&#39;aide du composant FontDialog | Microsoft Docs"
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
  - "Police (boîte de dialogue), afficher"
  - "Font (propriété), définir avec le composant FontDialog"
  - "FontDialog (composant Windows Forms)"
  - "polices, attributs"
  - "polices, sélectionner"
  - "polices, afficher la liste"
ms.assetid: 35692c1b-0937-4b7a-9207-1ae6bdc244a0
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# Comment&#160;: afficher une liste de polices &#224; l&#39;aide du composant FontDialog
Le composant [FontDialog](../../../../docs/framework/winforms/controls/fontdialog-component-windows-forms.md) permet à l'utilisateur de sélectionner une police et de modifier différents aspects de son affichage, comme sa taille et son épaisseur.  
  
 La police sélectionnée dans la boîte de dialogue est retournée dans la propriété <xref:System.Windows.Forms.FontDialog.Font%2A>.  Par conséquent, le fait de tirer parti de la police sélectionnée par l'utilisateur est aussi aisé que la lecture d'une propriété.  
  
### Pour sélectionner des propriétés de police à l'aide du composant FontDialog  
  
1.  Affichez la boîte de dialogue à l'aide de la méthode <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A>.  
  
2.  Utilisez la propriété <xref:System.Windows.Forms.DialogResult> pour déterminer la façon dont la boîte de dialogue a été fermée.  
  
3.  Utilisez la propriété <xref:System.Windows.Forms.FontDialog.Font%2A> pour définir la police souhaitée.  
  
     Dans l'exemple ci\-dessous, le gestionnaire d'événements <xref:System.Windows.Forms.Control.Click> du contrôle <xref:System.Windows.Forms.Button> ouvre un composant <xref:System.Windows.Forms.FontDialog>.  Lorsqu'une police est sélectionnée et que l'utilisateur clique sur **OK**, la propriété <xref:System.Windows.Forms.FontDialog.Font%2A> d'un contrôle <xref:System.Windows.Forms.TextBox> contenu dans le formulaire est définie sur la police choisie.  Cet exemple suppose que votre formulaire contient un contrôle <xref:System.Windows.Forms.Button>, un contrôle <xref:System.Windows.Forms.TextBox> et un composant <xref:System.Windows.Forms.FontDialog>.  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, _  
       ByVal e As System.EventArgs) Handles Button1.Click  
       If FontDialog1.ShowDialog() = DialogResult.OK Then  
          TextBox1.Font = FontDialog1.Font  
       End If  
    End Sub  
  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       if(fontDialog1.ShowDialog() == DialogResult.OK)  
       {  
          textBox1.Font = fontDialog1.Font;  
       }  
    }  
  
    ```  
  
    ```cpp  
    private:  
       void button1_Click(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          if(fontDialog1->ShowDialog() == DialogResult::OK)  
          {  
             textBox1->Font = fontDialog1->Font;  
          }  
       }  
    ```  
  
     \([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] et [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]\) Placez le code suivant dans le constructeur du formulaire pour inscrire le gestionnaire d'événements.  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
  
    ```  
  
    ```cpp  
    button1->Click += gcnew System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## Voir aussi  
 <xref:System.Windows.Forms.FontDialog>   
 [FontDialog, composant](../../../../docs/framework/winforms/controls/fontdialog-component-windows-forms.md)