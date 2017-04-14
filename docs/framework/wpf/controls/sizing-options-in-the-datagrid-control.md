---
title: "Options de dimensionnement dans le contr&#244;le DataGrid | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "redimensionner automatiquement DataGrid"
  - "DataGrid (contrôle WPF), dimensionner"
  - "taille (WPF), DataGrid"
ms.assetid: 96a0e47e-b010-4302-98ef-2daac446d8db
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# Options de dimensionnement dans le contr&#244;le DataGrid
Plusieurs options permettent de contrôler le dimensionnement de <xref:System.Windows.Controls.DataGrid>.  <xref:System.Windows.Controls.DataGrid>, ainsi que les lignes et colonnes de <xref:System.Windows.Controls.DataGrid>, peuvent être configurés pour un agrandissement automatique en fonction de leur contenu ou être affectés à des valeurs spécifiques.  Par défaut, <xref:System.Windows.Controls.DataGrid> s'agrandit et se réduit en fonction de la taille de son contenu.  
  
## Dimensionnement de DataGrid  
  
### Précautions lors de l'utilisation du dimensionnement automatique  
 Par défaut, les propriétés <xref:System.Windows.FrameworkElement.Height%2A> et <xref:System.Windows.FrameworkElement.Width%2A> de <xref:System.Windows.Controls.DataGrid> ont la valeur <xref:System.Double.NaN?displayProperty=fullName> \(« `Auto` » dans XAML\), et <xref:System.Windows.Controls.DataGrid> s'adapte à la taille de son contenu.  
  
 En cas de placement dans un conteneur qui ne restreint pas la taille de ses enfants \(<xref:System.Windows.Controls.Canvas> ou <xref:System.Windows.Controls.StackPanel>, par exemple\), <xref:System.Windows.Controls.DataGrid> s'étire au\-delà des limites visibles du conteneur et les barres de défilement ne sont pas visibles.  Cette condition implique des conséquences sur l'utilisation et sur les performances.  
  
 En cas de liaison à un groupe de données, si le <xref:System.Windows.FrameworkElement.Height%2A> de <xref:System.Windows.Controls.DataGrid> n'est pas restreint, il continue à ajouter une ligne pour chaque élément de données dans le groupe de données lié.  Cela peut entraîner l'agrandissement de <xref:System.Windows.Controls.DataGrid> en dehors des limites visibles de l'application au fur et à mesure de l'ajout de lignes.  Dans ce cas, <xref:System.Windows.Controls.DataGrid> n'affiche pas de barre de défilement, car son <xref:System.Windows.FrameworkElement.Height%2A> continue à s'agrandir pour s'adapter aux nouvelles lignes.  
  
 Un objet est créé pour chaque ligne de <xref:System.Windows.Controls.DataGrid>.  Si vous manipulez un groupe de données volumineux et autorisez le dimensionnement automatique de <xref:System.Windows.Controls.DataGrid>, la création d'un nombre important d'objets peut avoir un impact sur les performances de l'application.  
  
 Pour éviter ces problèmes lorsque vous utilisez des jeux de données volumineux, il est recommandé de définir le <xref:System.Windows.FrameworkElement.Height%2A> du <xref:System.Windows.Controls.DataGrid> ou de le placer dans un conteneur qui restreint son <xref:System.Windows.FrameworkElement.Height%2A>, comme <xref:System.Windows.Controls.Grid>.  Si <xref:System.Windows.FrameworkElement.Height%2A> est restreint, <xref:System.Windows.Controls.DataGrid> ne crée que les lignes qui s'adaptent dans le <xref:System.Windows.FrameworkElement.Height%2A> spécifié et, si nécessaire, recycle ces lignes pour afficher les nouvelles données.  
  
### Définition de la taille de DataGrid  
 <xref:System.Windows.Controls.DataGrid> peut être défini pour un dimensionnement automatique dans les limites spécifiées ou une taille particulière peut être définie pour <xref:System.Windows.Controls.DataGrid>.  Le tableau ci\-dessous indique les propriétés qui peuvent être définies pour contrôler la taille de <xref:System.Windows.Controls.DataGrid>.  
  
|Propriété|Description|  
|---------------|-----------------|  
|<xref:System.Windows.FrameworkElement.Height%2A>|Définit une hauteur spécifique pour <xref:System.Windows.Controls.DataGrid>.|  
|<xref:System.Windows.FrameworkElement.MaxHeight%2A>|Définit la limite supérieure pour la hauteur de <xref:System.Windows.Controls.DataGrid>.  <xref:System.Windows.Controls.DataGrid> se développe verticalement jusqu'à ce que la hauteur soit atteinte.|  
|<xref:System.Windows.FrameworkElement.MinHeight%2A>|Définit la limite inférieure pour la hauteur de <xref:System.Windows.Controls.DataGrid>.  <xref:System.Windows.Controls.DataGrid> se réduit verticalement jusqu'à ce que la hauteur soit atteinte.|  
|<xref:System.Windows.FrameworkElement.Width%2A>|Définit une largeur spécifique pour <xref:System.Windows.Controls.DataGrid>.|  
|<xref:System.Windows.FrameworkElement.MaxWidth%2A>|Définit la limite supérieure pour la largeur de <xref:System.Windows.Controls.DataGrid>.  <xref:System.Windows.Controls.DataGrid> se développe horizontalement jusqu'à ce que la largeur soit atteinte.|  
|<xref:System.Windows.FrameworkElement.MinWidth%2A>|Définit la limite inférieure pour la largeur de <xref:System.Windows.Controls.DataGrid>.  <xref:System.Windows.Controls.DataGrid> se réduit horizontalement jusqu'à ce que la largeur soit atteinte.|  
  
