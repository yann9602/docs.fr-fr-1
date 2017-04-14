---
title: "H&#233;ritage de la valeur de propri&#233;t&#233; | Microsoft Docs"
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
  - "héritage, valeurs des propriétés"
  - "propriétés, héritage de valeur"
  - "héritage de valeur"
ms.assetid: d7c338f9-f2bf-48ed-832c-7be58ac390e4
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# H&#233;ritage de la valeur de propri&#233;t&#233;
L'héritage de valeur de propriété est une fonctionnalité du système de propriétés [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  L'héritage de valeur de propriété permet aux éléments enfants dans une arborescence d'éléments d'obtenir la valeur d'une propriété particulière auprès d'éléments parents, en héritant cette valeur telle que définie dans l'élément parent le plus proche.  L'élément parent pourrait également avoir obtenu sa valeur par héritage de valeur de propriété. Le système effectue donc potentiellement un traitement récursif jusqu'à la racine de page.  L'héritage de valeur de propriété n'est pas le comportement par défaut du système de propriétés. Une propriété doit être établie avec un paramètre de métadonnées particulier pour pouvoir initialiser l'héritage de valeur de propriété sur les éléments enfants.  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
<a name="Property_Value_Inheritance_is_Containment_Inheritance"></a>   
## L'héritage de valeur de propriété correspond à l'héritage de contenance  
 Dans ce contexte, l'héritage n'est pas tout à fait le même concept que l'héritage dans le contexte de la programmation générale orientée objet et de type, où les classes dérivées héritent des définitions de membre de leurs classes de base.  Cette signification de l'héritage s'applique également dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] : les propriétés définies dans différentes classes de base sont exposées comme attributs pour des classes [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dérivées en cas d'utilisation comme éléments, et sont exposées comme membres pour le code.  L'héritage de valeur de propriété concerne plus particulièrement la manière dont les valeurs de propriété peuvent hériter d'un élément à un autre selon les relations parent\-enfant dans une arborescence d'éléments.  Cette arborescence d'éléments apparaît le plus clairement lors de l'imbrication d'éléments dans d'autres éléments lorsque vous définissez des applications dans le balisage [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  Vous pouvez également créer des arborescences d'objets par programme en ajoutant des objets aux collections désignées d'autres objets. L'héritage de valeur de propriété fonctionne de la même manière dans l'arborescence finie au moment de l'exécution.  
  
