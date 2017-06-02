---
title: "Comment&#160;: sp&#233;cifier des valeurs par d&#233;faut pour les nouvelles lignes dans le contr&#244;le DataGridView Windows Forms | Microsoft Docs"
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
  - "grilles de données, valeurs par défaut pour les nouvelles lignes"
  - "DataGridView (contrôle Windows Forms), entrée de données"
  - "DataGridView (contrôle Windows Forms), valeurs par défaut pour les nouvelles lignes"
  - "lignes, spécifier les valeurs par défaut"
ms.assetid: 8d127963-d9f8-4e4e-9f7f-beb66688f1f2
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# Comment&#160;: sp&#233;cifier des valeurs par d&#233;faut pour les nouvelles lignes dans le contr&#244;le DataGridView Windows Forms
Vous pouvez rendre les entrées de données plus commodes lorsque l'application remplace des valeurs par défaut par de nouvelles lignes ajoutées.  Avec la classe <xref:System.Windows.Forms.DataGridView>, vous pouvez remplir des valeurs par défaut avec l'événement <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded>.  Cet événement est déclenché lorsque l'utilisateur entre la ligne pour les nouveaux enregistrements.  Lorsque votre code gère cet événement, vous pouvez remplir les cellules voulues avec les valeurs de votre choix.  
  
 L'exemple de code suivant montre comment spécifier des valeurs par défaut pour les nouvelles lignes à l'aide de l'événement <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded>.  
  
## Exemple  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#120](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#120)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#120](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#120)]  
  
## Compilation du code  
 Cet exemple nécessite :  
  
-   un contrôle <xref:System.Windows.Forms.DataGridView> nommé `dataGridView1` ;  
  
-   Une fonction `NewCustomerId` pour générer des valeurs `CustomerID` uniques.  
  
-   Références aux assemblys <xref:System?displayProperty=fullName> et <xref:System.Windows.Forms?displayProperty=fullName>.  
  
## Voir aussi  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded?displayProperty=fullName>   
 [Saisie de données dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/data-entry-in-the-windows-forms-datagridview-control.md)   
 [Utilisation de la ligne pour les nouveaux enregistrements dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md)