## Dimensionnement des lignes et des en\-têtes de lignes  
  
### Lignes DataGrid  
 Par défaut, la propriété <xref:System.Windows.FrameworkElement.Height%2A> d'une ligne <xref:System.Windows.Controls.DataGrid> a la valeur <xref:System.Double.NaN?displayProperty=fullName> \(« `Auto` » dans XAML\), et la hauteur de ligne s'agrandit en fonction de la taille de son contenu.  La hauteur de toutes les lignes <xref:System.Windows.Controls.DataGrid> peut être spécifiée en définissant la propriété <xref:System.Windows.Controls.DataGrid.RowHeight%2A?displayProperty=fullName>.  L'utilisateur peut modifier la hauteur de ligne en faisant glisser les séparateurs d'en\-têtes de lignes.  
  
### En\-têtes de lignes DataGrid  
 Pour afficher les en\-têtes de lignes, la propriété <xref:System.Windows.Controls.DataGrid.HeadersVisibility%2A> doit avoir la valeur <xref:System.Windows.Controls.DataGridHeadersVisibility?displayProperty=fullName> ou <xref:System.Windows.Controls.DataGridHeadersVisibility?displayProperty=fullName>.  Par défaut, les en\-têtes de lignes sont affichés et sont redimensionnés automatiquement en fonction de leur contenu.  Pour affecter une largeur spécifique aux en\-têtes de lignes, définissez la propriété <xref:System.Windows.Controls.DataGrid.RowHeaderWidth%2A?displayProperty=fullName>.  
  
## Dimensionnement des colonnes et des en\-têtes de colonnes  
  
### Colonnes DataGrid  
 <xref:System.Windows.Controls.DataGrid> utilise des valeurs de <xref:System.Windows.Controls.DataGridLength> et de la structure <xref:System.Windows.Controls.DataGridLengthUnitType> pour spécifier des modes de redimensionnement absolu ou automatique.  
  
 Le tableau ci\-dessous indique les valeurs fournies par la structure <xref:System.Windows.Controls.DataGridLengthUnitType>.  
  
|Nom|Description|  
|---------|-----------------|  
|<xref:System.Windows.Controls.DataGridLengthUnitType>|Le mode de dimensionnement automatique par défaut dimensionne les colonnes <xref:System.Windows.Controls.DataGrid> en fonction du contenu des cellules et des en\-têtes de colonnes.|  
|<xref:System.Windows.Controls.DataGridLengthUnitType>|Le mode de dimensionnement automatique basé sur la cellule dimensionne les colonnes <xref:System.Windows.Controls.DataGrid> en fonction du contenu des cellules dans la colonne, sans prendre en compte les en\-têtes de colonnes.|  
|<xref:System.Windows.Controls.DataGridLengthUnitType>|Le mode de dimensionnement automatique basé sur l'en\-tête dimensionne les colonnes <xref:System.Windows.Controls.DataGrid> uniquement en fonction du contenu des en\-têtes de colonnes.|  
|<xref:System.Windows.Controls.DataGridLengthUnitType>|Le mode de redimensionnement en pixels dimensionne les colonnes <xref:System.Windows.Controls.DataGrid> selon la valeur numérique fournie.|  
|<xref:System.Windows.Controls.DataGridLengthUnitType>|Le mode de redimensionnement proportionnel permet de distribuer l'espace disponible selon des proportions pondérées.<br /><br /> En XAML, les valeurs étoiles sont exprimées sous forme de n\* où n représente une valeur numérique.  1\* équivaut à \*.  Par exemple si deux colonnes dans un <xref:System.Windows.Controls.DataGrid> ont des largeurs de \* et 2\*, la première colonne reçoit une partie de l'espace disponible et la deuxième colonne, deux parties.|  
  
 La classe <xref:System.Windows.Controls.DataGridLengthConverter> peut être utilisée pour convertir des données entre des valeurs numériques ou de chaîne et des valeurs <xref:System.Windows.Controls.DataGridLength>.  
  
 Par défaut, la propriété <xref:System.Windows.Controls.DataGrid.ColumnWidth%2A?displayProperty=fullName> a la valeur <xref:System.Windows.Controls.DataGridLength.SizeToHeader%2A> et la propriété <xref:System.Windows.Controls.DataGridColumn.Width%2A?displayProperty=fullName> a la valeur <xref:System.Windows.Controls.DataGridLength.Auto%2A>.  Lorsque le mode de dimensionnement est <xref:System.Windows.Controls.DataGridLength.Auto%2A> ou <xref:System.Windows.Controls.DataGridLength.SizeToCells%2A>, les colonnes s'agrandissent selon la largeur de leur contenu visible le plus large.  Lors du défilement, ces modes de dimensionnement provoquent le développement des colonnes si du contenu dont la taille est supérieure à la taille de colonne actuelle est affiché par défilement.  La colonne ne sera pas réduite une fois que le contenu disparaîtra de l'écran suite à un défilement.  
  
 Les colonnes de <xref:System.Windows.Controls.DataGrid> peuvent également être définies pour un dimensionnement automatique uniquement dans les limites spécifiées ou une taille particulière peut être définie pour les colonnes.  Le tableau ci\-dessous indique les propriétés qui peuvent être définies pour contrôler la taille des colonnes.  
  
