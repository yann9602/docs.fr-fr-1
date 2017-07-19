---
title: "Comment&#160;: charger des fichiers dans le contr&#244;le RichTextBox Windows Forms | Microsoft Docs"
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
  - "zones de texte, afficher les fichiers"
  - "exemples [Windows Forms], zones de texte"
  - "fichiers .rtf, ouvrir dans le contrôle RichTextBox"
  - "fichiers RTF, ouvrir dans le contrôle RichTextBox"
  - "fichiers texte, afficher dans le contrôle RichTextBox"
  - "fichiers .rtf, afficher dans le contrôle RichTextBox"
  - "contrôle RichTextBox [Windows Forms], ouvrir des fichiers"
  - "fichiers RTF, afficher dans le contrôle RichTextBox"
ms.assetid: c03451be-f285-4428-a71a-c41e002cc919
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# Comment&#160;: charger des fichiers dans le contr&#244;le RichTextBox Windows Forms
Le contrôle <xref:System.Windows.Forms.RichTextBox> Windows Forms peut afficher du texte brut, du texte brut Unicode ou un fichier au format RTF\( Rich\-Text Format\). Pour cela, appelez la méthode <xref:System.Windows.Forms.RichTextBox.LoadFile%2A>. Vous pouvez également utiliser la méthode <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> pour charger des données à partir d’un flux de données. Pour plus d'informations, consultez <xref:System.Windows.Forms.RichTextBox.LoadFile%28System.IO.Stream%2CSystem.Windows.Forms.RichTextBoxStreamType%29>.  
  
### Pour charger un fichier dans le contrôle RichTextBox  
  
1.  Déterminez le chemin du fichier à ouvrir à l’aide du composant <xref:System.Windows.Forms.OpenFileDialog>. Pour une vue d'ensemble, consultez [Vue d'ensemble du composant OpenFileDialog](../../../../docs/framework/winforms/controls/openfiledialog-component-overview-windows-forms.md).  
  
2.  Appelez la méthode <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> du contrôle <xref:System.Windows.Forms.RichTextBox> en spécifiant le fichier à charger et, éventuellement, un type de fichier. Dans l’exemple ci\-dessous, le fichier à charger est spécifié par la propriété <xref:System.Windows.Forms.FileDialog.FileName%2A> du composant <xref:System.Windows.Forms.OpenFileDialog>. Si vous appelez la méthode en spécifiant un nom de fichier comme seul argument, le type de fichier est supposé être RTF. Pour spécifier un autre type de fichier, appelez la méthode en spécifiant une valeur pour l’énumération <xref:System.Windows.Forms.RichTextBoxStreamType> comme deuxième argument.  
  
     Dans l’exemple ci\-dessous, le composant <xref:System.Windows.Forms.OpenFileDialog> s’affiche quand l’utilisateur clique sur un bouton. Le fichier sélectionné est ensuite ouvert et affiché dans le contrôle <xref:System.Windows.Forms.RichTextBox>. Cet exemple suppose qu’un formulaire contient un bouton, `btnOpenFile`.  
  
    ```vb  
    Private Sub btnOpenFile_Click(ByVal sender As System.Object, _  
       ByVal e As System.EventArgs) Handles btnOpenFile.Click  
         If OpenFileDialog1.ShowDialog() = DialogResult.OK Then  
           RichTextBox1.LoadFile(OpenFileDialog1.FileName, _  
              RichTextBoxStreamType.RichText)  
          End If  
    End Sub  
  
    ```  
  
    ```csharp  
    private void btnOpenFile_Click(object sender, System.EventArgs e)  
    {  
       if(openFileDialog1.ShowDialog() == DialogResult.OK)  
       {  
         richTextBox1.LoadFile(openFileDialog1.FileName, RichTextBoxStreamType.RichText);  
       }  
    }  
  
    ```  
  
    ```cpp  
    private:  
       void btnOpenFile_Click(System::Object ^  sender,  
          System::EventArgs ^  e)  
       {  
          if(openFileDialog1->ShowDialog() == DialogResult::OK)  
          {  
             richTextBox1->LoadFile(openFileDialog1->FileName,  
                RichTextBoxStreamType::RichText);  
          }  
       }  
    ```  
  
     \([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]\) Placez le code suivant dans le constructeur du formulaire pour inscrire le gestionnaire d’événements.  
  
    ```csharp  
    this.btnOpenFile.Click += new System.EventHandler(this. btnOpenFile_Click);  
  
    ```  
  
    ```cpp  
    this->btnOpenFile->Click += gcnew   
       System::EventHandler(this, &Form1::btnOpenFile_Click);  
    ```  
  
    > [!IMPORTANT]
    >  Pour exécuter ce processus, votre assembly peut nécessiter un niveau de privilège accordé par la classe <xref:System.Security.Permissions.FileIOPermission?displayProperty=fullName>. Si vous l’exécutez dans un contexte de confiance partielle, le processus peut lever une exception en raison de privilèges insuffisants. Pour plus d'informations, consultez [Notions fondamentales de la sécurité d'accès du code](../../../../docs/framework/misc/code-access-security-basics.md).  
  
## Voir aussi  
 <xref:System.Windows.Forms.RichTextBox.LoadFile%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.RichTextBox>   
 [RichTextBox, contrôle](../../../../docs/framework/winforms/controls/richtextbox-control-windows-forms.md)   
 [Contrôles à utiliser dans les Windows Forms](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)