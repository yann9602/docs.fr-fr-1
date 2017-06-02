---
title: "Comment&#160;: modifier l&#39;apparence du contr&#244;le LinkLabel Windows Forms | Microsoft Docs"
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
  - "LinkLabel (contrôle Windows Forms), modifier l'apparence des liens"
  - "LinkLabel (contrôle Windows Forms), exemples"
  - "LinkLabel (propriétés)"
  - "liens, modifier l'aspect"
ms.assetid: fdc5854f-5162-4457-8cbe-1042feb2d132
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# Comment&#160;: modifier l&#39;apparence du contr&#244;le LinkLabel Windows Forms
Vous pouvez modifier le texte affiché par le contrôle <xref:System.Windows.Forms.LinkLabel> selon vos besoins.  Par exemple, pour indiquer à l'utilisateur qu'il est possible de cliquer sur le texte, celui\-ci est généralement défini de façon à apparaître dans une couleur particulière et avec un soulignement.  Le texte change de couleur une fois que l'utilisateur a cliqué dessus.  Pour déterminer ce comportement, vous pouvez définir cinq propriétés différentes : les propriétés <xref:System.Windows.Forms.LinkLabel.LinkBehavior%2A>, <xref:System.Windows.Forms.LinkLabel.LinkArea%2A>, <xref:System.Windows.Forms.LinkLabel.LinkColor%2A>, <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A> et <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A>.  
  
### Pour modifier l'apparence d'un contrôle LinkLabel  
  
1.  Affectez aux propriétés <xref:System.Windows.Forms.LinkLabel.LinkColor%2A> et <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A> les couleurs de votre choix.  
  
     Vous pouvez effectuer cette opération par programme ou au moment du design, dans la fenêtre **Propriétés**.  
  
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
  
2.  Affectez à la propriété <xref:System.Windows.Forms.LinkLabel.Text%2A> une légende appropriée.  
  
     Vous pouvez effectuer cette opération par programme ou au moment du design, dans la fenêtre **Propriétés**.  
  
    ```vb  
    LinkLabel1.Text = "Click here to see more."  
  
    ```  
  
    ```csharp  
    linkLabel1.Text = "Click here to see more.";  
  
    ```  
  
    ```cpp  
    linkLabel1->Text = "Click here to see more.";  
    ```  
  
3.  Définissez la propriété <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> pour déterminer quelle partie de la légende doit être affichée en tant que lien.  
  
     La valeur de <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> est représentée par un <xref:System.Windows.Forms.LinkArea> qui contient deux nombres correspondant respectivement à la position du caractère de départ et au nombre de caractères.  Vous pouvez effectuer cette opération par programme ou au moment du design, dans la fenêtre **Propriétés**.  
  
    ```vb  
    LinkLabel1.LinkArea = new LinkArea(6,4)  
  
    ```  
  
    ```csharp  
    linkLabel1.LinkArea = new LinkArea(6,4);  
  
    ```  
  
    ```cpp  
    linkLabel1->LinkArea = LinkArea(6,4);  
    ```  
  
4.  Attribuez à la propriété <xref:System.Windows.Forms.LinkLabel.LinkBehavior%2A> les valeurs <xref:System.Windows.Forms.LinkBehavior>, <xref:System.Windows.Forms.LinkBehavior> ou <xref:System.Windows.Forms.LinkBehavior>.  
  
     Si la valeur choisie est <xref:System.Windows.Forms.LinkBehavior>, la partie de la légende déterminée par la propriété <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> ne sera soulignée que lorsque le pointeur sera positionné sur elle.  
  
5.  Dans le gestionnaire d'événements <xref:System.Windows.Forms.LinkLabel.LinkClicked>, attribuez à la propriété <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A> la valeur `true`.  
  
     Lorsqu'un lien a été visité, il est courant de modifier son apparence d'une certaine façon, habituellement par la couleur.  Le texte change alors de couleur pour prendre celle qui a été définie avec la propriété <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>.  
  
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
  
## Voir aussi  
 <xref:System.Windows.Forms.LinkLabel.LinkArea%2A>   
 <xref:System.Windows.Forms.LinkLabel.LinkColor%2A>   
 <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>   
 <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A>   
 [Vue d'ensemble du contrôle LinkLabel](../../../../docs/framework/winforms/controls/linklabel-control-overview-windows-forms.md)   
 [Comment : créer un lien vers un objet ou une page Web à l'aide du contrôle LinkLabel Windows Forms](../../../../docs/framework/winforms/controls/link-to-an-object-or-web-page-with-wf-linklabel-control.md)   
 [LinkLabel, contrôle](../../../../docs/framework/winforms/controls/linklabel-control-windows-forms.md)