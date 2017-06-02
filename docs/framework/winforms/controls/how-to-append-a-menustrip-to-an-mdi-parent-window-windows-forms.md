---
title: "Comment&#160;: ajouter un MenuStrip &#224; une fen&#234;tre parente MDI (Windows Forms) | Microsoft Docs"
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
  - "MDI, fusionner des éléments de menu"
  - "MenuStrip (contrôle Windows Forms), ajouter"
  - "MenuStrip (contrôle Windows Forms), fusionner"
ms.assetid: ab70c936-b452-4653-b417-17be57bb795b
caps.latest.revision: 17
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 17
---
# Comment&#160;: ajouter un MenuStrip &#224; une fen&#234;tre parente MDI (Windows Forms)
Dans certaines applications, le type d'une fenêtre enfant d'interface multidocument \(MDI\) peut être différent de celui de la fenêtre parente MDI.  Par exemple, le parent MDI peut être une feuille de calcul et l'enfant MDI un graphique.  Dans ce cas, vous souhaitez mettre à jour le contenu du menu du parent MDI avec le contenu du menu de l'enfant MDI à mesure que des fenêtres enfants MDI de types différents sont activées.  
  
 La procédure suivante utilise les propriétés <xref:System.Windows.Forms.Form.IsMdiContainer%2A>, <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A>, <xref:System.Windows.Forms.MergeAction> et <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> pour ajouter le menu MDI enfant au menu MDI parent.  La fermeture de la fenêtre MDI enfant supprime le menu ajouté du MDI parent.  
  
 Consultez également [Applications d'interface multidocument \(MDI, Multiple Document Interface\)](http://msdn.microsoft.com/library/xyhh2e7e%20\(v=vs.110\)).  
  
### Pour ajouter un élément à un menu MDI parent  
  
1.  Créez un formulaire et affectez la valeur `true` à sa propriété <xref:System.Windows.Forms.Form.IsMdiContainer%2A>.  
  
2.  Ajoutez un <xref:System.Windows.Forms.MenuStrip> à `Form1` et affectez la valeur `true` à la propriété <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> du <xref:System.Windows.Forms.MenuStrip>.  
  
3.  Affectez la valeur `false` à la propriété <xref:System.Windows.Forms.ToolStripItem.Visible%2A> du <xref:System.Windows.Forms.MenuStrip> de `Form1`.  
  
4.  Ajoutez un élément de menu de niveau supérieur au <xref:System.Windows.Forms.MenuStrip> de `Form1` et affectez la valeur `&File` à sa propriété <xref:System.Windows.Forms.Control.Text%2A>.  
  
5.  Ajoutez un élément de sous\-menu à l'élément de menu `&File` et affectez la valeur `&Open` à la propriété <xref:System.Windows.Forms.Form.Text%2A>.  
  
6.  Ajoutez un formulaire au projet, ajoutez un <xref:System.Windows.Forms.MenuStrip> au formulaire et affectez la valeur `true` à la propriété <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> du <xref:System.Windows.Forms.MenuStrip> de `Form2`.  
  
7.  Ajoutez un élément de menu de niveau supérieur au <xref:System.Windows.Forms.MenuStrip> de `Form2` et affectez la valeur `&Special` à sa propriété <xref:System.Windows.Forms.Form.Text%2A>.  
  
8.  Ajoutez deux éléments de sous\-menu à l'élément de menu `&Special` et affectez respectivement les valeurs `Command&1` et `Command&2` à leur propriété <xref:System.Windows.Forms.Form.Text%2A>.  
  
9. Affectez la valeur <xref:System.Windows.Forms.MergeAction> à la propriété <xref:System.Windows.Forms.MergeAction> des éléments de menu `&Special`, `Command&1` et `Command&2`.  
  
10. Créez un gestionnaire d'événements pour l'événement <xref:System.Windows.Forms.Control.Click> du <xref:System.Windows.Forms.ToolStripMenuItem> de `&New`.  
  
11. Dans le gestionnaire d'événements, insérez du code semblable à l'exemple de code suivant pour créer et afficher de nouvelles instances de `Form2` en tant qu'enfants MDI de `Form1`.  
  
    ```vb  
    Private Sub openToolStripMenuItem_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles openToolStripMenuItem.Click  
        Dim NewMDIChild As New Form2()  
        'Set the parent form of the child window.  
            NewMDIChild.MdiParent = Me  
        'Display the new form.  
            NewMDIChild.Show()  
    End Sub  
  
    ```  
  
     \[C\#\]  
  
    ```  
    private void openToolStripMenuItem_Click(object sender, EventArgs e)  
    {  
        Form2 newMDIChild = new Form2();  
        // Set the parent form of the child window.  
            newMDIChild.MdiParent = this;  
        // Display the new form.  
            newMDIChild.Show();  
    }  
  
    ```  
  
12. Insérez du code similaire à l'exemple de code suivant dans le `&Open`<xref:System.Windows.Forms.ToolStripMenuItem> pour inscrire le gestionnaire d'événements.  
  
    ```vb  
    Private Sub openToolStripMenuItem_Click(sender As Object, e As _  
    EventArgs) Handles openToolStripMenuItem.Click  
  
    ```  
  
    ```csharp  
    this.openToolStripMenuItem.Click += new System.EventHandler(this.openToolStripMenuItem_Click);  
  
    ```  
  
## Compilation du code  
 Cet exemple nécessite :  
  
-   deux <xref:System.Windows.Forms.Form> contrôles nommés `Form1` et `Form2` ;  
  
-   un contrôle <xref:System.Windows.Forms.MenuStrip> sur `Form1` nommé `menuStrip1` et un contrôle <xref:System.Windows.Forms.MenuStrip> sur `Form2` nommé `menuStrip2` ;  
  
-   des références aux assemblys <xref:System?displayProperty=fullName> et <xref:System.Windows.Forms?displayProperty=fullName>.