---
title: "Comment&#160;: redimensionner automatiquement des cellules lorsque leur contenu change dans le contr&#244;le DataGridView Windows&#160;Forms | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "grilles de données, redimensionner les cellules automatiquement"
  - "cellules, redimensionner automatiquement"
  - "contrôle DataGridView [Windows Forms], redimensionner les cellules"
ms.assetid: 1d68934d-a04c-4b12-9e66-c856c6828131
caps.latest.revision: 19
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 19
---
# Comment&#160;: redimensionner automatiquement des cellules lorsque leur contenu change dans le contr&#244;le DataGridView Windows&#160;Forms
Vous pouvez configurer le contrôle <xref:System.Windows.Forms.DataGridView> pour redimensionner ses lignes, colonnes et en\-têtes automatiquement chaque fois que du contenu change, pour que les cellules soient toujours assez grandes pour afficher leurs valeurs sans être découpées.  
  
 Vous disposez de nombreuses options pour limiter les cellules qui sont utilisées pour déterminer les nouvelles tailles. Par exemple, vous pouvez configurer le contrôle pour redimensionner automatiquement la largeur de ses colonnes uniquement en fonction des valeurs figurant sur les lignes qui sont affichées actuellement. Vous optimiserez ainsi les opérations lors de l'utilisation d'un nombre de lignes, bien que dans ce cas vous souhaiterez peut\-être utiliser des méthodes de dimensionnement telles que <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A> pour ajuster la taille quand bon vous semble.  
  
 Pour plus d’informations sur le redimensionnement automatique, consultez [Options de dimensionnement dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/sizing-options-in-the-windows-forms-datagridview-control.md).  
  
 L'exemple de code suivant illustre les options disponibles pour le redimensionnement automatique.  
  
## Exemple  
 [!code-cpp[System.Windows.Forms.DataGridView.AutoSizing#0](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.AutoSizing/CPP/autosizing.cpp#0)]
 [!code-csharp[System.Windows.Forms.DataGridView.AutoSizing#0](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.AutoSizing/CS/autosizing.cs#0)]
 [!code-vb[System.Windows.Forms.DataGridView.AutoSizing#0](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.AutoSizing/VB/autosizing.vb#0)]  
  
## Compilation du code  
 Cet exemple nécessite :  
  
-   Références aux assemblys System, System.Drawing et System.Windows.Forms.  
  
 Pour plus d’informations sur la création de cet exemple à partir de la ligne de commande associée à [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] ou à [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], consultez les pages [Génération à partir de la ligne de commande](../Topic/Building%20from%20the%20Command%20Line%20\(Visual%20Basic\).md) ou [Génération à partir de la ligne de commande avec csc.exe](../../../../ocs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Vous pouvez également générer cet exemple dans [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] en collant le code dans un nouveau projet.  Consultez également la page [Comment : compiler et exécuter un exemple complet de code Windows Forms à l’aide de Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## Voir aussi  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.DataGridView.ColumnHeadersHeightSizeMode%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView.RowHeadersWidthSizeMode%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView.AutoSizeRowsMode%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridViewColumn.InheritedAutoSizeMode%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridViewAutoSizeRowsMode>   
 <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode>   
 <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode>   
 <xref:System.Windows.Forms.DataGridViewColumnHeadersHeightSizeMode>   
 <xref:System.Windows.Forms.DataGridViewRowHeadersWidthSizeMode>   
 [Redimensionnement des colonnes et des lignes dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/resizing-columns-and-rows-in-the-windows-forms-datagridview-control.md)   
 [Options de dimensionnement dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/sizing-options-in-the-windows-forms-datagridview-control.md)   
 [Comment : redimensionner des cellules par programme pour les adapter au contenu du contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/programmatically-resize-cells-to-fit-content-in-the-datagrid.md)