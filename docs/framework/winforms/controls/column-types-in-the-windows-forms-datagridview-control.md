---
title: "Types de colonnes dans le contr&#244;le DataGridView Windows Forms | Microsoft Docs"
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
  - "colonnes (Windows Forms), types"
  - "grilles de données, colonnes"
  - "DataGridView (contrôle Windows Forms), types de colonnes"
ms.assetid: f0a0a9f1-8757-4bfd-891f-d7d12870dbed
caps.latest.revision: 17
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 17
---
# Types de colonnes dans le contr&#244;le DataGridView Windows Forms
Le contrôle <xref:System.Windows.Forms.DataGridView> utilise plusieurs types de colonne pour afficher ses informations et permettre aux utilisateurs de modifier ou d'ajouter des informations.  
  
 Lorsque vous liez un contrôle <xref:System.Windows.Forms.DataGridView> et attribuez à la propriété <xref:System.Windows.Forms.DataGridView.AutoGenerateColumns%2A> la valeur `true`, les colonnes sont générées automatiquement à l'aide des types de colonne par défaut appropriés pour les types de données contenus dans la source de données liée.  
  
 Vous pouvez également créer vous\-même des instances des classes de n'importe quelle colonne et les ajouter à la collection retournée par la propriété <xref:System.Windows.Forms.DataGridView.Columns%2A>.  Vous pouvez créer ces instances pour une utilisation comme colonnes indépendantes, ou vous pouvez les lier manuellement.  Par exemple, les colonnes liées manuellement sont utiles lorsque vous souhaitez remplacer une colonne générée automatiquement d'un certain type par une colonne d'un autre type.  
  
 Le tableau suivant décrit les diverses classes Column disponibles dans le contrôle <xref:System.Windows.Forms.DataGridView>.  
  
|Classe|Description|  
|------------|-----------------|  
|<xref:System.Windows.Forms.DataGridViewTextBoxColumn>|Utilisée avec les valeurs textuelles.  Générée automatiquement lors de la création d'une liaison entre les nombres et les chaînes.|  
|<xref:System.Windows.Forms.DataGridViewCheckBoxColumn>|Utilisée avec les valeurs <xref:System.Boolean> et <xref:System.Windows.Forms.CheckState>.  Générée automatiquement lors de la création d'une liaison entre les valeurs de ces types.|  
|<xref:System.Windows.Forms.DataGridViewImageColumn>|Utilisée pour l'affichage des images.  Générée automatiquement lors de la création d'une liaison avec les tableaux d'octets, les objets <xref:System.Drawing.Image> ou les objets <xref:System.Drawing.Icon>.|  
|<xref:System.Windows.Forms.DataGridViewButtonColumn>|Utilisée pour l'affichage de boutons dans les cellules.  Non générées automatiquement lors de la création de la liaison.  Utilisée généralement sous forme de colonnes indépendantes.|  
|<xref:System.Windows.Forms.DataGridViewComboBoxColumn>|Utilisée pour l'affichage de listes déroulantes dans des cellules.  Non générées automatiquement lors de la création de la liaison.  En général liée aux données manuellement.|  
|<xref:System.Windows.Forms.DataGridViewLinkColumn>|Utilisée pour l'affichage de liens dans les cellules.  Non générées automatiquement lors de la création de la liaison.  En général liée aux données manuellement.|  
|Votre type de colonne personnalisé|Vous pouvez créer votre propre classe Column en héritant de la classe <xref:System.Windows.Forms.DataGridViewColumn> ou de l'une de ses classes dérivées pour fournir l'apparence et le comportement personnalisés, ou des contrôles hébergés.  Pour plus d'informations, consultez [Comment : personnaliser les cellules et les colonnes du contrôle DataGridView Windows Forms en étendant leur comportement et leur apparence](../../../../docs/framework/winforms/controls/customize-cells-and-columns-in-the-datagrid-by-extending-behavior.md)|  
  
 Ces types de colonne sont décrits en détail dans les sections suivantes.  
  
## DataGridViewTextBoxColumn  
 Le <xref:System.Windows.Forms.DataGridViewTextBoxColumn> est un type de colonne à usage général pour une utilisation avec les valeurs textuelles telles que les nombres et les chaînes.  En mode édition, un contrôle <xref:System.Windows.Forms.TextBox> est affiché dans la cellule active, permettant aux utilisateurs de modifier la valeur de la cellule.  
  
 Les valeurs de cellules sont converties automatiquement en chaînes pour l'affichage.  Les valeurs entrées modifiées par l'utilisateur sont analysées automatiquement pour créer une valeur de cellule du type de données approprié.  Vous pouvez personnaliser ces conversions en gérant les événements <xref:System.Windows.Forms.DataGridView.CellFormatting> et <xref:System.Windows.Forms.DataGridView.CellParsing> du contrôle <xref:System.Windows.Forms.DataGridView>.  
  
 Le type de données de valeur de la cellule d'une colonne est spécifié dans la propriété <xref:System.Windows.Forms.DataGridViewColumn.ValueType%2A> de la colonne.  
  
