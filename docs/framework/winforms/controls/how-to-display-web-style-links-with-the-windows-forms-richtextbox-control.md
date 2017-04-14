---
title: "Comment&#160;: afficher des liens de style Web avec le contr&#244;le RichTextBox Windows Forms | Microsoft Docs"
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
  - "exemples (Windows Forms), zones de texte"
  - "RichTextBox (contrôle Windows Forms), lier à des pages Web"
  - "zones de texte, afficher les liens Web"
ms.assetid: 95089a37-a202-4f7a-94ee-6ee312908851
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# Comment&#160;: afficher des liens de style Web avec le contr&#244;le RichTextBox Windows Forms
Le contrôle <xref:System.Windows.Forms.RichTextBox> Windows Forms peut afficher les liens Web en utilisant des couleurs et le soulignement.  Vous pouvez écrire le code qui ouvre une fenêtre de navigateur dans laquelle s'affiche le site Web spécifié dans le texte du lien lorsque l'utilisateur clique sur ce lien.  
  
### Pour créer un lien vers une page Web avec le contrôle RichTextBox  
  
1.  Affectez à la propriété <xref:System.Windows.Forms.RichTextBox.Text%2A> une chaîne contenant une URL valide \(par exemple, « http:\/\/www.microsoft.com\/france »\).  
  
2.  Assurez\-vous que la propriété <xref:System.Windows.Forms.RichTextBox.DetectUrls%2A> a la valeur `true` \(valeur par défaut\).  
  
3.  Créez une nouvelle instance globale de l'objet <xref:System.Diagnostics.Process>.  
  
4.  Écrivez un gestionnaire d'événements pour l'événement <xref:System.Windows.Forms.RichTextBox.LinkClicked> qui envoie au navigateur le texte souhaité.  
  
     Dans l'exemple ci\-dessous, l'événement <xref:System.Windows.Forms.RichTextBox.LinkClicked> ouvre une instance d'Internet Explorer avec l'URL spécifiée dans la propriété <xref:System.Windows.Forms.RichTextBox.Text%2A> du contrôle <xref:System.Windows.Forms.RichTextBox>.  Cet exemple illustre un formulaire avec un contrôle <xref:System.Windows.Forms.RichTextBox>.  
  
    > [!IMPORTANT]
    >  Lors de l'appel à la méthode <xref:System.Diagnostics.Process.Start%2A?displayProperty=fullName>, vous rencontrez une exception <xref:System.Security.SecurityException> si vous exécutez le code dans un contexte de confiance partielle en raison de privilèges insuffisants.  Pour plus d'informations, consultez [Notions fondamentales de la sécurité d'accès du code](../../../../docs/framework/misc/code-access-security-basics.md).  
  
    ```vb  
    Public p As New System.Diagnostics.Process  
    Private Sub RichTextBox1_LinkClicked _  
       (ByVal sender As Object, ByVal e As _  
       System.Windows.Forms.LinkClickedEventArgs) _  
       Handles RichTextBox1.LinkClicked  
          ' Call Process.Start method to open a browser  
          ' with link text as URL.  
          p = System.Diagnostics.Process.Start("IExplore.exe", e.LinkText)  
    End Sub  
  
    ```  
  
    ```csharp  
    public System.Diagnostics.Process p = new System.Diagnostics.Process();  
  
    private void richTextBox1_LinkClicked(object sender,   
    System.Windows.Forms.LinkClickedEventArgs e)  
    {  
       // Call Process.Start method to open a browser  
       // with link text as URL.  
       p = System.Diagnostics.Process.Start("IExplore.exe", e.LinkText);  
    }  
  
    ```  
  
    ```cpp  
    public:  
       System::Diagnostics::Process ^ p;  
  
    private:  
       void richTextBox1_LinkClicked(System::Object ^  sender,  
          System::Windows::Forms::LinkClickedEventArgs ^  e)  
       {  
          // Call Process.Start method to open a browser  
          // with link text as URL.  
          p = System::Diagnostics::Process::Start("IExplore.exe",  
             e->LinkText);  
       }  
    ```  
  
     \([!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]\) Vous devez initialiser le processus `p` en incluant l'instruction suivante dans le constructeur de votre formulaire :  
  
    ```cpp  
    p = gcnew System::Diagnostics::Process();  
    ```  
  
     \([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]\) Placez le code suivant dans le constructeur du formulaire pour inscrire le gestionnaire d'événements.  
  
    ```csharp  
    this.richTextBox1.LinkClicked += new   
       System.Windows.Forms.LinkClickedEventHandler  
       (this.richTextBox1_LinkClicked);  
  
    ```  
  
    ```cpp  
    this->richTextBox1->LinkClicked += gcnew  
       System::Windows::Forms::LinkClickedEventHandler  
       (this, &Form1::richTextBox1_LinkClicked);  
    ```  
  
     Il est important d'arrêter immédiatement le processus que vous avez créé dès lors que vous avez fini de l'utiliser.  S'agissant du code présenté plus haut, le code permettant d'arrêter le processus peut ressembler à ce qui suit :  
  
    ```vb  
    Public Sub StopWebProcess()  
       p.Kill()  
    End Sub  
  
    ```  
  
    ```csharp  
    public void StopWebProcess()  
    {  
       p.Kill();  
    }  
  
    ```  
  
    ```cpp  
    public: void StopWebProcess()  
    {  
       p->Kill();  
    }  
    ```  
  
## Voir aussi  
 <xref:System.Windows.Forms.RichTextBox.DetectUrls%2A>   
 <xref:System.Windows.Forms.RichTextBox.LinkClicked>   
 <xref:System.Windows.Forms.RichTextBox>   
 [RichTextBox, contrôle](../../../../docs/framework/winforms/controls/richtextbox-control-windows-forms.md)   
 [Contrôles à utiliser dans les Windows Forms](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)