---
title: "Vue d'ensemble de la création d'images"
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
- cpp
helpviewer_keywords:
- metadata [WPF], images
- displaying images [WPF]
- Imaging API [WPF]
- image metadata [WPF]
- converting images [WPF]
- encoding image formats [WPF]
- format decoding for images [WPF]
- painting with images [WPF]
- stretching images [WPF]
- images [WPF], about imaging
- format encoding for images [WPF]
- cropping images [WPF]
- decoding image formats [WPF]
- rotating images [WPF]
ms.assetid: 72aad87a-e6f3-4937-94cd-a18b7766e990
caps.latest.revision: "32"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6821b724e45ea90a5b22c6efe6c36ee3b99e39ec
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="imaging-overview"></a>Vue d'ensemble de la création d'images
Cette rubrique fournit une introduction au [!INCLUDE[TLA#tla_wic](../../../../includes/tlasharptla-wic-md.md)]. [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] permet aux développeurs d’afficher, de transformer et de mettre en forme des images.  
  
  
<a name="_wpfImaging"></a>   
## <a name="wpf-imaging-component"></a>Composant de création d’images WPF  
 [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] apporte d’importantes améliorations aux fonctionnalités de création d’images dans [!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)]. Les fonctionnalités de création d’images, comme l’affichage d’une bitmap ou l’utilisation d’une image sur un contrôle ordinaire, dépendaient auparavant des bibliothèques [!INCLUDE[TLA#tla_gdi](../../../../includes/tlasharptla-gdi-md.md)] ou [!INCLUDE[TLA#tla_gdiplus](../../../../includes/tlasharptla-gdiplus-md.md)]. Ces [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] proposent des fonctionnalités de base en matière de création d’images, mais elles sont dépourvues de certaines autres fonctionnalités telles que la prise en charge de l’extensibilité de codec et des images haute fidélité. [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] a été conçu de manière à surmonter les lacunes de [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] et [!INCLUDE[TLA2#tla_gdiplus](../../../../includes/tla2sharptla-gdiplus-md.md)], et à fournir un nouvel ensemble d’[!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] pour afficher et utiliser des images dans vos applications.  
  
 Il existe deux moyens d’accéder à l’[!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] de [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] : un composant managé et un composant non managé. Le composant non managé fournit les fonctionnalités suivantes.  
  
-   Modèle d’extensibilité pour les formats d’image nouveaux ou propriétaires.  
  
-   Amélioration des performances et de la sécurité sur les formats d’image natifs, notamment [!INCLUDE[TLA#tla_bmp](../../../../includes/tlasharptla-bmp-md.md)], [!INCLUDE[TLA#tla_jpegorg](../../../../includes/tlasharptla-jpegorg-md.md)], [!INCLUDE[TLA#tla_png](../../../../includes/tlasharptla-png-md.md)], [!INCLUDE[TLA#tla_tiff](../../../../includes/tlasharptla-tiff-md.md)], [!INCLUDE[TLA#tla_wdp](../../../../includes/tlasharptla-wdp-md.md)], [!INCLUDE[TLA#tla_gif](../../../../includes/tlasharptla-gif-md.md)] et les icônes (.ico).  
  
-   Préservation de la profondeur de couleur élevée des données image jusqu’à 8 bits par canal (32 bits par pixel).  
  
-   Mise à l’échelle, rognage et rotation d’image non destructives.  
  
-   Gestion des couleurs simplifiée.  
  
-   Prise en charge des métadonnées dans les fichiers propriétaires.  
  
-   Le composant managé utilise l’infrastructure non managée pour fournir une intégration transparente d’images avec d’autres fonctionnalités [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], telles que l’[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)], l’animation et les graphiques. Le composant managé bénéficie également du modèle d’extensibilité codec de création d’images [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] qui permet la reconnaissance automatique des nouveaux formats d’image dans les applications [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].  
  
 La plupart des [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] résident dans le <xref:System.Windows.Media.Imaging?displayProperty=nameWithType> espace de noms, bien que plusieurs types importants, tels que <xref:System.Windows.Media.ImageBrush> et <xref:System.Windows.Media.ImageDrawing> résident dans le <xref:System.Windows.Media?displayProperty=nameWithType> espace de noms et <xref:System.Windows.Controls.Image> réside dans le <xref:System.Windows.Controls?displayProperty=nameWithType> espace de noms.  
  
 Cette rubrique fournit des informations supplémentaires sur le composant managé. Pour plus d’informations sur l’[!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] non managée, consultez la documentation [Composant de création d’images WPF non managé](https://msdn.microsoft.com/library/ee719902.aspx).  
  
<a name="_imageformats"></a>   
## <a name="wpf-image-formats"></a>Formats d’image WPF  
 Un codec est utilisé pour décoder ou encoder un format de média spécifique. [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] comprend un codec pour les formats d’image [!INCLUDE[TLA2#tla_bmp](../../../../includes/tla2sharptla-bmp-md.md)], [!INCLUDE[TLA2#tla_jpeg](../../../../includes/tla2sharptla-jpeg-md.md)], [!INCLUDE[TLA2#tla_png](../../../../includes/tla2sharptla-png-md.md)], [!INCLUDE[TLA2#tla_tiff](../../../../includes/tla2sharptla-tiff-md.md)], [!INCLUDE[TLA2#tla_wdp](../../../../includes/tla2sharptla-wdp-md.md)], [!INCLUDE[TLA2#tla_gif](../../../../includes/tla2sharptla-gif-md.md)] et ICON. Chacun de ces codecs permet aux applications de décoder et, sauf pour les icônes, d’encoder leurs formats d’image respectifs.  
  
 <xref:System.Windows.Media.Imaging.BitmapSource>est une classe importante utilisée dans le décodage et l’encodage d’images. Il s’agit du bloc de construction de base du pipeline de [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] et représente un seul jeu constant de pixels à une certaine taille et à une résolution donnée. A <xref:System.Windows.Media.Imaging.BitmapSource> peut être une frame individuelle d’une image à plusieurs frames, ou il peut être le résultat d’une transformation effectuée sur un <xref:System.Windows.Media.Imaging.BitmapSource>. Il est le parent de nombreuses classes principales utilisées dans [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] imaging comme <xref:System.Windows.Media.Imaging.BitmapFrame>.  
  
 A <xref:System.Windows.Media.Imaging.BitmapFrame> est utilisé pour stocker les données bitmap actuelles d’un format d’image. Nombreux formats d’image prennent uniquement en charge un seul <xref:System.Windows.Media.Imaging.BitmapFrame>, bien que les formats tels que [!INCLUDE[TLA2#tla_gif](../../../../includes/tla2sharptla-gif-md.md)] et [!INCLUDE[TLA2#tla_tiff](../../../../includes/tla2sharptla-tiff-md.md)] prennent en charge plusieurs frames par image. Les cadres sont utilisés par les décodeurs comme données d’entrée et sont transmis à des encodeurs pour créer des fichiers image.  
  
 L’exemple suivant montre comment un <xref:System.Windows.Media.Imaging.BitmapFrame> créé à partir d’un <xref:System.Windows.Media.Imaging.BitmapSource> puis ajoutés à un [!INCLUDE[TLA2#tla_tiff](../../../../includes/tla2sharptla-tiff-md.md)] image.  
  
 [!code-csharp[BitmapFrameExample#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BitmapFrameExample/CSharp/BitmapFrame.cs#10)]
 [!code-vb[BitmapFrameExample#10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BitmapFrameExample/VB/BitmapFrame.vb#10)]  
  
### <a name="image-format-decoding"></a>Décodage du format d’image  
 Le décodage d’une image est la traduction d’un format d’image en données d’image pouvant être utilisées par le système. Les données d’image peuvent ensuite être utilisées pour afficher, traiter ou encoder dans un format différent. La sélection du décodeur dépend du format d’image. La sélection du codec est automatique à moins qu’un décodeur spécifique ne soit indiqué. Les exemples de la section [Affichage d’images dans WPF](#_displayingimages) illustrent le décodage automatique. Les décodeurs de formats personnalisés développés à l’aide d’interfaces [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] non managées et inscrits automatiquement dans le système participent à la sélection du décodeur. Cela permet d’afficher automatiquement les formats personnalisés dans les applications [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].  
  
 L’exemple suivant illustre l’utilisation d’un décodeur de bitmap pour décoder une image au format [!INCLUDE[TLA2#tla_bmp](../../../../includes/tla2sharptla-bmp-md.md)].  
  
 [!code-cpp[BmpBitmapDecoderEncoder#5](../../../../samples/snippets/cpp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CPP/anotherfile.cpp#5)]
 [!code-csharp[BmpBitmapDecoderEncoder#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CSharp/BitmapFrame.cs#5)]
 [!code-vb[BmpBitmapDecoderEncoder#5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/VB/BitmapFrame.vb#5)]  
  
### <a name="image-format-encoding"></a>Encodage du format d’image  
 L’encodage d’image est la traduction de données d’image en un format d’image spécifique. Les données d’image encodées peuvent ensuite servir à créer des fichiers image. [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] fournit des encodeurs pour chacun des formats d’image décrits ci-dessus.  
  
 L’exemple suivant illustre l’utilisation d’un encodeur pour enregistrer une image bitmap nouvellement créée.  
  
 [!code-cpp[BmpBitmapDecoderEncoder#3](../../../../samples/snippets/cpp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CPP/anotherfile.cpp#3)]
 [!code-csharp[BmpBitmapDecoderEncoder#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CSharp/BitmapFrame.cs#3)]
 [!code-vb[BmpBitmapDecoderEncoder#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/VB/BitmapFrame.vb#3)]  
  
<a name="_displayingimages"></a>   
## <a name="displaying-images-in-wpf"></a>Affichage d’images dans WPF  
 Il existe plusieurs manières d’afficher une image dans une application [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)]. Images peuvent être affichées à l’aide un <xref:System.Windows.Controls.Image> contrôle, peint sur un visuel à l’aide un <xref:System.Windows.Media.ImageBrush>, ou dessiné à l’aide un <xref:System.Windows.Media.ImageDrawing>.  
  
### <a name="using-the-image-control"></a>Utilisation du contrôle Image  
 <xref:System.Windows.Controls.Image>est un élément d’infrastructure et le principal moyen d’afficher des images dans les applications. Dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], <xref:System.Windows.Controls.Image> peut être utilisé de deux manières ; de la syntaxe d’attribut ou de syntaxe de la propriété. L’exemple suivant montre comment restituer une image de 200 pixels de large à l’aide de la syntaxe d’attribut et de la syntaxe de balise de propriété. Pour plus d’informations sur les syntaxes d’attribut et de propriété, consultez [Vue d’ensemble des propriétés de dépendance](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md).  
  
 [!code-xaml[ImageElementExample_snip#ImageSimpleExampleInlineMarkup](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml#imagesimpleexampleinlinemarkup)]  
  
 La plupart des exemples utilisent un <xref:System.Windows.Media.Imaging.BitmapImage> objet pour faire référence à un fichier image. <xref:System.Windows.Media.Imaging.BitmapImage>est spécialisé <xref:System.Windows.Media.Imaging.BitmapSource> qui est optimisé pour [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] le chargement et est un moyen simple pour afficher des images en tant que le <xref:System.Windows.Controls.Image.Source%2A> d’un <xref:System.Windows.Controls.Image> contrôle.  
  
 L’exemple suivant montre comment afficher une image de 200 pixels de large à l’aide de code.  
  
> [!NOTE]
>  <xref:System.Windows.Media.Imaging.BitmapImage>implémente le <xref:System.ComponentModel.ISupportInitialize> interface pour optimiser l’initialisation de plusieurs propriétés. Les modifications de propriété ne peuvent se produire que lors de l’initialisation de l’objet. Appelez <xref:System.Windows.Media.Imaging.BitmapImage.BeginInit%2A> pour signaler que l’initialisation a commencé et <xref:System.Windows.Media.Imaging.BitmapImage.EndInit%2A> pour signaler que l’initialisation est terminée. Une fois initialisées, les modifications de propriété sont ignorées.  
  
 [!code-csharp[ImageElementExample_snip#ImageSimpleExampleInlineCode1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml.cs#imagesimpleexampleinlinecode1)]
 [!code-vb[ImageElementExample_snip#ImageSimpleExampleInlineCode1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/ImageSimpleExample.xaml.vb#imagesimpleexampleinlinecode1)]  
  
#### <a name="rotating-converting-and-cropping-images"></a>Rotation, conversion et rognage d’images  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]permet aux utilisateurs de transformer les images à l’aide des propriétés de <xref:System.Windows.Media.Imaging.BitmapImage> ou à l’aide supplémentaire <xref:System.Windows.Media.Imaging.BitmapSource> objets tels que <xref:System.Windows.Media.Imaging.CroppedBitmap> ou <xref:System.Windows.Media.Imaging.FormatConvertedBitmap>. Ces transformations d’image peuvent mettre à l’échelle ou faire pivoter une image, changer le format de pixel d’une image ou rogner une image.  
  
 Rotations d’image sont effectuées à l’aide de la <xref:System.Windows.Media.Imaging.BitmapImage.Rotation%2A> propriété du <xref:System.Windows.Media.Imaging.BitmapImage>. Les rotations s’effectuent uniquement par incréments de 90 degrés. Dans l’exemple suivant, une image est pivotée de 90 degrés.  
  
 [!code-xaml[ImageElementExample#TransformedXAML2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/TransformedImageExample.xaml#transformedxaml2)]  
  
 [!code-csharp[ImageElementExample#TransformedCSharp1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/TransformedImageExample.xaml.cs#transformedcsharp1)]
 [!code-vb[ImageElementExample#TransformedCSharp1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample/VB/TransformedImageExample.xaml.vb#transformedcsharp1)]  
  
 Conversion d’une image dans un format de pixel différent comme les nuances de gris s’effectue à l’aide <xref:System.Windows.Media.Imaging.FormatConvertedBitmap>. Dans les exemples suivants, une image est convertie en <xref:System.Windows.Media.PixelFormats.Gray4%2A>.  
  
 [!code-xaml[ImageElementExample_snip#ConvertedXAML2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/FormatConvertedExample.xaml#convertedxaml2)]  
  
 [!code-csharp[ImageElementExample_snip#ConvertedCSharp1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/FormatConvertedExample.xaml.cs#convertedcsharp1)]
 [!code-vb[ImageElementExample_snip#ConvertedCSharp1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/FormatConvertedExample.xaml.vb#convertedcsharp1)]  
  
 Pour rogner une image, soit le <xref:System.Windows.UIElement.Clip%2A> propriété du <xref:System.Windows.Controls.Image> ou <xref:System.Windows.Media.Imaging.CroppedBitmap> peut être utilisé. En règle générale, si vous souhaitez simplement afficher une partie d’une image, <xref:System.Windows.UIElement.Clip%2A> doit être utilisé. Si vous avez besoin encoder et enregistrer une image rognée, le <xref:System.Windows.Media.Imaging.CroppedBitmap> doit être utilisé. Dans l’exemple suivant, une image est rognée à l’aide de la propriété d’élément en utilisant un <xref:System.Windows.Media.EllipseGeometry>.  
  
 [!code-xaml[ImageElementExample_snip#CroppedXAMLUsingClip1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/CroppedImageExample.xaml#croppedxamlusingclip1)]  
  
 [!code-csharp[ImageElementExample_snip#CroppedCSharpUsingClip1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/CroppedImageExample.xaml.cs#croppedcsharpusingclip1)]
 [!code-vb[ImageElementExample_snip#CroppedCSharpUsingClip1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/CroppedImageExample.xaml.vb#croppedcsharpusingclip1)]  
  
#### <a name="stretching-images"></a>Étirement d’images  
 Le <xref:System.Windows.Controls.Image.Stretch%2A> propriété contrôle la façon dont une image est étirée pour remplir son conteneur. Le <xref:System.Windows.Controls.Image.Stretch%2A> propriété accepte les valeurs suivantes, définies par le <xref:System.Windows.Media.Stretch> énumération :  
  
-   <xref:System.Windows.Media.Stretch.None>: L’image n’est pas étiré pour remplir la zone de sortie. Si l’image est plus grande que la zone de sortie, elle est dessinée sur la zone de sortie, en découpant ce qui ne s’ajuste pas.  
  
-   <xref:System.Windows.Media.Stretch.Fill>: L’image est dimensionnée pour remplir la zone de sortie. Étant donné que la hauteur et la largeur de l’image sont mises à l’échelle indépendamment, les proportions d’origine de l’image risquent de ne pas être conservées. Autrement dit, l’image peut être déformée pour remplir complètement le conteneur de sortie.  
  
-   <xref:System.Windows.Media.Stretch.Uniform>: L’image est mise à l’échelle afin qu’elle s’adapte parfaitement au sein de la zone de sortie. Les proportions de l’image sont conservées.  
  
-   <xref:System.Windows.Media.Stretch.UniformToFill>: L’image est mise à l’échelle afin qu’il remplisse complètement la zone de sortie tout en conservant les proportions d’origine de l’image.  
  
 L’exemple suivant s’applique à chacun des disponibles <xref:System.Windows.Media.Stretch> énumérations d’un <xref:System.Windows.Controls.Image>.  
  
 L’illustration suivante montre la sortie de l’exemple et montre les effets différents <xref:System.Windows.Controls.Image.Stretch%2A> paramètres été appliqués à une image.  
  
 ![Différents paramètres d’étirement TileBrush](../../../../docs/framework/wpf/graphics-multimedia/media/img-mmgraphics-stretchenum.jpg "img_mmgraphics_stretchenum")  
Différents paramètres d’étirement TileBrush  
  
 [!code-xaml[ImageElementExample_snip#ImageStretchExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageStretchExample.xaml#imagestretchexamplewholepage)]  
  
### <a name="painting-with-images"></a>Peinture avec des images  
 Images peuvent également être affichées dans une application en utilisant la peinture avec un <xref:System.Windows.Media.Brush>. Les pinceaux permettent de peindre des objets de l’[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] aussi bien avec de simples couleurs unies qu’avec des ensembles complexes de modèles et d’images. Pour peindre des images, utilisez un <xref:System.Windows.Media.ImageBrush>. Un <xref:System.Windows.Media.ImageBrush> est un type de <xref:System.Windows.Media.TileBrush> qui définit son contenu comme une image bitmap. Un <xref:System.Windows.Media.ImageBrush> affiche une seule image, ce qui est spécifiée par son <xref:System.Windows.Media.ImageBrush.ImageSource%2A> propriété. Vous pouvez contrôler la manière dont l’image est étirée, alignée et mise en mosaïque, ce qui vous permet d’éviter la distorsion et de produire des modèles et d’autres effets. L’illustration suivante montre certains effets qui peuvent être réalisées avec un <xref:System.Windows.Media.ImageBrush>.  
  
 ![Exemples de sortie ImageBrush](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-mmgraphics-imagebrushexamples.gif "wcpsdk_mmgraphics_imagebrushexamples")  
Les pinceaux d’image peuvent remplir des formes, des contrôles, du texte, etc.  
  
 L’exemple suivant montre comment peindre l’arrière-plan d’un bouton avec une image en utilisant un <xref:System.Windows.Media.ImageBrush>.  
  
 [!code-xaml[UsingImageBrush#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush/CS/PaintingWithImages.xaml#4)]  
  
 Pour plus d’informations sur <xref:System.Windows.Media.ImageBrush> et peinture d’images, consultez [peinture avec des Images, des dessins et des éléments visuels](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md).  
  
<a name="_metadata"></a>   
## <a name="image-metadata"></a>Métadonnées d’image  
 Certains fichiers image contiennent des métadonnées qui décrivent le contenu ou les caractéristiques du fichier. Par exemple, la plupart des appareils photo numériques créent des images qui contiennent des métadonnées sur la marque et le modèle de l’appareil photo utilisé pour capturer l’image. Chaque format d’image gère les métadonnées différemment, mais [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] offre un moyen uniforme de stocker et récupérer des métadonnées pour chaque format d’image pris en charge.  
  
 Accès aux métadonnées est fournie par le <xref:System.Windows.Media.Imaging.BitmapSource.Metadata%2A> propriété d’un <xref:System.Windows.Media.Imaging.BitmapSource> objet. <xref:System.Windows.Media.Imaging.BitmapSource.Metadata%2A>Retourne un <xref:System.Windows.Media.Imaging.BitmapMetadata> objet qui inclut toutes les métadonnées contenues par l’image. Ces données peuvent figurer dans un schéma de métadonnées ou dans une combinaison de différents schémas. [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] prend en charge les schémas de métadonnées d’image suivants : [!INCLUDE[TLA#tla_exif](../../../../includes/tlasharptla-exif-md.md)], tEXt (PNG Textual Data), [!INCLUDE[TLA#tla_ifd](../../../../includes/tlasharptla-ifd-md.md)], [!INCLUDE[TLA#tla_iptc](../../../../includes/tlasharptla-iptc-md.md)] et [!INCLUDE[TLA#tla_xmp](../../../../includes/tlasharptla-xmp-md.md)].  
  
 Afin de simplifier le processus de lecture des métadonnées, <xref:System.Windows.Media.Imaging.BitmapMetadata> fournit plusieurs propriétés nommées facilement accessibles comme <xref:System.Windows.Media.Imaging.BitmapMetadata.Author%2A>, <xref:System.Windows.Media.Imaging.BitmapMetadata.Title%2A>, et <xref:System.Windows.Media.Imaging.BitmapMetadata.CameraModel%2A>. La plupart de ces propriétés nommées peuvent également servir à écrire des métadonnées. Une prise en charge de lecture des métadonnées supplémentaire est fournie par le lecteur de requêtes de métadonnées. Le <xref:System.Windows.Media.Imaging.BitmapMetadata.GetQuery%2A> méthode est utilisée pour récupérer un lecteur de requêtes de métadonnées en fournissant une requête de chaîne comme *« / app1/exif / «*. Dans l’exemple suivant, <xref:System.Windows.Media.Imaging.BitmapMetadata.GetQuery%2A> est utilisée pour obtenir le texte stocké dans le *« Texte/Description »* emplacement.  
  
 [!code-cpp[BitmapMetadata#GetQuery](../../../../samples/snippets/cpp/VS_Snippets_Wpf/BitMapMetadata/CPP/BitmapMetadata.cpp#getquery)]
 [!code-csharp[BitmapMetadata#GetQuery](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BitMapMetadata/CSharp/BitmapMetadata.cs#getquery)]
 [!code-vb[BitmapMetadata#GetQuery](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BitMapMetadata/VB/BitmapMetadata.vb#getquery)]  
  
 Pour écrire des métadonnées, un lecteur de requêtes de métadonnées est utilisé. <xref:System.Windows.Media.Imaging.BitmapMetadata.SetQuery%2A>Obtient le writer de requête et définit la valeur souhaitée. Dans l’exemple suivant, <xref:System.Windows.Media.Imaging.BitmapMetadata.SetQuery%2A> est utilisé pour écrire le texte stocké dans le *« Texte/Description »* emplacement.  
  
 [!code-cpp[BitmapMetadata#SetQuery](../../../../samples/snippets/cpp/VS_Snippets_Wpf/BitMapMetadata/CPP/BitmapMetadata.cpp#setquery)]
 [!code-csharp[BitmapMetadata#SetQuery](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BitMapMetadata/CSharp/BitmapMetadata.cs#setquery)]
 [!code-vb[BitmapMetadata#SetQuery](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BitMapMetadata/VB/BitmapMetadata.vb#setquery)]  
  
<a name="_extensibility"></a>   
## <a name="codec-extensibility"></a>Extensibilité des codecs  
 [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] intègre, entre autres fonctionnalités essentielles, un modèle d’extensibilité pour les nouveaux codecs d’image. Ces interfaces non managées permettent aux développeurs de codecs d’intégrer des codecs à [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] afin que les nouveaux formats d’image puissent automatiquement servir aux applications [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].  
  
 Pour obtenir un exemple d’extensibilité [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)], consultez la [Codec Win32, exemple](http://go.microsoft.com/fwlink/?LinkID=160052). Cet exemple montre comment créer un décodeur et un encodeur pour un format d’image personnalisé.  
  
> [!NOTE]
>  Le codec doit être signé numériquement pour pouvoir être reconnu par le système.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Media.Imaging.BitmapSource>  
 <xref:System.Windows.Media.Imaging.BitmapImage>  
 <xref:System.Windows.Controls.Image>  
 <xref:System.Windows.Media.Imaging.BitmapMetadata>  
 [Graphiques 2D et acquisition d'images](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)  
 [Codec Win32, exemple](http://go.microsoft.com/fwlink/?LinkID=160052)