|Propriété|Description|  
|---------------|-----------------|  
|<xref:System.Windows.Controls.DataGrid.MaxColumnWidth%2A?displayProperty=fullName>|Définit la limite supérieure de toutes les colonnes dans <xref:System.Windows.Controls.DataGrid>.|  
|<xref:System.Windows.Controls.DataGridColumn.MaxWidth%2A?displayProperty=fullName>|Définit la limite supérieure d'une colonne.  Substitue <xref:System.Windows.Controls.DataGrid.MaxColumnWidth%2A?displayProperty=fullName>.|  
|<xref:System.Windows.Controls.DataGrid.MinColumnWidth%2A?displayProperty=fullName>|Définit la limite inférieure de toutes les colonnes dans <xref:System.Windows.Controls.DataGrid>.|  
|<xref:System.Windows.Controls.DataGridColumn.MinWidth%2A?displayProperty=fullName>|Définit la limite inférieure d'une colonne.  Substitue <xref:System.Windows.Controls.DataGrid.MinColumnWidth%2A?displayProperty=fullName>.|  
|<xref:System.Windows.Controls.DataGrid.ColumnWidth%2A?displayProperty=fullName>|Définit une largeur spécifique pour toutes les colonnes dans <xref:System.Windows.Controls.DataGrid>.|  
|<xref:System.Windows.Controls.DataGridColumn.Width%2A?displayProperty=fullName>|Définit une largeur spécifique pour une colonne.  Substitue <xref:System.Windows.Controls.DataGrid.ColumnWidth%2A?displayProperty=fullName>.|  
  
### En\-têtes de colonnes DataGrid  
 Par défaut, les en\-têtes de colonnes <xref:System.Windows.Controls.DataGrid> sont affichés.  Pour masquer les en\-têtes de colonnes, la propriété <xref:System.Windows.Controls.DataGrid.HeadersVisibility%2A> doit avoir la valeur <xref:System.Windows.Controls.DataGridHeadersVisibility?displayProperty=fullName> ou <xref:System.Windows.Controls.DataGridHeadersVisibility?displayProperty=fullName>.  Par défaut, lorsque les en\-têtes de colonnes sont affichés, ils sont redimensionnés automatiquement en fonction de leur contenu.  Pour affecter une hauteur spécifique aux en\-têtes de colonnes, définissez la propriété <xref:System.Windows.Controls.DataGrid.ColumnHeaderHeight%2A?displayProperty=fullName>.  
  
### Redimensionnement à l'aide de la souris  
 Les utilisateurs peuvent redimensionner les lignes et les colonnes de <xref:System.Windows.Controls.DataGrid> en faisant glisser les séparateurs d'en\-tête des lignes et des colonnes.  <xref:System.Windows.Controls.DataGrid> prend également en charge le redimensionnement automatique des lignes et des colonnes en double\-cliquant sur le séparateur d'en\-tête de ligne ou de colonne.  Pour empêcher le redimensionnement de colonnes particulières par un utilisateur, affectez la valeur `false` à la propriété <xref:System.Windows.Controls.DataGridColumn.CanUserResize%2A?displayProperty=fullName> pour chaque colonne souhaitée.  Pour empêcher le redimensionnement de toutes les colonnes, affectez la valeur `false` à la propriété <xref:System.Windows.Controls.DataGrid.CanUserResizeColumns%2A?displayProperty=fullName>.  Pour empêcher le redimensionnement de toutes les lignes, affectez la valeur `false` à la propriété <xref:System.Windows.Controls.DataGrid.CanUserResizeRows%2A?displayProperty=fullName>.  
  
## Voir aussi  
 <xref:System.Windows.Controls.DataGrid>   
 <xref:System.Windows.Controls.DataGridColumn>   
 <xref:System.Windows.Controls.DataGridLength>   
 <xref:System.Windows.Controls.DataGridLengthConverter>