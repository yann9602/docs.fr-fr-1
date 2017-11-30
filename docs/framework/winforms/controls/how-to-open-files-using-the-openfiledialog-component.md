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
ms.openlocfilehash: 52726a770e33bec4b5ec9b24f33deb44ed6379b5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-open-files-using-the-openfiledialog-component"></a><span data-ttu-id="3b244-102">Guide pratique pour ouvrir des fichiers à l'aide du composant OpenFileDialog</span><span class="sxs-lookup"><span data-stu-id="3b244-102">How to: Open Files Using the OpenFileDialog Component</span></span>
<span data-ttu-id="3b244-103">Le <xref:System.Windows.Forms.OpenFileDialog> composant permet aux utilisateurs de parcourir les dossiers de leur ordinateur ou de n’importe quel ordinateur sur le réseau et sélectionner un ou plusieurs fichiers à ouvrir.</span><span class="sxs-lookup"><span data-stu-id="3b244-103">The <xref:System.Windows.Forms.OpenFileDialog> component allows users to browse the folders of their computer or any computer on the network and select one or more files to open.</span></span> <span data-ttu-id="3b244-104">La boîte de dialogue retourne le chemin et le nom du fichier que l’utilisateur a sélectionné dans la boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="3b244-104">The dialog box returns the path and name of the file the user selected in the dialog box.</span></span>  
  
 <span data-ttu-id="3b244-105">Une fois que l’utilisateur a sélectionné le fichier à ouvrir, vous avez le choix entre deux approches du mécanisme d’ouverture.</span><span class="sxs-lookup"><span data-stu-id="3b244-105">Once the user has selected the file to be opened, there are two approaches to the mechanism of opening the file.</span></span> <span data-ttu-id="3b244-106">Si vous préférez travailler avec des flux de fichier, vous pouvez créer une instance de la <xref:System.IO.StreamReader> classe.</span><span class="sxs-lookup"><span data-stu-id="3b244-106">If you prefer to work with file streams, you can create an instance of the <xref:System.IO.StreamReader> class.</span></span> <span data-ttu-id="3b244-107">Vous pouvez également utiliser le <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> méthode pour ouvrir le fichier sélectionné.</span><span class="sxs-lookup"><span data-stu-id="3b244-107">Alternately, you can use the <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> method to open the selected file.</span></span>  
  
 <span data-ttu-id="3b244-108">Le premier exemple ci-dessous implique une <xref:System.Security.Permissions.FileIOPermission> vérification d’autorisation (comme décrit dans la « Note de sécurité » ci-dessous), mais vous donne accès au nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="3b244-108">The first example below involves a <xref:System.Security.Permissions.FileIOPermission> permission check (as described in the "Security Note" below), but gives you access to the filename.</span></span> <span data-ttu-id="3b244-109">Vous pouvez utiliser cette technique dans les zones Ordinateur Local, Intranet et Internet.</span><span class="sxs-lookup"><span data-stu-id="3b244-109">You can use this technique from the Local Machine, Intranet, and Internet zones.</span></span> <span data-ttu-id="3b244-110">La seconde méthode effectue également une <xref:System.Security.Permissions.FileIOPermission> vérification d’autorisation, mais elle est mieux adapté aux applications dans les zones Intranet ou Internet.</span><span class="sxs-lookup"><span data-stu-id="3b244-110">The second method also does a <xref:System.Security.Permissions.FileIOPermission> permission check, but is better suited for applications in the Intranet or Internet zones.</span></span>  
  
### <a name="to-open-a-file-as-a-stream-using-the-openfiledialog-component"></a><span data-ttu-id="3b244-111">Pour ouvrir des fichiers à l’aide du composant OpenFileDialog</span><span class="sxs-lookup"><span data-stu-id="3b244-111">To open a file as a stream using the OpenFileDialog component</span></span>  
  
