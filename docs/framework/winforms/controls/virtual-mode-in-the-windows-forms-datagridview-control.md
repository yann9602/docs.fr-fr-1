---
title: "Mode virtuel dans le contr&#244;le DataGridView Windows Forms | Microsoft Docs"
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
  - "DataGridView (contrôle Windows Forms), mode virtuel"
ms.assetid: feae5d43-2848-4b1a-8ea7-77085dc415b5
caps.latest.revision: 21
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 21
---
# Mode virtuel dans le contr&#244;le DataGridView Windows Forms
Avec le mode virtuel, vous pouvez gérer l'interaction entre le contrôle <xref:System.Windows.Forms.DataGridView> et un cache de données personnalisé.  Pour implémenter le mode virtuel, attribuez à la propriété <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> la valeur `true` et gérez un ou plusieurs des événements décrits dans cette rubrique.  Vous gérerez en général au moins l'événement `CellValueNeeded`, qui permet au contrôle de rechercher les valeurs dans le cache de données.  
  
## Mode dépendant et mode virtuel  
 Le mode virtuel est nécessaire uniquement lorsque vous devez compléter ou remplacer le mode dépendant.  En mode dépendant, vous définissez la propriété <xref:System.Windows.Forms.DataGridView.DataSource%2A> et le contrôle charge automatiquement les données à partir de la source spécifiée et lui soumet les modifications de l'utilisateur.  Vous pouvez déterminer les colonnes dépendantes qui sont affichées, et la source de données elle\-même gère en général des opérations telles que le tri.  
  
## Complément du mode dépendant  
 Vous pouvez compléter le mode dépendant en affichant des colonnes indépendantes avec les colonnes dépendantes.  Ceci est appelé quelquefois le « mode mixte » et est utile pour afficher des éléments comme les valeurs calculées ou des contrôles d'interface utilisateur.  
  
 Comme les colonnes indépendantes se situent en dehors de la source de données, ils sont ignorés par les opérations de tri de la source de données.  Par conséquent, lorsque vous activez le tri en mode mixte, vous devez gérer les données indépendantes dans un cache local et implémenter le mode virtuel afin de laisser le contrôle <xref:System.Windows.Forms.DataGridView> interagir avec lui.  
  
 Pour plus d'informations sur l'utilisation du mode virtuel pour gérer les valeurs dans les colonnes indépendantes, consultez les exemples dans les rubriques de référence de la propriété <xref:System.Windows.Forms.DataGridViewCheckBoxColumn.ThreeState%2A?displayProperty=fullName> et de classe <xref:System.Windows.Forms.DataGridViewComboBoxColumn?displayProperty=fullName>.  
  
## Remplacement du mode dépendant  
 Si le mode dépendant ne répond pas vos besoins en termes de performances, vous pouvez gérer toutes vos données dans un cache personnalisé via des gestionnaires d'événements de mode virtuel.  Par exemple, vous pouvez utiliser le mode virtuel pour implémenter un mécanisme de chargement de données juste\-à\-temps qui récupère uniquement les données nécessaires d'une base de données de réseau afin d'optimiser les performances.  Ce scénario est particulièrement utile lorsque vous manipulez de grandes quantités de données sur une connexion réseau lente ou utilisez des ordinateurs clients qui disposent d'une quantité limitée de RAM ou d'espace de rangement.  
  
 Pour plus d'informations sur l'utilisation du mode virtuel dans un scénario juste\-à\-temps, consultez [Implémentation du mode virtuel avec le chargement de données juste\-à\-temps dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/implementing-virtual-mode-jit-data-loading-in-the-datagrid.md).  
  
## Événements de mode virtuel  
 Si vos données sont en lecture seule, l'événement `CellValueNeeded` peut être le seul événement que vous devrez gérer.  Les événements de mode virtuel supplémentaires vous permettent d'activer des fonctionnalités spécifiques comme les modifications des utilisateurs, l'ajout et la suppression de lignes, et les transactions de niveau de ligne.  
  
 Certains événements <xref:System.Windows.Forms.DataGridView> standard \(tels que les événements qui se produisent lorsque les utilisateurs ajoutent ou suppriment des lignes, ou lorsque des valeurs de cellules sont modifiées, analysées, validées ou mises en forme\) sont également utiles en mode virtuel.  Vous pouvez également gérer les événements qui vous laissent manipuler des valeurs qui ne sont pas généralement stockées dans une source de données liée, telles que le texte d'info\-bulle de cellule, le texte d'erreur de cellule et de ligne, les données des menus contextuels de cellule et de ligne et les données de hauteur de ligne.  
  
 Pour plus d'informations sur l'implémentation du mode virtuel pour gérer les données en lecture\/écriture avec une portée de validation au niveau de la ligne, consultez [Procédure pas à pas : implémentation du mode virtuel dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md).  
  
 Pour obtenir un exemple qui implémente le mode virtuel avec une portée de validation de niveau cellule, consultez la rubrique de référence de la propriété <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>.  
  
 Les événements suivants se produisent uniquement lorsque la propriété <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> a la valeur `true`.  
  
