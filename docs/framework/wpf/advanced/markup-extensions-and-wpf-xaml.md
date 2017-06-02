---
title: "Extensions de balisage et XAML WPF | Microsoft Docs"
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
  - "*Extension (classe)"
  - "Binding (extensions de balisage)"
  - "accolade"
  - "caractères, accolade"
  - "classes, MarkupExtension"
  - "accolades ({})"
  - "DynamicResource (extensions de balisage)"
  - "accolades littérales ({})"
  - "extensions de balisage"
  - "MarkupExtension (classe)"
  - "imbriquer la syntaxe d'extension"
  - "RelativeSource (extensions de balisage)"
  - "StaticResource (extensions de balisage)"
  - "TemplateBinding (extensions de balisage)"
  - "XAML, extensions de balisage"
ms.assetid: 618dc745-8b14-4886-833f-486d2254bb78
caps.latest.revision: 26
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 23
---
# Extensions de balisage et XAML WPF
Cette rubrique introduit le concept des extensions de balisage pour le XAML, notamment leurs règles de syntaxe, leur finalité et le modèle d'objet de classe sous\-jacent.  Les extensions de balisage sont une fonctionnalité générale du langage XAML et de l'implémentation .NET des services XAML.  Cette rubrique détaille spécifiquement des extensions de balisage pour une utilisation dans XAML WPF.  
  
   
  
<a name="XAML_Processors_and_Markup_Extensions"></a>   
## Processeurs XAML et extensions de balisage  
 En général, un analyseur XAML peut soit interpréter une valeur d'attribut en tant que chaîne littérale qui peut être convertie en une primitive ou qui la convertit en un objet d'une façon ou d'une autre.  Il peut s'agir du référencement d'un convertisseur de type ; cela est documenté dans la rubrique [TypeConverters et XAML](../../../../docs/framework/wpf/advanced/typeconverters-and-xaml.md).  Toutefois, certains scénarios peuvent nécessiter un comportement différent.  Par exemple, un processeur XAML peut recevoir pour instruction qu'une valeur d'un attribut ne doit pas avoir pour résultat de nouvel objet dans le graphique d'objet.  Au lieu de cela, l'attribut doit avoir pour résultat un graphique d'objet qui fait référence à un objet déjà construit dans une autre partie du graphique, ou objet statique.  Un autre scénario est qu'un processeur XAML peut être chargé d'utiliser une syntaxe qui fournit les arguments non définis par défaut au constructeur d'un objet. Ce sont les types de scénarios où une extension de balisage peut fournir la solution.  
  
<a name="Basic_Markup_Extension_Syntax"></a>   
## Syntaxe des extensions de balisage de base  
 Une extension de balisage peut être implémentée pour fournir les valeurs des propriétés dans une utilisation d'attribut ou d'un élément de propriété, ou les deux à la fois.  
  
 Lorsqu'elle sert à fournir une valeur d'attribut, la syntaxe qui distingue une séquence d'extension de balisage sur un processeur XAML correspond à la présence des accolades ouvrantes et fermantes \({ et }\).  Le type d'extension de balisage est alors identifié par le jeton de chaîne qui suit immédiatement l'accolade ouvrante.  
  
 Lorsqu'elle est utilisée dans la syntaxe d'un élément de propriété, une extension de balisage est visuellement identique à tout autre élément utilisé pour fournir une valeur d'élément de propriété : une déclaration d'élément XAML qui fait référence à la classe d'extension de balisage comme un élément, comprise entre les signes « inférieur à » et « supérieur à » \(\< \>\).  
  
<a name="XAML_Defined_Markup_Extensions"></a>   
## Extensions de balisage définies par XAML  
 Il existe plusieurs extensions de balisage qui ne sont pas spécifiques à l'implémentation WPF en XAML, mais sont plutôt des implémentations des intrinsèques ou des fonctionnalités XAML en tant que langage.  Ces extensions de balisage sont implémentées dans l'assembly System.Xaml dans le cadre des services XAML généraux de .NET Framework et se trouvent dans l'espace de noms XAML du langage XAML.  Quant à l'utilisation d'un balisage courant, ces extensions de balisage sont en général identifiables par le préfixe `x:` dans l'utilisation.  La classe de base <xref:System.Windows.Markup.MarkupExtension> \(également définie dans System.Xaml\) fournit le modèle que toutes les extensions de balisage doivent utiliser pour être prises en charge dans les lecteurs et les writers XAML, notamment dans le XAML de WPF.  
  
