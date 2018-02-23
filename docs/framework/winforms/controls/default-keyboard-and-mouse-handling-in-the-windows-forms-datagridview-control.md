---
title: "Gestion dans le contrôle DataGridView Windows Forms de la souris et de clavier par défaut"
ms.date: 02/13/2018
ms.prod: .net-framework
ms.technology:
- dotnet-winforms
ms.topic: article
helpviewer_keywords:
- data grids [Windows Forms], mouse handling
- DataGridView control [Windows Forms], navigation keys
- keyboards [Windows Forms], default handling in DataGridView control
- DataGridView control [Windows Forms], keyboard handling
- mouse [Windows Forms], default handling in DataGridView control
- DataGridView control [Windows Forms], mouse handling
- navigation keys [Windows Forms], DataGridView control
ms.assetid: 4519b928-bfc8-4e8b-bb9c-b1e76a0ca552
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 29e8afaefd35951288a4d8f5e5df2e3b5fbc4356
ms.sourcegitcommit: 973a12d1e6962cd9a9c263fbfaad040ec8267fe9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2018
---
# <a name="default-keyboard-and-mouse-handling-in-the-windows-forms-datagridview-control"></a>Gestion dans le contrôle DataGridView Windows Forms de la souris et de clavier par défaut

Les tableaux suivants décrivent comment les utilisateurs peuvent interagir avec le <xref:System.Windows.Forms.DataGridView> contrôle via un clavier et une souris.  
  
> [!NOTE]
>  Pour personnaliser le comportement du clavier, vous pouvez gérer les événements de clavier standard tels que <xref:System.Windows.Forms.Control.KeyDown>. En mode édition, toutefois, le contrôle d’édition hébergé reçoit l’entrée au clavier et les événements de clavier ne se produisent pas pour le <xref:System.Windows.Forms.DataGridView> contrôle. Pour gérer les événements du contrôle d’édition, joignez vos gestionnaires pour le contrôle d’édition dans un <xref:System.Windows.Forms.DataGridView.EditingControlShowing> Gestionnaire d’événements. Vous pouvez également personnaliser le comportement du clavier dans un <xref:System.Windows.Forms.DataGridView> sous-classe en substituant le <xref:System.Windows.Forms.DataGridView.ProcessDialogKey%2A> et <xref:System.Windows.Forms.DataGridView.ProcessDataGridViewKey%2A> méthodes.  
  
## <a name="default-keyboard-handling"></a>Gestion de clavier par défaut  
  
### <a name="basic-navigation-and-entry-keys"></a>Touches de navigation et l’entrée de base  
  
