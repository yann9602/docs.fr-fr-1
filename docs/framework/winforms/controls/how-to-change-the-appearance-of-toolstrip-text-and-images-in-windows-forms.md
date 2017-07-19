---
title: "Comment&#160;: modifier l&#39;apparence du texte et des images de ToolStrip dans les Windows Forms | Microsoft Docs"
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
  - "barres d'outils (Windows Forms), apparence"
  - "barres d'outils (Windows Forms), images"
  - "barres d'outils (Windows Forms), texte"
  - "ToolStrip (contrôle Windows Forms), apparence"
  - "ToolStrip (contrôle Windows Forms), images"
  - "ToolStrip (contrôle Windows Forms), texte"
ms.assetid: d62dc9d1-2edd-4dfa-aed7-1335d6e13d86
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# Comment&#160;: modifier l&#39;apparence du texte et des images de ToolStrip dans les Windows Forms
Vous pouvez contrôler si le texte et les images s'affichent sur <xref:System.Windows.Forms.ToolStripItem> et comment ils sont alignés les uns par rapport aux autres et par rapport à <xref:System.Windows.Forms.ToolStrip>.  
  
### Pour définir les éléments affichés sur un ToolStripItem  
  
-   Affectez la valeur souhaitée à la propriété <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A>.  Les possibilités sont `Image`, `ImageAndText`, `None` et `Text`.  La valeur par défaut est `ImageAndText`.  
  
    ```vb  
    ToolStripButton2.DisplayStyle = _  
        System.Windows.Forms.ToolStripItemDisplayStyle.Image  
  
    ```  
  
    ```csharp  
    toolStripButton2.DisplayStyle = System.Windows.Forms.ToolStripItemDisplayStyle.Image;  
  
    ```  
  
### Pour aligner du texte sur un ToolStripItem  
  
-   Affectez la valeur souhaitée à la propriété <xref:System.Windows.Forms.ToolStripItem.TextAlign%2A>.  Les possibilités sont toute combinaison de haut, milieu et bas avec gauche, centre et droit.  La valeur par défaut est `MiddleCenter`.  
  
    ```vb  
    ToolStripSplitButton1.TextAlign = _  
        System.Drawing.ContentAlignment.MiddleRight  
  
    ```  
  
    ```csharp  
    toolStripSplitButton1.TextAlign = System.Drawing.ContentAlignment.MiddleRight;  
  
    ```  
  
### Pour aligner une image sur un ToolStripItem  
  
-   Affectez la valeur souhaitée à la propriété <xref:System.Windows.Forms.ToolStripItem.ImageAlign%2A>.  Les possibilités sont toute combinaison de haut, milieu et bas avec gauche, centre et droit.  La valeur par défaut est `MiddleLeft`.  
  
    ```vb  
    ToolStripSplitButton1.ImageAlign = _  
        System.Drawing.ContentAlignment.MiddleRight  
  
    ```  
  
    ```csharp  
    toolStripSplitButton1.ImageAlign = System.Drawing.ContentAlignment.MiddleRight;  
  
    ```  
  
### Pour définir comment le texte et les images ToolStripItem sont affichés les uns par rapport aux autres  
  
-   Affectez la valeur souhaitée à la propriété <xref:System.Windows.Forms.ToolStripItem.TextImageRelation%2A>.  Les possibilités sont `ImageAboveText`, `ImageBeforeText`, `Overlay`, `TextAboveImage` et `TextBeforeImage`.  La valeur par défaut est `ImageBeforeText`.  
  
    ```vb  
    ToolStripButton1.TextImageRelation = _  
        System.Windows.Forms.TextImageRelation.ImageAboveText  
  
    ```  
  
    ```csharp  
    toolStripButton1.TextImageRelation = System.Windows.Forms.TextImageRelation.ImageAboveText;  
  
    ```  
  
## Voir aussi  
 <xref:System.Windows.Forms.ToolStrip>   
 [Vue d'ensemble du contrôle ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)   
 [Architecture du contrôle ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md)   
 [Résumé de la technologie ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-technology-summary.md)