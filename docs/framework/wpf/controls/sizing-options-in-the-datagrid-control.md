---
title: "Options de dimensionnement dans le contrôle DataGrid"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DataGrid control [WPF], sizing
- size [WPF], DataGrid
- automatically size DataGrid [WPF]
ms.assetid: 96a0e47e-b010-4302-98ef-2daac446d8db
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4219dc88a263b73aa89812a2f841a920c804796b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="sizing-options-in-the-datagrid-control"></a>Options de dimensionnement dans le contrôle DataGrid
Plusieurs options sont disponibles pour contrôler comment le <xref:System.Windows.Controls.DataGrid> se redimensionne. Le <xref:System.Windows.Controls.DataGrid>et les lignes et les colonnes dans le <xref:System.Windows.Controls.DataGrid>, peut être défini sur la taille s’adapte automatiquement à leur contenu, ou peut être défini sur des valeurs spécifiques. Par défaut, le <xref:System.Windows.Controls.DataGrid> augmente et ajuster la taille de son contenu.  
  
## <a name="sizing-the-datagrid"></a>Dimensionnement de DataGrid  
  
### <a name="cautions-when-using-automatic-sizing"></a>Avertissements lors de l’utilisation de dimensionnement automatique  
 Par défaut, le <xref:System.Windows.FrameworkElement.Height%2A> et <xref:System.Windows.FrameworkElement.Width%2A> propriétés de la <xref:System.Windows.Controls.DataGrid> sont définies sur <xref:System.Double.NaN?displayProperty=nameWithType> («`Auto`» en XAML) et le <xref:System.Windows.Controls.DataGrid> s’ajuste à la taille de son contenu.  
  
 Lorsqu’elle est placée à l’intérieur d’un conteneur qui ne restreint pas la taille de ses enfants, comme un <xref:System.Windows.Controls.Canvas> ou <xref:System.Windows.Controls.StackPanel>, le <xref:System.Windows.Controls.DataGrid> s’étire au-delà des limites visibles du conteneur et les barres de défilement ne seront pas affichées. Cette condition a des implications en matière de facilité d’utilisation et de performances.  
  
 Lorsqu’il est lié à un jeu de données, si le <xref:System.Windows.FrameworkElement.Height%2A> de la <xref:System.Windows.Controls.DataGrid> est non restreint, il continue à ajouter une ligne pour chaque élément de données dans le jeu de données lié. Cela peut provoquer le <xref:System.Windows.Controls.DataGrid> à croître en dehors des limites visibles de votre application lorsque des lignes sont ajoutées. Le <xref:System.Windows.Controls.DataGrid> n’affiche pas les barres de défilement dans ce cas, car son <xref:System.Windows.FrameworkElement.Height%2A> continueront à croître à prendre en compte les nouvelles lignes.  
  
 Un objet est créé pour chaque ligne dans le <xref:System.Windows.Controls.DataGrid>. Si vous travaillez avec un jeu de données volumineux et vous autorisez le <xref:System.Windows.Controls.DataGrid> dimensionnement automatique, la création d’un grand nombre d’objets peut affecter les performances de votre application.  
  
 Pour éviter ces problèmes lorsque vous travaillez avec grands jeux de données, il est recommandé de définir plus précisément le <xref:System.Windows.FrameworkElement.Height%2A> de la <xref:System.Windows.Controls.DataGrid> ou placez-le dans un conteneur qui restreint son <xref:System.Windows.FrameworkElement.Height%2A>, comme un <xref:System.Windows.Controls.Grid>. Lorsque le <xref:System.Windows.FrameworkElement.Height%2A> est limitée, le <xref:System.Windows.Controls.DataGrid> créera uniquement les lignes qui pourra être contenue dans son spécifié <xref:System.Windows.FrameworkElement.Height%2A>et recycle les lignes que nécessaire pour afficher les nouvelles données.  
  
### <a name="setting-the-datagrid-size"></a>Définition de la taille de la grille de données  
 Le <xref:System.Windows.Controls.DataGrid> peut être défini sur le dimensionnement automatique dans les limites spécifiées, ou le <xref:System.Windows.Controls.DataGrid> peut être définie à une taille spécifique. Le tableau suivant présente les propriétés qui peuvent être définies pour contrôler la <xref:System.Windows.Controls.DataGrid> taille.  
  
