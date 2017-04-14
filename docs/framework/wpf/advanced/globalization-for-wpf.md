---
title: "Globalisation pour WPF | Microsoft Docs"
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
  - "globalisation"
  - "interface utilisateur internationale, XAML"
  - "XAML, globalisation"
  - "XAML, interface utilisateur internationale"
ms.assetid: 4571ccfe-8a60-4f06-9b37-7ac0b1c2d10f
caps.latest.revision: 35
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 31
---
# Globalisation pour WPF
Cette rubrique présente certains problèmes dont vous devez être conscient lors de l'écriture d'applications [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] pour le marché international.  Les éléments de programmation de la globalisation sont définis dans [!INCLUDE[TLA#tla_net](../../../../includes/tlasharptla-net-md.md)] sous `System.Globalization`.  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
<a name="xaml_globalization"></a>   
## Globalisation XAML  
 Le langage [!INCLUDE[TLA#tla_xaml#initcap](../../../../includes/tlasharptla-xamlsharpinitcap-md.md)] est basé sur le langage [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] et bénéficie de la prise en charge de la globalisation définie dans la spécification [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)].  Les sections suivantes décrivent certaines fonctionnalités [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] que vous devez connaître.  
  
<a name="char_reference"></a>   
### Références de caractère  
 La référence de caractère donne le numéro du caractère [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] qu'elle représente, sous forme décimale ou hexadécimale.  L'exemple suivant présente une référence de caractère décimale.  
  
```  
Ϩ  
```  
  
 Ce deuxième exemple illustre une référence de caractère hexadécimale.  Notez la présence d'un **x** devant le nombre hexadécimal.  
  
```  
Ϩ  
```  
  
<a name="encoding"></a>   
### Encodage  
 Les encodages [!INCLUDE[TLA#tla_ascii](../../../../includes/tlasharptla-ascii-md.md)], [!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)] UTF\-16 et UTF\-8 sont pris en charge par le langage [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  L'instruction des encodage se trouve au début de chaque document [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  Si aucun attribut d'encodage ni ordre d'octets n'existe, la valeur UTF\-8 est affectée par défaut à l'analyseur.  UTF\-8 et UTF\-16 sont les encodages par défaut.  L'encodage UTF\-7 n'est pas pris en charge.  L'exemple suivant montre comment spécifier un encodage UTF\-8 dans un fichier [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
```  
?xml encoding="UTF-8"?  
```  
  
<a name="lang_attrib"></a>   
### Attribut Language  
 Le langage [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] utilise [xml:lang](../../../../docs/framework/xaml-services/xml-lang-handling-in-xaml.md) pour représenter l'attribut de langage d'un élément.  Pour tirer parti de la classe <xref:System.Globalization.CultureInfo>, la valeur d'attribut de langage doit être l'un des noms de culture prédéfinis par <xref:System.Globalization.CultureInfo>.  [xml:lang](../../../../docs/framework/xaml-services/xml-lang-handling-in-xaml.md) peut être hérité dans l'arborescence d'éléments \(par les règles XML, pas nécessairement à cause de l'héritage de propriétés de dépendance\) et sa valeur par défaut est une chaîne vide s'il n'est pas assigné explicitement.  
  
 L'attribut de langage est très utile pour spécifier des dialectes.  Par exemple, le français présente des différences orthographiques, lexicales et phonologiques en fonction de la zone géographique dans laquelle il est utilisé : en France, au Québec, en Belgique ou en Suisse.  Le chinois, le japonais et le coréen partagent également des points de code [!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)], bien que ces trois langues utilisent des polices et des idéogrammes très différents.  
  
 L'exemple de langage [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] suivant utilise l'attribut du langage `fr-CA` pour spécifier le français canadien.  
  
```  
<TextBlock xml:lang="fr-CA">Découvrir la France</TextBlock>  
```  
  
<a name="unicode"></a>   
### Unicode  
 Le langage [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] prend en charge toutes les fonctionnalités [!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)], y compris les substituts.  Tant que le jeu de caractères peut être mappé à [!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)], sa prise en charge est assurée.  Par exemple, le jeu de caractère GB18030 comprend quelques caractères mappés aux extensions A et B et aux paires de substitution du chinois, du japonais et du coréen \(CFK\) ; par conséquent, il est totalement pris en charge.  Une application [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] peut utiliser la classe <xref:System.Globalization.StringInfo> pour manipuler des chaînes sans chercher à savoir si celles\-ci contiennent des paires de substitution ou des caractères de non\-espacement.  
  
<a name="design_intl_ui_with_xaml"></a>   
## Conception d'une interface utilisateur internationale avec le langage XAML  
 Cette section décrit des fonctionnalités d'[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] que vous devez garder à l'esprit lors de l'écriture d'une application.  
  
<a name="intl_text"></a>   
### Texte international  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] inclut un traitement intégré pour tous les systèmes d'écriture pris en charge par [!INCLUDE[TLA#tla_winfx](../../../../includes/tlasharptla-winfx-md.md)].  
  
 Les scripts suivants sont actuellement pris en charge :  
  
-   Arabe  
  
-   Bengali  
  
-   Devanagari  
  
-   Cyrillique  
  
-   Grec  
  
-   Gujarati  
  
-   Gurmukhi  
  
-   Hébreu  
  
-   Scripts idéographiques  
  
-   Kannada  
  
-   Laotien  
  
-   Latin  
  
-   Malayalam  
  
-   Mongol  
  
-   Oriya  
  
-   Syriaque  
  
-   Tamoul  
  
-   Télougou  
  
-   Thâna  
  
-   Thaï\*  
  
-   Tibétain  
  
 \*Cette version prend en charge l'affichage et la modification de texte thaïlandais, mais pas la césure de mots.  
  
 Les scripts suivants ne sont actuellement pas pris en charge :  
  
-   Khmer  
  
-   Hangûl \(ancien coréen\)  
  
-   Birman  
  
-   Sinhala  
  
 Tous les moteurs de systèmes d'écriture prennent en charge les polices [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)].  Les polices [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] peuvent inclure les tableaux de disposition [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] qui permettent aux créateurs de polices de concevoir de meilleures polices typographiques internationales et haut de gamme.  Les tableaux de disposition de police [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] contiennent des informations sur les substitutions et le positionnement de glyphes, la justification et le positionnement de ligne de base, permettant aux applications de traitement de texte d'améliorer la disposition du texte.  
  
 Les polices [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] permettent de gérer des jeux de glyphes volumineux à l'aide de l'encodage [!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)].  Cet encodage est largement pris en charge au niveau international, comme les variantes de glyphes typographiques.  
  
 Le rendu de texte [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] est généré par la technologie de sous\-pixel [!INCLUDE[TLA#tla_ct](../../../../includes/tlasharptla-ct-md.md)] qui prend en charge l'indépendance vis\-à\-vis de la résolution.  La lisibilité est ainsi considérablement améliorée et les documents haute qualité de style magazine peuvent être pris en charge pour tous les scripts.  
  
<a name="intl_layout"></a>   
### Disposition internationale  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] offre un moyen très pratique pour prendre en charge des dispositions horizontales, bidirectionnelles et verticales.  Dans l'infrastructure de présentation, la propriété <xref:System.Windows.FrameworkElement.FlowDirection%2A> peut être utilisée pour définir la disposition.  Les modèles de sens du déroulement sont les suivants :  
  
-   *LeftToRight* : disposition horizontale pour le latin, les langues d'Asie orientale, etc.  
  
-   *RightToLeft* : disposition bidirectionnelle pour l'arabe, l'hébreu, etc.  
  
<a name="developing_localizable_apps"></a>   
## Développement d'applications localisables  
 Lorsque vous écrivez une application destinée à être utilisée dans le monde entier, vous ne devez pas oublier que cette application doit être localisable.  Les rubriques suivantes signalent certains éléments à prendre en compte.  
  
<a name="mui"></a>   
### Interface utilisateur multilingue  
 La prise en charge [!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)] d'interfaces utilisateur multilingues permet d'accéder à différentes langues pour les [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)].  Une application [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] utilise le modèle assembly pour prendre en charge les interfaces utilisateur multilingues.  Une application contient des assemblys indépendants de la langue ainsi que des assemblys de ressources satellites dépendants de la langue.  Le point d'entrée est un .EXE managé dans l'assembly principal.  Le chargeur de ressource [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tire parti du gestionnaire de ressources du [!INCLUDE[TLA2#tla_netframewk](../../../../includes/tla2sharptla-netframewk-md.md)] pour prendre en charge la recherche et la substitution de ressources.  Les assemblys satellites multilingues fonctionnent avec le même assembly principal.  L'assembly de ressources chargé dépend de la propriété <xref:System.Globalization.CultureInfo.CurrentUICulture%2A> du thread actuel.  
  
<a name="localizable_ui"></a>   
### Interface utilisateur localisable  
 Les applications [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] utilisent [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pour définir leur [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] permet aux développeurs de spécifier une hiérarchie d'objets avec un ensemble de propriétés et une logique.  Le langage [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] est principalement utilisé pour le développement d'applications [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], mais il peut également servir à spécifier une hiérarchie d'objets [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)].  La plupart des développeurs utilisent le langage [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pour spécifier l'[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] de leurs applications et utilisent un langage de programmation tel que [!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)] pour réagir à l'intervention de l'utilisateur.  
  
 Du point de vue des ressources, un fichier [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] conçu pour décrire une [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] dépendante de la langue est un élément de ressource et, par conséquent, son format de distribution final doit être localisable pour prendre en charge différentes langues du monde entier.  Le langage [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ne pouvant pas gérer d'événement, des blocs de code réservés à cette opération sont inclus dans de nombreuses applications [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  Pour plus d'informations, consultez [Vue d'ensemble du langage XAML \(WPF\)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md).  Le code est supprimé et compilé dans différents binaires lorsqu'un fichier [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] est représenté sous forme de jeton dans le formulaire BAML du XAML. Le formulaire BAML des fichiers, images et autres types d'objets de ressources managées XAML sont incorporés dans l'assembly des ressources satellites, pouvant être localisé dans d'autres langues, ou dans l'assembly principal, lorsque la localisation n'est pas requise.  
  
> [!NOTE]
>  Les applications [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] prennent en charge toutes les ressources [!INCLUDE[TLA2#tla_netframewk](../../../../includes/tla2sharptla-netframewk-md.md)][!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)], y compris les tables de chaînes, les images, etc.  
  
<a name="building_localizable_apps"></a>   
### Génération d'applications localisables  
 La localisation est l'adaptation d'une [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] à différentes cultures.  Pour qu'une application [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] soit localisable, les développeurs doivent générer toutes les ressources localisables dans un assembly de ressources.  L'assembly de ressources est localisé dans différentes langues et l'[!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] de gestion des ressources est utilisée pour le chargement du code\-behind.  Un fichier projet \(.proj\) est requis pour toute application [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  Toutes les ressources que vous utilisez dans votre application doivent être incluses dans ce fichier projet.  Cette opération est illustrée dans l'exemple suivant, à partir d'un fichier .csproj.  
  
```  
<Resource Include="data\picture1.jpg"/>  
<EmbeddedResource Include="data\stringtable.en-US.restext"/>  
```  
  
 Pour utiliser une ressource dans votre application, créez une instance <xref:System.Resources.ResourceManager> et chargez la ressource souhaitée.  L'exemple suivant illustre la procédure à suivre pour réaliser cette opération.  
  
 [!code-csharp[LocalizationResources#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationResources/CSharp/page1.xaml.cs#2)]  
  
<a name="using_clickonce"></a>   
## Utilisation de ClickOnce avec les applications localisées  
 ClickOnce est une nouvelle technologie de déploiement Windows Forms qui sera fournie avec [!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)].  Cette technologie permet d'installer des applications et de mettre à niveau des applications Web.  Lorsqu'une application déployée avec ClickOnce est localisée, elle ne peut être affichée que pour la culture localisée.  Par exemple, si une application déployée est localisée en japonais, elle ne peut être affichée que sous la version japonaise de [!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] et non pas sous sa version anglaise.  Cela représente un problème car il est fréquent que des utilisateurs japonais utilisent une version anglaise de [!INCLUDE[TLA2#tla_win](../../../../includes/tla2sharptla-win-md.md)].  
  
 Pour remédier à cela, l'attribut de secours de langage neutre doit être défini.  Un développeur d'applications peut également supprimer des ressources de l'assembly principal pour les placer dans un assembly satellite correspondant à une culture spécifique.  Pour contrôler ce processus, utilisez la classe <xref:System.Resources.NeutralResourcesLanguageAttribute>.  Le constructeur de la classe <xref:System.Resources.NeutralResourcesLanguageAttribute> a deux signatures, dont une qui utilise un paramètre <xref:System.Resources.UltimateResourceFallbackLocation> pour spécifier l'emplacement où <xref:System.Resources.ResourceManager> doit extraire les ressources de secours : assembly principal ou assembly satellite.  L'exemple suivant montre comment utiliser cet attribut.  Pour l'emplacement de secours ultime, le code indique au <xref:System.Resources.ResourceManager> qu'il doit rechercher les ressources dans le sous\-répertoire « de » du répertoire de l'assembly en cours d'exécution.  
  
```  
[assembly: NeutralResourcesLanguageAttribute(  
    "de" , UltimateResourceFallbackLocation.Satellite)]  
  
```  
  
## Voir aussi  
 [Vue d'ensemble de la globalisation et de la localisation WPF](../../../../docs/framework/wpf/advanced/wpf-globalization-and-localization-overview.md)