-   `x:Type` fournit l'objet <xref:System.Type> pour le type nommé.  Cette fonctionnalité est la plus fréquemment utilisée dans les styles et les modèles.  Pour plus d'informations, consultez [x:Type, extension de balisage](../../../../docs/framework/xaml-services/x-type-markup-extension.md).  
  
-   `x:Static` génère des valeurs statiques.  Les valeurs proviennent des entités de code de type de valeur qui ne désignent pas directement le type de la valeur d'une propriété cible, mais qui peuvent être évaluées en ce type.  Pour plus d'informations, consultez [x:Static, extension de balisage](../../../../docs/framework/xaml-services/x-static-markup-extension.md).  
  
-   `x:Null` spécifie `null` en tant que valeur pour une propriété et peut être utilisé pour les attributs ou les valeurs des éléments de propriétés.  Pour plus d'informations, consultez [x:Null, extension de balisage](../../../../docs/framework/xaml-services/x-null-markup-extension.md).  
  
-   `x:Array` permet la prise en charge de la création de tableaux généraux dans la syntaxe XAML, dans les cas où la prise en charge des collections assurée par les éléments de base WPF et les modèles de contrôle n'est pas délibérément utilisée.  Pour plus d'informations, consultez [x:Array, extension de balisage](../../../../docs/framework/xaml-services/x-array-markup-extension.md).  
  
> [!NOTE]
>  Le préfixe `x:` est utilisé pour le mappage d'espace de noms XAML standard des intrinsèques du langage XAML, dans l'élément racine d'un fichier ou d'une production XAML.  Par exemple, les modèles [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] pour les applications WPF initialisent un fichier XAML `x:` à l'aide de ce mappage .  Vous pouvez choisir un autre jeton de préfixe pour votre propre mappage d'espace de noms XAML. Dans cette documentation, le mappage `x:` par défaut est toutefois considéré comme le moyen d'identification de ces entités qui sont une partie définie de l'espace de noms XAML du langage XAML, par opposition à l'espace de noms par défaut de WPF ou à d'autres espaces de noms XAML non associés à une infrastructure spécifique.  
  
<a name="WPF_Specific_Markup_Extensions"></a>   
## Extensions de balisage spécifiques à WPF  
 Les extensions de balisage les plus courantes utilisées pour la programmation WPF sont celles qui prennent en charge les références de ressources \(`StaticResource` et `DynamicResource`\) et celles qui prennent en charge la liaison de données \(`Binding`\).  
  
-   `StaticResource` fournit la valeur d'une propriété en substituant la valeur d'une ressource déjà définie.  Une évaluation `StaticResource` est finalement effectuée au moment du chargement XAML et n'a pas accès au graphique d'objet pendant l'exécution. Pour plus d'informations, consultez [StaticResource, extension de balisage](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md).  
  
-   `DynamicResource` fournit la valeur d'une propriété en différant cette valeur pour être une référence à une ressource au moment de l'exécution.  Une référence à une ressource dynamique force une nouvelle recherche chaque fois qu'un accès à ladite ressource a lieu et que cette dernière a accès au graphique d'objet au moment de l'exécution.  Pour obtenir cet accès, le concept `DynamicResource` est pris en charge par les propriétés de dépendance dans le système de propriétés WPF et les expressions évaluées.  Par conséquent, vous pouvez uniquement utiliser `DynamicResource` pour une cible de propriété de dépendance.  Pour plus d'informations, consultez [DynamicResource, extension de balisage](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md).  
  
