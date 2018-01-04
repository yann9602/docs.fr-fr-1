---
title: Optimiser les performances 3D de WPF
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: 3-D graphics [WPF]
ms.assetid: 4bcf949d-d92f-4d8d-8a9b-1e4c61b25bf6
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 45053762a4782544531a09c92531b26f99663016
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="maximize-wpf-3d-performance"></a>Optimiser les performances 3D de WPF
Lorsque vous utilisez le [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] pour générer des contrôles 3D et inclure des scènes 3D dans vos applications, il est important de considérer l’optimisation des performances. Cette rubrique fournit une liste de classes et propriétés qui ont des implications en matière de performances pour votre application, ainsi que des recommandations pour optimiser les performances lorsque vous les utilisez 3D.  
  
 Cette rubrique suppose une connaissance approfondie de [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] fonctionnalités 3D. Les suggestions dans ce document s’appliquent à « couche de rendu 2 », approximativement définie comme le matériel prenant en charge la version 2.0 du nuanceur de pixels et la version 2.0 du nuanceur de sommets. Pour plus d’informations, consultez [Graphics Rendering Tiers](../../../../docs/framework/wpf/advanced/graphics-rendering-tiers.md).  
  
## <a name="performance-impact-high"></a>Impact sur les performances : élevé  
  
