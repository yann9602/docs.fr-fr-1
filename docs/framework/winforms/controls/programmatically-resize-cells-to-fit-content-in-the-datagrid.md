---
title: "Comment&#160;: redimensionner des cellules par programme pour les adapter au contenu du contr&#244;le DataGridView Windows Forms | Microsoft Docs"
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
  - "cellules, redimensionner en fonction du contenu"
  - "grilles de données, redimensionner les cellules en fonction du contenu"
  - "DataGridView (contrôle Windows Forms), redimensionner les cellules"
  - "grilles, redimensionner les cellules en fonction du contenu"
ms.assetid: 63d770dc-b3f5-462b-901a-3125b2753792
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# Comment&#160;: redimensionner des cellules par programme pour les adapter au contenu du contr&#244;le DataGridView Windows Forms
Vous pouvez utiliser les méthodes du contrôle <xref:System.Windows.Forms.DataGridView> pour redimensionner des lignes, des colonnes et des en\-têtes pour qu'ils affichent leurs valeurs entières sans coupure.  Vous pouvez utiliser ces méthodes pour redimensionner des éléments <xref:System.Windows.Forms.DataGridView> quand bon vous semble.  En guise d'alternative, vous pouvez configurer le contrôle pour redimensionner automatiquement ces éléments chaque fois que le contenu est modifié.  Toutefois, cette opération peut être inefficace quand vous travaillez avec grands jeux de données ou quand vos données changent fréquemment.  Pour plus d'informations, consultez [Options de dimensionnement dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/sizing-options-in-the-windows-forms-datagridview-control.md).  
  
 En général, vous ajustez par programmation les éléments <xref:System.Windows.Forms.DataGridView> en fonction de leur contenu uniquement quand vous chargez de nouvelles données à partir d'une source de données ou quand l'utilisateur a modifié une valeur.  Cela est utile pour optimiser les performances, mais aussi quand vous souhaitez permettre aux utilisateurs de redimensionner manuellement des lignes et des colonnes avec la souris.  
  
 L'exemple de code suivant illustre les options disponibles pour le redimensionnement par programmation.  
  
## Exemple  
 [!code-cpp[System.Windows.Forms.DataGridView.ProgrammaticResizing#0](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.ProgrammaticResizing/CPP/programmaticsizing.cpp#0)]
 [!code-csharp[System.Windows.Forms.DataGridView.ProgrammaticResizing#0](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.ProgrammaticResizing/CS/programmaticsizing.cs#0)]
 [!code-vb[System.Windows.Forms.DataGridView.ProgrammaticResizing#0](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.ProgrammaticResizing/VB/programmaticsizing.vb#0)]  
  
## Compilation du code  
 Cet exemple nécessite :  
  
-   Références aux assemblys System, System.Drawing et System.Windows.Forms.  
  
 Pour plus d'informations sur la création de cet exemple à partir de la ligne de commande pour [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] ou [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], consultez [Génération à partir de la ligne de commande](../Topic/Building%20from%20the%20Command%20Line%20\(Visual%20Basic\).md) ou [Génération à partir de la ligne de commande avec csc.exe](../../../../ocs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).  Vous pouvez également générer cet exemple dans [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] en collant le code dans un nouveau projet.  Consultez également [Comment : compiler et exécuter un exemple complet de code Windows Forms à l'aide de Visual Studio](http://msdn.microsoft.com/library/Bb129228%20\(v=vs.110\)).  
  
## Voir aussi  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.DataGridView.AutoResizeColumn%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView.AutoResizeColumnHeadersHeight%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView.AutoResizeRow%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView.AutoResizeRows%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView.AutoResizeRowHeadersWidth%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridViewAutoSizeRowMode>   
 <xref:System.Windows.Forms.DataGridViewAutoSizeRowsMode>   
 <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode>   
 <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode>   
 <xref:System.Windows.Forms.DataGridViewColumnHeadersHeightSizeMode>   
 <xref:System.Windows.Forms.DataGridViewRowHeadersWidthSizeMode>   
 [Redimensionnement des colonnes et des lignes dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/resizing-columns-and-rows-in-the-windows-forms-datagridview-control.md)   
 [Options de dimensionnement dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/sizing-options-in-the-windows-forms-datagridview-control.md)   
 [Comment : redimensionner automatiquement des cellules lorsque leur contenu change dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/automatically-resize-cells-when-content-changes-in-the-datagrid.md)