1.  <span data-ttu-id="3b244-112">Affichez la boîte de dialogue **Ouvrir un fichier** et appelez une méthode pour ouvrir le fichier sélectionné par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="3b244-112">Display the **Open File** dialog box and call a method to open the file selected by the user.</span></span>  
  
     <span data-ttu-id="3b244-113">Une approche consiste à utiliser le <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> méthode pour afficher la boîte de dialogue Ouvrir un fichier et utiliser une instance de la <xref:System.IO.StreamReader> pour ouvrir le fichier de classe.</span><span class="sxs-lookup"><span data-stu-id="3b244-113">One approach is to use the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method to display the Open File dialog box, and use an instance of the <xref:System.IO.StreamReader> class to open the file.</span></span>  
  
     <span data-ttu-id="3b244-114">L’exemple ci-dessous utilise le <xref:System.Windows.Forms.Button> du contrôle <xref:System.Windows.Forms.Control.Click> Gestionnaire d’événements pour ouvrir une instance de la <xref:System.Windows.Forms.OpenFileDialog> composant.</span><span class="sxs-lookup"><span data-stu-id="3b244-114">The example below uses the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Click> event handler to open an instance of the <xref:System.Windows.Forms.OpenFileDialog> component.</span></span> <span data-ttu-id="3b244-115">Quand un fichier est sélectionné et que l’utilisateur clique sur **OK**, le fichier sélectionné dans la boîte de dialogue s’ouvre.</span><span class="sxs-lookup"><span data-stu-id="3b244-115">When a file is chosen and the user clicks **OK**, the file selected in the dialog box opens.</span></span> <span data-ttu-id="3b244-116">Dans ce cas, le contenu est affiché dans une boîte de message, uniquement pour montrer que le flux de fichier a été lu.</span><span class="sxs-lookup"><span data-stu-id="3b244-116">In this case, the contents are displayed in a message box, just to show that the file stream has been read.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="3b244-117">Pour obtenir ou définir le <xref:System.Windows.Forms.FileDialog.FileName%2A> propriété, votre assembly requiert un niveau de privilège accordé par la <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> classe.</span><span class="sxs-lookup"><span data-stu-id="3b244-117">To get or set the <xref:System.Windows.Forms.FileDialog.FileName%2A> property, your assembly requires a privilege level granted by the <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="3b244-118">Si vous l’exécutez dans un contexte de confiance partielle, le processus peut lever une exception en raison de privilèges insuffisants.</span><span class="sxs-lookup"><span data-stu-id="3b244-118">If you are running in a partial-trust context, the process might throw an exception due to insufficient privileges.</span></span> <span data-ttu-id="3b244-119">Pour plus d’informations, consultez [Notions fondamentales de la sécurité d’accès du code](../../../../docs/framework/misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="3b244-119">For more information, see [Code Access Security Basics](../../../../docs/framework/misc/code-access-security-basics.md).</span></span>  
  
     <span data-ttu-id="3b244-120">L’exemple suppose que votre formulaire contient un <xref:System.Windows.Forms.Button> contrôle et une <xref:System.Windows.Forms.OpenFileDialog> composant.</span><span class="sxs-lookup"><span data-stu-id="3b244-120">The example assumes your form has a <xref:System.Windows.Forms.Button> control and an <xref:System.Windows.Forms.OpenFileDialog> component.</span></span>  
  
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
  
     <span data-ttu-id="3b244-121">([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] et [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Placez le code suivant dans le constructeur du formulaire pour inscrire le gestionnaire d'événements.</span><span class="sxs-lookup"><span data-stu-id="3b244-121">([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] and [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click += gcnew  
       System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="3b244-122">Pour plus d’informations sur la lecture à partir de flux de fichiers, consultez <xref:System.IO.FileStream.BeginRead%2A> et <xref:System.IO.FileStream.Read%2A>.</span><span class="sxs-lookup"><span data-stu-id="3b244-122">For more information about reading from file streams, see <xref:System.IO.FileStream.BeginRead%2A> and <xref:System.IO.FileStream.Read%2A>.</span></span>  
  
### <a name="to-open-a-file-as-a-file-using-the-openfiledialog-component"></a><span data-ttu-id="3b244-123">Pour ouvrir un fichier en tant que fichier à l’aide du composant OpenFileDialog</span><span class="sxs-lookup"><span data-stu-id="3b244-123">To open a file as a file using the OpenFileDialog component</span></span>  
  
1.  <span data-ttu-id="3b244-124">Utilisez le <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> méthode pour afficher la boîte de dialogue et les <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> méthode pour ouvrir le fichier.</span><span class="sxs-lookup"><span data-stu-id="3b244-124">Use the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method to display the dialog box and the <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> method to open the file.</span></span>  
  
     <span data-ttu-id="3b244-125">Le <xref:System.Windows.Forms.OpenFileDialog> du composant <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> méthode retourne les octets qui composent le fichier.</span><span class="sxs-lookup"><span data-stu-id="3b244-125">The <xref:System.Windows.Forms.OpenFileDialog> component's <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> method returns the bytes that compose the file.</span></span> <span data-ttu-id="3b244-126">Ces octets vous donnent un flux que vous lisez.</span><span class="sxs-lookup"><span data-stu-id="3b244-126">These bytes give you a stream to read from.</span></span> <span data-ttu-id="3b244-127">Dans l’exemple ci-dessous, un <xref:System.Windows.Forms.OpenFileDialog> est instancié avec un filtre « curseur », qui permet à l’utilisateur de choisir uniquement des fichiers avec l’extension de nom de fichier`.cur`.</span><span class="sxs-lookup"><span data-stu-id="3b244-127">In the example below, an <xref:System.Windows.Forms.OpenFileDialog> component is instantiated with a "cursor" filter on it, allowing the user to choose only files with the file name extension`.cur`.</span></span> <span data-ttu-id="3b244-128">Si un fichier `.cur` est sélectionné, le curseur du formulaire est défini sur le curseur sélectionné.</span><span class="sxs-lookup"><span data-stu-id="3b244-128">If a`.cur` file is chosen, the form's cursor is set to the selected cursor.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="3b244-129">Pour appeler le <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> (méthode), votre assembly requiert un niveau de privilège accordé par la <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> classe.</span><span class="sxs-lookup"><span data-stu-id="3b244-129">To call the <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> method, your assembly requires a privilege level granted by the <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="3b244-130">Si vous l’exécutez dans un contexte de confiance partielle, le processus peut lever une exception en raison de privilèges insuffisants.</span><span class="sxs-lookup"><span data-stu-id="3b244-130">If you are running in a partial-trust context, the process might throw an exception due to insufficient privileges.</span></span> <span data-ttu-id="3b244-131">Pour plus d’informations, consultez [Notions fondamentales de la sécurité d’accès du code](../../../../docs/framework/misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="3b244-131">For more information, see [Code Access Security Basics](../../../../docs/framework/misc/code-access-security-basics.md).</span></span>  
  
     <span data-ttu-id="3b244-132">L’exemple suppose que votre formulaire contient un <xref:System.Windows.Forms.Button> contrôle.</span><span class="sxs-lookup"><span data-stu-id="3b244-132">The example assumes your form has a <xref:System.Windows.Forms.Button> control.</span></span>  
  
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
  
     <span data-ttu-id="3b244-133">([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] et [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Placez le code suivant dans le constructeur du formulaire pour inscrire le gestionnaire d'événements.</span><span class="sxs-lookup"><span data-stu-id="3b244-133">([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] and [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click += gcnew  
       System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="3b244-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3b244-134">See Also</span></span>  
 <xref:System.Windows.Forms.OpenFileDialog>  
 [<span data-ttu-id="3b244-135">OpenFileDialog, composant</span><span class="sxs-lookup"><span data-stu-id="3b244-135">OpenFileDialog Component</span></span>](../../../../docs/framework/winforms/controls/openfiledialog-component-windows-forms.md)
