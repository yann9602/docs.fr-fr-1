---
title: "Modes de s&#233;lection dans le contr&#244;le DataGridView Windows Forms | Microsoft Docs"
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
  - "DataGridView (contrôle Windows Forms), mode de sélection"
  - "sélection, modes dans le contrôle DataGridView"
ms.assetid: a3ebfd3d-0525-479d-9d96-d9e017289b36
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# Modes de s&#233;lection dans le contr&#244;le DataGridView Windows Forms
Vous pouvez souhaiter que votre application effectue des actions basées sur des sélections d'utilisateur dans un contrôle <xref:System.Windows.Forms.DataGridView>.  Suivant ces actions, vous pouvez souhaiter restreindre les types de sélection possibles.  Supposons par exemple que votre application peut imprimer un rapport pour l'enregistrement actuellement sélectionné.  Dans ce cas, vous pouvez configurer le contrôle <xref:System.Windows.Forms.DataGridView> pour qu'il suffise de cliquer n'importe où dans une ligne pour la sélectionner tout entière, et pour qu'une seule ligne puisse être sélectionnée à la fois.  
  
 Vous pouvez spécifier les sélections autorisées en donnant à la propriété <xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=fullName> l'une des valeurs d'énumération <xref:System.Windows.Forms.DataGridViewSelectionMode> suivantes.  
  
|Valeur DataGridViewSelectionMode|Description|  
|--------------------------------------|-----------------|  
|<xref:System.Windows.Forms.DataGridViewSelectionMode>|Cliquer sur une cellule la sélectionne.  Les en\-têtes de ligne et de colonne ne peuvent pas être utilisés pour la sélection.|  
|<xref:System.Windows.Forms.DataGridViewSelectionMode>|Cliquer sur une cellule la sélectionne.  Cliquer sur un en\-tête de colonne sélectionne la colonne entière.  Les en\-têtes de colonne ne peuvent pas être utilisés pour le tri.|  
|<xref:System.Windows.Forms.DataGridViewSelectionMode>|Cliquer sur une cellule ou sur un en\-tête de colonne sélectionne la colonne entière.  Les en\-têtes de colonne ne peuvent pas être utilisés pour le tri.|  
|<xref:System.Windows.Forms.DataGridViewSelectionMode>|Cliquer sur une cellule ou sur un en\-tête de ligne sélectionne la ligne entière.|  
|<xref:System.Windows.Forms.DataGridViewSelectionMode>|Mode de sélection par défaut.  Cliquer sur une cellule la sélectionne.  Cliquer sur un en\-tête de ligne sélectionne la ligne entière.|  
  
> [!NOTE]
>  Changer de mode de sélection au moment de l'exécution efface automatiquement la sélection actuelle.  
  
 Par défaut, les utilisateurs peuvent sélectionner plusieurs lignes, colonnes ou cellules en faisant glisser la souris, en appuyant sur CTRL ou MAJ pour étendre ou modifier une sélection, ou en cliquant sur la cellule d'en\-tête située à l'angle supérieur gauche pour sélectionner toutes les cellules du contrôle.  Pour empêcher ce comportement, donnez à la propriété <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> la valeur `false`.  
  
 Les modes <xref:System.Windows.Forms.DataGridViewSelectionMode> et <xref:System.Windows.Forms.DataGridViewSelectionMode> permettent aux utilisateurs de supprimer des lignes en les sélectionnant et appuyant sur la touche SUPPR.  Les utilisateurs peuvent supprimer des lignes uniquement lorsque la cellule active n'est pas en mode édition, la propriété <xref:System.Windows.Forms.DataGridView.AllowUserToDeleteRows%2A> a la valeur `true`, et la source de données sous\-jacente prend en charge la suppression de ligne conduite par utilisateur.  Notez que ces paramètres n'empêchent pas suppression de ligne par programmation.  
  
## Sélection par programmation  
 Le mode de sélection actuel restreint le comportement de sélection par programmation ainsi que la sélection utilisateur.  Vous pouvez changer la sélection actuelle par programme en définissant la propriété `Selected` de toute cellule, ligne ou colonne présente dans le contrôle <xref:System.Windows.Forms.DataGridView>.  Vous pouvez également sélectionner toutes les cellules dans le contrôle à l'aide de la méthode <xref:System.Windows.Forms.DataGridView.SelectAll%2A>, suivant le mode de sélection.  Pour effacer la sélection, utilisez la méthode <xref:System.Windows.Forms.DataGridView.ClearSelection%2A>.  
  
 Si la propriété <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> a la valeur `true`, vous pouvez ajouter ou supprimer des éléments <xref:System.Windows.Forms.DataGridView> dans la sélection en modifiant la propriété `Selected` de l'élément.  Sinon, donner à la propriété `Selected` la valeur `true` pour un élément supprime automatiquement les autres éléments de la sélection.  
  
 Notez que la modification de la valeur de la propriété <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> ne modifie pas la sélection actuelle.  
  
 Vous pouvez récupérer une collection des cellules, lignes ou colonnes actuellement sélectionnées par l'intermédiaire des propriétés <xref:System.Windows.Forms.DataGridView.SelectedCells%2A>, <xref:System.Windows.Forms.DataGridView.SelectedRows%2A> et <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> du contrôle <xref:System.Windows.Forms.DataGridView>.  L'accès à ces propriétés est inefficace si toutes les cellules du contrôle sont sélectionnées.  Pour éviter une baisse des performances dans ce cas, utilisez d'abord la méthode <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A>.  En outre, accéder à ces collections pour déterminer le nombre de cellules, lignes ou colonnes sélectionnées peut être inefficace.  À la place, utilisez la méthode <xref:System.Windows.Forms.DataGridView.GetCellCount%2A>, <xref:System.Windows.Forms.DataGridViewRowCollection.GetRowCount%2A> ou <xref:System.Windows.Forms.DataGridViewColumnCollection.GetColumnCount%2A>, en passant la valeur <xref:System.Windows.Forms.DataGridViewElementStates>.  
  
> [!TIP]
>  L'exemple de code qui illustre l'utilisation par programmation des cellules sélectionnées peut être consulté dans la vue d'ensemble de la classe <xref:System.Windows.Forms.DataGridView>.  
  
## Voir aussi  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.DataGridView.MultiSelect%2A>   
 <xref:System.Windows.Forms.DataGridView.SelectionMode%2A>   
 <xref:System.Windows.Forms.DataGridViewSelectionMode>   
 [Sélection et utilisation du Presse\-papiers avec le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/selection-and-clipboard-use-with-the-windows-forms-datagridview-control.md)   
 [Comment : définir le mode de sélection du contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/how-to-set-the-selection-mode-of-the-windows-forms-datagridview-control.md)