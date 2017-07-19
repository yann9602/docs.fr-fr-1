---
title: "Comment&#160;: enregistrer des fichiers &#224; l&#39;aide du composant SaveFileDialog | Microsoft Docs"
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
  - "fichiers, enregistrer"
  - "OpenFile (méthode), enregistrer les fichiers avec le composant SaveFileDialog"
  - "SaveFileDialog (composant), enregistrer des fichiers"
  - "enregistrer des fichiers"
ms.assetid: 02e8f409-b83f-4707-babb-e71f6b223d90
caps.latest.revision: 20
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 19
---
# Comment&#160;: enregistrer des fichiers &#224; l&#39;aide du composant SaveFileDialog
Le composant <xref:System.Windows.Forms.SaveFileDialog> permet aux utilisateurs de parcourir le système de fichiers et de sélectionner les fichiers à enregistrer.  La boîte de dialogue retourne le chemin d'accès et le nom du fichier sélectionné dans la boîte de dialogue.  Vous devez toutefois écrire le code pour écrire réellement les fichiers sur le disque.  
  
### Pour enregistrer un fichier à l'aide du composant SaveFileDialog  
  
-   Affichez la boîte de dialogue **Enregistrer le fichier** et appelez une méthode pour enregistrer le fichier sélectionné.  
  
     Utilisez la méthode <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> du composant <xref:System.Windows.Forms.SaveFileDialog> pour enregistrer le fichier.  Cette méthode fournit un objet <xref:System.IO.Stream> dans lequel vous pouvez écrire.  
  
     L'exemple ci\-dessous utilise la propriété <xref:System.Windows.Forms.DialogResult> pour obtenir le nom du fichier, et la méthode <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> pour l'enregistrer.  La méthode <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> fournit un flux dans lequel vous pouvez écrire le fichier.  
  
     Dans l'exemple ci\-dessous, il existe un contrôle <xref:System.Windows.Forms.Button> avec une image qui lui a été assignée.  Lorsque vous cliquez sur le bouton, un composant <xref:System.Windows.Forms.SaveFileDialog> est instancié avec un filtre qui autorise la sélection de fichiers de type .gif, .jpeg et .bmp.  Si un fichier de ce type est sélectionné dans la boîte de dialogue Enregistrer le fichier, l'image du bouton est enregistrée.  
  
    > [!IMPORTANT]
    >  Pour obtenir ou définir la propriété <xref:System.Windows.Forms.FileDialog.FileName%2A>, votre assembly doit disposer d'un niveau de privilège accordé par la classe <xref:System.Security.Permissions.FileIOPermission?displayProperty=fullName>.  Si vous exécutez le programme dans un contexte partiellement fiable, le processus peut lever une exception en raison de privilèges insuffisants.  Pour plus d'informations, consultez [Notions fondamentales de la sécurité d'accès du code](../../../../docs/framework/misc/code-access-security-basics.md).  
  
     Cet exemple suppose que votre formulaire contient un contrôle <xref:System.Windows.Forms.Button> dont la propriété <xref:System.Windows.Forms.ButtonBase.Image%2A> a pour valeur un fichier de type .gif, .jpeg ou .bmp.  
  
    > [!NOTE]
    >  La propriété <xref:System.Windows.Forms.FileDialog.FilterIndex%2A> \(qui, en raison de l'héritage, fait partie de la classe <xref:System.Windows.Forms.SaveFileDialog>\) de la classe <xref:System.Windows.Forms.FileDialog> utilise un index de base un.  Ce point est important si vous écrivez du code pour enregistrer des données dans un format spécifique \(par exemple, l'enregistrement d'un fichier en texte brut par rapport au format binaire\).  Cette propriété est mise en évidence dans l'exemple suivant :  
  
    ```vb  
    Private Sub Button2_Click(ByVal sender As System.Object, _  
    ByVal e As System.EventArgs) Handles Button2.Click  
       ' Displays a SaveFileDialog so the user can save the Image  
       ' assigned to Button2.  
       Dim saveFileDialog1 As New SaveFileDialog()  
       saveFileDialog1.Filter = "JPeg Image|*.jpg|Bitmap Image|*.bmp|Gif Image|*.gif"  
       saveFileDialog1.Title = "Save an Image File"  
       saveFileDialog1.ShowDialog()  
  
       ' If the file name is not an empty string open it for saving.  
       If saveFileDialog1.FileName <> "" Then  
          ' Saves the Image via a FileStream created by the OpenFile method.  
          Dim fs As System.IO.FileStream = Ctype _  
             (saveFileDialog1.OpenFile(), System.IO.FileStream)  
          ' Saves the Image in the appropriate ImageFormat based upon the  
          ' file type selected in the dialog box.  
          ' NOTE that the FilterIndex property is one-based.  
          Select Case saveFileDialog1.FilterIndex  
             Case 1  
                Me.button2.Image.Save(fs, _  
                   System.Drawing.Imaging.ImageFormat.Jpeg)  
  
             Case 2  
                Me.button2.Image.Save(fs, _  
                   System.Drawing.Imaging.ImageFormat.Bmp)  
  
             Case 3  
                Me.button2.Image.Save(fs, _  
                   System.Drawing.Imaging.ImageFormat.Gif)  
           End Select  
  
           fs.Close()  
        End If  
    End Sub  
  
    ```  
  
    ```csharp  
    private void button2_Click(object sender, System.EventArgs e)  
    {  
       // Displays a SaveFileDialog so the user can save the Image  
       // assigned to Button2.  
       SaveFileDialog saveFileDialog1 = new SaveFileDialog();  
       saveFileDialog1.Filter = "JPeg Image|*.jpg|Bitmap Image|*.bmp|Gif Image|*.gif";  
       saveFileDialog1.Title = "Save an Image File";  
       saveFileDialog1.ShowDialog();  
  
       // If the file name is not an empty string open it for saving.  
       if(saveFileDialog1.FileName != "")  
       {  
          // Saves the Image via a FileStream created by the OpenFile method.  
          System.IO.FileStream fs =   
             (System.IO.FileStream)saveFileDialog1.OpenFile();  
          // Saves the Image in the appropriate ImageFormat based upon the  
          // File type selected in the dialog box.  
          // NOTE that the FilterIndex property is one-based.  
          switch(saveFileDialog1.FilterIndex)  
          {  
             case 1 :   
             this.button2.Image.Save(fs,   
                System.Drawing.Imaging.ImageFormat.Jpeg);  
             break;  
  
             case 2 :   
             this.button2.Image.Save(fs,   
                System.Drawing.Imaging.ImageFormat.Bmp);  
             break;  
  
             case 3 :   
             this.button2.Image.Save(fs,   
                System.Drawing.Imaging.ImageFormat.Gif);  
             break;  
          }  
  
       fs.Close();  
       }  
    }  
  
    ```  
  
    ```cpp  
    private:  
       System::Void button2_Click(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          // Displays a SaveFileDialog so the user can save the Image  
          // assigned to Button2.  
          SaveFileDialog ^ saveFileDialog1 = new SaveFileDialog();  
          saveFileDialog1->Filter =   
             "JPeg Image|*.jpg|Bitmap Image|*.bmp|Gif Image|*.gif";  
          saveFileDialog1->Title = "Save an Image File";  
          saveFileDialog1->ShowDialog();  
          // If the file name is not an empty string, open it for saving.  
          if(saveFileDialog1->FileName != "")  
          {  
             // Saves the Image through a FileStream created by  
             // the OpenFile method.  
             System::IO::FileStream ^ fs =   
                safe_cast<System::IO::FileStream*>(  
                saveFileDialog1->OpenFile());  
             // Saves the Image in the appropriate ImageFormat based on  
             // the file type selected in the dialog box.  
             // Note that the FilterIndex property is one based.  
             switch(saveFileDialog1->FilterIndex)  
             {  
                case 1 :  
                   this->button2->Image->Save(fs,  
                      System::Drawing::Imaging::ImageFormat::Jpeg);  
                   break;  
                case 2 :  
                   this->button2->Image->Save(fs,   
                      System::Drawing::Imaging::ImageFormat::Bmp);  
                   break;  
                case 3 :  
                   this->button2->Image->Save(fs,   
                      System::Drawing::Imaging::ImageFormat::Gif);  
                   break;  
             }  
          fs->Close();  
          }  
       }  
    ```  
  
     \([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] et [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]\) Placez le code suivant dans le constructeur du formulaire pour inscrire le gestionnaire d'événements.  
  
    ```csharp  
    this.button2.Click += new System.EventHandler(this.button2_Click);  
  
    ```  
  
    ```cpp  
    this->button2->Click += gcnew  
       System::EventHandler(this, &Form1::button2_Click);  
    ```  
  
     Pour plus d'informations sur l'écriture de flux de fichiers, consultez [FileStream.BeginWrite, méthode](frlrfSystemIOFileStreamClassBeginWriteTopic) et [FileStream.Write, méthode](https://msdn.microsoft.com/en-us/library/system.io.filestream.write.aspx).  
  
    > [!NOTE]
    >  Certains contrôles, tels que <xref:System.Windows.Forms.RichTextBox>, peuvent enregistrer des fichiers.  Pour plus d'informations, consultez la section "SaveFileDialog Composant" \(Composant SaveFileDialog\) de l'article technique [Essential Code for Windows Forms Dialog Boxes](http://go.microsoft.com/fwlink/?LinkID=102575) \(Code essentiel pour les boîtes de dialogue de Windows Forms\) dans MSDN Online Library.  
  
## Voir aussi  
 <xref:System.Windows.Forms.SaveFileDialog>   
 [SaveFileDialog, composant](../../../../docs/framework/winforms/controls/savefiledialog-component-windows-forms.md)