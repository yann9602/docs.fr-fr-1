---
title: "Redimensionnement des colonnes et des lignes dans le contrôle DataGridView Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DataGridView control [Windows Forms], sizing rows and columns
- columns [Windows Forms], resizing in grids
- data grids [Windows Forms], resizing columns and rows
ms.assetid: 7532764d-e5c1-4943-a08b-6377a722d3b6
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3621b05f1faae671d93106f50dfef1311959e48e
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2017
---
# <a name="resizing-columns-and-rows-in-the-windows-forms-datagridview-control"></a>Redimensionnement des colonnes et des lignes dans le contrôle DataGridView Windows Forms
Le `DataGridView` contrôle fournit de nombreuses options pour personnaliser le comportement de dimensionnement de ses colonnes et de lignes. En règle générale, `DataGridView` cellules ne se redimensionnent pas en fonction de leur contenu. Au lieu de cela, elles tronquent toute valeur d’affichage qui est supérieure à la cellule. Si le contenu peut être affiché sous forme de chaîne, la cellule affiche dans une info-bulle.  
  
 Par défaut, les utilisateurs peuvent faire glisser les séparateurs d’en-tête avec la souris pour afficher plus d’informations, ligne et colonne. Les utilisateurs peuvent double-cliquer également un séparateur pour redimensionner automatiquement la bande de ligne, de colonne ou en-tête associée en fonction de son contenu.  
  
 Le `DataGridView` contrôle fournit des propriétés, méthodes et événements qui vous permettent de personnaliser ou de désactiver tous ces comportements dirigés par l’utilisateur. En outre, vous pouvez redimensionner par programme des lignes, colonnes et en-têtes pour s’adapter à leur contenu, ou vous pouvez les configurer pour être redimensionnées automatiquement chaque fois que leur contenu change. Vous pouvez également configurer des colonnes pour diviser automatiquement la largeur disponible du contrôle dans les proportions que vous spécifiez.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Options de dimensionnement dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/sizing-options-in-the-windows-forms-datagridview-control.md)  
 Décrit les options de redimensionnement de lignes, colonnes et des en-têtes. Également fournit des détails sur les méthodes et propriétés liées au dimensionnement et décrit les scénarios d’utilisation courants.  
  
 [Mode Remplissage des colonnes dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/column-fill-mode-in-the-windows-forms-datagridview-control.md)  
 Décrit le mode de remplissage de colonne en détail et fournit du code de démonstration que vous pouvez utiliser pour faire des essais avec le mode de remplissage de colonne et les autres modes.  
  
 [Guide pratique pour définir les modes de redimensionnement du contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/how-to-set-the-sizing-modes-of-the-windows-forms-datagridview-control.md)  
 Décrit comment configurer les modes de dimensionnement pour des objectifs communs.  
  
 [Guide pratique pour redimensionner des cellules par programme pour les adapter au contenu du contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/programmatically-resize-cells-to-fit-content-in-the-datagrid.md)  
 Fournit du code de démonstration que vous pouvez utiliser pour faire des essais avec le redimensionnement par programmation.  
  
 [Guide pratique pour redimensionner automatiquement des cellules lorsque leur contenu change dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/automatically-resize-cells-when-content-changes-in-the-datagrid.md)  
 Fournit du code de démonstration que vous pouvez utiliser pour faire des essais avec les modes de dimensionnement automatique.  
  
## <a name="reference"></a>Référence  
 <xref:System.Windows.Forms.DataGridView>  
 Fournit la documentation de référence pour le contrôle <xref:System.Windows.Forms.DataGridView>.  
  
## <a name="see-also"></a>Voir aussi  
 [DataGridView, contrôle](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)
