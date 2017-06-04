---
title: "Comportement par d&#233;faut du clavier et de la souris dans le contr&#244;le DataGrid | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "DataGrid (WPF), comportement du clavier"
  - "DataGrid (WPF), comportement de la souris"
  - "comportement du clavier (WPF), DataGrid"
  - "comportement de la souris (WPF), DataGrid"
ms.assetid: 563b8854-ca39-4d97-8235-17eaa0f93c8d
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# Comportement par d&#233;faut du clavier et de la souris dans le contr&#244;le DataGrid
Cette rubrique explique comment les utilisateurs peuvent interagir avec le contrôle <xref:System.Windows.Controls.DataGrid> à l'aide du clavier et de la souris.  
  
 Les interactions standard avec <xref:System.Windows.Controls.DataGrid> comprennent la navigation, la sélection et la modification.  Le mode de sélection est affecté par les propriétés <xref:System.Windows.Controls.DataGrid.SelectionMode%2A> et <xref:System.Windows.Controls.DataGrid.SelectionUnit%2A>.  Les valeurs par défaut qui provoquent le comportement décrit dans cette rubrique sont <xref:System.Windows.Controls.DataGridSelectionMode?displayProperty=fullName> et <xref:System.Windows.Controls.DataGridSelectionUnit?displayProperty=fullName>.  Modifier ces valeurs peut provoquer un comportement différent de celui décrit.  Lorsqu'une cellule est en mode Édition, le contrôle d'édition peut remplacer le comportement standard du clavier de <xref:System.Windows.Controls.DataGrid>.  
  
## Comportement par défaut du clavier  
 Le tableau suivant répertorie le comportement par défaut du clavier pour <xref:System.Windows.Controls.DataGrid>.  
  
|Touche ou combinaison de touches|Description|  
|--------------------------------------|-----------------|  
|BAS|Déplace le focus vers la cellule située immédiatement au\-dessous de la cellule active.  Si le focus se trouve dans la dernière ligne, la touche BAS est sans effet.|  
|HAUT|Déplace le focus vers la cellule située immédiatement au\-dessus de la cellule active.  Si le focus se trouve dans la première ligne, la touche HAUT est sans effet.|  
|GAUCHE|Déplace le focus vers la cellule précédente de la ligne.  Si le focus se trouve dans la première cellule de la ligne, la touche GAUCHE est sans effet.|  
|DROITE|Déplace le focus vers la cellule suivante de la ligne.  Si le focus se trouve dans la dernière cellule de la ligne, la touche DROITE est sans effet.|  
|DÉBUT|Déplace le focus vers la première cellule de la ligne actuelle.|  
|FIN|Déplace le focus vers la dernière cellule de la ligne actuelle.|  
|PG.SUIV|Si les lignes ne sont pas regroupées, fait défiler le contrôle vers le bas selon le nombre de lignes totalement affichées.  Déplace le focus vers la dernière ligne totalement affichée sans modifier les colonnes.<br /><br /> Si les lignes sont regroupées, déplace le focus vers la dernière ligne dans <xref:System.Windows.Controls.DataGrid> sans modifier les colonnes.|  
|PG.PRÉC|Si les lignes ne sont pas regroupées, fait défiler le contrôle vers le haut selon le nombre de lignes totalement affichées.  Déplace le focus vers la première ligne affichée sans modifier les colonnes.<br /><br /> Si les lignes sont regroupées, déplace le focus vers la première ligne dans <xref:System.Windows.Controls.DataGrid> sans modifier les colonnes.|  
|TAB|Déplace le focus vers la prochaine cellule de la ligne actuelle.  Si le focus se trouve déjà dans la dernière cellule de la ligne, déplace le focus vers la première cellule de la ligne suivante.  Si le focus se trouve dans la dernière cellule du contrôle, déplace le focus vers le contrôle suivant dans l'ordre de tabulation du conteneur parent.<br /><br /> Si la cellule active est en mode Édition et que lorsque vous appuyez sur la touche de tabulation, le focus est déplacé de la ligne active, toutes les modifications qui ont été apportées à la ligne sont validées avant que le focus ne soit modifié.|  
|MAJ\+TAB|Déplace le focus vers la cellule précédente de la ligne actuelle.  Si le focus se trouve déjà dans la première cellule de la ligne, déplace le focus vers la dernière cellule de la ligne précédente.  Si le focus se trouve dans la première cellule du contrôle, déplace le focus vers le contrôle précédent dans l'ordre de tabulation du conteneur parent.<br /><br /> Si la cellule active est en mode Édition et que lorsque vous appuyez sur la touche de tabulation, le focus est déplacé de la ligne active, toutes les modifications qui ont été apportées à la ligne sont validées avant que le focus ne soit modifié.|  
|CTRL\+BAS|Déplace le focus vers la dernière cellule de la colonne actuelle.|  
|CTRL\+HAUT|Déplace le focus vers la première cellule de la colonne actuelle.|  
|CTRL\+FLECHE DROITE|Déplace le focus vers la dernière cellule de la ligne actuelle.|  
|CTRL\+FLECHE GAUCHE|Déplace le focus vers la première cellule de la ligne actuelle.|  
|CTRL\+ORIGINE|Déplace le focus vers la première cellule du contrôle.|  
|CTRL\+FIN|Déplace le focus vers la dernière cellule du contrôle.|  
|CTRL\+PAGE SUIVANTE|Identique à PAGE SUIVANTE.|  
|CTRL\+PG.PRÉC|Identique à PAGE PRÉCÉDENTE.|  
|F2|Si la propriété <xref:System.Windows.Controls.DataGrid.IsReadOnly%2A?displayProperty=fullName> a la valeur `false` et que la propriété <xref:System.Windows.Controls.DataGridColumn.IsReadOnly%2A?displayProperty=fullName> a la valeur `false` pour la colonne actuelle, place la cellule actuelle en mode édition de cellule.|  
|ENTRÉE|Valide toutes les modifications apportées à la cellule et à la ligne actives, et déplace le focus vers la cellule située immédiatement au\-dessous de la cellule active.  Si le focus se trouve sur la dernière ligne, valide toutes les modifications sans déplacer le focus.|  
|ÉCHAP|Si le contrôle est en mode édition, annule toutes les modifications apportées dans le contrôle.  Si la source de données sous\-jacente implémente <xref:System.ComponentModel.IEditableObject>, appuyez une deuxième fois sur ÉCHAP pour annuler le mode édition pour toute la ligne.|  
|RET.ARR|Supprime le caractère situé avant le curseur lors de la modification d'une cellule.|  
|DELETE|Supprime le caractère situé après le curseur lors de la modification d'une cellule.|  
|CTRL\+ENTRÉE|Valide toutes les modifications apportées à la cellule active sans déplacer le focus.|  
|CTRL\+A|Si <xref:System.Windows.Controls.DataGrid.SelectionMode%2A> est défini sur <xref:System.Windows.Controls.DataGridSelectionMode>, sélectionne toutes les lignes dans <xref:System.Windows.Controls.DataGrid>.|  
  
