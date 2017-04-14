---
title: "Comment&#160;: sp&#233;cifier le mode &#233;dition pour le contr&#244;le DataGridView Windows Forms | Microsoft Docs"
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
  - "grilles de données, mode édition"
  - "DataGridView (contrôle Windows Forms), mode édition"
ms.assetid: 93e117e8-94c4-411b-ba31-645e475ed85c
caps.latest.revision: 17
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 17
---
# Comment&#160;: sp&#233;cifier le mode &#233;dition pour le contr&#244;le DataGridView Windows Forms
Par défaut, les utilisateurs peuvent modifier le contenu de la cellule de zone de texte <xref:System.Windows.Forms.DataGridView> actuelle en y saisissant du texte ou en appuyant sur F2.  La cellule passe en mode édition si toutes les conditions suivantes sont réunies :  
  
-   La source de données sous\-jacente prend en charge l'édition.  
  
-   Le contrôle <xref:System.Windows.Forms.DataGridView> est activé.  
  
-   La valeur de propriété <xref:System.Windows.Forms.DataGridView.EditMode%2A> n'est pas <xref:System.Windows.Forms.DataGridViewEditMode>.  
  
-   Les propriétés `ReadOnly` de la cellule, de la ligne, de la colonne et du contrôle ont toutes la valeur `false`.  
  
 En mode Édition, l'utilisateur peut modifier la valeur de la cellule et appuyer sur ENTRÉE pour valider la modification ou ÉCHAP pour rétablir la cellule à sa valeur d'origine.  
  
 Vous pouvez configurer un contrôle <xref:System.Windows.Forms.DataGridView> afin qu'une cellule passe en mode Édition dès qu'elle devient la cellule active.  Le comportement des touches ENTRÉE et ÉCHAP sont inchangées dans ce cas, mais la cellule reste en mode Édition après que la valeur a été validée ou rétablie.  Vous pouvez également configurer le contrôle afin que les cellules passent en mode Édition uniquement lorsque les utilisateurs tapent du texte dans la cellule ou uniquement lorsque les utilisateurs appuient sur F2.  Enfin, vous pouvez empêcher des cellules de passer en mode Édition, sauf lorsque vous appelez la méthode <xref:System.Windows.Forms.DataGridView.BeginEdit%2A>.  
  
### Pour modifier le mode édition d'un contrôle DataGridView  
  
-   Affectez à la propriété <xref:System.Windows.Forms.DataGridView.EditMode%2A?displayProperty=fullName> l'énumération appropriée <xref:System.Windows.Forms.DataGridViewEditMode>.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#067](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#067)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#067](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#067)]  
  
## Compilation du code  
 Cet exemple nécessite :  
  
-   un contrôle <xref:System.Windows.Forms.DataGridView> nommé `dataGridView1` ;  
  
-   Références aux assemblys <xref:System> et <xref:System.Windows.Forms>.  
  
## Voir aussi  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.DataGridView.EditMode%2A?displayProperty=fullName>   
 [Saisie de données dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/data-entry-in-the-windows-forms-datagridview-control.md)