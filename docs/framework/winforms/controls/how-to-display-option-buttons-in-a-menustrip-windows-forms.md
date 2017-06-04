---
title: "Comment&#160;: afficher des cases d&#39;option dans un MenuStrip (Windows Forms) | Microsoft Docs"
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
  - "afficher des cases d'option, MenuStrip (Windows Forms)"
  - "MenuStrip (Windows Forms), afficher des cases d'option"
  - "cases d'option (Windows Forms), afficher dans un MenuStrip"
ms.assetid: 8b596af2-9ff8-4f7b-93d7-cba830e167f4
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# Comment&#160;: afficher des cases d&#39;option dans un MenuStrip (Windows Forms)
Les cases d'option sont semblables à des cases à cocher, mais les utilisateurs ne peuvent en sélectionner qu'une à la fois.  Bien que, par défaut, la classe <xref:System.Windows.Forms.ToolStripMenuItem> ne fournisse pas un comportement de case d'option, elle propose un comportement de case à cocher que vous pouvez personnaliser pour implémenter le comportement de case d'option pour les éléments de menu dans un contrôle <xref:System.Windows.Forms.MenuStrip>.  
  
 Lorsque la propriété <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> d'un élément de menu a la valeur `true`, les utilisateurs peuvent cliquer sur l'élément pour basculer l'affichage d'une coche.  La propriété <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> indique l'état actuel de l'élément.  Pour implémenter un comportement de case d'option de base, vous devez vous assurer que, lorsqu'un élément est sélectionné, la propriété <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> pour l'élément sélectionné précédemment a la valeur `false`.  
  
 Les procédures suivantes décrivent cette implémentation et les fonctionnalités supplémentaires dans une classe qui héritent de la classe <xref:System.Windows.Forms.ToolStripMenuItem>.  La classe `ToolStripRadioButtonMenuItem` substitue des membres, tels que <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A> et <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A>, pour fournir l'apparence et le comportement de sélection des cases d'option.  En outre, cette classe substitue la propriété <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> afin que les options d'un sous\-menu soient désactivées à moins que l'élément parent ne soit sélectionné.  
  
### Pour implémenter un comportement de sélection de case d'option  
  
1.  Affectez à la propriété <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> la valeur `true` pour activer la sélection d'élément.  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#110](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#110)]
     [!code-vb[ToolStripRadioButtonMenuItem#110](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#110)]  
  
2.  Substituez la méthode <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A> pour effacer la sélection de l'élément sélectionné précédemment lorsqu'un nouvel élément est sélectionné.  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#120](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#120)]
     [!code-vb[ToolStripRadioButtonMenuItem#120](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#120)]  
  
3.  Substituez la méthode <xref:System.Windows.Forms.ToolStripMenuItem.OnClick%2A> pour garantir qu'un clic sur un élément déjà sélectionné n'effacera pas la sélection.  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#130](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#130)]
     [!code-vb[ToolStripRadioButtonMenuItem#130](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#130)]  
  
### Pour modifier l'apparence des éléments de case d'option  
  
1.  Substituez la méthode <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> pour remplacer la coche par défaut par une case d'option en utilisant la classe <xref:System.Windows.Forms.RadioButtonRenderer>.  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#140](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#140)]
     [!code-vb[ToolStripRadioButtonMenuItem#140](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#140)]  
  
2.  Substituez les méthodes <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseEnter%2A>, <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseLeave%2A>, <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseDown%2A> et <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseUp%2A> pour effectuer le suivi de l'état de la souris et garantir que la méthode <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> peint l'état de case d'option correct.  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#150](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#150)]
     [!code-vb[ToolStripRadioButtonMenuItem#150](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#150)]  
  
### Pour désactiver les options d'un sous\-menu lorsque l'élément parent n'est pas sélectionné  
  
1.  Substituez la propriété <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> afin que l'élément soit désactivé lorsqu'il a un élément parent avec à la fois une valeur <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> de `true` et une valeur <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> de `false`.  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#160](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#160)]
     [!code-vb[ToolStripRadioButtonMenuItem#160](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#160)]  
  
2.  Substituez la méthode <xref:System.Windows.Forms.ToolStripMenuItem.OnOwnerChanged%2A> pour un abonnement à l'événement <xref:System.Windows.Forms.ToolStripMenuItem.CheckedChanged> de l'élément parent.  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#170](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#170)]
     [!code-vb[ToolStripRadioButtonMenuItem#170](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#170)]  
  
3.  Dans le gestionnaire pour l'événement <xref:System.Windows.Forms.ToolStripMenuItem.CheckedChanged> de l'élément parent, invalidez l'élément pour mettre à jour l'affichage avec le nouvel état activé.  
  
     [!code-csharp[ToolStripRadioButtonMenuItem#180](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#180)]
     [!code-vb[ToolStripRadioButtonMenuItem#180](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#180)]  
  
## Exemple  
 L'exemple de code suivant fournit la classe `ToolStripRadioButtonMenuItem` complète, une classe <xref:System.Windows.Forms.Form> et une classe `Program` pour illustrer le comportement de case d'option.  
  
 [!code-csharp[ToolStripRadioButtonMenuItem#000](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#000)]
 [!code-vb[ToolStripRadioButtonMenuItem#000](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#000)]  
  
## Compilation du code  
 Cet exemple nécessite :  
  
-   Références aux assemblys System, System.Drawing et System.Windows.Forms.  
  
## Voir aussi  
 <xref:System.Windows.Forms.MenuStrip>   
 <xref:System.Windows.Forms.ToolStripMenuItem>   
 <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.RadioButtonRenderer>   
 [MenuStrip, contrôle](../../../../docs/framework/winforms/controls/menustrip-control-windows-forms.md)   
 [Comment : implémenter un ToolStripRenderer personnalisé](../../../../docs/framework/winforms/controls/how-to-implement-a-custom-toolstriprenderer.md)