<a name="Practical_Applications_of_Property_Value_Inheritance"></a>   
## Applications pratiques de l'héritage de valeur de propriété  
 Les [!INCLUDE[TLA#tla_api#plural](../../../../includes/tlasharptla-apisharpplural-md.md)] [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] incluent plusieurs propriétés pour lesquelles l'héritage des propriétés est activé.  Dans le scénario classique, la propriété doit être définie une seule fois par page, mais cette propriété est également membre de l'une des classes d'éléments de base et existe donc également dans la plupart des éléments enfants.  Par exemple, la propriété <xref:System.Windows.FrameworkElement.FlowDirection%2A> contrôle le sens dans lequel le contenu passé doit être présenté et organisé dans la page.  En général, vous souhaitez que le concept de flux de texte soit géré de manière cohérente dans tous les éléments enfants.  Si le sens du déroulement a été réinitialisé pour l'une ou l'autre raison dans un niveau de l'arborescence d'éléments par un utilisateur ou par une action d'environnement, il doit être généralement réinitialisé partout.  Lorsque la propriété <xref:System.Windows.FrameworkElement.FlowDirection%2A> est faite pour hériter, la valeur ne doit être définie ou réinitialisée qu'une seule fois au niveau de l'arborescence d'éléments qui comprend les besoins de présentation de chaque page de l'application.  Même la valeur par défaut initiale héritera de cette manière.  Le modèle d'héritage de valeur de propriété permet également aux éléments individuels de réinitialiser la valeur dans les rares cas où vous souhaitez réellement avoir plusieurs sens de déroulement.  
  
<a name="Making_a_Custom_Property_Inheritable"></a>   
## Rendre une propriété personnalisée héritable  
 En modifiant les métadonnées d'une propriété personnalisée, vous pouvez également rendre vos propres propriétés personnalisées héritables.  Notez toutefois que la désignation d'une propriété comme pouvant être héritée exerce un impact sur les performances.  Lorsque cette propriété n'a pas de valeur locale établie ou de valeur obtenue par des styles, des modèles ou une liaison de données, une propriété qui peut être héritée fournit ses valeurs de propriété assignées à tous les éléments enfants dans l'arborescence logique.  
  
 Pour qu'une propriété participe à l'héritage de valeur, créez une propriété attachée personnalisée, comme décrit dans [Enregistrer une propriété jointe](../../../../docs/framework/wpf/advanced/how-to-register-an-attached-property.md).  Enregistrez la propriété avec les métadonnées \(<xref:System.Windows.FrameworkPropertyMetadata>\) et spécifiez l'option « Inherits » dans les paramètres d'options de ces métadonnées.  Veillez également à ce que la propriété ait une valeur par défaut établie, car cette valeur héritera désormais.  Bien que vous ayez enregistré la propriété comme étant attachée, vous pouvez également souhaiter créer un « wrapper » de propriété pour obtenir\/définir l'accès sur le type de propriétaire, comme vous le feriez pour une [propriété de dépendance](GTMT) « non attachée ».  Ensuite, la propriété héritable peut être définie soit en utilisant le wrapper de propriété direct sur le type de propriétaire ou les types dérivés, soit en utilisant la syntaxe de propriété attachée sur tout <xref:System.Windows.DependencyObject>.  
  
 Les propriétés attachées sont conceptuellement semblables aux propriétés globales. Vous pouvez chercher la valeur sur tout <xref:System.Windows.DependencyObject> et obtenir un résultat valide.  Le scénario classique pour les propriétés attachées consiste à définir des valeurs de propriété sur des éléments enfants. Ce scénario est plus efficace si la propriété concernée est une propriété attachée qui est toujours implicitement présente comme propriété attachée sur chaque élément \(<xref:System.Windows.DependencyObject>\) dans l'arborescence.  
  
> [!NOTE]
>  Bien que l'héritage de la valeur de propriété puisse sembler fonctionner pour les propriétés de dépendance non attachées, le comportement d'héritage d'une propriété non attachée par certaines limites d'éléments dans l'arborescence d'exécution n'est pas défini.  Utilisez toujours <xref:System.Windows.DependencyProperty.RegisterAttached%2A> pour inscrire des propriétés où vous avez spécifié <xref:System.Windows.FrameworkPropertyMetadata.Inherits%2A> dans les métadonnées.  
  
<a name="InheritanceContext"></a>   
## Héritage de valeurs de propriété au\-delà des limites d'arborescence  
 L'héritage des propriétés fonctionne en traversant une arborescence d'éléments.  Cette arborescence est souvent parallèle à l'arborescence logique.  Toutefois, lorsque vous incluez un objet de [niveau principal WPF](GTMT) dans le balisage qui définit une arborescence d'éléments \(comme un <xref:System.Windows.Media.Brush>\), vous avez créé une arborescence logique discontinue.  Une arborescence logique réelle ne s'étend pas conceptuellement au <xref:System.Windows.Media.Brush>, parce que l'arborescence logique est un concept d'[infrastructure WPF](GTMT).  Vous pouvez observer ce phénomène dans les résultats lors de l'utilisation des méthodes de <xref:System.Windows.LogicalTreeHelper>.  Toutefois, l'héritage de valeur de propriété peut rétablir la continuité de l'arborescence logique et peut toujours passer des valeurs héritées, tant que la propriété héritable a été enregistrée comme propriété attachée et qu'aucune limite de blocage d'héritage délibérée \(comme <xref:System.Windows.Controls.Frame>\) n'est rencontrée.  
  
## Voir aussi  
 [Métadonnées de propriété de dépendance](../../../../docs/framework/wpf/advanced/dependency-property-metadata.md)   
 [Vue d'ensemble des propriétés jointes](../../../../docs/framework/wpf/advanced/attached-properties-overview.md)   
 [Priorité de la valeur de propriété de dépendance](../../../../docs/framework/wpf/advanced/dependency-property-value-precedence.md)