-   `Binding` fournit une valeur liée aux données pour une propriété, en utilisant le contexte de données qui s'applique à l'objet parent pendant l'exécution.  Cette extension de balisage est relativement complexe car elle active une syntaxe inline substantielle pour spécifier une liaison de données.  Pour plus d'informations, consultez [Binding, extension de balisage](../../../../docs/framework/wpf/advanced/binding-markup-extension.md).  
  
-   `RelativeSource` fournit des informations sources pour une <xref:System.Windows.Data.Binding> qui peut naviguer entre plusieurs relations possibles dans l'arborescence d'objets au moment de l'exécution.  Cela fournit une source spécialisée pour les liaisons créées dans les modèles multiusage ou créées dans le code sans connaître l'intégralité de l'arborescence d'objets environnante.  Pour plus d'informations, consultez [RelativeSource, extension de balisage](../../../../docs/framework/wpf/advanced/relativesource-markupextension.md).  
  
-   `TemplateBinding` permet à un modèle de contrôle d'utiliser les valeurs de propriétés basées sur des modèles provenant de propriétés définies par un modèle objet de la classe qui utilisera le modèle.  En d'autres termes, la propriété dans la définition du modèle peut accéder à un contexte qui existe uniquement une fois que le modèle est appliqué.  Pour plus d'informations, consultez [TemplateBinding, extension de balisage](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md).  Pour plus d'informations sur l'utilisation pratique de `TemplateBinding`, consultez [Style avec ControlTemplates, exemple](http://go.microsoft.com/fwlink/?LinkID=160041).  
  
-   `ColorConvertedBitmap` prend en charge un scénario d'acquisition d'images relativement avancé.  Pour plus d'informations, consultez [ColorConvertedBitmap, extension de balisage](../../../../docs/framework/wpf/advanced/colorconvertedbitmap-markup-extension.md).  
  
-   `ComponentResourceKey` et `ThemeDictionary` prennent en charge les aspects de la recherche de ressources, en particulier pour les ressources et les thèmes empaquetés avec des contrôles personnalisés.  Pour plus d'informations, consultez [ComponentResourceKey, extension de balisage](../../../../docs/framework/wpf/advanced/componentresourcekey-markup-extension.md), [ThemeDictionary, extension de balisage](../../../../docs/framework/wpf/advanced/themedictionary-markup-extension.md) ou [Vue d'ensemble de la création de contrôles](../../../../docs/framework/wpf/controls/control-authoring-overview.md).  
  
<a name="StarExtension"></a>   
## \* Classes d'extension  
 Pour les extensions de balisage du langage XAML général et spécifiques à WPF, le comportement de chaque extension de balisage est identifié à un processeur XAML via une classe `*Extension` dérivée de <xref:System.Windows.Markup.MarkupExtension> et fournit une implémentation de la méthode <xref:System.Windows.Markup.StaticExtension.ProvideValue%2A>.  Cette méthode sur chaque extension fournit l'objet qui est retourné lorsque l'extension de balisage est évaluée.  L'objet retourné est en général évalué selon les différents jetons de chaîne qui sont passées à l'extension de balisage.  
  
 Par exemple, la classe <xref:System.Windows.StaticResourceExtension> fournit l'implémentation de surface de recherche de ressource réelle afin que son implémentation <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A> renvoie l'objet demandé, l'entrée de cette implémentation particulière étant une chaîne utilisée pour rechercher la ressource par son `x:Key`.  Bon nombre des détails de cette implémentation sont insignifiants si vous utilisez une extension de balisage existante.  
  
 Certaines extensions de balisage n'utilisent pas d'arguments de jeton de chaîne.  La raison est que soit ils retournent une valeur statique ou cohérente, soit parce que le contexte de la valeur devant être retournée est disponible via l'un des services transmis par le paramètre `serviceProvider`.  
  
 Le modèle d'attribution de nom `*Extension` est fourni à titre de commodité et de cohérence.  Il n'est pas nécessaire pour un processeur XAML d'identifier cette classe en tant que prise en charge pour une extension de balisage.  Tant que votre base de code inclut System.Xaml et utilise l'les implémentations des services XAML .NET Framework, tout ce qui est nécessaire pour être reconnu en tant qu'extension de balisage XAML est susceptible de dériver de <xref:System.Windows.Markup.MarkupExtension> et de prendre en charge une syntaxe de construction.  WPF définit les classes d'activation de l'extension de balisage qui ne suivent pas le modèle d'attribution de nom `*Extension`, par exemple <xref:System.Windows.Data.Binding>.  En général, la raison à cela est que la classe prend en charge des scénarios au delà de prise en charge pure de l'extension de balisage.  Dans le cas de <xref:System.Windows.Data.Binding>, cette classe prend en charge l'accès à l'exécution aux méthodes et aux propriétés de l'objet pour les scénarios qui n'ont rien à voir avec le XAML.  
  
