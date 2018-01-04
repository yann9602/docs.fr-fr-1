---
title: "Syntaxe XAML pour les tracés"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- attribute usage in XAML [WPF]
- XAML [WPF], attribute usage
- graphics [WPF], PathGeometry class
- XAML [WPF], object element usage
ms.assetid: b8586241-a02d-486e-9223-e1e98e047f41
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9cd8f9b14f114060ebec8e336c1212d61fa19c83
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="path-markup-syntax"></a>Syntaxe XAML pour les tracés
Chemins d’accès sont décrites dans [formes et dessins de base dans WPF Overview](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md) et [vue d’ensemble de Geometry](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md), toutefois, cette rubrique décrit en détail la mini-langue puissante et plus complexe, vous pouvez utiliser pour spécifier le chemin d’accès les géométries de manière plus compacte en [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Prérequis  
 Pour comprendre cette rubrique, vous devez être familiarisé avec les fonctionnalités de base de <xref:System.Windows.Media.Geometry> objets. Pour plus d’informations, consultez la [vue d’ensemble de Geometry](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md).  
  
<a name="abouthisdocument"></a>   
## <a name="streamgeometry-and-pathfigurecollection-mini-languages"></a>Mini langages StreamGeometry et PathFigureCollection  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]fournit deux classes qui fournissent des mini-langages pour décrire les chemins d’accès géométriques : <xref:System.Windows.Media.StreamGeometry> et <xref:System.Windows.Media.PathFigureCollection>.  
  
-   Vous utilisez la <xref:System.Windows.Media.StreamGeometry> mini langage lors de la définition d’une propriété de type <xref:System.Windows.Media.Geometry>, telles que la <xref:System.Windows.UIElement.Clip%2A> propriété d’un <xref:System.Windows.UIElement> ou <xref:System.Windows.Shapes.Path.Data%2A> propriété d’un <xref:System.Windows.Shapes.Path> élément. L’exemple suivant utilise la syntaxe d’attribut pour créer un <xref:System.Windows.Media.StreamGeometry>.  
  
     [!code-xaml[GeometrySample_snip_XAML#GraphicsMMStreamGeometryAttributeSyntaxInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample_snip_XAML/CS/MiniLanguageExample.xaml#graphicsmmstreamgeometryattributesyntaxinline)]  
  
-   Vous utilisez la <xref:System.Windows.Media.PathFigureCollection> mini langage lors de la définition la <xref:System.Windows.Media.PathGeometry.Figures%2A> propriété d’un <xref:System.Windows.Media.PathGeometry>. L’exemple suivant utilise une syntaxe d’attribut pour créer un <xref:System.Windows.Media.PathFigureCollection> pour un <xref:System.Windows.Media.PathGeometry>.  
  
     [!code-xaml[GeometrySample_snip_XAML#GraphicsMMPathFigureCollectionAttributeSyntaxInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample_snip_XAML/CS/MiniLanguageExample.xaml#graphicsmmpathfigurecollectionattributesyntaxinline)]  
  
 Comme vous pouvez le constater dans les exemples précédents, les deux mini langages sont très similaires. Il est toujours possible d’utiliser un <xref:System.Windows.Media.PathGeometry> dans toute situation où vous pouvez utiliser un <xref:System.Windows.Media.StreamGeometry>; c’est le cas l’application que vous devez utiliser ? Utiliser un <xref:System.Windows.Media.StreamGeometry> lorsque vous n’avez pas besoin de modifier le chemin d’accès après sa création ; utilisez un <xref:System.Windows.Media.PathGeometry> si vous n’avez pas besoin de modifier le chemin d’accès.  
  
 Pour plus d’informations sur les différences entre <xref:System.Windows.Media.PathGeometry> et <xref:System.Windows.Media.StreamGeometry> , consultez la [vue d’ensemble de Geometry](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md).  
  
### <a name="a-note-about-white-space"></a>Remarque à propos des espaces blancs  
 Par souci de concision, un seul espace est indiqué dans les sections de syntaxe qui suivent, mais plusieurs espaces sont également acceptables partout où un seul espace est affiché.  
  
 Deux nombres n’ont pas réellement besoin d’être séparés par une virgule ou un espace blanc, mais cela peut être fait lorsque la chaîne résultante est ambiguë. Par exemple, `2..3` est en fait deux nombres : « 2 ». et « .3 ». De même, `2-3` est « 2 » et « -3 ». Les espaces ne sont pas requis avant ou après les commandes.  
  
### <a name="syntax"></a>Syntaxe  
 Le [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] attribut syntaxe d’utilisation pour un <xref:System.Windows.Media.StreamGeometry> est composé d’une option <xref:System.Windows.Media.FillRule> valeur et un ou plusieurs descriptions de figure.  
  
|Utilisation d’attribut XAML pour StreamGeometry|  
|-----------------------------------------|  
|`<`*objet* *propriété* `="`[ `fillRule`] `figureDescription`[ `figureDescription`] *`" ... />`|  
  
 Le [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] attribut syntaxe d’utilisation pour un <xref:System.Windows.Media.PathFigureCollection> est composé d’une ou plusieurs descriptions de figure.  
  
|Utilisation d’attributs XAML pour PathFigureCollection|  
|-----------------------------------------------|  
|`<`*objet* *propriété* `="` `figureDescription`[ `figureDescription`] *`" ... />`|  
  
|Terme|Description|  
|----------|-----------------|  
|*fillRule*|<xref:System.Windows.Media.FillRule?displayProperty=nameWithType><br /><br /> Spécifie si le <xref:System.Windows.Media.StreamGeometry> utilise le <xref:System.Windows.Media.FillRule.EvenOdd> ou <xref:System.Windows.Media.FillRule.Nonzero> <xref:System.Windows.Media.PathGeometry.FillRule%2A>.<br /><br /> -   `F0`Spécifie la <xref:System.Windows.Media.FillRule.EvenOdd> règle de remplissage.<br />-   `F1`Spécifie la <xref:System.Windows.Media.FillRule.Nonzero> règle de remplissage.<br /><br /> Si vous omettez cette commande, le sous-tracé utilise le comportement par défaut, qui est <xref:System.Windows.Media.FillRule.EvenOdd>. Si vous spécifiez cette commande, vous devez la placer en premier.|  
|*figureDescription*|Une figure composée d’une commande move, de commandes draw et d’une commande close facultative.<br /><br /> `moveCommand` `drawCommands`  `[` `closeCommand` `]`|  
|*moveCommand*|Une commande move qui spécifie le point de départ de la figure. Consultez le [commande Déplacer](#themovecommand) section.|  
|*drawCommands*|Une ou plusieurs commandes draw qui décrivent le contenu de la figure. Consultez le [commandes de dessin](#drawcommands) section.|  
|*closeCommand*|Une commande close facultative qui ferme la figure. Consultez le [commande Fermer](#closecommand) section.|  
  
<a name="themovecommand"></a>   
## <a name="move-command"></a>Commande move  
 Spécifie le point de départ d’une nouvelle figure.  
  
|Syntaxe|  
|------------|  
|`M` *startPoint*<br /><br /> ou<br /><br /> `m` *startPoint*|  
  
|Terme|Description|  
|----------|-----------------|  
|*startPoint*|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Le point de départ d’une nouvelle figure.|  
  
 Majuscules `M` indique que `startPoint` est une valeur absolue ; une minuscule `m` indique que `startPoint` est un décalage par rapport au point précédent, ou (0,0) s’il n’en existe aucun. Si vous énumérez plusieurs points après la commande move, une ligne est tracée entre ces points, même si vous avez spécifié la commande line.  
  
<a name="drawcommands"></a>   
## <a name="draw-commands"></a>Commandes draw  
 Une commande draw peut se composer de plusieurs commandes shape. Les commandes shape suivantes sont disponibles : line, horizontal line, vertical line, cubic Bezier curve, quadratic Bezier curve, smooth cubic Bezier curve, smooth quadratic Bezier curve et elliptical arc.  
  
 Vous entrez chaque commande en utilisant une majuscule ou une minuscule : les majuscules indiquent des valeurs absolues et les minuscules indiquent des valeurs relatives : les points de contrôle pour ce segment sont relatifs au point de fin de l’exemple précédent. Lorsque vous entrez plusieurs commandes du même type, vous pouvez omettre l’entrée de commande en double. par exemple, `L 100,200 300,400` équivaut à `L 100,200 L 300,400`. Le tableau suivant décrit les **déplacer** et **dessiner** commandes.  
  
### <a name="line-command"></a>Commande line  
 Crée une ligne droite entre le point actuel et le point de fin spécifié. `l 20 30`et `L 20,30` sont des exemples de valide **ligne** commandes.  
  
|Syntaxe|  
|------------|  
|`L` *endPoint*<br /><br /> ou<br /><br /> `l` *endPoint*|  
  
|Terme|Description|  
|----------|-----------------|  
|*endPoint*|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Extrémité de la ligne.|  

Majuscules `L` indique que `endPoint` est une valeur absolue ; une minuscule `l` indique que `endPoint` est un décalage par rapport au point précédent, ou (0,0) s’il n’en existe aucun.

### <a name="horizontal-line-command"></a>Commande Horizontal Line  
 Crée une ligne horizontale entre le point actuel et la coordonnée x spécifiée. `H 90` est un exemple de commande horizontal line valide.

  
|Syntaxe|  
|------------|  
|`H`  *x*<br /><br /> ou<br /><br /> `h`  *x*|  
  
|Terme|Description|  
|----------|-----------------|  
|*x*|<xref:System.Double?displayProperty=nameWithType><br /><br /> La coordonnée x du point de fin de la ligne.|  
  
Majuscules `H` indique que `x` est une valeur absolue ; une minuscule `h` indique que `x` est un décalage par rapport au point précédent, ou (0,0) s’il n’en existe aucun.
  
### <a name="vertical-line-command"></a>Commande Vertical Line  
 Crée une ligne verticale entre le point actuel et la coordonnée y spécifiée. `v 90` est un exemple de commande vertical line valide.

  
|Syntaxe|  
|------------|  
|`V`  *y*<br /><br /> ou<br /><br /> `v`  *y*|  
  
|Terme|Description|  
|----------|-----------------|  
|*y*|<xref:System.Double?displayProperty=nameWithType><br /><br /> La coordonnée y du point de fin de la ligne.|  

Majuscules `V` indique que `y` est une valeur absolue ; une minuscule `v` indique que `y` est un décalage par rapport au point précédent, ou (0,0) s’il n’en existe aucun.  
    
### <a name="cubic-bezier-curve-command"></a>Commande Cubic Bezier Curve  
 Crée une courbe de Bézier cubique entre le point actuel et le point de terminaison spécifié à l’aide de deux points de contrôle spécifiés (`controlPoint`1 et `controlPoint`2). `C 100,200 200,400 300,200` est un exemple de commande curve valide.  
  
|Syntaxe|  
|------------|  
|`C` `controlPoint`1`controlPoint`2`endPoint`<br /><br /> ou<br /><br /> `c` `controlPoint`1`controlPoint`2`endPoint`|  
  
|Terme|Description|  
|----------|-----------------|  
|`controlPoint`1|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Le premier point de contrôle de la courbe, qui détermine la tangente de départ de la courbe.|  
|`controlPoint`2|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Le deuxième point de contrôle de la courbe, qui détermine la tangente de fin de la courbe.|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Point vers lequel la courbe est dessinée.|  
  
### <a name="quadratic-bezier-curve-command"></a>Commande Quadratic Bezier Curve  
 Crée une courbe de Bézier quadratique entre le point actuel et le point de terminaison spécifié à l’aide du point de contrôle spécifié (`controlPoint`). `q 100,200 300,200` est un exemple de commande quadratic Bezier curve valide.  
  
|Syntaxe|  
|------------|  
|`Q` `controlPoint` `endPoint`<br /><br /> ou<br /><br /> `q` `controlPoint` `endPoint`|  
  
|Terme|Description|  
|----------|-----------------|  
|`controlPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Le point de contrôle de la courbe, qui détermine la tangente de départ et la tangente de fin de la courbe.|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Point vers lequel la courbe est dessinée.|  
  
### <a name="smooth-cubic-bezier-curve-command"></a>Commande Smooth cubic Bezier curve  
 Crée une courbe de Bézier cubique lissée entre le point actuel et le point de fin spécifié. Le premier point de contrôle est supposé être la réflexion du deuxième point de contrôle de la commande précédente par rapport au point actuel. S’il n’existe pas de commande précédente, ou si la commande précédente n’était pas une commande cubic Bezier curve ni une commande smooth cubic Bezier curve, imaginez que le premier point de contrôle coïncide avec le point actuel. Le deuxième point de contrôle, le point de contrôle pour la fin de la courbe, est spécifié par `controlPoint`2. Par exemple, `S 100,200 200,300` est une commande de courbe de Bézier cubique lissée correcte.  
  
|Syntaxe|  
|------------|  
|`S` `controlPoint`2`endPoint`<br /><br /> ou<br /><br /> `s` `controlPoint`2`endPoint`|  
  
|Terme|Description|  
|----------|-----------------|  
|`controlPoint`2|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Le point de contrôle de la courbe, qui détermine la tangente de fin de la courbe.|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Point vers lequel la courbe est dessinée.|  
  
### <a name="smooth-quadratic-bezier-curve-command"></a>Commande Smooth quadratic Bezier curve  
 Crée une courbe de Bézier quadratique lissée entre le point actuel et le point de fin spécifié. Le point de contrôle est supposé être la réflexion du point de contrôle de la commande précédente par rapport au point actuel. S’il n’existe pas de commande précédente, ou si la commande précédente n’était pas une commande quadratic Bezier curve ni une commande smooth quadratic Bezier curve, le point de contrôle coïncide avec le point actuel.  
  
|Syntaxe|  
|------------|  
|`T` `controlPoint` `endPoint`<br /><br /> ou<br /><br /> `t` `controlPoint` `endPoint`|  
  
|Terme|Description|  
|----------|-----------------|  
|`controlPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Le point de contrôle de la courbe, qui détermine la tangente de départ et de fin de la courbe.|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Point vers lequel la courbe est dessinée.|  
  
### <a name="elliptical-arc-command"></a>Commande Elliptical Arc  
 Crée un arc elliptique entre le point actuel et le point de fin spécifié.  
  
|Syntaxe|  
|------------|  
|`A` `size` `rotationAngle` `isLargeArcFlag` `sweepDirectionFlag` `endPoint`<br /><br /> ou<br /><br /> `a` `size` `rotationAngle` `isLargeArcFlag` `sweepDirectionFlag` `endPoint`|  
  
|Terme|Description|  
|----------|-----------------|  
|`size`|<xref:System.Windows.Size?displayProperty=nameWithType><br /><br /> Rayons X et Y de l’arc.|  
|`rotationAngle`|<xref:System.Double?displayProperty=nameWithType><br /><br /> La rotation de l’ellipse, en degrés.|  
|`isLargeArcFlag`|Défini sur 1 si l’angle de l’arc doit être de 180 degrés ou plus ; dans le cas contraire, défini sur 0.|  
|`sweepDirectionFlag`|Défini sur 1 si l’arc est dessiné dans une direction d’angle positif ; dans le cas contraire, défini sur 0.|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> Point où l’arc est dessiné.|  
  
<a name="closecommand"></a>   
## <a name="the-close-command"></a>Commande close  
 Termine la figure actuelle et crée une ligne qui relie le point actuel au point de départ de la figure. Cette commande crée une jonction de ligne (angle) entre le dernier segment et le premier segment de la figure.  
  
|Syntaxe|  
|------------|  
|`Z`<br /><br /> ou<br /><br /> `z`|  

<a name="pointsyntax"></a>   
## <a name="point-syntax"></a>Syntaxe de point  
 Décrit les coordonnées x et y d’un point où (0,0) est l’angle supérieur gauche.
  
|Syntaxe|  
|------------|  
|`x` `,` `y`<br /><br /> ou<br /><br /> `x` `y`|  
  
|Terme|Description|  
|----------|-----------------|  
|`x`|<xref:System.Double?displayProperty=nameWithType><br /><br /> Coordonnée X du point.|  
|`y`|<xref:System.Double?displayProperty=nameWithType><br /><br /> Coordonnée Y du point.|  
  
<a name="specialvalues"></a>   
## <a name="special-values"></a>Valeurs spéciales  
 Plutôt que d’utiliser une valeur numérique standard, vous pouvez opter pour les valeurs spéciales suivantes. Ces valeurs sont sensibles à la casse.  
  
 Infini  
 Représente <xref:System.Double.PositiveInfinity?displayProperty=nameWithType>.  
  
 -Infini  
 Représente <xref:System.Double.NegativeInfinity?displayProperty=nameWithType>.  
  
 NaN  
 Représente <xref:System.Double.NaN?displayProperty=nameWithType>.  
  
 Vous pouvez également utiliser la notation scientifique. Par exemple, `+1.e17` est une valeur valide.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Shapes.Path>  
 <xref:System.Windows.Media.StreamGeometry>  
 <xref:System.Windows.Media.PathGeometry>  
 <xref:System.Windows.Media.PathFigureCollection>  
 [Vue d’ensemble des formes et dessins de base dans WPF](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)  
 [Vue d’ensemble de Geometry](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)  
 [Rubriques de guide pratique](../../../../docs/framework/wpf/graphics-multimedia/geometries-how-to-topics.md)