|Clé ou combinaison de touches|Description|  
|----------------------------|-----------------|  
|BAS|Déplace le focus vers la cellule directement sous la cellule active. Si le focus est dans la dernière ligne, n’exécute aucune opération.|  
|GAUCHE|Déplace le focus vers la cellule précédente dans la ligne. Si le focus est dans la première cellule de la ligne, n’exécute aucune opération.|  
|DROITE|Déplace le focus vers la cellule suivante dans la ligne. Si le focus est dans la dernière cellule de la ligne, n’exécute aucune opération.|  
|HAUT|Déplace le focus vers la cellule juste au-dessus de la cellule active. Si le focus est dans la première ligne, n’exécute aucune opération.|  
|ORIGINE|Déplace le focus vers la première cellule de la ligne actuelle.|  
|FIN|Déplace le focus vers la dernière cellule de la ligne actuelle.|  
|Page suivante|Fait défiler le contrôle vers le bas par le nombre de lignes qui sont entièrement affichés. Déplace le focus vers la dernière ligne affichée entièrement sans modifier les colonnes.|  
|Page précédente|Fait défiler le contrôle vers le haut par le nombre de lignes qui sont entièrement affichés. Déplace le focus sur la première ligne affichée sans modifier les colonnes.|  
|TAB|Si le <xref:System.Windows.Forms.DataGridView.StandardTab%2A> valeur de propriété est `false`, déplace le focus vers la cellule suivante dans la ligne actuelle. Si le focus se trouve déjà dans la dernière cellule de la ligne, déplace le focus vers la première cellule de la ligne suivante. Si le focus est dans la dernière cellule dans le contrôle, déplace le focus vers le contrôle suivant dans l’ordre de tabulation du conteneur parent.<br /><br /> Si le <xref:System.Windows.Forms.DataGridView.StandardTab%2A> valeur de propriété est `true`, déplace le focus vers le contrôle suivant dans l’ordre de tabulation du conteneur parent.|  
|MAJ+TAB|Si le <xref:System.Windows.Forms.DataGridView.StandardTab%2A> valeur de propriété est `false`, déplace le focus vers la cellule précédente dans la ligne actuelle. Si le focus se trouve déjà dans la première cellule de la ligne, déplace le focus vers la dernière cellule de la ligne précédente. Si le focus est dans la première cellule dans le contrôle, déplace le focus au contrôle précédent dans l’ordre de tabulation du conteneur parent.<br /><br /> Si le <xref:System.Windows.Forms.DataGridView.StandardTab%2A> valeur de propriété est `true`, déplace le focus vers le contrôle précédent dans l’ordre de tabulation du conteneur parent.|  
|CTRL+TAB|Si le <xref:System.Windows.Forms.DataGridView.StandardTab%2A> valeur de propriété est `false`, déplace le focus vers le contrôle suivant dans l’ordre de tabulation du conteneur parent.<br /><br /> Si le <xref:System.Windows.Forms.DataGridView.StandardTab%2A> valeur de propriété est `true`, déplace le focus vers la cellule suivante dans la ligne actuelle. Si le focus se trouve déjà dans la dernière cellule de la ligne, déplace le focus vers la première cellule de la ligne suivante. Si le focus est dans la dernière cellule dans le contrôle, déplace le focus vers le contrôle suivant dans l’ordre de tabulation du conteneur parent.|  
|CTRL+MAJ+TAB|Si le <xref:System.Windows.Forms.DataGridView.StandardTab%2A> valeur de propriété est `false`, déplace le focus vers le contrôle précédent dans l’ordre de tabulation du conteneur parent.<br /><br /> Si le <xref:System.Windows.Forms.DataGridView.StandardTab%2A> valeur de propriété est `true`, déplace le focus vers la cellule précédente dans la ligne actuelle. Si le focus se trouve déjà dans la première cellule de la ligne, déplace le focus vers la dernière cellule de la ligne précédente. Si le focus est dans la première cellule dans le contrôle, déplace le focus au contrôle précédent dans l’ordre de tabulation du conteneur parent.|  
|CTRL + FLÈCHE|Déplace le focus vers la cellule la plus éloignée dans la direction de la flèche.|  
|CTRL + ORIGINE|Déplace le focus vers la première cellule dans le contrôle.|  
|CTRL + FIN|Déplace le focus vers la dernière cellule dans le contrôle.|  
|CTRL + PAGE VERS LE BAS/HAUT|Identique à PG. suiv ou Pg. préc.|  
|F2|Met la cellule active en mode édition de cellule si la <xref:System.Windows.Forms.DataGridView.EditMode%2A> valeur de propriété est <xref:System.Windows.Forms.DataGridViewEditMode.EditOnF2> ou <xref:System.Windows.Forms.DataGridViewEditMode.EditOnKeystrokeOrF2>.|
|F3|Trie la colonne actuelle si le <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType> valeur de propriété est <xref:System.Windows.Forms.DataGridViewColumnSortMode.Automatic>. Il est le même qu’un clic sur l’en-tête de colonne en cours. Disponible à partir de .NET Framework 4.7.2. Pour activer cette fonctionnalité, les applications doivent cibler .NET Framework 4.7.2 ou versions ultérieures ou optez explicitement pour les améliorations d’accessibilité utilisent les commutateurs AppContext.|  
|F4|Si la cellule active est une <xref:System.Windows.Forms.DataGridViewComboBoxCell>, met la cellule en mode édition et affiche la liste déroulante.|  
|ALT + HAUT/BAS|Si la cellule active est une <xref:System.Windows.Forms.DataGridViewComboBoxCell>, met la cellule en mode édition et affiche la liste déroulante.|  
|Espace|Si la cellule active est une <xref:System.Windows.Forms.DataGridViewButtonCell>, <xref:System.Windows.Forms.DataGridViewLinkCell>, ou <xref:System.Windows.Forms.DataGridViewCheckBoxCell>, déclenche les <xref:System.Windows.Forms.DataGridView.CellClick> et <xref:System.Windows.Forms.DataGridView.CellContentClick> les événements. Si la cellule active est une <xref:System.Windows.Forms.DataGridViewButtonCell>, appuie également sur le bouton. Si la cellule active est une <xref:System.Windows.Forms.DataGridViewCheckBoxCell>, modifie également l’état d’activation.|  
|ENTRÉE|Valide toutes les modifications à la cellule active et la ligne et déplace le focus vers la cellule directement sous la cellule active. Si le focus est dans la dernière ligne, valide toutes les modifications sans déplacer le focus.|  
|ÉCHAP|Si le contrôle est en mode édition, annule la modification. Si le contrôle n’est pas en mode édition, rétablit toutes les modifications qui ont été apportées à la ligne actuelle si le contrôle est lié à une source de données qui prend en charge la modification ou le mode virtuel a été implémenté avec une portée de validation au niveau de la ligne.|  
|RETOUR ARRIÈRE|Supprime le caractère avant le point d’insertion lors de la modification d’une cellule.|  
|SUPPR|Supprime le caractère après le point d’insertion lors de la modification d’une cellule.|  
|CTRL+ENTRÉE|Valide toutes les modifications à la cellule active sans déplacer le focus. Également toute modification apportée à la ligne actuelle si le contrôle est lié à une source de données qui prend en charge le mode édition ou virtuel a été implémenté avec des validations au niveau des lignes de la validation étendue.|  
|CTRL+0|Insère un <xref:System.DBNull.Value?displayProperty=nameWithType> valeur dans la cellule active si la cellule peut être modifiée. Par défaut, la valeur d’affichage pour un <xref:System.DBNull> valeur de la cellule est la valeur de la <xref:System.Windows.Forms.DataGridViewCellStyle.NullValue%2A> propriété de la <xref:System.Windows.Forms.DataGridViewCellStyle> en vigueur pour la cellule active.|  
  
