---
title: "Vue d&#39;ensemble des transformations 3D | Microsoft Docs"
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
  - "transformations 3D"
  - "transformations, 3D"
ms.assetid: e45e555d-ac1e-4b36-aced-e433afe7f27f
caps.latest.revision: 18
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 17
---
# Vue d&#39;ensemble des transformations 3D
Cette rubrique décrit comment appliquer des transformations à des modèles 3D dans le système graphique [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  Les transformations permettent au développeur de repositionner, redimensionner et réorienter des modèles sans modifier les valeurs de base qui les définissent.  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
## Espace de coordonnées 3D  
 Le contenu graphique 3D [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] est encapsulé dans un élément, <xref:System.Windows.Controls.Viewport3D>, cette boîte participe à la structure du document à deux dimensions.  Le système graphique traite Viewport3D comme un élément visuel à deux dimensions comme de nombreux autres dans [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  Viewport3D fonctionne comme une fenêtre – une fenêtre d'affichage – dans une scène tridimensionnelle.  Plus précisément, c'est une surface sur laquelle une scène 3D est projetée.  Même si vous pouvez utiliser Viewport3D avec d'autres objets de dessin 2D dans la même scène graphique, vous ne pouvez pas interpénétrer d'objets 2D et 3D dans un Viewport3D.  Dans la discussion suivante, l'espace de coordonnées décrit est contenu par l'élément Viewport3D.  
  
 Le système de coordonnées [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] pour les graphiques 2D localise l'origine dans la partie supérieure gauche de la surface de rendu \(en général l'écran\).  Dans le système 2D, les valeurs d'axe des abscisses positives continuent à droite et les valeurs d'axe des ordonnées positives continuent vers le bas.  Dans le système de coordonnées 3D toutefois, l'origine est située dans le centre de l'écran, avec les valeurs d'axe des abscisses positives qui continuent à droite mais les valeurs d'axe des ordonnées positives qui continuent vers le haut, et les valeurs d'axe z positives qui continuent vers l'extérieur de l'origine, vers la visionneuse.  
  
 ![Systèmes de coordonnées](../../../../docs/framework/wpf/graphics-multimedia/media/coordsystem-1.png "CoordSystem\-1")  
Comparaison de systèmes de coordonnées  
  
 L'espace défini par ces axes est le système de référence stationnaire pour les objets 3D dans [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  Comme vous générez des modèles dans cet espace et créez des lumières et des caméras pour les consulter, il est utile de distinguer ce système de référence stationnaire, ou « espace universel », du système de référence local que vous créez pour chaque modèle lorsque vous lui appliquez des transformations.  Souvenez\-vous également que les objets dans espace universel peuvent sembler entièrement différents, ou ne pas être visibles du tout, selon les paramètres de lumière et de caméra, mais la position de la caméra ne modifie pas l'emplacement d'objets dans l'espace universel.  
  
## Transformation de modèles  
 Lorsque vous créez des modèles, ils ont un emplacement particulier dans la scène.  Pour déplacer ces modèles dans la scène, pour les faire pivoter ou pour modifier leur taille, il n'est pas pratique de modifier les vertex qui définissent les modèles eux\-mêmes.  À la place, comme en 2D, vous appliquez des transformations aux modèles.  
  
 Chaque objet modèle a une propriété <xref:System.Windows.Media.Media3D.Model3D.Transform%2A> avec laquelle vous pouvez déplacer, réorienter ou redimensionner le modèle.  Lorsque vous appliquez une transformation, vous compensez efficacement tous les points du modèle par n'importe quel vecteur ou valeur spécifié par la transformation.  En d'autres termes, vous avez transformé l'espace de coordonnées dans lequel le modèle est défini \(« espace modèle »\), mais vous n'avez pas modifié les valeurs qui composent la géométrie du modèle dans le système de coordonnées de la scène entière \(« espace universel »\).  
  
## Translations  
 Les transformations 3D héritent de la classe de base abstraite <xref:System.Windows.Media.Media3D.Transform3D> ; elles incluent les classes de transformation affines <xref:System.Windows.Media.Media3D.TranslateTransform3D>, <xref:System.Windows.Media.Media3D.ScaleTransform3D> et <xref:System.Windows.Media.Media3D.RotateTransform3D>.  Le système 3D [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] fournit également une classe <xref:System.Windows.Media.Media3D.MatrixTransform3D> qui vous permet de spécifier les mêmes transformations en opérations de matrice plus concises.  
  
 <xref:System.Windows.Media.Media3D.TranslateTransform3D> déplace tous les points du modèle 3D dans le sens du vecteur d'offset que vous spécifiez avec les propriétés <xref:System.Windows.Media.Media3D.TranslateTransform3D.OffsetX%2A>, <xref:System.Windows.Media.Media3D.TranslateTransform3D.OffsetY%2A> et <xref:System.Windows.Media.Media3D.TranslateTransform3D.OffsetZ%2A>.  Par exemple, étant donné un vertex d'un cube à \(2,2,2\), un vecteur d'offset de \(0,1.6,1\) déplacerait ce vertex \(2,2,2\) à \(2,3.6,3\).  Le vertex du cube est \(2,2,2\) dans l'espace modèle, mais comme cet espace modèle a modifié sa relation à l'espace universel afin que \(2,2,2\) dans l'espace modèle soit \(2,3.6,3\) dans l'espace universel.  
  
 ![Figure de traduction](../../../../docs/framework/wpf/graphics-multimedia/media/transforms-translate.png "Transforms\-Translate")  
Translation avec offset  
  
 Les exemples de code suivants montrent comment appliquer une translation.  
  
 [!code-xml[animation3dgallery_snip#Translation3DAnimationExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Translation3DAnimationExample.xaml#translation3danimationexamplewholepage)]  
  
## Transformations d'échelle  
 <xref:System.Windows.Media.Media3D.ScaleTransform3D> modifie l'échelle du modèle à l'aide d'un vecteur d'échelle spécifié avec une référence à un point central.  Spécifiez une échelle uniforme, qui met le modèle à l'échelle avec la même valeur pour les axes X, Y et Z, pour modifier la taille du modèle proportionnellement.  Par exemple, affecter la valeur 0,5 aux propriétés <xref:System.Windows.Media.ScaleTransform.ScaleX%2A>, <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> et <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleZ%2A> de la transformation divise par deux la taille du modèle ; affecter la valeur 2 aux mêmes propriétés double son échelle pour les trois axes.  
  
 ![Uniform ScaleTransform3D](../../../../docs/framework/wpf/graphics-multimedia/media/threecubes-uniformscale-1.png "threecubes\_uniformscale\_1")  
Exemple de vecteur d'échelle  
  
 En spécifiant une transformation d'échelle non uniforme – une transformation d'échelle dont les valeurs X, Y et Z ne sont pas les mêmes – une ou deux dimensions du modèle peuvent être étirées ou contractées sans que cela n'affecte les autres.  Par exemple, affecter la valeur 1 à <xref:System.Windows.Media.ScaleTransform.ScaleX%2A>, la valeur 2 à <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> et la valeur 1 à <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleZ%2A> doublerait la hauteur du modèle sans le modifier au niveau des axes X et Z.  
  
 Par défaut, ScaleTransform3D provoque le développement ou la contraction des vertex à l'origine \(0,0,0\).  Si le modèle que vous souhaitez transformer n'est pas dessiné depuis l'origine, la mise à l'échelle du modèle à partir de l'origine ne mettra pas à l'échelle le modèle « sur place ». À la place, lorsque les vertex du modèle sont multipliés par le vecteur d'échelle, l'opération de mise à l'échelle entraînera la translation du modèle ainsi que sa mise à l'échelle.  
  
 ![Trois cubes mis à l'échelle avec point central spécifié](../../../../docs/framework/wpf/graphics-multimedia/media/threecubes-scaledwithcenter-1.png "threecubes\_scaledwithcenter\_1")  
Exemple de centre d'échelle  
  
 Pour mettre un modèle à l'échelle « sur place », spécifiez le centre du modèle en définissant les propriétés <xref:System.Windows.Media.ScaleTransform.CenterX%2A>, <xref:System.Windows.Media.ScaleTransform.CenterY%2A> et <xref:System.Windows.Media.Media3D.ScaleTransform3D.CenterZ%2A> de ScaleTransform3D.  Cela garantit que le système graphique met l'espace modèle à l'échelle puis le translate vers le centre du <xref:System.Windows.Media.Media3D.Point3D> spécifié.  Inversement, si vous avez généré le modèle par rapport à l'origine et que vous spécifiez un autre point, vous devez vous attendre à ce que la transformation du modèle l'éloigne de l'origine.  
  
## Transformations  
 Vous pouvez faire pivoter un modèle en 3D de différentes manières.  Une rotation classique spécifie un axe et un angle de rotation autour de cet axe.  La classe <xref:System.Windows.Media.Media3D.RotateTransform3D> vous permet de définir une <xref:System.Windows.Media.Media3D.Rotation3D> avec sa propriété <xref:System.Windows.Media.Media3D.RotateTransform3D.Rotation%2A>.  Vous spécifiez ensuite les propriétés <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A> et <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A> sur la Rotation3D, dans ce cas <xref:System.Windows.Media.Media3D.AxisAngleRotation3D>, pour définir la transformation.  Les exemples suivants font pivoter un modèle de 60 degrés autour de l'axe Y.  
  
 [!code-xml[animation3dgallery_snip#Rotate3DUsingAxisAngleRotation3DExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Rotat3DUsingAxisAngleRotation3DExample.xaml#rotate3dusingaxisanglerotation3dexamplewholepage)]  
  
 Remarque : [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 3D est un système situé à droite, c'est\-à\-dire qu'une valeur d'angle positive pour une rotation entraîne une rotation dans le sens inverse des aiguilles d'une montre autour de l'axe.  
  
 Les rotations d'axe\/d'angle effectuent une rotation autour de l'origine si une valeur n'est pas spécifiée pour les propriétés <xref:System.Windows.Media.Media3D.RotateTransform3D.CenterX%2A>, <xref:System.Windows.Media.Media3D.RotateTransform3D.CenterY%2A> et <xref:System.Windows.Media.Media3D.RotateTransform3D.CenterZ%2A> sur RotateTransform3D.  Comme pour la mise à l'échelle, n'oubliez pas que la rotation transforme la totalité de l'espace de coordonnées du modèle.  Si le modèle n'a pas été créé par rapport à l'origine ou qu'il a d'abord été translaté, la rotation peut s'effectuer autour de l'origine au lieu de s'effectuer sur place.  
  
 ![Rotation avec nouveau point central](../../../../docs/framework/wpf/graphics-multimedia/media/threecubes-rotationwithcenter-1.png "threecubes\_rotationwithcenter\_1")  
Rotation avec spécification d'un nouveau centre  
  
 Pour faire pivoter le modèle « sur place », spécifiez l'actuel centre du modèle comme centre de la rotation.  Étant donné que la géométrie est généralement modelée par rapport à l'origine, vous pouvez, la plupart du temps, obtenir le résultat attendu d'un ensemble de transformations en redimensionnant d'abord le modèle \(mise à l'échelle\), puis en définissant son orientation \(rotation\) et en le déplaçant enfin à l'emplacement souhaité \(translation\).  
  
 ![Rotation de 60 degrés selon les axes x et y](../../../../docs/framework/wpf/graphics-multimedia/media/twocubes-rotation2axes-1.png "twocubes\_rotation2axes\_1")  
Exemple de rotation  
  
 Les rotations d'axe\/d'angle fonctionnent bien pour les transformations statiques et certaines animations.  Toutefois, envisagez la rotation d'un modèle de cube de 60 degrés autour de l'axe X, puis de 45 degrés autour de l'axe Z.  Vous pouvez décrire cette transformation sous forme de deux transformations affines discrètes ou sous forme de matrice.  Toutefois, il peut être difficile d'animer souplement une rotation définie de cette façon.  Même si les positions de début et de fin du modèle calculées par chacune des approches sont les mêmes, les positions intermédiaires par lesquelles passe le modèle sont incertaines en terme de calcul.  Les quaternions représentent une autre façon de calculer l'interpolation entre le début et la fin d'une rotation.  
  
 Un quaternion représente un axe dans un espace en trois dimensions et une rotation autour de cet axe.  Par exemple, un quaternion peut représente un axe \(1,1,2\) et une rotation de 50 degrés.  La capacité des quaternions à définir des rotations vient des deux opérations qu'ils peuvent gérer : composition et interpolation.  La composition de deux quaternions appliquée à une géométrie signifie « fait pivoter la géométrie autour de l'axe2 via la rotation2, puis la fait pivoter autour de l'axe1 via la rotation1 ». À l'aide de la composition, vous pouvez combiner les deux rotations sur la géométrie pour obtenir un seul quaternion qui représente le résultat.  Étant donné que l'interpolation de quaternion peut calculer un chemin souple et raisonnable à partir d'un axe et un sens vers un autre, vous pouvez interpoler à partir de l'original vers le quaternion composé pour effectuer une transition en souplesse de l'un à l'autre, ce qui vous permet d'animer la transformation.  Pour les modèles que vous souhaitez animer, vous pouvez spécifier une destination <xref:System.Windows.Media.Media3D.Quaternion> pour la rotation à l'aide de <xref:System.Windows.Media.Media3D.QuaternionRotation3D> pour la propriété <xref:System.Windows.Media.Media3D.RotateTransform3D.Rotation%2A>.  
  
## Utilisation de collections de transformations  
 Lorsque vous générez une scène, il est courant d'appliquer plusieurs transformations à un modèle.  Ajoutez des transformations à la collection <xref:System.Windows.Media.Media3D.Transform3DGroup.Children%2A> de la classe <xref:System.Windows.Media.Media3D.Transform3DGroup> pour regrouper facilement les transformations à appliquer aux différents modèles de la scène.  Il est souvent commode de réutiliser une transformation dans plusieurs groupes, de même que vous pouvez réutiliser un modèle en appliquant un ensemble de transformations différent à chaque instance.  Notez que l'ordre dans lequel les transformations sont ajoutées à la collection est important : les transformations dans la collection sont appliquées de la première à la dernière.  
  
## Animation de transformations  
 L'implémentation [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 3D participe au même système de minutage et d'animation que les graphiques 2D.  En d'autres termes, pour animer une scène 3D, animez les propriétés de ses modèles.  Il est possible d'animer directement des propriétés de primitives, mais il est en général plus facile d'animer des transformations qui modifient la position ou l'apparence de modèles.  Étant donné que les transformations peuvent être appliquées aux objets <xref:System.Windows.Media.Media3D.Model3DGroup> aussi bien qu'aux modèles individuels, il est possible d'appliquer un ensemble d'animations à l'enfant d'un Model3DGroup et un autre ensemble d'animations à un groupe d'objets.  Pour plus d'informations générales sur le système [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] de minutage et d'animation, consultez les rubriques [Vue d'ensemble de l'animation](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md) et [Vue d'ensemble des storyboards](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md).  
  
 Pour animer un objet dans [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], créez une chronologie, définissez une animation \(qui est en fait une modification de quelques valeurs de propriété dans le temps\) et spécifiez la propriété à laquelle appliquer l'animation.  Cette propriété doit être une propriété d'un FrameworkElement.  Étant donné que tous les objets dans une scène 3D sont enfants de Viewport3D, les propriétés ciblées par toute animation que vous souhaitez appliquer à la scène sont des propriétés de propriétés de Viewport3D.  Il est important d'élaborer le chemin de la propriété pour l'animation avec précaution, car la syntaxe peut être détaillée.  
  
 Supposons que vous souhaitez faire pivoter un objet sur place, mais également lui appliquer un mouvement de balancier pour afficher une plus grande partie de l'objet.  Vous pouvez choisir d'appliquer un RotateTransform3D au modèle et d'animer l'axe de sa rotation d'un vecteur à un autre.  L'exemple de code suivant montre l'application d'un <xref:System.Windows.Media.Animation.Vector3DAnimation> à la propriété Axis du Rotation3D de la transformation, en supposant que le RotateTransform3D soit l'une des multiples transformations appliquées au modèle avec un <xref:System.Windows.Media.TransformGroup>.  
  
 [!code-csharp[3doverview#3DOverview3DN1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn1)]
 [!code-vb[3doverview#3DOverview3DN1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn1)]  
  
 [!code-csharp[3doverview#3DOverview3DN3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn3)]
 [!code-vb[3doverview#3DOverview3DN3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn3)]  
  
 Utilisez une syntaxe similaire pour cibler d'autres propriétés de transformation pour déplacer l'objet ou le mettre à l'échelle.  Par exemple, vous pouvez appliquer un <xref:System.Windows.Media.Animation.Point3DAnimation> à la propriété ScaleCenter sur une mise à l'échelle pour entraîner une légère distorsion de la forme d'un modèle.  
  
 Même si les exemples précédents transforment les propriétés de <xref:System.Windows.Media.Media3D.GeometryModel3D>, il est également possible de transformer les propriétés d'autres modèles dans la scène.  En animant des translations appliquées aux objets Light, par exemple, vous pouvez créer des effets de lumière et d'ombre mobiles qui peuvent modifier l'apparence de vos modèles de manière significative.  
  
 Étant donné que les caméras sont également des modèles, il est également possible de transformer les propriétés de caméra.  Même si vous pouvez certainement modifier l'apparence de la scène en modifiant l'emplacement de la caméra ou les distances du plan – en réalité, en modifiant toute la projection de scène – notez que bon nombre des effets que vous obtenez de cette façon peuvent ne pas avoir autant d'impact visuel sur la visionneuse que les transformations appliquées à l'emplacement ou à la position des modèles dans la scène.  
  
## Voir aussi  
 [Vue d'ensemble des graphiques 3D](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)   
 [Vue d'ensemble des transformations](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)   
 [Transformations 2D, exemple \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkID=158252)