### Interprétation de la classe d'extension du texte d'initialisation  
 Les jetons de chaîne qui suivent le nom d'extension de balisage et sont toujours compris entre les accolades sont interprétés par un processeur XAML de l'une des manières suivantes :  
  
-   Une virgule représente toujours le séparateur de jetons individuels.  
  
-   Si des jetons séparés individuels ne contiennent pas de signes égal, chaque jeton est traité comme un argument de constructeur.  Chaque paramètre de constructeur doit être indiqué comme le type attendu par cette signature, et dans l'ordre approprié attendu par cette dernière.  
  
    > [!NOTE]
    >  Un processeur XAML doit appeler le constructeur correspondant au nombre d'argument du nombre de paires.  Pour cette raison, si vous implémentez une extension de balisage personnalisée, ne fournissez pas plusieurs paramètres avec le même nombre d'arguments.  Le comportement de la façon dont un processeur XAML se comporte si plusieurs chemins d'accès du constructeur d'une extension de balisage avec le même nombre de paramètres existe n'est pas défini, mais vous devez anticiper qu'un processeur XAML est autorisé à lever une exception sur l'utilisation si cette situation existe dans les définitions de type d'extension de balisage.  
  
-   Si les jetons séparés individuels contiennent des signes égal, un processeur XAML commence alors par appeler le constructeur par défaut de l'extension de balisage.  Chaque paire name\=value est ensuite interprétée comme un nom de propriété existant sur l'extension de balisage, et une valeur à assigner à cette propriété.  
  
-   S'il existe un résultat parallèle entre le comportement du constructeur et le comportement du paramètre de propriété dans une extension de balisage, peu importe le comportement que vous utilisez.  Il est plus courant d'utiliser les paires *propriété*`=`*valeur* pour les extensions de balisage qui comportent plusieurs propriétés définissables, ne fût\-ce que parce qu'elle rend votre balisage plus intentionnel et vous êtes moins susceptible d'inverser par erreur les paramètres de constructeur.  \(Lorsque vous spécifiez des paires propriété\=valeur, ces propriétés peuvent se trouver dans n'importe quel ordre.\) En outre, il n'est aucunement garanti qu'une extension de balisage fournisse un paramètre de constructeur définissant chacune de ses propriétés définissables.  Par exemple, <xref:System.Windows.Data.Binding> est une extension de balisage, avec de nombreuses propriétés définissables par le biais de l'extension au format *propriété*`=`*valeur*, mais <xref:System.Windows.Data.Binding> prend en charge deux constructeurs seulement : un constructeur par défaut et un autre qui définit un chemin d'accès initial.  
  
-   Une virgule littérale ne peut pas être transmise à une extension de balisage sans échappement.  
  
<a name="EscapeSequences"></a>   
## Séquences d'échappement et extensions de balisage  
 La gestion des attributs dans un processeur XAML utilise les accolades en tant qu'indicateurs d'une séquence d'extension de balisage.  Il est également possible, si nécessaire, de produire une valeur de caractère pour un attribut d'accolade littérale en entrant une séquence d'échappement à l'aide d'une paire d'accolades vide, suivie par l'accolade littérale.  Consultez [{}, séquence d'échappement\/extension de balisage](../../../../docs/framework/xaml-services/escape-sequence-markup-extension.md).  
  
