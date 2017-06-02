---
title: "Comment&#160;: activer la saisie semi-automatique dans les contr&#244;les ToolStrip dans les Windows Forms | Microsoft Docs"
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
  - "AutoComplete, activer dans les barres d'outils"
  - "AutoComplete, exemples"
  - "exemples (Windows Forms), barres d'outils"
  - "barres d'outils (Windows Forms), AutoComplete"
  - "ToolStrip (contrôle Windows Forms), AutoComplete"
  - "ToolStripComboBox (classe), exemples"
ms.assetid: fd66d085-1af1-45d4-930a-cde944da2e16
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# Comment&#160;: activer la saisie semi-automatique dans les contr&#244;les ToolStrip dans les Windows Forms
La procédure suivante combine <xref:System.Windows.Forms.ToolStripLabel> avec <xref:System.Windows.Forms.ToolStripComboBox> qui peut se dérouler pour afficher une liste d'éléments, tels que des sites Web visités récemment.  Si l'utilisateur tape un caractère qui correspond au premier caractère de l'un des éléments de la liste, l'élément est affiché immédiatement.  
  
> [!NOTE]
>  La saisie semi\-automatique fonctionne avec les contrôles `ToolStrip` de la même façon qu'avec les contrôles traditionnels, tels que <xref:System.Windows.Forms.ComboBox> et <xref:System.Windows.Forms.TextBox>.  
  
### Pour activer la saisie semi\-automatique dans un contrôle ToolStrip  
  
1.  Créez un contrôle <xref:System.Windows.Forms.ToolStrip> et ajoutez\-lui des éléments.  
  
    ```vb  
    ToolStrip1 = New System.Windows.Forms.ToolStrip  
    ToolStrip1.Items.AddRange(New System.Windows.Forms.ToolStripItem()_  
        {ToolStripLabel1, ToolStripComboBox1})  
    ```  
  
    ```csharp  
    toolStrip1 = new System.Windows.Forms.ToolStrip();  
    toolStrip1.Items.AddRange(new System.Windows.Forms.ToolStripItem[]   
        {toolStripLabel1, toolStripComboBox1});  
  
    ```  
  
2.  Affectez à la propriété <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> de l'étiquette et de la zone de liste déroulante la valeur <xref:System.Windows.Forms.ToolStripItemOverflow> afin que la liste soit toujours disponible quelle que soit la taille du formulaire.  
  
    ```vb  
    ToolStripLabel1.Overflow = _  
        System.Windows.Forms.ToolStripItemOverflow.Never  
    ToolStripComboBox1.Overflow = _  
        System.Windows.Forms.ToolStripItemOverflow.Never  
    ```  
  
    ```csharp  
    toolStripLabel1.Overflow = _  
        System.Windows.Forms.ToolStripItemOverflow.Never  
    toolStripComboBox1.Overflow = System.Windows.Forms.ToolStripItemOverflow.Never  
  
    ```  
  
3.  Ajoutez des mots à la collection Items du contrôle <xref:System.Windows.Forms.ToolStripComboBox>.  
  
    ```vb  
    ToolStripComboBox1.Items.AddRange(New Object() {"First Item", _  
        "Second Item", "Third Item"})  
  
    ```  
  
    ```csharp  
    toolStripComboBox1.Items.AddRange(new object[] {"First item", "Second item", "Third item"});  
  
    ```  
  
4.  Affectez à la propriété de la zone de liste déroulante <xref:System.Windows.Forms.ComboBox.AutoCompleteMode%2A> la valeur <xref:System.Windows.Forms.AutoCompleteMode>.  
  
    ```vb  
    ToolStripComboBox1.AutoCompleteMode = _  
        System.Windows.Forms.AutoCompleteMode.Append  
    ```  
  
    ```csharp  
    toolStripComboBox1.AutoCompleteMode = System.Windows.Forms.AutoCompleteMode.Append;  
  
    ```  
  
5.  Affectez à la propriété de la zone de liste déroulante <xref:System.Windows.Forms.ComboBox.AutoCompleteSource%2A> la valeur <xref:System.Windows.Forms.AutoCompleteSource>.  
  
    ```vb  
    ToolStripComboBox1.AutoCompleteSource = _  
        System.Windows.Forms.AutoCompleteSource.ListItems  
    ```  
  
    ```csharp  
    toolStripComboBox1.AutoCompleteSource = System.Windows.Forms.AutoCompleteSource.ListItems;  
  
    ```  
  
## Voir aussi  
 <xref:System.Windows.Forms.ToolStrip>   
 <xref:System.Windows.Forms.ToolStripLabel>   
 <xref:System.Windows.Forms.ToolStripComboBox>   
 <xref:System.Windows.Forms.ToolStripComboBox.AutoCompleteMode%2A>   
 <xref:System.Windows.Forms.ToolStripComboBox.AutoCompleteSource%2A>   
 [Vue d'ensemble du contrôle ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)   
 [Architecture du contrôle ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md)   
 [Résumé de la technologie ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-technology-summary.md)