---
title: "Comment : activer la saisie semi-automatique dans les contrôles ToolStrip dans les Windows Forms"
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
helpviewer_keywords:
- AutoComplete [Windows Forms], examples
- toolbars [Windows Forms], AutoComplete
- examples [Windows Forms], toolbars
- AutoComplete [Windows Forms], enabling in toolbars
- ToolStripComboBox class [Windows Forms], examples
- ToolStrip control [Windows Forms], AutoComplete
ms.assetid: fd66d085-1af1-45d4-930a-cde944da2e16
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ac74e50eb6558c38d46714dd7bfe0cfd61133ac8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-enable-autocomplete-in-toolstrip-controls-in-windows-forms"></a>Comment : activer la saisie semi-automatique dans les contrôles ToolStrip dans les Windows Forms
La procédure suivante combine un <xref:System.Windows.Forms.ToolStripLabel> avec un <xref:System.Windows.Forms.ToolStripComboBox> qui peut être déplacé vers le bas pour afficher une liste d’éléments, tels que récemment visité des sites Web. Si l’utilisateur tape un caractère qui correspond au premier caractère d’un des éléments dans la liste, l’élément apparaît immédiatement.  
  
> [!NOTE]
>  La saisie semi-automatique fonctionne avec `ToolStrip` de la même façon qu’il fonctionne avec les contrôles traditionnels, tels que les contrôles <xref:System.Windows.Forms.ComboBox> et <xref:System.Windows.Forms.TextBox>.  
  
### <a name="to-enable-autocomplete-in-a-toolstrip-control"></a>Pour activer la saisie semi-automatique dans un contrôle ToolStrip  
  
1.  Créer un <xref:System.Windows.Forms.ToolStrip> contrôler et ajouter des éléments.  
  
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
  
2.  Définir le <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> propriété de l’étiquette et la zone de liste déroulante <xref:System.Windows.Forms.ToolStripItemOverflow.Never> afin que la liste est toujours disponible, la taille du formulaire.  
  
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
  
3.  Ajouter des mots à la collection d’éléments de la <xref:System.Windows.Forms.ToolStripComboBox> contrôle.  
  
    ```vb  
    ToolStripComboBox1.Items.AddRange(New Object() {"First Item", _  
        "Second Item", "Third Item"})  
    ```  
  
    ```csharp  
    toolStripComboBox1.Items.AddRange(new object[] {"First item", "Second item", "Third item"});  
    ```  
  
4.  Définir le <xref:System.Windows.Forms.ComboBox.AutoCompleteMode%2A> propriété de la zone de liste déroulante <xref:System.Windows.Forms.AutoCompleteMode.Append>.  
  
    ```vb  
    ToolStripComboBox1.AutoCompleteMode = _  
        System.Windows.Forms.AutoCompleteMode.Append  
    ```  
  
    ```csharp  
    toolStripComboBox1.AutoCompleteMode = System.Windows.Forms.AutoCompleteMode.Append;  
    ```  
  
5.  Définir le <xref:System.Windows.Forms.ComboBox.AutoCompleteSource%2A> propriété de la zone de liste déroulante <xref:System.Windows.Forms.AutoCompleteSource.ListItems>.  
  
    ```vb  
    ToolStripComboBox1.AutoCompleteSource = _  
        System.Windows.Forms.AutoCompleteSource.ListItems  
    ```  
  
    ```csharp  
    toolStripComboBox1.AutoCompleteSource = System.Windows.Forms.AutoCompleteSource.ListItems;  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.ToolStripLabel>  
 <xref:System.Windows.Forms.ToolStripComboBox>  
 <xref:System.Windows.Forms.ToolStripComboBox.AutoCompleteMode%2A>  
 <xref:System.Windows.Forms.ToolStripComboBox.AutoCompleteSource%2A>  
 [Vue d’ensemble du contrôle ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)  
 [Architecture du contrôle ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md)  
 [Résumé de la technologie ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-technology-summary.md)
