---
title: "Raccourcis clavier du contr&#244;le DataGrid Windows Forms | Microsoft Docs"
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
  - "DataGrid (contrôle Windows Forms), touches de navigation"
  - "raccourcis clavier, DataGrid (contrôle)"
ms.assetid: a01780f9-20d5-4f5f-808f-c790c9a007a5
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# Raccourcis clavier du contr&#244;le DataGrid Windows Forms
> [!NOTE]
>  Le contrôle <xref:System.Windows.Forms.DataGridView> remplace le contrôle <xref:System.Windows.Forms.DataGrid> et lui ajoute des fonctionnalités ; toutefois, le contrôle <xref:System.Windows.Forms.DataGrid> est conservé pour la compatibilité descendante et l'utilisation future si tel est votre choix.  Pour plus d'informations, consultez [Différences entre les contrôles DataGridView et DataGrid Windows Forms](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Le tableau suivant répertorie les raccourcis clavier permettant de se déplacer au sein du contrôle <xref:System.Windows.Forms.DataGrid> Windows Forms :  
  
|Action|Raccourci|  
|------------|---------------|  
|Terminer une entrée de cellule et descendre à la cellule suivante.<br /><br /> Si le focus est placé sur le lien d'une table enfant, vous déplacer jusqu'à cette table.|ENTRÉE|  
|En mode d'édition de cellule, annuler la modification de la cellule.<br /><br /> En sélection défilante, annuler la modification de la ligne.|ÉCHAP|  
|Supprimer le caractère situé avant le point d'insertion lors de la modification d'une cellule.|RET.ARR|  
|Supprimer le caractère situé après le point d'insertion lors de la modification d'une cellule.|DELETE|  
|Vous déplacer sur la première cellule de la ligne en cours.|DÉBUT|  
|Vous déplacer sur la dernière cellule de la ligne en cours.|FIN|  
|Sélectionner les caractères de la cellule en cours et placer le point d'insertion à la fin de la ligne.  Revient à double\-cliquer sur une cellule.|F2|  
|Si le focus est placé sur une cellule, vous déplacer sur la cellule suivante de la ligne.<br /><br /> Si le focus est placé sur la dernière cellule d'une ligne, vous déplacer jusqu'au premier lien de la table enfant de la ligne et le développer.<br /><br /> Si le focus est placé sur un lien enfant, vous déplacer jusqu'au lien enfant suivant.<br /><br /> Si le focus est placé sur le dernier lien enfant, vous déplacer sur la première cellule de la ligne suivante.|TAB|  
|Si le focus est placé sur une cellule, vous déplacer sur la cellule précédente de la ligne.<br /><br /> Si le focus est placé sur la première cellule d'une ligne, vous déplacer jusqu'au dernier lien développé de la table enfant ou sur la dernière cellule de la ligne précédente.<br /><br /> Si le focus est placé sur un lien enfant, vous déplacer jusqu'au lien enfant précédent.<br /><br /> Si le focus est placé sur le premier lien enfant, vous déplacer sur la dernière cellule de la ligne précédente.|MAJ\+TAB|  
|Vous déplacer sur le contrôle suivant dans l'ordre de tabulation.|CTRL\+TAB|  
|Vous déplacer sur le contrôle précédent dans l'ordre de tabulation.|CTRL\+MAJ\+TAB|  
|Si vous êtes dans une table enfant, vous déplacer jusqu'à la table parente.  Revient à cliquer sur le bouton Précédent.|ALT\+GAUCHE|  
|Développer les liens de la table enfant.  ALT\+BAS développe tous les liens \(et non pas uniquement les liens sélectionnés\).|ALT\+BAS ou CTRL\+SIGNE PLUS|  
|Réduire les liens de la table enfant.  ALT\+HAUT réduit tous les liens \(et non pas uniquement les liens sélectionnés\).|ALT\+HAUT ou CTRL\+SIGNE MOINS|  
|Vous déplacer sur la cellule non vide la plus éloignée, dans la direction de la flèche.|CTRL\+FLÈCHE|  
|Étendre la sélection d'une ligne dans la direction de la flèche \(sauf les liens de la table enfant\).|MAJ\+HAUT\/BAS|  
|Étendre la sélection jusqu'à la ligne non vide la plus éloignée dans la direction de la flèche \(sauf les liens de la table enfant\).|CRTL\+MAJ\+HAUT\/BAS|  
|Vous déplacer sur la première cellule en haut à gauche.|CTRL\+ORIGINE|  
|Vous déplacer sur la dernière cellule située en bas à droite.|CTRL\+FIN|  
|Étendre la sélection jusqu'à la première ligne.|CTRL\+MAJ\+ORIGINE|  
|Étendre la sélection jusqu'à la dernière ligne.|CTRL\+MAJ\+FIN|  
|Sélectionner la ligne en cours \(sauf les liens de la table enfant\).|MAJ\+ESPACE|  
|Sélectionner toute la grille \(sauf les liens de la table enfant\).|CTRL\+A|  
|Dans une table enfant, afficher la ligne parente.|CTRL\+PAGE SUIVANTE|  
|Dans une table enfant, masquer la ligne parente.|CTRL\+PG.PRÉC|  
|Étendre la sélection d'une page vers le bas \(sauf les liens de la table enfant\).|MAJ\+PG.SUIV|  
|Étendre la sélection d'une page vers le haut \(sauf les liens de la table enfant\).|MAJ\+PG.PRÉC|  
|Appeler la méthode <xref:System.Windows.Forms.DataGrid.EndEdit%2A> pour la ligne en cours.|CTRL\+ENTRÉE|  
|En mode édition, entrer une valeur <xref:System.DBNull.Value?displayProperty=fullName> dans une cellule.|CTRL\+0|  
  
## Voir aussi  
 [Vue d'ensemble du contrôle DataGrid](../../../../docs/framework/winforms/controls/datagrid-control-overview-windows-forms.md)   
 [DataGrid, contrôle](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)