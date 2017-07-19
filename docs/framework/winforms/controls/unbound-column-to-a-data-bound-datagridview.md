---
title: "Comment&#160;: ajouter une colonne ind&#233;pendante &#224; un contr&#244;le DataGridView Windows Forms li&#233; aux donn&#233;es | Microsoft Docs"
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
  - "colonnes (Windows Forms), données indépendantes"
  - "grilles de données, ajouter des colonnes indépendantes"
  - "DataGridView (contrôle Windows Forms), données indépendantes"
ms.assetid: f7bdc4d8-ba8e-421b-ad62-82d936f01372
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# Comment&#160;: ajouter une colonne ind&#233;pendante &#224; un contr&#244;le DataGridView Windows Forms li&#233; aux donn&#233;es
Les données que vous affichez dans le contrôle <xref:System.Windows.Forms.DataGridView> proviennent normalement d'une source de données quelconque. Vous pouvez toutefois vouloir afficher une colonne de données qui ne provienne pas de la source de données.  Ce type de colonne est appelé colonne indépendante.  Les colonnes indépendantes peuvent prendre de nombreuses formes.  Souvent, elles sont utilisées pour fournir un accès aux détails d'une ligne de données.  
  
 L'exemple de code suivant montre comment créer une colonne indépendante de boutons **Détails** pour afficher une table enfant liée à une ligne particulière d'une table parent quand vous implémentez un scénario maître\/détail.  Pour répondre aux clics de bouton, implémentez un gestionnaire d'événements <xref:System.Windows.Forms.DataGridView.CellClick?displayProperty=fullName> qui affiche un formulaire contenant la table enfant.  
  
 Cette tâche est prise en charge dans Visual Studio.  Voir également [Comment : ajouter et supprimer des colonnes dans le contrôle DataGridView Windows Forms à l'aide du concepteur](http://msdn.microsoft.com/library/dyyesckz\(v=vs.110\)).  
  
## Exemple  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#010](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#010)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#010](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#010)]  
  
## Compilation du code  
 Cet exemple nécessite :  
  
-   un contrôle <xref:System.Windows.Forms.DataGridView> nommé `dataGridView1` ;  
  
-   des références aux assemblys <xref:System?displayProperty=fullName> et <xref:System.Windows.Forms?displayProperty=fullName>.  
  
## Voir aussi  
 <xref:System.Windows.Forms.DataGridView>   
 [Affichage des données dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)   
 [Modes d'affichage des données dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/data-display-modes-in-the-windows-forms-datagridview-control.md)