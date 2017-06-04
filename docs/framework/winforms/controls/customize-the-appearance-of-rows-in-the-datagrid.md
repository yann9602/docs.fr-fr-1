---
title: "Comment&#160;: personnaliser l&#39;apparence des lignes du contr&#244;le DataGridView Windows Forms | Microsoft Docs"
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
  - "grilles de données, personnaliser les lignes"
  - "DataGridView (contrôle Windows Forms), personnaliser les lignes"
  - "lignes, personnaliser dans le contrôle DataGridView"
ms.assetid: d40b53d2-7e7c-48c5-8570-6e79d15c3bbb
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# Comment&#160;: personnaliser l&#39;apparence des lignes du contr&#244;le DataGridView Windows Forms
Vous pouvez contrôler l'apparence des lignes <xref:System.Windows.Forms.DataGridView> en gérant l'un ou l'autre des événements <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=fullName> et <xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=fullName> \(ou les deux\).  Ces événements sont conçus pour que vous puissiez peindre uniquement ce que vous souhaitez, tout en laissant le contrôle <xref:System.Windows.Forms.DataGridView> peindre le reste.  Par exemple, si vous souhaitez peindre un arrière\-plan personnalisé, vous pouvez gérer l'événement <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=fullName> et laisser chaque cellule peindre son propre contenu de premier plan.  Vous pouvez également laisser les cellules se peindre elles\-mêmes et ajouter du contenu de premier plan personnalisé dans un gestionnaire pour l'événement <xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=fullName>.  Vous pouvez aussi désactiver la peinture des cellules et peindre tout vous\-même dans un gestionnaire d'événements <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=fullName>.  
  
 L'exemple de code suivant implémente des gestionnaires pour les deux événements pour fournir un arrière\-plan de sélection dégradé et du contenu de premier plan personnalisé qui s'étend sur plusieurs colonnes.  
  
## Exemple  
 [!code-csharp[System.Windows.Forms.DataGridViewRowPainting#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRowPainting/CS/datagridviewrowpainting.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewRowPainting#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRowPainting/VB/datagridviewrowpainting.vb#00)]  
  
## Compilation du code  
 Cet exemple nécessite :  
  
-   Références aux assemblys System, System.Drawing et System.Windows.Forms.  
  
 Pour plus d'informations sur la création de cet exemple à partir de la ligne de commande pour [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] ou [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], consultez [Génération à partir de la ligne de commande](../Topic/Building%20from%20the%20Command%20Line%20\(Visual%20Basic\).md) ou [Génération à partir de la ligne de commande avec csc.exe](../../../../ocs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).  Vous pouvez également générer cet exemple dans [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] en collant le code dans un nouveau projet.  Consultez également [Comment : compiler et exécuter un exemple complet de code Windows Forms à l'aide de Visual Studio](http://msdn.microsoft.com/library/Bb129228%20\(v=vs.110\)).  
  
## Voir aussi  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=fullName>   
 [Personnalisation du contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)   
 [Architecture du contrôle DataGridView](../../../../docs/framework/winforms/controls/datagridview-control-architecture-windows-forms.md)