## DataGridViewCheckBoxColumn  
 <xref:System.Windows.Forms.DataGridViewCheckBoxColumn> est utilisé avec les valeurs <xref:System.Boolean> et <xref:System.Windows.Forms.CheckState>.  Les valeurs <xref:System.Boolean> apparaissent comme des cases à cocher à deux ou trois états, en fonction de la valeur de la propriété <xref:System.Windows.Forms.DataGridViewCheckBoxColumn.ThreeState%2A>.  Lorsque la colonne est liée aux valeurs <xref:System.Windows.Forms.CheckState>, la propriété <xref:System.Windows.Forms.DataGridViewCheckBoxColumn.ThreeState%2A> a la valeur `true` par défaut.  
  
 En général, les valeurs de cellules des cases à cocher sont destinées soit au stockage, comme toutes autres données, soit à l'exécution d'opérations en bloc.  Si vous souhaitez répondre immédiatement au clic des utilisateurs sur une cellule de case à cocher, vous pouvez gérer l'événement <xref:System.Windows.Forms.DataGridView.CellClick>, mais cet événement se produit avant la mise à jour de la valeur de la cellule.  Si vous avez besoin de la nouvelle valeur au moment du clic, l'une des options consiste à calculer ce que la valeur attendue sera selon la valeur actuelle.  Une autre approche consiste à valider immédiatement la modification et à gérer l'événement <xref:System.Windows.Forms.DataGridView.CellValueChanged> pour y répondre.  Pour valider la modification lorsque l'utilisateur clique sur la cellule, vous devez gérer l'événement <xref:System.Windows.Forms.DataGridView.CurrentCellDirtyStateChanged>.  Dans le gestionnaire, si la cellule active est une cellule de case à cocher, appelez la méthode <xref:System.Windows.Forms.DataGridView.CommitEdit%2A> et passez la valeur <xref:System.Windows.Forms.DataGridViewDataErrorContexts>.  
  
## DataGridViewImageColumn  
 Le <xref:System.Windows.Forms.DataGridViewImageColumn> est utilisé pour afficher des images.  Les colonnes d'image peuvent être remplies automatiquement à partir d'une source de données, remplies manuellement pour les colonnes indépendantes ou remplies dynamiquement dans un gestionnaire d'événement <xref:System.Windows.Forms.DataGridView.CellFormatting>.  
  
 Le remplissage automatique d'une colonne d'image à partir d'une source de données fonctionne avec les tableaux d'octets dans divers formats d'image, y compris tous les formats pris en charge par la classe <xref:System.Drawing.Image> et le format OLE Picture utilisé par Microsoft® Access et l'exemple de base de données Northwind.  
  
 Le remplissage d'une colonne d'image manuellement est utile lorsque vous souhaitez fournir les fonctionnalités d'un <xref:System.Windows.Forms.DataGridViewButtonColumn>, mais avec une apparence personnalisée.  Vous pouvez gérer l'événement <xref:System.Windows.Forms.DataGridView.CellClick?displayProperty=fullName> pour répondre aux clics dans une cellule d'image.  
  
 Le remplissage des cellules d'une colonne d'image dans un gestionnaire d'événement <xref:System.Windows.Forms.DataGridView.CellFormatting> est utile lorsque vous souhaitez fournir des images pour les valeurs calculées ou les valeurs qui n'ont pas un format image.  Par exemple, vous pouvez avoir une colonne "Risque" avec des valeurs de chaîne, telles que `"high"`, `"middle"` et `"low"` que vous souhaitez afficher comme icônes.  Alternativement, vous pouvez avoir une colonne "Image" qui contient les emplacements des images qui doivent être chargées plutôt que le contenu binaire des images.  
  
