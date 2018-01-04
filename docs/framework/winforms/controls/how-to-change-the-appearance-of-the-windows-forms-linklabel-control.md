---
title: "Comment : modifier l'apparence du contrôle LinkLabel Windows Forms"
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
- LinkLabel properties
- LinkLabel control [Windows Forms], changing appearance of links
- links [Windows Forms], changing appearance
- examples [Windows Forms], LinkLabel control
- LinkLabel control [Windows Forms], examples
ms.assetid: fdc5854f-5162-4457-8cbe-1042feb2d132
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7dc3963ab1b242ce8dce53d9bba996f52347679b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-change-the-appearance-of-the-windows-forms-linklabel-control"></a>Comment : modifier l'apparence du contrôle LinkLabel Windows Forms
Vous pouvez modifier le texte affiché par le <xref:System.Windows.Forms.LinkLabel> contrôle pour satisfaire à des fins diverses. Par exemple, il est courant pour indiquer à l’utilisateur que le texte peut être sélectionné en définissant le texte à afficher dans une couleur spécifique avec un trait de soulignement. Une fois que l’utilisateur clique sur le texte, la couleur est remplacée par une couleur différente. Pour contrôler ce comportement, vous pouvez définir cinq propriétés différentes : la <xref:System.Windows.Forms.LinkLabel.LinkBehavior%2A>, <xref:System.Windows.Forms.LinkLabel.LinkArea%2A>, <xref:System.Windows.Forms.LinkLabel.LinkColor%2A>, <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>, et <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> propriétés.  
  
### <a name="to-change-the-appearance-of-a-linklabel-control"></a>Pour modifier l’apparence d’un contrôle LinkLabel  
  
1.  Définir le <xref:System.Windows.Forms.LinkLabel.LinkColor%2A> et <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A> propriétés pour les couleurs de votre choix.  
  
     Cela peut être effectué par programme ou au moment du design dans le **propriétés** fenêtre.  
  
    ```vb  
    ' You can set the color using decimal values for red, green, and blue  
    LinkLabel1.LinkColor = Color.FromArgb(0, 0, 255)  
    ' Or you can set the color using defined constants  
    LinkLabel1.VisitedLinkColor = Color.Purple  
    ```  
  
    ```csharp  
    // You can set the color using decimal values for red, green, and blue  
    linkLabel1.LinkColor = Color.FromArgb(0, 0, 255);  
    // Or you can set the color using defined constants  
    linkLabel1.VisitedLinkColor = Color.Purple;  
    ```  
  
    ```cpp  
    // You can set the color using decimal values for red, green, and blue  
    linkLabel1->LinkColor = Color::FromArgb(0, 0, 255);  
    // Or you can set the color using defined constants  
    linkLabel1->VisitedLinkColor = Color::Purple;  
    ```  
  
2.  Définir le <xref:System.Windows.Forms.LinkLabel.Text%2A> propriété à une légende appropriée.  
  
     Cela peut être effectué par programme ou au moment du design dans le **propriétés** fenêtre.  
  
    ```vb  
    LinkLabel1.Text = "Click here to see more."  
    ```  
  
    ```csharp  
    linkLabel1.Text = "Click here to see more.";  
    ```  
  
    ```cpp  
    linkLabel1->Text = "Click here to see more.";  
    ```  
  
3.  Définir le <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> propriété pour déterminer quelle partie de la légende doit être affichée sous forme de lien.  
  
     Le <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> valeur est représentée par un <xref:System.Windows.Forms.LinkArea> contenant deux nombres, la position de caractère de départ et le nombre de caractères. Cela peut être effectué par programme ou au moment du design dans le **propriétés** fenêtre.  
  
    ```vb  
    LinkLabel1.LinkArea = new LinkArea(6,4)  
    ```  
  
    ```csharp  
    linkLabel1.LinkArea = new LinkArea(6,4);  
    ```  
  
    ```cpp  
    linkLabel1->LinkArea = LinkArea(6,4);  
    ```  
  
4.  Définir le <xref:System.Windows.Forms.LinkLabel.LinkBehavior%2A> propriété <xref:System.Windows.Forms.LinkBehavior.AlwaysUnderline>, <xref:System.Windows.Forms.LinkBehavior.HoverUnderline>, ou <xref:System.Windows.Forms.LinkBehavior.NeverUnderline>.  
  
     Si elle est définie sur <xref:System.Windows.Forms.LinkBehavior.HoverUnderline>, la partie de la légende déterminée par <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> sera souligné uniquement lorsque le curseur dessus.  
  
5.  Dans le <xref:System.Windows.Forms.LinkLabel.LinkClicked> Gestionnaire d’événements, définissez la <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> propriété `true`.  
  
     Lorsqu’un lien a été visité, il est courant de modifier son apparence d’une certaine façon, habituellement par couleur. Le texte change la couleur spécifiée par la <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A> propriété.  
  
    ```vb  
    Protected Sub LinkLabel1_LinkClicked (ByVal sender As Object, _  
       ByVal e As EventArgs) Handles LinkLabel1.LinkClicked  
       ' Change the color of the link text  
       ' by setting LinkVisited to True.  
       LinkLabel1.LinkVisited = True  
       ' Then do whatever other action is appropriate  
    End Sub  
    ```  
  
    ```csharp  
    protected void LinkLabel1_LinkClicked(object sender, System.EventArgs e)  
    {  
       // Change the color of the link text by setting LinkVisited   
       // to True.  
       linkLabel1.LinkVisited = true;  
       // Then do whatever other action is appropriate  
    }  
    ```  
  
    ```cpp  
    private:  
       System::Void linkLabel1_LinkClicked(System::Object ^  sender,  
          System::Windows::Forms::LinkLabelLinkClickedEventArgs ^  e)  
       {  
          // Change the color of the link text by setting LinkVisited   
          // to True.  
          linkLabel1->LinkVisited = true;  
          // Then do whatever other action is appropriate  
       }  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.LinkLabel.LinkArea%2A>  
 <xref:System.Windows.Forms.LinkLabel.LinkColor%2A>  
 <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>  
 <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A>  
 [Vue d'ensemble du contrôle LinkLabel](../../../../docs/framework/winforms/controls/linklabel-control-overview-windows-forms.md)  
 [Guide pratique pour créer un lien vers un objet ou une page web à l’aide du contrôle LinkLabel Windows Forms](../../../../docs/framework/winforms/controls/link-to-an-object-or-web-page-with-wf-linklabel-control.md)  
 [LinkLabel, contrôle](../../../../docs/framework/winforms/controls/linklabel-control-windows-forms.md)
