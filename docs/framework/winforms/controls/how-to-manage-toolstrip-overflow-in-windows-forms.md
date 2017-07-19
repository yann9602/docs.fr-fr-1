---
title: "Comment&#160;: G&#233;rer le d&#233;passement de capacit&#233; de contr&#244;les ToolStrip dans les Windows Forms | Microsoft Docs"
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
  - "CanOverflow (propriété)"
  - "exemples (Windows Forms), barres d'outils"
  - "Overflow (propriété)"
  - "barres d'outils (Windows Forms), gérer le dépassement"
  - "ToolStrip (contrôle Windows Forms), gérer le dépassement"
ms.assetid: fa10e0ad-4cbf-4c0d-9082-359c2f855d4e
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# Comment&#160;: G&#233;rer le d&#233;passement de capacit&#233; de contr&#244;les ToolStrip dans les Windows Forms
Lorsque tous les éléments d'un contrôle <xref:System.Windows.Forms.ToolStrip> ne peuvent pas être contenus dans l'espace alloué, vous pouvez activer la fonctionnalité de dépassement de capacité sur le contrôle <xref:System.Windows.Forms.ToolStrip> et déterminer le comportement de dépassement de capacité de contrôles <xref:System.Windows.Forms.ToolStripItem> spécifiques.  
  
 Lorsque vous ajoutez des <xref:System.Windows.Forms.ToolStripItem> qui nécessitent davantage d'espace que l'espace alloué au contrôle <xref:System.Windows.Forms.ToolStrip> en raison de la taille actuelle du formulaire, <xref:System.Windows.Forms.ToolStripOverflowButton> apparaît automatiquement sur le contrôle <xref:System.Windows.Forms.ToolStrip>.  <xref:System.Windows.Forms.ToolStripOverflowButton> apparaît et les éléments pour lesquels le dépassement de capacité est activé sont déplacés dans le menu déroulant de dépassement de capacité.  Cela permet de personnaliser et d'affecter des priorités à la façon dont les éléments <xref:System.Windows.Forms.ToolStrip> s'ajustent aux différentes tailles de formulaire.  Vous pouvez également modifier l'aspect de vos éléments lorsqu'ils présentent un dépassement de capacité en utilisant les propriétés <xref:System.Windows.Forms.ToolStripItem.Placement%2A> et <xref:System.Windows.Forms.ToolStripOverflow.DisplayedItems%2A?displayProperty=fullName> ainsi que l'événement <xref:System.Windows.Forms.ToolStrip.LayoutCompleted>.  Si vous agrandissez le formulaire au moment du design ou de l'exécution, des éléments <xref:System.Windows.Forms.ToolStripItem> supplémentaires peuvent être affichés sur le contrôle <xref:System.Windows.Forms.ToolStrip> principal et le <xref:System.Windows.Forms.ToolStripOverflowButton> peut même disparaître jusqu'à ce que vous réduisiez la taille du formulaire.  
  
### Pour activer le dépassement de capacité sur un contrôle ToolStrip  
  
-   Vérifiez que la propriété <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A> n'a pas la valeur `false` pour le contrôle <xref:System.Windows.Forms.ToolStrip>.  La valeur par défaut est `True`.  
  
     Lorsque <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A> a la valeur `True` \(valeur par défaut\), un élément <xref:System.Windows.Forms.ToolStripItem> est envoyé au menu déroulant de dépassement de capacité lorsque le contenu de l'élément <xref:System.Windows.Forms.ToolStripItem> dépasse la largeur d'un <xref:System.Windows.Forms.ToolStrip> horizontal ou la hauteur d'un <xref:System.Windows.Forms.ToolStrip> vertical.  
  
### Pour spécifier le comportement de dépassement de capacité d'un ToolStripItem spécifique  
  
-   Affectez la valeur souhaitée à la propriété <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> de l'élément <xref:System.Windows.Forms.ToolStripItem>.  Les possibilités sont `Always`, `Never` et `AsNeeded`.  par défaut est `AsNeeded`.  
  
    ```vb  
    toolStripTextBox1.Overflow = _  
    System.Windows.Forms.ToolStripItemOverflow.Never  
  
    ```  
  
    ```csharp  
    toolStripTextBox1.Overflow = _  
    System.Windows.Forms.ToolStripItemOverflow.Never;  
  
    ```  
  
## Voir aussi  
 <xref:System.Windows.Forms.ToolStrip>   
 <xref:System.Windows.Forms.ToolStripOverflowButton>   
 <xref:System.Windows.Forms.ToolStripItem.Overflow%2A>   
 <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A>   
 [Vue d'ensemble du contrôle ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)   
 [Architecture du contrôle ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md)   
 [Résumé de la technologie ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-technology-summary.md)