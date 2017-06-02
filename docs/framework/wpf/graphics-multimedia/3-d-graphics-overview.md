---
title: "Vue d&#39;ensemble des graphiques 3D | Microsoft Docs"
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
  - "graphiques 3D"
  - "graphiques (WPF), 3D"
ms.assetid: 67f31ed4-e36b-4b02-9889-dcce245d7afc
caps.latest.revision: 21
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 20
---
# Vue d&#39;ensemble des graphiques 3D
<a name="introduction"></a> La fonctionnalité [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] de [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] permet aux développeurs de dessiner, de transformer et d'animer des graphiques 3D dans le balisage et le code procédural.  Les développeurs peuvent regrouper les graphiques [!INCLUDE[TLA#tla_2d](../../../../includes/tlasharptla-2d-md.md)] et [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] pour créer des contrôles riches, pour fournir les illustrations complexes de données ou pour améliorer l'expérience utilisateur de l'interface d'une application. La prise en charge de [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] n'est pas conçue pour fournir une plateforme complète de développement de jeu. Cette rubrique fournit une introduction de la fonctionnalité [!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)] dans le système graphique [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
   
  
<a name="threed_in_2d"></a>   
## 3D dans un conteneur 2D  
 Le contenu graphique [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] est encapsulé dans un élément <xref:System.Windows.Controls.Viewport3D> qui peut participer à la structure du document à deux dimensions.  Le système graphique traite <xref:System.Windows.Controls.Viewport3D> comme un élément visuel à deux dimensions semblable à bien d'autres dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  <xref:System.Windows.Controls.Viewport3D> fonctionne comme une fenêtre \(d'affichage\) dans une scène tridimensionnelle.  Plus précisément, c'est une surface sur laquelle une scène [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] est projetée.  
  
 Dans une application [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] classique, utilisez <xref:System.Windows.Controls.Viewport3D> comme vous le feriez avec un autre élément conteneur comme Grille ou Zone de dessin.  Bien que vous puissiez utiliser <xref:System.Windows.Controls.Viewport3D> avec d'autres objets de dessin [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] dans la même scène graphique, vous ne pouvez pas interpénétrer d'objets [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] et [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] dans une <xref:System.Windows.Controls.Viewport3D>.  Cette rubrique se concentrera sur la façon de dessiner des graphiques [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] à l'intérieur de la <xref:System.Windows.Controls.Viewport3D>.  
  
<a name="coord_space"></a>   
## Espace de coordonnées 3D  
 Le système de coordonnées [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pour les graphiques [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] localise l'origine dans la partie supérieure gauche de la zone de rendu \(en général l'écran\).  Dans le système [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)], les valeurs d'axe des abscisses positives continuent à droite et les valeurs d'axe des ordonnées positives continuent vers le bas.  Dans le système de coordonnées [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] toutefois, l'origine est située dans le centre de la zone de rendu, avec les valeurs d'axe des abscisses positives qui continuent à droite mais les valeurs d'axe des ordonnées positives qui continuent vers le haut, et les valeurs d'axe z positives qui continuent vers l'extérieur de l'origine, vers la visionneuse.  
  
 ![Systèmes de coordonnées](../../../../docs/framework/wpf/graphics-multimedia/media/coordsystem-1.png "CoordSystem\-1")  
Représentations de systèmes de coordonnées 2D et 3D classiques  
  
 L'espace défini par ces axes est le système de référence stationnaire pour les objets [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  Comme vous générez des modèles dans cet espace et créez des lumières et des caméras pour les consulter, il est utile de distinguer ce système de référence stationnaire, ou « espace universel », du système de référence local que vous créez pour chaque modèle lorsque vous lui appliquez des transformations.  Souvenez\-vous également que les objets dans espace universel peuvent sembler entièrement différents, ou ne pas être visibles du tout, selon les paramètres de lumière et de caméra, mais la position de la caméra ne modifie pas l'emplacement d'objets dans l'espace universel.  
  
