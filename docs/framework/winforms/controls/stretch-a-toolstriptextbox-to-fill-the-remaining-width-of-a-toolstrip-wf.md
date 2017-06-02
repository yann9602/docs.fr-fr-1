---
title: "Comment&#160;: &#233;tirer un ToolStripTextBox pour remplir la largeur restante d&#39;un ToolStrip (Windows Forms) | Microsoft Docs"
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
  - "zones de texte, étirer dans un contrôle ToolStrip (Windows Forms)"
  - "ToolStrip (contrôle Windows Forms), étirer une zone de texte"
ms.assetid: 0e610fbf-85fe-414c-900c-9704a5dd5cc6
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# Comment&#160;: &#233;tirer un ToolStripTextBox pour remplir la largeur restante d&#39;un ToolStrip (Windows Forms)
Lorsque vous affectez à la propriété <xref:System.Windows.Forms.ToolStrip.Stretch%2A> d'un contrôle <xref:System.Windows.Forms.ToolStrip> la valeur `true`, le contrôle remplit son conteneur d'un bout à l'autre, et est redimensionné lorsque son conteneur l'est aussi.  Dans cette configuration, vous pouvez trouver utile d'étirer un élément dans le contrôle, tel qu'un <xref:System.Windows.Forms.ToolStripTextBox>, pour remplir l'espace disponible et redimensionner lorsque le contrôle redimensionne.  Cet étirement est utile si, par exemple, vous souhaitez obtenir un aspect et un comportement semblables à la barre d'adresses dans Microsoft® Internet Explorer.  
  
## Exemple  
 L'exemple de code suivant fournit une classe dérivée de <xref:System.Windows.Forms.ToolStripTextBox> appelée `ToolStripSpringTextBox`.  Cette classe substitue la méthode <xref:System.Windows.Forms.ToolStripTextBox.GetPreferredSize%2A> pour calculer la largeur disponible du contrôle <xref:System.Windows.Forms.ToolStrip> parent une fois que la largeur combinée de tous les autres éléments a été soustraite.  Cet exemple de code fournit également une classe <xref:System.Windows.Forms.Form> et une classe `Program` pour illustrer le nouveau comportement.  
  
 [!code-csharp[ToolStripSpringTextBox#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripSpringTextBox/cs/ToolStripSpringTextBox.cs#00)]
 [!code-vb[ToolStripSpringTextBox#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripSpringTextBox/vb/ToolStripSpringTextBox.vb#00)]  
  
## Compilation du code  
 Cet exemple nécessite :  
  
-   Références aux assemblys System, System.Drawing et System.Windows.Forms.  
  
## Voir aussi  
 <xref:System.Windows.Forms.ToolStrip>   
 <xref:System.Windows.Forms.ToolStrip.Stretch%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.ToolStripTextBox>   
 <xref:System.Windows.Forms.ToolStripTextBox.GetPreferredSize%2A?displayProperty=fullName>   
 [Architecture du contrôle ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md)   
 [Comment : utiliser la propriété Spring dans un StatusStrip de manière interactive](../../../../docs/framework/winforms/controls/how-to-use-the-spring-property-interactively-in-a-statusstrip.md)