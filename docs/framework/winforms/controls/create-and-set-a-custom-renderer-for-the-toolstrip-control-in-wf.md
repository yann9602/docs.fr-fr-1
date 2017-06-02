---
title: "Comment&#160;: cr&#233;er et d&#233;finir un convertisseur personnalis&#233; pour le contr&#244;le ToolStrip dans les Windows Forms | Microsoft Docs"
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
  - "exemples (Windows Forms), barres d'outils"
  - "barres d'outils (Windows Forms), rendu"
  - "ToolStrip (contrôle Windows Forms), rendu personnalisé"
  - "ToolStrip (contrôle Windows Forms), rendu"
ms.assetid: 88a804ba-679f-4ba3-938a-0dc396199c5b
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# Comment&#160;: cr&#233;er et d&#233;finir un convertisseur personnalis&#233; pour le contr&#244;le ToolStrip dans les Windows Forms
Les contrôles <xref:System.Windows.Forms.ToolStrip> fournissent une prise en charge simple pour les thèmes et les styles.  Vous pouvez personnaliser totalement l'aspect et le comportement en affectant à la propriété <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=fullName> ou <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=fullName> un convertisseur personnalisé.  
  
 Vous pouvez assigner des convertisseurs à chaque contrôle <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, <xref:System.Windows.Forms.ContextMenuStrip> ou <xref:System.Windows.Forms.StatusStrip> ; vous pouvez également utiliser la propriété <xref:System.Windows.Forms.ToolStripManager.Renderer%2A> pour tous les objets en affectant à la propriété <xref:System.Windows.Forms.ToolStrip.RenderMode%2A?displayProperty=fullName> la valeur <xref:System.Windows.Forms.ToolStripRenderMode?displayProperty=fullName>.  
  
> [!NOTE]
>  <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> ne retourne <xref:System.Windows.Forms.ToolStripRenderMode> que si la valeur de <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=fullName> n'est pas `null`.  
  
### Pour créer un convertisseur personnalisé  
  
1.  Étendez la classe <xref:System.Windows.Forms.ToolStripRenderer>.  
  
2.  Implémentez le rendu personnalisé souhaité en substituant les membres *On…* appropriés  
  
    ```vb  
    Public Class RedTextRenderer  
        Inherits System.Windows.Forms.ToolStripRenderer  
        Protected Overrides Sub OnRenderItemText(ByVal e As _  
            ToolStripItemTextRenderEventArgs)   
            e.TextColor = Color.Red  
            e.TextFont = New Font("Helvetica", 7, FontStyle.Bold)  
            MyBase.OnRenderItemText(e)  
        End Sub  
    End Class  
  
    ```  
  
     \[C\#\]  
  
    ```  
    public class RedTextRenderer : _  
        System.Windows.Forms.ToolStripRenderer  
    {  
        protected override void _  
            OnRenderItemText(ToolStripItemTextRenderEventArgs e)  
        {  
            e.TextColor = Color.Red;  
            e.TextFont = new Font("Helvetica", 7, FontStyle.Bold);  
           base.OnRenderItemText(e);  
        }  
    }  
  
    ```  
  
### Pour définir le convertisseur personnalisé en tant que convertisseur actuel  
  
1.  Pour définir le convertisseur personnalisé pour <xref:System.Windows.Forms.ToolStrip>, affectez à la propriété <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=fullName> le convertisseur personnalisé.  
  
    ```vb  
    toolStrip1.Renderer = New RedTextRenderer()  
  
    ```  
  
     \[C\#\]  
  
    ```  
    toolStrip1.Renderer = new RedTextRenderer();  
  
    ```  
  
2.  De même, pour définir le convertisseur personnalisé pour toutes les classes <xref:System.Windows.Forms.ToolStrip> contenues dans votre application, affectez à la propriété <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=fullName> le convertisseur personnalisé et à la propriété <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> la valeur <xref:System.Windows.Forms.ToolStripRenderMode>.  
  
    ```vb  
    toolStrip1.RenderMode = ToolStripRenderMode.ManagerRenderMode  
    ToolStripManager.Renderer = New RedTextRenderer()  
  
    ```  
  
     \[C\#\]  
  
    ```  
    toolStrip1.RenderMode = ToolStripRenderMode.ManagerRenderMode;  
    ToolStripManager.Renderer = new RedTextRenderer();  
  
    ```  
  
## Voir aussi  
 <xref:System.Windows.Forms.ToolStripManager.Renderer%2A>   
 <xref:System.Windows.Forms.ToolStripRenderer>   
 <xref:System.Windows.Forms.ToolStrip.RenderMode%2A>   
 [Vue d'ensemble du contrôle ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)   
 [Architecture du contrôle ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md)   
 [Résumé de la technologie ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-technology-summary.md)