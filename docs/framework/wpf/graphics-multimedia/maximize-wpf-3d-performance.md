---
title: "Optimiser les performances 3D de WPF | Microsoft Docs"
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
  - "graphiques 3D (WPF)"
ms.assetid: 4bcf949d-d92f-4d8d-8a9b-1e4c61b25bf6
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# Optimiser les performances 3D de WPF
À mesure que vous utilisez [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] pour générer des contrôles 3D et inclure des scènes 3D dans vos applications, il est important de prendre en compte l'optimisation des performances. Cette rubrique fournit une liste de classes et de propriétés 3D qui ont des conséquences de performance pour votre application, avec les recommandations pour l'optimisation des performances lorsque vous les utilisez.  
  
 Cette rubrique suppose une connaissance avancée des fonctionnalités 3D de [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  Les suggestions dans ce document s'appliquent à la "couche de rendu 2", approximativement définie comme le matériel prenant en charge Pixel Shader version 2.0 et Vertex Shader version 2.0.  Pour plus d'informations, consultez [Couches de rendu graphiques](../../../../docs/framework/wpf/advanced/graphics-rendering-tiers.md).  
  
## Impact sur les performances : élevé  
  
|||  
|-|-|  
|Propriété|Recommandation|  
|<xref:System.Windows.Media.Brush>|Vitesse du pinceau \(de la plus rapide à la plus lente\) :<br /><br /> <xref:System.Windows.Media.SolidColorBrush><br /><br /> <xref:System.Windows.Media.LinearGradientBrush><br /><br /> <xref:System.Windows.Media.ImageBrush><br /><br /> <xref:System.Windows.Media.DrawingBrush> \(mis en cache\)<br /><br /> <xref:System.Windows.Media.VisualBrush> \(mis en cache\)<br /><br /> <xref:System.Windows.Media.RadialGradientBrush><br /><br /> <xref:System.Windows.Media.DrawingBrush> \(non mis en cache\)<br /><br /> <xref:System.Windows.Media.VisualBrush> \(non mis en cache\)|  
|<xref:System.Windows.UIElement.ClipToBoundsProperty>|Attribuez la valeur False à `Viewport3D.ClipToBounds` lorsque vous n'avez pas besoin que [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] découpe explicitement le contenu d'un <xref:System.Windows.Controls.Viewport3D> sur le rectangle du Viewport3D. Le découpage [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] anticrénelage peut s'avérer très lent, et `ClipToBounds` est activé \(lentement\) par défaut sur <xref:System.Windows.Controls.Viewport3D>.|  
|<xref:System.Windows.UIElement.IsHitTestVisible%2A>|Affectez la valeur false à `Viewport3D.IsHitTestVisible` à chaque fois que vous n'avez pas besoin de [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] pour prendre en compte le contenu d'un <xref:System.Windows.Controls.Viewport3D> lors de la réalisation d'un test d'atteinte de souris.  Le contenu 3D du test d'atteinte est effectué dans le logiciel et peut s'avérer lent avec de grands maillages. <xref:System.Windows.UIElement.IsHitTestVisible%2A> est activé \(lentement\) par défaut sur <xref:System.Windows.Controls.Viewport3D>.|  
|<xref:System.Windows.Media.Media3D.GeometryModel3D>|Créez des modèles différents uniquement lorsqu'ils ont besoin de matériaux ou transformations différents.  Sinon, essayez de fusionner de nombreuses instances <xref:System.Windows.Media.Media3D.GeometryModel3D> avec les mêmes matériaux et transformations dans quelques <xref:System.Windows.Media.Media3D.GeometryModel3D> et instances <xref:System.Windows.Media.Media3D.MeshGeometry3D> plus grandes.|  
|<xref:System.Windows.Media.Media3D.MeshGeometry3D>|L'animation du maillage, modifiant chaque vertex d'un maillage sur une base image par image, n'est pas toujours efficace dans [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. Pour réduire l'impact sur les performances des notifications de modifications lorsque chaque vertex est modifié, détachez le maillage de l'arborescence d'éléments visuels avant d'effectuer la modification par vertex.  Une fois le maillage modifié, rattachez\-le à l'arborescence d'éléments visuels.  En outre, essayez de réduire la taille des maillages qui seront animés de cette façon.|  
|Anticrénelage 3D|Pour augmenter la vitesse de rendu, désactivez l'échantillonnage multiple sur un <xref:System.Windows.Controls.Viewport3D> en affectant à la propriété attachée <xref:System.Windows.Media.RenderOptions.EdgeMode%2A> la valeur `Aliased`.  Par défaut, l'anticrénelage 3D est désactivé sur [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)] et activé sur [!INCLUDE[TLA#tla_longhorn](../../../../includes/tlasharptla-longhorn-md.md)] avec 4 exemples par pixel.|  
|Texte|Le texte vivant dans une scène 3D \(vivant car il se trouve dans un <xref:System.Windows.Media.DrawingBrush> ou <xref:System.Windows.Media.VisualBrush>\) peut s'avérer lent.  Essayez d'utiliser à la place \(via <xref:System.Windows.Media.Imaging.RenderTargetBitmap>\) des images du texte à moins que le texte change.|  
|<xref:System.Windows.Media.TileBrush>|Si vous devez utiliser un <xref:System.Windows.Media.VisualBrush> ou un <xref:System.Windows.Media.DrawingBrush> dans une scène 3D car le contenu du pinceau n'est pas statique, essayez de mettre en cache le pinceau \(en affectant à la propriété attachée <xref:System.Windows.Media.RenderOptions.CachingHint%2A> la valeur `Cache`\).  Définissez les seuils de l'invalidation de l'échelle minimum \(avec les propriétés attachées <xref:System.Windows.Media.RenderOptions.CacheInvalidationThresholdMinimum%2A> et <xref:System.Windows.Media.RenderOptions.CacheInvalidationThresholdMaximum%2A>\) et maximum afin que les pinceaux mis en cache ne soient pas trop fréquemment régénérés, tout en maintenant encore votre niveau de qualité souhaitée.  Par défaut, <xref:System.Windows.Media.DrawingBrush> et <xref:System.Windows.Media.VisualBrush> ne sont pas mis en cache, ce qui signifie qu'à chaque fois que quelque chose peint avec le pinceau doit être restitué à nouveau, le contenu entier du pinceau doit d'abord être restitué à nouveau sur une surface intermédiaire.|  
|<xref:System.Windows.Media.Effects.BitmapEffect>|<xref:System.Windows.Media.Effects.BitmapEffect> force tout le contenu affecté à être restitué sans accélération matérielle.  Pour de meilleures performances, n'utilisez pas <xref:System.Windows.Media.Effects.BitmapEffect>.|  
  
## Impact sur les performances : moyen  
  
|||  
|-|-|  
|Propriété|Recommandation|  
|<xref:System.Windows.Media.Media3D.MeshGeometry3D>|Lorsqu'un maillage est défini comme triangles attenants avec des sommets partagés et que ces derniers ont la même position, les coordonnées normales de texture définissent chaque vertex partagé une seule fois, puis définissent vos triangles par index avec <xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A>.|  
|<xref:System.Windows.Media.ImageBrush>|Essayez de réduire des tailles de texture lorsque vous avez le contrôle explicite sur la taille \(lorsque vous utilisez un <xref:System.Windows.Media.Imaging.RenderTargetBitmap> et\/ou un <xref:System.Windows.Media.ImageBrush>\).  Notez que les textures de résolution inférieures peuvent réduire la qualité visuelle, donc essayez de rechercher le bon équilibre entre qualité et performance.|  
|Opacité|Lorsque vous restituez le contenu 3D translucide \(comme les réflexions\), utilisez les propriétés d'opacité sur les pinceaux ou les matériaux \(via <xref:System.Windows.Media.Brush.Opacity%2A> ou <xref:System.Windows.Media.Media3D.DiffuseMaterial.Color%2A>\) au lieu de créer un <xref:System.Windows.Controls.Viewport3D> translucide séparé en définissant `Viewport3D.Opacity` à une valeur inférieure à 1.|  
|<xref:System.Windows.Controls.Viewport3D>|Réduisez le nombre d'objets <xref:System.Windows.Controls.Viewport3D> que vous utilisez dans une scène.  Mettez de nombreux modèles 3D dans le même Viewport3D plutôt que de créer des instances Viewport3D séparées pour chaque modèle.|  
|<xref:System.Windows.Freezable>|En général, il est avantageux de réutiliser <xref:System.Windows.Media.Media3D.MeshGeometry3D>, <xref:System.Windows.Media.Media3D.GeometryModel3D>, pinceaux et matériaux.  Tous peuvent avoir plusieurs parents puisqu'ils sont dérivés de `Freezable`.|  
|<xref:System.Windows.Freezable>|Appelez la méthode <xref:System.Windows.Freezable.Freeze%2A> sur les Freezables lorsque leurs propriétés restent inchangées dans votre application.  Le verrouillage peut diminuer le jeu de travail et augmenter la vitesse.|  
|<xref:System.Windows.Media.Brush>|Utilisez <xref:System.Windows.Media.ImageBrush> au lieu de <xref:System.Windows.Media.VisualBrush> ou <xref:System.Windows.Media.DrawingBrush> lorsque le contenu du pinceau ne change pas.  Le contenu 2D peut être converti en <xref:System.Windows.Controls.Image> via <xref:System.Windows.Media.Imaging.RenderTargetBitmap> puis peut être utilisé dans un <xref:System.Windows.Media.ImageBrush>.|  
|<xref:System.Windows.Media.Media3D.GeometryModel3D.BackMaterial%2A>|N'utilisez pas <xref:System.Windows.Media.Media3D.GeometryModel3D.BackMaterial%2A> à moins que vous ne deviez réellement consulter les faces arrière de votre <xref:System.Windows.Media.Media3D.GeometryModel3D>.|  
|<xref:System.Windows.Media.Media3D.Light>|Vitesse légère \(de la plus rapide à la plus lente\) :<br /><br /> <xref:System.Windows.Media.Media3D.AmbientLight><br /><br /> <xref:System.Windows.Media.Media3D.DirectionalLight><br /><br /> <xref:System.Windows.Media.Media3D.PointLight><br /><br /> <xref:System.Windows.Media.Media3D.SpotLight>|  
|<xref:System.Windows.Media.Media3D.MeshGeometry3D>|Essayez de garder les tailles de maillage sous les limites suivantes :<br /><br /> <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> : 20 001 instances <xref:System.Windows.Media.Media3D.Point3D><br /><br /> <xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A> : 60 003 instances <xref:System.Int32>|  
|<xref:System.Windows.Media.Media3D.Material>|Vitesse matérielle \(de la plus rapide à la plus lente\) :<br /><br /> <xref:System.Windows.Media.Media3D.EmissiveMaterial><br /><br /> <xref:System.Windows.Media.Media3D.DiffuseMaterial><br /><br /> <xref:System.Windows.Media.Media3D.SpecularMaterial>|  
|<xref:System.Windows.Media.Brush>|[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 3D n'accepte pas les pinceaux invisibles \(pinceaux ambiants noirs, pinceaux clairs, etc.\) de manière homogène.  Envisagez omettant ces derniers de votre scène.|  
|<xref:System.Windows.Media.Media3D.MaterialGroup>|Chaque <xref:System.Windows.Media.Media3D.Material> dans un <xref:System.Windows.Media.Media3D.MaterialGroup> provoque un autre passe de rendu, ce qui signifie que l'intégration de nombreux matériaux, même simples, peut augmenter considérablement la demande de remplissage sur votre GPU.  Réduisez le nombre de matériaux dans votre <xref:System.Windows.Media.Media3D.MaterialGroup>.|  
  
## Impact sur les performances : faible  
  
|||  
|-|-|  
|Propriété|Recommandation|  
|<xref:System.Windows.Media.Media3D.Transform3DGroup>|Lorsque vous n'avez pas besoin d'animation ou de liaison de données, au lieu d'utiliser un groupe de transformations contenant plusieurs transformations, utilisez un <xref:System.Windows.Media.Media3D.MatrixTransform3D> unique, en le définissant comme étant le produit de toutes les transformations qui existerait autrement indépendamment dans le groupe de transformations.|  
|<xref:System.Windows.Media.Media3D.Light>|Réduisez le nombre de lumières dans votre scène.  Trop de lumières dans une scène forceront [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] à revenir au rendu logiciel.  Les limites sont d'environ 110 objets <xref:System.Windows.Media.Media3D.DirectionalLight>, 70 objets <xref:System.Windows.Media.Media3D.PointLight> ou 40 objets <xref:System.Windows.Media.Media3D.SpotLight>.|  
|<xref:System.Windows.Media.Media3D.ModelVisual3D>|Séparez les objets en mouvement des objets statiques en les mettant dans des instances <xref:System.Windows.Media.Media3D.ModelVisual3D> séparées.  ModelVisual3D est plus "lourd" que <xref:System.Windows.Media.Media3D.GeometryModel3D> car il met en cache des limites transformées.  GeometryModel3D est optimisé pour être un modèle ; ModelVisual3D est optimisé pour être un nœud de scène.  Utilisez ModelVisual3D pour mettre des instances partagées de GeometryModel3D dans la scène.|  
|<xref:System.Windows.Media.Media3D.Light>|Réduisez le nombre de fois où vous modifiez le nombre de lumières dans la scène.  Chaque modification de lumière force une régénération et une recompilation du nuanceur, à moins que cette configuration n'ait existé précédemment \(et donc avait son nuanceur mis en cache\).|  
|Lumière|Les lumières noires ne seront pas visibles, mais s'ajouteront au temps de rendu, vous pouvez envisager de les omettre.|  
|<xref:System.Windows.Media.Media3D.MeshGeometry3D>|Pour réduire le temps de construction de grandes collections dans [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], tel qu'un <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A>, <xref:System.Windows.Media.Media3D.MeshGeometry3D.Normals%2A>, <xref:System.Windows.Media.Media3D.MeshGeometry3D.TextureCoordinates%2A> et <xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A> MeshGeometry3D, dimensionnez au préalable les collections avant le remplissage de valeur.  Si possible, passez les structures de données préremplies des constructeurs des collections en tant que tableaux ou listes.|  
  
## Voir aussi  
 [Vue d'ensemble des graphiques 3D](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)