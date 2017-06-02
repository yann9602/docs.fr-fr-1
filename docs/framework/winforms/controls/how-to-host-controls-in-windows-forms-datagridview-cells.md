---
title: "Comment&#160;: h&#233;berger des contr&#244;les dans des cellules DataGridView Windows Forms | Microsoft Docs"
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
  - "cellules, héberger des contrôles"
  - "contrôles (Windows Forms), héberger dans les cellules"
  - "DataGridView (contrôle Windows Forms), héberger les contrôles dans les cellules"
ms.assetid: e79a9d4e-64ec-41f5-93ec-f5492633cbb2
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# Comment&#160;: h&#233;berger des contr&#244;les dans des cellules DataGridView Windows Forms
Le contrôle <xref:System.Windows.Forms.DataGridView> fournit plusieurs types de colonnes, ce qui permet à vos utilisateurs d'entrer et de modifier des valeurs de plusieurs façons.  Toutefois, si ces types de colonnes ne répondent pas à vos besoins de saisie de données, vous pouvez créer vos propres types de colonnes avec des cellules qui hébergent les contrôles de votre choix.  Pour cela, vous devez définir des classes qui dérivent de <xref:System.Windows.Forms.DataGridViewColumn> et <xref:System.Windows.Forms.DataGridViewCell>.  Vous devez aussi définir une classe qui dérive de <xref:System.Windows.Forms.Control> et implémente l'interface <xref:System.Windows.Forms.IDataGridViewEditingControl>.  
  
 L'exemple de code suivant montre comment créer une colonne de calendrier.  Les cellules de cette colonne affichent des dates dans des cellules de zone de texte ordinaires, mais quand l'utilisateur modifie une cellule, un contrôle <xref:System.Windows.Forms.DateTimePicker> apparaît.  Pour éviter de devoir réimplémenter une fonctionnalité d'affichage de zone de texte, la classe `CalendarCell` dérive de la classe <xref:System.Windows.Forms.DataGridViewTextBoxCell> au lieu d'hériter directement de la classe <xref:System.Windows.Forms.DataGridViewCell>.  
  
> [!NOTE]
>  Quand vous dérivez de <xref:System.Windows.Forms.DataGridViewCell> ou <xref:System.Windows.Forms.DataGridViewColumn> et que vous ajoutez de nouvelles propriétés à la classe dérivée, veillez à substituer la méthode `Clone` pour copier les nouvelles propriétés lors des opérations de clonage.  Vous devez aussi appeler la méthode `Clone` de la classe de base pour que les propriétés de la classe de base soient copiées dans la nouvelle cellule ou colonne.  
  
## Exemple  
 [!code-csharp[System.Windows.Forms.DataGridViewCalendarColumn#000](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCalendarColumn/CS/datagridviewcalendarcolumn.cs#000)]
 [!code-vb[System.Windows.Forms.DataGridViewCalendarColumn#000](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCalendarColumn/VB/datagridviewcalendarcolumn.vb#000)]  
  
## Compilation du code  
 L'exemple suivant nécessite :  
  
-   des références aux assemblys System et System.Windows.Forms.  
  
 Pour plus d'informations sur la création de cet exemple à partir de la ligne de commande pour [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] ou [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], consultez [Génération à partir de la ligne de commande](../Topic/Building%20from%20the%20Command%20Line%20\(Visual%20Basic\).md) ou [Génération à partir de la ligne de commande avec csc.exe](../../../../ocs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).  Vous pouvez également générer cet exemple dans [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] en collant le code dans un nouveau projet.  Consultez également [Comment : compiler et exécuter un exemple complet de code Windows Forms à l'aide de Visual Studio](http://msdn.microsoft.com/library/Bb129228%20\(v=vs.110\)).  
  
## Voir aussi  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.DataGridViewColumn>   
 <xref:System.Windows.Forms.DataGridViewCell>   
 <xref:System.Windows.Forms.DataGridViewTextBoxCell>   
 <xref:System.Windows.Forms.IDataGridViewEditingControl>   
 <xref:System.Windows.Forms.DateTimePicker>   
 [Personnalisation du contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)   
 [Architecture du contrôle DataGridView](../../../../docs/framework/winforms/controls/datagridview-control-architecture-windows-forms.md)   
 [Types de colonnes dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)