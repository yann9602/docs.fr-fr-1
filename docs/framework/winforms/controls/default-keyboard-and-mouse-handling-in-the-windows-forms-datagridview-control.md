---
title: "Gestion par d&#233;faut du clavier et de la souris dans le contr&#244;le DataGridView Windows Forms | Microsoft Docs"
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
  - "grilles de données, gestion de la souris"
  - "DataGridView (contrôle Windows Forms), gestion de claviers"
  - "DataGridView (contrôle Windows Forms), gestion de la souris"
  - "DataGridView (contrôle Windows Forms), touches de navigation"
  - "claviers, gestion par défaut dans le contrôle DataGridView"
  - "souris, gestion par défaut dans le contrôle DataGridView"
  - "touches de navigation, DataGridView (contrôle)"
ms.assetid: 4519b928-bfc8-4e8b-bb9c-b1e76a0ca552
caps.latest.revision: 19
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 19
---
# Gestion par d&#233;faut du clavier et de la souris dans le contr&#244;le DataGridView Windows Forms
Les tableaux suivants décrivent comment les utilisateurs peuvent interagir avec le contrôle <xref:System.Windows.Forms.DataGridView> par l'intermédiaire d'un clavier et d'une souris.  
  
> [!NOTE]
>  Pour personnaliser le comportement du clavier, vous pouvez gérer les événements de clavier standard, tels que <xref:System.Windows.Forms.Control.KeyDown>.  En mode Édition, toutefois, le contrôle d'édition hébergé reçoit l'entrée au clavier et les événements de clavier ne se produisent pas pour le contrôle <xref:System.Windows.Forms.DataGridView>.  Pour gérer les événements du contrôle d'édition, joignez vos gestionnaires au contrôle d'édition dans un gestionnaire d'événements <xref:System.Windows.Forms.DataGridView.EditingControlShowing>.  Vous pouvez également personnaliser le comportement du clavier dans une sous\-classe <xref:System.Windows.Forms.DataGridView> en substituant les méthodes <xref:System.Windows.Forms.DataGridView.ProcessDialogKey%2A> et <xref:System.Windows.Forms.DataGridView.ProcessDataGridViewKey%2A>.  
  
## Gestion par défaut du clavier  
  
### Touches de saisie et de navigation de base  
  