<a name="cameras"></a>   
## Caméras et projections  
 Les développeurs qui travaillent dans [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] sont habitués à positionner des primitives de dessin sur un écran à deux dimensions.  Lorsque vous créez une scène [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)], il est important de se rappeler que vous créez vraiment une représentation [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] d'objets [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)].  Du fait qu'une apparence de scène [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] a un aspect différent selon le point de vue du spectateur, vous devez spécifier ce point de vue.  La classe <xref:System.Windows.Media.Media3D.Camera> vous permet de spécifier ce point de vue pour une scène [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)].  
  
 Une autre méthode pour comprendre comment une scène [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] est représentée sur une surface [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] est de décrire la scène comme une projection sur la surface de visionnage.  La <xref:System.Windows.Media.Media3D.ProjectionCamera> vous permet de spécifier des projections différentes et leurs propriétés pour changer la manière dont le spectateur consulte les modèles [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)].  Une <xref:System.Windows.Media.Media3D.PerspectiveCamera> spécifie une projection qui dessine en raccourci la scène.  En d'autres termes, la <xref:System.Windows.Media.Media3D.PerspectiveCamera> fournit la perspective de point de fuite.  Vous pouvez spécifier la position de la caméra dans l'espace de coordonnées de la scène, la direction et le champ de vision pour la caméra, et un vecteur qui définit la direction « vers le haut » dans la scène.  Le diagramme suivant illustre la projection de la <xref:System.Windows.Media.Media3D.PerspectiveCamera>.  
  
 Les propriétés <xref:System.Windows.Media.Media3D.ProjectionCamera.NearPlaneDistance%2A> et <xref:System.Windows.Media.Media3D.ProjectionCamera.FarPlaneDistance%2A> de <xref:System.Windows.Media.Media3D.ProjectionCamera> limitent la plage de projection de la caméra.  Étant donné que les caméras peuvent se trouver n'importe où dans la scène, il est possible de positionner la caméra à l'intérieur d'un modèle ou très près de lui, ce qui ne permet pas de distinguer facilement les objets.  <xref:System.Windows.Media.Media3D.ProjectionCamera.NearPlaneDistance%2A> vous permet de spécifier une distance minimum à respecter vis\-à\-vis de la caméra dans laquelle les objets ne seront pas dessinés.  Inversement, <xref:System.Windows.Media.Media3D.ProjectionCamera.FarPlaneDistance%2A> vous permet de spécifier une distance de la caméra au\-delà de laquelle les objets ne seront pas dessinés, ce qui garantit que les objets trop loin pour être reconnus ne seront pas inclus dans la scène.  
  
 ![Installation de l'appareil photo](../../../../docs/framework/wpf/graphics-multimedia/media/coordsystem-6.png "CoordSystem\-6")  
Position de la caméra  
  
 <xref:System.Windows.Media.Media3D.OrthographicCamera> spécifie une projection orthogonale d'un modèle [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] sur une surface visuelle [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)].  Comme les autres caméras , elle indique une position, une direction d'affichage et une direction « vers le haut ».  Contrairement à la <xref:System.Windows.Media.Media3D.PerspectiveCamera>, toutefois, la <xref:System.Windows.Media.Media3D.OrthographicCamera> décrit une projection qui n'inclut pas de réduction de perspective.  En d'autres termes, <xref:System.Windows.Media.Media3D.OrthographicCamera> décrit une zone d'affichage dont les côtés sont parallèles, au lieu d'une zone dont les côtés se rejoignent à un point de la caméra.  L'image suivante affiche le même modèle que celui visionné à l'aide de <xref:System.Windows.Media.Media3D.PerspectiveCamera> et <xref:System.Windows.Media.Media3D.OrthographicCamera>.  
  
 ![Projection orthographique et en perspective](../../../../docs/framework/wpf/graphics-multimedia/media/camera-projections4.png "Camera\_projections4")  
Perspective et projections orthogonales  
  
 Le code suivant affiche des paramètres de caméra typiques.  
  
 [!code-csharp[3dgallery_procedural_snip#Basic3DShapeCodeExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/Basic3DShapeExample.cs#basic3dshapecodeexampleinline1)]
 [!code-vb[3dgallery_procedural_snip#Basic3DShapeCodeExampleInline1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/3DGallery_procedural_snip/visualbasic/basic3dshapeexample.vb#basic3dshapecodeexampleinline1)]  
  
<a name="models_meshes"></a>   
## Modèle et primitives de maillage  
 <xref:System.Windows.Media.Media3D.Model3D> est la classe de base abstraite qui représente un objet [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] générique.  Pour générer une scène [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)], vous avez besoin de quelques objets à afficher, et des objets qui composent le graphique de scène dérivé de <xref:System.Windows.Media.Media3D.Model3D>.  Actuellement, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] prend en charge des géométries de modélisation avec <xref:System.Windows.Media.Media3D.GeometryModel3D>.  La propriété <xref:System.Windows.Media.Media3D.GeometryModel3D.Geometry%2A> de ce modèle prend un maillage de base.  
  
 Pour générer un modèle, commencez en générant une primitive, ou maillage.  Une primitive [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] est une collection des sommets qui forment une entité [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] unique.  La plupart des systèmes [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] fournissent des primitives modelées sur la figure fermée la plus simple : un triangle défini par trois sommets.  Du fait que les trois points d'un triangle sont coplanaires, vous pouvez continuer à ajouter des triangles pour modeler plus de formes complexes, appelées mailles.  
  
 Le système [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)][!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)]fournit actuellement la classe <xref:System.Windows.Media.Media3D.MeshGeometry3D>, qui vous permet de spécifier n'importe quelle géométrie ; il ne actuellement prend pas en charge les primitives [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] prédéfinies comme sphères et formes cubiques.  Commencez à créer un <xref:System.Windows.Media.Media3D.MeshGeometry3D> en spécifiant une liste de sommets de triangle comme sa propriété <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A>.  Chaque vertex est spécifié comme un <xref:System.Windows.Media.Media3D.Point3D>.  \(En [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], spécifiez cette propriété comme une liste de nombres groupés par trois qui représente les coordonnées de chaque vertex.\) Selon sa géométrie, votre maillage peut être composé de nombreux triangles, certains d'entre eux partageant les mêmes angles \(sommets\).  Pour dessiner le maillage correctement, le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a besoin d'informations quant à quels sommets sont partagés par quels triangles.  Vous fournissez cette information en spécifiant une liste d'index de triangle avec la propriété <xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A>.  Cette liste spécifie l'ordre dans lequel les points spécifiés dans la liste <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> détermineront un triangle.  
  
 [!code-xml[basic3d#Basic3DXAML3DN3](../../../../samples/snippets/xaml/VS_Snippets_Wpf/Basic3D/XAML/Window1.xaml#basic3dxaml3dn3)]  
  
 Dans l'exemple précédent, la liste <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> spécifie huit sommets pour définir un maillage en forme de cube.  La propriété <xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A> spécifie une liste de douze groupes de trois index.  Chaque nombre dans la liste fait référence à un offset dans la liste <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A>.  Par exemple, les trois premiers sommets spécifiés par la liste <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> sont \(1,1,0\), \(0,1,0\) et \(0,0,0\).  Les trois premiers index spécifiés par la liste <xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A> sont 0, 2 et 1, ce qui correspond aux premier, troisième et deuxième points dans la liste <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A>.  En conséquence, le premier triangle qui compose le modèle de cube sera composé de \(1,1,0\) à \(0,1,0\) à \(0,0,0\), et les onze triangles restants seront déterminé d'une façon similaire.  
  
 Vous pouvez continuer à définir le modèle en spécifiant des valeurs pour les propriétés <xref:System.Windows.Media.Media3D.MeshGeometry3D.Normals%2A> et <xref:System.Windows.Media.Media3D.MeshGeometry3D.TextureCoordinates%2A>.  Pour restituer la surface du modèle, le système graphique a besoin d'informations quant à la direction faisant face à la surface sur tout triangle donné.  Il utilise cette information pour faire des calculs d'éclairage pour le modèle : les surfaces qui font face directement à une source de lumière apparaissent plus claires que celles se trouvant en angle par rapport à la lumière.  Bien que [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] puisse déterminer des vecteurs normaux par défaut en utilisant les coordonnées de position, vous pouvez également spécifier des vecteurs normaux différents pour se rapprocher de l'apparence de surfaces courbées.  
  
 La propriété <xref:System.Windows.Media.Media3D.MeshGeometry3D.TextureCoordinates%2A> spécifie une collection de <xref:System.Windows.Point>s qui indique au système graphique comment mapper les coordonnées qui déterminent la manière dont la texture est dessinée sur les sommets du maillage.  Les <xref:System.Windows.Media.Media3D.MeshGeometry3D.TextureCoordinates%2A> sont spécifiées sous la forme d'une valeur comprise entre zéro et 1 \(valeurs incluses\).  Comme avec la propriété <xref:System.Windows.Media.Media3D.MeshGeometry3D.Normals%2A>, le système graphique peut calculer des coordonnées de texture par défaut, mais vous pouvez choisir de définir des coordonnées de texture différentes pour contrôler le mappage d'une texture qui inclut une partie d'un modèle à répétition, par exemple.  Plus d'informations à propos des coordonnées de texture se trouvent dans les rubriques suivantes ou dans le Kit de développement logiciel \(SDK\) Managed Direct3D.  
  
 L'exemple suivant indique comment créer une face du cube modèle en code procédural.  Notez que vous pouvez dessiner le cube entier comme un GeometryModel3D unique ; cet exemple dessine la face du cube en tant que modèle distinct pour appliquer ultérieurement des textures séparées à chaque face.  
  
 [!code-csharp[3doverview#3DOverview3DN6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn6)]
 [!code-vb[3doverview#3DOverview3DN6](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn6)]  
  
 [!code-csharp[3doverview#3DOverview3DN7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn7)]
 [!code-vb[3doverview#3DOverview3DN7](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn7)]  
  
<a name="materials"></a>   
## Application de matières au modèle  
 Pour qu'un maillage ressemble à un objet tridimensionnel, il doit avoir une texture appliquée pour couvrir la surface définie par ses sommets et triangles afin de pouvoir être allumé et projeté par la caméra.  Dans [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)], vous utilisez la classe <xref:System.Windows.Media.Brush> pour appliquer des couleurs, des modèles, des dégradés ou d'autres contenus visuels aux zones de l'écran.  Toutefois, l'apparence d'objets [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] est une fonction du modèle d'éclairage, pas seulement de la couleur ou du modèle leur étant appliqué.  Les objets réels reflètent différemment la lumière selon la qualité de leurs surfaces : les surfaces lustrées et brillantes n'ont pas la même apparence que les surfaces rugueuses ou mattes, et certains objets paraissent absorber la lumière pendant que d'autres brillent.  Vous pouvez appliquer tous les mêmes pinceaux aux objets [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] que vous pouvez appliquer aux objets [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)], mais vous ne pouvez pas les appliquer directement.  
  
 Pour définir les caractéristiques de la surface d'un modèle, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] utilise la classe abstraite <xref:System.Windows.Media.Media3D.Material>.  Les sous\-classes concrètes de matière déterminent quelques\-unes des caractéristiques d'apparence de la surface du modèle, et chacune fournit également une propriété Brush à laquelle vous pouvez passer un SolidColorBrush, TileBrush ou VisualBrush.  
  
-   <xref:System.Windows.Media.Media3D.DiffuseMaterial> spécifie que le pinceau sera appliqué au modèle comme si ce modèle était allumé indirectement.  L'utilisation de DiffuseMaterial est très similaire à l'utilisation de pinceaux directement sur les modèles [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] ; les surfaces de modèle ne reflètent pas la lumière bien que brillants.  
  
-   <xref:System.Windows.Media.Media3D.SpecularMaterial> spécifie que le pinceau sera appliqué au modèle comme si la surface du modèle était dure ou brillante, capable de refléter des surbrillances.  Vous pouvez définir le degré auquel la texture suggérera cette qualité réflectrice, ou « brillant », en spécifiant une valeur pour la propriété <xref:System.Windows.Media.Media3D.SpecularMaterial.SpecularPower%2A>.  
  
-   <xref:System.Windows.Media.Media3D.EmissiveMaterial> vous permet de spécifier que la texture sera appliquée comme si le modèle émettait une lumière équivalente à la couleur du pinceau.  Cela ne transforme pas le modèle en lumière ; toutefois, il participera différemment à l'ombrage qu'il ne le ferait en cas de texture avec DiffuseMaterial ou SpecularMaterial.  
  
 Pour optimiser les performances, les faces arrières d'un <xref:System.Windows.Media.Media3D.GeometryModel3D> \(ces faces qui sont hors de vue parce qu'elles sont sur le côté opposé du modèle par rapport à la caméra\) sont éliminées de la scène.  Pour spécifier un <xref:System.Windows.Media.Media3D.Material> à appliquer à la face arrière d'un modèle comme un plan, définissez la propriété <xref:System.Windows.Media.Media3D.GeometryModel3D.BackMaterial%2A> du modèle.  
  
 Pour accomplir des qualités de surface, comme les effects de brillance ou de reflet, vous pouvez appliquer plusieurs pinceaux différents à un modèle à la suite.  Vous pouvez appliquer et réutiliser plusieurs matières à l'aide de la classe <xref:System.Windows.Media.Media3D.MaterialGroup>.  Les enfants du MaterialGroup sont appliqués du premier au dernier en plusieurs passes de rendu.  
  
 Les exemples de code suivants indiquent comment appliquer une couleur unie et un dessin comme pinceaux aux modèles [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)].  
  
 [!code-xml[basic3d#Basic3DXAML3DN5](../../../../samples/snippets/xaml/VS_Snippets_Wpf/Basic3D/XAML/Window1.xaml#basic3dxaml3dn5)]  
  
 [!code-xml[3doverview#3DOverview3DN9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/app.xaml#3doverview3dn9)]  
  
 [!code-csharp[3doverview#3DOverview3DN8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn8)]
 [!code-vb[3doverview#3DOverview3DN8](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn8)]  
  
<a name="lights"></a>   
## Éclairage de la scène  
 Les lumières dans les graphiques [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] font la même chose que les vraies : elles rendent des surfaces visibles.  Plus précisément, les lumières déterminent quelle partie d'une scène sera incluse dans la projection.  Les objets de lumière dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] créent divers effets lumineux et d'effets d'ombre et sont modelés d'après le comportement de différentes lumières réelles.  Vous devez inclure au moins une lumière dans votre scène, ou aucun modèle ne sera visible.  
  
 Les lumières suivantes dérivent de la classe de base <xref:System.Windows.Media.Media3D.Light> :  
  
-   <xref:System.Windows.Media.Media3D.AmbientLight> : fournit une lumière ambiante qui éclaire uniformément tous les objets indépendamment de leur emplacement ou orientation.  
  
-   <xref:System.Windows.Media.Media3D.DirectionalLight> : éclaire comme une source de lumière distante.  Les lumières directionnelles ont un <xref:System.Windows.Media.Media3D.DirectionalLight.Direction%2A> spécifié comme un Vector3D, mais aucun emplacement spécifié.  
  
-   <xref:System.Windows.Media.Media3D.PointLight> : Éclaire comme une source de lumière proche.  Les PointLights ont une position et convertissent la lumière de cette position.  Les objets dans la scène sont éclairés en fonction de leur position et de leur distance par rapport à la lumière.  <xref:System.Windows.Media.Media3D.PointLightBase> expose une propriété <xref:System.Windows.Media.Media3D.PointLightBase.Range%2A> qui détermine une distance au\-delà de laquelle les modèles ne seront pas éclairés par la lumière.  PointLight expose également des propriétés d'atténuation qui déterminent comment l'intensité de la lumière diminue avec la distance.  Vous pouvez spécifier des interpolations constantes, linéaires ou quadratiques pour l'atténuation de la lumière.  
  
-   <xref:System.Windows.Media.Media3D.SpotLight> : Hérite de <xref:System.Windows.Media.Media3D.PointLight>.  Les projecteurs éclairent comme PointLight et disposent à la fois de la position et de la direction.  Ils projettent la lumière dans une zone en forme de cône définie par les propriétés <xref:System.Windows.Media.Media3D.SpotLight.InnerConeAngle%2A> et <xref:System.Windows.Media.Media3D.SpotLight.OuterConeAngle%2A>, indiquées en degrés.  
  
 Les lumières sont des objets <xref:System.Windows.Media.Media3D.Model3D>, vous pouvez donc transformer et animer des propriétés de lumière, comme la position, la couleur, la direction et la plage.  
  
 [!code-xml[hittest3d#HitTest3D3DN6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTest3D/CSharp/Window1.xaml#hittest3d3dn6)]  
  
 [!code-csharp[basic3d#Basic3D3DN11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Basic3D/CSharp/Window1.xaml.cs#basic3d3dn11)]
 [!code-vb[basic3d#Basic3D3DN11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Basic3D/visualbasic/window1.xaml.vb#basic3d3dn11)]  
  
 [!code-csharp[basic3d#Basic3D3DN12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Basic3D/CSharp/Window1.xaml.cs#basic3d3dn12)]
 [!code-vb[basic3d#Basic3D3DN12](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Basic3D/visualbasic/window1.xaml.vb#basic3d3dn12)]  
  
 [!code-csharp[basic3d#Basic3D3DN13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Basic3D/CSharp/Window1.xaml.cs#basic3d3dn13)]
 [!code-vb[basic3d#Basic3D3DN13](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Basic3D/visualbasic/window1.xaml.vb#basic3d3dn13)]  
  
<a name="transforms"></a>   
## Transformation de modèles  
 Lorsque vous créez des modèles, ils ont un emplacement particulier dans la scène.  Pour déplacer ces modèles dans la scène, pour les faire pivoter ou pour modifier leur taille, il n'est pas pratique de modifier les vertex qui définissent les modèles eux\-mêmes.  À la place, comme dans [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)], vous appliquez des transformations aux modèles.  
  
 Chaque objet modèle a une propriété <xref:System.Windows.Media.Media3D.Model3D.Transform%2A> avec laquelle vous pouvez déplacer, réorienter ou redimensionner le modèle.  Lorsque vous appliquez une transformation, vous compensez efficacement tous les points du modèle par quelque vecteur ou valeur que ce soit spécifié par la transformation.  En d'autres termes, vous avez transformé l'espace de coordonnées dans lequel le modèle est défini \(« espace modèle »\), mais vous n'avez pas modifié les valeurs qui composent la géométrie du modèle dans le système de coordonnées de la scène entière \(« espace universel »\).  
  
 Pour plus d'informations sur la transformation de modèles, consultez [Vue d'ensemble des transformations 3D](../../../../docs/framework/wpf/graphics-multimedia/3-d-transformations-overview.md).  
  
<a name="animations"></a>   
## Animation de modèles  
 L'implémentation [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] participe au même système de minutage et d'animation que les graphiques [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)].  En d'autres termes, pour animer une scène 3D, animez les propriétés de ses modèles.  Il est possible d'animer directement des propriétés de primitives, mais il est en général plus facile d'animer des transformations qui modifient la position ou l'apparence de modèles.  Comme les transformations peuvent être appliquées aux objets <xref:System.Windows.Media.Media3D.Model3DGroup> aussi bien qu'aux modèles individuels, il est possible d'appliquer un jeu d'animations à un enfant d'un Model3DGroup et un autre jeu d'animations à un groupe d'objets enfants.  Vous pouvez également accomplir divers effets visuels en animant les propriétés d'éclairage de votre scène.  Enfin, vous pouvez choisir d'animer la projection elle\-même en animant la position de la caméra ou du champ de vision.  Pour les informations générales sur le système [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] de minutage et d'animation, consultez les rubriques [Vue d'ensemble de l'animation](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md), [Vue d'ensemble des storyboards](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md), et [Vue d'ensemble des objets Freezable](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).  
  
 Pour animer un objet dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], vous créez une chronologie, définissez une animation \(qui est en fait une modification de quelques valeurs de propriété dans le temps\) et spécifiez la propriété sur laquelle appliquer l'animation.  Comme tous les objets dans une scène [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] sont enfants de <xref:System.Windows.Controls.Viewport3D>, les propriétés ciblées par toute animation que vous souhaitez appliquer à la scène sont des propriétés de propriétés de Viewport3D.  
  
 Supposez vous souhaitiez faire apparaître un modèle pour qu'il sembler dévier sur place.  Vous pouvez choisir d'appliquer un <xref:System.Windows.Media.Media3D.RotateTransform3D> au modèle et d'animer l'axe de sa rotation d'un vecteur à un autre.  L'exemple de code suivant montre l'application d'un Vector3DAnimation à la propriété Axis du Rotation3D de la transformation, en assumant que le RotateTransform3D soit l'une des multiples transformations appliquées au modèle avec un TransformGroup.  
  
 [!code-csharp[3doverview#3DOverview3DN1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn1)]
 [!code-vb[3doverview#3DOverview3DN1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn1)]  
  
 [!code-csharp[3doverview#3DOverview3DN3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn3)]
 [!code-vb[3doverview#3DOverview3DN3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn3)]  
  
 [!code-csharp[3doverview#3DOverview3DN4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn4)]
 [!code-vb[3doverview#3DOverview3DN4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn4)]  
  
 [!code-csharp[3doverview#3DOverview3DN5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn5)]
 [!code-vb[3doverview#3DOverview3DN5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn5)]  
  
<a name="animations1"></a>   
## Ajout de contenu 3D à la fenêtre  
 Pour restituer la scène, ajoutez des modèles et des lumières à un <xref:System.Windows.Media.Media3D.Model3DGroup>, puis définissez le <xref:System.Windows.Media.Media3D.Model3DGroup> comme <xref:System.Windows.Media.Media3D.ModelVisual3D.Content%2A> d'un <xref:System.Windows.Media.Media3D.ModelVisual3D>.  Ajoutez le <xref:System.Windows.Media.Media3D.ModelVisual3D> à la collection <xref:System.Windows.Controls.Viewport3D.Children%2A> du <xref:System.Windows.Controls.Viewport3D>.  Ajoutez des caméras au <xref:System.Windows.Controls.Viewport3D> en définissant sa propriété <xref:System.Windows.Controls.Viewport3D.Camera%2A>.  
  
 Enfin, ajoutez le <xref:System.Windows.Controls.Viewport3D> à la fenêtre.  Lorsque le <xref:System.Windows.Controls.Viewport3D> est inclus en tant que contenu d'un élément de disposition telle que la zone de dessin, indiquez la taille du Viewport3D en définissant ses propriétés <xref:System.Windows.FrameworkElement.Height%2A> et <xref:System.Windows.FrameworkElement.Width%2A> \(héritées de <xref:System.Windows.FrameworkElement>\).  
  
 [!code-xml[hostingwpfusercontrolinwf#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingWpfUserControlInWf/CSharp/HostingWpfUserControlInWf/ConeControl.xaml#1)]  
  
## Voir aussi  
 <xref:System.Windows.Controls.Viewport3D>   
 <xref:System.Windows.Media.Media3D.PerspectiveCamera>   
 <xref:System.Windows.Media.Media3D.DirectionalLight>   
 <xref:System.Windows.Media.Media3D.Material>   
 [Vue d'ensemble des transformations 3D](../../../../docs/framework/wpf/graphics-multimedia/3-d-transformations-overview.md)   
 [Optimiser les performances 3D de WPF](../../../../docs/framework/wpf/graphics-multimedia/maximize-wpf-3d-performance.md)   
 [Rubriques Comment](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-how-to-topics.md)   
 [Vue d'ensemble des formes et dessins de base dans WPF](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)   
 [Peinture avec des objets d'image, de dessin et visuels](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)