## Touches de sélection  
 Si la propriété <xref:System.Windows.Controls.DataGrid.SelectionMode%2A> a la valeur <xref:System.Windows.Controls.DataGridSelectionMode>, le comportement de navigation ne change pas, mais la navigation avec le clavier tout en appuyant sur MAJ \(y compris CTRL\+MAJ\) modifie une sélection de plusieurs lignes.  Avant le début de la navigation, le contrôle marque la ligne actuelle en tant que ligne d'ancrage.  Lorsque vous naviguez tout en appuyant sur MAJ, la sélection inclut toutes les lignes situées entre la ligne d'ancrage et la ligne actuelle.  
  
 Les touches de sélection suivantes modifient la sélection de plusieurs lignes.  
  
-   MAJ\+BAS  
  
-   MAJ\+HAUT  
  
-   MAJ\+PG.SUIV  
  
-   MAJ\+PG.PRÉC  
  
-   CTRL\+MAJ\+BAS  
  
-   CTRL\+MAJ\+HAUT  
  
-   CTRL\+MAJ\+ORIGINE  
  
-   CTRL\+MAJ\+FIN  
  
## Comportement par défaut de la souris  
 Le tableau suivant répertorie le comportement par défaut de la souris pour <xref:System.Windows.Controls.DataGrid>.  
  
