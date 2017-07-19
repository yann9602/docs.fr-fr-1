---
title: "Comment&#160;: d&#233;sactiver des boutons d&#39;une colonne de boutons dans le contr&#244;le DataGridView Windows Forms | Microsoft Docs"
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
  - "boutons, désactiver dans les colonnes de boutons"
  - "grilles de données, désactiver des boutons"
  - "DataGridView (contrôle Windows Forms), désactiver les cellules de boutons"
ms.assetid: 5c344d01-013a-4a6b-8f8d-62ec9321d81e
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# Comment&#160;: d&#233;sactiver des boutons d&#39;une colonne de boutons dans le contr&#244;le DataGridView Windows Forms
Le contrôle <xref:System.Windows.Forms.DataGridView> inclut la classe <xref:System.Windows.Forms.DataGridViewButtonCell> pour l'affichage des cellules avec une interface utilisateur telle qu'un bouton.  Toutefois, <xref:System.Windows.Forms.DataGridViewButtonCell> ne permet pas de désactiver l'apparence du bouton affiché par la cellule.  
  
 L'exemple de code suivant montre comment personnaliser la classe <xref:System.Windows.Forms.DataGridViewButtonCell> pour afficher des boutons qui peuvent apparaître désactivés.  L'exemple définit un nouveau type de cellule, `DataGridViewDisableButtonCell`, qui dérive de <xref:System.Windows.Forms.DataGridViewButtonCell>.  Ce type de cellule fournit une nouvelle propriété `Enabled` qui peut prendre la valeur `false` pour dessiner un bouton désactivé dans la cellule.  L'exemple définit également un nouveau type de colonne, `DataGridViewDisableButtonColumn`, qui affiche des objets `DataGridViewDisableButtonCell`.  Pour illustrer ce nouveau type de cellule et de colonne, la valeur actuelle de chaque <xref:System.Windows.Forms.DataGridViewCheckBoxCell> dans le <xref:System.Windows.Forms.DataGridView> parent détermine si la propriété  `Enabled` du `DataGridViewDisableButtonCell` sur la même ligne est `true` ou `false`.  
  
> [!NOTE]
>  Quand vous dérivez de <xref:System.Windows.Forms.DataGridViewCell> ou <xref:System.Windows.Forms.DataGridViewColumn> et que vous ajoutez de nouvelles propriétés à la classe dérivée, veillez à substituer la méthode `Clone` pour copier les nouvelles propriétés lors des opérations de clonage.  Vous devez aussi appeler la méthode `Clone` de la classe de base pour que les propriétés de la classe de base soient copiées dans la nouvelle cellule ou colonne.  
  
## Exemple  
 [!code-csharp[System.Windows.Forms.DataGridView.DisabledButtons#0](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DisabledButtons/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.DataGridView.DisabledButtons#0](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DisabledButtons/VB/form1.vb#0)]  
  
## Compilation du code  
 Cet exemple nécessite :  
  
-   Références aux assemblys System, System.Drawing, System.Windows.Forms et System.Windows.Forms.VisualStyles.  
  
 Pour plus d'informations sur la création de cet exemple à partir de la ligne de commande pour [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] ou [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], consultez [Génération à partir de la ligne de commande](../Topic/Building%20from%20the%20Command%20Line%20\(Visual%20Basic\).md) ou [Génération à partir de la ligne de commande avec csc.exe](../../../../ocs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).  Vous pouvez également générer cet exemple dans [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] en collant le code dans un nouveau projet.  Consultez également [Comment : compiler et exécuter un exemple complet de code Windows Forms à l'aide de Visual Studio](http://msdn.microsoft.com/library/Bb129228%20\(v=vs.110\)).  
  
## Voir aussi  
 [Personnalisation du contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)   
 [Architecture du contrôle DataGridView](../../../../docs/framework/winforms/controls/datagridview-control-architecture-windows-forms.md)   
 [Types de colonnes dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)