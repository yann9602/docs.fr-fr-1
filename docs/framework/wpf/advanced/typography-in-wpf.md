---
title: "Typographie dans WPF | Microsoft Docs"
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
  - "typographie, à propos de la typographie"
ms.assetid: 06cbf17b-6eff-4fe5-949d-2dd533e4e1f4
caps.latest.revision: 27
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 26
---
# Typographie dans WPF
Cette rubrique présente les principales fonctionnalités typographiques de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  Ces fonctionnalités incluent l'amélioration de la qualité et des performances de rendu de texte, une prise en charge de la typographie [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)], un texte international amélioré, une prise en charge de police améliorée et de nouvelles interfaces de programmation d'applications \(API, Application Programming Interface\) textes.  
  
   
  
<a name="Improved_Quality_and_Performance_of_Text"></a>   
## Amélioration de la qualité et des performances du texte  
 Le texte dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] est restitué à l'aide de [!INCLUDE[TLA#tla_ct](../../../../includes/tlasharptla-ct-md.md)], ce qui améliore sa clarté et sa lisibilité.  [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] est une technologie logicielle développée par [!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)] qui améliore la lisibilité de texte sur les écrans LCD existants, tels que les écrans d'ordinateurs portables, les écrans de Pocket PC et les écrans plats.  [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] utilise un rendu d'une précision inférieure au pixel qui permet l'affichage du texte avec une fidélité supérieure à sa forme réelle en alignant les caractères sur une fraction d'un pixel.  Cette résolution accrue augmente la netteté des détails dans l'affichage textuel, ce qui facilite grandement la lecture sur de longues périodes.  Une autre amélioration de [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] est l'anticrénelage de direction y qui lisse le haut et le bas des courbes superficielles dans les caractères de texte.  Pour plus d'informations sur les fonctionnalités [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)], consultez [Vue d'ensemble de ClearType](../../../../docs/framework/wpf/advanced/cleartype-overview.md).  
  
 ![Texte avec anticrénelage ClearType dans la direction y](../../../../docs/framework/wpf/advanced/media/typographyinwpf02.png "TypographyInWPF02")  
Texte avec anticrénelage de direction y ClearType  
  
 L'ensemble du pipeline de rendu de texte peut être accéléré par matériel dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], sous réserve que votre ordinateur respecte le niveau matériel minimum requis.  Un rendu ne pouvant pas être exécuté à l'aide de matériel correspond à un rendu logiciel.  L'accélération matérielle affecte toutes les phases du pipeline de rendu de texte, du stockage de glyphes individuels à l'application de l'algorithme de fusion [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] à la sortie finale affichée, en passant par la constitution de glyphes en exécutions de glyphes et l'application d'effets.  Pour plus d'informations sur l'accélération matérielle, consultez [Couches de rendu graphiques](../../../../docs/framework/wpf/advanced/graphics-rendering-tiers.md).  
  
 ![Diagramme du pipeline de rendu de texte](../../../../docs/framework/wpf/advanced/media/typographyinwpf01.png "TypographyInWPF01")  
Diagramme du pipeline de rendu de texte  
  
 En outre, un texte animé, par caractères ou par glyphes, tire pleinement parti de la fonction de matériel graphique activée par [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  On obtient une animation de texte lisse.  
  
<a name="Rich_Typography"></a>   
## Typographie riche  
 Le format de police [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] est une extension du format de police [!INCLUDE[TLA#tla_truetype](../../../../includes/tlasharptla-truetype-md.md)].  Le format de police [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] a été développé conjointement par [!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)] et Adobe ; il offre un large éventail de fonctionnalités typographiques avancées.  L'objet <xref:System.Windows.Documents.Typography> expose une grande partie des fonctionnalités avancées des polices [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)], telles que les paraphes et styles de substitution.  Le [!INCLUDE[TLA2#tla_lhsdk](../../../../includes/tla2sharptla-lhsdk-md.md)] fournit un jeu d'exemples de polices [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] conçues avec des fonctionnalités puissantes, telles que les polices Pericles et Pescadero.  Pour plus d'informations, consultez [Exemple de pack de polices OpenType](../../../../docs/framework/wpf/advanced/sample-opentype-font-pack.md).  
  
 La police Pericles [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] contient des glyphes supplémentaires qui offrent des styles de substitution au jeu de glyphes standard.  Le texte suivant affiche des glyphes de styles de substitution.  
  
 ![Texte utilisant des glyphes de style alternatifs OpenType](../../../../docs/framework/wpf/advanced/media/opentypefont02.png "opentypefont02")  
Texte utilisant des glyphes de styles de substitution OpenType  
  
 Les paraphes sont des glyphes décoratifs qui utilisent une ornementation élaborée souvent associée à la calligraphie.  Le texte suivant affiche des glyphes standard et des glyphes de paraphe pour la police Pescadero.  
  
 ![Texte utilisant des glyphes standard et ornés OpenType](../../../../docs/framework/wpf/advanced/media/opentypefont08.png "opentypefont08")  
Texte utilisant des glyphes de paraphe et des glyphes standard OpenType  
  
 Pour plus d'informations sur les fonctionnalités [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)], consultez [Fonctionnalités des polices OpenType](../../../../docs/framework/wpf/advanced/opentype-font-features.md).  
  
<a name="Enhanced_International_Text_Support"></a>   
## Prise en charge de texte international améliorée  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] offre une prise en charge de texte international améliorée en fournissant les fonctionnalités suivantes :  
  
-   Interligne automatique dans tous les systèmes d'écriture, via des mesures adaptables.  
  
-   Prise en charge générale du texte international.  Pour plus d'informations, consultez [Globalisation pour WPF](../../../../docs/framework/wpf/advanced/globalization-for-wpf.md).  
  
-   Saut de ligne, césure et justification par langue.  
  
<a name="Enhanced_Font_Support"></a>   
## Prise en charge de police améliorée  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] offre une prise en charge de police améliorée en fournissant les fonctionnalités suivantes :  
  
-   Unicode pour tout texte.  La sélection et le comportement de la police ne requièrent plus de jeu de caractères ou de page de codes.  
  
-   Comportement de police indépendant des paramètres globaux, tels que les paramètres régionaux du système.  
  
-   Types <xref:System.Windows.FontWeight>, <xref:System.Windows.FontStretch> et <xref:System.Windows.FontStyle> distincts pour définir un <xref:System.Windows.Media.FontFamily>.  Cette fonctionnalité offre une souplesse plus importante que dans la programmation [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)], dans laquelle des combinaisons Boolean italique et gras sont utilisées pour définir une famille de polices.  
  
-   Sens d'écriture \(horizontal ou vertical\) géré indépendamment du nom de police.  
  
-   Police de liaison et police de substitution dans un fichier [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] portable, à l'aide de la technologie de police composite.  Les polices composites permettent de générer une gamme complète de polices multilingues.  Les polices composites fournissent également un mécanisme qui évite d'afficher les glyphes manquants.  Pour plus d'informations, consultez les notes dans la classe <xref:System.Windows.Media.FontFamily>.  
  
-   Polices internationales générées à partir de polices composites, à l'aide d'un groupe de polices d'une seule langue.  Cela permet de limiter les coûts de ressources lors du développement de polices pour plusieurs langues.  
  
-   Polices composites incorporées dans un document, autorisant ainsi la portabilité du document.  Pour plus d'informations, consultez les notes dans la classe <xref:System.Windows.Media.FontFamily>.  
  
<a name="New_Text_APIs"></a>   
## Nouvelles interfaces de programmation d'applications \(API\) textes  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fournit plusieurs [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] textes que les développeurs doivent utiliser lorsqu'ils incluent du texte dans leurs applications.  Ces [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] sont groupées dans trois catégories :  
  
-   **Disposition et interface utilisateur**.  Les contrôles de texte courants pour l'[!INCLUDE[TLA#tla_gui](../../../../includes/tlasharptla-gui-md.md)].  
  
-   **Dessin de texte léger**.  Permet de dessiner du texte directement sur des objets.  
  
-   **Mise en forme du texte avancée**.  Permet d'implémenter un moteur de texte personnalisé.  
  
### Disposition et interface utilisateur  
 Au niveau de fonctionnalités le plus élevé, les [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] textes fournissent des contrôles d'[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] courants tels que <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.TextBlock> et <xref:System.Windows.Controls.TextBox>.  Ces contrôles fournissent les éléments d'[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] de base dans une application et proposent une méthode simple pour présenter et interagir avec le texte.  Les contrôles tels que <xref:System.Windows.Controls.RichTextBox> et <xref:System.Windows.Controls.PasswordBox> permettent une gestion du texte plus avancée ou spécialisée.  Les classes telles que <xref:System.Windows.Documents.TextRange>, <xref:System.Windows.Documents.TextSelection> et <xref:System.Windows.Documents.TextPointer> permettent une manipulation utile du texte.  Ces contrôles d'[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] fournissent des propriétés telles que <xref:System.Windows.Controls.Control.FontFamily%2A>, <xref:System.Windows.Controls.Control.FontSize%2A> et <xref:System.Windows.Controls.Control.FontStyle%2A> qui vous permettent de contrôler la police utilisée pour rendre le texte.  
  
#### Utilisation d'effets bitmap, de transformations et d'effets de texte  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vous permet de créer des utilisations visuellement intéressantes de texte via des fonctionnalités d'utilisation telles que les effets bitmap, les transformations et les effets de texte.  L'exemple suivant présente un type classique d'effet d'ombre portée appliqué au texte.  
  
 ![Ombre du texte avec adoucissement &#61; 0,25](../../../../docs/framework/wpf/advanced/media/shadowtext01.png "ShadowText01")  
Texte avec ombre portée  
  
 L'exemple suivant présente un effet d'ombre portée et un bruit appliqués au texte.  
  
 ![Ombre du texte avec bruit](../../../../docs/framework/wpf/advanced/media/shadowtext04.png "ShadowText04")  
Texte avec ombre portée et bruit  
  
 L'exemple suivant présente un effet de lumière externe appliqué au texte.  
  
 ![Ombre du texte utilisant OuterGlowBitmapEffect](../../../../docs/framework/wpf/advanced/media/shadowtext05.png "ShadowText05")  
Texte avec effet de lumière externe  
  
 L'exemple suivant présente un effet flou appliqué au texte.  
  
 ![Ombre du texte utilisant BlurBitmapEffect](../../../../docs/framework/wpf/advanced/media/shadowtext06.png "ShadowText06")  
Texte avec effet flou  
  
 Dans l'exemple suivant, la deuxième ligne du texte est mise à l'échelle par 150 % le long de l'axe x et la troisième ligne du texte est mise à l'échelle par 150 % le long de l'axe y.  
  
 ![Texte mis à l'échelle à l'aide de ScaleTransform](../../../../docs/framework/wpf/advanced/media/transformedtext02.png "TransformedText02")  
Texte avec ScaleTransform  
  
 L'exemple suivant présente le texte incliné le long de l'axe x.  
  
 ![Texte incliné à l'aide de SkewTransform](../../../../docs/framework/wpf/advanced/media/transformedtext03.png "TransformedText03")  
Texte avec SkewTransform  
  
 Un objet <xref:System.Windows.Media.TextEffect> est un objet d'assistance qui vous permet de traiter le texte comme un ou plusieurs groupes de caractères dans une chaîne de texte.  L'exemple suivant montre un caractère individuel qui fait l'objet d'une rotation.  Chaque caractère fait indépendamment l'objet d'une rotation à intervalles d'une seconde.  
  
 ![Capture d'écran : effet de rotation du texte](../../../../docs/framework/wpf/advanced/media/texteffect01.png "TextEffect01")  
Exemple d'animation d'un effet de texte rotatif  
  
#### Utilisation de documents dynamiques  
 Outre les contrôles d'[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] courants, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] offre un contrôle de disposition pour la présentation de texte : l'élément <xref:System.Windows.Documents.FlowDocument>.  L'élément <xref:System.Windows.Documents.FlowDocument>, conjointement à l'élément <xref:System.Windows.Controls.DocumentViewer>, fournit un contrôle pour les grandes quantités de texte avec diverses spécifications de disposition.  Les contrôles de disposition donnent accès à une typographie avancée via l'objet <xref:System.Windows.Documents.Typography> et les propriétés de police d'autres contrôles d'[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  
  
 L'exemple suivant présente le contenu de texte hébergé dans un <xref:System.Windows.Controls.FlowDocumentReader>, offrant une prise en charge de la recherche, de la navigation, de la pagination et de la mise à l'échelle du contenu.  
  
 ![Exemple de capture d'écran : utilisation des polices OpenType](../../../../docs/framework/wpf/advanced/media/typographyinwpf-03.png "TypographyInWPF\_03")  
Texte hébergé dans un FlowDocumentReader  
  
 Pour plus d'informations, consultez [Documents dans WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md).  
  
### Dessin de texte léger  
 Vous pouvez dessiner du texte directement sur des objets [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] en utilisant la méthode <xref:System.Windows.Media.DrawingContext.DrawText%2A> de l'objet <xref:System.Windows.Media.DrawingContext>.  Pour utiliser cette méthode, vous créez un objet <xref:System.Windows.Media.FormattedText>.  Cet objet vous permet de dessiner un texte multiligne dans lequel chaque caractère du texte peut être mis en forme individuellement.  Les fonctionnalités de l'objet <xref:System.Windows.Media.FormattedText> contiennent la plupart des fonctionnalités des indicateurs DrawText dans l'API Win32.  De plus, l'objet <xref:System.Windows.Media.FormattedText> contient des fonctionnalités telles que la prise en charge des points de suspension qui s'affichent lorsque le texte dépasse les limites.  L'exemple suivant présente un texte auquel plusieurs formats sont appliqués, notamment un dégradé linéaire sur les deuxième et troisième mots.  
  
 ![Texte affiché à l'aide de l'objet FormattedText](../../../../docs/framework/wpf/advanced/media/formattedtext01.png "FormattedText01")  
Texte affiché à l'aide d'un objet FormattedText  
  
 Vous pouvez convertir le texte mis en forme en objets <xref:System.Windows.Media.Geometry>, ce qui vous permet de créer d'autres types de texte présentant un intérêt visuel.  Par exemple, vous pouvez créer un objet <xref:System.Windows.Media.Geometry> basé sur le contour d'une chaîne de texte.  
  
 ![Contour du texte utilisant un pinceau de dégradé linéaire](../../../../docs/framework/wpf/advanced/media/outlinedtext02.png "OutlinedText02")  
Contour du texte à l'aide d'un pinceau à dégradé linéaire  
  
 Les exemples suivants illustrent plusieurs façons de créer des effets visuels intéressants en modifiant le trait, le remplissage et la surbrillance du texte converti.  
  
 ![Texte avec différentes couleurs de trait et de remplissage](../../../../docs/framework/wpf/advanced/media/outlinedtext03.png "OutlinedText03")  
Exemple de définition du trait et du remplissage de différentes couleurs  
  
 ![Texte avec pinceau image appliqué au trait](../../../../docs/framework/wpf/advanced/media/outlinedtext04.png "OutlinedText04")  
Exemple de pinceau image appliqué au trait  
  
 ![Texte avec pinceau image appliqué au trait](../../../../docs/framework/wpf/advanced/media/outlinedtext05.png "OutlinedText05")  
Exemple de pinceau image appliqué au trait et surbrillance  
  
 Pour plus d'informations sur l'objet <xref:System.Windows.Media.FormattedText>, consultez [Dessin du texte mis en forme](../../../../docs/framework/wpf/advanced/drawing-formatted-text.md)  
  
### Mise en forme de texte avancée  
 Au niveau le plus avancé des [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] textes, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vous offre la possibilité de créer une disposition de texte personnalisée en utilisant l'objet <xref:System.Windows.Media.TextFormatting.TextFormatter> et d'autres types dans l'espace de noms <xref:System.Windows.Media.TextFormatting>.  <xref:System.Windows.Media.TextFormatting.TextFormatter> et les classes associées vous permettent d'implémenter la disposition de texte personnalisée qui prend en charge votre propre définition des formats de caractère, styles de paragraphe, règles du saut de ligne et d'autres fonctionnalités de disposition pour le texte international.  Rares sont les cas dans lesquels vous souhaiterez substituer l'implémentation par défaut de la prise en charge de la disposition du texte [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  Toutefois, si vous créez une application ou un contrôle d'édition de texte, vous aurez peut\-être besoin d'une implémentation différente de l'implémentation [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] par défaut.  
  
 Contrairement à une [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] texte traditionnelle, le <xref:System.Windows.Media.TextFormatting.TextFormatter> interagit avec le client de disposition de texte par l'intermédiaire d'un ensemble de méthodes de rappel.  Cela suppose que le client fournisse ces méthodes dans une implémentation de la classe <xref:System.Windows.Media.TextFormatting.TextSource>.  Le diagramme suivant montre l'interaction de la disposition du texte entre l'application cliente et <xref:System.Windows.Media.TextFormatting.TextFormatter>.  
  
 ![Diagramme du client de disposition du texte et TextFormatter](../../../../docs/framework/wpf/advanced/media/textformatter01.png "TextFormatter01")  
Interaction entre l'application et TextFormatter  
  
 Pour plus d'informations sur la création de la disposition de texte personnalisée, consultez [Mise en forme de texte avancée](../../../../docs/framework/wpf/advanced/advanced-text-formatting.md).  
  
## Voir aussi  
 <xref:System.Windows.Media.FormattedText>   
 <xref:System.Windows.Media.TextFormatting.TextFormatter>   
 [Vue d'ensemble de ClearType](../../../../docs/framework/wpf/advanced/cleartype-overview.md)   
 [Fonctionnalités des polices OpenType](../../../../docs/framework/wpf/advanced/opentype-font-features.md)   
 [Dessin du texte mis en forme](../../../../docs/framework/wpf/advanced/drawing-formatted-text.md)   
 [Mise en forme de texte avancée](../../../../docs/framework/wpf/advanced/advanced-text-formatting.md)   
 [Text](../../../../docs/framework/wpf/advanced/optimizing-performance-text.md)   
 [Typographie Microsoft \(page éventuellement en anglais\)](http://www.microsoft.com/typography/default.mspx)