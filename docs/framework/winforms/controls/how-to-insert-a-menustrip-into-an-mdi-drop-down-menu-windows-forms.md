---
title: "Comment&#160;: ins&#233;rer un MenuStrip dans un menu d&#233;roulant MDI (Windows Forms) | Microsoft Docs"
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
  - "MenuStrip (contrôle Windows Forms), insérer"
  - "MenuStrip (contrôle Windows Forms), fusionner"
ms.assetid: 0fad444e-26d9-49af-8860-044d9c10d608
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# Comment&#160;: ins&#233;rer un MenuStrip dans un menu d&#233;roulant MDI (Windows Forms)
Dans certaines applications, le type d'une fenêtre d'interface multidocument \(MDI\) enfant peut être différent de la fenêtre MDI parente.  Par exemple, le parent MDI peut être une feuille de calcul et l'enfant MDI peut être un graphique.  Dans ce cas, vous voulez mettre à jour le contenu du menu du parent MDI avec le contenu du menu de l'enfant MDI lorsque des fenêtres MDI enfants de types différents sont activées.  
  
 La procédure suivante utilise les propriétés <xref:System.Windows.Forms.Form.IsMdiContainer%2A>, <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A>, <xref:System.Windows.Forms.MergeAction> et <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> pour insérer un groupe d'éléments du menu MDI enfant dans la partie déroulante du menu MDI parent.  La fermeture de la fenêtre MDI enfant supprime les éléments de menu insérés à partir du parent MDI.  
  
### Pour insérer un MenuStrip dans un menu déroulant MDI  
  
1.  Créez un formulaire et affectez à sa propriété <xref:System.Windows.Forms.Form.IsMdiContainer%2A> la valeur `true`.  
  
2.  Ajoutez <xref:System.Windows.Forms.MenuStrip> à `Form1` et affectez à la propriété <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> de <xref:System.Windows.Forms.MenuStrip> la valeur `true`.  
  
3.  Ajoutez un élément de menu de niveau supérieur à `Form1` <xref:System.Windows.Forms.MenuStrip> et affectez à sa propriété <xref:System.Windows.Forms.Control.Text%2A> la valeur `&File`.  
  
4.  Ajoutez trois éléments de sous\-menu à l'élément de menu `&File` et affectez à leurs propriétés <xref:System.Windows.Forms.ToolStripItem.Text%2A> les valeurs `&Open`, `&Import from` et `E&xit`.  
  
5.  Ajoutez deux éléments de sous\-menu à l'élément de sous\-menu `&Import from` et affectez à leurs propriétés <xref:System.Windows.Forms.ToolStripItem.Text%2A> les valeurs `&Word` et `&Excel`.  
  
6.  Ajoutez un formulaire au projet, ajoutez <xref:System.Windows.Forms.MenuStrip> au formulaire et affectez à la propriété <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> de `Form2` <xref:System.Windows.Forms.MenuStrip> la valeur `true`.  
  
7.  Ajoutez un élément de menu de niveau supérieur à `Form2` <xref:System.Windows.Forms.MenuStrip> et affectez à sa propriété <xref:System.Windows.Forms.ToolStripItem.Text%2A> la valeur `&File`.  
  
8.  Ajoutez des éléments de sous\-menu au menu `&File` de `Form2` dans l'ordre suivant : <xref:System.Windows.Forms.ToolStripSeparator>, `&Save`, `&Close` `and Save` et à nouveau <xref:System.Windows.Forms.ToolStripSeparator>.  
  
9. Définissez les propriétés <xref:System.Windows.Forms.MergeAction> et <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> des éléments de menu `Form2` comme indiqué dans le tableau suivant.  
  
    |Élément de menu Form2|Valeur MergeAction|Valeur MergeIndex|  
    |---------------------------|------------------------|-----------------------|  
    |Fichier|MatchOnly|\-1|  
    |Separator|Insert|2|  
    |Enregistrer|Insert|3|  
    |Save and Close|Insert|4|  
    |Separator|Insert|5|  
  
10. Créez un gestionnaire d'événements pour l'événement <xref:System.Windows.Forms.Control.Click> de l'élément `&Open` <xref:System.Windows.Forms.ToolStripMenuItem>.  
  
11. Dans le gestionnaire d'événements, créez et affichez de nouvelles instances de `Form2` en tant qu'enfants MDI de `Form1` en insérant un code similaire à celui\-ci :  
  
    ```vb  
    Private Sub openToolStripMenuItem_Click(ByVal sender As System.Object, _  
    ByVal e As System.EventArgs) Handles openToolStripMenuItem.Click  
        Dim NewMDIChild As New Form2()  
        'Set the parent form of the child window.  
            NewMDIChild.MdiParent = Me  
        'Display the new form.  
            NewMDIChild.Show()  
    End Sub  
  
    ```  
  
    ```csharp  
    private void openToolStripMenuItem_Click(object sender, EventArgs e)  
    {  
        Form2 newMDIChild = new Form2();  
        // Set the parent form of the child window.  
            newMDIChild.MdiParent = this;  
        // Display the new form.  
            newMDIChild.Show();  
    }  
  
    ```  
  
12. Insérez un code similaire à l'exemple de code suivant dans `&Open` <xref:System.Windows.Forms.ToolStripMenuItem> pour inscrire le gestionnaire d'événements.  
  
    ```vb  
    Private Sub openToolStripMenuItem_Click(sender As Object, e As _  
    EventArgs) Handles openToolStripMenuItem.Click  
  
    ```  
  
    ```csharp  
    this.openToolStripMenuItem.Click += new System.EventHandler(this.openToolStripMenuItem_Click);  
  
    ```  
  
## Compilation du code  
 Cet exemple nécessite :  
  
-   Deux contrôles <xref:System.Windows.Forms.Form> nommés `Form1` et `Form2`.  
  
-   Un contrôle <xref:System.Windows.Forms.MenuStrip> placé sur `Form1` et nommé `menuStrip1`, ainsi qu'un contrôle <xref:System.Windows.Forms.MenuStrip> placé sur `Form2` et nommé `menuStrip2`.  
  
-   Références aux assemblys <xref:System?displayProperty=fullName> et <xref:System.Windows.Forms?displayProperty=fullName>.  
  
## Voir aussi  
 [Comment : créer des formulaires MDI parents](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)   
 [Comment : créer des formulaires MDI enfants](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md)   
 [Vue d'ensemble du contrôle MenuStrip](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)