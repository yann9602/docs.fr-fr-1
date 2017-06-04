---
title: "Comment&#160;: ouvrir des fichiers &#224; l&#39;aide du composant OpenFileDialog | Microsoft Docs"
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
  - "fichiers, ouvrir avec le composant OpenFileDialog"
  - "OpenFile (méthode)"
  - "OpenFile (méthode), OpenFileDialog (composant)"
  - "OpenFileDialog (composant), ouvrir des fichiers"
ms.assetid: 9d88367a-cc21-4ffd-be74-89fd63767d35
caps.latest.revision: 21
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 18
---
# Comment&#160;: ouvrir des fichiers &#224; l&#39;aide du composant OpenFileDialog
Le composant <xref:System.Windows.Forms.OpenFileDialog> permet aux utilisateurs de parcourir les dossiers de leur ordinateur ou de n'importe quel ordinateur du réseau et de sélectionner un ou plusieurs fichiers à ouvrir.  La boîte de dialogue retourne le chemin d'accès et le nom du fichier sélectionné dans la boîte de dialogue.  
  
 Une fois le fichier à ouvrir sélectionné, son ouverture peut être réalisée de deux manières.  Si vous préférez travailler avec des flux de fichiers, vous pouvez créer une instance de la classe <xref:System.IO.StreamReader>.  Sinon, vous pouvez utiliser la méthode <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> pour ouvrir le fichier sélectionné.  
  
 Le premier exemple ci\-dessous implique une vérification d'autorisation <xref:System.Security.Permissions.FileIOPermission> \(comme décrit dans la « Remarque sur la sécurité » ci\-dessous\), mais vous donne accès au nom du fichier.  Vous pouvez utiliser cette technique à partir de l'ordinateur local, de l'intranet et de zones Internet.  La seconde méthode effectue également une vérification d'autorisation <xref:System.Security.Permissions.FileIOPermission>, mais elle est mieux adaptée aux applications d'intranet ou de zones Internet.  
  
### Pour ouvrir un fichier en tant que flux à l'aide du composant OpenFileDialog  
  
