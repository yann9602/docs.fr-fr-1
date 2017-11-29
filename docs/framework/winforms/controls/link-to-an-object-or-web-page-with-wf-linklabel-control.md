---
title: "Comment : créer un lien vers un objet ou une page web à l’aide du contrôle LinkLabel Windows Forms"
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
- examples [Windows Forms], LinkLabel control
- Windows Forms, linking to objects
- Web page link control
- linking [Windows Forms], to other forms
- Windows Forms, linking to Web pages
- links [Windows Forms], to other forms
- LinkLabel control [Windows Forms], linking to object or Web page
- LinkLabel control [Windows Forms], examples
ms.assetid: 6c91c975-3cb7-4504-82f0-fc6255f8fb85
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 04566d96fe9031821b904df3bf9ec93244b62cfe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-link-to-an-object-or-web-page-with-the-windows-forms-linklabel-control"></a>Comment : créer un lien vers un objet ou une page web à l’aide du contrôle LinkLabel Windows Forms
Windows Forms <xref:System.Windows.Forms.LinkLabel> contrôle vous permet de créer des liens Web dans votre formulaire. Un clic sur le lien, vous pouvez modifier sa couleur pour indiquer que le lien a été visité. Pour plus d’informations sur la modification de la couleur, consultez [Comment : modifier l’apparence du contrôle LinkLabel Windows Forms](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-linklabel-control.md).  
  
## <a name="linking-to-another-form"></a>Lier à un autre formulaire  
  
#### <a name="to-link-to-another-form-with-a-linklabel-control"></a>Pour lier à un autre formulaire avec un contrôle LinkLabel  
  
1.  Définir le <xref:System.Windows.Forms.LinkLabel.Text%2A> propriété à une légende appropriée.  
  
2.  Définir le <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> propriété pour déterminer quelle partie de la légende doit être affichée sous forme de lien. Comment elle est indiquée dépend des propriétés relatives à l’apparence de l’étiquette du lien. Le <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> valeur est représentée par un <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> objet contenant deux nombres, la position de caractère de départ et le nombre de caractères. Le <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> propriété peut être définie dans la fenêtre Propriétés ou dans le code d’une manière semblable à ce qui suit :  
  
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
  
3.  Dans le <xref:System.Windows.Forms.LinkLabel.LinkClicked> Gestionnaire d’événements, appeler le <xref:System.Windows.Forms.Form.Show%2A> méthode pour ouvrir un autre formulaire dans le projet et définir le <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> propriété `true`.  
  
    > [!NOTE]
    >  Une instance de la <xref:System.Windows.Forms.LinkLabelLinkClickedEventArgs> classe comporte une référence à la <xref:System.Windows.Forms.LinkLabel> contrôle qui a été activé, il est donc inutile d’effectuer un cast du `sender` objet.  
  
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
  
## <a name="linking-to-a-web-page"></a>Lien vers une Page Web  
 Le <xref:System.Windows.Forms.LinkLabel> contrôle peut également être utilisé pour afficher une page Web avec le navigateur par défaut.  
  
#### <a name="to-start-internet-explorer-and-link-to-a-web-page-with-a-linklabel-control"></a>Pour démarrer Internet Explorer et lien vers une page Web avec un contrôle LinkLabel  
  
1.  Définir le <xref:System.Windows.Forms.LinkLabel.Text%2A> propriété à une légende appropriée.  
  
2.  Définir le <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> propriété pour déterminer quelle partie de la légende doit être affichée sous forme de lien.  
  
3.  Dans le <xref:System.Windows.Forms.LinkLabel.LinkClicked> Gestionnaire d’événements, au beau milieu d’un bloc de gestion des exceptions, appelez une deuxième procédure qui définit la <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> propriété `true` et utilise le <xref:System.Diagnostics.Process.Start%2A> méthode pour démarrer le navigateur par défaut avec une URL. Pour utiliser le <xref:System.Diagnostics.Process.Start%2A> méthode, vous devez ajouter une référence à la <xref:System.Diagnostics?displayProperty=nameWithType> espace de noms.  
  
    > [!IMPORTANT]
    >  Si le code ci-dessous est exécuté dans un environnement de confiance partielle (tels que sur un lecteur partagé), le compilateur JIT échoue lorsque le `VisitLink` méthode est appelée. La `System.Diagnostics.Process.Start` instruction provoque une demande de liaison échoue. En interceptant l’exception lors de la `VisitLink` est appelée, le code ci-dessous garantit que si le compilateur JIT échoue, l’erreur est gérée correctement.  
  
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
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType>  
 [Vue d'ensemble du contrôle LinkLabel](../../../../docs/framework/winforms/controls/linklabel-control-overview-windows-forms.md)  
 [Guide pratique pour modifier l'apparence du contrôle LinkLabel Windows Forms](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-linklabel-control.md)  
 [LinkLabel, contrôle](../../../../docs/framework/winforms/controls/linklabel-control-windows-forms.md)
