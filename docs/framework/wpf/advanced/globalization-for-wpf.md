---
title: Globalisation pour WPF
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology: dotnet-wpf
ms.topic: article
helpviewer_keywords:
- XAML [WPF], international user interface
- XAML [WPF], globalization
- international user interface [WPF], XAML
- globalization [WPF]
ms.assetid: 4571ccfe-8a60-4f06-9b37-7ac0b1c2d10f
caps.latest.revision: "35"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e6f39d40284e6212715d85fece545e653ff2e60a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="globalization-for-wpf"></a>Globalisation pour WPF
Cette rubrique présente les problèmes que vous devez être conscient lors de l’écriture [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] applications pour le marché international. Les éléments de programmation de globalisation sont définis dans [!INCLUDE[TLA#tla_net](../../../../includes/tlasharptla-net-md.md)] dans `System.Globalization`.  
  

  
<a name="xaml_globalization"></a>   
## <a name="xaml-globalization"></a>Globalisation XAML  
 [!INCLUDE[TLA#tla_xaml#initcap](../../../../includes/tlasharptla-xamlsharpinitcap-md.md)]est basé sur [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] et tire parti de la prise en charge de la globalisation définie dans le [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] spécification. Les sections suivantes décrivent certaines [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] les fonctionnalités que vous devez connaître.  
  
<a name="char_reference"></a>   
### <a name="character-references"></a>Références de caractères  
Une référence de caractère donne l’unité de code UTF16 de particulier [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] représente, sous forme décimale ou hexadécimale de caractères. L’exemple suivant montre une référence de caractère décimale pour la LETTRE MAJUSCULE COPTE HORI, ou 'Ϩ' :

```
&#1000;
```

L’exemple suivant montre une référence de caractère hexadécimale. Notez qu’il possède un **x** devant le nombre hexadécimal.

```
&#x3E8;
```

<a name="encoding"></a>   
### <a name="encoding"></a>Encodage  
 L’encodage pris en charge par [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] sont [!INCLUDE[TLA#tla_ascii](../../../../includes/tlasharptla-ascii-md.md)], [!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)] UTF-16 et UTF-8. L’instruction d’encodage est au début de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] document. Si aucun attribut d’encodage ni ordre d’octets n’existe, la valeur UTF-8 est affectée par défaut à l’analyseur. UTF-8 et UTF-16 sont les encodages par défaut. UTF-7 n’est pas pris en charge. L’exemple suivant montre comment spécifier un encodage UTF-8 dans un [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] fichier.  
  
```  
?xml encoding="UTF-8"?  
```  
  
<a name="lang_attrib"></a>   
### <a name="language-attribute"></a>Attribut de langue  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]utilise [XML : lang](../../../../docs/framework/xaml-services/xml-lang-handling-in-xaml.md) pour représenter l’attribut de langage d’un élément.  Pour tirer parti de la <xref:System.Globalization.CultureInfo> (classe), la valeur d’attribut de langage doit être un des noms de cultures prédéfinis par <xref:System.Globalization.CultureInfo>. [xml:lang](../../../../docs/framework/xaml-services/xml-lang-handling-in-xaml.md) peut être hérité dans l’arborescence d’éléments (par les règles XML, pas nécessairement à cause de l’héritage de propriétés de dépendance) et sa valeur par défaut est une chaîne vide s’il n’est pas assigné explicitement.  
  
 L’attribut de langue est très utile pour spécifier des dialectes. Par exemple, le français présente des différences orthographiques, lexicales et phonologiques en fonction de la zone géographique dans laquelle il est utilisé : en France, au Québec, en Belgique ou en Suisse. Chinois, japonais et coréen partagent également des points de code dans [!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)], mais les idéogrammes sont différentes, et elles utilisent les polices totalement différentes.  
  
 Les éléments suivants [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] exemple utilise le `fr-CA` l’attribut de langue pour spécifier le Français du Canada.  
  
```xml  
<TextBlock xml:lang="fr-CA">Découvrir la France</TextBlock>  
```  
  
<a name="unicode"></a>   
### <a name="unicode"></a>Unicode  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]prend en charge tous les [!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)] fonctionnalités, y compris les substituts. Tant que le jeu de caractères peut être mappé à [!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)], il est pris en charge. Par exemple, le jeu de caractères GB18030 comprend quelques caractères mappés aux extensions A et B et aux paires de substitution du chinois, du japonais et du coréen (CFK) ; par conséquent, il est totalement pris en charge. A [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application peut utiliser <xref:System.Globalization.StringInfo> pour manipuler des chaînes sans comprendre si elles ont des paires de substitution ou des caractères de non-espacement.  
  
<a name="design_intl_ui_with_xaml"></a>   
## <a name="designing-an-international-user-interface-with-xaml"></a>Conception d’une interface utilisateur internationale avec le langage XAML  
 Cette section décrit [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] les fonctionnalités dont vous devez tenir compte lors de l’écriture d’une application.  
  
<a name="intl_text"></a>   
### <a name="international-text"></a>Texte international  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]inclut un traitement intégré pour tous les [!INCLUDE[TLA#tla_winfx](../../../../includes/tlasharptla-winfx-md.md)] pris en charge les systèmes d’écriture.  
  
 Les scripts suivants sont pris en charge :  
  
-   Arabe  
  
-   Bengali  
  
-   Dévanâgarî  
  
-   Cyrillique  
  
-   Grec  
  
-   Gujarati  
  
-   Gurmukhi  
  
-   Hébreu  
  
-   Scripts idéographiques  
  
-   Kannada  
  
-   Lao  
  
-   Latin  
  
-   Malayalam  
  
-   Mongol  
  
-   Odia  
  
-   Syriaque  
  
-   Tamoul  
  
-   Telugu  
  
-   Tana  
  
-   Thaï*  
  
-   Tibétain  
  
 *Cette version prend en charge l’affichage et la modification de texte thaïlandais, mais pas la césure de mots.  
  
 Les scripts suivants ne sont pas pris en charge :  
  
-   Khmer  
  
-   Hangûl (ancien coréen)  
  
-   Myanmar  
  
-   Sinhala  
  
 Prise en charge des moteurs de système d’écriture [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] polices. [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)]les polices peuvent inclure la [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] des tables de mise en page qui permettent aux créateurs de polices de concevoir de meilleures polices typographiques internationales et haut de gamme. Le [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] tableaux de disposition de police contiennent des informations sur les substitutions de glyphe, positionnement de glyphes, la justification et de positionnement de ligne de base, permettant aux applications de traitement de texte améliorer la disposition du texte.  
  
 [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)]les polices permettent la gestion des glyphes volumineux définit à l’aide de [!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)] codage. Cet encodage est largement pris en charge au niveau international, comme les variantes de glyphes typographiques.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]rendu de texte est rendue possible par [!INCLUDE[TLA#tla_ct](../../../../includes/tlasharptla-ct-md.md)] technologie de pixel qui prend en charge l’indépendance de résolution. La lisibilité est ainsi considérablement améliorée et les documents haute qualité de style magazine peuvent être pris en charge pour tous les scripts.  
  
<a name="intl_layout"></a>   
### <a name="international-layout"></a>Disposition internationale  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] offre un moyen très pratique pour prendre en charge des dispositions horizontales, bidirectionnelles et verticales. Dans l’infrastructure de présentation du <xref:System.Windows.FrameworkElement.FlowDirection%2A> propriété peut être utilisée pour définir la disposition. Les modèles de sens du déroulement sont les suivants :  
  
-   *LeftToRight* : disposition horizontale pour le latin, les langues d’Asie orientale, etc.  
  
-   *RightToLeft* : disposition bidirectionnelle pour l’arabe, l’hébreu, etc.  
  
<a name="developing_localizable_apps"></a>   
## <a name="developing-localizable-applications"></a>Développement d’applications localisables  
 Quand vous écrivez une application destinée à être utilisée dans le monde entier, vous ne devez pas oublier que cette application doit être localisable. Les rubriques suivantes signalent certains éléments à prendre en compte.  
  
<a name="mui"></a>   
### <a name="multilingual-user-interface"></a>Interface utilisateur multilingue  
 Interfaces utilisateur multilingue (MUI) est un [!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)] prend en charge pour la commutation [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] d’une langue à l’autre. A [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application utilise le modèle assembly pour prendre en charge d’interface utilisateur multilingue. Une application contient des assemblys indépendants de la langue ainsi que des assemblys de ressources satellites dépendants de la langue. Le point d’entrée est un .EXE managé dans l’assembly principal.  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]chargeur de ressources tire parti de la [!INCLUDE[TLA2#tla_netframewk](../../../../includes/tla2sharptla-netframewk-md.md)]du Gestionnaire de ressources pour prendre en charge la recherche de ressources et de secours. Les assemblys satellites multilingues fonctionnent avec le même assembly principal. Dépend de l’assembly de ressources est chargé la <xref:System.Globalization.CultureInfo.CurrentUICulture%2A> du thread actuel.  
  
<a name="localizable_ui"></a>   
### <a name="localizable-user-interface"></a>Interface utilisateur localisable  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]les applications utilisent [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pour définir leur [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] permet aux développeurs de spécifier une hiérarchie d’objets avec un ensemble de propriétés et une logique. La principale utilisation de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] consiste à développer des [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications, mais il peut être utilisé pour spécifier une hiérarchie de n’importe quel [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] objets. La plupart des développeurs [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pour spécifier l’application [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] et utiliser un langage de programmation tel que [!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)] pour réagir à une interaction utilisateur.  
  
 À partir d’un point de vue des ressources, un [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] fichier conçu pour décrire un dépendant de la langue [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] est un élément de ressource et par conséquent, son format de distribution final doit être localisable pour prendre en charge des langues internationales. Étant donné que [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ne peut pas gérer les événements de nombreux [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] applications contiennent des blocs de code pour ce faire. Pour plus d’informations, consultez [vue d’ensemble du XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md). Code est supprimé et compilé dans différents binaires lorsqu’un [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] fichier tokenisé en la forme BAML du code XAML. Le formulaire BAML des fichiers, des images et d’autres types d’objets de ressources managées XAML est incorporé dans l’assembly des ressources satellites, pouvant être localisé dans d’autres langues, ou dans l’assembly principal, quand la localisation n’est pas nécessaire.  
  
> [!NOTE]
>  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]les applications prennent en charge toutes les [!INCLUDE[TLA2#tla_netframewk](../../../../includes/tla2sharptla-netframewk-md.md)] [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] ressources, y compris les tables de chaînes, des images et ainsi de suite.  
  
<a name="building_localizable_apps"></a>   
### <a name="building-localizable-applications"></a>Génération d’applications localisables  
 La localisation consiste à adapter une [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] à différentes cultures. Pour rendre un [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] localisable, les développeurs doivent générer toutes les ressources localisables dans un assembly de ressources d’application. L’assembly de ressources est localisé dans différentes langues, et le code-behind utilise la gestion des ressources [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] à charger. Un des fichiers requis pour un [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application est un fichier projet (.proj). Toutes les ressources que vous utilisez dans votre application doivent être comprises dans le fichier projet. Cette opération est illustrée dans l’exemple suivant, à partir d’un fichier .csproj.  
  
```xml  
<Resource Include="data\picture1.jpg"/>  
<EmbeddedResource Include="data\stringtable.en-US.restext"/>  
```  
  
 Pour utiliser une ressource dans votre application d’instancier un <xref:System.Resources.ResourceManager> et charger la ressource que vous souhaitez utiliser. L'exemple suivant illustre la procédure à suivre pour réaliser cette opération.  
  
 [!code-csharp[LocalizationResources#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationResources/CSharp/page1.xaml.cs#2)]  
  
<a name="using_clickonce"></a>   
## <a name="using-clickonce-with-localized-applications"></a>Utilisation de ClickOnce avec les applications localisées  
 ClickOnce est une nouvelle technologie de déploiement Windows Forms qui est fournis avec [!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)]. Cette technologie permet d’installer des applications et de mettre à niveau des applications web. Quand une application déployée avec ClickOnce est localisée, elle ne peut être affichée que sous la culture localisée. Par exemple, si une application déployée est localisée en japonais elle peut uniquement être affichée sur japonais [!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] pas sur anglais [!INCLUDE[TLA2#tla_win](../../../../includes/tla2sharptla-win-md.md)]. Cela pose un problème, car il s’agit d’un scénario courant pour les utilisateurs japonais exécuter une version anglaise de [!INCLUDE[TLA2#tla_win](../../../../includes/tla2sharptla-win-md.md)].  
  
 La solution à ce problème consiste à définir l’attribut de secours de langue neutre. Un développeur d’applications peut également supprimer des ressources de l’assembly principal pour les placer dans un assembly satellite correspondant à une culture spécifique. Pour contrôler ce processus, utilisez le <xref:System.Resources.NeutralResourcesLanguageAttribute>. Le constructeur de la <xref:System.Resources.NeutralResourcesLanguageAttribute> classe a deux signatures, celle qui prend un <xref:System.Resources.UltimateResourceFallbackLocation> paramètre pour spécifier l’emplacement où le <xref:System.Resources.ResourceManager> doit extraire les ressources de secours : assembly principal ou assembly satellite. L'exemple suivant montre comment utiliser l'attribut. Pour l’emplacement de secours ultime, le code génère la <xref:System.Resources.ResourceManager> pour rechercher les ressources dans le sous-répertoire « de » du répertoire de l’assembly en cours d’exécution.  
  
```  
[assembly: NeutralResourcesLanguageAttribute(  
    "de" , UltimateResourceFallbackLocation.Satellite)]  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de la globalisation et de la localisation WPF](../../../../docs/framework/wpf/advanced/wpf-globalization-and-localization-overview.md)
