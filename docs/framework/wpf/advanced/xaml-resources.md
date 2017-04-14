---
title: "Ressources XAML | Microsoft Docs"
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
  - "réutiliser des ressources"
  - "réutilisation des ressources"
  - "réutiliser des objets couramment définis"
  - "XAML, la réutilisation des ressources"
ms.assetid: 91580b89-a0a8-4889-aecb-fddf8e63175f
caps.latest.revision: 33
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 32
---
# Ressources XAML
Une ressource est un objet qui peut être réutilisé dans différents endroits de votre application. Exemples de ressources incluent des styles et des pinceaux. Cette présentation décrit comment utiliser des ressources dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Vous pouvez également créer et accéder aux ressources à l’aide de code ou indifféremment entre code et [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]. Pour plus d’informations, consultez [ressources et Code](../../../../docs/framework/wpf/advanced/resources-and-code.md).  
  
> [!NOTE]
>  Les fichiers de ressources décrites dans cette rubrique sont différents que les fichiers de ressources décrites dans [ressource d’Application WPF, de contenu et les fichiers de données](../../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md) et différent de ressources incorporés ou liés décrits dans [ressources de gestion de l’Application (.NET)](../Topic/Managing%20Application%20Resources%20\(.NET\).md).  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
<a name="usingresources"></a>   
## <a name="using-resources-in-xaml"></a>Utilisation des ressources en XAML  
 L’exemple suivant définit un <xref:System.Windows.Media.SolidColorBrush> en tant que ressource sur l’élément racine d’une page. L’exemple fait référence à la ressource, puis l’utilise pour définir les propriétés de plusieurs éléments enfants, y compris une <xref:System.Windows.Shapes.Ellipse>, un <xref:System.Windows.Controls.TextBlock>et un <xref:System.Windows.Controls.Button>.  
  
 [!code-xml[FEResourceSH_snip#XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page1.xaml#xaml)]  
  
 Chaque élément de niveau infrastructure ( <xref:System.Windows.FrameworkElement> ou <xref:System.Windows.FrameworkContentElement>) a un <xref:System.Windows.FrameworkElement.Resources%2A> propriété, qui est la propriété qui contient les ressources (comme un <xref:System.Windows.ResourceDictionary>) qui définit une ressource. Vous pouvez définir les ressources sur n’importe quel élément. Toutefois, les ressources sont souvent définies sur l’élément racine, qui est <xref:System.Windows.Controls.Page> dans l’exemple.  
  
 Chaque ressource dans un dictionnaire de ressources doit avoir une clé unique. Lorsque vous définissez des ressources dans le balisage, vous affectez la clé unique via le [x : Key Directive](../../../../docs/framework/xaml-services/x-key-directive.md). En règle générale, la clé est une chaîne ; Toutefois, vous pouvez également définir cela à d’autres types d’objet en utilisant les extensions de balisage approprié. Les clés pour les ressources sont utilisées par certaines fonctionnalités dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], notamment pour les styles, les ressources de composant et le style des données.  
  
 Après avoir défini une ressource, vous pouvez référencer la ressource à utiliser pour une valeur de propriété à l’aide d’une syntaxe d’extension de balisage de ressource qui spécifie le nom de clé, par exemple :  
  
 [!code-xml[FEResourceSH_snip#KeyNameUsage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page2.xaml#keynameusage)]  
  
 Dans l’exemple précédent, lorsque le [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] chargeur traite la valeur `{StaticResource MyBrush}` pour la <xref:System.Windows.Controls.Control.Background%2A> propriété sur <xref:System.Windows.Controls.Button>, la logique de recherche de ressources vérifie d’abord le dictionnaire de ressources pour le <xref:System.Windows.Controls.Button> élément. Si <xref:System.Windows.Controls.Button> n’a pas de définition de la clé de ressource `MyBrush` (il n’est pas le cas ; sa collection de ressources est vide), la recherche vérifie alors l’élément parent de <xref:System.Windows.Controls.Button>, c'est-à-dire <xref:System.Windows.Controls.Page>. Par conséquent, lorsque vous définissez une ressource sur le <xref:System.Windows.Controls.Page> élément racine, tous les éléments dans l’arborescence logique de la <xref:System.Windows.Controls.Page> peuvent y accéder, et vous pouvez réutiliser la même ressource pour définir la valeur d’une propriété qui accepte le <xref:System.Type> qui représente la ressource. Dans l’exemple précédent, la même `MyBrush` ressource définit deux propriétés différentes : la <xref:System.Windows.Controls.Control.Background%2A> d’un <xref:System.Windows.Controls.Button>et le <xref:System.Windows.Shapes.Shape.Fill%2A> d’un <xref:System.Windows.Shapes.Rectangle>.  
  
<a name="staticdynamic"></a>   
## <a name="static-and-dynamic-resources"></a>Ressources statiques et dynamiques  
 Une ressource peut être référencée comme une ressource statique ou une ressource dynamique. Cela en utilisant la [StaticResource Markup Extension](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md) ou [Extension de balisage DynamicResource](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md). Une extension de balisage est une fonctionnalité de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] qui permet de spécifier une référence d’objet en ayant l’extension de balisage traite la chaîne d’attribut et retourne l’objet à un [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] chargeur. Pour plus d’informations sur le comportement des extensions de balisage, consultez [Extensions de balisage et XAML WPF](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).  
  
 Lorsque vous utilisez une extension de balisage, vous fournissez généralement un ou plusieurs paramètres sous forme de chaîne qui sont traités par cette extension de balisage particulière, plutôt qu’en cours d’évaluation dans le cadre de la propriété définie. Le [StaticResource Markup Extension](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md) traite une clé en recherchant la valeur de cette clé dans tous les dictionnaires de ressources disponibles. Cela se produit pendant le chargement, qui est le point dans le temps lorsque le processus de chargement doit affecter la valeur de propriété qui prend la référence de ressource statique. Le [Extension de balisage DynamicResource](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md) à la place des processus une clé en créant une expression et cette expression reste sans évaluation jusqu'à ce que l’application s’exécute en fait, date à laquelle l’expression est évaluée et fournit une valeur.  
  
 Lorsque vous référencez une ressource, les considérations suivantes peuvent déterminer si vous utilisez une référence à une ressource statique ou une référence à une ressource dynamique :  
  
-   La conception globale de la façon dont vous créez les ressources pour votre application (par page, dans l’application, en perdre [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], dans un assembly ressource seulement).  
  
-   La fonctionnalité d’application : mise à jour des ressources dans la partie en temps réel des spécifications de votre application ?  
  
-   Le comportement de recherche respectif de ce type de référence de ressource.  
  
-   La propriété ou type de ressource et le comportement natif de ces types.  
  
### <a name="static-resources"></a>Ressources statiques  
 Références de ressources statiques travail mieux dans les circonstances suivantes :  
  
-   Conception de votre application concentre l’essentiel de l’ensemble de ses ressources dans la page ou les ressources de niveau application dictionnaires. Références de ressources statiques ne sont pas réévaluées selon les comportements d’exécution tels que le rechargement d’une page, et par conséquent, il peut y avoir des gains de performance pour éviter un grand nombre de références de ressource dynamique lorsqu’ils ne sont pas nécessaires pour la conception de votre application et les ressources.  
  
-   Vous définissez la valeur d’une propriété qui n’est pas suite un <xref:System.Windows.DependencyObject> ou <xref:System.Windows.Freezable>.  
  
-   Vous créez un dictionnaire de ressources qui est compilé dans une DLL et empaqueté dans le cadre de l’application ou partagé entre plusieurs applications.  
  
-   Vous créez un thème pour un contrôle personnalisé et définissez des ressources qui sont utilisées dans les thèmes. Dans ce cas, vous ne souhaitez généralement pas le comportement de recherche de référence de ressource dynamique, mais plutôt le comportement de référence de ressource statique afin que la recherche est prévisible et autonome dans le thème. Une ressource dynamique référence, même qu'une référence dans un thème est laissée sans évaluation jusqu'à l’exécution, et il existe un risque que lorsque le thème est appliqué, redéfinit une clé que votre thème essaie de référencer un élément local et l’élément local tombera préalable pour le thème lui-même dans la recherche. Dans ce cas, votre thème se comportera pas attendu.  
  
-   Vous utilisez des ressources pour définir le grand nombre de propriétés de dépendance. Propriétés de dépendance ont la valeur effective de la mise en cache activée par le système de propriétés, donc si vous fournissez une valeur pour une propriété de dépendance qui peut être évaluées au moment du chargement, la propriété de dépendance n’a pas rechercher une expression reevaluated et peut retourner la dernière valeur effective. Cette technique peut être un gain de performances.  
  
-   Vous souhaitez modifier la ressource sous-jacente pour tous les consommateurs ou vous souhaitez maintenir séparez des instances accessibles en écriture pour chaque consommateur à l’aide de la [x : Shared Attribute](../../../../docs/framework/xaml-services/x-shared-attribute.md).  
  
#### <a name="static-resource-lookup-behavior"></a>Comportement de recherche de ressources statiques  
  
1.  Le processus de recherche vérifie la clé du dictionnaire de ressources défini par l’élément qui définit la propriété demandée.  
  
2.  Le processus de recherche parcourt alors l’arborescence logique vers le haut, à l’élément parent et son dictionnaire de ressources. Ce processus se poursuit jusqu'à ce que l’élément racine est atteint.  
  
3.  Ensuite, les ressources d’application sont vérifiées. Ressources d’application sont ces ressources du dictionnaire de ressources défini par le <xref:System.Windows.Application> de l’objet pour votre [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.  
  
 Les références de ressources statiques dans un dictionnaire de ressources doivent faire référence à une ressource qui a déjà été définie sur le plan lexical avant la référence à une ressource. Références anticipées ne peut pas être résolus en une référence à une ressource statique. Pour cette raison, si vous utilisez des références de ressources statiques, vous devez concevoir votre structure de dictionnaire de ressources telles que les ressources destinées à une utilisation par ressource sont définis sur ou près du début de chaque dictionnaire de ressources respectif.  
  
 Recherche de ressources statiques peut s’étendre aux thèmes, ou dans les ressources système, mais cela est pris en charge seulement parce que le [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] chargeur diffère de la requête. Le rapport est nécessaire pour que le thème d’exécution lors du que chargement de la page s’applique correctement à l’application. Toutefois, références de ressources statiques aux clés qui sont connues pour exister seulement dans les thèmes ou en tant que système de ressources ne sont pas recommandées. Il s’agit, car de telles références ne sont pas réévaluées si le thème est modifié par l’utilisateur en temps réel. Une référence à une ressource dynamique est plus fiable lorsque vous demandez des ressources système ou thème. L’exception est lorsqu’un élément de thème lui-même demande une autre ressource. Ces références doivent être des références de ressources statiques, pour les raisons mentionnées précédemment.  
  
 Le comportement d’exception si une référence à une ressource statique n’est pas trouvée varie. Si la ressource a été différée, l’exception se produit lors de l’exécution. Si la ressource n’était pas différée, l’exception se produit au moment du chargement.  
  
### <a name="dynamic-resources"></a>Ressources dynamiques  
 Les ressources dynamiques fonctionnent mieux dans les circonstances suivantes :  
  
-   La valeur de la ressource dépend des conditions qui ne sont pas connues avant l’exécution. Cela inclut les ressources système ou des ressources qui sont autrement paramétrables. Par exemple, vous pouvez créer des valeurs d’accesseur Set qui font référence aux propriétés du système, comme exposé par <xref:System.Windows.SystemColors>, <xref:System.Windows.SystemFonts>, ou <xref:System.Windows.SystemParameters>. Ces valeurs sont véritablement dynamiques car elles proviennent en fin de compte l’environnement d’exécution de l’utilisateur et le système d’exploitation. Vous pouvez également avoir des thèmes de niveau application qui peuvent changer, où l’accès aux ressources de niveau page doit également intercepter la modification.  
  
-   Vous créez ou référencez des styles de thème pour un contrôle personnalisé.  
  
-   Vous envisagez d’ajuster le contenu d’un <xref:System.Windows.ResourceDictionary> pendant une durée de vie d’application.  
  
-   Vous avez une structure de ressources complexe avec des interdépendances, où une référence directe peut être nécessaire. Références de ressources statiques ne prennent pas en charge les références vers l’avant, mais les références de ressources dynamiques prennent en charge les car la ressource n’a pas besoin d’être évaluée avant l’exécution, et références anticipées ne sont donc pas un concept pertinent.  
  
-   Vous faites référence à une ressource qui est particulièrement important du point de vue d’une compilation ou une plage de travail, et la ressource ne peut pas être utilisée immédiatement lorsque la page se charge. Références de ressources statiques toujours chargement à partir de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] lorsque la page se charge ; Toutefois, une référence à une ressource dynamique ne se charge pas jusqu'à ce qu’il est réellement utilisé.  
  
-   Vous créez un style où les valeurs d’accesseur Set peuvent provenir d’autres valeurs qui sont influencées par les thèmes ou autres paramètres de l’utilisateur.  
  
-   Vous appliquez des ressources à des éléments qui peuvent être à nouveau apparentés dans l’arborescence logique pendant la durée de vie des applications. Le parent peut également modifier l’étendue de recherche de ressources, par conséquent, si vous souhaitez que la ressource d’un élément nouveau apparenté réévaluation en fonction de la nouvelle étendue, utilisez toujours une référence à une ressource dynamique.  
  
#### <a name="dynamic-resource-lookup-behavior"></a>Comportement de recherche dynamique des ressources  
 Comportement de recherche pour une référence de ressource dynamique correspond au comportement de recherche dans votre code si vous appelez <xref:System.Windows.FrameworkElement.FindResource%2A> ou <xref:System.Windows.FrameworkElement.SetResourceReference%2A>.  
  
1.  Le processus de recherche vérifie la clé du dictionnaire de ressources défini par l’élément qui définit la propriété demandée.  
  
    -   Si l’élément définit un <xref:System.Windows.FrameworkElement.Style%2A> propriété, le <xref:System.Windows.Style.Resources%2A> dictionnaire au sein de la <xref:System.Windows.Style> est activée.  
  
    -   Si l’élément définit un <xref:System.Windows.Controls.Control.Template%2A> propriété, le <xref:System.Windows.FrameworkTemplate.Resources%2A> dictionnaire au sein de la <xref:System.Windows.FrameworkTemplate> est activée.  
  
2.  Le processus de recherche parcourt alors l’arborescence logique vers le haut, à l’élément parent et son dictionnaire de ressources. Ce processus se poursuit jusqu'à ce que l’élément racine est atteint.  
  
3.  Ensuite, les ressources d’application sont vérifiées. Ressources d’application sont ces ressources du dictionnaire de ressources défini par le <xref:System.Windows.Application> de l’objet pour votre [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.  
  
4.  Dictionnaire de ressources de thème pour le thème actuellement actif est activée. Si le thème change au moment de l’exécution, la valeur est réévaluée.  
  
5.  Les ressources système sont vérifiées.  
  
 Comportement d’exception (le cas échéant) varie :  
  
-   Si une ressource a été demandée par un <xref:System.Windows.FrameworkElement.FindResource%2A> appeler et n’a pas été trouvé, une exception est levée.  
  
-   Si une ressource a été demandée par un <xref:System.Windows.FrameworkElement.TryFindResource%2A> appeler et est introuvable, aucune exception n’est levée, mais la valeur retournée est `null`. Si la valeur de propriété n’accepte pas `null`, il est toujours possible qu’une exception plus profonde soit levée (Cela dépend de la propriété définie).  
  
-   Si une ressource a été demandée par une référence à une ressource dynamique dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]et est introuvable, alors le comportement dépend du système de propriétés général, mais le comportement général est comme si aucune opération de définition de propriété s’est produite au niveau où la ressource existe. Par exemple, si vous essayez de définir l’arrière-plan d’un élément bouton à l’aide d’une ressource qui ne peut pas être déterminée, puis aucune valeur ne définie résultats, mais la valeur effective peut quand même provenir d’autres participants dans la priorité de système et la valeur de propriété. Par exemple, la valeur arrière-plan peut quand même provenir d’un style de bouton défini localement ou dans le style de thème. Pour les propriétés qui ne sont pas définies par les styles de thème, la valeur effective après une évaluation des ressources ayant échoué peut-être provenir de la valeur par défaut dans les métadonnées de propriété.  
  
#### <a name="restrictions"></a>Restrictions  
 Références de ressources dynamiques ayant quelques restrictions notables. Au moins une des opérations suivantes doit être remplie :  
  
-   La valeur de propriété doit être une propriété sur un <xref:System.Windows.FrameworkElement> ou <xref:System.Windows.FrameworkContentElement>. Que la propriété doit être soutenue par une <xref:System.Windows.DependencyProperty>.  
  
-   La référence est une valeur d’un <xref:System.Windows.Style><xref:System.Windows.Setter>.  
  
-   La valeur de propriété doit être une propriété sur un <xref:System.Windows.Freezable> qui est fourni en tant que valeur de l’un <xref:System.Windows.FrameworkElement> ou <xref:System.Windows.FrameworkContentElement> propriété, ou un <xref:System.Windows.Setter> valeur.  
  
 Étant donné que la valeur de propriété doit être un <xref:System.Windows.DependencyProperty> ou <xref:System.Windows.Freezable> propriété, la plupart des modifications de propriété peuvent se propager à l’interface utilisateur, car une modification de propriété (la valeur de ressource dynamique modifiée) est reconnue par le système de propriétés. La plupart des contrôles incluent la logique qui forcera une autre disposition d’un contrôle si une <xref:System.Windows.DependencyProperty> modifications et la propriété peut affecter la disposition. Cependant, pas toutes les propriétés qui ont un [Extension de balisage DynamicResource](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md) comme valeur sont assurées de fournir la valeur de sorte qu’ils mettent à jour en temps réel dans l’interface utilisateur. Cette fonctionnalité peut varier en fonction de la propriété, ainsi que selon le type de propriétaire de la propriété, ou même la structure logique de votre application.  
  
<a name="stylesimplicitkeys"></a>   
## <a name="styles-datatemplates-and-implicit-keys"></a>Styles, DataTemplates et clés implicites  
 Plus haut, il a été indiqué que tous les éléments dans un <xref:System.Windows.ResourceDictionary> doit avoir une clé. Toutefois, cela ne signifie pas que toutes les ressources doivent avoir explicite `x:Key`. Plusieurs types d’objet prend en charge une clé implicite lorsque défini en tant que ressource, où la valeur de clé est liée à la valeur d’une autre propriété. Il s’agit une clé implicite, alors qu’un `x:Key` attribut est une clé explicite. Vous pouvez remplacer toute clé implicite en spécifiant une clé explicite.  
  
 Un scénario très important pour les ressources est lorsque vous définissez un <xref:System.Windows.Style>. En fait, un <xref:System.Windows.Style> est presque toujours défini en tant qu’entrée dans un dictionnaire de ressources, car les styles sont par nature prévues pour être réutilisées. Pour plus d’informations sur les styles, consultez [styles et modèles](../../../../docs/framework/wpf/controls/styling-and-templating.md).  
  
 Styles des contrôles peuvent être créées avec et référencés avec une clé implicite. Les styles de thème qui définissent l’apparence par défaut d’un contrôle s’appuient sur cette clé implicite. La clé implicite du point de vue de sa requête est le <xref:System.Type> du contrôle lui-même. La clé implicite du point de vue de la définition de la ressource est la <xref:System.Windows.Style.TargetType%2A> du style. Par conséquent, si vous créez des thèmes pour les contrôles personnalisés, créant des styles qui interagissent avec des styles de thème existant, il est inutile de spécifier un [x : Key Directive](../../../../docs/framework/xaml-services/x-key-directive.md) pour que <xref:System.Windows.Style>. Et si vous souhaitez utiliser les styles de thème, vous n’avez pas besoin spécifier un style à tous les. Par exemple, la définition de style suivante fonctionne, même si le <xref:System.Windows.Style> ressource ne semble pas avoir une clé :  
  
 [!code-xml[FEResourceSH_snip#ImplicitStyle](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page2.xaml#implicitstyle)]  
  
 Que style a vraiment une clé : la clé implicite `typeof(` <xref:System.Windows.Controls.Button>`)`. Dans le balisage, vous pouvez spécifier un <xref:System.Windows.Style.TargetType%2A> directement en tant que le type de nom (ou vous pouvez éventuellement utiliser [{x : Type...}](../../../../docs/framework/xaml-services/x-type-markup-extension.md) pour retourner un <xref:System.Type>.  
  
 Grâce aux mécanismes de style de thème par défaut utilisés par [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], ce style est appliqué en tant que style d’exécution d’une <xref:System.Windows.Controls.Button> sur la page, même si le <xref:System.Windows.Controls.Button> lui-même ne tente pas de spécifier sa <xref:System.Windows.FrameworkElement.Style%2A> propriété ou une référence à une ressource spécifique pour le style. Votre style défini dans la page se trouve plus haut dans la séquence de recherche plus haut que le style de dictionnaire thème, à l’aide de la même clé que celle qui a le style de dictionnaire du thème. Vous pouvez simplement spécifier `<Button>Hello</Button>` n’importe où dans la page et le style que vous avez défini avec <xref:System.Windows.Style.TargetType%2A> de `Button` s’applique à ce bouton. Si vous le souhaitez, vous pouvez masquer toujours explicitement le style avec la même valeur de type en tant que <xref:System.Windows.Style.TargetType%2A>, pour plus de clarté dans votre balisage, mais qui est facultatif.  
  
 Les clés implicites pour les styles ne s’appliquent pas sur un contrôle si <xref:System.Windows.FrameworkElement.OverridesDefaultStyle%2A> est `true` (Notez également que <xref:System.Windows.FrameworkElement.OverridesDefaultStyle%2A> peut être défini dans le cadre du comportement natif pour la classe de contrôle, plutôt qu’explicitement sur une instance du contrôle). En outre, pour prendre en charge les clés implicites pour les scénarios de classe dérivée, le contrôle doit substituer <xref:System.Windows.FrameworkElement.DefaultStyleKey%2A> (tous les contrôles existants fournis dans le cadre de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] cela). Pour plus d’informations sur la conception du contrôle, les thèmes et les styles, consultez [recommandations en matière de conception des contrôles d’appliquer un style](../../../../docs/framework/wpf/controls/guidelines-for-designing-stylable-controls.md).  
  
 <xref:System.Windows.DataTemplate> a également une clé implicite. La clé implicite pour un <xref:System.Windows.DataTemplate> est la <xref:System.Windows.DataTemplate.DataType%2A> valeur de propriété.                  <xref:System.Windows.DataTemplate.DataType%2A> peut également être spécifié comme nom de type au lieu d’utiliser explicitement [{x : Type...} ](../../../../docs/framework/xaml-services/x-type-markup-extension.md). Pour plus d’informations, consultez [vue d’ensemble de la création de modèles de données](../../../../docs/framework/wpf/data/data-templating-overview.md).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.ResourceDictionary>   
 [Ressources d’application](../../../../docs/framework/wpf/advanced/optimizing-performance-application-resources.md)   
 [Ressources et Code](../../../../docs/framework/wpf/advanced/resources-and-code.md)   
 [Définir et référencer une ressource](../../../../docs/framework/wpf/advanced/how-to-define-and-reference-a-resource.md)   
 [Vue d’ensemble de la gestion des applications](../../../../docs/framework/wpf/app-development/application-management-overview.md)   
 [Extension de balisage x : Type](../../../../docs/framework/xaml-services/x-type-markup-extension.md)   
 [Extension de balisage de StaticResource](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md)   
 [Extension de balisage de DynamicResource](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md)