### <a name="selection-keys"></a>Touches de sélection

 Si le <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> est définie sur `false` et <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> est définie sur <xref:System.Windows.Forms.DataGridViewSelectionMode.CellSelect>, la modification de la cellule active à l’aide des touches de navigation modifie la sélection dans la nouvelle cellule. Le MAJ, CTRL et ALT enfoncées n’affectent pas ce comportement.  
  
 Si le <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> a la valeur <xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect> ou <xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>, le même comportement se produit, mais avec les ajouts suivants.  
  
|Clé ou combinaison de touches|Description|  
|----------------------------|-----------------|  
|MAJ + ESPACE|Sélectionne la ligne ou colonne complète (le même qu’un clic sur l’en-tête de ligne ou colonne).|  
|touche de navigation (touche de direction, PG accueil, fin)|Si une ligne ou colonne complète est sélectionnée, la modification de la cellule active à une nouvelle ligne ou colonne déplace la sélection vers la nouvelle ligne ou complète colonne (selon le mode de sélection).|  
  
 Si <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> a la valeur `false` et <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> a la valeur <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect> ou <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect>, la modification de la cellule active à une nouvelle ligne ou une colonne à l’aide du clavier déplace la sélection à la ligne complète ou la colonne. Le MAJ, CTRL et ALT enfoncées n’affectent pas ce comportement.  
  
 Si <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> a la valeur `true`, le comportement de navigation ne change pas, mais navigation avec le clavier tout en appuyant sur MAJ (y compris les touches CTRL + MAJ) modifiera une sélection de plusieurs cellules. Avant le début de la navigation, le contrôle marque la cellule active en tant que cellule d’ancrage. Lorsque vous naviguez tout en appuyant sur MAJ, la sélection inclut toutes les cellules entre la cellule d’ancrage et la cellule active. Autres cellules du contrôle resteront sélectionnées si elles ont été déjà sélectionnées, mais elles peuvent être désélectionnées si la navigation au clavier les place temporairement entre la cellule d’ancrage et la cellule active.  
  
 Si <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> a la valeur `true` et <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> a la valeur <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect> ou <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect>, le comportement de la cellule d’ancrage et la cellule active est la même, mais uniquement des lignes entières ou des colonnes sont sélectionnées ou désélectionnées.  
  
## <a name="default-mouse-handling"></a>Gestion de la souris par défaut
  
### <a name="basic-mouse-handling"></a>Gestion de la base de la souris
  
> [!NOTE]
>  Un clic sur une cellule avec le bouton gauche de la souris toujours modifie la cellule active. Cliquez sur une cellule avec le bouton droit de la souris pour ouvrir un menu contextuel, lorsque celle-ci est disponible.  
  