|Événement|Description|  
|---------------|-----------------|  
|<xref:System.Windows.Forms.DataGridView.CellValueNeeded>|Utilisé par le contrôle pour extraire une valeur de la cellule du cache de données pour l'affichage.  Cet événement se produit uniquement pour les cellules dans les colonnes indépendantes.|  
|<xref:System.Windows.Forms.DataGridView.CellValuePushed>|Utilisé par le contrôle pour valider l'entrée d'utilisateur pour une cellule dans le cache de données.  Cet événement se produit uniquement pour les cellules dans les colonnes indépendantes.<br /><br /> Appelez la méthode <xref:System.Windows.Forms.DataGridView.UpdateCellValue%2A> lors de la modification d'une valeur mise en cache en dehors d'un gestionnaire d'événements <xref:System.Windows.Forms.DataGridView.CellValuePushed> afin de faire en sorte que la valeur actuelle soit affichée dans le contrôle et appliquer tous modes de dimensionnement automatiques actuellement en vigueur.|  
|<xref:System.Windows.Forms.DataGridView.NewRowNeeded>|Utilisé par le contrôle pour indiquer le besoin pour une nouvelle ligne dans le cache de données.|  
|<xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded>|Utilisé par le contrôle pour déterminer si une ligne a des modifications non validées.|  
|<xref:System.Windows.Forms.DataGridView.CancelRowEdit>|Utilisé par le contrôle pour indiquer qu'une ligne doit être rétablie à ses valeurs mises en cache.|  
  
 Les événements suivants sont utiles en mode virtuel, mais peuvent être utilisés indépendamment du paramètre de propriété <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>.  
  
|Événements|Description|  
|----------------|-----------------|  
|<xref:System.Windows.Forms.DataGridView.UserDeletingRow><br /><br /> <xref:System.Windows.Forms.DataGridView.UserDeletedRow><br /><br /> <xref:System.Windows.Forms.DataGridView.RowsRemoved><br /><br /> <xref:System.Windows.Forms.DataGridView.RowsAdded>|Utilisés par le contrôle pour indiquer quand des lignes sont supprimées ou ajoutées, vous laissant ainsi mettre à jour le cache de données en conséquence.|  
|<xref:System.Windows.Forms.DataGridView.CellFormatting><br /><br /> <xref:System.Windows.Forms.DataGridView.CellParsing><br /><br /> <xref:System.Windows.Forms.DataGridView.CellValidating><br /><br /> <xref:System.Windows.Forms.DataGridView.CellValidated><br /><br /> <xref:System.Windows.Forms.DataGridView.RowValidating><br /><br /> <xref:System.Windows.Forms.DataGridView.RowValidated>|Utilisés par le contrôle pour mettre en forme des valeurs de cellules pour l'affichage et pour analyser et valider l'entrée d'utilisateur.|  
|<xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded>|Utilisés par le contrôle pour extraire le texte d'info\-bulle de la cellule lorsque la propriété <xref:System.Windows.Forms.DataGridView.DataSource%2A> est définie ou lorsque la propriété <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> a la valeur `true`.<br /><br /> Les info\-bulles de cellule sont affichées uniquement lorsque la valeur de propriété <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A> a la propriété `true`.|  
|<xref:System.Windows.Forms.DataGridView.CellErrorTextNeeded><br /><br /> <xref:System.Windows.Forms.DataGridView.RowErrorTextNeeded>|Utilisés par le contrôle pour extraire le texte d'erreur de cellule ou de ligne lorsque la propriété <xref:System.Windows.Forms.DataGridView.DataSource%2A> est définie ou lorsque la propriété <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> a la valeur `true`.<br /><br /> Appelez la méthode <xref:System.Windows.Forms.DataGridView.UpdateCellErrorText%2A> ou la méthode <xref:System.Windows.Forms.DataGridView.UpdateRowErrorText%2A> lorsque vous modifiez le texte d'erreur de ligne ou de cellule afin de faire en sorte que la valeur actuelle soit affichée dans le contrôle.<br /><br /> Les glyphes d'erreur de ligne et de cellule sont affichés lorsque les propriétés <xref:System.Windows.Forms.DataGridView.ShowCellErrors%2A> et <xref:System.Windows.Forms.DataGridView.ShowRowErrors%2A> ont la valeur `true`.|  
|<xref:System.Windows.Forms.DataGridView.CellContextMenuStripNeeded><br /><br /> <xref:System.Windows.Forms.DataGridView.RowContextMenuStripNeeded>|Utilisés par le contrôle pour extraire une cellule ou une ligne <xref:System.Windows.Forms.ContextMenuStrip> lorsque la propriété <xref:System.Windows.Forms.DataGridView.DataSource%2A> de contrôle est définie ou la propriété <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> a la valeur `true`.|  
|<xref:System.Windows.Forms.DataGridView.RowHeightInfoNeeded><br /><br /> <xref:System.Windows.Forms.DataGridView.RowHeightInfoPushed>|Utilisés par le contrôle pour extraire ou stocker des informations de hauteur de ligne dans le cache de données.  Appelez la méthode <xref:System.Windows.Forms.DataGridView.UpdateRowHeightInfo%2A> lors de la modification des informations de hauteur de ligne mises en cache en dehors d'un gestionnaire d'événements <xref:System.Windows.Forms.DataGridView.RowHeightInfoPushed> afin de faire en sorte que la valeur actuelle soit utilisée dans l'affichage du contrôle.|  
  
## Méthodes conseillées en mode virtuel  
 Si vous implémentez le mode virtuel afin de manipuler efficacement de grandes quantités de données, vous souhaiterez également garantir que vous travaillerez efficacement avec le contrôle <xref:System.Windows.Forms.DataGridView> lui\-même.  Pour plus d'informations sur l'utilisation efficace de styles de cellule, du dimensionnement automatique, des sélections et du partage de lignes, consultez [Meilleures pratiques pour la mise à l'échelle du contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md).  
  
## Voir aussi  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>   
 [Réglage des performances dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/performance-tuning-in-the-windows-forms-datagridview-control.md)   
 [Meilleures pratiques pour la mise à l'échelle du contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md)   
 [Procédure pas à pas : implémentation du mode virtuel dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md)   
 [Implémentation du mode virtuel avec le chargement de données juste\-à\-temps dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)