---
title: "Vue d&#39;ensemble des fonctionnalit&#233;s bidirectionnelles dans WPF | Microsoft Docs"
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
  - "fonctionnalités bidirectionnelles"
  - "FlowDirection (propriété)"
  - "FlowDocument (propriété)"
  - "éléments Span"
ms.assetid: fd850e25-7dba-408c-b521-8873e51dc968
caps.latest.revision: 22
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 18
---
# Vue d&#39;ensemble des fonctionnalit&#233;s bidirectionnelles dans WPF
Contrairement aux autres plateformes de développement, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] propose de nombreuses fonctionnalités qui prennent en charge le développement rapide de contenu bidirectionnel, par exemple des données de gauche à droite et de droite à gauche mélangées dans le même document.  Parallèlement, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] crée une excellente expérience pour les utilisateurs qui ont besoin de fonctionnalités bidirectionnelles tels que les utilisateurs de langue arabe et hébreu.  
  
 Les sections suivantes expliquent de nombreuses fonctionnalités bidirectionnelles, accompagnées d'exemples qui illustrent comment réaliser le meilleur affichage de contenu bidirectionnel.  La plupart des exemples utilisent [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)], vous pouvez cependant facilement appliquer ces concepts à du code [!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)] ou [!INCLUDE[TLA#tla_visualb](../../../../includes/tlasharptla-visualb-md.md)].  
  
   
  