|Propriété|Recommandation|  
|-|-|  
|<xref:System.Windows.Media.Brush>|Vitesse du pinceau (plus rapide à la plus lente) :<br /><br /> <xref:System.Windows.Media.SolidColorBrush><br /><br /> <xref:System.Windows.Media.LinearGradientBrush><br /><br /> <xref:System.Windows.Media.ImageBrush><br /><br /> <xref:System.Windows.Media.DrawingBrush>(mise en cache)<br /><br /> <xref:System.Windows.Media.VisualBrush>(mise en cache)<br /><br /> <xref:System.Windows.Media.RadialGradientBrush><br /><br /> <xref:System.Windows.Media.DrawingBrush>(non mis en cache)<br /><br /> <xref:System.Windows.Media.VisualBrush>(non mis en cache)|  
|<xref:System.Windows.UIElement.ClipToBoundsProperty>|Définir `Viewport3D.ClipToBounds` sur false, chaque fois que vous n’avez pas besoin d’avoir [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] explicitement détourer le contenu d’un <xref:System.Windows.Controls.Viewport3D> au rectangle de la de Viewport3D. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]l’extrait de la non crénelé peut être très lente, et `ClipToBounds` est activé (lentement) par défaut sur <xref:System.Windows.Controls.Viewport3D>.|  
|<xref:System.Windows.UIElement.IsHitTestVisible%2A>|Définissez `Viewport3D.IsHitTestVisible` sur false, chaque fois que vous n’avez pas besoin [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] à prendre en compte le contenu d’un <xref:System.Windows.Controls.Viewport3D> lorsque souris effectue le test de positionnement.  Contenu 3D du test d’atteinte est effectué dans le logiciel et peut être lent avec de grands maillages. <xref:System.Windows.UIElement.IsHitTestVisible%2A>est activé (lentement) par défaut sur <xref:System.Windows.Controls.Viewport3D>.|  
|<xref:System.Windows.Media.Media3D.GeometryModel3D>|Créer des modèles différents uniquement lorsqu’ils ont besoin des matériaux ou transformations différents.  Sinon, essayez de fusionner de nombreuses <xref:System.Windows.Media.Media3D.GeometryModel3D> instances avec les mêmes matériaux et transformations dans quelques supérieure <xref:System.Windows.Media.Media3D.GeometryModel3D> et <xref:System.Windows.Media.Media3D.MeshGeometry3D> instances.|  
|<xref:System.Windows.Media.Media3D.MeshGeometry3D>|Animation de maillage : modification des sommets individuels d’un maillage par image, n’est pas toujours efficace dans [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  Pour réduire l’impact sur les performances de notifications de modifications lorsque chaque vertex est modifié, détachez le maillage de l’arborescence d’éléments visuels avant d’effectuer la modification par vertex.  Une fois que le maillage a été modifié, le rattacher à l’arborescence visuelle.  En outre, essayez de réduire la taille des mailles qui seront animées de cette façon.|  
|Anticrénelage 3D|Pour augmenter la vitesse de rendu, désactivez l’échantillonnage multiple sur un <xref:System.Windows.Controls.Viewport3D> en définissant la propriété jointe <xref:System.Windows.Media.RenderOptions.EdgeMode%2A> à `Aliased`.  Par défaut, l’anticrénelage 3D est désactivé sur [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)] et activé sur [!INCLUDE[TLA#tla_longhorn](../../../../includes/tlasharptla-longhorn-md.md)] avec 4 exemples par pixel.|  
|Texte|Texte vivant dans une scène 3D (live, car il est un <xref:System.Windows.Media.DrawingBrush> ou <xref:System.Windows.Media.VisualBrush>) peut être lente. Essayez d’utiliser des images du texte à la place (via <xref:System.Windows.Media.Imaging.RenderTargetBitmap>), sauf si le texte est modifié.|  
|<xref:System.Windows.Media.TileBrush>|Si vous devez utiliser un <xref:System.Windows.Media.VisualBrush> ou un <xref:System.Windows.Media.DrawingBrush> dans une scène 3D, car le contenu du pinceau n’est pas statique, essayez de la mise en cache le pinceau (définition de la propriété jointe <xref:System.Windows.Media.RenderOptions.CachingHint%2A> à `Cache`).  Définir des seuils de l’invalidation de l’échelle minimale et maximale (avec les propriétés attachées <xref:System.Windows.Media.RenderOptions.CacheInvalidationThresholdMinimum%2A> et <xref:System.Windows.Media.RenderOptions.CacheInvalidationThresholdMaximum%2A>) afin que les pinceaux mis en cache ne soient régénérés trop fréquemment, tout en conservant votre niveau de qualité souhaitée.  Par défaut, <xref:System.Windows.Media.DrawingBrush> et <xref:System.Windows.Media.VisualBrush> ne sont pas mis en cache, ce qui signifie que que chaque fois que quelque chose peint avec le pinceau doit être restitué à nouveau, le contenu entier du pinceau doit tout d’abord être restitué à nouveau une surface intermédiaire.|  
|<xref:System.Windows.Media.Effects.BitmapEffect>|<xref:System.Windows.Media.Effects.BitmapEffect>force tout le contenu affecté à être restitué sans accélération matérielle.  Pour des performances optimales, n’utilisez pas <xref:System.Windows.Media.Effects.BitmapEffect>.|  
  
## <a name="performance-impact-medium"></a>Impact sur les performances : moyen  
  
|Propriété|Recommandation|  
|-|-|  
|<xref:System.Windows.Media.Media3D.MeshGeometry3D>|Lorsqu’un maillage est défini comme triangles attenants avec des sommets partagés et ces derniers ont la même position, normal et les coordonnées de texture, définissent chaque vertex partagé une seule fois et définissez ensuite vos triangles par index avec <xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A>.|  
|<xref:System.Windows.Media.ImageBrush>|Essayez de réduire des tailles de texture lorsque vous avez un contrôle explicite sur la taille (lorsque vous utilisez un <xref:System.Windows.Media.Imaging.RenderTargetBitmap> et/ou un <xref:System.Windows.Media.ImageBrush>).  Notez que les textures de résolution inférieures peuvent réduire la qualité visuelle, alors que vous essayez de trouver le juste équilibre entre la qualité et de performances.|  
|Opacité|Lors du rendu 3D translucide contenu (tels que des réflexions), utilisez les propriétés d’opacité sur les pinceaux ou les matériaux (via <xref:System.Windows.Media.Brush.Opacity%2A> ou <xref:System.Windows.Media.Media3D.DiffuseMaterial.Color%2A>) au lieu de créer un distinct translucide <xref:System.Windows.Controls.Viewport3D> en définissant `Viewport3D.Opacity` sur une valeur inférieure à 1.|  
|<xref:System.Windows.Controls.Viewport3D>|Réduire le nombre de <xref:System.Windows.Controls.Viewport3D> objets vous utilisez dans une scène.  Placer de nombreux modèles 3D dans le même Viewport3D plutôt que de créer des instances Viewport3D distincts pour chaque modèle.|  
|<xref:System.Windows.Freezable>|En règle générale, il est avantageux de réutiliser <xref:System.Windows.Media.Media3D.MeshGeometry3D>, <xref:System.Windows.Media.Media3D.GeometryModel3D>, pinceaux et matériaux.  Tous sont peuvent avoir plusieurs parents puisqu’ils sont dérivés de `Freezable`.|  
|<xref:System.Windows.Freezable>|Appelez le <xref:System.Windows.Freezable.Freeze%2A> méthode sur les objets Freezable lorsque leurs propriétés restent inchangées dans votre application.  Gel peut réduire la plage de travail et augmenter la vitesse.|  
|<xref:System.Windows.Media.Brush>|Utilisez <xref:System.Windows.Media.ImageBrush> au lieu de <xref:System.Windows.Media.VisualBrush> ou <xref:System.Windows.Media.DrawingBrush> lorsque le contenu du pinceau ne change pas.  Le contenu 2D peut être converti en un <xref:System.Windows.Controls.Image> via <xref:System.Windows.Media.Imaging.RenderTargetBitmap> , puis utilisé dans une <xref:System.Windows.Media.ImageBrush>.|  
|<xref:System.Windows.Media.Media3D.GeometryModel3D.BackMaterial%2A>|N’utilisez pas <xref:System.Windows.Media.Media3D.GeometryModel3D.BackMaterial%2A> , sauf si vous avez besoin afficher les faces arrière de votre <xref:System.Windows.Media.Media3D.GeometryModel3D>.|  
|<xref:System.Windows.Media.Media3D.Light>|Vitesse de la lumière (plus rapide à la plus lente) :<br /><br /> <xref:System.Windows.Media.Media3D.AmbientLight><br /><br /> <xref:System.Windows.Media.Media3D.DirectionalLight><br /><br /> <xref:System.Windows.Media.Media3D.PointLight><br /><br /> <xref:System.Windows.Media.Media3D.SpotLight>|  
|<xref:System.Windows.Media.Media3D.MeshGeometry3D>|Essayez de conserver les tailles de maillage sous ces limites :<br /><br /> <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A>: 20,001 <xref:System.Windows.Media.Media3D.Point3D> instances<br /><br /> <xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A>: 60,003 <xref:System.Int32> instances|  
|<xref:System.Windows.Media.Media3D.Material>|Vitesse matérielle (plus rapide à la plus lente) :<br /><br /> <xref:System.Windows.Media.Media3D.EmissiveMaterial><br /><br /> <xref:System.Windows.Media.Media3D.DiffuseMaterial><br /><br /> <xref:System.Windows.Media.Media3D.SpecularMaterial>|  
|<xref:System.Windows.Media.Brush>|[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]3D n’accepte pas les pinceaux invisibles (pinceaux ambiants noirs, pinceaux clairs, etc.) de façon cohérente.  Envisagez d’omettre ceux-ci de votre scène.|  
|<xref:System.Windows.Media.Media3D.MaterialGroup>|Chaque <xref:System.Windows.Media.Media3D.Material> dans un <xref:System.Windows.Media.Media3D.MaterialGroup> provoque un autre passe de rendu, par conséquent, y compris les nombreux matériaux, même simples, peut augmenter considérablement la demande de remplissage sur votre GPU.  Réduire le nombre de documents dans votre <xref:System.Windows.Media.Media3D.MaterialGroup>.|  
  
## <a name="performance-impact-low"></a>Impact sur les performances : faible  
  
|Propriété|Recommandation|  
|-|-|  
|<xref:System.Windows.Media.Media3D.Transform3DGroup>|Lorsque vous n’avez pas besoin d’animation ou de liaison de données, au lieu d’utiliser un groupe de transformations contenant plusieurs transformations, utilisent un seul <xref:System.Windows.Media.Media3D.MatrixTransform3D>, la valeur sera le produit de toutes les transformations qui existerait autrement indépendamment dans le groupe de transformation.|  
|<xref:System.Windows.Media.Media3D.Light>|Réduisez le nombre de lumières dans votre scène. Trop de lumières dans une scène force [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] à revenir au rendu logiciel.  Les limites sont d’environ 110 <xref:System.Windows.Media.Media3D.DirectionalLight> objets, 70 <xref:System.Windows.Media.Media3D.PointLight> objets ou 40 <xref:System.Windows.Media.Media3D.SpotLight> objets.|  
|<xref:System.Windows.Media.Media3D.ModelVisual3D>|Séparer le déplacement d’objets à partir des objets statiques en les plaçant dans distinct <xref:System.Windows.Media.Media3D.ModelVisual3D> instances.  ModelVisual3D est « plus » de <xref:System.Windows.Media.Media3D.GeometryModel3D> , car elle met en cache des limites transformées.  GeometryModel3D est optimisé pour être un modèle ; ModelVisual3D est optimisé pour être un nœud de scène.  Utilisez ModelVisual3D pour placer des instances partagées de GeometryModel3D dans la scène.|  
|<xref:System.Windows.Media.Media3D.Light>|Réduire le nombre de fois que vous changez le nombre de lumières dans la scène.  Chaque modification de lumière force une régénération du nuanceur et la recompilation, sauf si cette configuration n’ait existé précédemment (et donc avait son nuanceur mis en cache).|  
|Clair|Noir lumières ne seront pas visibles, mais ils seront ajoutent pour restituer l’heure ; envisagez de les omettre.|  
|<xref:System.Windows.Media.Media3D.MeshGeometry3D>|Pour réduire le temps de construction de grandes collections dans [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], telles que d’un MeshGeometry3D <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A>, <xref:System.Windows.Media.Media3D.MeshGeometry3D.Normals%2A>, <xref:System.Windows.Media.Media3D.MeshGeometry3D.TextureCoordinates%2A>, et <xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A>, dimensionnez au préalable les collections avant le remplissage de valeur. Si possible, passer des structures de données prédéfinie de constructeurs les collections telles que les tableaux ou listes.|  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble des graphiques 3D](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)