1.  Affichez la boîte de dialogue **Ouvrir un fichier** et appelez une méthode pour ouvrir le fichier sélectionné.  
  
     Vous pouvez utiliser la méthode <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> pour afficher la boîte de dialogue Ouvrir un fichier, puis utiliser une instance de la classe <xref:System.IO.StreamReader> pour ouvrir le fichier.  
  
     L'exemple ci\-dessous utilise le gestionnaire d'événements <xref:System.Windows.Forms.Control.Click> du contrôle <xref:System.Windows.Forms.Button> pour ouvrir une instance du composant <xref:System.Windows.Forms.OpenFileDialog>.  Lorsque l'utilisateur choisit un fichier et clique sur **OK**, le fichier sélectionné dans la boîte de dialogue s'ouvre.  Dans ce cas, le contenu s'affiche dans un message, pour indiquer que le flux de fichier a été lu.  
  
    > [!IMPORTANT]
    >  Pour obtenir ou définir la propriété <xref:System.Windows.Forms.FileDialog.FileName%2A>, votre assembly doit disposer d'un niveau de privilège accordé par la classe <xref:System.Security.Permissions.FileIOPermission?displayProperty=fullName>.  Si vous exécutez le programme dans un contexte partiellement fiable, le processus peut lever une exception en raison de privilèges insuffisants.  Pour plus d'informations, consultez [Notions fondamentales de la sécurité d'accès du code](../../../../docs/framework/misc/code-access-security-basics.md).  
  
     Cet exemple suppose que votre formulaire contient un contrôle <xref:System.Windows.Forms.Button> et un composant <xref:System.Windows.Forms.OpenFileDialog>.  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, _  
       ByVal e As System.EventArgs) Handles Button1.Click  
       If OpenFileDialog1.ShowDialog() = System.Windows.Forms.DialogResult.OK Then  
         Dim sr As New System.IO.StreamReader(OpenFileDialog1.FileName)  
         MessageBox.Show(sr.ReadToEnd)  
         sr.Close()  
       End If  
    End Sub  
  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       if(openFileDialog1.ShowDialog() == System.Windows.Forms.DialogResult.OK)  
       {  
          System.IO.StreamReader sr = new   
             System.IO.StreamReader(openFileDialog1.FileName);  
          MessageBox.Show(sr.ReadToEnd());  
          sr.Close();  
       }  
    }  
  
    ```  
  
    ```cpp  
    private:  
       void button1_Click(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          if(openFileDialog1->ShowDialog() == System::Windows::Forms::DialogResult::OK)  
          {  
             System::IO::StreamReader ^ sr = gcnew  
                System::IO::StreamReader(openFileDialog1->FileName);  
             MessageBox::Show(sr->ReadToEnd());  
             sr->Close();  
          }  
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
  
    > [!NOTE]
    >  Pour plus d'informations sur la lecture à partir de flux de fichiers, consultez [FileStream.BeginRead, méthode](frlrfSystemIOFileStreamClassBeginReadTopic) et [FileStream.Read, méthode](https://msdn.microsoft.com/en-us/library/system.io.filestream.read.aspx).  
  
### Pour ouvrir un fichier en tant que tel à l'aide du composant OpenFileDialog  
  
1.  Utilisez la méthode <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> pour afficher la boîte de dialogue et la méthode <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> pour ouvrir le fichier.  
  
     La méthode <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> du composant <xref:System.Windows.Forms.OpenFileDialog> retourne les octets qui composent le fichier.  Ces octets vous fournissent un flux à partir duquel vous pouvez lire.  Dans l'exemple ci\-dessous, un composant <xref:System.Windows.Forms.OpenFileDialog> est instancié avec un filtre « curseur », qui permet à l'utilisateur de choisir uniquement des fichiers portant l'extension `.cur`.  S'il sélectionne un fichier `.cur` , le curseur du formulaire est réglé sur le curseur sélectionné.  
  
    > [!IMPORTANT]
    >  Pour appeler la méthode <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A>, votre assembly doit disposer d'un niveau de privilège accordé par la classe <xref:System.Security.Permissions.FileIOPermission?displayProperty=fullName>.  Si vous exécutez le programme dans un contexte partiellement fiable, le processus peut lever une exception en raison de privilèges insuffisants.  Pour plus d'informations, consultez [Notions fondamentales de la sécurité d'accès du code](../../../../docs/framework/misc/code-access-security-basics.md).  
  
     Cet exemple suppose que votre formulaire contient un contrôle <xref:System.Windows.Forms.Button>.  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, _  
       ByVal e As System.EventArgs) Handles Button1.Click  
       ' Displays an OpenFileDialog so the user can select a Cursor.  
       Dim openFileDialog1 As New OpenFileDialog()  
       openFileDialog1.Filter = "Cursor Files|*.cur"  
       openFileDialog1.Title = "Select a Cursor File"  
  
       ' Show the Dialog.  
       ' If the user clicked OK in the dialog and   
       ' a .CUR file was selected, open it.  
       If openFileDialog1.ShowDialog() = System.Windows.Forms.DialogResult.OK Then  
         ' Assign the cursor in the Stream to the Form's Cursor property.  
         Me.Cursor = New Cursor(openFileDialog1.OpenFile())  
       End If  
    End Sub  
  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       // Displays an OpenFileDialog so the user can select a Cursor.  
       OpenFileDialog openFileDialog1 = new OpenFileDialog();  
       openFileDialog1.Filter = "Cursor Files|*.cur";  
       openFileDialog1.Title = "Select a Cursor File";  
  
       // Show the Dialog.  
       // If the user clicked OK in the dialog and  
       // a .CUR file was selected, open it.  
        if (openFileDialog1.ShowDialog() == System.Windows.Forms.DialogResult.OK)  
       {  
          // Assign the cursor in the Stream to the Form's Cursor property.  
          this.Cursor = new Cursor(openFileDialog1.OpenFile());  
       }  
    }  
  
    ```  
  
    ```cpp  
    private:  
       void button1_Click(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          // Displays an OpenFileDialog so the user can select a Cursor.  
          OpenFileDialog ^ openFileDialog1 = new OpenFileDialog();  
          openFileDialog1->Filter = "Cursor Files|*.cur";  
          openFileDialog1->Title = "Select a Cursor File";  
  
          // Show the Dialog.  
          // If the user clicked OK in the dialog and  
          // a .CUR file was selected, open it.  
          if (openFileDialog1->ShowDialog() == System::Windows::Forms::DialogResult::OK)  
          {  
             // Assign the cursor in the Stream to  
             // the Form's Cursor property.  
             this->Cursor = gcnew  
                System::Windows::Forms::Cursor(  
                openFileDialog1->OpenFile());  
          }  
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
 <xref:System.Windows.Forms.OpenFileDialog>   
 [OpenFileDialog, composant](../../../../docs/framework/winforms/controls/openfiledialog-component-windows-forms.md)