## DataGridViewButtonColumn  
 Avec le <xref:System.Windows.Forms.DataGridViewButtonColumn>, vous pouvez afficher une colonne de cellules qui contiennent des boutons.  Ceci est utile lorsque vous souhaitez fournir à vos utilisateurs un moyen facile d'exécuter des actions sur des enregistrements particuliers, comme la passation d'une commande ou l'affichage d'enregistrements enfants dans une fenêtre séparée.  
  
 Les colonnes de boutons ne sont pas générées automatiquement lors de la liaison de données avec un contrôle <xref:System.Windows.Forms.DataGridView>.  Pour utiliser des colonnes de boutons, vous devez les créer manuellement et les ajouter à la collection retournée par la propriété <xref:System.Windows.Forms.DataGridView.Columns%2A?displayProperty=fullName>.  
  
 Vous pouvez répondre aux clics des utilisateurs dans les cellules de boutons en gérant l'événement <xref:System.Windows.Forms.DataGridView.CellClick?displayProperty=fullName>.  
  
## DataGridViewComboBoxColumn  
 Avec le <xref:System.Windows.Forms.DataGridViewComboBoxColumn>, vous pouvez afficher une colonne de cellules qui contiennent des zones de liste déroulante.  Ceci est utile pour l'entrée de données dans les champs qui peuvent contenir uniquement des valeurs particulières, telles que la colonne Category de la table Products dans l'exemple de base de données Northwind.  
  
 Vous pouvez remplir la liste déroulante utilisée pour toutes les cellules de la même façon qu'une liste déroulante <xref:System.Windows.Forms.ComboBox>, soit manuellement via la collection retournée par la propriété <xref:System.Windows.Forms.DataGridViewComboBoxColumn.Items%2A>, soit en le liant à une source de données via les propriétés <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A>, <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DisplayMember%2A> et <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A>.  Pour plus d'informations, consultez [ComboBox, contrôle](../../../../docs/framework/winforms/controls/combobox-control-windows-forms.md).  
  
 Vous pouvez lier les valeurs de cellules réelles à la source de données utilisée par le contrôle <xref:System.Windows.Forms.DataGridView> en définissant la propriété <xref:System.Windows.Forms.DataGridViewColumn.DataPropertyName%2A> du <xref:System.Windows.Forms.DataGridViewComboBoxColumn?displayProperty=fullName>.  
  
 Les colonnes de zone de liste déroulante ne sont pas générées automatiquement lors de la liaison de données d'un contrôle <xref:System.Windows.Forms.DataGridView>.  Pour utiliser des colonnes de zone de liste déroulante, vous devez les créer manuellement et les ajouter à la collection retournée par la propriété <xref:System.Windows.Forms.DataGridView.Columns%2A>.  
  
## DataGridViewLinkColumn  
 Avec le <xref:System.Windows.Forms.DataGridViewLinkColumn>, vous pouvez afficher une colonne de cellules qui contiennent des liens hypertexte.  Ceci utile pour les valeurs URL dans la source de données ou en tant qu'alternative à la colonne de boutons pour les comportements spéciaux comme l'ouverture d'une fenêtre avec des enregistrements enfants.  
  
 Les colonnes de liens ne sont pas générées automatiquement lors de la liaison de données d'un contrôle <xref:System.Windows.Forms.DataGridView>.  Pour utiliser des colonnes de liens, vous devez les créer manuellement et les ajouter à la collection retournée par la propriété <xref:System.Windows.Forms.DataGridView.Columns%2A>.  
  
 Vous pouvez répondre aux clics des utilisateurs sur les liens en gérant l'événement <xref:System.Windows.Forms.DataGridView.CellContentClick>.  Cet événement est distinct des événements <xref:System.Windows.Forms.DataGridView.CellClick> et <xref:System.Windows.Forms.DataGridView.CellMouseClick>, qui se produisent lorsqu'un utilisateur clique n'importe où dans une cellule.  
  
 La classe <xref:System.Windows.Forms.DataGridViewLinkColumn> fournit plusieurs propriétés permettant de modifier l'apparence des liens avant, pendant et après un clic sur ces liens.  
  
## Voir aussi  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.DataGridViewColumn>   
 <xref:System.Windows.Forms.DataGridViewButtonColumn>   
 <xref:System.Windows.Forms.DataGridViewCheckBoxColumn>   
 <xref:System.Windows.Forms.DataGridViewComboBoxColumn>   
 <xref:System.Windows.Forms.DataGridViewImageColumn>   
 <xref:System.Windows.Forms.DataGridViewTextBoxColumn>   
 <xref:System.Windows.Forms.DataGridViewLinkColumn>   
 [DataGridView, contrôle](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)   
 [Comment : afficher des images dans les cellules du contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/how-to-display-images-in-cells-of-the-windows-forms-datagridview-control.md)   
 [Comment : utiliser des colonnes de type image dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/how-to-work-with-image-columns-in-the-windows-forms-datagridview-control.md)   
 [Personnalisation du contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)