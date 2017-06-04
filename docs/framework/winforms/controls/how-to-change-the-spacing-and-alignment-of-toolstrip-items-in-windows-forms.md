---
title: "Comment&#160;: modifier l&#39;espacement et l&#39;alignement d&#39;&#233;l&#233;ments ToolStrip dans les Windows Forms | Microsoft Docs"
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
  - "barres d'outils (Windows Forms), aligner les éléments"
  - "ToolStrip (contrôle Windows Forms), aligner les éléments"
ms.assetid: cd483466-0f49-43df-addf-e2b5fcd64027
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# Comment&#160;: modifier l&#39;espacement et l&#39;alignement d&#39;&#233;l&#233;ments ToolStrip dans les Windows Forms
Le contrôle <xref:System.Windows.Forms.ToolStrip> prend totalement en charge les fonctionnalités de disposition telles que le dimensionnement, l'espacement des contrôles <xref:System.Windows.Forms.ToolStripItem> les uns par rapport aux autres, la disposition des contrôles sur le <xref:System.Windows.Forms.ToolStrip> et l'espacement des contrôles par rapport au <xref:System.Windows.Forms.ToolStrip>.  
  
 La valeur par défaut de la propriété <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> étant `true`, les contrôles sont automatiquement dimensionnés, sauf si vous affectez à la propriété <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> la valeur `false`.  
  
### Pour dimensionner manuellement un ToolStripItem  
  
1.  Affectez à la propriété <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> la valeur `false` pour le contrôle associé.  
  
    ```vb  
    ToolStripButton1.AutoSize = False  
  
    ```  
  
    ```csharp  
    toolStripButton1.AutoSize = false;  
  
    ```  
  
2.  Définissez la propriété <xref:System.Windows.Forms.ToolStripItem.Size%2A> comme vous le souhaitez pour le <xref:System.Windows.Forms.ToolStripItem> associé.  
  
### Pour définir l'espacement d'un ToolStripItem  
  
1.  Insérez les valeurs souhaitées \(en pixels\) dans la propriété <xref:System.Windows.Forms.ToolStripItem.Margin%2A> du contrôle associé.  
  
     Les valeurs de la propriété <xref:System.Windows.Forms.ToolStripItem.Margin%2A> spécifient l'espacement entre l'élément et éléments adjacents dans cet ordre: gauche, haut, droit et bas.  
  
    ```vb  
    ToolStripTextBox1.Margin = New System.Windows.Forms.Padding _  
        (3, 0, 3, 0)  
  
    ```  
  
    ```csharp  
    toolStripTextBox1.Margin = new System.Windows.Forms.Padding   
        (3, 0, 3, 0);  
  
    ```  
  
### Pour aligner un contrôle ToolStripItem à droite du contrôle ToolStrip  
  
1.  Affectez à la propriété <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> la valeur <xref:System.Windows.Forms.ToolStripItemAlignment> pour le contrôle associé.  Par défaut, <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> a la valeur <xref:System.Windows.Forms.ToolStripItemAlignment>, qui aligne les contrôles à gauche du <xref:System.Windows.Forms.ToolStrip>.  
  
    ```vb  
    ToolStripSplitButton1.Alignment = _  
        System.Windows.Forms.ToolStripItemAlignment.Right  
  
    ```  
  
    ```csharp  
    toolStripSplitButton1.Alignment =   
        System.Windows.Forms.ToolStripItemAlignment.Right;  
  
    ```  
  
### Pour organiser des éléments ToolStrip sur ToolStrip  
  
-   Affectez à la propriété <xref:System.Windows.Forms.ToolStrip.LayoutStyle%2A> la valeur de <xref:System.Windows.Forms.ToolStripLayoutStyle> de votre choix.  
  
    ```vb  
    ToolStripDropDown1.LayoutStyle = _  
        System.Windows.Forms.ToolStripLayoutStyle.Flow  
  
    ```  
  
    ```csharp  
    toolStripDropDown1.LayoutStyle =   
        System.Windows.Forms.ToolStripLayoutStyle.Flow;  
  
    ```  
  
## Voir aussi  
 <xref:System.Windows.Forms.ToolStrip>   
 <xref:System.Windows.Forms.Control.Layout>   
 <xref:System.Windows.Forms.ToolStrip.LayoutCompleted>   
 <xref:System.Windows.Forms.ToolStrip.LayoutSettings%2A>   
 <xref:System.Windows.Forms.ToolStripItem.TextImageRelation%2A>   
 <xref:System.Windows.Forms.ToolStripItem.Placement%2A>   
 <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A>   
 [Vue d'ensemble du contrôle ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)   
 [Architecture du contrôle ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md)   
 [Résumé de la technologie ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-technology-summary.md)