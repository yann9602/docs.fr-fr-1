---
title: "Comment : modifier l'espacement et l'alignement d'éléments ToolStrip dans les Windows Forms"
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
- ToolStrip control [Windows Forms], aligning items
- examples [Windows Forms], toolbars
- toolbars [Windows Forms], aligning items
ms.assetid: cd483466-0f49-43df-addf-e2b5fcd64027
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 58cad83b7253b71363f9ccf7fbda74e03803f381
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-change-the-spacing-and-alignment-of-toolstrip-items-in-windows-forms"></a>Comment : modifier l'espacement et l'alignement d'éléments ToolStrip dans les Windows Forms
Le <xref:System.Windows.Forms.ToolStrip> contrôle prend entièrement en charge les fonctionnalités de disposition telles que le dimensionnement, l’espacement des <xref:System.Windows.Forms.ToolStripItem> contrôle entre eux, la disposition des contrôles sur le <xref:System.Windows.Forms.ToolStrip>et l’espacement des contrôles relatif à la <xref:System.Windows.Forms.ToolStrip>.  
  
 Étant donné que la valeur par défaut de la <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> propriété est `true`, les contrôles sont dimensionnés automatiquement, sauf si vous définissez la <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> propriété `false`.  
  
### <a name="to-manually-size-a-toolstripitem"></a>Pour dimensionner manuellement un ToolStripItem  
  
1.  Définir le <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> propriété `false` pour le contrôle associé.  
  
    ```vb  
    ToolStripButton1.AutoSize = False  
    ```  
  
    ```csharp  
    toolStripButton1.AutoSize = false;  
    ```  
  
2.  Définir le <xref:System.Windows.Forms.ToolStripItem.Size%2A> propriété comme vous le souhaitez pour associé <xref:System.Windows.Forms.ToolStripItem>.  
  
### <a name="to-set-the-spacing-of-a-toolstripitem"></a>Pour définir l’espacement d’un ToolStripItem  
  
1.  Insérez les valeurs souhaitées, en pixels, dans le <xref:System.Windows.Forms.ToolStripItem.Margin%2A> propriété du contrôle associé.  
  
     Les valeurs de la <xref:System.Windows.Forms.ToolStripItem.Margin%2A> propriété spécifient l’espacement entre l’élément et les éléments adjacents dans cet ordre : gauche, haut, droite et bas.  
  
    ```vb  
    ToolStripTextBox1.Margin = New System.Windows.Forms.Padding _  
        (3, 0, 3, 0)  
    ```  
  
    ```csharp  
    toolStripTextBox1.Margin = new System.Windows.Forms.Padding   
        (3, 0, 3, 0);  
    ```  
  
### <a name="to-align-a-toolstripitem-to-the-right-side-of-the-toolstrip"></a>Pour aligner un ToolStripItem au côté droit du ToolStrip  
  
1.  Définir le <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> propriété <xref:System.Windows.Forms.ToolStripItemAlignment.Right> pour le contrôle associé. Par défaut, <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> a la valeur <xref:System.Windows.Forms.ToolStripItemAlignment.Left>, qui aligne les contrôles sur le côté gauche de la <xref:System.Windows.Forms.ToolStrip>.  
  
    ```vb  
    ToolStripSplitButton1.Alignment = _  
        System.Windows.Forms.ToolStripItemAlignment.Right  
    ```  
  
    ```csharp  
    toolStripSplitButton1.Alignment =   
        System.Windows.Forms.ToolStripItemAlignment.Right;  
    ```  
  
### <a name="to-arrange-toolstrip-items-on-the-toolstrip"></a>Pour organiser des éléments ToolStrip sur le ToolStrip  
  
-   Définir le <xref:System.Windows.Forms.ToolStrip.LayoutStyle%2A> à la valeur de propriété <xref:System.Windows.Forms.ToolStripLayoutStyle> souhaité.  
  
    ```vb  
    ToolStripDropDown1.LayoutStyle = _  
        System.Windows.Forms.ToolStripLayoutStyle.Flow  
    ```  
  
    ```csharp  
    toolStripDropDown1.LayoutStyle =   
        System.Windows.Forms.ToolStripLayoutStyle.Flow;  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.Control.Layout>  
 <xref:System.Windows.Forms.ToolStrip.LayoutCompleted>  
 <xref:System.Windows.Forms.ToolStrip.LayoutSettings%2A>  
 <xref:System.Windows.Forms.ToolStripItem.TextImageRelation%2A>  
 <xref:System.Windows.Forms.ToolStripItem.Placement%2A>  
 <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A>  
 [Vue d’ensemble du contrôle ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)  
 [Architecture du contrôle ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md)  
 [Résumé de la technologie ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-technology-summary.md)