|Propriété|Description|  
|--------------|-----------------|  
|<xref:System.Windows.FrameworkElement.Height%2A>|Définit une hauteur spécifique pour le <xref:System.Windows.Controls.DataGrid>.|  
|<xref:System.Windows.FrameworkElement.MaxHeight%2A>|Définit la limite supérieure pour la hauteur de la <xref:System.Windows.Controls.DataGrid>. Le <xref:System.Windows.Controls.DataGrid> se développe verticalement jusqu'à ce qu’il atteigne cette hauteur.|  
|<xref:System.Windows.FrameworkElement.MinHeight%2A>|Définit la limite inférieure pour la hauteur de la <xref:System.Windows.Controls.DataGrid>. Le <xref:System.Windows.Controls.DataGrid> se réduit verticalement jusqu'à ce qu’il atteigne cette hauteur.|  
|<xref:System.Windows.FrameworkElement.Width%2A>|Définit une largeur spécifique pour le <xref:System.Windows.Controls.DataGrid>.|  
|<xref:System.Windows.FrameworkElement.MaxWidth%2A>|Définit la limite supérieure pour la largeur de la <xref:System.Windows.Controls.DataGrid>. Le <xref:System.Windows.Controls.DataGrid> se développe horizontalement jusqu'à ce qu’il atteigne cette largeur.|  
|<xref:System.Windows.FrameworkElement.MinWidth%2A>|Définit la limite inférieure pour la largeur de la <xref:System.Windows.Controls.DataGrid>. Le <xref:System.Windows.Controls.DataGrid> se réduit horizontalement jusqu'à ce qu’il atteigne cette largeur.|  
  
## <a name="sizing-rows-and-row-headers"></a>Redimensionnement de lignes et des en-têtes de ligne  
  
### <a name="datagrid-rows"></a>Lignes de grille de données  
 Par défaut, un <xref:System.Windows.Controls.DataGrid> de ligne <xref:System.Windows.FrameworkElement.Height%2A> est définie sur <xref:System.Double.NaN?displayProperty=nameWithType> («`Auto`» en XAML), et la hauteur de ligne s’agrandit la taille de son contenu. La hauteur de toutes les lignes de la <xref:System.Windows.Controls.DataGrid> peut être spécifié en définissant le <xref:System.Windows.Controls.DataGrid.RowHeight%2A?displayProperty=nameWithType> propriété. Les utilisateurs peuvent modifier la hauteur de ligne en faisant glisser les séparateurs d’en-têtes de ligne.  
  
### <a name="datagrid-row-headers"></a>En-têtes de lignes de la grille de données  
 Pour afficher les en-têtes de ligne, la <xref:System.Windows.Controls.DataGrid.HeadersVisibility%2A> propriété doit être définie sur <xref:System.Windows.Controls.DataGridHeadersVisibility.Row?displayProperty=nameWithType> ou <xref:System.Windows.Controls.DataGridHeadersVisibility.All?displayProperty=nameWithType>. Par défaut, les en-têtes de ligne sont affichés, et ils sont redimensionnés automatiquement en fonction de leur contenu. Les en-têtes de lignes peuvent être donnés à une largeur spécifique en définissant le <xref:System.Windows.Controls.DataGrid.RowHeaderWidth%2A?displayProperty=nameWithType> propriété.  
  
## <a name="sizing-columns-and-column-headers"></a>Dimensionnement des colonnes et des en-têtes de colonne  
  
### <a name="datagrid-columns"></a>Colonnes DataGrid  
 Le <xref:System.Windows.Controls.DataGrid> utilise les valeurs de la <xref:System.Windows.Controls.DataGridLength> et <xref:System.Windows.Controls.DataGridLengthUnitType> pour spécifier les modes de dimensionnement absolu ou automatique.  
  
 Le tableau suivant indique les valeurs fournies par le <xref:System.Windows.Controls.DataGridLengthUnitType> structure.  
  
|Name|Description|  
|----------|-----------------|  
|<xref:System.Windows.Controls.DataGridLengthUnitType.Auto>|La valeur par défaut des tailles de mode de dimensionnement automatique <xref:System.Windows.Controls.DataGrid> colonnes basées sur le contenu des cellules et des en-têtes de colonne.|  
|<xref:System.Windows.Controls.DataGridLengthUnitType.SizeToCells>|Automatique basée sur une cellule de tailles de mode de dimensionnement <xref:System.Windows.Controls.DataGrid> colonnes basées sur le contenu des cellules dans la colonne, y compris ne pas les en-têtes de colonne.|  
|<xref:System.Windows.Controls.DataGridLengthUnitType.SizeToHeader>|Automatique basée sur l’en-tête de tailles de mode de dimensionnement <xref:System.Windows.Controls.DataGrid> colonnes basées sur le contenu des en-têtes de colonnes uniquement.|  
|<xref:System.Windows.Controls.DataGridLengthUnitType.Pixel>|Basée sur le pixel tailles de mode de dimensionnement <xref:System.Windows.Controls.DataGrid> colonnes basées sur la valeur numérique fournie.|  
|<xref:System.Windows.Controls.DataGridLengthUnitType.Star>|Le mode de redimensionnement en étoile est utilisé pour distribuer l’espace disponible par proportions pondérées.<br /><br /> En XAML, les valeurs étoiles sont exprimées sous forme de n * où n représente une valeur numérique. 1\* équivaut à \*. Par exemple, si deux colonnes dans un <xref:System.Windows.Controls.DataGrid> ont des largeurs de \* et 2\*, la première colonne reçoit une partie de l’espace disponible et la deuxième colonne reçoit deux parties de l’espace disponible.|  
  
 Le <xref:System.Windows.Controls.DataGridLengthConverter> classe peut être utilisée pour convertir des données entre les valeurs de chaîne ou numérique et <xref:System.Windows.Controls.DataGridLength> valeurs.  
  
 Par défaut, le <xref:System.Windows.Controls.DataGrid.ColumnWidth%2A?displayProperty=nameWithType> est définie sur <xref:System.Windows.Controls.DataGridLength.SizeToHeader%2A>et le <xref:System.Windows.Controls.DataGridColumn.Width%2A?displayProperty=nameWithType> est définie sur <xref:System.Windows.Controls.DataGridLength.Auto%2A>. Lorsque le mode de dimensionnement a la valeur <xref:System.Windows.Controls.DataGridLength.Auto%2A> ou <xref:System.Windows.Controls.DataGridLength.SizeToCells%2A>, colonnes finira par atteindre la largeur de leur contenu visible le plus large. Lors du défilement, ces modes de dimensionnement provoquent développement si le contenu des colonnes qui est plus grand que la taille actuelle de la colonne devient visible. La colonne ne peut pas réduire une fois que le contenu défile hors de l’affichage.  
  
 Colonnes dans les <xref:System.Windows.Controls.DataGrid> peut également être définie pour le dimensionnement automatique uniquement dans les limites spécifiées, ou peuvent être définis à une taille spécifique. Le tableau suivant présente les propriétés qui peuvent être définies pour contrôler les tailles de colonne.  
  