<a name="FlowDirection"></a>   
## FlowDirection  
 La propriété de base qui définit le sens de déroulement du contenu dans une application [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] est <xref:System.Windows.FrameworkElement.FlowDirection%2A>.  Cette propriété peut avoir une des deux valeurs d'énumération, <xref:System.Windows.FlowDirection> ou <xref:System.Windows.FlowDirection>.  Cette propriété est disponible pour tous les éléments [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] qui héritent de <xref:System.Windows.FrameworkElement>.  
  
 Les exemples suivants définissent le sens de déroulement d'un élément <xref:System.Windows.Controls.TextBox>.  
  
 **Sens de déroulement de gauche à droite**  
  
 [!code-xml[LTRRTL#LTR](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LTRRTL/CS/Pane1.xaml#ltr)]  
  
 **Sens de déroulement de droite à gauche**  
  
 [!code-xml[LTRRTL#RTL](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LTRRTL/CS/Pane1.xaml#rtl)]  
  
 Le graphique suivant montre le rendu généré par le code précédent.  
  
 **Graphique illustrant FlowDirection**  
  
 ![Alignement TextBlock](../../../../docs/framework/wpf/advanced/media/lefttorightrighttoleft.png "LefttoRightRighttoLeft")  
  
 Un élément au sein d'une arborescence d'[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] héritera de la propriété <xref:System.Windows.FrameworkElement.FlowDirection%2A> de son conteneur.  Dans l'exemple suivant, le <xref:System.Windows.Controls.TextBlock> est à l'intérieur d'un contrôle <xref:System.Windows.Controls.Grid>, qui réside dans une <xref:System.Windows.Window>.  Définir <xref:System.Windows.FrameworkElement.FlowDirection%2A> pour <xref:System.Windows.Window> implique de le définir pour <xref:System.Windows.Controls.Grid> ainsi que pour <xref:System.Windows.Controls.TextBlock>.  
  
 L'exemple suivant montre comment définir la propriété <xref:System.Windows.FrameworkElement.FlowDirection%2A>.  
  
 [!code-xml[FlowDirection#FlowDirection](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDirection/CS/Window1.xaml#flowdirection)]  
  
 La <xref:System.Windows.Window> de niveau supérieur a un <xref:System.Windows.FlowDirection> <xref:System.Windows.FlowDirection>, tous les éléments contenus dans celui\-ci héritent ainsi également du même <xref:System.Windows.FrameworkElement.FlowDirection%2A>.  Pour qu'un élément substitue un <xref:System.Windows.FrameworkElement.FlowDirection%2A> spécifié, il doit ajouter une modification de sens explicite, comme le deuxième <xref:System.Windows.Controls.TextBlock> de l'exemple précédent qui le modifie en <xref:System.Windows.FlowDirection>.  Lorsque aucun <xref:System.Windows.FrameworkElement.FlowDirection%2A> n'est défini, la valeur par défaut <xref:System.Windows.FlowDirection> s'applique.  
  
 Le graphique suivant montre la sortie produite par l'exemple précédent.  
  
 **Graphique illustrant FlowDirection assigné explicitement**  
  
 ![Illustration du sens du déroulement](../../../../docs/framework/wpf/advanced/media/flowdir.png "FlowDir")  
  
<a name="FlowDocument"></a>   
## FlowDocument  
 De nombreuses plateformes de développement telles que [!INCLUDE[TLA#tla_html](../../../../includes/tlasharptla-html-md.md)], [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] et Java™ fournissent une prise en charge spéciale du développement de contenu bidirectionnel.  Les langages de balisage tels que [!INCLUDE[TLA#tla_html](../../../../includes/tlasharptla-html-md.md)] procurent aux rédacteurs de contenu le balisage nécessaire pour afficher du texte dans n'importe quel sens requis, par exemple la balise [!INCLUDE[TLA#tla_html](../../../../includes/tlasharptla-html-md.md)] 4.0 « dir », qui prend les valeurs « rtl » ou « ltr ».  Cette balise est similaire à la propriété <xref:System.Windows.FrameworkElement.FlowDirection%2A>, mais la propriété <xref:System.Windows.FrameworkElement.FlowDirection%2A> a un fonctionnement plus avancé en ce qui concerne la disposition de contenu textuel et elle peut être utilisée pour du contenu autre que du texte.  
  
 Dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], un <xref:System.Windows.Documents.FlowDocument> est un élément d'[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] polyvalent qui peut héberger une combinaison de texte, tableaux, images et autres éléments.  Les exemples des sections suivantes utilisent cet élément.  
  
 L'ajout de texte à un <xref:System.Windows.Documents.FlowDocument> peut être effectué de plusieurs façons.  Ceci peut être réalisé simplement à l'aide d'un <xref:System.Windows.Documents.Paragraph> qui est un élément au niveau bloc utilisé pour grouper du contenu tel que du texte.  Pour ajouter du texte aux éléments inclus, l'exemple utilise <xref:System.Windows.Documents.Span> et <xref:System.Windows.Documents.Run>.  <xref:System.Windows.Documents.Span> est un élément inclus de contenu de flux utilisé pour grouper d'autres éléments inclus, tandis qu'un <xref:System.Windows.Documents.Run> est un élément inclus de contenu de flux destiné à contenir une séquence de texte non formaté.  Un <xref:System.Windows.Documents.Span> peut contenir plusieurs éléments <xref:System.Windows.Documents.Run>.  
  
 Le premier exemple de document contient un document qui a plusieurs noms de partage réseau ; par exemple `\\server1\folder\file.ext`.  Que ce lien réseau soit dans un document en arabe ou en anglais, vous souhaiterez toujours qu'il apparaisse de la même façon.  Le graphique suivant montre le lien dans un document <xref:System.Windows.FlowDirection> en arabe.  
  
 **Graphique illustrant l'utilisation de l'élément Span**  
  
 ![Document se déroulant de droite à gauche](../../../../docs/framework/wpf/advanced/media/flowdocument.png "FlowDocument")  
  
 Le texte étant dans le sens <xref:System.Windows.FlowDirection>, tous les caractères spéciaux, tel que « \\ », séparent le texte dans un ordre qui va de droite à gauche.  Il en résulte que le lien n'est pas affiché dans le bon ordre, et que par conséquent, pour résoudre le problème, le texte doit être incorporé afin de conserver un <xref:System.Windows.Documents.Run> séparé se déroulant dans le sens <xref:System.Windows.FlowDirection>.  Au lieu d'avoir un <xref:System.Windows.Documents.Run> séparé pour chaque langue, une meilleure façon de résoudre le problème est d'incorporer le texte anglais, qui est le moins souvent utilisé, dans un <xref:System.Windows.Documents.Span> de plus grande taille en langue arabe.  
  
 C'est ce que montre le graphique suivant :  
  
 **Graphique illustrant l'utilisation d'un élément Run incorporé dans un élément Span**  
  
 ![Capture d'écran XamlPad](../../../../docs/framework/wpf/advanced/media/runspan.png "RunSpan")  
  
 L'exemple suivant montre comment utiliser les éléments <xref:System.Windows.Documents.Run> et <xref:System.Windows.Documents.Span> dans des documents.  
  
 [!code-xml[RunSpan#RunSpan](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RunSpan/CS/Window1.xaml#runspan)]  
  
<a name="SpanElements"></a>   
## Éléments Span  
 L'élément <xref:System.Windows.Documents.Span> fonctionne comme une limite qui sépare les textes qui ont des sens de déroulement différents.  Même les éléments <xref:System.Windows.Documents.Span> qui ont un sens de déroulement identique sont considérés comme ayant des portées bidirectionnelles différentes, ce qui signifie que les éléments <xref:System.Windows.Documents.Span> sont ordonnés dans le <xref:System.Windows.FlowDirection> du conteneur, et que seul le contenu à l'intérieur de l'élément <xref:System.Windows.Documents.Span> suit le <xref:System.Windows.FlowDirection> du <xref:System.Windows.Documents.Span>.  
  
 Le graphique suivant montre le sens de déroulement de plusieurs éléments <xref:System.Windows.Controls.TextBlock>.  
  
 **Graphique illustrant FlowDirection dans plusieurs éléments TextBlock**  
  
 ![Blocs de texte avec directions de flux différentes](../../../../docs/framework/wpf/advanced/media/span.png "Span")  
  
 L'exemple suivant montre comment utiliser les éléments <xref:System.Windows.Documents.Span> et <xref:System.Windows.Documents.Run> pour produire les résultats affichés dans le graphique précédent.  
  
 [!code-xml[Span#Span](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Span/CS/Window1.xaml#span)]  
  
 Dans les éléments <xref:System.Windows.Controls.TextBlock> de l'exemple, les éléments <xref:System.Windows.Documents.Span> sont disposés selon le <xref:System.Windows.FlowDirection> de leurs parents, mais le texte situé à l'intérieur de chaque élément <xref:System.Windows.Documents.Span> se déroule dans son <xref:System.Windows.FlowDirection> propre.  Ceci s'applique au latin et à l'arabe ou à toute autre langue.  
  
### Ajout de xml:lang  
 Le graphique suivant montre un autre exemple qui utilise des nombres et des expressions arithmétiques, telles que `"200.0+21.4=221.4"`.  Notez que seul <xref:System.Windows.FlowDirection> est défini.  
  
 **Graphique affichant des nombres en utilisant uniquement FlowDirection**  
  
 ![Nombres se déroulant de droite à gauche](../../../../docs/framework/wpf/advanced/media/langattribute.png "LangAttribute")  
  
 Les utilisateurs de cette application seront déçus par la sortie du résultat, car bien que <xref:System.Windows.FlowDirection> soit correct, les nombres ne sont pas formés comme des nombres arabes devraient l'être.  
  
 Les éléments XAML peuvent inclure un attribut [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)]\(`xml:lang`\) qui définit la langue de chaque élément.  XAML prend en charge également un principe de langue [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] par lequel les valeurs `xml:lang` appliquées aux éléments parents dans l'arborescence sont utilisées par les éléments enfants.  Dans l'exemple précédent, du fait qu'une langue n'était pas définie pour l'élément <xref:System.Windows.Documents.Run> ni pour aucun de ses éléments de niveau supérieur, la langue `xml:lang` par défaut a été utilisée, c'est à dire `en-US` en XAML.  L'algorithme interne de [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] de mise en forme des nombres sélectionne les nombres dans la langue correspondante, dans ce cas l'anglais.  Afin que les chiffres arabes soient correctement affichés, `xml:lang` doit être défini.  
  
 Le graphique suivant montre l'exemple avec `xml:lang` ajouté.  
  
 **Graphique illustrant l'utilisation de l'attribut xml:lang**  
  
 ![Chiffres arabes se déroulant de droite à gauche](../../../../docs/framework/wpf/advanced/media/langattribute2.png "LangAttribute2")  
  
 L'exemple suivant ajoute `xml:lang` à l'application.  
  
 [!code-xml[LangAttribute#LangAttribute](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LangAttribute/CS/Window1.xaml#langattribute)]  
  
 N'oubliez pas que de nombreuses langues ont différentes valeurs `xml:lang` selon la région ciblée, par exemple `"ar-SA"` et `"ar-EG"` représentent deux variantes de l'arabe.  Les exemples précédents montrent que vous devez définir à la fois les valeurs `xml:lang` et <xref:System.Windows.FlowDirection>.  
  
<a name="FlowDirectionNontext"></a>   
## FlowDirection avec des éléments autres que textuels  
 <xref:System.Windows.FlowDirection> définit non seulement comment le texte se déroule dans un élément textuel, mais également le sens de déroulement de presque tous les éléments de l'[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  Le graphique suivant montre un <xref:System.Windows.Controls.ToolBar> qui utilise un <xref:System.Windows.Media.LinearGradientBrush> horizontal pour dessiner son arrière\-plan.  
  
 **Graphique montrant une barre d'outils avec un dégradé de gauche à droite**  
  
 ![Capture d'écran dégradée](../../../../docs/framework/wpf/advanced/media/gradient.png "Gradient")  
  
 Après l'affectation de <xref:System.Windows.FlowDirection> à <xref:System.Windows.FlowDirection>, non seulement les boutons de <xref:System.Windows.Controls.ToolBar> sont organisés de droite à gauche, mais <xref:System.Windows.Media.LinearGradientBrush> réaligne même ses offsets pour qu'ils se déroulent de droite à gauche.  
  
 Le graphique suivant illustre le réalignement de <xref:System.Windows.Media.LinearGradientBrush>.  
  
 **Graphique montrant une barre d'outils avec un dégradé de droite à gauche**  
  
 ![Dégradé de droite à gauche](../../../../docs/framework/wpf/advanced/media/gradient2-wpf.png "Gradient2\_WPF")  
  
 L'exemple suivant dessine un <xref:System.Windows.Controls.ToolBar> de sens <xref:System.Windows.FlowDirection>.  \(Pour le dessiner de gauche à droite, supprimez l'attribut <xref:System.Windows.FlowDirection> sur le <xref:System.Windows.Controls.ToolBar>\).  
  
 [!code-xml[Gradient#Gradient](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Gradient/CS/Window1.xaml#gradient)]  
  
<a name="FlowDirectionExceptions"></a>   
### Exceptions de FlowDirection  
 Il existe quelques cas où <xref:System.Windows.FlowDirection> ne se comporte pas comme prévu.  Cette section décrit deux de ces exceptions.  
  
 **Image**  
  
 Une <xref:System.Windows.Controls.Image> représente un contrôle qui affiche une image.  En [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)], elle peut être utilisée avec une propriété <xref:System.Windows.Controls.Image.Source%2A> qui définit l'[!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] de l'<xref:System.Windows.Controls.Image> à afficher.  
  
 Contrairement aux autres éléments de l' [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], une <xref:System.Windows.Controls.Image> n'hérite pas du <xref:System.Windows.FlowDirection> de son conteneur.  Cependant, si le <xref:System.Windows.FlowDirection> a explicitement la valeur <xref:System.Windows.FlowDirection>, une <xref:System.Windows.Controls.Image> s'affiche retournée horizontalement.  Cette implémentation est une fonctionnalité pratique pour les développeurs de contenu bidirectionnel, parce que dans certains cas, le fait de retourner l'image horizontalement produit l'effet recherché.  
  
 Le graphique suivant affiche une <xref:System.Windows.Controls.Image> retournée.  
  
 **Graphique illustrant une image retournée**  
  
 ![Capture d'écran XamlPad](../../../../docs/framework/wpf/advanced/media/image.png "Image")  
  
 L'exemple suivant montre que l'<xref:System.Windows.Controls.Image> ne réussit pas à hériter du <xref:System.Windows.FlowDirection> du <xref:System.Windows.Controls.StackPanel> qui la contient.  **Remarque** vous devez avoir un fichier nommé **ms\_logo.jpg** sur votre lecteur C:\\ pour exécuter cet exemple.  
  
 [!code-xml[Image#Image](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Image/CS/Window1.xaml#image)]  
  
 **Remarque** un fichier **ms\_logo.jpg** est inclus dans les fichiers à télécharger.  Le code suppose que le fichier .jpg n'est pas à l'intérieur de votre projet mais quelque part sur le lecteur C:\\.  Vous devez copier le fichier .jpg depuis vos fichiers projet vers votre lecteur C:\\ ou modifier le code afin qu'il recherche le fichier à l'intérieur du projet.  Pour ce faire, modifiez `Source="file://c:/ms_logo.jpg"` en `Source="ms_logo.jpg"`.  
  
 **Tracés**  
  
 En plus de <xref:System.Windows.Controls.Image>, un autre élément intéressant est <xref:System.Windows.Shapes.Path>.  Un tracé est un objet qui peut dessiner une série de lignes et de courbes connectées.  Il se comporte de manière semblable à une <xref:System.Windows.Controls.Image> en ce qui concerne son <xref:System.Windows.FlowDirection> ; par exemple, un <xref:System.Windows.FlowDirection> de valeur <xref:System.Windows.FlowDirection> correspond à un miroir horizontal de son sens de déroulement <xref:System.Windows.FlowDirection>.  Cependant, contrairement à <xref:System.Windows.Controls.Image>, <xref:System.Windows.Shapes.Path> hérite du <xref:System.Windows.FlowDirection> du conteneur et il n'est pas nécessaire de le spécifier explicitement.  
  
 L'exemple suivant dessine une flèche simple à l'aide de 3 lignes.  La première flèche hérite du sens de déroulement <xref:System.Windows.FlowDirection> de <xref:System.Windows.Controls.StackPanel> de telle sorte que ses points de début et de terminaison sont mesurés à partir d'une racine située sur le côté droit.  La deuxième flèche qui a un <xref:System.Windows.FlowDirection> <xref:System.Windows.FlowDirection> explicite débute également sur le côté droit.  Cependant, la troisième flèche a sa racine de début située sur le côté gauche.  Pour plus d'informations sur le dessin, consultez <xref:System.Windows.Media.LineGeometry> et <xref:System.Windows.Media.GeometryGroup>.  
  
 [!code-xml[Paths#Paths](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Paths/CS/Window1.xaml#paths)]  
  
 Le graphique suivant montre la sortie produite par l'exemple précédent.  
  
 **Graphique illustrant des flèches dessinées à l'aide de l'élément Path**  
  
 ![Chemins d'accès](../../../../docs/framework/wpf/advanced/media/paths.png "Paths")  
  
 <xref:System.Windows.Controls.Image> et <xref:System.Windows.Shapes.Path> sont deux exemples de la façon dont [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] utilise <xref:System.Windows.FlowDirection>.  En plus de la disposition d'éléments de l'[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] dans un sens spécifique au sein d'un conteneur, <xref:System.Windows.FlowDirection> peut être utilisé avec des éléments tels que <xref:System.Windows.Controls.InkPresenter>, qui restitue de l'encre sur une surface, <xref:System.Windows.Media.LinearGradientBrush>, <xref:System.Windows.Media.RadialGradientBrush>.  Si vous avez besoin d'un comportement de droite à gauche de votre contenu qui reproduit un comportement de gauche à droite ou inversement, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] vous fournit cette fonctionnalité.  
  
<a name="NumberSubstitution"></a>   
## Substitution de nombres  
 Historiquement, [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] a pris en charge la substitution de nombres en permettant la représentation de chiffres identiques sous des formes différentes selon la culture, tout en gardant un stockage interne de ces chiffres unifié entre les différents paramètres régionaux ; les nombres sont stockés dans leurs valeurs connues hexadécimales, par exemple 0x40, 0x41, mais affichés en fonction de la langue sélectionnée.  
  
 Ceci a permis aux applications de traiter les valeurs numériques sans avoir besoin de les convertir d'une langue à une autre ; un utilisateur peut par exemple ouvrir une feuille de calcul [!INCLUDE[TLA#tla_xl](../../../../includes/tlasharptla-xl-md.md)] sur une version localisée en arabe de [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] et voir les nombres sous leur forme arabe, mais l'ouvrir sur une version européenne de [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] et voir ces mêmes nombres dans leur représentation européenne.  Ceci est également nécessaire pour les autres symboles tels que les virgules et le symbole du pourcentage parce qu'ils accompagnent habituellement des nombres dans le même document.  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] continue dans la même tradition et ajoute une prise en charge supplémentaire de cette fonctionnalité qui permet un meilleur contrôle de l'utilisateur sur quand et comment la substitution est utilisée.  Bien que cette fonctionnalité soit conçue pour n'importe quelle langue, elle est particulièrement utile pour du contenu bidirectionnel, où la mise en forme des chiffres est habituellement un défi pour les développeurs d'application du fait des différentes cultures dans lesquelles peut s'exécuter l'application.  
  
 La principale propriété qui contrôle comment la substitution de nombres fonctionne dans [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] est la propriété de dépendance <xref:System.Windows.Media.NumberSubstitution.Substitution%2A>.  La classe <xref:System.Windows.Media.NumberSubstitution> spécifie comment les nombres doivent être affichés dans le texte.  Elle a trois propriétés publiques qui définissent son comportement.  Voici un résumé de chacune de ces propriétés.  
  
 **CultureSource :**  
  
 Cette propriété spécifie la manière dont est déterminée la culture pour les nombres.  Elle prend une des trois valeurs d'énumération <xref:System.Windows.Media.NumberCultureSource>.  
  
-   Override : la culture pour les nombres est celle de la propriété <xref:System.Windows.Media.NumberSubstitution.CultureOverride%2A>.  
  
-   Text : la culture pour les nombres est la culture de l'exécution de texte.  Dans le balisage, ceci correspond à `xml:lang` ou sa propriété d'alias `Language` <xref:System.Windows.FrameworkElement.Language%2A> ou <xref:System.Windows.FrameworkContentElement.Language%2A>.  C'est également la valeur par défaut pour les classes dérivant de <xref:System.Windows.FrameworkContentElement>.  De telles classes comprennent <xref:System.Windows.Documents.Paragraph?displayProperty=fullName>, <xref:System.Windows.Documents.Table?displayProperty=fullName>, <xref:System.Windows.Documents.TableCell?displayProperty=fullName>, etc.  
  
-   User : la culture pour les nombres est la culture du thread actuel.  Cette propriété est la valeur par défaut pour toutes les sous\-classes de <xref:System.Windows.FrameworkElement> telles que <xref:System.Windows.Controls.Page>, <xref:System.Windows.Window> et <xref:System.Windows.Controls.TextBlock>.  
  
 **CultureOverride** :  
  
 La propriété <xref:System.Windows.Media.NumberSubstitution.CultureOverride%2A> est utilisée uniquement si la propriété <xref:System.Windows.Media.NumberSubstitution.CultureSource%2A> a la valeur <xref:System.Windows.Media.NumberCultureSource> et est ignorée dans le cas contraire.  Elle spécifie la culture pour les nombres.  La valeur `null`, la valeur par défaut, est interprétée comme en\-US.  
  
 **Substitution** :  
  
 Cette propriété spécifie le type de substitution de nombres à effectuer.  Elle prend une des valeurs d'énumération <xref:System.Windows.Media.NumberSubstitutionMethod> suivantes.  
  
-   <xref:System.Windows.Media.NumberSubstitutionMethod> : la méthode de substitution est déterminée en fonction de la propriété <xref:System.Globalization.NumberFormatInfo.DigitSubstitution%2A?displayProperty=fullName> de la culture pour les nombres.  Il s'agit de la valeur par défaut.  
  
-   <xref:System.Windows.Media.NumberSubstitutionMethod> : si la culture pour les nombres est l'arabe ou le farsi, il spécifie que les chiffres dépendent du contexte.  
  
-   <xref:System.Windows.Media.NumberSubstitutionMethod> : les nombres sont toujours restitués comme des chiffres européens.  
  
-   <xref:System.Windows.Media.NumberSubstitutionMethod> : les nombres sont restitués à l'aide des chiffres nationaux pour la culture pour les  nombres, comme spécifié par le <xref:System.Globalization.CultureInfo.NumberFormat%2A>de la culture.  
  
-   <xref:System.Windows.Media.NumberSubstitutionMethod> : les nombres sont restitués en utilisant les chiffres traditionnels de la culture pour les nombres.  Pour la plupart des cultures, c'est le même que <xref:System.Windows.Media.NumberSubstitutionMethod>.  Toutefois, l'utilisation de <xref:System.Windows.Media.NumberSubstitutionMethod> produit des chiffres latins pour certaines cultures arabes, tandis que cette valeur produit des chiffres arabes pour toutes les cultures arabes.  
  
 Que signifient ces valeurs pour un développeur de contenu bidirectionnel ?  Dans la plupart des cas, le développeur peut uniquement avoir besoin de définir <xref:System.Windows.FlowDirection> et la langue de chaque élément textuel de l'[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], par exemple `Language="ar-SA"`, et la logique de <xref:System.Windows.Media.NumberSubstitution> se charge d'afficher les nombres en fonction de la bonne [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  L'exemple suivant illustre l'utilisation des nombres arabes et anglais dans une application [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] s'exécutant sur une version arabe de [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)].  
  
 [!code-xml[Numbers#Numbers](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Numbers/CS/Window1.xaml#numbers)]  
  
 Le graphique suivant montre la sortie produite par l'exemple précédent lors de son exécution sur une version arabe de [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)].  
  
 **Graphique montrant l'affichage de nombres arabes et anglais**  
  
 ![Capture d'écran XamlPad avec numéros](../../../../docs/framework/wpf/advanced/media/numbers.png "Numbers")  
  
 <xref:System.Windows.FlowDirection> était important dans le cas présent parce qu'affecter à <xref:System.Windows.FlowDirection> la valeur <xref:System.Windows.FlowDirection> à la place aurait produit des chiffres européens.  Les sections suivantes expliquent comment obtenir un affichage unifié des chiffres dans l'ensemble de votre document.  Si cet exemple ne s'exécute pas sur une version arabe de Windows, tous les chiffres sont affichés en tant que chiffres européens.  
  
 **Définition des règles de substitution**  
  
 Dans une application réelle il est possible que vous ayez besoin de définir la langue par programme.  Par exemple, vous souhaitez affecter à l'attribut `xml:lang` le même que celui utilisé par l'[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]du système, ou peut\-être modifier la langue en fonction de l'état de l'application.  
  
 Si vous souhaitez effectuer des modifications en fonction de l'état de l'application, utilisez d'autres fonctionnalités fournies par [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  
  
 En premier lieu, définissez `NumberSubstitution.CultureSource="Text"` pour le composant de l'application.  L'utilisation de ce paramètre permet de s'assurer que les paramètres ne proviennent pas de l'[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] pour les éléments de texte qui ont « User » comme valeur par défaut, tel que <xref:System.Windows.Controls.TextBlock>.  
  
 Par exemple :  
  
||  
|-|  
|`<TextBlock`<br /><br /> `Name="text1" NumberSubstitution.CultureSource="Text">`<br /><br /> `1234+5679=6913`<br /><br /> `</TextBlock>`|  
  
 Dans le code [!INCLUDE[TLA2#tla_lhcshrp](../../../../includes/tla2sharptla-lhcshrp-md.md)] correspondant, définissez par exemple la propriété `Language`, à `"ar-SA"`.  
  
||  
|-|  
|`text1.Language =`<br /><br /> `System.Windows.Markup.XmlLanguage.GetLanguage("ar-SA");`|  
  
 Si vous avez besoin définir la propriété de `Language` à la langue [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] de l'utilisateur actuel, utilisez le code suivant.  
  
||  
|-|  
|`text1.Language =`<br /><br /> `System.Windows.Markup.XmlLanguage.GetLanguage(`<br /><br /> `System.Globalization.CultureInfo.CurrentUICulture.IetfLanguageTag);`|  
  
 <xref:System.Globalization.CultureInfo.CurrentCulture%2A> représente la culture actuelle utilisée par le thread actuel au moment de l'exécution.  
  
 Votre exemple final en [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] doit être semblable à l'exemple suivant.  
  
 [!code-xml[Numbers2#Numbers2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Numbers2/CS/Window1.xaml#numbers2)]  
  
 Votre exemple final en [!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)] doit être semblable à ce qui suit.  
  
 [!code-csharp[NumbersCSharp#NumbersCSharp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NumbersCSharp/CSharp/Window1.xaml.cs#numberscsharp)]  
  
 Le graphique suivant montre à quoi ressemble la fenêtre pour l'un ou l'autre de ces langages de programmation.  
  
 **Graphique affichant des nombres arabes**  
  
 ![Chiffres arabes](../../../../docs/framework/wpf/advanced/media/numbers2.png "Numbers2")  
  
 **Utilisation de la propriété Substitution**  
  
 La façon dont fonctionne la substitution de nombres dans [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] dépend à la fois de la langue de l'élément de texte et de son <xref:System.Windows.FlowDirection>.  Si <xref:System.Windows.FlowDirection> est de gauche à droite, ce sont des chiffres européens qui sont restituées.  Cependant, s'il est précédé par du texte arabe, ou que la langue a la valeur « ar » et que <xref:System.Windows.FlowDirection> a la valeur <xref:System.Windows.FlowDirection>, ce sont les chiffres arabes qui sont restitués à la place.  
  
 Toutefois, dans certains cas, il se peut que vous souhaitiez créer une application unifiée, avec par exemple des chiffres européens pour tous les utilisateurs.  Ou des chiffres arabes dans des cellules de <xref:System.Windows.Documents.Table> avec un <xref:System.Windows.Style> spécifique.  Pour ce faire, une méthode simple consiste à utiliser la propriété <xref:System.Windows.Media.NumberSubstitution.Substitution%2A>.  
  
 Dans l'exemple suivant, le premier <xref:System.Windows.Controls.TextBlock> n'a pas sa propriété <xref:System.Windows.Media.NumberSubstitution.Substitution%2A> définie, l'algorithme affiche donc les chiffres arabes comme prévu.  Cependant, dans le deuxième <xref:System.Windows.Controls.TextBlock>, la substitution a la valeur European qui remplace la substitution par défaut pour les nombres arabes, et ce sont des chiffres européens qui sont affichés.  
  
 [!code-xml[Numbers3#Numbers3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Numbers3/CS/Window1.xaml#numbers3)]