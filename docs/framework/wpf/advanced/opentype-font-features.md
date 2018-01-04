---
title: "Fonctionnalités des polices OpenType"
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
- fonts [WPF], OpenType
- typography [WPF], OpenType font technology
- OpenType font technology [WPF]
ms.assetid: 4061a9d1-fe8b-4921-9e17-18ec7d2e3ea2
caps.latest.revision: "38"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6344fed6cf480e3d3f91a559c99b79f438afa985
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="opentype-font-features"></a>Fonctionnalités des polices OpenType
Cette rubrique fournit une vue d’ensemble de quelques-unes des fonctionnalités clés de la technologie de police [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] dans [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  
  

  
<a name="overview"></a>   
## <a name="opentype-font-format"></a>Format des polices OpenType  
 Le format de police [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] est une extension du format de police [!INCLUDE[TLA#tla_truetype](../../../../includes/tlasharptla-truetype-md.md)], qui ajoute une prise en charge des données de police PostScript. Le format de police [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] a été développé conjointement par [!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)] et Adobe Corporation. Les polices [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] et les services du système d’exploitation qui prennent en charge les polices [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] offrent aux utilisateurs un moyen simple d’installer et d’utiliser des polices, que celles-ci contiennent des contours [!INCLUDE[TLA2#tla_truetype](../../../../includes/tla2sharptla-truetype-md.md)] ou des contours CFF (PostScript).  
  
 Le format de police [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] répond aux problèmes suivants que rencontrent les développeurs :  
  
-   Prise en charge multi-plateforme élargie.  
  
-   Meilleure prise en charge des jeux de caractères internationaux.  
  
-   Meilleure protection des données de police.  
  
-   Taille des fichiers plus petite permettant une distribution plus efficace des polices.  
  
-   Prise en charge élargie des contrôles typographiques avancés.  
  
> [!NOTE]
>  Le Kit de développement logiciel (SDK) Windows contient un jeu d’exemples de polices [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] que vous pouvez utiliser avec les applications [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. Ces polices offrent la plupart des fonctionnalités illustrées dans le reste de cette rubrique. Pour plus d’informations, consultez [Exemple de pack de polices OpenType](../../../../docs/framework/wpf/advanced/sample-opentype-font-pack.md).  
  
 Consultez la [spécification OpenType](http://go.microsoft.com/fwlink/?LinkId=96731) pour plus d’informations sur le format de police [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)].  
  
### <a name="advanced-typographic-extensions"></a>Extensions typographiques avancées  
 Les tableaux typographiques avancés (tableaux de disposition [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)]) étendent les fonctionnalités des polices avec des contours [!INCLUDE[TLA2#tla_truetype](../../../../includes/tla2sharptla-truetype-md.md)] ou CFF. Les polices de disposition [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] contiennent des informations supplémentaires qui étendent les fonctionnalités des polices pour une prise en charge de la typographie internationale de haute qualité. La plupart des polices [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] exposent uniquement une partie des fonctionnalités [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] disponibles. Les polices [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] offrent les fonctionnalités suivantes :  
  
-   Mappage riche entre les caractères et les glyphes qui prennent en charge les ligatures, les formes positionnelles, les alternatives et les substitutions de police.  
  
-   Prise en charge du positionnement à deux dimensions et de l’attachement de glyphes.  
  
-   Présence d’informations explicites de script et de langage dans la police, ce qui permet à une application de traitement de texte d’ajuster son comportement en conséquence.  
  
 Les tableaux de disposition [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] sont décrits plus en détail dans la section relative aux [tableaux de fichiers de police](http://www.microsoft.com/typography/otspec/otff.htm) de la spécification [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)].  
  
 Le reste de cette vue d’ensemble présente l’ampleur et la flexibilité de quelques-unes des visuellement intéressantes [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] les fonctionnalités qui sont exposées par les propriétés de la <xref:System.Windows.Documents.Typography> objet. Pour plus d’informations sur cet objet, consultez [Classe Typography](#typography_class).  
  
<a name="variants"></a>   
## <a name="variants"></a>Variantes  
 Les variantes servent à restituer différents styles typographiques, tels que les exposants et les indices.  
  
### <a name="superscripts-and-subscripts"></a>Exposants et indices  
 Le <xref:System.Windows.Documents.Typography.Variants%2A> propriété vous permet de définir des valeurs d’exposant et d’indice pour une [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] police.  
  
 Le texte suivant présente des exposants avec la police Palatino Linotype.  
  
 ![Texte utilisant des exposants OpenType](../../../../docs/framework/wpf/advanced/media/opentypefont14.gif "opentypefont14")  
Texte utilisant des exposants OpenType  
  
 Le balisage suivant montre comment définir des exposants pour la police Palatino Linotype, à l’aide des propriétés de la <xref:System.Windows.Documents.Typography> objet.  
  
 [!code-xaml[OpenTypeFontSamples#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#12)]  
  
 Le texte suivant présente des indices avec la police Palatino Linotype.  
  
 ![Texte utilisant des indices OpenType](../../../../docs/framework/wpf/advanced/media/opentypefont15.gif "opentypefont15")  
Texte utilisant des indices OpenType  
  
 Le balisage suivant montre comment définir des indices pour la police Palatino Linotype, à l’aide des propriétés de la <xref:System.Windows.Documents.Typography> objet.  
  
 [!code-xaml[OpenTypeFontSamples#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#13)]  
  
### <a name="decorative-uses-of-superscripts-and-subscripts"></a>Utilisations décoratives d’exposants et d’indices  
 Vous pouvez aussi utiliser des exposants et des indices pour créer des effets décoratifs de texte à casse mixte. Le texte suivant présente des exposants et des indices avec la police Palatino Linotype. Notez que les majuscules ne sont pas affectées.  
  
 ![Texte utilisant des exposants OpenType et indices](../../../../docs/framework/wpf/advanced/media/opentypefont16.gif "opentypefont16")  
Texte utilisant des exposants et des indices OpenType  
  
 Le balisage suivant montre comment définir des exposants et des indices pour une police, à l’aide des propriétés de la <xref:System.Windows.Documents.Typography> objet.  
  
 [!code-xaml[OpenTypeFontSamples#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#14)]  
  
<a name="capitals"></a>   
## <a name="capitals"></a>Majuscules  
 Les majuscules représentent un jeu de formes typographiques qui restituent le texte dans des glyphes de type majuscule. En règle générale, quand le texte est entièrement restitué en majuscules, l’espacement entre les lettres peut sembler trop serré et le poids et la proportion des lettres trop lourds. [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] prend en charge plusieurs formats de style pour les majuscules, à savoir les petites majuscules, les mini-majuscules, les caractères de titre et l’espacement des majuscules. Ces formats de style permettent de contrôler l’apparence des majuscules.  
  
 Le texte suivant présente des majuscules standard avec la police Pescadero, suivies de lettres de type « SmallCaps » et « AllSmallCaps ». Dans ce cas, la taille de police utilisée est identique pour les trois mots.  
  
 ![Texte utilisant des majuscules OpenType](../../../../docs/framework/wpf/advanced/media/opentypefont11.gif "opentypefont11")  
Texte utilisant des majuscules OpenType  
  
 Le balisage suivant montre comment définir des majuscules pour la police Pescadero, à l’aide des propriétés de la <xref:System.Windows.Documents.Typography> objet. Quand le format « SmallCaps » est utilisé, les majuscules de début sont ignorées.  
  
 [!code-xaml[OpenTypeFontSamples#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#9)]  
  
### <a name="titling-capitals"></a>Majuscules de titres  
 Le poids et les proportions des majuscules de titres ont été réduits pour leur conférer un aspect plus élégant que les majuscules normales. Les majuscules de titres sont généralement utilisées dans les titres avec des tailles de police supérieures. Le texte suivant présente des majuscules normales et des majuscules de titres avec la police Pescadero. Comme vous pouvez le constater, le plein est plus fin dans le texte de la deuxième ligne.  
  
 ![Texte utilisant des majuscules de titre de OpenType](../../../../docs/framework/wpf/advanced/media/opentypefont20.gif "OpenTypeFont20")  
Texte utilisant des majuscules de titres OpenType  
  
 Le balisage suivant montre comment définir des majuscules pour la police Pescadero, à l’aide des propriétés de la <xref:System.Windows.Documents.Typography> objet.  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet17](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#opentypefontsnippet17)]  
  
### <a name="capital-spacing"></a>Espacement des majuscules  
 L’espacement des majuscules est une fonctionnalité qui permet d’accroître l’espacement du texte quand celui-ci se compose uniquement de majuscules. Les majuscules sont généralement conçues pour se mêler aux minuscules. L’espacement employé entre une majuscule et une minuscule peut paraître trop serré quand toutes les lettres sont des majuscules. Le texte suivant présente l’espacement normal et l’espacement de majuscules avec la police Pescadero.  
  
 ![Texte à l’aide de l’espacement des majuscules OpenType](../../../../docs/framework/wpf/advanced/media/opentypefont21.gif "OpenTypeFont21")  
Texte utilisant l'espacement des majuscules OpenType  
  
 Le balisage suivant montre comment définir l’espacement des majuscules pour la police Pescadero, à l’aide des propriétés de la <xref:System.Windows.Documents.Typography> objet.  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet18](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#opentypefontsnippet18)]  
  
<a name="ligatures"></a>   
## <a name="ligatures"></a>Ligatures  
 Une ligature est un glyphe formé de deux ou plusieurs glyphes dans le but de créer un texte plus lisible ou esthétique. Les polices [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] prennent en charge quatre types de ligature :  
  
-   **Ligatures standard** : conçues pour améliorer la lisibilité. Par exemple, « fi », « fl » et « ff » sont des ligatures standard.  
  
-   **Ligatures contextuelles** : conçues pour améliorer la lisibilité en offrant un meilleur comportement de jointure entre les caractères qui composent la ligature.  
  
-   **Ligatures discrétionnaires** : conçues à des fins esthétiques et pas spécifiquement pour la lisibilité.  
  
-   **Ligatures historiques** : conçues en fonction de critères historiques et pas spécifiquement pour la lisibilité.  
  
 Le texte suivant présente des glyphes à ligatures standard avec la police Pericles.  
  
 ![Texte utilisant des ligatures standards OpenType](../../../../docs/framework/wpf/advanced/media/opentypefont04.gif "opentypefont04")  
Texte utilisant des ligatures standard OpenType  
  
 Le balisage suivant montre comment définir des ligatures standard pour la police Pericles, à l’aide des propriétés de la <xref:System.Windows.Documents.Typography> objet.  
  
 [!code-xaml[OpenTypeFontSamples#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#4)]  
  
 Le texte suivant présente des glyphes à ligatures discrétionnaires avec la police Pericles.  
  
 ![Texte utilisant des ligatures discrétionnaires OpenType](../../../../docs/framework/wpf/advanced/media/opentypefont05.gif "opentypefont05")  
Texte utilisant des ligatures discrétionnaires OpenType  
  
 Le balisage suivant montre comment définir des ligatures discrétionnaires pour la police Pericles, à l’aide des propriétés de la <xref:System.Windows.Documents.Typography> objet.  
  
 [!code-xaml[OpenTypeFontSamples#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#5)]  
  
 Par défaut, les polices [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] dans [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] autorisent les ligatures standard. Par exemple, si vous utilisez la police Palatino Linotype, les ligatures standard « fi », « ff » et « fl » apparaissent comme un glyphe de caractères combinés. Notez que les deux caractères de chaque ligature standard se touchent.  
  
 ![Texte utilisant des ligatures standards OpenType](../../../../docs/framework/wpf/advanced/media/opentypefont06.gif "opentypefont06")  
Texte utilisant des ligatures standard OpenType  
  
 Vous pouvez cependant désactiver les fonctionnalités de ligature standard de sorte qu’une ligature standard comme « ff » s’affiche comme deux glyphes distincts et non comme un glyphe de caractères combinés.  
  
 ![Texte utilisant des ligatures standard OpenType désactivées](../../../../docs/framework/wpf/advanced/media/opentypefont07.gif "opentypefont07")  
Texte utilisant des ligatures standard OpenType désactivées  
  
 Le balisage suivant montre comment désactiver des glyphes de ligatures standard pour la police Palatino Linotype, à l’aide des propriétés de la <xref:System.Windows.Documents.Typography> objet.  
  
 [!code-xaml[OpenTypeFontSamples#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#6)]  
  
<a name="swashes"></a>   
## <a name="swashes"></a>Lettres ornées  
 Les lettres ornées sont des glyphes décoratifs qui utilisent une ornementation élaborée souvent associée à la calligraphie. Le texte suivant présente des glyphes standard et des glyphes à lettres ornées avec la police Pescadero.  
  
 ![Texte utilisant des glyphes standard et ornés OpenType](../../../../docs/framework/wpf/advanced/media/opentypefont08.gif "opentypefont08")  
Texte utilisant des glyphes standard et ornés OpenType  
  
 Les lettres ornées sont souvent utilisés comme éléments décoratifs dans des expressions courtes annonçant par exemple un événement. Le texte suivant utilise des lettres ornées pour mettre en relief les majuscules du nom de l’événement.  
  
 ![Texte utilisant des glyphes ornés OpenType](../../../../docs/framework/wpf/advanced/media/opentypefont09.gif "opentypefont09")  
Texte utilisant des lettres ornées OpenType  
  
 Le balisage suivant montre comment définir des glyphes ornés pour une police, à l’aide des propriétés de la <xref:System.Windows.Documents.Typography> objet.  
  
 [!code-xaml[OpenTypeFontSamples#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#7)]  
  
### <a name="contextual-swashes"></a>Lettres ornées contextuelles  
 Certaines combinaisons de glyphes à lettres ornées peuvent donner des résultats peu esthétiques, avec notamment le chevauchement de hampes descendantes dans les lettres adjacentes. En utilisant des lettres ornées contextuelles, vous pouvez obtenir un meilleur résultat visuel. Le texte suivant présente le même mot avant et après l’application d’une lettre ornée contextuelle.  
  
 ![Texte utilisant des glyphes ornés contextuels OpenType](../../../../docs/framework/wpf/advanced/media/opentypefont19.gif "OpenTypeFont19")  
Texte utilisant des glyphes ornés contextuels OpenType  
  
 Le balisage suivant montre comment définir un paraphe contextuel pour la police Pescadero, à l’aide des propriétés de la <xref:System.Windows.Documents.Typography> objet.  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet16](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#opentypefontsnippet16)]  
  
<a name="alternates"></a>   
## <a name="alternates"></a>Alternatives  
 Les alternatives sont des glyphes qui peuvent être remplacés par un glyphe standard. Les polices [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)], telles que la police Pericles utilisée dans les exemples suivants, peuvent contenir des glyphes de style alternatif dont vous pouvez vous servir pour donner à du texte différentes apparences. Le texte suivant présente des glyphes standard avec la police Pericles.  
  
 ![Texte utilisant des glyphes standards OpenType](../../../../docs/framework/wpf/advanced/media/opentypefont01.gif "opentypefont01")  
Texte utilisant des glyphes standard OpenType  
  
 La police [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] Pericles contient des glyphes supplémentaires qui représentent des styles alternatifs au jeu de glyphes standard. Le texte suivant présente des glyphes de style alternatif.  
  
 ![Texte utilisant des glyphes de style alternatifs OpenType](../../../../docs/framework/wpf/advanced/media/opentypefont02.gif "opentypefont02")  
Texte utilisant des glyphes de style alternatifs OpenType  
  
 Le balisage suivant montre comment définir des glyphes de style alternatifs pour la police Pericles, à l’aide des propriétés de la <xref:System.Windows.Documents.Typography> objet.  
  
 [!code-xaml[OpenTypeFontSamples#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#2)]  
  
 Le texte suivant présente plusieurs autres glyphes de style alternatif pour la police Pericles.  
  
 ![Texte utilisant des glyphes de style alternatifs OpenType](../../../../docs/framework/wpf/advanced/media/opentypefont03.gif "opentypefont03")  
Texte utilisant des glyphes de style alternatifs OpenType  
  
 L’exemple de balisage suivant montre comment définir ces autres glyphes de style alternatif.  
  
 [!code-xaml[OpenTypeFontSamples#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#3)]  
  
### <a name="random-contextual-alternates"></a>Alternatives contextuelles aléatoires  
 Les alternatives contextuelles aléatoires proposent plusieurs glyphes de substitution pour un même caractère. Quand elle est implémentée avec des polices de caractères d’écriture, cette fonctionnalité peut simuler l’écriture manuscrite à partir d’un jeu de glyphes choisis de façon aléatoire avec de légères différences d’apparence. Le texte suivant présente des alternatives contextuelles aléatoires avec la police Lindsey. Notez que la lettre « a » présente de légères variations.  
  
 ![Texte utilisant les alternatives contextuelles aléatoires OpenType](../../../../docs/framework/wpf/advanced/media/opentypefont23.gif "OpenTypeFont23")  
Texte utilisant des alternatives contextuelles aléatoires OpenType  
  
 Le balisage suivant montre comment définir les alternatives contextuelles aléatoires pour la police Lindsey, à l’aide des propriétés de la <xref:System.Windows.Documents.Typography> objet.  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet20](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/Window1.xaml#opentypefontsnippet20)]  
  
### <a name="historical-forms"></a>Formes historiques  
 Les formes historiques sont des conventions typographiques qui étaient courantes dans le passé. Dans le texte, l’expression « Boston, Massachusetts » présente une forme historique de glyphes avec la police Palatino Linotype.  
  
 ![Texte utilisant des formulaires historiques OpenType](../../../../docs/framework/wpf/advanced/media/opentypefont10.gif "opentypefont10")  
Texte utilisant des formes historiques OpenType  
  
 Le balisage suivant montre comment définir des formulaires historiques pour la police Palatino Linotype, à l’aide des propriétés de la <xref:System.Windows.Documents.Typography> objet.  
  
 [!code-xaml[OpenTypeFontSamples#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#8)]  
  
<a name="numerical_styles"></a>   
## <a name="numerical-styles"></a>Styles numériques  
 Les polices OpenType prennent en charge un grand nombre de fonctionnalités qui peuvent être utilisées avec des valeurs numériques dans du texte.  
  
### <a name="fractions"></a>Fractions  
 Les polices [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] prennent en charge les fractions représentées avec une barre oblique ou horizontale.  
  
 Le texte suivant présente des styles de fraction avec la police Palatino Linotype.  
  
 ![Texte à l’aide de OpenType avec barres obliques et fractions](../../../../docs/framework/wpf/advanced/media/opentypefont12.gif "opentypefont12")  
Texte utilisant des fractions OpenType avec barres obliques et barres horizontales  
  
 Le balisage suivant montre comment définir des styles de fraction pour la police Palatino Linotype, à l’aide des propriétés de la <xref:System.Windows.Documents.Typography> objet.  
  
 [!code-xaml[OpenTypeFontSamples#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#10)]  
  
### <a name="old-style-numerals"></a>Chiffres de style ancien  
 Les polices [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] prennent en charge un format de chiffres de style ancien. Ce format est utile pour présenter les chiffres dans des styles qui ne sont plus courants. Le texte suivant présente une date du 18e siècle dans des formats numériques de style ancien avec la police Palatino Linotype.  
  
 ![Texte utilisant des chiffres OpenType de style ancien](../../../../docs/framework/wpf/advanced/media/opentypefont24.gif "OpenTypeFont24")  
Texte utilisant les chiffres OpenType de style ancien  
  
 Le texte suivant présente des chiffres standard avec la police Palatino Linotype, suivis de chiffres de style ancien.  
  
 ![Texte à l’aide d’anciens jeux de chiffres style OpenType](../../../../docs/framework/wpf/advanced/media/opentypefont13.gif "opentypefont13")  
Texte utilisant les jeux de chiffres OpenType de style ancien  
  
 Le balisage suivant montre comment définir des chiffres de style ancien pour la police Palatino Linotype, à l’aide des propriétés de la <xref:System.Windows.Documents.Typography> objet.  
  
 [!code-xaml[OpenTypeFontSamples#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#11)]  
  
### <a name="proportional-and-tabular-figures"></a>Chiffres proportionnels et tabulaires  
 Les polices [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] prennent en charge les chiffres proportionnels et tabulaires dans le but de contrôler l’alignement des chiffres par rapport à leur largeur. Les chiffres proportionnels sont considérés comme ayant chacun une largeur différente (« 1 » est plus étroit que « 5 »). À l’inverse, les chiffres tabulaires sont considérés comme ayant la même largeur, ce qui permet de les aligner verticalement et d’améliorer leur lisibilité dans les documents financiers.  
  
 Le texte ci-dessous présente deux chiffres proportionnels dans la première colonne avec la police Miramonte. Comme vous pouvez le constater, les chiffres « 5 » et « 1 » n’ont pas la même largeur. La deuxième colonne présente ces deux mêmes valeurs numériques avec des largeurs ajustées au moyen de la fonctionnalité des chiffres tabulaires.  
  
 ![Texte utilisant les chiffres tabulaires et proportionnels OpenType](../../../../docs/framework/wpf/advanced/media/opentypefont22.gif "OpenTypeFont22")  
Texte utilisant les chiffres tabulaires et proportionnels OpenType  
  
 Le balisage suivant montre comment définir des illustrations proportionnelles et tabulaires pour la police Miramonte, à l’aide des propriétés de la <xref:System.Windows.Documents.Typography> objet.  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet19](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/Window1.xaml#opentypefontsnippet19)]  
  
### <a name="slashed-zero"></a>Zéro barré  
 Les polices [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] prennent en charge le format numérique zéro barré pour distinguer la lettre « O » du chiffre « 0 ». Le chiffre zéro barré est souvent utilisé pour les identificateurs dans les informations financières et commerciales.  
  
 Le texte suivant présente un exemple d’identificateur de commande avec la police Miramonte. La première ligne contient des chiffres standard. La deuxième ligne contient des chiffres zéro barré pour mieux les distinguer de la lettre « O » majuscule.  
  
 ![Des chiffres zéro barré de texte à l’aide de OpenType](../../../../docs/framework/wpf/advanced/media/opentypefont17.gif "OpenTypeFont17")  
Texte utilisant des chiffres zéro barré OpenType  
  
 Le balisage suivant montre comment définir des chiffres zéro pour la police Miramonte, à l’aide des propriétés de barré le <xref:System.Windows.Documents.Typography> objet.  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#opentypefontsnippet15)]  
  
<a name="typography_class"></a>   
## <a name="typography-class"></a>Classe Typography  
 Le <xref:System.Windows.Documents.Typography> objet expose l’ensemble des fonctionnalités qui une [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] prend en charge de la police. En définissant les propriétés de <xref:System.Windows.Documents.Typography> dans le balisage, vous pouvez créer facilement des documents qui tirent parti de [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] fonctionnalités.  
  
 Le texte suivant présente des majuscules standard avec la police Pescadero, suivies de lettres de type « SmallCaps » et « AllSmallCaps ». Dans ce cas, la taille de police utilisée est identique pour les trois mots.  
  
 ![Texte utilisant des majuscules OpenType](../../../../docs/framework/wpf/advanced/media/opentypefont11.gif "opentypefont11")  
Texte utilisant des majuscules OpenType  
  
 Le balisage suivant montre comment définir des majuscules pour la police Pescadero, à l’aide des propriétés de la <xref:System.Windows.Documents.Typography> objet. Quand le format « SmallCaps » est utilisé, les majuscules de début sont ignorées.  
  
 [!code-xaml[OpenTypeFontSamples#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#9)]  
  
 L’exemple de code suivant effectue la même tâche que l’exemple de balisage précédent.  
  
 [!code-csharp[TypographyCodeSnippets#TypographyCodeSnippet1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TypographyCodeSnippets/CSharp/Page1.xaml.cs#typographycodesnippet1)]
 [!code-vb[TypographyCodeSnippets#TypographyCodeSnippet1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TypographyCodeSnippets/visualbasic/page1.xaml.vb#typographycodesnippet1)]  
  
### <a name="typography-class-properties"></a>Propriétés de la classe Typography  
 Le tableau suivant répertorie les propriétés, les valeurs et les paramètres par défaut de la <xref:System.Windows.Documents.Typography> objet.  
  
|Propriété|Valeur(s)|Valeur par défaut|  
|--------------|----------------|-------------------|  
|<xref:System.Windows.Documents.Typography.AnnotationAlternates%2A>|Valeur numérique - octet|0|  
|<xref:System.Windows.Documents.Typography.Capitals%2A>|<xref:System.Windows.FontCapitals.AllPetiteCaps> &#124; <xref:System.Windows.FontCapitals.AllSmallCaps> &#124; <xref:System.Windows.FontCapitals.Normal> &#124; <xref:System.Windows.FontCapitals.PetiteCaps> &#124; <xref:System.Windows.FontCapitals.SmallCaps> &#124; <xref:System.Windows.FontCapitals.Titling> &#124; <xref:System.Windows.FontCapitals.Unicase>|<xref:System.Windows.FontCapitals.Normal?displayProperty=nameWithType>|  
|<xref:System.Windows.Documents.Typography.CapitalSpacing%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.CaseSensitiveForms%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.ContextualAlternates%2A>|<xref:System.Boolean>|`true`|  
|<xref:System.Windows.Documents.Typography.ContextualLigatures%2A>|<xref:System.Boolean>|`true`|  
|<xref:System.Windows.Documents.Typography.ContextualSwashes%2A>|Valeur numérique - octet|0|  
|<xref:System.Windows.Documents.Typography.DiscretionaryLigatures%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.EastAsianExpertForms%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.EastAsianLanguage%2A>|<xref:System.Windows.FontEastAsianLanguage.HojoKanji> &#124; <xref:System.Windows.FontEastAsianLanguage.Jis04> &#124; <xref:System.Windows.FontEastAsianLanguage.Jis78> &#124; <xref:System.Windows.FontEastAsianLanguage.Jis83> &#124; <xref:System.Windows.FontEastAsianLanguage.Jis90> &#124; <xref:System.Windows.FontEastAsianLanguage.NlcKanji> &#124; <xref:System.Windows.FontEastAsianLanguage.Normal> &#124; <xref:System.Windows.FontEastAsianLanguage.Simplified> &#124; <xref:System.Windows.FontEastAsianLanguage.Traditional> &#124; <xref:System.Windows.FontEastAsianLanguage.TraditionalNames>|<xref:System.Windows.FontEastAsianLanguage.Normal?displayProperty=nameWithType>|  
|<xref:System.Windows.Documents.Typography.EastAsianWidths%2A>|<xref:System.Windows.FontEastAsianWidths.Full> &#124; <xref:System.Windows.FontEastAsianWidths.Half> &#124; <xref:System.Windows.FontEastAsianWidths.Normal> &#124; <xref:System.Windows.FontEastAsianWidths.Proportional> &#124; <xref:System.Windows.FontEastAsianWidths.Quarter> &#124; <xref:System.Windows.FontEastAsianWidths.Third>|<xref:System.Windows.FontEastAsianWidths.Normal?displayProperty=nameWithType>|  
|<xref:System.Windows.Documents.Typography.Fraction%2A>|<xref:System.Windows.FontFraction.Normal> &#124; <xref:System.Windows.FontFraction.Slashed> &#124; <xref:System.Windows.FontFraction.Stacked>|<xref:System.Windows.FontFraction.Normal?displayProperty=nameWithType>|  
|<xref:System.Windows.Documents.Typography.HistoricalForms%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.HistoricalLigatures%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.Kerning%2A>|<xref:System.Boolean>|`true`|  
|<xref:System.Windows.Documents.Typography.MathematicalGreek%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.NumeralAlignment%2A>|<xref:System.Windows.FontNumeralAlignment.Normal> &#124; <xref:System.Windows.FontNumeralAlignment.Proportional> &#124; <xref:System.Windows.FontNumeralAlignment.Tabular>|<xref:System.Windows.FontNumeralAlignment.Normal?displayProperty=nameWithType>|  
|<xref:System.Windows.Documents.Typography.NumeralStyle%2A>|<xref:System.Boolean>|<xref:System.Windows.FontNumeralStyle.Normal?displayProperty=nameWithType>|  
|<xref:System.Windows.Documents.Typography.SlashedZero%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StandardLigatures%2A>|<xref:System.Boolean>|`true`|  
|<xref:System.Windows.Documents.Typography.StandardSwashes%2A>|Valeur numérique - octet|0|  
|<xref:System.Windows.Documents.Typography.StylisticAlternates%2A>|Valeur numérique - octet|0|  
|<xref:System.Windows.Documents.Typography.StylisticSet1%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet2%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet3%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet4%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet5%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet6%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet7%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet8%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet9%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet10%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet11%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet12%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet13%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet14%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet15%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet16%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet17%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet18%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet19%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet20%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.Variants%2A>|<xref:System.Windows.FontVariants.Inferior> &#124; <xref:System.Windows.FontVariants.Normal> &#124; <xref:System.Windows.FontVariants.Ordinal> &#124; <xref:System.Windows.FontVariants.Ruby> &#124; <xref:System.Windows.FontVariants.Subscript> &#124; <xref:System.Windows.FontVariants.Superscript>|<xref:System.Windows.FontVariants.Normal?displayProperty=nameWithType>|  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Documents.Typography>  
 [Spécification OpenType](http://go.microsoft.com/fwlink/?LinkId=96731)  
 [Typographie dans WPF](../../../../docs/framework/wpf/advanced/typography-in-wpf.md)  
 [Exemple de pack de polices OpenType](../../../../docs/framework/wpf/advanced/sample-opentype-font-pack.md)  
 [Empaquetage de polices avec des applications](../../../../docs/framework/wpf/advanced/packaging-fonts-with-applications.md)
