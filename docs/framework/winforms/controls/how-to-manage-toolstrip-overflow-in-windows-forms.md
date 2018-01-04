---
title: "Comment : Gérer le dépassement de capacité de contrôles ToolStrip dans les Windows Forms"
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
- ToolStrip control [Windows Forms], managing overflow
- toolbars [Windows Forms], managing overflow
- examples [Windows Forms], toolbars
- CanOverflow property
ms.assetid: fa10e0ad-4cbf-4c0d-9082-359c2f855d4e
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 619c4832626693a56280c70af3ade5dbb9e9d4de
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-manage-toolstrip-overflow-in-windows-forms"></a>Comment : Gérer le dépassement de capacité de contrôles ToolStrip dans les Windows Forms
Lorsque tous les éléments sur un <xref:System.Windows.Forms.ToolStrip> contrôle ne tiennent pas dans l’espace alloué, vous pouvez activer la fonctionnalité de dépassement sur les <xref:System.Windows.Forms.ToolStrip> et déterminent le comportement de dépassement de capacité de spécifiques <xref:System.Windows.Forms.ToolStripItem>s.  
  
 Lorsque vous ajoutez <xref:System.Windows.Forms.ToolStripItem>qui requièrent davantage d’espace est alloué à la <xref:System.Windows.Forms.ToolStrip> étant donné la taille du formulaire en cours, une <xref:System.Windows.Forms.ToolStripOverflowButton> apparaît automatiquement dans le <xref:System.Windows.Forms.ToolStrip>. Le <xref:System.Windows.Forms.ToolStripOverflowButton> s’affiche, et activé de dépassement de capacité des éléments sont déplacés dans le menu de dépassement de capacité de liste déroulante. Cela vous permet de personnaliser et de hiérarchiser comment votre <xref:System.Windows.Forms.ToolStrip> éléments s’ajustent aux différentes tailles de formulaire. Vous pouvez également modifier l’apparence de vos éléments lorsqu’elles se trouvent dans le dépassement de capacité à l’aide de la <xref:System.Windows.Forms.ToolStripItem.Placement%2A> et <xref:System.Windows.Forms.ToolStripOverflow.DisplayedItems%2A?displayProperty=nameWithType> propriétés et le <xref:System.Windows.Forms.ToolStrip.LayoutCompleted> événement. Si vous agrandissez le formulaire au moment du design ou au moment de l’exécution, plus <xref:System.Windows.Forms.ToolStripItem>peuvent être affichés sur le principal <xref:System.Windows.Forms.ToolStrip> et <xref:System.Windows.Forms.ToolStripOverflowButton> peut même disparaître jusqu'à ce que vous réduisez la taille du formulaire.  
  
### <a name="to-enable-overflow-on-a-toolstrip-control"></a>Pour activer le dépassement de capacité sur un contrôle ToolStrip  
  
-   Vérifiez que le <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A> propriété n’est pas définie sur `false` pour le <xref:System.Windows.Forms.ToolStrip>. La valeur par défaut est `True`.  
  
     Lorsque <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A> est `True` (la valeur par défaut), un <xref:System.Windows.Forms.ToolStripItem> est envoyé dans le menu de dépassement de capacité de liste déroulante lorsque le contenu de la <xref:System.Windows.Forms.ToolStripItem> dépasse la largeur d’un bouton horizontal <xref:System.Windows.Forms.ToolStrip> ou la hauteur d’un vertical <xref:System.Windows.Forms.ToolStrip>.  
  
### <a name="to-specify-overflow-behavior-of-a-specific-toolstripitem"></a>Pour spécifier le comportement de dépassement de capacité d’un ToolStripItem spécifique  
  
-   Définir le <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> propriété de la <xref:System.Windows.Forms.ToolStripItem> la valeur souhaitée. Les possibilités sont `Always`, `Never`, et `AsNeeded`. Le defaultis `AsNeeded`.  
  
    ```vb  
    toolStripTextBox1.Overflow = _  
    System.Windows.Forms.ToolStripItemOverflow.Never  
    ```  
  
    ```csharp  
    toolStripTextBox1.Overflow = _  
    System.Windows.Forms.ToolStripItemOverflow.Never;  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.ToolStripOverflowButton>  
 <xref:System.Windows.Forms.ToolStripItem.Overflow%2A>  
 <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A>  
 [Vue d’ensemble du contrôle ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)  
 [Architecture du contrôle ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md)  
 [Résumé de la technologie ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-technology-summary.md)