<a name="Nesting"></a>   
## Imbrication d'extensions de balisage dans l'utilisation de XAML  
 L'imbrication de plusieurs extensions de balisage est prise en charge et chaque extension de balisage sera d'abord évaluée le plus profondément.  Considérons, par exemple, l'utilisation suivante :  
  
```  
<Setter Property="Background"  
  Value="{DynamicResource {x:Static SystemColors.ControlBrushKey}}" />  
  
```  
  
 Dans cette utilisation, l'instruction `x:Static` est évaluée en premier et retourne une chaîne.  Cette chaîne est ensuite utilisée comme argument pour `DynamicResource`.  
  
## Extensions de balisage et syntaxe des éléments de propriétés  
 Lorsqu'elle est utilisée comme un élément objet qui renseigne une valeur d'élément de propriété, une classe d'extension de balisage est visuellement indiscernable d'un élément objet dépendant du type ordinaire qui peut être utilisé en XAML.  La différence pratique entre un élément objet classique et une extension de balisage est que l'extension de balisage est évaluée en une valeur typée ou différée comme expression.  Par conséquent, les mécanismes pour toutes les erreurs de type possibles des valeurs de propriété pour l'extension de balisage sont différents, de manière similaire à la façon dont une propriété à liaison tardive est traitée dans d'autres modèles de programmation.  Un élément objet ordinaire sera évalué pour la correspondance de type par rapport à la propriété cible qu'il définit lorsque le XAML est analysé.  
  
 La plupart des extensions de balisage, lorsqu'elles sont utilisées dans la syntaxe d'élément objet pour remplir un élément de propriété, ne devraient pas contenir de contenu ou toute autre syntaxe d'élément de propriété.  Par conséquent, vous devriez fermer la balise de l'élément objet et ne fournir aucun élément enfant.  Chaque fois qu'un processeur XAML rencontre un élément objet, le constructeur de cette classe est appelé, ce qui instancie l'objet créé à partir de l'élément analysé.  Une classe d'extension de balisage n'est aucunement différente : si vous souhaitez que votre extension de balisage soit utilisable dans la syntaxe de l'élément objet, vous devez indiquer un constructeur par défaut.  Certaines extensions de balisage existantes ont au moins une valeur de propriété requise qui doit être spécifiée pour une initialisation efficace.  Si tel est le cas, cette valeur de propriété est en général donnée comme attribut de propriété sur l'élément objet.  Les extensions de balisage comportant des propriétés requises \(et les noms de ces propriétés\) seront notées dans les pages de référence [Fonctionnalités de langage pour les espaces de noms XAML \(x:\)](../../../../docs/framework/xaml-services/xaml-namespace-x-language-features.md) et [Extensions XAML WPF](../../../../docs/framework/wpf/advanced/wpf-xaml-extensions.md).  Ces pages indiqueront également si la syntaxe des éléments objet ou des attributs est rejetée pour des extensions de balisage particulières.  Il convient d'attirer l'attention sur le cas [x:Array, extension de balisage](../../../../docs/framework/xaml-services/x-array-markup-extension.md), qui ne peut pas prendre en charge la syntaxe d'attribut car le contenu de ce tableau doit être spécifié dans le balisage en tant contenu.  Le contenu des tableaux étant géré comme des objets généraux, aucun convertisseur de type par défaut de l'attribut ne peut alors être exécuté.  Par ailleurs, [x:Array, extension de balisage](../../../../docs/framework/xaml-services/x-array-markup-extension.md) requiert un paramètre `type`.  
  
## Voir aussi  
 [Vue d'ensemble du langage XAML \(WPF\)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)   
 [Fonctionnalités de langage pour les espaces de noms XAML \(x:\)](../../../../docs/framework/xaml-services/xaml-namespace-x-language-features.md)   
 [Extensions XAML WPF](../../../../docs/framework/wpf/advanced/wpf-xaml-extensions.md)   
 [StaticResource, extension de balisage](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md)   
 [Binding, extension de balisage](../../../../docs/framework/wpf/advanced/binding-markup-extension.md)   
 [DynamicResource, extension de balisage](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md)   
 [x:Type, extension de balisage](../../../../docs/framework/xaml-services/x-type-markup-extension.md)