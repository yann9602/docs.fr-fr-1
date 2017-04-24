---
title: "Vue d&#39;ensemble de la cr&#233;ation d&#39;images | Microsoft Docs"
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
  - "convertir des images"
  - "rogner des images"
  - "formats de décodage d'images"
  - "afficher des images"
  - "formats d'encodage d'images"
  - "décodage de format pour des images"
  - "encodage de format pour des images"
  - "métadonnées d'image"
  - "images, à propos de la création d'images"
  - "API de création d'images"
  - "métadonnées, images"
  - "peindre avec des images"
  - "faire pivoter des images"
  - "étirer des images"
ms.assetid: 72aad87a-e6f3-4937-94cd-a18b7766e990
caps.latest.revision: 32
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 29
---
# Vue d&#39;ensemble de la cr&#233;ation d&#39;images
Cette rubrique fournit une introduction au [!INCLUDE[TLA#tla_wic](../../../../includes/tlasharptla-wic-md.md)].  La [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] permet aux développeurs d'afficher, de transformer et de formater des images.  
  
   
  
<a name="_wpfImaging"></a>   
## Composant de création d'images WPF  
 La [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] apporte d'importantes améliorations aux fonctionnalités de création d'images dans [!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)].  Les fonctionnalités de création d'images, comme l'affichage d'une bitmap ou l'utilisation d'une image sur un contrôle ordinaire dépendaient auparavant des bibliothèques [!INCLUDE[TLA#tla_gdi](../../../../includes/tlasharptla-gdi-md.md)] ou [!INCLUDE[TLA#tla_gdiplus](../../../../includes/tlasharptla-gdiplus-md.md)].  Ces [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] proposent des fonctionnalités de base pour la création d'images, mais sont dépourvues de fonctionnalités telles que la prise en charge de l'extensibilité de codec et des images haute fidélité.  [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] est conçu de manière à résoudre les points faibles de [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] et [!INCLUDE[TLA2#tla_gdiplus](../../../../includes/tla2sharptla-gdiplus-md.md)] et à fournir un nouveau jeu d'[!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] pour afficher et utiliser des images dans vos applications.  
  
 Il existe deux moyens d'accéder à l'[!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] de [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] : un composant managé et un composant non managé.  Le composant non  propose les fonctionnalités suivantes.  
  
-   Modèle d'extensibilité pour les formats d'image nouveaux ou propriétaires.  
  
-   Performance et sécurité améliorées sur les formats d'image natifs, notamment [!INCLUDE[TLA#tla_bmp](../../../../includes/tlasharptla-bmp-md.md)], [!INCLUDE[TLA#tla_jpegorg](../../../../includes/tlasharptla-jpegorg-md.md)], [!INCLUDE[TLA#tla_png](../../../../includes/tlasharptla-png-md.md)], [!INCLUDE[TLA#tla_tiff](../../../../includes/tlasharptla-tiff-md.md)], [!INCLUDE[TLA#tla_wdp](../../../../includes/tlasharptla-wdp-md.md)], [!INCLUDE[TLA#tla_gif](../../../../includes/tlasharptla-gif-md.md)] et les icônes \(.ico\).  
  
-   Préservation de la profondeur de couleur élevée des données image jusqu'à 8 bits par canal \(32 bits par pixel\).  
  
-   Mise à l'échelle, rognage et rotation d'image non destructives.  
  
-   Gestion des couleurs simplifiées.  
  
-   Prise en charge des métadonnées dans les fichiers propriétaires.  
  
-   Le composant managé utilise l'infrastructure non managée pour fournir une intégration transparente d'images avec d'autres fonctionnalités [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] telles que l'[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)], l'animation et les graphiques.  Le composant managé bénéficie également du modèle d'extensibilité codec de création d'images [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] qui permet la reconnaissance automatique des nouveaux formats d'image dans les applications [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].  
  
 La plupart des [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] de [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] se trouvent dans l'espace de noms <xref:System.Windows.Media.Imaging?displayProperty=fullName>, bien que plusieurs types importants, tels que <xref:System.Windows.Media.ImageBrush> et <xref:System.Windows.Media.ImageDrawing> se trouvent dans l'espace de noms <xref:System.Windows.Media?displayProperty=fullName> et que <xref:System.Windows.Controls.Image> se trouve dans l'espace de noms <xref:System.Windows.Controls?displayProperty=fullName>.  
  
 Cette rubrique fournit des informations supplémentaires sur le composant managé.  Pour plus d'informations sur l'[!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] non managée, consultez [Composant de création d'images WPF non managé](_wic_lh).  
  
<a name="_imageformats"></a>   
## Formats d'image WPF  
 Un codec est utilisé pour décoder ou encoder un format de média spécifique.  [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] comprend un codec pour les formats d'image [!INCLUDE[TLA2#tla_bmp](../../../../includes/tla2sharptla-bmp-md.md)], [!INCLUDE[TLA2#tla_jpeg](../../../../includes/tla2sharptla-jpeg-md.md)], [!INCLUDE[TLA2#tla_png](../../../../includes/tla2sharptla-png-md.md)], [!INCLUDE[TLA2#tla_tiff](../../../../includes/tla2sharptla-tiff-md.md)], [!INCLUDE[TLA2#tla_wdp](../../../../includes/tla2sharptla-wdp-md.md)], [!INCLUDE[TLA2#tla_gif](../../../../includes/tla2sharptla-gif-md.md)] et ICON.  Chacun de ces codecs permet aux applications de décoder et, sauf pour les icônes, d'encoder leurs formats d'image respectifs.  
  
 <xref:System.Windows.Media.Imaging.BitmapSource> est une classe importante utilisée dans le décodage et l'encodage d'images.  Il s'agit du bloc de construction de base du pipeline de [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)]. Il représente un seul jeu constant de pixels à une certaine taille et à une certaine résolution.  Un <xref:System.Windows.Media.Imaging.BitmapSource> peut être une frame individuelle d'une image à plusieurs frames, ou peut être le résultat d'une transformation effectuée sur un <xref:System.Windows.Media.Imaging.BitmapSource>.  C'est le parent de nombreuses classes principales utilisées dans la création d'images [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] comme <xref:System.Windows.Media.Imaging.BitmapFrame>.  
  
 Un <xref:System.Windows.Media.Imaging.BitmapFrame> sert à stocker les données bitmap actuelles d'un format d'image.  De nombreux formats d'image prennent seulement en charge un <xref:System.Windows.Media.Imaging.BitmapFrame> unique, bien que les formats tels que [!INCLUDE[TLA2#tla_gif](../../../../includes/tla2sharptla-gif-md.md)] et [!INCLUDE[TLA2#tla_tiff](../../../../includes/tla2sharptla-tiff-md.md)] prennent en charge plusieurs frames par image.  Les frames sont utilisées par les décodeurs comme données d'entrée et passées à des encodeurs pour créer les fichiers image.  
  
 L'exemple suivant montre comment est créé un <xref:System.Windows.Media.Imaging.BitmapFrame> à partir d'un <xref:System.Windows.Media.Imaging.BitmapSource>, puis ajouté à une image [!INCLUDE[TLA2#tla_tiff](../../../../includes/tla2sharptla-tiff-md.md)].  
  
 [!code-csharp[BitmapFrameExample#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BitmapFrameExample/CSharp/BitmapFrame.cs#10)]
 [!code-vb[BitmapFrameExample#10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BitmapFrameExample/VB/BitmapFrame.vb#10)]  
  
### Décodage du format d'image  
 Le décodage d'une image est la traduction d'un format d'image en données d'image pouvant être utilisées par le système.  Les données d'image peuvent être utilisées pour afficher, traiter ou encoder dans un format différent.  La sélection du décodeur est basée sur le format de l'image.  La sélection du codec est automatique à moins qu'un décodeur spécifique ne soit indiqué.  Les exemples de la section [Affichage d'images dans WPF](#_displayingimages) illustrent le décodage automatique.  Les décodeurs de formats personnalisés, développés à l'aide des interfaces de [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] non managées, et inscrits automatiquement dans le système participent à la sélection du décodeur.  Cela permet d'afficher automatiquement les formats personnalisés dans les applications [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].  
  
 L'exemple suivant montre comment utiliser un décodeur de bitmap pour décoder une image au format [!INCLUDE[TLA2#tla_bmp](../../../../includes/tla2sharptla-bmp-md.md)].  
  
 [!code-cpp[BmpBitmapDecoderEncoder#5](../../../../samples/snippets/cpp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CPP/anotherfile.cpp#5)]
 [!code-csharp[BmpBitmapDecoderEncoder#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CSharp/BitmapFrame.cs#5)]
 [!code-vb[BmpBitmapDecoderEncoder#5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/VB/BitmapFrame.vb#5)]  
  
### Encodage du format d'image  
 L'encodage d'une image est la traduction de données d'image en un format d'image spécifique.  Les données d'image encodées peuvent ensuite être utilisées pour créer des fichiers image.  [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] fournit des encodeurs pour chacun des formats d'image décrits ci\-dessus.  
  
 L'exemple suivant montre comment utiliser un encodeur pour enregistrer une image bitmap nouvellement créée.  
  
 [!code-cpp[BmpBitmapDecoderEncoder#3](../../../../samples/snippets/cpp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CPP/anotherfile.cpp#3)]
 [!code-csharp[BmpBitmapDecoderEncoder#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CSharp/BitmapFrame.cs#3)]
 [!code-vb[BmpBitmapDecoderEncoder#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/VB/BitmapFrame.vb#3)]  
  
<a name="_displayingimages"></a>   
## Affichage d'images dans WPF  
 Il existe plusieurs manières d'afficher une image dans une application [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)].  Les images peuvent être affichées en utilisant un contrôle <xref:System.Windows.Controls.Image>, peint sur un visuel à l'aide d'un <xref:System.Windows.Media.ImageBrush>, ou dessiné à l'aide d'un <xref:System.Windows.Media.ImageDrawing>.  
  
### Utilisation du contrôle d'image  
 <xref:System.Windows.Controls.Image> est un élément d'infrastructure et le principal moyen d'afficher des images dans les applications.  En [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], <xref:System.Windows.Controls.Image> peut être utilisé de deux façons ; syntaxe d'attribut ou syntaxe de propriété.  Les exemples suivants montrent comment restituer une image de 200 pixels de large à l'aide des syntaxes d'attribut et de balise de propriété.  Pour plus d'informations sur la syntaxe d'attribut et la syntaxe de propriété, consultez [Vue d'ensemble des propriétés de dépendance](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md).  
  
 [!code-xml[ImageElementExample_snip#ImageSimpleExampleInlineMarkup](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml#imagesimpleexampleinlinemarkup)]  
  
 La plupart des exemples utilisent un objet <xref:System.Windows.Media.Imaging.BitmapImage> pour référencer un fichier image.  <xref:System.Windows.Media.Imaging.BitmapImage> est un <xref:System.Windows.Media.Imaging.BitmapSource> spécialisé optimisé pour le chargement [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] qui permet d'afficher facilement des images comme la <xref:System.Windows.Controls.Image.Source%2A> d'un contrôle <xref:System.Windows.Controls.Image>.  
  
 L'exemple suivant montre comment restituer une image de 200 pixels de large à l'aide de code.  
  
> [!NOTE]
>  <xref:System.Windows.Media.Imaging.BitmapImage> implémente l'interface <xref:System.ComponentModel.ISupportInitialize> pour optimiser l'initialisation de plusieurs propriétés.  Les modifications de propriété ne peuvent se produire que lors de l'initialisation de l'objet.  Appelez <xref:System.Windows.Media.Imaging.BitmapImage.BeginInit%2A> pour signaler que l'initialisation a démarré et <xref:System.Windows.Media.Imaging.BitmapImage.EndInit%2A> pour signaler que l'initialisation est terminée.  Une fois initialisées, les modifications de propriété sont ignorées.  
  
 [!code-csharp[ImageElementExample_snip#ImageSimpleExampleInlineCode1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml.cs#imagesimpleexampleinlinecode1)]
 [!code-vb[ImageElementExample_snip#ImageSimpleExampleInlineCode1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/ImageSimpleExample.xaml.vb#imagesimpleexampleinlinecode1)]  
  
#### Rotation, conversion et rognage d'images  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] permet aux utilisateurs de transformer des images en utilisant des propriétés de <xref:System.Windows.Media.Imaging.BitmapImage> ou des objets <xref:System.Windows.Media.Imaging.BitmapSource> supplémentaires tels que <xref:System.Windows.Media.Imaging.CroppedBitmap> ou <xref:System.Windows.Media.Imaging.FormatConvertedBitmap>.  Ces transformations d'image peuvent mettre à l'échelle ou faire pivoter une image, modifier le format de pixel d'une image ou rogner une image.  
  
 Les rotations d'image s'effectuent en utilisant la propriété <xref:System.Windows.Media.Imaging.BitmapImage.Rotation%2A> de <xref:System.Windows.Media.Imaging.BitmapImage>.  Les rotations s'effectuent uniquement par incréments de 90 degrés.  Dans l'exemple suivant, une image est pivotée de 90 degrés.  
  
 [!code-xml[ImageElementExample#TransformedXAML2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/TransformedImageExample.xaml#transformedxaml2)]  
  
 [!code-csharp[ImageElementExample#TransformedCSharp1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/TransformedImageExample.xaml.cs#transformedcsharp1)]
 [!code-vb[ImageElementExample#TransformedCSharp1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample/VB/TransformedImageExample.xaml.vb#transformedcsharp1)]  
  
 La conversion d'une image dans un format de pixel différent comme les nuances de gris s'effectue en utilisant <xref:System.Windows.Media.Imaging.FormatConvertedBitmap>.  Dans les exemples suivants, une image est convertie en <xref:System.Windows.Media.PixelFormats.Gray4%2A>.  
  
 [!code-xml[ImageElementExample_snip#ConvertedXAML2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/FormatConvertedExample.xaml#convertedxaml2)]  
  
 [!code-csharp[ImageElementExample_snip#ConvertedCSharp1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/FormatConvertedExample.xaml.cs#convertedcsharp1)]
 [!code-vb[ImageElementExample_snip#ConvertedCSharp1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/FormatConvertedExample.xaml.vb#convertedcsharp1)]  
  
 Pour rogner une image, utilisez la propriété <xref:System.Windows.UIElement.Clip%2A> de <xref:System.Windows.Controls.Image> ou <xref:System.Windows.Media.Imaging.CroppedBitmap>.  En général, si vous souhaitez afficher une portion d'une image, <xref:System.Windows.UIElement.Clip%2A> doit être utilisé.  Si vous avez besoin d'encoder et d'enregistrer une image rognée, <xref:System.Windows.Media.Imaging.CroppedBitmap> doit être utilisé.  Dans l'exemple suivant, une image est rognée à l'aide de la propriété Clip en utilisant <xref:System.Windows.Media.EllipseGeometry>.  
  
 [!code-xml[ImageElementExample_snip#CroppedXAMLUsingClip1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/CroppedImageExample.xaml#croppedxamlusingclip1)]  
  
 [!code-csharp[ImageElementExample_snip#CroppedCSharpUsingClip1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/CroppedImageExample.xaml.cs#croppedcsharpusingclip1)]
 [!code-vb[ImageElementExample_snip#CroppedCSharpUsingClip1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/CroppedImageExample.xaml.vb#croppedcsharpusingclip1)]  
  
#### Étirement d'images  
 La propriété <xref:System.Windows.Controls.Image.Stretch%2A> contrôle la manière dont une image est étirée pour remplir son conteneur.  La propriété <xref:System.Windows.Controls.Image.Stretch%2A> accepte les valeurs suivantes, qui sont définies par l'énumération <xref:System.Windows.Media.Stretch> :  
  
-   <xref:System.Windows.Media.Stretch> : l'image n'est pas étirée pour remplir la zone de sortie.  Si l'image est plus grande que la zone de sortie, elle est dessinée sur la zone de sortie, en découpant ce qui ne s'ajuste pas.  
  
-   <xref:System.Windows.Media.Stretch> : l'image n'est pas mise à l'échelle pour s'ajuster à la zone de sortie.  Comme la hauteur et la largeur d'image sont mises à l'échelle indépendamment, les proportions d'origine de l'image ne sont pas nécessairement conservées.  Autrement dit, l'image peut être retracée pour remplir complètement le conteneur de sortie.  
  
-   <xref:System.Windows.Media.Stretch> : l'image est mise à l'échelle de manière à s'ajuster complètement à la zone de sortie.  Les proportions de l'image sont conservées.  
  
-   <xref:System.Windows.Media.Stretch> : l'image est mise à l'échelle de manière à remplir complètement la zone de sortie tout en conservant ses proportions d'origine.  
  
 L'exemple suivant applique chacune des énumérations <xref:System.Windows.Media.Stretch> disponibles sur une <xref:System.Windows.Controls.Image>.  
  
 L'image suivante montre le résultat de l'exemple et montre les effets obtenus par les différents paramètres <xref:System.Windows.Controls.Image.Stretch%2A> lorsqu'ils sont appliqués à une image.  
  
 ![Différents paramètres d'étirement TileBrush](../../../../docs/framework/wpf/graphics-multimedia/media/img-mmgraphics-stretchenum.png "img\_mmgraphics\_stretchenum")  
Paramètres d'étirement différents  
  
 [!code-xml[ImageElementExample_snip#ImageStretchExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageStretchExample.xaml#imagestretchexamplewholepage)]  
  
### Peinture avec des images  
 Les images peuvent également être affichées dans une application en peignant avec un <xref:System.Windows.Media.Brush>.  Les pinceaux vous permettent de peindre des objets [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] avec n'importe quoi, des couleurs simples et soldes aux ensembles complexes de modèles et d'images.  Pour peindre avec des images, utilisez un <xref:System.Windows.Media.ImageBrush>.  Un <xref:System.Windows.Media.ImageBrush> est un type de <xref:System.Windows.Media.TileBrush> qui définit son contenu comme une image bitmap.  Un <xref:System.Windows.Media.ImageBrush> affiche une seule image qui est spécifiée par sa propriété <xref:System.Windows.Media.ImageBrush.ImageSource%2A>.  Vous pouvez contrôler la manière dont l'image est étirée, alignée et mise en mosaïque, ce qui vous permet d'éviter la distorsion et de produire des modèles et autres effets.  L'illustration suivante indique divers effets pouvant être accomplis avec un <xref:System.Windows.Media.ImageBrush>.  
  
 ![Exemples de sortie ImageBrush](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-mmgraphics-imagebrushexamples.png "wcpsdk\_mmgraphics\_imagebrushexamples")  
Les pinceaux d'image peuvent remplir des formes, des contrôles, du texte, etc.  
  
 L'exemple suivant montre comment peindre l'arrière\-plan d'un bouton avec une image à l'aide d'un <xref:System.Windows.Media.ImageBrush>.  
  
 [!code-xml[UsingImageBrush#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush/CS/PaintingWithImages.xaml#4)]  
  
 Pour plus d'informations sur <xref:System.Windows.Media.ImageBrush> et la peinture d'images, consultez [Peinture avec des objets d'image, de dessin et visuels](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md).  
  
<a name="_metadata"></a>   
## Métadonnées d'image  
 Certains fichiers image contiennent des métadonnées qui décrivent le contenu ou les caractéristiques du fichier.  Par exemple, la plupart des appareils photo numériques créent des images contenant des métadonnées sur la marque et le modèle de l'appareil photo utilisé pour capturer l'image.  Chaque format d'image gère les métadonnées différemment, mais la [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] offre un moyen uniforme de stocker et de récupérer les métadonnées pour chaque format d'image pris en charge.  
  
 L'accès aux métadonnées s'effectue via la propriété <xref:System.Windows.Media.Imaging.BitmapSource.Metadata%2A> d'un objet <xref:System.Windows.Media.Imaging.BitmapSource>.  <xref:System.Windows.Media.Imaging.BitmapSource.Metadata%2A> retourne un objet <xref:System.Windows.Media.Imaging.BitmapMetadata> qui inclut toutes les métadonnées contenues par l'image.  Ces données peuvent figurer dans un schéma de métadonnées ou dans une combinaison de différents schémas.  [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] prend en charge les schémas de métadonnées d'image suivants : [!INCLUDE[TLA#tla_exif](../../../../includes/tlasharptla-exif-md.md)], tEXt \(PNG Textual Data\), [!INCLUDE[TLA#tla_ifd](../../../../includes/tlasharptla-ifd-md.md)], [!INCLUDE[TLA#tla_iptc](../../../../includes/tlasharptla-iptc-md.md)] et [!INCLUDE[TLA#tla_xmp](../../../../includes/tlasharptla-xmp-md.md)].  
  
 Afin de simplifier le processus de lecture des métadonnées, <xref:System.Windows.Media.Imaging.BitmapMetadata> fournit plusieurs propriétés nommées facilement accessibles telles que <xref:System.Windows.Media.Imaging.BitmapMetadata.Author%2A>, <xref:System.Windows.Media.Imaging.BitmapMetadata.Title%2A> et <xref:System.Windows.Media.Imaging.BitmapMetadata.CameraModel%2A>.  La plupart de ces propriétés nommées peuvent également être utilisées pour écrire des métadonnées.  Une prise en charge de lecture des métadonnées supplémentaire  est fournie par le lecteur de requêtes de métadonnées.  La méthode <xref:System.Windows.Media.Imaging.BitmapMetadata.GetQuery%2A> sert à récupérer un lecteur de requêtes de métadonnées en fournissant une requête de chaîne telle que *"\/app1\/exif\/"*.  Dans l'exemple suivant, <xref:System.Windows.Media.Imaging.BitmapMetadata.GetQuery%2A> est utilisé pour obtenir le texte stocké dans l'emplacement *"\/Texte\/Description"*.  
  
 [!code-cpp[BitmapMetadata#GetQuery](../../../../samples/snippets/cpp/VS_Snippets_Wpf/BitMapMetadata/CPP/BitmapMetadata.cpp#getquery)]
 [!code-csharp[BitmapMetadata#GetQuery](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BitMapMetadata/CSharp/BitmapMetadata.cs#getquery)]
 [!code-vb[BitmapMetadata#GetQuery](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BitMapMetadata/VB/BitmapMetadata.vb#getquery)]  
  
 Pour écrire les métadonnées, un writer de requête de métadonnées est utilisé.  <xref:System.Windows.Media.Imaging.BitmapMetadata.SetQuery%2A> obtient le writer de requête et définit la valeur souhaitée.  Dans l'exemple suivant, <xref:System.Windows.Media.Imaging.BitmapMetadata.SetQuery%2A> est utilisé pour enregistrer le texte stocké dans l'emplacement *"\/Texte\/Description"*.  
  
 [!code-cpp[BitmapMetadata#SetQuery](../../../../samples/snippets/cpp/VS_Snippets_Wpf/BitMapMetadata/CPP/BitmapMetadata.cpp#setquery)]
 [!code-csharp[BitmapMetadata#SetQuery](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BitMapMetadata/CSharp/BitmapMetadata.cs#setquery)]
 [!code-vb[BitmapMetadata#SetQuery](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BitMapMetadata/VB/BitmapMetadata.vb#setquery)]  
  
<a name="_extensibility"></a>   
## Extensibilité codec  
 Une fonctionnalité principale de la [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] est le modèle d'extensibilité pour les nouveaux codecs d'image.  Ces interfaces non managées permettent aux développeurs de codec d'intégrer des codecs à [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] afin que de nouveaux formats d'image puissent être utilisés automatiquement par les applications [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].  
  
 Pour obtenir un exemple d'[!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] d'extensibilité, consultez [Codec Win32, exemple](http://go.microsoft.com/fwlink/?LinkID=160052).  L'exemple montre comment créer un décodeur et un encodeur pour un format d'image personnalisé.  
  
> [!NOTE]
>  Le codec doit être signé numériquement pour que le système le reconnaisse.  
  
## Voir aussi  
 <xref:System.Windows.Media.Imaging.BitmapSource>   
 <xref:System.Windows.Media.Imaging.BitmapImage>   
 <xref:System.Windows.Controls.Image>   
 <xref:System.Windows.Media.Imaging.BitmapMetadata>   
 [Graphiques 2D et acquisition d'images](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)   
 [Exemple de codec Win32 \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkID=160052)