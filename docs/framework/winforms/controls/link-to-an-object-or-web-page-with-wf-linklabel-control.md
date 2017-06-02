---
title: "Comment&#160;: cr&#233;er un lien vers un objet ou une page Web &#224; l&#39;aide du contr&#244;le LinkLabel Windows Forms | Microsoft Docs"
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
  - "exemples (Windows Forms), LinkLabel (contrôle)"
  - "lier, à d'autres formulaires"
  - "LinkLabel (contrôle Windows Forms), exemples"
  - "LinkLabel (contrôle Windows Forms), lier à un objet ou à une page Web"
  - "liens, à d'autres formulaires"
  - "contrôle de lien de page Web"
  - "Windows Forms, lier aux objets"
  - "Windows Forms, lier à des pages Web"
ms.assetid: 6c91c975-3cb7-4504-82f0-fc6255f8fb85
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# Comment&#160;: cr&#233;er un lien vers un objet ou une page Web &#224; l&#39;aide du contr&#244;le LinkLabel Windows Forms
Le contrôle <xref:System.Windows.Forms.LinkLabel> Windows Forms vous permet de créer des liens de style Web dans votre formulaire.  Vous pouvez modifier la couleur d'un lien sur lequel l'utilisateur a cliqué pour indiquer que ce lien a été visité.  Pour plus d'informations sur le changement de couleur, consultez [Comment : modifier l'apparence du contrôle LinkLabel Windows Forms](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-linklabel-control.md).  
  
## Liaison à un autre formulaire  
  
#### Pour créer un lien vers un autre formulaire à l'aide du contrôle LinkLabel  
  
1.  Affectez à la propriété <xref:System.Windows.Forms.LinkLabel.Text%2A> une légende appropriée.  
  
2.  Définissez la propriété <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> pour déterminer quelle partie de la légende doit être affichée en tant que lien.  La manière dont le lien est indiqué est déterminée par les propriétés d'apparence du contrôle LinkLabel.  La valeur de la propriété <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> est représentée par un objet <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> qui contient deux nombres correspondant respectivement à la position du caractère de départ et au nombre de caractères.  La propriété <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> peut être définie dans la fenêtre Propriétés ou dans le code d'une manière semblable aux éléments suivants :  
  
    ```vb  
    ' In this code example, the link area has been set to begin  
    ' at the first character and extend for eight characters.  
    ' You may need to modify this based on the text entered in Step 1.  
    LinkLabel1.LinkArea = New LinkArea(0, 8)  
  
    ```  
  
    ```csharp  
    // In this code example, the link area has been set to begin  
    // at the first character and extend for eight characters.  
    // You may need to modify this based on the text entered in Step 1.  
    linkLabel1.LinkArea = new LinkArea(0,8);  
  
    ```  
  
    ```cpp  
    // In this code example, the link area has been set to begin  
    // at the first character and extend for eight characters.  
    // You may need to modify this based on the text entered in Step 1.  
    linkLabel1->LinkArea = LinkArea(0,8);  
    ```  
  
3.  Dans le gestionnaire d'événements <xref:System.Windows.Forms.LinkLabel.LinkClicked>, appelez la méthode <xref:System.Windows.Forms.Form.Show%2A> pour ouvrir un autre formulaire dans le projet et attribuez à la propriété <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> la valeur `true`.  
  
    > [!NOTE]
    >  Une instance de la classe <xref:System.Windows.Forms.LinkLabelLinkClickedEventArgs> possède une référence au contrôle <xref:System.Windows.Forms.LinkLabel> sur lequel l'utilisateur a cliqué, de sorte qu'il n'est pas nécessaire d'effectuer un cast de l'objet `sender` .  
  
    ```vb  
    Protected Sub LinkLabel1_LinkClicked(ByVal Sender As System.Object, _  
       ByVal e As System.Windows.Forms.LinkLabelLinkClickedEventArgs) _  
       Handles LinkLabel1.LinkClicked  
       ' Show another form.  
       Dim f2 As New Form()  
       f2.Show  
       LinkLabel1.LinkVisited = True  
    End Sub  
  
    ```  
  
    ```csharp  
    protected void linkLabel1_LinkClicked(object sender, System. Windows.Forms.LinkLabelLinkClickedEventArgs e)  
    {  
       // Show another form.  
       Form f2 = new Form();  
       f2.Show();  
       linkLabel1.LinkVisited = true;  
    }  
  
    ```  
  
    ```cpp  
    private:  
       void linkLabel1_LinkClicked(System::Object ^  sender,  
          System::Windows::Forms::LinkLabelLinkClickedEventArgs ^  e)  
       {  
          // Show another form.  
          Form ^ f2 = new Form();  
          f2->Show();  
          linkLabel1->LinkVisited = true;  
       }  
    ```  
  
