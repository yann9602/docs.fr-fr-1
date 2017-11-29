---
title: Vue d'ensemble des graphiques 3D
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- 3-D graphics [WPF]
- graphics [WPF], 3-D
ms.assetid: 67f31ed4-e36b-4b02-9889-dcce245d7afc
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 979cc7580471f616d39056f541b8374b372e8e88
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="3-d-graphics-overview"></a>Vue d'ensemble des graphiques 3D
<a name="introduction"></a>La fonctionnalité [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] dans [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] permet aux développeurs de dessiner, transformer et animer des graphiques 3D avec du balisage et du code procédural. Les développeurs peuvent combiner les graphiques [!INCLUDE[TLA#tla_2d](../../../../includes/tlasharptla-2d-md.md)] et [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] pour créer des contrôles riches, fournir des illustrations complexes de données ou améliorer l’expérience utilisateur pour l’interface de l’application. La prise en charge de [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] n’est pas conçue pour fournir une plateforme de développement de jeu complète. Cette rubrique fournit une vue d’ensemble de la fonctionnalité [!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)] dans le système graphique [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
 
  
<a name="threed_in_2d"></a>   
## <a name="3-d-in-a-2-d-container"></a>3D dans un conteneur 2D  
 [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)]contenu graphique [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] est encapsulé dans un élément, <xref:System.Windows.Controls.Viewport3D>, qui peut participer à la structure de l’élément à deux dimensions. Le système graphique traite <xref:System.Windows.Controls.Viewport3D> comme un élément visuel à deux dimensions comme de nombreux autres dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. <xref:System.Windows.Controls.Viewport3D>fonctionne comme une fenêtre, une fenêtre d’affichage, dans une scène 3D. Plus précisément, c’est une surface sur laquelle une scène [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] est projetée.  
  
 Dans un conventionnelle [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] application, utilisez <xref:System.Windows.Controls.Viewport3D> comme vous le feriez pour un autre élément conteneur comme grille ou zone de dessin.  Bien que vous puissiez utiliser <xref:System.Windows.Controls.Viewport3D> avec d’autres [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] dessiner des objets dans le même graphique de scène, vous ne pouvez pas interpénétrer [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] et [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] objets au sein d’un <xref:System.Windows.Controls.Viewport3D>.  Cette rubrique se concentrera sur comment dessiner [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] graphics à l’intérieur de la <xref:System.Windows.Controls.Viewport3D>.  
  
<a name="coord_space"></a>   
## <a name="3-d-coordinate-space"></a>Espace de coordonnées 3D  
 Le système de coordonnées [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pour les graphiques [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] localise l’origine dans le coin supérieur gauche de la zone de rendu (en général l’écran). Dans le système [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)], les valeurs positives de l’axe des X continuent à droite et les valeurs positives de l’axe des Y positives continuent vers le bas.  Dans le système de coordonnées [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)], toutefois, l’origine se trouve dans le centre de la zone de rendu, avec les valeurs positives de l’axe des X continuant à droite mais celles de l’axe des Y continuant vers le haut à la place, alors que les valeurs positives de l’axe des Z continuent vers l’extérieur à partir de l’origine, vers le visionneur.  
  
 ![Systèmes de coordonnées](../../../../docs/framework/wpf/graphics-multimedia/media/coordsystem-1.png "CoordSystem-1")  
