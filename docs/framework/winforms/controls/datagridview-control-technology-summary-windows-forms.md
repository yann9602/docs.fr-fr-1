---
title: "R&#233;sum&#233; de la technologie du contr&#244;le DataGridView (Windows Forms) | Microsoft Docs"
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
  - "grilles de données, à propos des grilles de données"
  - "DataGridView (contrôle Windows Forms), à propos du contrôle DataGridView"
ms.assetid: 094498c3-a126-4a3f-83fe-f69e96c7717b
caps.latest.revision: 17
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 17
---
# R&#233;sum&#233; de la technologie du contr&#244;le DataGridView (Windows Forms)
Cette rubrique résume les informations relatives au contrôle `DataGridView` et aux classes qui le prennent en charge.  
  
 Afficher des données sous forme de tableau est une tâche que vous êtes susceptible d'effectuer fréquemment.  Le contrôle `DataGridView` est conçu pour être une solution complète de présentation des données dans une grille.  
  
## Mots clés  
 DataGridView, BindingSource, table, cellule, liaison de données, mode virtuel  
  
## Espaces de noms  
 <xref:System.Windows.Forms?displayProperty=fullName>  
  
 <xref:System.Data?displayProperty=fullName>  
  
## Technologies associées  
 `BindingSource`  
  
## Background  
 Les concepteurs d'interfaces utilisateur trouvent souvent nécessaire d'afficher des données sous forme de tableau pour les utilisateurs.  Le [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] offre plusieurs moyens d'afficher des données dans une table ou une grille.  Le contrôle `DataGridView` représente l'évolution la plus récente de cette technologie pour les applications Windows Forms.  
  
 Le contrôle `DataGridView` peut afficher des lignes de données d'un magasin de données.  De nombreux types de magasins de données sont pris en charge.  Le magasin de données peut contenir des données simples, non typées, comme un tableau unidimensionnel, ou contenir des données typées, comme un <xref:System.Data.DataSet>.  Pour plus d'informations, consultez [Comment : lier des données au contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/how-to-bind-data-to-the-windows-forms-datagridview-control.md).  
  
 Le contrôle `DataGridView` offre un moyen puissant et flexible d'afficher des données sous forme de tableau.  Vous pouvez utiliser le contrôle pour afficher des groupes de données très petits ou très grands, dans des vues modifiables ou en lecture seule.  
  
 Vous pouvez étendre le contrôle `DataGridView` de plusieurs manières pour générer un comportement personnalisé dans vos applications.  Par exemple, vous pouvez spécifier par programme vos propres algorithmes de tri, et vous pouvez créer vos propres types de cellules.  Vous pouvez facilement personnaliser l'apparence du contrôle `DataGridView` en choisissant parmi plusieurs propriétés.  De nombreux types de magasins de données peuvent être utilisés comme source de données, mais le contrôle `DataGridView` peut fonctionner sans source de données liée à lui.  
  
## Implémentation de classes DataGridView  
 Il existe plusieurs manières de tirer parti des fonctionnalités d'extensibilité du contrôle `DataGridView`.  Vous pouvez personnaliser de nombreux aspects du contrôle à travers des événements et des propriétés, mais certaines personnalisations nécessitent que vous créiez de nouvelles classes, dérivées de classes `DataGridView` existantes.  
  
 Les classes de base les plus fréquemment utilisées sont `DataGridViewCell` et `DataGridViewColumn`.  Vous pouvez dériver votre propre classe de cellule de `DataGridViewCell` ou de n'importe laquelle de ses classes enfants.  Bien que vous puissiez ajouter n'importe quel type de cellule à n'importe quelle colonne, vous dériverez en général également une classe Column auxiliaire de `DataGridViewColumn` qui héberge des cellules de votre type de cellule personnalisé par défaut.  
  
 Vous pouvez implémenter l'interface `IDataGridViewEditingCell` dans votre classe de cellule dérivée pour créer un type de cellule qui dispose de la fonctionnalité d'édition mais n'héberge pas de contrôle en mode édition.  Pour créer un contrôle que vous pouvez héberger dans une cellule en mode édition, vous pouvez implémenter l'interface `IDataGridViewEditingControl` dans une classe dérivée de <xref:System.Windows.Forms.Control>.  
  
 Pour plus d'informations, consultez [Comment : personnaliser les cellules et les colonnes du contrôle DataGridView Windows Forms en étendant leur comportement et leur apparence](../../../../docs/framework/winforms/controls/customize-cells-and-columns-in-the-datagrid-by-extending-behavior.md) et [Comment : héberger des contrôles dans des cellules DataGridView Windows Forms](../../../../docs/framework/winforms/controls/how-to-host-controls-in-windows-forms-datagridview-cells.md).  
  
## Présentation des classes DataGridView en un clin d'œil  
 <xref:System.Windows.Forms>  
  
|Zone technologique|Classes\/interfaces\/éléments de configuration|  
|------------------------|----------------------------------------------------|  
|Liaison de données|<xref:System.Windows.Forms.BindingSource>|  
|Présentation des données|<xref:System.Windows.Forms.DataGridView><br /><br /> <xref:System.Windows.Forms.DataGridViewCell> et classes dérivées<br /><br /> <xref:System.Windows.Forms.DataGridViewRow> et classes dérivées<br /><br /> <xref:System.Windows.Forms.DataGridViewColumn> et classes dérivées<br /><br /> <xref:System.Windows.Forms.DataGridViewCellStyle>|  
|Extensibilité <xref:System.Windows.Forms.DataGridView>|<xref:System.Windows.Forms.DataGridViewCell> et classes dérivées<br /><br /> <xref:System.Windows.Forms.DataGridViewColumn> et classes dérivées<br /><br /> <xref:System.Windows.Forms.IDataGridViewEditingCell><br /><br /> <xref:System.Windows.Forms.IDataGridViewEditingControl>|  
  
## Nouveautés  
 Le contrôle <xref:System.Windows.Forms.DataGridView> est conçu pour être une solution complète d'affichage des données sous forme de tableau avec Windows Forms.  Vous devez envisager d'utiliser le contrôle <xref:System.Windows.Forms.DataGridView> avant d'autres solutions, telles que <xref:System.Windows.Forms.DataGrid>, lorsque vous créez une nouvelle application.  Pour plus d'informations, consultez [Différences entre les contrôles DataGridView et DataGrid Windows Forms](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Le contrôle <xref:System.Windows.Forms.DataGridView> peut fonctionner en étroite collaboration avec le composant <xref:System.Windows.Forms.BindingSource>.  Ce composant est conçu pour être la source des données principale d'un formulaire.  Il peut gérer l'interaction entre un contrôle <xref:System.Windows.Forms.DataGridView> et sa source de données, indépendamment du type de la source de données.  
  
## Voir aussi  
 [Vue d'ensemble du contrôle DataGridView](../../../../docs/framework/winforms/controls/datagridview-control-overview-windows-forms.md)   
 [Architecture du contrôle DataGridView](../../../../docs/framework/winforms/controls/datagridview-control-architecture-windows-forms.md)   
 [Protection des informations de connexion](../../../../docs/framework/data/adonet/protecting-connection-information.md)