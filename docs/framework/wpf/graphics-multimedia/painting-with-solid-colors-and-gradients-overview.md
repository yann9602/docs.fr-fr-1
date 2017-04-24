---
title: "Vue d&#39;ensemble de la peinture avec des couleurs unies ou des d&#233;grad&#233;s | Microsoft Docs"
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
  - "pinceaux, peindre avec des dégradés"
  - "pinceaux, peindre avec des couleurs unies"
  - "dégradés, peindre avec"
  - "peindre avec des dégradés"
  - "peindre avec des couleurs unies"
  - "couleurs unies, peindre avec"
ms.assetid: f5b182f3-c5c7-4cbe-9f2f-65e690d08255
caps.latest.revision: 21
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 18
---
# Vue d&#39;ensemble de la peinture avec des couleurs unies ou des d&#233;grad&#233;s
Cette rubrique décrit comment utiliser les objets <xref:System.Windows.Media.SolidColorBrush>, <xref:System.Windows.Media.LinearGradientBrush> et <xref:System.Windows.Media.RadialGradientBrush> pour peindre avec des couleurs unies, des dégradés linéaires et des dégradés radiaux.  
  
   
  
<a name="solidcolor"></a>   
## Peinture d'une zone avec une couleur unie  
 Une des opérations les plus courantes, sur n'importe quelle plateforme, est de peindre une zone de <xref:System.Windows.Media.Color> unie.  Pour effectuer cette tâche, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] fournit la classe <xref:System.Windows.Media.SolidColorBrush>.  Les sections suivantes décrivent les différentes manières de peindre avec <xref:System.Windows.Media.SolidColorBrush>.  
  
<a name="solidcolorinxaml"></a>   
### Utilisation de SolidColorBrush en "XAML"  
 Pour peindre une zone d'une couleur unie en [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], utilisez une des options suivantes.  
  
