---
title: "Redimensionnement des colonnes et des lignes dans le contr&#244;le DataGridView Windows Forms | Microsoft Docs"
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
  - "colonnes (Windows Forms), redimensionner dans les grilles"
  - "grilles de données, redimensionner les colonnes et les lignes"
  - "DataGridView (contrôle Windows Forms), dimensionner les lignes et les colonnes"
ms.assetid: 7532764d-e5c1-4943-a08b-6377a722d3b6
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# Redimensionnement des colonnes et des lignes dans le contr&#244;le DataGridView Windows Forms
Le contrôle `DataGridView` fournit de nombreuses options de personnalisation du comportement de dimensionnement de ses colonnes et de ses lignes.  En général, les cellules `DataGridView` ne se redimensionnent pas en fonction de leur contenu.  À la place, elles tronquent toute valeur d'affichage supérieure à celle de la cellule.  Si le contenu peut être affiché comme une chaîne, la cellule l'affiche dans une Info\-bulle.  
  
 Par défaut, les utilisateurs peuvent faire glisser les séparateurs de ligne, colonne et en\-tête à l'aide de la souris pour afficher plus d'informations.  Les utilisateurs peuvent également double\-cliquer sur un séparateur pour redimensionner automatiquement la ligne, colonne ou en\-tête associé, en fonction de son contenu.  
  
 Le contrôle `DataGridView` fournit des propriétés, méthodes et événements qui vous permettent de personnaliser ou de désactiver tous ces comportements dirigés par utilisateur.  En outre, vous pouvez redimensionner par programme des lignes, colonnes et en\-tête en fonction de leur contenu, ou vous pouvez les configurer pour qu'ils se redimensionnent automatiquement chaque fois que leur contenu change.  Vous pouvez également configurer des colonnes pour diviser automatiquement la largeur disponible du contrôle dans les proportions que vous spécifiez.  
  
## Dans cette section  
 [Options de dimensionnement dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/sizing-options-in-the-windows-forms-datagridview-control.md)  
 Décrit les options de dimensionnement les lignes, des colonnes et des en\-têtes.  Fournit également des détails sur les propriétés et aux méthodes relatives au dimensionnement et décrit des scénarios d'utilisation communs.  
  
 [Mode Remplissage des colonnes dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/column-fill-mode-in-the-windows-forms-datagridview-control.md)  
 Décrit le mode de remplissage de colonne en détail et fournit du code de démonstration pour expérimenter le mode de remplissage de colonne et d'autres modes.  
  
 [Comment : définir les modes de redimensionnement du contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/how-to-set-the-sizing-modes-of-the-windows-forms-datagridview-control.md)  
 Décrit comment configurer les modes de dimensionnement pour des objectifs communs.  
  
 [Comment : redimensionner des cellules par programme pour les adapter au contenu du contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/programmatically-resize-cells-to-fit-content-in-the-datagrid.md)  
 Fournit du code de démonstration pour expérimenter le redimensionnement par programmation.  
  
 [Comment : redimensionner automatiquement des cellules lorsque leur contenu change dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/automatically-resize-cells-when-content-changes-in-the-datagrid.md)  
 Fournit du code de démonstration pour expérimenter les modes de dimensionnement automatiques.  
  
## Référence  
 <xref:System.Windows.Forms.DataGridView>  
 Fournit de la documentation de référence pour le contrôle <xref:System.Windows.Forms.DataGridView>.  
  
## Voir aussi  
 [DataGridView, contrôle](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)