|Touche ou combinaison de touches|Description|  
|--------------------------------------|-----------------|  
|BAS|Déplace le focus vers la cellule située immédiatement au\-dessous de la cellule active.  Si le focus se trouve sur la dernière ligne, n'exécute aucune action.|  
|GAUCHE|Déplace le focus vers la cellule précédente de la ligne.  Si le focus se trouve dans la première cellule de la ligne, n'exécute aucune action.|  
|DROITE|Déplace le focus vers la cellule suivante de la ligne.  Si le focus se trouve dans la dernière cellule de la ligne, n'exécute aucune action.|  
|HAUT|Déplace le focus vers la cellule située immédiatement au\-dessus de la cellule active.  Si le focus se trouve sur la première ligne, n'exécute aucune action.|  
|DÉBUT|Déplace le focus vers la première cellule de la ligne actuelle.|  
|FIN|Déplace le focus vers la dernière cellule de la ligne actuelle.|  
|PG.SUIV|Fait défiler le contrôle vers le bas selon le nombre de lignes totalement affichées.  Déplace le focus vers la dernière ligne totalement affichée sans modifier les colonnes.|  
|PG.PRÉC|Fait défiler le contrôle vers le haut selon le nombre de lignes totalement affichées.  Déplace le focus vers la première ligne affichée sans modifier les colonnes.|  
|TAB|Si la valeur de la propriété <xref:System.Windows.Forms.DataGridView.StandardTab%2A> est `false`, déplace le focus vers la cellule suivante de la ligne actuelle.  Si le focus se trouve déjà dans la dernière cellule de la ligne, déplace le focus vers la première cellule de la ligne suivante.  Si le focus se trouve dans la dernière cellule du contrôle, déplace le focus vers le contrôle suivant dans l'ordre de tabulation du conteneur parent.<br /><br /> Si la valeur de la propriété <xref:System.Windows.Forms.DataGridView.StandardTab%2A> est `true`, déplace le focus vers le contrôle suivant dans l'ordre de tabulation du conteneur parent.|  
|MAJ\+TAB|Si la valeur de la propriété <xref:System.Windows.Forms.DataGridView.StandardTab%2A> est `false`, déplace le focus vers la cellule précédente de la ligne actuelle.  Si le focus se trouve déjà dans la première cellule de la ligne, déplace le focus vers la dernière cellule de la ligne précédente.  Si le focus se trouve dans la première cellule du contrôle, déplace le focus vers le contrôle précédent dans l'ordre de tabulation du conteneur parent.<br /><br /> Si la valeur de la propriété <xref:System.Windows.Forms.DataGridView.StandardTab%2A> est `true`, déplace le focus vers le contrôle précédent dans l'ordre de tabulation du conteneur parent.|  
|CTRL\+TAB|Si la valeur de la propriété <xref:System.Windows.Forms.DataGridView.StandardTab%2A> est `false`, déplace le focus vers le contrôle suivant dans l'ordre de tabulation du conteneur parent.<br /><br /> Si la valeur de la propriété <xref:System.Windows.Forms.DataGridView.StandardTab%2A> est `true`, déplace le focus vers la cellule suivante de la ligne actuelle.  Si le focus se trouve déjà dans la dernière cellule de la ligne, déplace le focus vers la première cellule de la ligne suivante.  Si le focus se trouve dans la dernière cellule du contrôle, déplace le focus vers le contrôle suivant dans l'ordre de tabulation du conteneur parent.|  
|CTRL\+MAJ\+TAB|Si la valeur de la propriété <xref:System.Windows.Forms.DataGridView.StandardTab%2A> est `false`, déplace le focus vers le contrôle précédent dans l'ordre de tabulation du conteneur parent.<br /><br /> Si la valeur de la propriété <xref:System.Windows.Forms.DataGridView.StandardTab%2A> est `true`, déplace le focus vers la cellule précédente de la ligne actuelle.  Si le focus se trouve déjà dans la première cellule de la ligne, déplace le focus vers la dernière cellule de la ligne précédente.  Si le focus se trouve dans la première cellule du contrôle, déplace le focus vers le contrôle précédent dans l'ordre de tabulation du conteneur parent.|  
|CTRL\+FLÈCHE|Déplace le focus vers la cellule la plus éloignée, dans la direction de la flèche.|  
|CTRL\+ORIGINE|Déplace le focus vers la première cellule du contrôle.|  
|CTRL\+FIN|Déplace le focus vers la dernière cellule du contrôle.|  
|CTRL\+PG. PRÉC\/PG. SUIV.|Identique à PG. PRÉC ou PG. SUIV.|  
|F2|Place la cellule active en mode édition de cellule si la valeur de la propriété <xref:System.Windows.Forms.DataGridView.EditMode%2A> est <xref:System.Windows.Forms.DataGridViewEditMode> ou <xref:System.Windows.Forms.DataGridViewEditMode>.|  
|F4|Si la cellule active est <xref:System.Windows.Forms.DataGridViewComboBoxCell>, place la cellule en mode édition et affiche la liste déroulante.|  
|ALT\+HAUT\/BAS|Si la cellule active est <xref:System.Windows.Forms.DataGridViewComboBoxCell>, place la cellule en mode édition et affiche la liste déroulante.|  
|ESPACE|Si la cellule active est <xref:System.Windows.Forms.DataGridViewButtonCell>, <xref:System.Windows.Forms.DataGridViewLinkCell> ou <xref:System.Windows.Forms.DataGridViewCheckBoxCell>, déclenche les événements <xref:System.Windows.Forms.DataGridView.CellClick> et <xref:System.Windows.Forms.DataGridView.CellContentClick>.  Si la cellule active est <xref:System.Windows.Forms.DataGridViewButtonCell>, appuie également sur le bouton.  Si la cellule active est <xref:System.Windows.Forms.DataGridViewCheckBoxCell>, modifie également l'état d'activation.|  
|ENTRÉE|Valide toutes les modifications apportées à la cellule et à la ligne actives, et déplace le focus vers la cellule située immédiatement au\-dessous de la cellule active.  Si le focus se trouve sur la dernière ligne, valide toutes les modifications sans déplacer le focus.|  
|ÉCHAP|Si le contrôle se trouve en mode édition, annule la modification.  Si le contrôle n'est pas en mode édition, rétablit les modifications apportées à la ligne actuelle si le contrôle est lié à une source de données qui prend en charge l'édition ou si le mode virtuel a été implémenté avec une portée de validation au niveau de la ligne.|  
|RET.ARR|Supprime le caractère situé avant le point d'insertion lors de la modification d'une cellule.|  
|DELETE|Supprime le caractère situé après le point d'insertion lors de la modification d'une cellule.|  
|CTRL\+ENTRÉE|Valide toutes les modifications apportées à la cellule active sans déplacer le focus.  Valide également les éventuelles modifications apportées à la ligne actuelle si le contrôle est lié à une source de données qui prend en charge l'édition ou si le mode virtuel a été implémenté avec une portée de validation au niveau de la ligne.|  
|CTRL\+0|Entre une valeur <xref:System.DBNull.Value?displayProperty=fullName> dans la cellule active si la cellule peut être modifiée.  Par défaut, la valeur d'affichage d'une valeur de la cellule <xref:System.DBNull> est la valeur de la propriété <xref:System.Windows.Forms.DataGridViewCellStyle.NullValue%2A> de <xref:System.Windows.Forms.DataGridViewCellStyle> appliqué à la cellule active.|  
  