|Action de la souris|Description|  
|------------------|-----------------|  
|Bouton gauche de la souris vers le bas|Rend la cellule d’un clic sur la cellule active et déclenche le <xref:System.Windows.Forms.DataGridView.CellMouseDown?displayProperty=nameWithType> événement.|  
|Bouton gauche de la souris|Déclenche l'événement <xref:System.Windows.Forms.DataGridView.CellMouseUp?displayProperty=nameWithType>.|  
|Cliquez sur le bouton gauche de la souris|Déclenche la <xref:System.Windows.Forms.DataGridView.CellClick?displayProperty=nameWithType> et <xref:System.Windows.Forms.DataGridView.CellMouseClick?displayProperty=nameWithType> événements|  
|Bouton gauche de la souris enfoncé et faites glisser sur une cellule d’en-tête de colonne|Si le <xref:System.Windows.Forms.DataGridView.AllowUserToOrderColumns%2A?displayProperty=nameWithType> propriété est `true`, déplace la colonne afin qu’elle peut être placée dans une nouvelle position.|  
  
### <a name="mouse-selection"></a>Sélection de la souris

 Aucun comportement de sélection n’est associé avec le bouton central de la souris ou la roulette de la souris.  
  
 Si le <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> est définie sur `false` et <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> est définie sur <xref:System.Windows.Forms.DataGridViewSelectionMode.CellSelect>, le comportement suivant se produit.  
  
|Action de la souris|Description|  
|------------------|-----------------|  
|Cliquez sur le bouton gauche de la souris|Sélectionne uniquement la cellule active si l’utilisateur clique sur une cellule. Aucun comportement de sélection si l’utilisateur clique sur un en-tête de ligne ou de colonne.|  
|Cliquez sur le bouton droit de la souris|Affiche un menu contextuel si celle-ci est disponible.|  
  
 Le même comportement se produit lorsque le <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> a la valeur <xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect> ou <xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>, sauf que, selon le mode de sélection, en cliquant sur un en-tête de ligne ou de colonne est sélectionner la ligne ou colonne complète et définir la cellule active à la première cellule de la ligne ou colonne.  
  
 Si <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> a la valeur <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect> ou <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect>, cliquez sur une cellule dans une ligne ou colonne sélectionne la ligne ou colonne complète.  
  
 Si <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> a la valeur `true`, en cliquant sur une cellule tout en appuyant sur CTRL ou MAJ modifiera une sélection de plusieurs cellules.  
  
 Lorsque vous cliquez sur une cellule tout en appuyant sur CTRL, la cellule modifiera son état de sélection tandis que toutes les autres cellules conservent leur état actuel de la sélection.  
  
 Lorsque vous cliquez sur une cellule ou une série de cellules tout en appuyant sur MAJ, la sélection inclut toutes les cellules entre la cellule active et une cellule d’ancrage située à la position de la cellule active avant le premier clic. Lorsque vous cliquez et faites glisser le pointeur sur plusieurs cellules, la cellule d’ancrage est la cellule cliqué au début de l’opération de glissement. Les clics suivants tout en appuyant sur MAJ modifient la cellule active, mais pas la cellule d’ancrage. Autres cellules du contrôle resteront sélectionnées si elles ont été déjà sélectionnées, mais elles peuvent être désélectionnées si la navigation de la souris les place temporairement entre la cellule d’ancrage et la cellule active.  
  
 Si <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> a la valeur `true` et <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> a la valeur <xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect> ou <xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>, en cliquant sur un en-tête de ligne ou colonne (selon le mode de sélection) tout en appuyant sur MAJ modifiera une sélection existante de lignes ou colonnes complètes si ces un sélection existe. Dans le cas contraire, il sera effacer la sélection et démarrer une nouvelle sélection de lignes ou colonnes complètes. En cliquant sur un en-tête de ligne ou une colonne tout en appuyant sur CTRL, toutefois, ajoute ou supprime la ligne sélectionnée ou la colonne à partir de la sélection actuelle sans modifier la sélection actuelle.  
  
 Si <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> a la valeur `true` et <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> a la valeur <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect> ou <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect>, en cliquant sur une cellule tout en appuyant sur la touche MAJ ou CTRL comporte de la même manière, sauf que complète uniquement les lignes et colonnes sont affectées.  
  
## <a name="see-also"></a>Voir aussi

<xref:System.Windows.Forms.DataGridView>  
 [DataGridView, contrôle](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)
