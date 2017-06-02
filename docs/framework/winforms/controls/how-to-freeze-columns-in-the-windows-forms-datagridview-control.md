---
title: "Comment&#160;: figer les colonnes du contr&#244;le DataGridView Windows Forms | Microsoft Docs"
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
  - "colonnes (Windows Forms), bloquer"
  - "DataGridView (contrôle Windows Forms), colonnes toujours affichées"
  - "DataGridView (contrôle Windows Forms), bloquer les colonnes"
ms.assetid: 2ef8b1de-782e-4867-af8d-58171ab5c106
caps.latest.revision: 17
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 17
---
# Comment&#160;: figer les colonnes du contr&#244;le DataGridView Windows Forms
Quand des utilisateurs consultent des données affichées dans un contrôle Windows Forms <xref:System.Windows.Forms.DataGridView>, ils doivent parfois faire fréquemment référence à une même colonne ou un même ensemble de colonnes.  Par exemple, lors de l'affichage d'un tableau d'informations sur des clients qui contient de nombreuses colonnes, il est utile d'afficher le nom du client en permanence tout en laissant d'autres colonnes défiler à l'extérieur de la zone visible.  
  
 Pour obtenir ce comportement, vous pouvez figer des colonnes dans le contrôle.  Quand vous figez une colonne, toutes les colonnes à sa gauche \(ou à sa droite dans les scripts de droite à gauche\) sont aussi figées.  Les colonnes figées restent en place, tandis que toutes les autres colonnes peuvent défiler.  
  
> [!NOTE]
>  Si la réorganisation des colonnes est activée, les colonnes figées sont traitées comme un groupe distinct des colonnes non figées.  Les utilisateurs peuvent repositionner des colonnes dans l'un ou l'autre groupe, mais ils ne peuvent pas déplacer une colonne d'un groupe à l'autre.  
  
 La propriété <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A> d'une colonne détermine si la colonne est toujours visible dans la grille.  
  
 Cette tâche est prise en charge dans Visual Studio.  Consultez également [Comment : figer les colonnes du contrôle DataGridView Windows Forms à l'aide du concepteur](http://msdn.microsoft.com/library/717ss6s6%20\(v=vs.110\)).  
  
### Pour figer une colonne par programmation  
  
-   Affectez à la propriété <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A?displayProperty=fullName> la valeur `true`.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#061](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#061)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#061](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#061)]  
  
## Compilation du code  
 Cet exemple nécessite :  
  
-   un contrôle <xref:System.Windows.Forms.DataGridView> nommé `dataGridView1` qui contient une colonne nommée `AddToCartButton` ;  
  
-   des références aux assemblys <xref:System?displayProperty=fullName> et <xref:System.Windows.Forms?displayProperty=fullName>.  
  
## Voir aussi  
 <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView>   
 [Fonctionnalités de base liées aux colonnes, lignes et cellules dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/basic-column-row-and-cell-features-wf-datagridview-control.md)   
 [Comment : activer la réorganisation des colonnes du contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/how-to-enable-column-reordering-in-the-windows-forms-datagridview-control.md)