## Liaison à une page Web  
 Le contrôle <xref:System.Windows.Forms.LinkLabel> peut également être utilisé pour afficher une page Web dans le navigateur par défaut.  
  
#### Pour démarrer Internet Explorer et créer un lien vers une page Web à l'aide du contrôle LinkLabel  
  
1.  Affectez à la propriété <xref:System.Windows.Forms.LinkLabel.Text%2A> une légende appropriée.  
  
2.  Définissez la propriété <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> pour déterminer quelle partie de la légende doit être affichée en tant que lien.  
  
3.  Dans le gestionnaire d'événements <xref:System.Windows.Forms.LinkLabel.LinkClicked>, au milieu d'un bloc de traitement des exceptions, appelez une deuxième procédure qui affecte la valeur `true` à la propriété <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A>, puis utilisez la méthode <xref:System.Diagnostics.Process.Start%2A> pour démarrer le navigateur par défaut avec une URL.  Pour utiliser la méthode <xref:System.Diagnostics.Process.Start%2A>, vous devez ajouter une référence à l'espace de noms <xref:System.Diagnostics?displayProperty=fullName>.  
  
    > [!IMPORTANT]
    >  Si le code ci\-dessous est exécuté dans un environnement partiellement fiable \(par exemple un lecteur partagé\), le compilateur JIT échoue lors de l'appel à la méthode `VisitLink`.  L'instruction `System.Diagnostics.Process.Start`  entraîne une demande de lien qui échoue.  En interceptant l'exception lors de l'appel à la méthode `VisitLink`, le code ci\-dessous garantit que si le compilateur JIT échoue, l'erreur est gérée correctement.  
  
    ```vb  
    Private Sub LinkLabel1_LinkClicked(ByVal sender As System.Object, _  
       ByVal e As System.Windows.Forms.LinkLabelLinkClickedEventArgs) _  
       Handles LinkLabel1.LinkClicked  
       Try  
          VisitLink()  
       Catch ex As Exception  
          ' The error message  
          MessageBox.Show("Unable to open link that was clicked.")  
       End Try  
    End Sub  
  
    Sub VisitLink()  
       ' Change the color of the link text by setting LinkVisited   
       ' to True.  
       LinkLabel1.LinkVisited = True  
       ' Call the Process.Start method to open the default browser   
       ' with a URL:  
       System.Diagnostics.Process.Start("http://www.microsoft.com")  
    End Sub  
  
    ```  
  
    ```csharp  
    private void linkLabel1_LinkClicked(object sender, System.Windows.Forms.LinkLabelLinkClickedEventArgs e)  
    {  
       try  
       {  
          VisitLink();  
       }  
       catch (Exception ex )  
       {  
          MessageBox.Show("Unable to open link that was clicked.");  
       }  
    }  
  
    private void VisitLink()  
    {  
       // Change the color of the link text by setting LinkVisited   
       // to true.  
       linkLabel1.LinkVisited = true;  
       //Call the Process.Start method to open the default browser   
       //with a URL:  
       System.Diagnostics.Process.Start("http://www.microsoft.com");  
    }  
  
    ```  
  
    ```cpp  
    private:  
       void linkLabel1_LinkClicked(System::Object ^  sender,  
          System::Windows::Forms::LinkLabelLinkClickedEventArgs ^  e)  
       {  
          try  
          {  
             VisitLink();  
          }  
          catch (Exception ^ ex)  
          {  
             MessageBox::Show("Unable to open link that was clicked.");  
          }  
       }  
    private:  
       void VisitLink()  
       {  
          // Change the color of the link text by setting LinkVisited   
          // to true.  
          linkLabel1->LinkVisited = true;  
          // Call the Process.Start method to open the default browser   
          // with a URL:  
          System::Diagnostics::Process::Start("http://www.microsoft.com");  
       }  
    ```  
  
## Voir aussi  
 <xref:System.Diagnostics.Process.Start%2A?displayProperty=fullName>   
 [Vue d'ensemble du contrôle LinkLabel](../../../../docs/framework/winforms/controls/linklabel-control-overview-windows-forms.md)   
 [Comment : modifier l'apparence du contrôle LinkLabel Windows Forms](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-linklabel-control.md)   
 [LinkLabel, contrôle](../../../../docs/framework/winforms/controls/linklabel-control-windows-forms.md)