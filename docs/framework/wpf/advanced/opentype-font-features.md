---
title: "Fonctionnalit&#233;s des polices OpenType | Microsoft Docs"
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
  - "polices OpenType"
  - "typographie, technologie de police OpenType"
  - "OpenType (technologie de police)"
ms.assetid: 4061a9d1-fe8b-4921-9e17-18ec7d2e3ea2
caps.latest.revision: 38
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 37
---
# Fonctionnalit&#233;s des polices OpenType
Cette rubrique fournit une vue d’ensemble de certaines des fonctionnalités clés de [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] technologie de police dans [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  
  
   
  
<a name="overview"></a>   
## <a name="opentype-font-format"></a>Format des polices OpenType  
 Le [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] format de police est une extension de la [!INCLUDE[TLA#tla_truetype](../../../../includes/tlasharptla-truetype-md.md)] format de police, la prise en charge des données des polices PostScript. Le [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] format de police a été développé conjointement par [!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)] et Adobe Corporation. [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)]la prise en charge des services du système d’exploitation et les polices [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] polices offrent aux utilisateurs un moyen simple pour installer et utiliser des polices, si les polices contiennent [!INCLUDE[TLA2#tla_truetype](../../../../includes/tla2sharptla-truetype-md.md)] plans ou les plans CFF (PostScript).  
  
 Le [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] format de police résout les problèmes de développement suivantes :  
  
-   Prise en charge étendue de multi-plateforme.  
  
-   Meilleure prise en charge pour les jeux de caractères internationaux.  
  
-   Une meilleure protection des données des polices.  
  
-   Fichiers plus petits pour faciliter la distribution de la police.  
  
-   Prise en charge élargie des contrôles typographiques avancés.  
  
> [!NOTE]
>  Le Kit de développement logiciel Windows contient un jeu d’exemples [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] les polices que vous pouvez utiliser avec [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] applications. Ces polices fournissent la plupart des fonctionnalités illustrées dans le reste de cette rubrique. Pour plus d’informations, consultez [exemple de Pack de polices OpenType](../../../../docs/framework/wpf/advanced/sample-opentype-font-pack.md).  
  
 Consultez le [spécification OpenType](http://go.microsoft.com/fwlink/?LinkId=96731) pour des détails sur les [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] format de police.  
  
### <a name="advanced-typographic-extensions"></a>Extensions typographiques avancées  
 Les tableaux typographiques avancés ([!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] tableaux de disposition) étendent les fonctionnalités de polices avec des [!INCLUDE[TLA2#tla_truetype](../../../../includes/tla2sharptla-truetype-md.md)] ou CFF contours. [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)]Polices de mise en page contiennent des informations supplémentaires qui étend les fonctionnalités des polices pour prendre en charge la typographie internationale de haute qualité. La plupart des [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] polices exposent uniquement un sous-ensemble du total [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] fonctionnalités disponibles. [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)]polices fournissent les fonctionnalités suivantes.  
  
-   Mappage riche entre caractères et glyphes prenant en charge des ligatures, des formulaires de position, remplaçants et autres substitutions de polices.  
  
-   Prise en charge des pièces jointes de positionnement et le glyphe à deux dimensions.  
  
-   Informations de script et de langage explicites contenues dans police, une application de traitement de texte peut ajuster son comportement en conséquence.  
  
 Le [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] tableaux de disposition sont décrites plus en détail dans les [« Font File Tables »](http://www.microsoft.com/typography/otspec/otff.htm) section de la [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] spécification.  
  
 Le reste de cette vue d’ensemble introduit l’ampleur et la flexibilité de quelques-unes des visuellement intéressantes [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] fonctionnalités exposées par les propriétés de la <xref:System.Windows.Documents.Typography> objet. Pour plus d’informations sur cet objet, consultez [typographie classe](#typography_class).  
  
<a name="variants"></a>   
## <a name="variants"></a>Variantes  
 Les variantes sont utilisées pour restituer différents styles typographiques, tels que des exposants et des indices.  
  
### <a name="superscripts-and-subscripts"></a>Exposants et indices  
 Le <xref:System.Windows.Documents.Typography.Variants%2A> propriété vous permet de définir des valeurs d’exposant et d’indice pour une [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] police.  
  
 Le texte suivant affiche des exposants pour la police Palatino Linotype.  
  
 ![Texte utilisant des exposants OpenType](../../../../docs/framework/wpf/advanced/media/opentypefont14.png "opentypefont14")  
Texte utilisant des exposants OpenType  
  
 L’exemple de balise suivant montre comment définir des exposants pour la police Palatino Linotype, à l’aide des propriétés de la <xref:System.Windows.Documents.Typography> objet.  
  
 [!code-xml[OpenTypeFontSamples#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#12)]  
  
 Le texte suivant affiche des indices pour la police Palatino Linotype.  
  
 ![Texte utilisant des indices OpenType](../../../../docs/framework/wpf/advanced/media/opentypefont15.png "opentypefont15")  
Texte utilisant des indices OpenType  
  
 L’exemple de balise suivant montre comment définir des indices pour la police Palatino Linotype, à l’aide des propriétés de la <xref:System.Windows.Documents.Typography> objet.  
  
 [!code-xml[OpenTypeFontSamples#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#13)]  
  
### <a name="decorative-uses-of-superscripts-and-subscripts"></a>Utilisations décoratives d’exposants et indices  
 Vous pouvez également utiliser des exposants et des indices pour créer des effets décoratifs de texte à casse mixte. Le texte suivant affiche le texte en exposant et indice pour la police Palatino Linotype. Notez que les majuscules ne sont pas affectés.  
  
 ![Texte utilisant des indices et des exposants OpenType](../../../../docs/framework/wpf/advanced/media/opentypefont16.png "opentypefont16")  
Texte utilisant des exposants et des indices OpenType  
  
 L’exemple de balise suivant montre comment définir des exposants et des indices pour une police, à l’aide des propriétés de la <xref:System.Windows.Documents.Typography> objet.  
  
 [!code-xml[OpenTypeFontSamples#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#14)]  
  
<a name="capitals"></a>   
## <a name="capitals"></a>Majuscules  
 Les majuscules sont un jeu de formats typographiques qui restituent le texte dans des glyphes de type majuscule. En règle générale, lorsque le texte est restitué en majuscules, l’espacement entre les lettres peut apparaître trop serré et le poids et proportion des lettres trop lourds. [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)]prend en charge les formats de style pour les majuscules, y compris les petites majuscules, les majuscules menues, titres et l’espacement des majuscules. Ces formats de style permettent de contrôler l’apparence de majuscules.  
  
 Le texte suivant affiche des majuscules standard pour la police Pescadero, suivis par les lettres sous la forme « SmallCaps » et « AllSmallCaps ». Dans ce cas, la même taille de police est utilisée pour les trois mots.  
  
 ![Texte utilisant des majuscules OpenType](../../../../docs/framework/wpf/advanced/media/opentypefont11.png "opentypefont11")  
Texte utilisant des majuscules OpenType  
  
 L’exemple de balise suivant montre comment définir des majuscules pour la police Pescadero, à l’aide des propriétés de la <xref:System.Windows.Documents.Typography> objet. Lorsque le format « SmallCaps » est utilisé, toute majuscule principale est ignorée.  
  
 [!code-xml[OpenTypeFontSamples#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#9)]  
  
### <a name="titling-capitals"></a>Des majuscules de titre  
 Des majuscules sont conçues pour donner un aspect plus élégant que les majuscules normales et poids et proportion. Des majuscules sont généralement utilisés dans une police plus grande comme en-têtes. Le texte suivant affiche les normales et des majuscules pour la police Pescadero. Remarquez les traits plus fins du texte sur la deuxième ligne.  
  
 ![Texte utilisant des majuscules de titre OpenType](../../../../docs/framework/wpf/advanced/media/opentypefont20.png "OpenTypeFont20")  
Texte utilisant des majuscules de titre OpenType  
  
 L’exemple de balise suivant montre comment définir des majuscules pour la police Pescadero, à l’aide des propriétés de la <xref:System.Windows.Documents.Typography> objet.  
  
 [!code-xml[OpenTypeFontSamples#OpenTypeFontSnippet17](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#opentypefontsnippet17)]  
  
### <a name="capital-spacing"></a>Espacement des majuscules  
 L’espacement des majuscules est une fonctionnalité qui vous permet de fournir plus d’espacement lors de l’utilisation des majuscules dans le texte. Les lettres majuscules sont généralement conçus pour fusionner avec les lettres minuscules. L’espacement qui apparaît attirant entre et une lettre majuscule et une minuscule peuvent sembler trop serrés lorsque toutes les lettres majuscules sont utilisées. Le texte suivant affiche l’espacement normal et de capital pour la police Pescadero.  
  
 ![Texte utilisant l’espacement des majuscules OpenType](../../../../docs/framework/wpf/advanced/media/opentypefont21.png "OpenTypeFont21")  
Texte utilisant l'espacement des majuscules OpenType  
  
 L’exemple de balise suivant montre comment définir l’espacement des majuscules pour la police Pescadero, à l’aide des propriétés de la <xref:System.Windows.Documents.Typography> objet.  
  
 [!code-xml[OpenTypeFontSamples#OpenTypeFontSnippet18](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#opentypefontsnippet18)]  
  
<a name="ligatures"></a>   
## <a name="ligatures"></a>Ligatures  
 Les ligatures sont deux ou plusieurs des glyphes qui sont formés en un glyphe unique pour créer le texte plus lisible ou attrayant. [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)]polices prennent en charge quatre types de ligatures :  
  
-   **Des ligatures standard**. Conçu pour améliorer la lisibilité. Les ligatures standard incluent « fi », « fl » et « ff ».  
  
-   **Ligatures contextuelles**. Conçu pour améliorer la lisibilité en fournissant le meilleur comportement de jointure entre les caractères qui composent la ligature.  
  
-   **Des ligatures discrétionnaires**. Conçu pour être décoratives et pas spécifiquement conçu pour une meilleure lisibilité.  
  
-   **Ligatures historiques**. Conçu pour être historiques et pas spécifiquement conçu pour une meilleure lisibilité.  
  
 Le texte suivant affiche des glyphes de ligature standard pour la police Pericles.  
  
 ![Texte utilisant des ligatures standards OpenType](../../../../docs/framework/wpf/advanced/media/opentypefont04.png "opentypefont04")  
Texte utilisant des ligatures standard OpenType  
  
 L’exemple de balise suivant montre comment définir des ligatures standard pour la police Pericles, à l’aide des propriétés de la <xref:System.Windows.Documents.Typography> objet.  
  
 [!code-xml[OpenTypeFontSamples#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#4)]  
  
 Le texte suivant affiche des glyphes de ligatures discrétionnaires pour la police Pericles.  
  
 ![Texte utilisant des ligatures discrétionnaires OpenType](../../../../docs/framework/wpf/advanced/media/opentypefont05.png "opentypefont05")  
Texte utilisant des ligatures discrétionnaires OpenType  
  
 L’exemple de balise suivant montre comment définir des glyphes de ligatures discrétionnaires pour la police Pericles, à l’aide des propriétés de la <xref:System.Windows.Documents.Typography> objet.  
  
 [!code-xml[OpenTypeFontSamples#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#5)]  
  
 Par défaut, [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] polices dans [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] autorisent les ligatures standard. Par exemple, si vous utilisez la police Palatino Linotype, les ligatures standard « fi », « ff » et « fl » apparaissent comme un glyphe de caractères combinés. Notez que la paire de caractères de chaque ligature standard touch.  
  
 ![Texte utilisant des ligatures standards OpenType](../../../../docs/framework/wpf/advanced/media/opentypefont06.png "opentypefont06")  
Texte utilisant des ligatures standard OpenType  
  
 Toutefois, vous pouvez désactiver les fonctionnalités de ligature standard afin qu’une ligature standard tels que « ff » affiche comme deux glyphes séparés, plutôt que comme un glyphe de caractères combinés.  
  
 ![Texte utilisant des ligatures standard OpenType désactivées](../../../../docs/framework/wpf/advanced/media/opentypefont07.png "opentypefont07")  
Texte utilisant des ligatures standard OpenType désactivées  
  
 L’exemple de balise suivant montre comment désactiver des glyphes de ligature standard pour la police Palatino Linotype, à l’aide des propriétés de la <xref:System.Windows.Documents.Typography> objet.  
  
 [!code-xml[OpenTypeFontSamples#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#6)]  
  
<a name="swashes"></a>   
## <a name="swashes"></a>Glyphes ornés  
 Glyphes ornés sont des glyphes décoratifs qui utilisent une ornementation élaborée souvent associée calligraphique. Le texte suivant affiche des glyphes standard et ornés pour la police Pescadero.  
  
 ![Texte utilisant des glyphes standard et ornés OpenType](../../../../docs/framework/wpf/advanced/media/opentypefont08.png "opentypefont08")  
Texte utilisant des glyphes standard et ornés OpenType  
  
 Glyphes ornés sont souvent utilisés comme éléments décoratifs dans des expressions courtes telles que les annonces d’événement. Le texte suivant utilise des glyphes ornés pour accentuer les majuscules du nom de l’événement.  
  
 ![Texte utilisant des glyphes ornés OpenType](../../../../docs/framework/wpf/advanced/media/opentypefont09.png "opentypefont09")  
Texte utilisant des glyphes ornés OpenType  
  
 L’exemple de balise suivant montre comment définir des glyphes ornés pour une police, à l’aide des propriétés de la <xref:System.Windows.Documents.Typography> objet.  
  
 [!code-xml[OpenTypeFontSamples#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#7)]  
  
### <a name="contextual-swashes"></a>Glyphes ornés contextuels  
 Certaines combinaisons des glyphes ornés peuvent provoquer une apparence peu attrayante, telles que les hampes inférieures chevauchant les lettres adjacentes. À l’aide d’un ornés contextuels vous permet d’utiliser un glyphe ornés de substitution qui produit une meilleure apparence. Le texte suivant illustre le même mot avant et après qu’un ornés contextuels est appliqué.  
  
 ![Texte utilisant des glyphes ornés contextuels OpenType](../../../../docs/framework/wpf/advanced/media/opentypefont19.png "OpenTypeFont19")  
Texte utilisant des glyphes ornés contextuels OpenType  
  
 L’exemple de balise suivant montre comment définir un paraphe contextuel pour la police Pescadero, à l’aide des propriétés de la <xref:System.Windows.Documents.Typography> objet.  
  
 [!code-xml[OpenTypeFontSamples#OpenTypeFontSnippet16](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#opentypefontsnippet16)]  
  
<a name="alternates"></a>   
## <a name="alternates"></a>Alterne  
 Les variantes sont des glyphes qui peuvent être remplacées par un glyphe standard. [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)]polices, telles que la police Pericles utilisée dans les exemples suivants, peuvent contenir des glyphes que vous pouvez utiliser pour créer différentes apparences pour le texte. Le texte suivant affiche des glyphes standard pour la police Pericles.  
  
 ![Texte utilisant des glyphes standards OpenType](../../../../docs/framework/wpf/advanced/media/opentypefont01.png "opentypefont01")  
Texte utilisant des glyphes standard OpenType  
  
 Le Pericles [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] police contient des glyphes supplémentaires qui offrent des remplaçants stylistiques au jeu de glyphes standard. Le texte suivant affiche des glyphes de style alternatifs.  
  
 ![Texte utilisant des glyphes de style d’alternatifs OpenType](../../../../docs/framework/wpf/advanced/media/opentypefont02.png "opentypefont02")  
Texte utilisant des glyphes de style alternatifs OpenType  
  
 L’exemple de balise suivant montre comment définir des glyphes de style alternatifs pour la police Pericles, à l’aide des propriétés de la <xref:System.Windows.Documents.Typography> objet.  
  
 [!code-xml[OpenTypeFontSamples#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#2)]  
  
 Le texte suivant affiche plusieurs autres glyphes de remplaçants stylistiques pour la police Pericles.  
  
 ![Texte utilisant des glyphes de style d’alternatifs OpenType](../../../../docs/framework/wpf/advanced/media/opentypefont03.png "opentypefont03")  
Texte utilisant des glyphes de style alternatifs OpenType  
  
 Le balisage suivant montre comment définir ces autres glyphes de style alternatifs.  
  
 [!code-xml[OpenTypeFontSamples#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#3)]  
  
### <a name="random-contextual-alternates"></a>Alternatives contextuelles aléatoires  
 Les alternatives contextuelles aléatoires fournissent plusieurs glyphes de substitution pour un caractère unique. En cas d’implémentation avec les polices d’écriture, cette fonctionnalité peut simuler l’écriture manuscrite à l’aide d’un jeu de glyphes choisis au hasard avec de légères différences dans l’apparence. Le texte suivant utilise les alternatives contextuelles aléatoires pour la police Lindsey. Notez que la lettre « a » varie légèrement dans l’apparence  
  
 ![Texte utilisant les alternatives contextuelles aléatoires OpenType](../../../../docs/framework/wpf/advanced/media/opentypefont23.png "OpenTypeFont23")  
Texte utilisant les alternatives contextuelles aléatoires OpenType  
  
 L’exemple de balise suivant montre comment définir les alternatives contextuelles aléatoires pour la police Lindsey, à l’aide des propriétés de la <xref:System.Windows.Documents.Typography> objet.  
  
 [!code-xml[OpenTypeFontSamples#OpenTypeFontSnippet20](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/Window1.xaml#opentypefontsnippet20)]  
  
### <a name="historical-forms"></a>Formulaires historiques  
 Les formats historiques sont des conventions typographiques qui étaient courantes dans le passé. Le texte suivant affiche l’expression, « Boston, Massachusetts », à l’aide d’un format historique de glyphes pour la police Palatino Linotype.  
  
 ![Texte utilisant des formulaires historiques OpenType](../../../../docs/framework/wpf/advanced/media/opentypefont10.png "opentypefont10")  
Texte utilisant des formulaires historiques OpenType  
  
 L’exemple de balise suivant montre comment définir des formulaires historiques pour la police Palatino Linotype, à l’aide des propriétés de la <xref:System.Windows.Documents.Typography> objet.  
  
 [!code-xml[OpenTypeFontSamples#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#8)]  
  
<a name="numerical_styles"></a>   
## <a name="numerical-styles"></a>Styles numériques  
 Les polices OpenType prennent en charge un grand nombre de fonctionnalités qui peut être utilisé avec des valeurs numériques en texte.  
  
### <a name="fractions"></a>Fractions  
 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)]polices prennent en charge les styles pour les fractions, y compris barré et sur deux.  
  
 Le texte suivant affiche des styles de fraction pour la police Palatino Linotype.  
  
 ![Texte utilisant OpenType fractions barrées et empilées](../../../../docs/framework/wpf/advanced/media/opentypefont12.png "opentypefont12")  
Texte utilisant des fractions OpenType avec barres obliques et barres horizontales  
  
 L’exemple de balise suivant montre comment définir des styles de fraction pour la police Palatino Linotype, à l’aide des propriétés de la <xref:System.Windows.Documents.Typography> objet.  
  
 [!code-xml[OpenTypeFontSamples#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#10)]  
  
### <a name="old-style-numerals"></a>Chiffres de Style ancien  
 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)]polices prennent en charge un format numérique de style ancien. Ce format est utile pour afficher des chiffres dans les styles qui ne sont plus standards. Le texte suivant affiche une date du 18e siècle dans les formats de chiffres standard et de style ancien pour la police Palatino Linotype.  
  
 ![Texte utilisant les chiffres OpenType de style ancien](../../../../docs/framework/wpf/advanced/media/opentypefont24.png "OpenTypeFont24")  
Texte utilisant les chiffres OpenType de style ancien  
  
 Le texte suivant affiche des chiffres standard pour la police Palatino Linotype, suivi par des chiffres de style ancien.  
  
 ![Texte utilisant des jeux de chiffres de style ancien OpenType](../../../../docs/framework/wpf/advanced/media/opentypefont13.png "opentypefont13")  
Texte utilisant les jeux de chiffres OpenType de style ancien  
  
 L’exemple de balise suivant montre comment définir des chiffres de style ancien pour la police Palatino Linotype, à l’aide des propriétés de la <xref:System.Windows.Documents.Typography> objet.  
  
 [!code-xml[OpenTypeFontSamples#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#11)]  
  
### <a name="proportional-and-tabular-figures"></a>Illustrations proportionnelles et tabulaires  
 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)]polices prennent en charge une fonctionnalité d’illustration proportionnelle et tabulaire pour contrôler l’alignement des largeurs lors de l’utilisation de chiffres. Nombres proportionnels traitent chaque chiffre comme ayant une largeur différente : « 1 » est plus étroit que « 5 ». Les illustrations tabulaires sont traitées comme des chiffres de largeur égale afin qu’ils s’alignent verticalement, ce qui améliore la lisibilité des informations de type financier.  
  
 Le texte suivant affiche deux illustrations proportionnelles dans la première colonne à l’aide de la police Miramonte. Notez la différence de largeur entre les chiffres « 5 » et « 1 ». La deuxième colonne affiche deux valeurs numériques identiques avec les largeurs ajustées à l’aide de la fonctionnalité d’illustration tabulaire.  
  
 ![Texte utilisant les chiffres OpenType proportionnels se tabulaire](../../../../docs/framework/wpf/advanced/media/opentypefont22.png "OpenTypeFont22")  
Texte utilisant les chiffres OpenType proportionnelles et tabulaires  
  
 L’exemple de balise suivant montre comment définir des illustrations proportionnelles et tabulaires pour la police Miramonte, à l’aide des propriétés de la <xref:System.Windows.Documents.Typography> objet.  
  
 [!code-xml[OpenTypeFontSamples#OpenTypeFontSnippet19](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/Window1.xaml#opentypefontsnippet19)]  
  
### <a name="slashed-zero"></a>Zéro barré  
 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)]polices prennent en charge un barré zéro format de chiffre à mettre en évidence la différence entre la lettre « O » et le chiffre « 0 ». Le barré que chiffre zéro est souvent utilisée pour les identificateurs dans les informations financières et commerciales.  
  
 Le texte suivant affiche un identificateur de commande d’exemple à l’aide de la police Miramonte. La première ligne utilise des chiffres standard. La deuxième ligne utilisée barré chiffres zéro pour fournir un meilleur contraste avec la lettre « O » majuscule.  
  
 ![Des chiffres zéro barré de texte à l’aide de OpenType](../../../../docs/framework/wpf/advanced/media/opentypefont17.png "OpenTypeFont17")  
Texte utilisant des chiffres zéro avec barre oblique OpenType  
  
 Le balisage suivant montre comment définir des chiffres zéro pour la police Miramonte, à l’aide des propriétés de barré le <xref:System.Windows.Documents.Typography> objet.  
  
 [!code-xml[OpenTypeFontSamples#OpenTypeFontSnippet15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#opentypefontsnippet15)]  
  
<a name="typography_class"></a>   
## <a name="typography-class"></a>Classe de typographie  
 Le <xref:System.Windows.Documents.Typography> objet expose l’ensemble des fonctionnalités qui un [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] prend en charge de la police. En définissant les propriétés de <xref:System.Windows.Documents.Typography> dans le balisage, vous pouvez créer facilement des documents qui tirent parti de [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] fonctionnalités.  
  
 Le texte suivant affiche des majuscules standard pour la police Pescadero, suivis par les lettres sous la forme « SmallCaps » et « AllSmallCaps ». Dans ce cas, la même taille de police est utilisée pour les trois mots.  
  
 ![Texte utilisant des majuscules OpenType](../../../../docs/framework/wpf/advanced/media/opentypefont11.png "opentypefont11")  
Texte utilisant des majuscules OpenType  
  
 L’exemple de balise suivant montre comment définir des majuscules pour la police Pescadero, à l’aide des propriétés de la <xref:System.Windows.Documents.Typography> objet. Lorsque le format « SmallCaps » est utilisé, toute majuscule principale est ignorée.  
  
 [!code-xml[OpenTypeFontSamples#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#9)]  
  
 L’exemple de code suivant effectue la même tâche que le balisage précédent.  
  
 [!code-csharp[TypographyCodeSnippets#TypographyCodeSnippet1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TypographyCodeSnippets/CSharp/Page1.xaml.cs#typographycodesnippet1)]
 [!code-vb[TypographyCodeSnippets#TypographyCodeSnippet1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TypographyCodeSnippets/visualbasic/page1.xaml.vb#typographycodesnippet1)]  
  
### <a name="typography-class-properties"></a>Propriétés de classe de typographie  
 Le tableau suivant répertorie les propriétés, valeurs et paramètres par défaut de la <xref:System.Windows.Documents.Typography> objet.  
  
|Propriété|Valeur (s)|Valeur par défaut|  
|--------------|----------------|-------------------|  
|<xref:System.Windows.Documents.Typography.AnnotationAlternates%2A>|Valeur numérique - octet|0|  
|<xref:System.Windows.Documents.Typography.Capitals%2A>|<xref:System.Windows.FontCapitals> | <xref:System.Windows.FontCapitals> | <xref:System.Windows.FontCapitals> | <xref:System.Windows.FontCapitals> | <xref:System.Windows.FontCapitals> | <xref:System.Windows.FontCapitals> | <xref:System.Windows.FontCapitals>|<xref:System.Windows.FontCapitals?displayProperty=fullName>|  
|<xref:System.Windows.Documents.Typography.CapitalSpacing%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.CaseSensitiveForms%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.ContextualAlternates%2A>|<xref:System.Boolean>|`true`|  
|<xref:System.Windows.Documents.Typography.ContextualLigatures%2A>|<xref:System.Boolean>|`true`|  
|<xref:System.Windows.Documents.Typography.ContextualSwashes%2A>|Valeur numérique - octet|0|  
|<xref:System.Windows.Documents.Typography.DiscretionaryLigatures%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.EastAsianExpertForms%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.EastAsianLanguage%2A>|<xref:System.Windows.FontEastAsianLanguage> | <xref:System.Windows.FontEastAsianLanguage> | <xref:System.Windows.FontEastAsianLanguage> | <xref:System.Windows.FontEastAsianLanguage> | <xref:System.Windows.FontEastAsianLanguage> | <xref:System.Windows.FontEastAsianLanguage> | <xref:System.Windows.FontEastAsianLanguage> | <xref:System.Windows.FontEastAsianLanguage> | <xref:System.Windows.FontEastAsianLanguage> | <xref:System.Windows.FontEastAsianLanguage>|<xref:System.Windows.FontEastAsianLanguage?displayProperty=fullName>|  
|<xref:System.Windows.Documents.Typography.EastAsianWidths%2A>|<xref:System.Windows.FontEastAsianWidths> | <xref:System.Windows.FontEastAsianWidths> | <xref:System.Windows.FontEastAsianWidths> | <xref:System.Windows.FontEastAsianWidths> | <xref:System.Windows.FontEastAsianWidths> | <xref:System.Windows.FontEastAsianWidths>|<xref:System.Windows.FontEastAsianWidths?displayProperty=fullName>|  
|<xref:System.Windows.Documents.Typography.Fraction%2A>|<xref:System.Windows.FontFraction> | <xref:System.Windows.FontFraction> | <xref:System.Windows.FontFraction>|<xref:System.Windows.FontFraction?displayProperty=fullName>|  
|<xref:System.Windows.Documents.Typography.HistoricalForms%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.HistoricalLigatures%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.Kerning%2A>|<xref:System.Boolean>|`true`|  
|<xref:System.Windows.Documents.Typography.MathematicalGreek%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.NumeralAlignment%2A>|<xref:System.Windows.FontNumeralAlignment> | <xref:System.Windows.FontNumeralAlignment> | <xref:System.Windows.FontNumeralAlignment>|<xref:System.Windows.FontNumeralAlignment?displayProperty=fullName>|  
|<xref:System.Windows.Documents.Typography.NumeralStyle%2A>|<xref:System.Boolean>|<xref:System.Windows.FontNumeralStyle?displayProperty=fullName>|  
|<xref:System.Windows.Documents.Typography.SlashedZero%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StandardLigatures%2A>|<xref:System.Boolean>|`true`|  
|<xref:System.Windows.Documents.Typography.StandardSwashes%2A>|valeur numérique-octet|0|  
|<xref:System.Windows.Documents.Typography.StylisticAlternates%2A>|valeur numérique-octet|0|  
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
|<xref:System.Windows.Documents.Typography.Variants%2A>|<xref:System.Windows.FontVariants> | <xref:System.Windows.FontVariants> | <xref:System.Windows.FontVariants> | <xref:System.Windows.FontVariants> | <xref:System.Windows.FontVariants> | <xref:System.Windows.FontVariants>|<xref:System.Windows.FontVariants?displayProperty=fullName>|  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Documents.Typography>   
 [Spécification OpenType](http://go.microsoft.com/fwlink/?LinkId=96731)   
 [Typographie dans WPF](../../../../docs/framework/wpf/advanced/typography-in-wpf.md)   
 [Exemple de Pack de polices OpenType](../../../../docs/framework/wpf/advanced/sample-opentype-font-pack.md)   
 [Empaqueter des polices avec des Applications](../../../../docs/framework/wpf/advanced/packaging-fonts-with-applications.md)