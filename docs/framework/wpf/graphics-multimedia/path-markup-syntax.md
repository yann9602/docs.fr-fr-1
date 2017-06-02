---
title: "Syntaxe XAML pour les trac&#233;s | Microsoft Docs"
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
  - "PathGeometry (classe)"
  - "utilisation d'attributs en XAML"
  - "Utilisation d’attributs XAML"
  - "classes, PathGeometry"
  - "graphiques, PathGeometry (classe)"
  - "Utilisation d’éléments objet XAML"
ms.assetid: b8586241-a02d-486e-9223-e1e98e047f41
caps.latest.revision: 22
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 22
---
# Syntaxe XAML pour les trac&#233;s
Les tracés sont abordés dans [Shapes and Basic Drawing in WPF Overview](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md) et [vue d’ensemble de la géométrie](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md), toutefois, cette rubrique décrit en détail le mini langage puissant et plus complexe, vous pouvez utiliser pour spécifier des géométries de tracés de manière plus compacte en [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].  
  
 Cette rubrique contient les sections suivantes.  
  
<a name="autoTopLevelSectionsOUTLINE0"></a>   
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Conditions préalables  
 Pour comprendre cette rubrique, vous devez être familiarisé avec les fonctionnalités de base de <xref:System.Windows.Media.Geometry> objets. Pour plus d’informations, consultez la [Geometry Overview](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md).  
  
<a name="abouthisdocument"></a>   
## <a name="streamgeometry-and-pathfigurecollection-mini-languages"></a>StreamGeometry et PathFigureCollection Mini-langues  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]fournit deux classes qui fournissent des mini-langages permettant de décrire des tracés géométriques : <xref:System.Windows.Media.StreamGeometry> et <xref:System.Windows.Media.PathFigureCollection>.  
  
