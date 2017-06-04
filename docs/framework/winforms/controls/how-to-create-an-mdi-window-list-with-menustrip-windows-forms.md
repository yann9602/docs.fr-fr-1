---
title: "Comment&#160;: cr&#233;er une liste des fen&#234;tres MDI avec MenuStrip (Windows Forms) | Microsoft Docs"
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
  - "MDI, créer des listes de fenêtres"
  - "MenuStrip (contrôle Windows Forms), créer des listes de fenêtres"
ms.assetid: 04fb414b-811f-4a83-aab6-b4a24646dec5
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# Comment&#160;: cr&#233;er une liste des fen&#234;tres MDI avec MenuStrip (Windows Forms)
Utilisez l'interface MDI \(Multiple\-Document Interface\) pour créer des applications qui peuvent ouvrir plusieurs documents simultanément et effectuer une opération de copier\/coller du contenu d'un document vers un autre.  
  
 Cette procédure indique comment créer une liste de tous les formulaires enfants actifs dans le menu Fenêtre du parent.  
  
### Pour créer une liste de fenêtres MDI sur un MenuStrip  
  
1.  Créez un formulaire et affectez à sa propriété <xref:System.Windows.Forms.Form.IsMdiContainer%2A> la valeur `true`.  
  
2.  Ajoutez <xref:System.Windows.Forms.MenuStrip> au formulaire.  
  
3.  Ajoutez deux éléments de menu de niveau supérieur à <xref:System.Windows.Forms.MenuStrip> et affectez à leurs propriétés <xref:System.Windows.Forms.Control.Text%2A> les valeurs `&File` et `&Window`.  
  
4.  Ajoutez un élément de sous\-menu à l'élément de menu `&File` et affectez à sa propriété <xref:System.Windows.Forms.ToolStripItem.Text%2A> la valeur `&Open`.  
  
5.  définissez la propriété d' <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> d' <xref:System.Windows.Forms.MenuStrip> à `&Window`<xref:System.Windows.Forms.ToolStripMenuItem>.  
  
6.  Ajoutez un formulaire au projet et ajoutez à ce dernier le contrôle souhaité \(un autre <xref:System.Windows.Forms.MenuStrip>, par exemple\).  
  
7.  créez un gestionnaire d'événements pour l'événement d' <xref:System.Windows.Forms.Control.Click> d' `&New`<xref:System.Windows.Forms.ToolStripMenuItem>.  
  
8.  Dans le gestionnaire d'événements, créez et affichez de nouvelles instances de `Form2` en tant qu'enfants MDI de `Form1` en insérant un code similaire à celui\-ci :  
  
    ```vb  
    Private Sub openToolStripMenuItem_Click(ByVal sender As _  
    System.Object, ByVal e As System.EventArgs) Handles _  
    openToolStripMenuItem.Click  
        Dim NewMDIChild As New Form2()  
        'Set the parent form of the child window.  
            NewMDIChild.MdiParent = Me  
        'Display the new form.  
            NewMDIChild.Show()  
    End Sub  
  
    ```  
  
     \[C\#\]  
  
    ```  
    private void newToolStripMenuItem_Click(object sender, EventArgs e)  
    {  
        Form2 newMDIChild = new Form2();  
        // Set the parent form of the child window.  
            newMDIChild.MdiParent = this;  
        // Display the new form.  
            newMDIChild.Show();  
    }  
  
    ```  
  
9. Placez le code similaire au code suivant dans `&New`<xref:System.Windows.Forms.ToolStripMenuItem> pour inscrire le gestionnaire d'événements.  
  
    ```vb  
    Private Sub newToolStripMenuItem_Click(sender As Object, e As _  
    EventArgs) Handles newToolStripMenuItem.Click  
  
    ```  
  
    ```csharp  
    this.newToolStripMenuItem.Click += new System.EventHandler(this.newToolStripMenuItem_Click);  
  
    ```  
  
## Compilation du code  
 Cet exemple nécessite :  
  
-   Deux contrôles <xref:System.Windows.Forms.Form> nommés `Form1` et `Form2`.  
  
-   Un contrôle <xref:System.Windows.Forms.MenuStrip> placé sur `Form1` et nommé `menuStrip1`, ainsi qu'un contrôle <xref:System.Windows.Forms.MenuStrip> placé sur `Form2` et nommé `menuStrip2`.  
  
-   Références aux assemblys <xref:System?displayProperty=fullName> et <xref:System.Windows.Forms?displayProperty=fullName>.  
  
## Voir aussi  
 [Comment : créer des formulaires MDI parents](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)   
 [Comment : créer des formulaires MDI enfants](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md)   
 [MenuStrip, contrôle](../../../../docs/framework/winforms/controls/menustrip-control-windows-forms.md)