Représentations de système de coordonnées 2D et 3D classiques  
  
 L’espace défini par ces axes est le système de référence stationnaire pour les objets [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Lorsque vous générez des modèles dans cet espace et créez des lumières et des caméras pour les consulter, il est utile de distinguer ce frame stationnaire de référence, ou « espace universel » du frame local de référence que vous créez pour chaque modèle lorsque vous lui appliquez des transformations. N’oubliez également pas que les objets dans l’espace universel peuvent sembler entièrement différents, ou ne pas du tout être visibles, en fonction des paramètres de lumière et de caméra, mais que la position de la caméra ne modifie pas l’emplacement des objets dans l’espace universel.  
  
<a name="cameras"></a>   
## <a name="cameras-and-projections"></a>Caméras et projections  
 Les développeurs qui travaillent dans [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] sont habitués à positionner des primitives de dessin sur un écran à deux dimensions. Lorsque vous créez une scène [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)], il est important de vous rappeler que vous créez en fait une représentation [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] des objets [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)]. Comme une scène [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] a un aspect différent en fonction de la perspective du spectateur, vous devez spécifier ce point de vue. Le <xref:System.Windows.Media.Media3D.Camera> classe vous permet de spécifier ce point de vue pour une [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] scène.  
  
 Une autre façon de comprendre comment une scène [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] est représentée sur une surface [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] est de décrire la scène comme une projection sur la surface d’affichage. Le <xref:System.Windows.Media.Media3D.ProjectionCamera> vous permet de spécifier des projections différentes et leurs propriétés pour modifier la manière dont le spectateur consulte [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] modèles. A <xref:System.Windows.Media.Media3D.PerspectiveCamera> spécifie une projection qui dessine en raccourci la scène.  En d’autres termes, le <xref:System.Windows.Media.Media3D.PerspectiveCamera> propose la perspective de point de fuite.  Vous pouvez spécifier la position de la caméra dans l’espace de coordonnées de la scène, la direction et le champ de vue pour la caméra, et un vecteur qui définit le sens de « haut » dans la scène. Le diagramme suivant illustre le <xref:System.Windows.Media.Media3D.PerspectiveCamera>de projection.  
  
 Le <xref:System.Windows.Media.Media3D.ProjectionCamera.NearPlaneDistance%2A> et <xref:System.Windows.Media.Media3D.ProjectionCamera.FarPlaneDistance%2A> propriétés de <xref:System.Windows.Media.Media3D.ProjectionCamera> limiter la plage de projection de la caméra. Étant donné que les caméras peuvent se trouver n’importe où dans la scène, il est possible de placer la caméra à l’intérieur d’un modèle ou très près d’un modèle, ce qui fait qu’il est difficile de bien distinguer les objets.  <xref:System.Windows.Media.Media3D.ProjectionCamera.NearPlaneDistance%2A>vous permet de spécifier une distance minimale à partir de la caméra au-delà de laquelle les objets ne seront pas dessinés.  À l’inverse, <xref:System.Windows.Media.Media3D.ProjectionCamera.FarPlaneDistance%2A> vous permet de spécifier une distance de la caméra au-delà de laquelle les objets ne seront pas dessinés, ce qui garantit que les objets trop loin pour être reconnus ne sont pas inclus dans la scène.  
  
 ![Le programme d’installation de la caméra](../../../../docs/framework/wpf/graphics-multimedia/media/coordsystem-6.png "CoordSystem-6")  
Position d'une caméra  
  
 <xref:System.Windows.Media.Media3D.OrthographicCamera>Spécifie une projection orthographique d’un [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] modèle pour un [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] surface visuelle. Comme les autres caméras, elle spécifie une position, la direction d’affichage et la direction « vers le haut ». Contrairement aux <xref:System.Windows.Media.Media3D.PerspectiveCamera>, toutefois, <xref:System.Windows.Media.Media3D.OrthographicCamera> décrit une projection qui n’inclut pas de perspective. En d’autres termes, <xref:System.Windows.Media.Media3D.OrthographicCamera> décrit une zone d’affichage dont les côtés sont parallèles, au lieu d’un dont les côtés se rejoignent à un point de l’appareil photo. L’illustration suivante montre le même modèle tel qu’affiché à l’aide de <xref:System.Windows.Media.Media3D.PerspectiveCamera> et <xref:System.Windows.Media.Media3D.OrthographicCamera>.  
  
 ![Projection orthographique et en perspective](../../../../docs/framework/wpf/graphics-multimedia/media/camera-projections4.png "Camera_projections4")  
