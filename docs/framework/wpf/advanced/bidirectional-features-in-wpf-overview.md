---
title: "Vue d'ensemble des fonctionnalités bidirectionnelles dans WPF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Span elements [WPF]
- bidirectional features [WPF]
ms.assetid: fd850e25-7dba-408c-b521-8873e51dc968
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b50d98d5f02a59a013d7577f0e312e6ffde35690
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="bidirectional-features-in-wpf-overview"></a>Vue d'ensemble des fonctionnalités bidirectionnelles dans WPF
Contrairement à d’autres plateformes de développement, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] propose de nombreuses fonctionnalités qui prennent en charge le développement rapide de contenu bidirectionnel, par exemple, mixte de gauche à droite et de droite à gauche des données dans le même document. En même temps, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] crée une excellente expérience pour les utilisateurs qui ont besoin de fonctionnalités bidirectionnelles tels que les utilisateurs de langue arabe et hébreu.  
  
 Les sections suivantes expliquent de nombreuses fonctionnalités bidirectionnelles, accompagnées d’exemples qui illustrent comment réaliser le meilleur affichage de contenu bidirectionnel. La plupart des exemples utilisent [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)], même si vous pouvez facilement appliquer les concepts à [!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)] ou [!INCLUDE[TLA#tla_visualb](../../../../includes/tlasharptla-visualb-md.md)] code.  
  

  
<a name="FlowDirection"></a>   
## <a name="flowdirection"></a>FlowDirection  
 La propriété de base qui définit le sens du flux de contenu dans un [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application est <xref:System.Windows.FrameworkElement.FlowDirection%2A>. Cette propriété peut être définie à une des deux valeurs d’énumération <xref:System.Windows.FlowDirection.LeftToRight> ou <xref:System.Windows.FlowDirection.RightToLeft>. La propriété est disponible à tous les [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] les éléments qui héritent de <xref:System.Windows.FrameworkElement>.  
  
 Les exemples suivants définissent le sens du flux d’un <xref:System.Windows.Controls.TextBox> élément.  
  
 **Sens de déroulement de gauche à droite**  
  
 [!code-xaml[LTRRTL#LTR](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LTRRTL/CS/Pane1.xaml#ltr)]  
  
 **Sens de déroulement de droite à gauche**  
  
 [!code-xaml[LTRRTL#RTL](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LTRRTL/CS/Pane1.xaml#rtl)]  
  
 Le graphique suivant montre le rendu généré par le code précédent.  
  
 **Graphique illustrant FlowDirection**  
  
 ![Alignement TextBlock](../../../../docs/framework/wpf/advanced/media/lefttorightrighttoleft.PNG "LefttoRightRighttoLeft")  
  
 Un élément dans un [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] arborescence héritent le <xref:System.Windows.FrameworkElement.FlowDirection%2A> à partir de son conteneur. Dans l’exemple suivant, la <xref:System.Windows.Controls.TextBlock> se trouve dans un <xref:System.Windows.Controls.Grid>, qui réside dans un <xref:System.Windows.Window>. Définition de la <xref:System.Windows.FrameworkElement.FlowDirection%2A> pour le <xref:System.Windows.Window> implique de le définir pour le <xref:System.Windows.Controls.Grid> et <xref:System.Windows.Controls.TextBlock> ainsi.  
  
 L’exemple suivant illustre la définition <xref:System.Windows.FrameworkElement.FlowDirection%2A>.  
  
 [!code-xaml[FlowDirection#FlowDirection](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDirection/CS/Window1.xaml#flowdirection)]  
  
 Le niveau supérieur <xref:System.Windows.Window> a un <xref:System.Windows.FlowDirection.RightToLeft> <xref:System.Windows.FlowDirection>, de sorte que tous les éléments contenus dans celui-ci héritent également le même <xref:System.Windows.FrameworkElement.FlowDirection%2A>. Pour un élément à remplacer spécifié <xref:System.Windows.FrameworkElement.FlowDirection%2A> il doit ajouter une modification de sens explicite, comme le deuxième <xref:System.Windows.Controls.TextBlock> dans l’exemple précédent qui le modifie en <xref:System.Windows.FlowDirection.LeftToRight>. Lorsqu’aucun <xref:System.Windows.FrameworkElement.FlowDirection%2A> est défini, la valeur par défaut <xref:System.Windows.FlowDirection.LeftToRight> s’applique.  
  
 Le graphique suivant montre la sortie produite par l’exemple précédent.  
  
 **Graphique illustrant FlowDirection assigné explicitement**  
  
 ![Illustration du sens du déroulement](../../../../docs/framework/wpf/advanced/media/flowdir.PNG "FlowDir")  
  
<a name="FlowDocument"></a>   
## <a name="flowdocument"></a>FlowDocument  
 Comme de nombreuses plateformes de développement [!INCLUDE[TLA#tla_html](../../../../includes/tlasharptla-html-md.md)], [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] et Java fournissent la prise en charge spéciale pour le développement de contenu bidirectionnel. Les langages de balisage, tels que [!INCLUDE[TLA#tla_html](../../../../includes/tlasharptla-html-md.md)] aux rédacteurs de contenu le balisage nécessaire pour afficher du texte dans n’importe quelle direction requise, par exemple le [!INCLUDE[TLA#tla_html](../../../../includes/tlasharptla-html-md.md)] 4.0 balise, « dir » qui prend les valeurs « rtl » ou « ltr ». Cette balise est similaire à la <xref:System.Windows.FrameworkElement.FlowDirection%2A> propriété, mais la <xref:System.Windows.FrameworkElement.FlowDirection%2A> propriété fonctionne de façon plus avancée à la disposition de contenu textuel et peut être utilisée pour le contenu autre que du texte.  
  
 Dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], un <xref:System.Windows.Documents.FlowDocument> est un flexible [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] élément qui peut héberger une combinaison de texte, des tables, des images et autres éléments. Les exemples des sections suivantes utilisent cet élément.  
  
 Ajout de texte à un <xref:System.Windows.Documents.FlowDocument> peut être effectuée de plusieurs façons. Un moyen simple de le faire s’effectue via un <xref:System.Windows.Documents.Paragraph> qui est un élément de niveau bloc utilisé pour grouper du contenu tel que le texte. Pour ajouter du texte aux éléments inclus, les exemples utilisent <xref:System.Windows.Documents.Span> et <xref:System.Windows.Documents.Run>. <xref:System.Windows.Documents.Span>est un élément de contenu de flux inline utilisé pour regrouper d’autres éléments inclus, pendant un <xref:System.Windows.Documents.Run> est un flux inline contenu élément destiné à contenir une séquence de texte non formaté. A <xref:System.Windows.Documents.Span> peut contenir plusieurs <xref:System.Windows.Documents.Run> éléments.  
  
 Le premier exemple de document contient un document qui possède un numéro de réseau de partager des noms ; par exemple `\\server1\folder\file.ext`. Que ce lien réseau soit dans un document en arabe ou en anglais, vous souhaiterez toujours qu’il apparaisse de la même façon. Le graphique suivant montre le lien dans un arabe <xref:System.Windows.FlowDirection.RightToLeft> document.  
  
 **Graphique illustrant l’utilisation de l’élément Span**  
  
 ![Document se déroulant de droite à gauche](../../../../docs/framework/wpf/advanced/media/flowdocument.PNG "FlowDocument")  
  
 Car le texte est <xref:System.Windows.FlowDirection.RightToLeft>particulières de tous les caractères, tels que le «\\», décomposer le texte dans un droit d’ordre de gauche. Qui résulte dans le lien n’est ne pas affiché dans le bon ordre, par conséquent, pour résoudre le problème, le texte doit être incorporé afin de conserver un distinct <xref:System.Windows.Documents.Run> circuler <xref:System.Windows.FlowDirection.LeftToRight>. Au lieu d’avoir un distinct <xref:System.Windows.Documents.Run> pour chaque langue, un meilleur moyen de résoudre le problème est d’incorporer le texte anglais moins fréquemment utilisé dans une plus grande arabe <xref:System.Windows.Documents.Span>.  
  
 C’est ce que montre le graphique ci-après.  
  
 **Graphique illustrant l’utilisation d’un élément Run incorporé dans un élément Span**  
  
 ![Capture d’écran XamlPad](../../../../docs/framework/wpf/advanced/media/runspan.PNG "RunSpan")  
  
 L’exemple suivant montre comment utiliser <xref:System.Windows.Documents.Run> et <xref:System.Windows.Documents.Span> les éléments dans les documents.  
  
 [!code-xaml[RunSpan#RunSpan](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RunSpan/CS/Window1.xaml#runspan)]  
  
<a name="SpanElements"></a>   
## <a name="span-elements"></a>Éléments Span  
 Le <xref:System.Windows.Documents.Span> élément fonctionne comme une limite qui sépare les textes avec directions de flux différentes.  Même <xref:System.Windows.Documents.Span> éléments avec la même direction de flux sont considérés comme des étendues différentes bidirectionnel ce qui signifie que la <xref:System.Windows.Documents.Span> éléments sont classés dans le conteneur <xref:System.Windows.FlowDirection>, uniquement le contenu dans le <xref:System.Windows.Documents.Span> élément suit la <xref:System.Windows.FlowDirection> de la <xref:System.Windows.Documents.Span>.  
  
 L’illustration suivante montre le sens du flux de plusieurs <xref:System.Windows.Controls.TextBlock> éléments.  
  
 **Graphique illustrant FlowDirection dans plusieurs éléments TextBlock**  
  
 ![Blocs de texte avec directions de flux différentes](../../../../docs/framework/wpf/advanced/media/span.PNG "Span")  
  
 L’exemple suivant montre comment utiliser le <xref:System.Windows.Documents.Span> et <xref:System.Windows.Documents.Run> éléments à produire les résultats présentés dans le graphique précédent.  
  
 [!code-xaml[Span#Span](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Span/CS/Window1.xaml#span)]  
  
 Dans le <xref:System.Windows.Controls.TextBlock> éléments dans l’exemple, le <xref:System.Windows.Documents.Span> éléments sont disposés selon le <xref:System.Windows.FlowDirection> de leurs parents, mais le texte au sein de chaque <xref:System.Windows.Documents.Span> élément se déroule dans son propre <xref:System.Windows.FlowDirection>. Ceci s’applique au latin et à l’arabe ou à toute autre langue.  
  
### <a name="adding-xmllang"></a>Ajout de xml:lang  
 L’illustration suivante montre un autre exemple qui utilise des nombres et des expressions arithmétiques, tel que `"200.0+21.4=221.4"`. Notez que seuls les <xref:System.Windows.FlowDirection> est définie.  
  
 **Graphique affichant des nombres en utilisant uniquement FlowDirection**  
  
 ![Nombres se déroulant de droite à gauche](../../../../docs/framework/wpf/advanced/media/langattribute.PNG "LangAttribute")  
  
 Les utilisateurs de cette application seront déçus par la sortie, même si le <xref:System.Windows.FlowDirection> est correct, les nombres ne sont pas formés comme chiffres arabes doivent être.  
  
 Les éléments XAML peuvent inclure un [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] attribut (`xml:lang`) qui définit la langue de chaque élément. XAML prend également en charge un [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] principe de langue dans laquelle `xml:lang` appliqués à des éléments parents dans l’arborescence de valeurs sont utilisées par les éléments enfants. Dans l’exemple précédent, car un autre langage n’a pas été défini pour le <xref:System.Windows.Documents.Run> élément ou l’un de ses haut niveau des éléments, la valeur par défaut `xml:lang` a été utilisé, qui est `en-US` pour XAML. L’algorithme de mise en forme numéro interne de [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] sélectionne les nombres dans la langue correspondante, dans ce cas l’anglais. Pour rendre l’arabe correcte des numéros de rendu `xml:lang` doit être définie.  
  
 L’illustration suivante montre l’exemple avec `xml:lang` ajouté.  
  
 **Graphique illustrant l’utilisation de l’attribut xml:lang**  
  
 ![Chiffres arabes se déroulant de droite à gauche](../../../../docs/framework/wpf/advanced/media/langattribute2.PNG "LangAttribute2")  
  
 L’exemple suivant ajoute `xml:lang` à l’application.  
  
 [!code-xaml[LangAttribute#LangAttribute](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LangAttribute/CS/Window1.xaml#langattribute)]  
  
 Sachez que pour de nombreuses langues différentes `xml:lang` valeurs en fonction de la région ciblée, par exemple, `"ar-SA"` et `"ar-EG"` représentent deux variantes de l’arabe. Les exemples précédents montrent que vous devez définir les deux le `xml:lang` et <xref:System.Windows.FlowDirection> valeurs.  
  
<a name="FlowDirectionNontext"></a>   
## <a name="flowdirection-with-non-text-elements"></a>FlowDirection avec des éléments autres que textuels  
 <xref:System.Windows.FlowDirection>définit non seulement le texte dans un élément textuel, mais également le sens du flux de presque toutes les autres [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] élément. Le graphique suivant illustre un <xref:System.Windows.Controls.ToolBar> qui utilise une horizontale <xref:System.Windows.Media.LinearGradientBrush> pour dessiner son arrière-plan.  
  
 **Graphique montrant une barre d’outils avec un dégradé de gauche à droite**  
  
 ![Capture d’écran dégradée](../../../../docs/framework/wpf/advanced/media/gradient.PNG "Gradient")  
  
 Après avoir défini la <xref:System.Windows.FlowDirection> à <xref:System.Windows.FlowDirection.RightToLeft>, non seulement la <xref:System.Windows.Controls.ToolBar> boutons sont disposés de droite à gauche, mais <xref:System.Windows.Media.LinearGradientBrush> aligne ses offsets pour le flux de droite à gauche.  
  
 Le graphique suivant illustre le réalignement de le <xref:System.Windows.Media.LinearGradientBrush>.  
  
 **Graphique montrant une barre d’outils avec un dégradé de droite à gauche**  
  
 ![Dégradé de droite à gauche](../../../../docs/framework/wpf/advanced/media/gradient2-wpf.PNG "Gradient2_WPF")  
  
 L’exemple suivant dessine une <xref:System.Windows.FlowDirection.RightToLeft> <xref:System.Windows.Controls.ToolBar>. (Pour dessiner de gauche à droite, supprimez le <xref:System.Windows.FlowDirection> de l’attribut le <xref:System.Windows.Controls.ToolBar>.  
  
 [!code-xaml[Gradient#Gradient](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Gradient/CS/Window1.xaml#gradient)]  
  
<a name="FlowDirectionExceptions"></a>   
### <a name="flowdirection-exceptions"></a>Exceptions de FlowDirection  
 Il existe quelques cas où <xref:System.Windows.FlowDirection> ne se comporte pas comme prévu. Cette section décrit deux de ces exceptions.  
  
 **Image**  
  
 Un <xref:System.Windows.Controls.Image> représente un contrôle qui affiche une image. Dans [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] il peut être utilisé avec un <xref:System.Windows.Controls.Image.Source%2A> propriété qui définit les [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] de la <xref:System.Windows.Controls.Image> à afficher.  
  
 Contrairement à d’autres [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] éléments, un <xref:System.Windows.Controls.Image> n’hérite pas les <xref:System.Windows.FlowDirection> à partir du conteneur. Toutefois, si le <xref:System.Windows.FlowDirection> est défini explicitement à <xref:System.Windows.FlowDirection.RightToLeft>, un <xref:System.Windows.Controls.Image> s’affiche retournée horizontalement. Cette implémentation est une fonctionnalité pratique pour les développeurs de contenu bidirectionnel, car dans certains cas, le fait de retourner l’image horizontalement produit l’effet recherché.  
  
 L’illustration suivante montre un renversée <xref:System.Windows.Controls.Image>.  
  
 **Graphique illustrant une image retournée**  
  
 ![Capture d’écran XamlPad](../../../../docs/framework/wpf/advanced/media/image.PNG "Image")  
  
 L’exemple suivant montre que le <xref:System.Windows.Controls.Image> ne parvient pas à hériter le <xref:System.Windows.FlowDirection> à partir de la <xref:System.Windows.Controls.StackPanel> qui le contient. **Remarque** vous devez disposer d’un fichier nommé **ms_logo.jpg** sur votre lecteur C:\ pour exécuter cet exemple.  
  
 [!code-xaml[Image#Image](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Image/CS/Window1.xaml#image)]  
  
 **Remarque** inclus dans les fichiers de téléchargement est un **ms_logo.jpg** fichier. Le code suppose que le fichier .jpg n’est pas à l’intérieur de votre projet mais quelque part sur le lecteur C:\. Vous devez copier le fichier .jpg depuis les fichiers de projet vers votre lecteur C:\ ou modifier le code pour qu’il recherche le fichier à l’intérieur du projet. Pour ce faire, modifiez `Source="file://c:/ms_logo.jpg"` à `Source="ms_logo.jpg"`.  
  
 **Tracés**  
  
 Outre une <xref:System.Windows.Controls.Image>, un autre élément intéressant est <xref:System.Windows.Shapes.Path>. Un tracé est un objet qui peut dessiner une série de lignes et de courbes reliées. Il se comporte de manière très similaire à une <xref:System.Windows.Controls.Image> concernant son <xref:System.Windows.FlowDirection>, par exemple son <xref:System.Windows.FlowDirection.RightToLeft> <xref:System.Windows.FlowDirection> est un miroir horizontal de son <xref:System.Windows.FlowDirection.LeftToRight> une. Cependant, contrairement à un <xref:System.Windows.Controls.Image>, <xref:System.Windows.Shapes.Path> hérite son <xref:System.Windows.FlowDirection> à partir du conteneur et il est inutile de spécifier explicitement.  
  
 L’exemple suivant dessine une flèche simple à l’aide de 3 lignes. La première flèche hérite le <xref:System.Windows.FlowDirection.RightToLeft> direction de flux le <xref:System.Windows.Controls.StackPanel> afin que son démarrage et les points de terminaison sont mesurés à partir d’une racine sur le côté droit. La deuxième flèche qui a un explicite <xref:System.Windows.FlowDirection.RightToLeft> <xref:System.Windows.FlowDirection> démarre également sur le côté droit. Cependant, la troisième flèche a sa racine de début située sur le côté gauche. Pour plus d’informations sur le dessin, consultez <xref:System.Windows.Media.LineGeometry> et <xref:System.Windows.Media.GeometryGroup>.  
  
 [!code-xaml[Paths#Paths](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Paths/CS/Window1.xaml#paths)]  
  
 Le graphique suivant montre la sortie produite par l’exemple précédent.  
  
 **Graphique illustrant des flèches dessinées à l’aide de l’élément Path**  
  
 ![Chemins d’accès](../../../../docs/framework/wpf/advanced/media/paths.PNG "Paths")  
  
 Le <xref:System.Windows.Controls.Image> et <xref:System.Windows.Shapes.Path> sont deux exemples de la façon dont [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] utilise <xref:System.Windows.FlowDirection>. En regard de la disposition de [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] éléments selon une orientation spécifique dans un conteneur, <xref:System.Windows.FlowDirection> peut être utilisée avec des éléments tels que <xref:System.Windows.Controls.InkPresenter> qui restitue l’encre sur une surface, <xref:System.Windows.Media.LinearGradientBrush>, <xref:System.Windows.Media.RadialGradientBrush>. Chaque fois que vous avez besoin d’un comportement de droite à gauche de votre contenu qui reproduit un comportement de gauche à droite, ou vice versa, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] fournit cette fonctionnalité.  
  
<a name="NumberSubstitution"></a>   
## <a name="number-substitution"></a>Substitution de nombres  
 Historiquement, [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] a pris en charge la substitution de nombres en permettant la représentation sous forme de différentes formes de culturels pour les chiffres de mêmes, tout en conservant le stockage interne de ces chiffres unifié entre les différents paramètres régionaux, des nombres sont stockées dans leurs bien connu des valeurs hexadécimales, 0 x 40, 0 x 41, selon la langue sélectionnée.  
  
 Ceci a permis aux applications de traiter les valeurs numériques sans avoir besoin de les convertir d’une langue à l’autre, par exemple un utilisateur peut ouvrir une [!INCLUDE[TLA#tla_xl](../../../../includes/tlasharptla-xl-md.md)] feuille de calcul dans un arabe localisé [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] et afficher les numéros de mise en forme en chiffres arabes, mais l’ouvrir dans une version européenne du [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] et afficher une représentation européenne de nombres même. Ceci est également nécessaire pour les autres symboles tels que les virgules et le symbole du pourcentage, car ils accompagnent habituellement des nombres dans le même document.  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] continue dans la même tradition et ajoute une prise en charge supplémentaire de cette fonctionnalité qui permet un meilleur contrôle de l’utilisateur sur quand et comment la substitution est utilisée. Bien que cette fonctionnalité soit conçue pour n’importe quelle langue, elle est particulièrement utile pour du contenu bidirectionnel, où la mise en forme des chiffres pour une langue spécifique est habituellement un défi pour les développeurs d’application du fait des différentes cultures dans lesquelles peut s’exécuter l’application.  
  
 La principale propriété qui contrôle la substitution de nombres comment fonctionne dans [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] est le <xref:System.Windows.Media.NumberSubstitution.Substitution%2A> propriété de dépendance. La <xref:System.Windows.Media.NumberSubstitution> classe spécifie la façon dont les nombres dans le texte à afficher. Elle a trois propriétés publiques qui définissent son comportement. Voici un résumé de chacune des propriétés.  
  
 **CultureSource :**  
  
 Cette propriété spécifie la manière dont est déterminée la culture pour les nombres. Elle prend l’une des trois <xref:System.Windows.Media.NumberCultureSource> valeurs d’énumération.  
  
-   Override : La culture pour les nombres est celle de <xref:System.Windows.Media.NumberSubstitution.CultureOverride%2A> propriété.  
  
-   Text : la culture pour les nombres est la culture de l’exécution de texte. Dans le balisage, ceci serait `xml:lang`, ou son alias `Language` propriété (<xref:System.Windows.FrameworkElement.Language%2A> ou <xref:System.Windows.FrameworkContentElement.Language%2A>). En outre, il est la valeur par défaut pour les classes qui dérivent de <xref:System.Windows.FrameworkContentElement>. Ces classes incluent <xref:System.Windows.Documents.Paragraph?displayProperty=nameWithType>, <xref:System.Windows.Documents.Table?displayProperty=nameWithType>, <xref:System.Windows.Documents.TableCell?displayProperty=nameWithType> et ainsi de suite.  
  
-   User : la culture pour les nombres est la culture du thread actuel. Cette propriété est la valeur par défaut pour toutes les sous-classes de <xref:System.Windows.FrameworkElement> comme <xref:System.Windows.Controls.Page>, <xref:System.Windows.Window> et <xref:System.Windows.Controls.TextBlock>.  
  
 **CultureOverride** :  
  
 Le <xref:System.Windows.Media.NumberSubstitution.CultureOverride%2A> propriété est utilisée uniquement si le <xref:System.Windows.Media.NumberSubstitution.CultureSource%2A> est définie sur <xref:System.Windows.Media.NumberCultureSource.Override> et est ignorée dans le cas contraire. Elle spécifie la culture pour les nombres. La valeur `null`, la valeur par défaut, est interprétée en tant qu’en-US.  
  
 **Substitution** :  
  
 Cette propriété spécifie le type de substitution de nombres à effectuer. Elle prend l’une des opérations suivantes <xref:System.Windows.Media.NumberSubstitutionMethod> valeurs d’énumération.  
  
-   <xref:System.Windows.Media.NumberSubstitutionMethod.AsCulture>: La méthode de substitution est déterminée en fonction de la culture des nombres <xref:System.Globalization.NumberFormatInfo.DigitSubstitution%2A?displayProperty=nameWithType> propriété. Il s'agit de la valeur par défaut.  
  
-   <xref:System.Windows.Media.NumberSubstitutionMethod.Context>: Si la culture des nombres est une culture arabe ou PERSANE, il spécifie que les chiffres dépendent du contexte.  
  
-   <xref:System.Windows.Media.NumberSubstitutionMethod.European>: Les nombres sont toujours rendus en tant que chiffres européens.  
  
-   <xref:System.Windows.Media.NumberSubstitutionMethod.NativeNational>: Les nombres sont restitués à l’aide des chiffres nationaux pour la culture des nombres, comme spécifié par la culture <xref:System.Globalization.CultureInfo.NumberFormat%2A>.  
  
-   <xref:System.Windows.Media.NumberSubstitutionMethod.Traditional>: Les nombres sont rendus avec les chiffres traditionnels pour la culture des nombres. Pour la plupart des cultures, cela équivaut à <xref:System.Windows.Media.NumberSubstitutionMethod.NativeNational>. Toutefois, <xref:System.Windows.Media.NumberSubstitutionMethod.NativeNational> entraîne des chiffres latins pour certaines cultures arabes, tandis que cette valeur produit des chiffres arabes pour toutes les cultures arabes.  
  
 Que signifient ces valeurs pour un développeur de contenu bidirectionnel ? Dans la plupart des cas, le développeur peut doit uniquement définir <xref:System.Windows.FlowDirection> et la langue de chaque texte [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] élément, par exemple `Language="ar-SA"` et <xref:System.Windows.Media.NumberSubstitution> logique prend en charge d’afficher les nombres en fonction de la bonne [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. L’exemple suivant illustre l’utilisation de nombres arabes et anglais dans une [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] application qui s’exécute sur une version arabe de [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)].  
  
 [!code-xaml[Numbers#Numbers](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Numbers/CS/Window1.xaml#numbers)]  
  
 Le graphique suivant montre la sortie de l’exemple précédent, si vous exécutez sur une version arabe de [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)].  
  
 **Graphique montrant l’affichage de nombres arabes et anglais**  
  
 ![Capture d’écran XamlPad avec numéros](../../../../docs/framework/wpf/advanced/media/numbers.PNG "Numbers")  
  
 Le <xref:System.Windows.FlowDirection> était important dans ce cas, car la définition de la <xref:System.Windows.FlowDirection> à <xref:System.Windows.FlowDirection.LeftToRight> à la place aurait produit des chiffres européens. Les sections suivantes expliquent comment obtenir un affichage unifié des chiffres dans l’ensemble de votre document. Si cet exemple ne s’exécute pas sur une version arabe de Windows, tous les chiffres sont affichés en tant que chiffres européens.  
  
 **Définition des règles de substitution**  
  
 Dans une application réelle, il est possible que vous ayez besoin de définir la langue par programmation. Par exemple, vous souhaitez définir la `xml:lang` attribut est le même que celui utilisé par le système [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], ou peut-être modifier la langue en fonction de l’état de l’application.  
  
 Si vous souhaitez apporter en fonction de modifications sur l’état de l’application, utilisez d’autres fonctionnalités fournies par [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  
  
 Tout d’abord, définissez le composant d’application `NumberSubstitution.CultureSource="Text"`. À l’aide de ce paramètre permet de s’assurer que les paramètres ne proviennent pas du [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] pour les éléments de texte qui ont « User » en tant que la valeur par défaut, tel que <xref:System.Windows.Controls.TextBlock>.  
  
 Exemple :  
  
||  
|-|  
|`<TextBlock`<br /><br /> `Name="text1" NumberSubstitution.CultureSource="Text">`<br /><br /> `1234+5679=6913`<br /><br /> `</TextBlock>`|  
  
 Dans le [!INCLUDE[TLA2#tla_lhcshrp](../../../../includes/tla2sharptla-lhcshrp-md.md)] de code, définissez la `Language` propriété, par exemple, pour `"ar-SA"`.  
  
||  
|-|  
|`text1.Language =`<br /><br /> `System.Windows.Markup.XmlLanguage.GetLanguage("ar-SA");`|  
  
 Si vous devez définir le `Language` propriété à l’utilisateur actuel [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] langue utiliser le code suivant.  
  
||  
|-|  
|`text1.Language =`<br /><br /> `System.Windows.Markup.XmlLanguage.GetLanguage(`<br /><br /> `System.Globalization.CultureInfo.CurrentUICulture.IetfLanguageTag);`|  
  
 <xref:System.Globalization.CultureInfo.CurrentCulture%2A>représente la culture actuelle utilisée par le thread actuel en cours d’exécution.  
  
 Votre dernière [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] exemple doit être similaire à l’exemple suivant.  
  
 [!code-xaml[Numbers2#Numbers2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Numbers2/CS/Window1.xaml#numbers2)]  
  
 Votre dernière [!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)] exemple doit être similaire à ce qui suit.  
  
 [!code-csharp[NumbersCSharp#NumbersCSharp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NumbersCSharp/CSharp/Window1.xaml.cs#numberscsharp)]  
  
 Le graphique suivant montre à quoi ressemble la fenêtre pour l’un ou l’autre de ces langages de programmation.  
  
 **Graphique affichant des nombres arabes**  
  
 ![Nombres arabes](../../../../docs/framework/wpf/advanced/media/numbers2.PNG "Numbers2")  
  
 **Utilisation de la propriété Substitution**  
  
 La substitution de nombres de façon fonctionne dans [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] dépend de la langue de l’élément de texte et son <xref:System.Windows.FlowDirection>. Si le <xref:System.Windows.FlowDirection> de gauche à droite, puis les chiffres européens sont rendus. Toutefois si elle est précédée par du texte arabe ou a la langue définie à « ar » et le <xref:System.Windows.FlowDirection> est <xref:System.Windows.FlowDirection.RightToLeft>, chiffres arabes sont rendus à la place.  
  
 Toutefois, dans certains cas, il se peut que vous souhaitiez créer une application unifiée, avec par exemple des chiffres européens pour tous les utilisateurs. Ou des chiffres arabes dans <xref:System.Windows.Documents.Table> cellules comportant un spécifique <xref:System.Windows.Style>. Une méthode simple pour effectuer qui utilise le <xref:System.Windows.Media.NumberSubstitution.Substitution%2A> propriété.  
  
 Dans l’exemple suivant, la première <xref:System.Windows.Controls.TextBlock> n’a pas la <xref:System.Windows.Media.NumberSubstitution.Substitution%2A> propriété définie, l’algorithme affiche donc les chiffres arabes comme prévu. Toutefois dans le deuxième <xref:System.Windows.Controls.TextBlock>, la substitution a la valeur européenne substitution de la substitution de la valeur par défaut pour les chiffres arabes et chiffres européens sont affichés.  
  
 [!code-xaml[Numbers3#Numbers3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Numbers3/CS/Window1.xaml#numbers3)]