|Propriété|Description|  
|--------------|-----------------|  
|<xref:System.Windows.Controls.DataGrid.MaxColumnWidth%2A?displayProperty=nameWithType>|Définit la limite supérieure pour toutes les colonnes dans le <xref:System.Windows.Controls.DataGrid>.|  
|<xref:System.Windows.Controls.DataGridColumn.MaxWidth%2A?displayProperty=nameWithType>|Définit la limite supérieure pour une colonne individuelle. Substitue <xref:System.Windows.Controls.DataGrid.MaxColumnWidth%2A?displayProperty=nameWithType>.|  
|<xref:System.Windows.Controls.DataGrid.MinColumnWidth%2A?displayProperty=nameWithType>|Définit la limite inférieure de toutes les colonnes dans le <xref:System.Windows.Controls.DataGrid>.|  
|<xref:System.Windows.Controls.DataGridColumn.MinWidth%2A?displayProperty=nameWithType>|Définit la limite inférieure d’une colonne individuelle. Substitue <xref:System.Windows.Controls.DataGrid.MinColumnWidth%2A?displayProperty=nameWithType>.|  
|<xref:System.Windows.Controls.DataGrid.ColumnWidth%2A?displayProperty=nameWithType>|Définit une largeur spécifique pour toutes les colonnes dans le <xref:System.Windows.Controls.DataGrid>.|  
|<xref:System.Windows.Controls.DataGridColumn.Width%2A?displayProperty=nameWithType>|Définit une largeur spécifique pour une colonne individuelle. Substitue <xref:System.Windows.Controls.DataGrid.ColumnWidth%2A?displayProperty=nameWithType>.|  
  
### <a name="datagrid-column-headers"></a>En-têtes de colonne DataGrid  
 Par défaut, <xref:System.Windows.Controls.DataGrid> les en-têtes de colonne sont affichés. Pour masquer les en-têtes de colonne, le <xref:System.Windows.Controls.DataGrid.HeadersVisibility%2A> propriété doit être définie sur <xref:System.Windows.Controls.DataGridHeadersVisibility.Row?displayProperty=nameWithType> ou <xref:System.Windows.Controls.DataGridHeadersVisibility.None?displayProperty=nameWithType>. Par défaut, lorsque les en-têtes de colonne sont affichés, ils redimensionne automatiquement pour s’ajuster à leur contenu. Les en-têtes de colonne peuvent être donnés à une hauteur spécifique en définissant le <xref:System.Windows.Controls.DataGrid.ColumnHeaderHeight%2A?displayProperty=nameWithType> propriété.  
  
### <a name="resizing-with-the-mouse"></a>Redimensionnement avec la souris  
 Les utilisateurs peuvent redimensionner <xref:System.Windows.Controls.DataGrid> lignes et colonnes en faisant glisser les séparateurs d’en-têtes de lignes ou de colonnes. Le <xref:System.Windows.Controls.DataGrid> prend également en charge le redimensionnement automatique des lignes et des colonnes en double-cliquant sur le séparateur d’en-tête de ligne ou de colonne. Pour empêcher un utilisateur de redimensionner les colonnes particuliers, définissez le <xref:System.Windows.Controls.DataGridColumn.CanUserResize%2A?displayProperty=nameWithType> propriété `false` pour les colonnes individuelles. Pour empêcher les utilisateurs de redimensionner toutes les colonnes, définissez la <xref:System.Windows.Controls.DataGrid.CanUserResizeColumns%2A?displayProperty=nameWithType> propriété `false`. Pour empêcher les utilisateurs de redimensionner toutes les lignes, définissez la <xref:System.Windows.Controls.DataGrid.CanUserResizeRows%2A?displayProperty=nameWithType> propriété `false`.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Controls.DataGrid>  
 <xref:System.Windows.Controls.DataGridColumn>  
 <xref:System.Windows.Controls.DataGridLength>  
 <xref:System.Windows.Controls.DataGridLengthConverter>