-   Sélectionnez un pinceau de couleur unie prédéfinie par son nom.  Par exemple, vous pouvez affecter au <xref:System.Windows.Controls.Control.Background%2A> d'un bouton la valeur "Red" ou "MediumBlue".  Pour obtenir la liste des autres pinceaux de couleur unie prédéfinie, consultez les propriétés statiques de la classe <xref:System.Windows.Media.Brushes>.  Voici un exemple :  
  
     [!code-xml[BrushOverviewExamples_snip#SolidColorBrushNamedColor1XAML](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/SolidColorBrushExample.xaml#solidcolorbrushnamedcolor1xaml)]  
  
-   Choisissez une couleur dans la palette de couleurs 32 bits en spécifiant les quantités de rouge, de vert et de bleu à combiner pour obtenir une seule couleur unie.  Le format utilisé pour définir une couleur de la palette 32 bits est "*\#rrvvbb*", où *rr* est un nombre hexadécimal à deux chiffres spécifiant la quantité relative de rouge, *vv* la quantité de vert et *bb* la quantité de bleu.  De plus, la couleur peut être spécifiée par "\#*aarrvvbb*" où *aa* spécifie la valeur *alpha*, ou transparence, de la couleur.  Cette approche vous permet de créer des couleurs qui sont partiellement transparentes.  Dans l'exemple suivant, <xref:System.Windows.Controls.Control.Background%2A> d'un <xref:System.Windows.Controls.Button> est défini à la valeur rouge entièrement opaque à l'aide de la notation hexadécimale.  
  
     [!code-xml[BrushOverviewExamples_snip#SolidColorBrushHex1XAML](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/SolidColorBrushExample.xaml#solidcolorbrushhex1xaml)]  
  
-   Utilisez la syntaxe de balise de propriété pour décrire <xref:System.Windows.Media.SolidColorBrush>.  Cette syntaxe est plus documentée, mais elle vous permet de spécifier des paramètres supplémentaires, tel que l'opacité du pinceau.  Dans l'exemple suivant, les propriétés <xref:System.Windows.Controls.Control.Background%2A> de deux éléments <xref:System.Windows.Controls.Button> ont la valeur rouge entièrement opaque.  La première couleur du pinceau est décrite à l'aide d'un nom de couleur prédéfinie.  La deuxième couleur du pinceau est décrite à l'aide de la notation hexadécimale.  
  
     [!code-xml[BrushOverviewExamples_snip#SolidColorBrushPropertyTag1XAML](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/SolidColorBrushExample.xaml#solidcolorbrushpropertytag1xaml)]  
  
<a name="solidcolorsincode"></a>   
### Peinture avec SolidColorBrush dans du code  
 Pour peindre une zone d'une couleur unie dans du code, utilisez l'une des options suivantes.  
  
-   Utilisez un des pinceaux prédéfinis fournis par la classe <xref:System.Windows.Media.Brushes>.  Dans l'exemple suivant, le <xref:System.Windows.Controls.Control.Background%2A> du <xref:System.Windows.Controls.Button> a la valeur <xref:System.Windows.Media.Brushes.Red%2A>.  
  
     [!code-csharp[BrushOverviewExamples_snip#SolidColorBrushPredefinedBrush1CSharp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/SolidColorBrushExample.cs#solidcolorbrushpredefinedbrush1csharp)]  
  
-   Créez un <xref:System.Windows.Media.SolidColorBrush> et affectez sa propriété <xref:System.Windows.Media.SolidColorBrush.Color%2A> à l'aide d'une structure <xref:System.Windows.Media.Color>.  Vous pouvez utiliser une couleur prédéfinie de la classe <xref:System.Windows.Media.Colors> ou vous pouvez créer une <xref:System.Windows.Media.Color> à l'aide de la méthode statique <xref:System.Windows.Media.Color.FromArgb%2A>.  
  
     L'exemple suivant montre comment affecter la propriété <xref:System.Windows.Media.SolidColorBrush.Color%2A> d'un <xref:System.Windows.Media.SolidColorBrush> à l'aide d'une couleur prédéfinie.  
  
     [!code-csharp[BrushOverviewExamples_snip#SolidColorBrushPredefinedColor1CSharp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/SolidColorBrushExample.cs#solidcolorbrushpredefinedcolor1csharp)]  
  
 La méthode statique <xref:System.Windows.Media.Color.FromArgb%2A> vous permet de spécifier les valeurs [alpha](GTMT), rouge, vert et bleu de la couleur.  La plage de ces valeurs s'étend en général de 0 à 255.  Par exemple, une valeur [alpha](GTMT) de 0 indique qu'une couleur est complètement transparente, tandis qu'une valeur de 255 indique que la couleur est complètement opaque.  De même, une valeur de rouge de 0 indique que cette couleur ne contient pas de rouge, tandis qu'une valeur de 255 indique que cette couleur contient la quantité maximum de rouge possible.  Dans l'exemple suivant, la couleur d'un pinceau est décrite en spécifiant les valeurs alpha, rouge, vert et bleu.  
  
 [!code-csharp[BrushOverviewExamples_snip#SolidColorBrushfromArgbExample1CSharp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/SolidColorBrushExample.cs#solidcolorbrushfromargbexample1csharp)]  
  
 Pour obtenir des informations sur d'autres manières de spécifier la couleur, consultez la rubrique de référence <xref:System.Windows.Media.Color>.  
  
<a name="gradient"></a>   
## Peinture d'une zone avec un dégradé  
 Les pinceaux à dégradé permettent de peindre une zone avec plusieurs couleurs qui fusionnent le long d'un axe.  Vous pouvez les utiliser pour créer des impressions d'ombre et de lumière, afin de donner à vos contrôles une apparence 3D.  Vous pouvez également les utiliser pour simuler du verre, du chrome, de l'eau et d'autres surfaces lisses.  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fournit deux types de pinceaux de dégradé : <xref:System.Windows.Media.LinearGradientBrush> et <xref:System.Windows.Media.RadialGradientBrush>.  
  
<a name="lineargradientbrush"></a>   
## Dégradés linéaires  
 <xref:System.Windows.Media.LinearGradientBrush> peint une zone avec un dégradé défini le long d'une ligne, l'*axe de dégradé*.  Vous pouvez spécifier les couleurs du dégradé et leur emplacement le long de l'axe de dégradé à l'aide des objets <xref:System.Windows.Media.GradientStop>.  Vous pouvez également modifier l'axe de dégradé, ce qui vous permet de créer des dégradés horizontaux et verticaux et d'inverser le sens du dégradé.  L'axe de dégradé est décrit dans la section suivante.  Par défaut, un dégradé est créé en diagonale.  
  
 L'exemple suivant affiche le code qui crée un dégradé linéaire de quatre couleurs.  
  
 [!code-xml[GradientBrushExamples_snip#DiagonalGradient1XAML](../../../../samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#diagonalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#DiagonalGradient1CSharp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#diagonalgradient1csharp)]  
  
 Ce code génère le dégradé suivant :  
  
 ![Dégradé linéaire en diagonale](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-diaglgradient-nolabel.png "wcpsdk\_graphicsmm\_diaglgradient\_nolabel")  
  
 **Remarque :** les exemples de dégradés de cette rubrique utilisent le système de coordonnées par défaut pour définir les points de départ et d'arrivée.  Le système de coordonnées par défaut est relatif par rapport à une zone englobante : 0 indique 0 % de la zone englobante, et 1 indique 100 % de la zone englobante.  Vous pouvez modifier ce système de coordonnées en affectant à la propriété <xref:System.Windows.Media.GradientBrush.MappingMode%2A> la valeur <xref:System.Windows.Media.BrushMappingMode>.  Un système de coordonnées absolues n'est pas relatif par rapport à une zone englobante.  Les valeurs sont interprétées directement dans l'espace local.  
  
 <xref:System.Windows.Media.GradientStop> est le bloc de construction de base d'un pinceau à dégradé.  Un point de dégradé spécifie une <xref:System.Windows.Media.GradientStop.Color%2A> à un <xref:System.Windows.Media.GradientStop.Offset%2A> le long de l'axe de dégradé.  
  
-   La propriété <xref:System.Windows.Media.GradientStop.Color%2A> du point de dégradé spécifie la couleur du point de dégradé.  Vous pouvez définir la couleur en utilisant une couleur prédéfinie \(fournie par la classe <xref:System.Windows.Media.Colors>\) ou en spécifiant les valeurs ScRVB ou ARVB.  En [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], vous pouvez aussi utiliser une notation hexadécimale pour décrire une couleur.  Pour plus d'informations, consultez la structure <xref:System.Windows.Media.Color>.  
  
-   La propriété <xref:System.Windows.Media.GradientStop.Offset%2A> du point de dégradé définit la position de la couleur du point de dégradé sur l'axe de dégradé.  L'offset est un <xref:System.Double> dont les valeurs s'étendent de 0 à 1.  Plus la valeur de l'offset d'un point de dégradé est proche de 0, plus la couleur est proche de celle du début du dégradé.  Plus la valeur de l'offset du dégradé est proche de 1, plus la couleur est proche de la fin du dégradé.  
  
 La couleur de chaque point entre deux points de dégradé est interpolée de façon linéaire sous la forme d'une combinaison des couleurs des deux points de dégradé englobants.  L'illustration suivante met en évidence les points de dégradé de l'exemple précédent.  Les cercles indiquent l'emplacement des points de dégradé et une ligne en pointillés montre l'axe de dégradé.  
  
 ![Points de dégradé dans un dégradé linéaire](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-4gradientstops.png "wcpsdk\_graphicsmm\_4gradientstops")  
  
 Le premier point de dégradé spécifie la couleur jaune à un offset de `0.0`.  Le deuxième point de dégradé spécifie la couleur rouge à un offset de `0.25`.  Les points situés entre ces deux points de dégradé passent graduellement du jaune au rouge lorsqu'on se déplace de la gauche vers la droite le long de l'axe de dégradé.  Le troisième point de dégradé spécifie la couleur bleue à un offset de `0.75`.  Les points situés entre le deuxième et le troisième point de dégradé passent progressivement du rouge au bleu.  Le quatrième point de dégradé spécifie la couleur vert citron à un offset de `1.0`.  Les points situés entre le troisième et le quatrième point de dégradé passent progressivement du bleu au vert citron.  
  
<a name="gradientaxis"></a>   
### L'axe de dégradé  
 Comme mentionné précédemment, les points de dégradé d'un pinceau à dégradé linéaire sont positionnés le long d'une ligne, l'axe de dégradé.  Vous pouvez modifier l'orientation et la taille de la ligne à l'aide des propriétés <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> et <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> du pinceau.  En manipulant les propriétés <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> et <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> du pinceau, vous pouvez créer des dégradés horizontaux et verticaux, inverser le sens du dégradé, concentrer la dispersion du dégradé, etc.  
  
 Par défaut, les propriétés <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> et <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> du pinceau à dégradé linéaire sont relatives par rapport à la zone qui est peinte.  Le point \(0,0\) représente l'angle supérieur gauche de la zone qui est peinte, et \(1,1\) représente l'angle inférieur droit de la zone qui est peinte.  La valeur par défaut de la propriété <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> de <xref:System.Windows.Media.LinearGradientBrush> est \(0,0\), et la valeur par défaut de <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> est \(1,1\), ce qui crée un dégradé diagonal qui commence à l'angle supérieur gauche et qui s'étend jusqu'à l'angle inférieur droit de la zone qui est peinte.  L'illustration suivante représente l'axe de dégradé d'un pinceau à dégradé linéaire avec les valeurs par défaut de <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> et <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A>.  
  
 ![Axe du dégradé pour un dégradé linéaire en diagonale](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-diagonalgradientaxis.png "wcpsdk\_graphicsmm\_diagonalgradientaxis")  
  
 L'exemple suivant montre comment créer un dégradé horizontal en spécifiant les propriétés <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> et <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> du pinceau.  Remarquez que les points de dégradé sont identiques à ceux des exemples précédents ; en modifiant simplement <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> et <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A>, le dégradé est passé de diagonal en horizontal.  
  
 [!code-xml[GradientBrushExamples_snip#HorizontalGradient1XAML](../../../../samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#horizontalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#HorizontalGradient1CSharp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#horizontalgradient1csharp)]  
  
 L'illustration suivante montre le dégradé qui est créé.  L'axe de dégradé est indiqué par une ligne en pointillés, et les points de dégradé sont indiqués par des cercles.  
  
 ![Axe du dégradé pour un dégradé linéaire horizontal](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-horizontalgradient.png "wcpsdk\_graphicsmm\_horizontalgradient")  
  
 L'exemple suivant montre comment créer un dégradé vertical.  
  
 [!code-xml[GradientBrushExamples_snip#VerticalGradient1XAML](../../../../samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#verticalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#VerticalGradient1CSharp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#verticalgradient1csharp)]  
  
 L'illustration suivante montre le dégradé qui est créé.  L'axe de dégradé est indiqué par une ligne en pointillés, et les points de dégradé sont indiqués par des cercles.  
  
 ![Axe du dégradé pour un dégradé vertical](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-verticalgradient.png "wcpsdk\_graphicsmm\_verticalgradient")  
  
<a name="radialgradients"></a>   
## Dégradés radiaux  
 De même que <xref:System.Windows.Media.LinearGradientBrush>, <xref:System.Windows.Media.RadialGradientBrush> peint une zone avec des couleurs qui fusionnent le long d'un axe.  Les exemples précédents montraient que l'axe d'un pinceau à dégradé linéaire est une ligne droite.  Un axe de pinceau à dégradé radial est défini par un cercle ; ses couleurs "rayonnent" de son origine vers l'extérieur.  
  
 Dans l'exemple suivant, un pinceau à dégradé radial est utilisé pour peindre l'intérieur d'un rectangle.  
  
 [!code-xml[GradientBrushExamples_snip#RadialGradient1XAML](../../../../samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/RadialGradientBrushExample.xaml#radialgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#RadialGradient1CSharp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/RadialGradientBrushExample.cs#radialgradient1csharp)]  
  
 L'illustration suivante montre le dégradé créé dans l'exemple précédent.  Les points de dégradé du pinceau sont mis en surbrillance.  Notez que, même si les résultats sont différents, les points de dégradé de cet exemple sont identiques aux points de dégradé des précédents exemples de pinceau à dégradé linéaire.  
  
 ![Arrêts du dégradé dans un dégradé radial](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-4gradientstops-rg.png "wcpsdk\_graphicsmm\_4gradientstops\_rg")  
  
 <xref:System.Windows.Media.RadialGradientBrush.GradientOrigin%2A> spécifie le point de départ de l'axe de dégradé d'un pinceau à dégradé radial.  L'axe de dégradé rayonne de l'origine du dégradé vers le cercle du dégradé.  Le cercle de dégradé d'un pinceau est défini par ses propriétés <xref:System.Windows.Media.RadialGradientBrush.Center%2A>, <xref:System.Windows.Media.RadialGradientBrush.RadiusX%2A> et <xref:System.Windows.Media.RadialGradientBrush.RadiusY%2A>.  
  
 L'illustration suivante montre plusieurs dégradés radiaux dont les paramètres <xref:System.Windows.Media.RadialGradientBrush.GradientOrigin%2A>, <xref:System.Windows.Media.RadialGradientBrush.Center%2A>, <xref:System.Windows.Media.RadialGradientBrush.RadiusX%2A> et <xref:System.Windows.Media.RadialGradientBrush.RadiusY%2A> sont différents.  
  
 ![Paramètres de RadialGradientBrush](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-originscirclesandradii.png "wcpsdk\_graphicsmm\_originscirclesandradii")  
Des objets RadialGradientBrush de paramètres GradientOrigin, Center, RadiusX et RadiusY différents.  
  
<a name="specifyinggradientcolors"></a>   
## Spécification de points de dégradé transparents ou partiellement transparents  
 Les points de dégradé ne fournissant pas de propriété d'opacité, vous devez spécifier le canal alpha des couleurs à l'aide de la notation hexadécimale [!INCLUDE[TLA#tla_argb](../../../../includes/tlasharptla-argb-md.md)] dans le balisage ou utiliser la méthode <xref:System.Windows.Media.Color.FromScRgb%2A?displayProperty=fullName> pour créer des points de dégradé transparents ou partiellement transparents.  Les sections suivantes expliquent comment créer des points de dégradé partiellement transparents en [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] et dans du code.  Pour plus d'informations sur le paramétrage de l'opacité du pinceau entier, consultez la section [Spécification de l'opacité d'un pinceau](#brushesAndOpacity).  
  
<a name="argbsyntax"></a>   
### Spécification de l'opacité de la couleur en « XAML »  
 En [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], vous utilisez la notation hexadécimale [!INCLUDE[TLA2#tla_argb](../../../../includes/tla2sharptla-argb-md.md)] pour spécifier l'opacité des couleurs individuelles.  La notation hexadécimale [!INCLUDE[TLA2#tla_argb](../../../../includes/tla2sharptla-argb-md.md)] utilise la syntaxe suivante :  
  
 `#`**aa** *rrvvbb*  
  
 Dans la ligne précédente, *aa* représente une valeur hexadécimale à deux chiffres utilisée pour spécifier l'opacité de la couleur.  *rr*, *vv* et *bb* représentent chacun une valeur hexadécimale à deux chiffres utilisée pour spécifier les quantités de rouge, de vert et de bleu dans la couleur.  Chaque chiffre hexadécimal peut avoir une valeur de 0 à 9 ou de A à F.  0 est la plus petite valeur et F est la plus grande.   Une valeur alpha 00 spécifie une couleur qui est totalement transparente, alors qu'une valeur alpha FF crée une couleur qui est totalement opaque.  Dans l'exemple suivant, la notation hexadécimale [!INCLUDE[TLA2#tla_argb](../../../../includes/tla2sharptla-argb-md.md)] est utilisée pour spécifier deux couleurs.  La première est partiellement transparente \(elle a une valeur alpha de x20\), tandis que la deuxième est complètement opaque.  
  
 [!code-xml[GradientBrushExamples_snip#TransparentGradientStopExample1XAML](../../../../samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/GradientStopsExample.xaml#transparentgradientstopexample1xaml)]  
  
<a name="fromscrgbsyntax"></a>   
### Spécification de l'opacité de la couleur dans du code  
 Lorsque vous utilisez du code, la méthode statique <xref:System.Windows.Media.Color.FromArgb%2A> vous permet de spécifier une valeur alpha lorsque vous créez une couleur.  La méthode prend quatre paramètres de type <xref:System.Byte>.  Le premier paramètre spécifie le canal alpha de la couleur ; les trois autres paramètres spécifient les valeurs du rouge, du vert et du bleu de la couleur.  Chaque valeur doit être comprise entre 0 et 255 inclus.  Une valeur alpha de 0 spécifie que la couleur est totalement transparente, tandis qu'une valeur de 255 spécifie que la couleur est totalement opaque.  Dans l'exemple suivant, la méthode <xref:System.Windows.Media.Color.FromArgb%2A> est utilisée pour produire deux couleurs.  La première couleur est partiellement transparente \(sa valeur alpha est 32\), tandis que la deuxième est complètement opaque.  
  
 [!code-csharp[GradientBrushExamples_snip#TransparentGradientStopExample1CSharp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/GradientStopsExample.cs#transparentgradientstopexample1csharp)]  
  
 Vous pouvez également utiliser la méthode <xref:System.Windows.Media.Color.FromScRgb%2A>, qui vous permet d'utiliser des valeurs ScRVB pour créer une couleur.  
  
<a name="otherbrushes"></a>   
## Peinture avec des objets d'image, de dessin, de modèle et visuels  
 Les classes <xref:System.Windows.Media.ImageBrush>, <xref:System.Windows.Media.DrawingBrush> et <xref:System.Windows.Media.VisualBrush> vous permettent de peindre une zone avec des objets d'image, de dessin ou visuels.  Pour plus d'informations sur la peinture avec des objets d'image, de dessin et de modèle, consultez [Peinture avec des objets d'image, de dessin et visuels](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md).  
  
## Voir aussi  
 <xref:System.Windows.Media.Brush>   
 <xref:System.Windows.Media.SolidColorBrush>   
 <xref:System.Windows.Media.LinearGradientBrush>   
 <xref:System.Windows.Media.RadialGradientBrush>   
 [Peinture avec des objets d'image, de dessin et visuels](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)   
 [Vue d'ensemble des transformations du pinceau](../../../../docs/framework/wpf/graphics-multimedia/brush-transformation-overview.md)   
 [Couches de rendu graphiques](../../../../docs/framework/wpf/advanced/graphics-rendering-tiers.md)