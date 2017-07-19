---
title: "Comment&#160;: h&#233;riter de contr&#244;les Windows Forms existants | Microsoft Docs"
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
  - "contrôles personnalisés (Windows Forms), héritage"
  - "héritage, contrôles personnalisés Windows Forms"
ms.assetid: 1e1fc8ea-c615-4cf0-a356-16d6df7444ab
caps.latest.revision: 18
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 18
---
# Comment&#160;: h&#233;riter de contr&#244;les Windows Forms existants
Pour enrichir les fonctionnalités d'un contrôle, créez un contrôle dérivé d'un contrôle existant par héritage.  Lorsque vous héritez d'un contrôle existant, vous héritez de toutes ses fonctionnalités et propriétés visuelles.  Par exemple, si vous avez créé un contrôle hérité de <xref:System.Windows.Forms.Button>, il aura l'aspect et le comportement d'un contrôle <xref:System.Windows.Forms.Button> standard.  Vous pouvez alors développer ou modifier les fonctionnalités du nouveau contrôle en implémentant de nouvelles méthodes et propriétés.  Dans certains contrôles, vous pouvez également modifier l'aspect visuel du contrôle hérité en substituant la méthode <xref:System.Windows.Forms.Control.OnPaint%2A>.  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.  Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils**.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### Pour créer un contrôle hérité  
  
1.  Créer un projet **Windows Forms Application**.  
  
2.  Dans le menu **Projet**, cliquez sur **Ajouter un nouvel élément**.  
  
     La boîte de dialogue **Ajouter un nouvel élément** s'affiche alors.  
  
3.  Dans la boîte de dialogue **Ajouter un nouvel élément**, cliquez sur **Contrôle personnalisé**.  
  
     Un nouveau contrôle personnalisé est alors ajouté à votre projet.  
  
4.  Si vous utilisez Visual Basic, dans la partie supérieure de l'**Explorateur de solutions**, cliquez sur **Afficher tous les fichiers**.  Développez CustomControl1.vb puis ouvrez CustomControl1.Designer.vb dans l'éditeur de code.  
  
5.  Si vous utilisez C\#, ouvrez CustomControl1.cs dans l'éditeur de code.  
  
6.  Recherchez la déclaration de classe héritée de <xref:System.Windows.Forms.Control>.  
  
7.  Remplacez la classe de base par le contrôle dont vous voulez hériter.  
  
     Par exemple, si vous souhaitez hériter de <xref:System.Windows.Forms.Button>, remplacez la déclaration de classe par ce qui suit :  
  
    ```vb  
    Partial Class CustomControl1  
        Inherits System.Windows.Forms.Button  
    ```  
  
    ```csharp  
    public partial class CustomControl1 : System.Windows.Forms.Button  
    ```  
  
8.  Si vous utilisez Visual Basic, enregistrez et fermez CustomControl1.Designer.vb.  Ouvrez CustomControl1.vb dans l'éditeur de code.  
  
9. Implémentez les éventuelles méthodes ou propriétés personnalisées que votre contrôle contiendra.  
  
10. Pour modifier l'aspect graphique du contrôle, substituez la méthode <xref:System.Windows.Forms.Control.OnPaint%2A>.  
  
    > [!NOTE]
    >  La substitution de la méthode <xref:System.Windows.Forms.Control.OnPaint%2A> ne vous permet pas de modifier l'apparence de tous les contrôles.  Les contrôles dont la peinture est définie par Windows \(par exemple, <xref:System.Windows.Forms.TextBox>\) n'appellent jamais leur méthode <xref:System.Windows.Forms.Control.OnPaint%2A> et n'utiliseront donc jamais le code personnalisé.  Reportez\-vous à la documentation traitant du contrôle que vous souhaitez modifier pour vérifier si la méthode <xref:System.Windows.Forms.Control.OnPaint%2A> est disponible.  Pour obtenir la liste de tous les Contrôles Windows Form, consultez [Contrôles à utiliser dans les Windows Forms](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md).  Si un contrôle ne comprend pas la méthode membre <xref:System.Windows.Forms.Control.OnPaint%2A>, vous ne pouvez pas modifier son apparence en substituant cette méthode.  Pour plus d'informations sur la peinture personnalisée, consultez [Peinture et rendu personnalisés des contrôles](../../../../docs/framework/winforms/controls/custom-control-painting-and-rendering.md).  
  
    ```vb  
    Protected Overrides Sub OnPaint(ByVal e As _  
       System.Windows.Forms.PaintEventArgs)  
       MyBase.OnPaint(e)  
       ' Insert code to do custom painting.   
       ' If you want to completely change the appearance of your control,  
       ' do not call MyBase.OnPaint(e).  
    End Sub  
  
    ```  
  
    ```csharp  
    protected override void OnPaint(PaintEventArgs pe)  
    {  
       base.OnPaint(pe);  
       // Insert code to do custom painting.  
       // If you want to completely change the appearance of your control,  
       // do not call base.OnPaint(pe).  
    }  
    ```  
  
11. Enregistrez et testez le contrôle.  
  
## Voir aussi  
 [Variétés de contrôles personnalisés](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)   
 [Comment : hériter de la classe du contrôle](../../../../docs/framework/winforms/controls/how-to-inherit-from-the-control-class.md)   
 [Comment : hériter de la classe UserControl](../../../../docs/framework/winforms/controls/how-to-inherit-from-the-usercontrol-class.md)   
 [Comment : créer des contrôles pour des Windows Forms](../../../../docs/framework/winforms/controls/how-to-author-controls-for-windows-forms.md)   
 [Troubleshooting Inherited Event Handlers in Visual Basic](../Topic/Troubleshooting%20Inherited%20Event%20Handlers%20in%20Visual%20Basic.md)   
 [Procédure pas à pas : héritage à partir d'un contrôle Windows Forms à l'aide de Visual Basic](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic.md)   
 [Procédure pas à pas : héritage d'un contrôle Windows Forms à l'aide de Visual C\#](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)