### Touches de sélection  
 Si la propriété <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> a la valeur `false` et que la propriété <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> a la valeur <xref:System.Windows.Forms.DataGridViewSelectionMode>, la modification de la cellule active à l'aide des touches de navigation remplace la sélection par la nouvelle cellule.  Les touches MAJ, CTRL et ALT n'affectent pas ce comportement.  
  
 Si <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> a la valeur <xref:System.Windows.Forms.DataGridViewSelectionMode> ou <xref:System.Windows.Forms.DataGridViewSelectionMode>, le même comportement se produit, mais avec les ajouts suivants.  
  
|Touche ou combinaison de touches|Description|  
|--------------------------------------|-----------------|  
|MAJ\+ESPACE|Sélectionne la ligne ou la colonne complète \(correspond au clic sur l'en\-tête de la ligne ou de la colonne\).|  
|Touche de navigation \(touche de direction, PG. PRÉC\/PG. SUIV., DÉBUT, FIN\)|Si une ligne ou une colonne complète est sélectionnée, le remplacement de la cellule active par une nouvelle ligne ou colonne déplace la sélection vers la nouvelle ligne ou colonne complète \(selon le mode de sélection\).|  
  
 Si <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> a la valeur `false` et que <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> a la valeur <xref:System.Windows.Forms.DataGridViewSelectionMode> ou <xref:System.Windows.Forms.DataGridViewSelectionMode>, le remplacement de la cellule active par une nouvelle ligne ou colonne en utilisant le clavier déplace la sélection vers la nouvelle ligne ou colonne complète.  Les touches MAJ, CTRL et ALT n'affectent pas ce comportement.  
  
 Si <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> a la valeur `true`, le comportement de navigation ne change pas, mais la navigation avec le clavier tout en appuyant sur MAJ \(y compris CTRL\+MAJ\) modifiera une sélection de plusieurs cellules.  Avant le début de la navigation, le contrôle marque la cellule active en tant que cellule d'ancrage.  Lorsque vous naviguez tout en appuyant sur MAJ, la sélection inclut toutes les cellules situées entre la cellule d'ancrage et la cellule active.  D'autres cellules du contrôle resteront sélectionnées si elles l'étaient déjà, mais elles peuvent être désélectionnées si la navigation via le clavier les place temporairement entre la cellule d'ancrage et la cellule active.  
  
 Si <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> a la valeur `true` et <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> a la valeur <xref:System.Windows.Forms.DataGridViewSelectionMode> ou <xref:System.Windows.Forms.DataGridViewSelectionMode>, le comportement de la cellule d'ancrage et de la cellule active est le même, mais seules les lignes ou les colonnes complètes sont sélectionnées ou désélectionnées.  
  
## Gestion de souris par défaut  
  
### Gestion de souris de base  
  
> [!NOTE]
>  Le fait de cliquer sur une cellule avec le bouton gauche de la souris modifie toujours la cellule active.  Le fait de cliquer sur une cellule avec le bouton droit de la souris ouvre un menu contextuel, s'il est disponible.  
  
|Action de souris|Description|  
|----------------------|-----------------|  
|Bouton gauche de la souris enfoncé|Fait de la cellule sur laquelle est effectué un clic la cellule active et déclenche l'événement <xref:System.Windows.Forms.DataGridView.CellMouseDown?displayProperty=fullName>.|  
|Bouton gauche de la souris libéré|Déclenche l'événement <xref:System.Windows.Forms.DataGridView.CellMouseUp?displayProperty=fullName>.|  
|Clic avec le bouton gauche de la souris|Déclenche les événements <xref:System.Windows.Forms.DataGridView.CellClick?displayProperty=fullName> et <xref:System.Windows.Forms.DataGridView.CellMouseClick?displayProperty=fullName>.|  
|Bouton gauche de la souris enfoncé et opération de glisser sur une cellule d'en\-tête de colonne|Si la propriété <xref:System.Windows.Forms.DataGridView.AllowUserToOrderColumns%2A?displayProperty=fullName> a la valeur `true`, déplace la colonne afin qu'elle puisse être placée dans une nouvelle position.|  
  
### Sélection de la souris  
 Aucun comportement de sélection n'est associé au bouton du milieu de la souris ou à la roulette de la souris.  
  
 Si la propriété <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> a la valeur `false` et que la propriété <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> a la valeur <xref:System.Windows.Forms.DataGridViewSelectionMode>, le comportement suivant se produit.  
  
|Action de souris|Description|  
|----------------------|-----------------|  
|Clic avec le bouton gauche de la souris|Sélectionne uniquement la cellule active si l'utilisateur clique sur une cellule.  Aucun comportement de sélection si l'utilisateur clique sur un en\-tête de ligne ou de colonne.|  
|Clic avec le bouton droit de la souris|Affiche un menu contextuel, s'il est disponible.|  
  
 Le même comportement se produit lorsque <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> a la valeur <xref:System.Windows.Forms.DataGridViewSelectionMode> ou <xref:System.Windows.Forms.DataGridViewSelectionMode>, sauf que, selon le mode de sélection, le fait de cliquer sur un en\-tête de ligne ou de colonne sélectionne la ligne ou colonne complète et définit comme cellule active la première cellule de la ligne ou colonne.  
  
 Si <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> a la valeur <xref:System.Windows.Forms.DataGridViewSelectionMode> ou <xref:System.Windows.Forms.DataGridViewSelectionMode>, le fait de cliquer sur l'une des cellules d'une ligne ou d'une colonne sélectionne la ligne ou la colonne complète.  
  
 Si <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> a la valeur `true`, vous modifiez une sélection de plusieurs cellules en cliquant sur une cellule tout en appuyant sur la touche CTRL ou MAJ.  
  
 Lorsque vous cliquez sur une cellule tout en appuyant sur CTRL, la cellule modifiera son état de sélection alors que toutes les autres cellules conserveront leur état de sélection actuel.  
  
 Lorsque vous cliquez sur une cellule ou sur une série de cellules tout en appuyant sur MAJ, la sélection inclut toutes les cellules qui figurent entre la cellule active et une cellule d'ancrage située à la position de la cellule active avant le premier clic.  Lorsque vous cliquez et faites glisser le pointeur sur plusieurs cellules, la cellule d'ancrage est la cellule sur laquelle le clic a eu lieu au début de l'opération de glisser.  Les clics suivants tout en appuyant sur la touche MAJ modifient la cellule active, mais pas la cellule d'ancrage.  D'autres cellules du contrôle resteront sélectionnées si elles l'étaient déjà, mais elles peuvent être désélectionnées si la navigation via la souris les place temporairement entre la cellule d'ancrage et la cellule active.  
  
 Si <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> a la valeur `true` et <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> a la valeur <xref:System.Windows.Forms.DataGridViewSelectionMode> ou <xref:System.Windows.Forms.DataGridViewSelectionMode>, le fait de cliquer sur un en\-tête de ligne ou de colonne \(selon le mode de sélection\) tout en appuyant sur MAJ modifiera une sélection existante de lignes ou colonnes complètes si cette sélection existe.  Sinon, la sélection sera effacée et une nouvelle sélection de lignes ou colonnes complètes démarrera.  Toutefois, si vous cliquez sur un en\-tête de ligne ou de colonne tout en appuyant sur CTRL, cela ajoutera ou supprimera la ligne ou la colonne sur laquelle vous avez cliqué dans la sélection actuelle sans modifier par ailleurs cette dernière.  
  
 Si <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> a la valeur `true` et <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> a la valeur <xref:System.Windows.Forms.DataGridViewSelectionMode> ou <xref:System.Windows.Forms.DataGridViewSelectionMode>, et que vous cliquez sur une cellule tout en appuyant sur la touche MAJ ou CTRL, vous obtenez le même comportement, mais seules les lignes et les colonnes complètes sont affectées.  
  
## Voir aussi  
 <xref:System.Windows.Forms.DataGridView>   
 [DataGridView, contrôle](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)