|Action de souris|Description|  
|----------------------|-----------------|  
|Clic sur une ligne désélectionnée|Fait de la ligne sur laquelle est effectué un clic la ligne active et de la cellule cliquée,la cellule active.|  
|Cliquez sur la cellule active|Met la cellule active en mode édition.|  
|Déplacement d'une cellule d'en\-tête de colonne|Si la propriété <xref:System.Windows.Controls.DataGrid.CanUserReorderColumns%2A?displayProperty=fullName> a la valeur `true` et que la propriété <xref:System.Windows.Controls.DataGridColumn.CanUserReorder%2A?displayProperty=fullName> a la valeur `true` pour la colonne actuelle, déplace la colonne afin qu'elle puisse être placée dans une nouvelle position.|  
|Déplacement d'un séparateur d'en\-tête de colonne|Si la propriété <xref:System.Windows.Controls.DataGrid.CanUserResizeColumns%2A?displayProperty=fullName> a la valeur `true` et que la propriété <xref:System.Windows.Controls.DataGridColumn.CanUserResize%2A?displayProperty=fullName> a la valeur `true` pour la colonne actuelle, redimensionne la colonne.|  
|Double\-cliquez sur un séparateur de l'en\-tête de colonne|Si la propriété <xref:System.Windows.Controls.DataGrid.CanUserResizeColumns%2A?displayProperty=fullName> est `true` et que la propriété <xref:System.Windows.Controls.DataGridColumn.CanUserResize%2A?displayProperty=fullName> est `true` pour la colonne actuelle, la colonne est redimensionnée automatiquement à l'aide du mode de redimensionnement <xref:System.Windows.Controls.DataGridLength.Auto%2A>.|  
|Clic sur une cellule d'en\-tête de colonne|Si la propriété <xref:System.Windows.Controls.DataGrid.CanUserSortColumns%2A?displayProperty=fullName> a la valeur `true` et que la propriété <xref:System.Windows.Controls.DataGridColumn.CanUserSort%2A?displayProperty=fullName> a la valeur `true` pour la colonne actuelle, trie la colonne.<br /><br /> Si l'utilisateur clique sur l'en\-tête d'une colonne qui est déjà triée, l'ordre de tri est inversé pour cette colonne.<br /><br /> Si l'utilisateur clique sur plusieurs en\-têtes de colonne tout en appuyant sur la touche MAJ, les colonnes correspondantes sont triées dans l'ordre dans lequel l'utilisateur a cliqué sur leur en\-tête.|  
|CTRL\+clic sur une ligne|Si <xref:System.Windows.Controls.DataGrid.SelectionMode%2A> a la valeur <xref:System.Windows.Controls.DataGridSelectionMode>, modifie une sélection de plusieurs lignes non contiguës.<br /><br /> Désélectionne la ligne, si elle est déjà sélectionnée.|  
|MAJ\+clic sur une ligne|Si <xref:System.Windows.Controls.DataGrid.SelectionMode%2A> a la valeur <xref:System.Windows.Controls.DataGridSelectionMode>, modifie une sélection de plusieurs lignes contiguës.|  
|Cliquez sur un en\-tête de groupe de lignes|Développe ou réduit le groupe.|  
|Cliquez sur le bouton Sélectionner tout situé dans le coin supérieur gauche de <xref:System.Windows.Controls.DataGrid>|Si <xref:System.Windows.Controls.DataGrid.SelectionMode%2A> est défini sur <xref:System.Windows.Controls.DataGridSelectionMode>, sélectionne toutes les lignes dans <xref:System.Windows.Controls.DataGrid>.|  
  
## Sélection de la souris  
 Si la propriété <xref:System.Windows.Controls.DataGrid.SelectionMode%2A> a la valeur <xref:System.Windows.Controls.DataGridSelectionMode>, vous modifiez une sélection de plusieurs lignes en cliquant sur une ligne tout en appuyant sur la touche CTRL ou MAJ.  
  
 Lorsque vous cliquez sur une ligne tout en appuyant sur CTRL, la ligne modifie son état de sélection, tandis que toutes les autres lignes conservent leur état de sélection actuel.  Procédez comme suit pour sélectionner les lignes non adjacentes.  
  
 Lorsque vous cliquez sur une ligne tout en appuyant sur MAJ, la sélection inclut toutes les lignes qui figurent entre la ligne actuelle et une ligne d'ancrage située à la position de la ligne actuelle avant le premier clic.  Les clics suivants tout en appuyant sur la touche MAJ modifient la ligne actuelle, mais pas la ligne d'ancrage.  Procédez comme suit pour sélectionner une plage des lignes adjacentes.  
  
 CTRL\+MAJ peut être combiné pour sélectionner les plages non adjacentes des lignes adjacentes.  Pour ce faire, entrez la première plage à l'aide de MAJ\+clic, comme décrit précédemment.  Une fois la première plage de lignes sélectionnée, utilisez CTRL\+click pour entrer la première ligne de la plage suivante, puis cliquez sur la dernière ligne de la plage suivante tout en appuyant sur CTRL\+MAJ.  
  
## Voir aussi  
 <xref:System.Windows.Controls.DataGrid>   
 <xref:System.Windows.Controls.DataGrid.SelectionMode%2A>