Projections en perspective et orthographiques  
  
 Le code suivant montre des paramètres de caméra typiques.  
  
 [!code-csharp[3dgallery_procedural_snip#Basic3DShapeCodeExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/Basic3DShapeExample.cs#basic3dshapecodeexampleinline1)]
 [!code-vb[3dgallery_procedural_snip#Basic3DShapeCodeExampleInline1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/3DGallery_procedural_snip/visualbasic/basic3dshapeexample.vb#basic3dshapecodeexampleinline1)]  
  
<a name="models_meshes"></a>   
## <a name="model-and-mesh-primitives"></a>Modèle et primitives de maillage  
  
 <xref:System.Windows.Media.Media3D.Model3D>est la classe de base abstraite qui représente un type générique [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] objet. Pour générer un [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] scène, vous avez besoin de quelques objets à afficher, et les objets qui composent le graphique de scène dérivent <xref:System.Windows.Media.Media3D.Model3D>. Actuellement, le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] prend en charge la modélisation des géométries avec <xref:System.Windows.Media.Media3D.GeometryModel3D>. Le <xref:System.Windows.Media.Media3D.GeometryModel3D.Geometry%2A> propriété de ce modèle prend un maillage de base.  
  
 Pour générer un modèle, commencez par créer une primitive, ou maillage. Une primitive [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] est une collection de sommets qui forment une seule entité [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)]. La plupart des systèmes [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] fournissent des primitives modelées sur la figure fermée la plus simple : un triangle défini par trois sommets.  Les trois points d’un triangle étant coplanaires, vous pouvez continuer à ajouter des triangles pour modeler des formes complexes, appelées mailles.  
  
 Le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] système fournit actuellement les <xref:System.Windows.Media.Media3D.MeshGeometry3D> (classe), qui vous permet de spécifier n’importe quelle géométrie ; il ne prend pas en charge prédéfinis [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] primitives, tels que les domaines et les formulaires cubiques. Commencer à créer un <xref:System.Windows.Media.Media3D.MeshGeometry3D> en spécifiant une liste des sommets de triangle comme sa <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> propriété. Chaque vertex est spécifié comme un <xref:System.Windows.Media.Media3D.Point3D>.  (Dans [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], spécifiez cette propriété comme une liste de nombres groupés par trois qui représentent les coordonnées de chaque sommet.) Selon sa géométrie, votre maillage peut être composé de nombreux triangles, certains d'entre eux partageant les mêmes angles (sommets). Pour dessiner le maillage correctement, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a besoin d’informations sur les sommets qui sont partagés par les triangles respectifs. Vous fournissez ces informations en spécifiant une liste d’indices de triangle avec la <xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A> propriété. Cette liste spécifie l’ordre dans lequel les points spécifiés dans la <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> liste détermine un triangle.  
  
 [!code-xaml[basic3d#Basic3DXAML3DN3](../../../../samples/snippets/xaml/VS_Snippets_Wpf/Basic3D/XAML/Window1.xaml#basic3dxaml3dn3)]  
  
 Dans l’exemple précédent, le <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> liste spécifie huit sommets pour définir un maillage en forme de cube. Le <xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A> propriété spécifie une liste de douze groupes de trois index.  Chaque nombre dans la liste fait référence à un offset dans le <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> liste.  Par exemple, les trois premiers sommets spécifiés par la <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> liste sont (1,1,0), (0,1,0) et (0,0,0). Les trois premiers index spécifiés par le <xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A> liste sont 0, 2 et 1, qui correspond à la première, troisième et deuxième points dans le <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> liste. Par conséquent, le premier triangle qui compose le modèle de cube sera composé de (1,1,0) à (0,1,0) à (0,0,0), et les onze triangles restants seront déterminés de la même façon.  
  
 Vous pouvez continuer la définition du modèle en spécifiant des valeurs pour le <xref:System.Windows.Media.Media3D.MeshGeometry3D.Normals%2A> et <xref:System.Windows.Media.Media3D.MeshGeometry3D.TextureCoordinates%2A> propriétés.  Pour restituer la surface du modèle, le système graphique a besoin d’informations sur la direction à laquelle la surface fait face sur tout triangle donné. Il utilise ces informations pour effectuer des calculs d’éclairage pour le modèle : les surfaces qui font face directement à une source de lumière apparaissent plus claires que celles inclinées par rapport à la lumière. Même si [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] peut déterminer les vecteurs normaux par défaut en utilisant les coordonnées de position, vous pouvez également spécifier différents vecteurs normaux pour reproduire approximativement l’apparence des surfaces courbes.  
  
 Le <xref:System.Windows.Media.Media3D.MeshGeometry3D.TextureCoordinates%2A> propriété spécifie une collection de <xref:System.Windows.Point>qui indique au système graphique comment mapper les coordonnées qui déterminent la façon dont une texture est dessinée sur les sommets du maillage. <xref:System.Windows.Media.Media3D.MeshGeometry3D.TextureCoordinates%2A>sont spécifiés comme une valeur comprise entre 0 et 1 (inclus).  Comme avec la <xref:System.Windows.Media.Media3D.MeshGeometry3D.Normals%2A> propriété, le système graphique peut calculer des coordonnées de texture par défaut, mais vous pouvez choisir de définir les coordonnées de texture différentes pour contrôler le mappage d’une texture qui inclut la partie d’un modèle extensible, par exemple. Vous trouverez plus d’informations sur les coordonnées de texture dans les rubriques suivantes, ou dans le kit de développement managé Direct3D.  
  
 L’exemple suivant montre comment créer une face du modèle de cube en code procédural. Notez que vous pouvez dessiner le cube entier comme un GeometryModel3D simple. Cet exemple dessine la face du cube en tant que modèle distinct pour appliquer ultérieurement des textures séparées à chaque face.  
  
 [!code-csharp[3doverview#3DOverview3DN6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn6)]
 [!code-vb[3doverview#3DOverview3DN6](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn6)]  
  
 [!code-csharp[3doverview#3DOverview3DN7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn7)]
 [!code-vb[3doverview#3DOverview3DN7](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn7)]  
  
<a name="materials"></a>   
## <a name="applying-materials-to-the-model"></a>Application de matériaux au modèle  
  
 Pour qu’une maille ressemble à un objet en trois dimensions, elle doit avoir une texture appliquée pour couvrir la surface définie par ses sommets et triangles afin de pouvoir être éclairée et projetée par la caméra. Dans [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)], vous utilisez la <xref:System.Windows.Media.Brush> classe pour appliquer des couleurs, les modèles, les dégradés ou autre contenu visuel aux zones de l’écran.  L’apparence des objets [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)], cependant, est une fonction du modèle d’éclairage, pas seulement de la couleur ou du modèle qui leur est appliqué. Les objets réels reflètent différemment la lumière selon la qualité de leurs surfaces : les surfaces brillantes ne semblent pas si rugueuses que les surfaces mates, et certains objets semblent absorber la lumière alors que d’autres brillent. Vous pouvez appliquer les mêmes pinceaux aux objets [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] que ceux que vous pouvez appliquer aux objets [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)], mais vous ne pouvez pas les appliquer directement.  
  
 Pour définir les caractéristiques de la surface d’un modèle, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] utilise la <xref:System.Windows.Media.Media3D.Material> classe abstraite. Les sous-classes concrètes de Material déterminent certaines des caractéristiques d’apparence de la surface du modèle, et chacune fournit également une propriété Brush à laquelle vous pouvez passer un SolidColorBrush, TileBrush ou VisualBrush.  
  
-   <xref:System.Windows.Media.Media3D.DiffuseMaterial>Spécifie que le pinceau sera appliqué au modèle comme si ce modèle était allumé indirectement. L’utilisation de DiffuseMaterial est très semblable à celle de pinceaux directement sur les modèles [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] ; les surfaces de modèle ne reflètent pas la lumière même si elles sont brillantes.  
  
-   <xref:System.Windows.Media.Media3D.SpecularMaterial>Spécifie que le pinceau sera appliqué au modèle comme si la surface du modèle était dure ou brillante, capable de refléter des surbrillances. Vous pouvez définir le degré auquel la texture suggérera cette qualité réfléchissante, ou « brillant », en spécifiant une valeur pour le <xref:System.Windows.Media.Media3D.SpecularMaterial.SpecularPower%2A> propriété.  
  
-   <xref:System.Windows.Media.Media3D.EmissiveMaterial>vous permet de spécifier que la texture sera appliquée comme si le modèle émettait une lumière égale à la couleur du pinceau. Cela ne fait pas du modèle un éclairage. Toutefois, il participera différemment à l’ombrage que s’il était texturé avec DiffuseMaterial ou SpecularMaterial.  
  
 Pour de meilleures performances, les faces arrière d’un <xref:System.Windows.Media.Media3D.GeometryModel3D> (ces faces qui sont hors de l’affichage, car elles sont sur le côté opposé du modèle à partir de la caméra) sont éliminées de la scène.  Pour spécifier un <xref:System.Windows.Media.Media3D.Material> pour appliquer à la face arrière d’un modèle comme un plan, définissez du modèle <xref:System.Windows.Media.Media3D.GeometryModel3D.BackMaterial%2A> propriété.  
  
 Pour obtenir certaines qualités de surface, comme les effets lumineux ou de miroir, vous souhaiterez appliquer plusieurs pinceaux différents à un modèle à la suite. Vous pouvez appliquer et réutiliser plusieurs matières à l’aide de la <xref:System.Windows.Media.Media3D.MaterialGroup> classe. Les enfants du MaterialGroup sont appliqués du premier au dernier en plusieurs passes de rendu.  
  
 Les exemples de code suivants montrent comment appliquer une couleur unie et un dessin en tant que pinceaux sur les modèles [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)].  
  
 [!code-xaml[basic3d#Basic3DXAML3DN5](../../../../samples/snippets/xaml/VS_Snippets_Wpf/Basic3D/XAML/Window1.xaml#basic3dxaml3dn5)]  
  
 [!code-xaml[3doverview#3DOverview3DN9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/app.xaml#3doverview3dn9)]  
  
 [!code-csharp[3doverview#3DOverview3DN8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn8)]
 [!code-vb[3doverview#3DOverview3DN8](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn8)]  
  
<a name="lights"></a>   
## <a name="illuminating-the-scene"></a>Éclairage de la scène  
 Les lumières dans les graphiques [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] font ce que les lumières font dans le monde réel : elles rendent des surfaces visibles. Plus précisément, les lumières déterminent la partie d’une scène qui figurera dans la projection. Les objets de lumière dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] créent divers effets de lumière et d’ombre et sont modelés d’après le comportement de diverses lumières réelles. Vous devez inclure au moins une lumière dans votre scène, sans quoi aucun modèle ne sera visible.  
  
 Lumières suivantes dérivent de la classe de base <xref:System.Windows.Media.Media3D.Light>:  
  
-   <xref:System.Windows.Media.Media3D.AmbientLight>: Fournit une lumière ambiante qui éclaire tous les objets de manière uniforme, quelle que soit leur emplacement ou orientation.  
  
-   <xref:System.Windows.Media.Media3D.DirectionalLight>: Éclaire comme une source de lumière distante.  Les lumières directionnelles ont un <xref:System.Windows.Media.Media3D.DirectionalLight.Direction%2A> spécifié comme un Vector3D, mais aucun emplacement spécifié.  
  
-   <xref:System.Windows.Media.Media3D.PointLight>: Éclaire comme une source de lumière proche. Les PointLights ont une position et convertissent la lumière à partir de cette position. Les objets dans la scène sont éclairés en fonction de leur position et de la distance par rapport à la lumière. <xref:System.Windows.Media.Media3D.PointLightBase>expose un <xref:System.Windows.Media.Media3D.PointLightBase.Range%2A> propriété qui détermine une distance au-delà de laquelle les modèles ne seront pas éclairés par la lumière. PointLight expose également des propriétés d’atténuation qui déterminent comment l’intensité lumineuse diminue sur la distance. Vous pouvez spécifier des interpolations constantes, linéaires ou quadratiques pour l’atténuation de la lumière.  
  
-   <xref:System.Windows.Media.Media3D.SpotLight>: Hérite <xref:System.Windows.Media.Media3D.PointLight>. Les Spotlights éclairent comme PointLight et ont une position et une direction. Ils projettent la lumière dans une zone de forme conique définie par <xref:System.Windows.Media.Media3D.SpotLight.InnerConeAngle%2A> et <xref:System.Windows.Media.Media3D.SpotLight.OuterConeAngle%2A> propriétés, spécifiées en degrés.  
  
 Témoins lumineux sont <xref:System.Windows.Media.Media3D.Model3D> des objets, vous pouvez donc transformer et animer des propriétés de lumière, y compris la position, de couleur, de direction et de plage.  
  
 [!code-xaml[hittest3d#HitTest3D3DN6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTest3D/CSharp/Window1.xaml#hittest3d3dn6)]  
  
 [!code-csharp[basic3d#Basic3D3DN11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Basic3D/CSharp/Window1.xaml.cs#basic3d3dn11)]
 [!code-vb[basic3d#Basic3D3DN11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Basic3D/visualbasic/window1.xaml.vb#basic3d3dn11)]  
  
 [!code-csharp[basic3d#Basic3D3DN12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Basic3D/CSharp/Window1.xaml.cs#basic3d3dn12)]
 [!code-vb[basic3d#Basic3D3DN12](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Basic3D/visualbasic/window1.xaml.vb#basic3d3dn12)]  
  
 [!code-csharp[basic3d#Basic3D3DN13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Basic3D/CSharp/Window1.xaml.cs#basic3d3dn13)]
 [!code-vb[basic3d#Basic3D3DN13](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Basic3D/visualbasic/window1.xaml.vb#basic3d3dn13)]  
  
<a name="transforms"></a>   
## <a name="transforming-models"></a>Transformation de modèles  
 Lorsque vous créez des modèles, ils ont un emplacement particulier dans la scène. Pour déplacer ces modèles dans la scène, pour les faire pivoter ou pour modifier leur taille, il n’est pas pratique de modifier les vertex qui définissent les modèles eux-mêmes.  Au lieu de cela, tout comme dans [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)], vous appliquez des transformations aux modèles.  
  
 Chaque objet modèle a une <xref:System.Windows.Media.Media3D.Model3D.Transform%2A> propriété avec laquelle vous pouvez déplacer, réorienter ou redimensionner le modèle.  Lorsque vous appliquez une transformation, vous décalez tous les points du modèle par le vecteur ou la valeur que la transformation spécifie. En d’autres termes, vous avez transformé l’espace de coordonnées dans lequel le modèle est défini (« espace de modèle »), mais vous n’avez pas modifié les valeurs qui composent la géométrie du modèle dans le système de coordonnées de la scène entière (« espace universel »).  
  
 Pour plus d’informations sur la transformation de modèles, consultez [Vue d'ensemble des transformations 3D](../../../../docs/framework/wpf/graphics-multimedia/3-d-transformations-overview.md).  
  
<a name="animations"></a>   
## <a name="animating-models"></a>Animation de modèles  
 Le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] implémentation est inclus dans le même système de minutage et d’animation que [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] graphics. En d’autres termes, pour animer une scène 3D, animez les propriétés de ses modèles. Il est possible d’animer directement des propriétés de primitives, mais il est généralement plus facile d’animer des transformations qui modifient la position ou l’apparence de modèles. Étant donné que les transformations peuvent être appliquées aux <xref:System.Windows.Media.Media3D.Model3DGroup> des objets, ainsi que des modèles individuels, il est possible d’appliquer un ensemble d’animations à un enfant d’un Model3DGroup et un autre ensemble d’animations à un groupe d’objets enfants. Vous pouvez également obtenir divers effets visuels en animant les propriétés d’éclairage de votre scène. Enfin, vous pouvez choisir d’animer la projection elle-même en animant la position d’une caméra ou un champ de vue. Pour plus d’informations sur le minutage [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] et le système d’animation, consultez les rubriques [Vue d'ensemble de l'animation](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md), [Vue d'ensemble des storyboards](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md) et [Vue d'ensemble des objets Freezable](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).  
  
 Pour animer un objet dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], vous créez une chronologie, définissez une animation (qui est en fait une modification de valeur de propriété dans le temps) et spécifiez la propriété à laquelle appliquer l’animation. Étant donné que tous les objets dans une [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] scène sont des enfants de <xref:System.Windows.Controls.Viewport3D>, les propriétés ciblées par toute animation que vous souhaitez appliquer à la scène sont des propriétés de Viewport3D.  
  
 Supposons que vous souhaitez faire osciller un modèle. Vous pouvez choisir d’appliquer un <xref:System.Windows.Media.Media3D.RotateTransform3D> au modèle et d’animer l’axe de sa rotation d’un vecteur à un autre. L’exemple de code suivant montre comment appliquer une Vector3DAnimation à la propriété Axis de la Rotation3D de la transformation, en supposant que RotateTransform3D est une des multiples transformations appliquées au modèle avec un TransformGroup.  
  
 [!code-csharp[3doverview#3DOverview3DN1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn1)]
 [!code-vb[3doverview#3DOverview3DN1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn1)]  
  
 [!code-csharp[3doverview#3DOverview3DN3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn3)]
 [!code-vb[3doverview#3DOverview3DN3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn3)]  
  
 [!code-csharp[3doverview#3DOverview3DN4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn4)]
 [!code-vb[3doverview#3DOverview3DN4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn4)]  
  
 [!code-csharp[3doverview#3DOverview3DN5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn5)]
 [!code-vb[3doverview#3DOverview3DN5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn5)]  
  
<a name="animations1"></a>   
## <a name="add-3-d-content-to-the-window"></a>Ajouter du contenu 3D à la fenêtre  
 Pour restituer la scène, ajoutez des modèles et les témoins lumineux à un <xref:System.Windows.Media.Media3D.Model3DGroup>, puis définissez le <xref:System.Windows.Media.Media3D.Model3DGroup> comme le <xref:System.Windows.Media.Media3D.ModelVisual3D.Content%2A> d’un <xref:System.Windows.Media.Media3D.ModelVisual3D>. Ajouter le <xref:System.Windows.Media.Media3D.ModelVisual3D> à la <xref:System.Windows.Controls.Viewport3D.Children%2A> collection de la <xref:System.Windows.Controls.Viewport3D>. Ajoutez des caméras pour le <xref:System.Windows.Controls.Viewport3D> en définissant son <xref:System.Windows.Controls.Viewport3D.Camera%2A> propriété.  
  
 Enfin, ajoutez le <xref:System.Windows.Controls.Viewport3D> à la fenêtre. Lorsque le <xref:System.Windows.Controls.Viewport3D> est inclus en tant que le contenu d’un élément de disposition comme zone de dessin, spécifiez la taille de la Viewport3D en définissant ses <xref:System.Windows.FrameworkElement.Height%2A> et <xref:System.Windows.FrameworkElement.Width%2A> propriétés (héritée de <xref:System.Windows.FrameworkElement>).  
  
 [!code-xaml[hostingwpfusercontrolinwf#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingWpfUserControlInWf/CSharp/HostingWpfUserControlInWf/ConeControl.xaml#1)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Controls.Viewport3D>  
 <xref:System.Windows.Media.Media3D.PerspectiveCamera>  
 <xref:System.Windows.Media.Media3D.DirectionalLight>  
 <xref:System.Windows.Media.Media3D.Material>  
 [Vue d’ensemble des transformations 3D](../../../../docs/framework/wpf/graphics-multimedia/3-d-transformations-overview.md)  
 [Optimiser les performances 3D WPF](../../../../docs/framework/wpf/graphics-multimedia/maximize-wpf-3d-performance.md)  
 [Rubriques de guide pratique](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-how-to-topics.md)  
 [Vue d’ensemble des formes et dessins de base dans WPF](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)  
 [Peinture avec des images, des dessins et des objets visuels](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)
