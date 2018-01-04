---
title: "Guide pratique pour ouvrir des fichiers à l'aide du composant OpenFileDialog"
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
- OpenFileDialog component [Windows Forms], opening files
- OpenFile method [Windows Forms], OpenFileDialog component
- files [Windows Forms], opening with OpenFileDialog component
ms.assetid: 9d88367a-cc21-4ffd-be74-89fd63767d35
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fabe176ade1ae94a20100162ab7ab6fadfb2999f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-open-files-using-the-openfiledialog-component"></a>Guide pratique pour ouvrir des fichiers à l'aide du composant OpenFileDialog
Le <xref:System.Windows.Forms.OpenFileDialog> composant permet aux utilisateurs de parcourir les dossiers de leur ordinateur ou de n’importe quel ordinateur sur le réseau et sélectionner un ou plusieurs fichiers à ouvrir. La boîte de dialogue retourne le chemin et le nom du fichier que l’utilisateur a sélectionné dans la boîte de dialogue.  
  
 Une fois que l’utilisateur a sélectionné le fichier à ouvrir, vous avez le choix entre deux approches du mécanisme d’ouverture. Si vous préférez travailler avec des flux de fichier, vous pouvez créer une instance de la <xref:System.IO.StreamReader> classe. Vous pouvez également utiliser le <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> méthode pour ouvrir le fichier sélectionné.  
  
 Le premier exemple ci-dessous implique une <xref:System.Security.Permissions.FileIOPermission> vérification d’autorisation (comme décrit dans la « Note de sécurité » ci-dessous), mais vous donne accès au nom de fichier. Vous pouvez utiliser cette technique dans les zones Ordinateur Local, Intranet et Internet. La seconde méthode effectue également une <xref:System.Security.Permissions.FileIOPermission> vérification d’autorisation, mais elle est mieux adapté aux applications dans les zones Intranet ou Internet.  
  
### <a name="to-open-a-file-as-a-stream-using-the-openfiledialog-component"></a>Pour ouvrir des fichiers à l’aide du composant OpenFileDialog  
  
1.  Affichez la boîte de dialogue **Ouvrir un fichier** et appelez une méthode pour ouvrir le fichier sélectionné par l’utilisateur.  
  
     Une approche consiste à utiliser le <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> méthode pour afficher la boîte de dialogue Ouvrir un fichier et utiliser une instance de la <xref:System.IO.StreamReader> pour ouvrir le fichier de classe.  
  
     L’exemple ci-dessous utilise le <xref:System.Windows.Forms.Button> du contrôle <xref:System.Windows.Forms.Control.Click> Gestionnaire d’événements pour ouvrir une instance de la <xref:System.Windows.Forms.OpenFileDialog> composant. Quand un fichier est sélectionné et que l’utilisateur clique sur **OK**, le fichier sélectionné dans la boîte de dialogue s’ouvre. Dans ce cas, le contenu est affiché dans une boîte de message, uniquement pour montrer que le flux de fichier a été lu.  
  
    > [!IMPORTANT]
    >  Pour obtenir ou définir le <xref:System.Windows.Forms.FileDialog.FileName%2A> propriété, votre assembly requiert un niveau de privilège accordé par la <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> classe. Si vous l’exécutez dans un contexte de confiance partielle, le processus peut lever une exception en raison de privilèges insuffisants. Pour plus d’informations, consultez [Notions fondamentales de la sécurité d’accès du code](../../../../docs/framework/misc/code-access-security-basics.md).  
  
     L’exemple suppose que votre formulaire contient un <xref:System.Windows.Forms.Button> contrôle et une <xref:System.Windows.Forms.OpenFileDialog> composant.  
  
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
  
     ([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] et [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Placez le code suivant dans le constructeur du formulaire pour inscrire le gestionnaire d'événements.  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click += gcnew  
       System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
    > [!NOTE]
    >  Pour plus d’informations sur la lecture à partir de flux de fichiers, consultez <xref:System.IO.FileStream.BeginRead%2A> et <xref:System.IO.FileStream.Read%2A>.  
  
### <a name="to-open-a-file-as-a-file-using-the-openfiledialog-component"></a>Pour ouvrir un fichier en tant que fichier à l’aide du composant OpenFileDialog  
  
1.  Utilisez le <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> méthode pour afficher la boîte de dialogue et les <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> méthode pour ouvrir le fichier.  
  
     Le <xref:System.Windows.Forms.OpenFileDialog> du composant <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> méthode retourne les octets qui composent le fichier. Ces octets vous donnent un flux que vous lisez. Dans l’exemple ci-dessous, un <xref:System.Windows.Forms.OpenFileDialog> est instancié avec un filtre « curseur », qui permet à l’utilisateur de choisir uniquement des fichiers avec l’extension de nom de fichier`.cur`. Si un fichier `.cur` est sélectionné, le curseur du formulaire est défini sur le curseur sélectionné.  
  
    > [!IMPORTANT]
    >  Pour appeler le <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> (méthode), votre assembly requiert un niveau de privilège accordé par la <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> classe. Si vous l’exécutez dans un contexte de confiance partielle, le processus peut lever une exception en raison de privilèges insuffisants. Pour plus d’informations, consultez [Notions fondamentales de la sécurité d’accès du code](../../../../docs/framework/misc/code-access-security-basics.md).  
  
     L’exemple suppose que votre formulaire contient un <xref:System.Windows.Forms.Button> contrôle.  
  
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
  
     ([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] et [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Placez le code suivant dans le constructeur du formulaire pour inscrire le gestionnaire d'événements.  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click += gcnew  
       System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.OpenFileDialog>  
 [OpenFileDialog, composant](../../../../docs/framework/winforms/controls/openfiledialog-component-windows-forms.md)