-   Vous utilisez la <xref:System.Windows.Media.StreamGeometry> mini langage lors de la définition d’une propriété de type <xref:System.Windows.Media.Geometry>, telles que la <xref:System.Windows.UIElement.Clip%2A> propriété d’un <xref:System.Windows.UIElement> ou <xref:System.Windows.Shapes.Path.Data%2A> propriété d’un <xref:System.Windows.Shapes.Path> élément. L’exemple suivant utilise la syntaxe d’attribut pour créer un <xref:System.Windows.Media.StreamGeometry>.  
  
     [!code-xml[GeometrySample_snip_XAML#GraphicsMMStreamGeometryAttributeSyntaxInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample_snip_XAML/CS/MiniLanguageExample.xaml#graphicsmmstreamgeometryattributesyntaxinline)]  
  
-   Vous utilisez la <xref:System.Windows.Media.PathFigureCollection> mini langage lors de la définition la <xref:System.Windows.Media.PathGeometry.Figures%2A> propriété d’un <xref:System.Windows.Media.PathGeometry>. L’exemple suivant utilise une syntaxe d’attribut pour créer un <xref:System.Windows.Media.PathFigureCollection> pour un <xref:System.Windows.Media.PathGeometry>.  
  
     [!code-xml[GeometrySample_snip_XAML#GraphicsMMPathFigureCollectionAttributeSyntaxInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample_snip_XAML/CS/MiniLanguageExample.xaml#graphicsmmpathfigurecollectionattributesyntaxinline)]  
  
 Comme vous pouvez le constater dans les exemples précédents, les deux langages de mini sont très similaires. Il est toujours possible d’utiliser un <xref:System.Windows.Media.PathGeometry> dans tous les cas où vous pouvez utiliser un <xref:System.Windows.Media.StreamGeometry>; c’est le cas quel modèle dois-je utiliser ? Utilisez un <xref:System.Windows.Media.StreamGeometry> lorsque vous n’avez pas besoin de modifier le chemin d’accès après sa création, utilisez un <xref:System.Windows.Media.PathGeometry> si vous n’avez pas besoin de modifier le chemin d’accès.  
  
 Pour plus d’informations sur les différences entre <xref:System.Windows.Media.PathGeometry> et <xref:System.Windows.Media.StreamGeometry> , voir la [Geometry Overview](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md).  
  
### <a name="a-note-about-white-space"></a>Remarque à propos des espaces blancs  
 Par souci de concision, un espace est indiqué dans les sections de syntaxe qui suivent, mais plusieurs espaces seraient acceptables partout où un espace unique est affiché.  
  
 Deux nombres est inutile d’être séparées par une virgule ou un espace blanc, mais cela n’est possible lorsque la chaîne résultante est ambiguë. Par exemple, `2..3` représente deux nombres : « 2 ». Et «.&3; ». De même, `2-3` est « 2 » et « -3 ». Les espaces ne sont pas requis avant ou après les commandes.  
  
### <a name="syntax"></a>Syntaxe  
 Le [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] attribut syntaxe d’utilisation pour un <xref:System.Windows.Media.StreamGeometry> est composé de facultatif <xref:System.Windows.Media.FillRule> valeur et un ou plusieurs descriptions de figure.  
  
|Utilisation d’attributs XAML pour StreamGeometry|  
|-----------------------------------------|  
|`<`*object* *property* `="`[                                         `fillRule`]                                          `figureDescription`[                                         `figureDescription`]*`" ... />`|  
  
 Le [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] attribut syntaxe d’utilisation pour un <xref:System.Windows.Media.PathFigureCollection> se compose d’une ou plusieurs descriptions de figure.  
  
|Utilisation d’attributs XAML de PathFigureCollection|  
|-----------------------------------------------|  
|`<`*object* *property* `="` `figureDescription`[                                         `figureDescription`]*`" ... />`|  
  
|Terme|Description|  
|----------|-----------------|  
|*fillRule*|<xref:System.Windows.Media.FillRule?displayProperty=fullName><br /><br /> Spécifie si les <xref:System.Windows.Media.StreamGeometry> utilise le <xref:System.Windows.Media.FillRule> ou <xref:System.Windows.Media.FillRule><xref:System.Windows.Media.PathGeometry.FillRule%2A>.<br /><br /> -   `F0`Spécifie le <xref:System.Windows.Media.FillRule> règle de remplissage.<br />-   `F1`Spécifie le <xref:System.Windows.Media.FillRule> règle de remplissage.<br /><br /> Si vous omettez cette commande, le sous-tracé utilise le comportement par défaut, qui est <xref:System.Windows.Media.FillRule>. Si vous spécifiez cette commande, vous devez tout d’abord le placer.|  
|*figureDescription*|Figure composée d’une commande de déplacement, dessiner des commandes et commande facultative.<br /><br /> `moveCommand` `drawCommands`  `[` `closeCommand` `]`|  
|*moveCommand*|Une commande de déplacement qui spécifie le point de départ de la figure. Consultez le [commande Déplacer](#themovecommand) section.|  
|*drawCommands*|Une ou plusieurs commandes de dessin qui décrivent le contenu de la figure. Consultez le [commandes de dessin](#drawcommands) section.|  
|*closeCommand*|Commande facultative qui ferme la figure. Consultez le [commande Fermer](#closecommand) section.|  
  
<a name="themovecommand"></a>   
## <a name="move-command"></a>Commande de déplacement  
 Spécifie le point de départ d’une nouvelle figure.  
  
|Syntaxe|  
|------------|  
|`M`*startPoint*<br /><br /> ou<br /><br /> `m`*startPoint*|  
  
|Terme|Description|  
|----------|-----------------|  
|*point de départ*|<xref:System.Windows.Point?displayProperty=fullName><br /><br /> Le point de départ d’une nouvelle figure.|  
  
 Majuscules `M` indique que `startPoint` est une valeur absolue ; une minuscule `m` indique que `startPoint` est un décalage par rapport au point précédent, ou (0,0) s’il n’existe. Si vous énumérez plusieurs points après la commande de déplacement, une ligne est tracée entre ces points bien que vous avez spécifié la ligne de commande.  
  
<a name="drawcommands"></a>   
## <a name="draw-commands"></a>Commandes de dessin  
 Une commande de dessin peut se composer de plusieurs commandes de forme. Les commandes de forme suivantes sont disponibles : ligne, ligne horizontale, verticale, courbe de Bézier cubique, courbe de Bézier quadratique, lisse courbe de Bézier cubique, courbe de Bézier quadratique lisse et arc elliptique.  
  
 Vous entrez chaque commande en utilisant une majuscule ou une minuscule : lettres majuscules indiquent des valeurs absolues et des lettres minuscules indiquent des valeurs relatives : les points de contrôle pour ce segment sont par rapport au point de fin de l’exemple précédent. Lorsque vous entrez plusieurs commandes du même type, vous pouvez omettre l’entrée de commande en double. par exemple, `L 100,200 300,400` équivaut à `L 100,200 L 300,400`. Le tableau suivant décrit les **déplacer** et **dessiner** commandes.  
  
### <a name="line-command"></a>Ligne de commande  
 Crée une ligne droite entre le point actuel et le point de terminaison spécifié.                           `l 20 30`et `L 20,30` sont des exemples de valide **ligne** commandes.  
  
|Syntaxe|  
|------------|  
|`L`*point de terminaison*<br /><br /> ou<br /><br /> `l`*point de terminaison*|  
  
|Terme|Description|  
|----------|-----------------|  
|*point de terminaison*|<xref:System.Windows.Point?displayProperty=fullName><br /><br /> Extrémité de la ligne.|  
  
### <a name="horizontal-line-command"></a>Commande de ligne horizontale  
 Crée une ligne horizontale entre le point actuel et la coordonnée x spécifiée.                          `H 90`est un exemple de commande de ligne horizontale valide.  
  
|Syntaxe|  
|------------|  
|`H`  *x*<br /><br /> ou<br /><br /> `h`  *x*|  
  
|Terme|Description|  
|----------|-----------------|  
|*x*|<xref:System.Double?displayProperty=fullName><br /><br /> Coordonnée x du point de terminaison de la ligne.|  
  
### <a name="vertical-line-command"></a>Commande de ligne verticale  
 Crée une ligne verticale entre le point actuel et la coordonnée y spécifiée.                          `v 90`est un exemple de commande de ligne verticale valide.  
  
|Syntaxe|  
|------------|  
|`V`  *y*<br /><br /> ou<br /><br /> `v`  *y*|  
  
|Terme|Description|  
|----------|-----------------|  
|*y*|<xref:System.Double?displayProperty=fullName><br /><br /> Coordonnée y du point de terminaison de la ligne.|  
  
### <a name="cubic-bezier-curve-command"></a>Commande de courbe de Bézier cubique  
 Crée une courbe de Bézier cubique entre le point actuel et le point de terminaison spécifié à l’aide de deux points de contrôle spécifiés ( `controlPoint`1 et `controlPoint`2).                          `C 100,200 200,400 300,200`est un exemple de commande de courbe valide.  
  
|Syntaxe|  
|------------|  
|`C` `controlPoint`1`controlPoint`2`endPoint`<br /><br /> ou<br /><br /> `c` `controlPoint`1`controlPoint`2`endPoint`|  
  
|Terme|Description|  
|----------|-----------------|  
|`controlPoint`1|<xref:System.Windows.Point?displayProperty=fullName><br /><br /> Le premier point de contrôle de la courbe, qui détermine la tangente de début de la courbe.|  
|`controlPoint`2|<xref:System.Windows.Point?displayProperty=fullName><br /><br /> Le deuxième point de contrôle de la courbe, qui détermine la tangente de fin de la courbe.|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=fullName><br /><br /> Point vers lequel la courbe est dessinée.|  
  
### <a name="quadratic-bezier-curve-command"></a>Commande de courbe de Bézier quadratique  
 Crée une courbe de Bézier quadratique entre le point actuel et le point de terminaison spécifié à l’aide du point de contrôle spécifié ( `controlPoint`).                          `q 100,200 300,200`est un exemple de commande de courbe de Bézier quadratique valide.  
  
|Syntaxe|  
|------------|  
|`Q` `controlPoint` `endPoint`<br /><br /> ou<br /><br /> `q` `controlPoint` `endPoint`|  
  
|Terme|Description|  
|----------|-----------------|  
|`controlPoint`|<xref:System.Windows.Point?displayProperty=fullName><br /><br /> Le point de contrôle de la courbe, qui détermine le début et fin tangentes de la courbe.|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=fullName><br /><br /> Point vers lequel la courbe est dessinée.|  
  
### <a name="smooth-cubic-bezier-curve-command"></a>Courbe de Bézier cubique lisse commande  
 Crée une courbe de Bézier cubique entre le point actuel et le point de terminaison spécifié. Le premier point de contrôle est par défaut la réflexion du deuxième point de contrôle de la commande précédente par rapport au point actuel. S’il n’existe pas de commande précédente, ou si la commande précédente n’était pas une commande de courbe de Bézier cubique ou une commande de courbe de Bézier cubique lissée, supposons que le premier point de contrôle ne coïncide avec le point actuel. Le deuxième point de contrôle, le point de contrôle pour la fin de la courbe, est spécifié par `controlPoint`2. Par exemple, `S 100,200 200,300` est une commande de courbe de Bézier cubique lissée correcte.  
  
|Syntaxe|  
|------------|  
|`S` `controlPoint`2`endPoint`<br /><br /> ou<br /><br /> `s` `controlPoint`2`endPoint`|  
  
|Terme|Description|  
|----------|-----------------|  
|`controlPoint`2|<xref:System.Windows.Point?displayProperty=fullName><br /><br /> Le point de contrôle de la courbe, qui détermine la tangente de fin de la courbe.|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=fullName><br /><br /> Point vers lequel la courbe est dessinée.|  
  
### <a name="smooth-quadratic-bezier-curve-command"></a>Courbe de Bézier quadratique lisse commande  
 Crée une courbe de Bézier quadratique entre le point actuel et le point de terminaison spécifié. Le point de contrôle est par défaut la réflexion du point de contrôle de la commande précédente par rapport au point actuel. S’il n’existe pas de commande précédente, ou si la commande précédente n’était pas une commande de courbe de Bézier quadratique ou une commande de courbe de Bézier quadratique lisse, le point de contrôle ne coïncide avec le point actuel.  
  
|Syntaxe|  
|------------|  
|`T` `controlPoint` `endPoint`<br /><br /> ou<br /><br /> `t` `controlPoint` `endPoint`|  
  
|Terme|Description|  
|----------|-----------------|  
|`controlPoint`|<xref:System.Windows.Point?displayProperty=fullName><br /><br /> Le point de contrôle de la courbe, qui détermine le début et la tangente de la courbe.|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=fullName><br /><br /> Point vers lequel la courbe est dessinée.|  
  
### <a name="elliptical-arc-command"></a>Commande d’Arc elliptique  
 Crée un arc elliptique entre le point actuel et le point de terminaison spécifié.  
  
|Syntaxe|  
|------------|  
|`A` `size` `rotationAngle` `isLargeArcFlag` `sweepDirectionFlag` `endPoint`<br /><br /> ou<br /><br /> `a` `size` `rotationAngle` `isLargeArcFlag` `sweepDirectionFlag` `endPoint`|  
  
|Terme|Description|  
|----------|-----------------|  
|`size`|<xref:System.Windows.Size?displayProperty=fullName><br /><br /> Rayons X et Y de l’arc.|  
|`rotationAngle`|<xref:System.Double?displayProperty=fullName><br /><br /> La rotation de l’ellipse, en degrés.|  
|`isLargeArcFlag`|La valeur 1 si l’angle de l’arc doit être 180 degrés ou plus ; dans le cas contraire, la valeur 0.|  
|`sweepDirectionFlag`|La valeur 1 si l’arc est dessiné dans une direction d’angle positif ; dans le cas contraire, la valeur 0.|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=fullName><br /><br /> Point où l’arc est dessiné.|  
  
<a name="closecommand"></a>   
## <a name="the-close-command"></a>La commande Fermer  
 Termine la figure en cours et crée une ligne qui relie le point actuel au point de départ de la figure. Cette commande crée une jonction de ligne (angle) entre le dernier segment et le premier segment de la figure.  
  
|Syntaxe|  
|------------|  
|`Z`<br /><br /> ou<br /><br /> `z`|  
  
<a name="pointsyntax"></a>   
## <a name="point-syntax"></a>Syntaxe de point  
 Décrit les coordonnées x et y d’un point.  
  
|Syntaxe|  
|------------|  
|`x` `,` `y`<br /><br /> ou<br /><br /> `x` `y`|  
  
|Terme|Description|  
|----------|-----------------|  
|`x`|<xref:System.Double?displayProperty=fullName><br /><br /> Coordonnée x du point.|  
|`y`|<xref:System.Double?displayProperty=fullName><br /><br /> Coordonnée y du point.|  
  
<a name="specialvalues"></a>   
## <a name="special-values"></a>Valeurs spéciales  
 Au lieu d’une valeur numérique standard, vous pouvez également utiliser des valeurs spéciales suivantes. Ces valeurs respectent la casse.  
  
 Infini  
 Représente <xref:System.Double.PositiveInfinity?displayProperty=fullName>.  
  
 -Infini  
 Représente <xref:System.Double.NegativeInfinity?displayProperty=fullName>.  
  
 NaN  
 Représente <xref:System.Double.NaN?displayProperty=fullName>.  
  
 Vous pouvez également utiliser la notation scientifique. Par exemple, `+1.e17` est une valeur valide.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Shapes.Path>   
 <xref:System.Windows.Media.StreamGeometry>   
 <xref:System.Windows.Media.PathGeometry>   
 <xref:System.Windows.Media.PathFigureCollection>   
 [Formes et dessins de base dans la vue d’ensemble WPF](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)   
 [Vue d’ensemble de Geometry](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)   
 [Rubriques "Comment"](../../../../docs/framework/wpf/graphics-multimedia/geometries-how-to-topics.md)