---
title: "Comment&#160;: personnaliser la mise en forme des donn&#233;es dans le contr&#244;le DataGridView Windows Forms | Microsoft Docs"
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
  - "cellules, afficher les couleurs dans le contrôle DataGridView (Windows Forms)"
  - "couleurs, afficher dans le contrôle DataGridView (Windows Forms)"
  - "données (Windows Forms), mettre en forme dans le contrôle DataGridView"
  - "grilles de données, mettre en forme des données"
  - "DataGridView (contrôle Windows Forms), personnalisation des cellules"
  - "DataGridView (contrôle Windows Forms), styles de cellules"
  - "DataGridView (contrôle Windows Forms), modifier les couleurs des cellules"
  - "DataGridView (contrôle Windows Forms), mettre en forme des données"
  - "DataGridView (contrôle Windows Forms), substituer les valeurs des cellules pour l'affichage"
  - "Windows Forms, modifier les couleurs des cellules DataGridView"
ms.assetid: a6e72c70-ce18-425f-828d-d57be6f96ab6
caps.latest.revision: 21
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 21
---
# Comment&#160;: personnaliser la mise en forme des donn&#233;es dans le contr&#244;le DataGridView Windows Forms
L'exemple de code suivant montre comment implémenter un gestionnaire pour l'événement <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=fullName> qui modifie le mode d'affichage des cellules en fonction de leurs colonnes et de leurs valeurs.  
  
 Les cellules de la colonne `Balance` qui contiennent des nombres négatifs ont un arrière\-plan rouge.  Vous pouvez également appliquer la mise en forme « Monnaie » à ces cellules pour afficher les valeurs négatives entre parenthèses.  Pour plus d'informations, consultez [Comment : mettre en forme des données dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/how-to-format-data-in-the-windows-forms-datagridview-control.md).  
  
 Les cellules de la colonne `Priority` affichent des images au lieu des valeurs de cellules textuelles correspondantes.  La propriété <xref:System.Windows.Forms.ConvertEventArgs.Value%2A> de <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs> sert à obtenir la valeur de la cellule textuelle et à définir la valeur d'affichage d'image correspondante.  
  
## Exemple  
 [!code-csharp[System.Windows.Forms.DataGridViewCustomizeDataFormatting#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCustomizeDataFormatting/cs/customFormatting.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewCustomizeDataFormatting#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCustomizeDataFormatting/vb/customFormatting.vb#00)]  
  
## Compilation du code  
 Cet exemple nécessite :  
  
-   des références aux assemblys System, System.Drawing et System.Windows.Forms ;  
  
-   des images <xref:System.Drawing.Bitmap> nommées `highPri.bmp`, `mediumPri.bmp` et `lowPri.bmp` résidant dans le même répertoire que le fichier exécutable.  
  
 Pour plus d'informations sur la création de cet exemple à partir de la ligne de commande pour [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] ou [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], consultez [Génération à partir de la ligne de commande](../Topic/Building%20from%20the%20Command%20Line%20\(Visual%20Basic\).md) ou [Génération à partir de la ligne de commande avec csc.exe](../../../../ocs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).  Vous pouvez également générer cet exemple dans [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] en collant le code dans un nouveau projet.  Consultez également [Comment : compiler et exécuter un exemple complet de code Windows Forms à l'aide de Visual Studio](http://msdn.microsoft.com/library/Bb129228%20\(v=vs.110\)).  
  
## Voir aussi  
 <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.DataGridViewCellStyle>   
 <xref:System.Drawing.Bitmap>   
 [Affichage des données dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)   
 [Comment : mettre en forme des données dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/how-to-format-data-in-the-windows-forms-datagridview-control.md)   
 [Styles de cellules dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)   
 [Mise en forme de données dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/data-formatting-in-the-windows-forms-datagridview-control.md)