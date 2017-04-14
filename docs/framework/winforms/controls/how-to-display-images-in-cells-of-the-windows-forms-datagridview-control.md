---
title: "Comment&#160;: afficher des images dans les cellules du contr&#244;le DataGridView Windows Forms | Microsoft Docs"
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
  - "cellules, afficher des images"
  - "grilles de données, afficher des images dans les cellules"
  - "grilles de données, afficher dans les grilles"
  - "DataGridView (contrôle Windows Forms), afficher des images"
ms.assetid: 53b13d31-1b56-476d-9ab4-18bfac138a22
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# Comment&#160;: afficher des images dans les cellules du contr&#244;le DataGridView Windows Forms
Une image ou un graphique est l'une des valeurs que vous pouvez afficher dans une ligne de données.  Fréquemment, ces graphiques prennent la forme d'une photographie de salarié ou d'un logo de société.  
  
 L'incorporation d'images est simple lorsque vous affichez des données dans le contrôle <xref:System.Windows.Forms.DataGridView>.  Le contrôle <xref:System.Windows.Forms.DataGridView> gère en mode natif tout format d'image pris en charge par la classe <xref:System.Drawing.Image>, ainsi que le format d'image OLE utilisé par certaines bases de données.  
  
 Si la source de données du contrôle <xref:System.Windows.Forms.DataGridView> a une colonne d'images, celles\-ci seront affichées automatiquement par le contrôle <xref:System.Windows.Forms.DataGridView>.  
  
 L'exemple de code suivant illustre comment extraire une icône d'une ressource incorporée et la convertir en une bitmap pour l'affichage dans chaque cellule d'une colonne d'images.  Pour un autre exemple qui remplace des valeurs de cellules textuelles par les images correspondantes, consultez [Comment : personnaliser la mise en forme des données dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).  
  
## Exemple  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#050](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#050)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#050](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#050)]  
  
## Compilation du code  
 Cet exemple nécessite :  
  
-   un contrôle <xref:System.Windows.Forms.DataGridView> nommé `dataGridView1` ;  
  
-   Une ressource d'icône incorporée nommée `tree.ico`.  
  
-   Références aux assemblys <xref:System?displayProperty=fullName>, <xref:System.Windows.Forms?displayProperty=fullName> et <xref:System.Drawing?displayProperty=fullName>.  
  
## Voir aussi  
 <xref:System.Windows.Forms.DataGridView>   
 [Fonctionnalités de base liées aux colonnes, lignes et cellules dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/basic-column-row-and-cell-features-wf-datagridview-control.md)   
 [Comment : personnaliser la mise en forme des données dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)