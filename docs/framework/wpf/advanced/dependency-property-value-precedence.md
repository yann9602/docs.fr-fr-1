---
title: "Priorit&#233; de la valeur de propri&#233;t&#233; de d&#233;pendance | Microsoft Docs"
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
  - "classes, propriétaires de propriétés de dépendance"
  - "propriétés de dépendance, classes en tant que propriétaires"
  - "propriétés de dépendance, métadonnées"
  - "métadonnées, propriétés de dépendance"
ms.assetid: 1fbada8e-4867-4ed1-8d97-62c07dad7ebc
caps.latest.revision: 27
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 26
---
# Priorit&#233; de la valeur de propri&#233;t&#233; de d&#233;pendance
<a name="introduction"></a> Cette rubrique explique comment les mécanismes du système de propriétés [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] peuvent affecter la valeur d'une propriété de dépendance [](GTMT) et décrit la priorité selon laquelle les aspects du système de propriétés s'appliquent à la valeur effective d'une propriété.  
  
   
  
<a name="prerequisites"></a>   
## Composants requis  
 Cette rubrique suppose que vous comprenez les propriétés de dépendance du point de vue d'un consommateur de propriétés de dépendance existantes sur les classes [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] et que vous avez lu [Vue d'ensemble des propriétés de dépendance](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md).  Pour suivre les exemples dans cette rubrique, vous devez également comprendre le [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] et savoir comment écrire des applications [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
<a name="intro"></a>   
## Le système de propriétés WPF  
 Le système de propriétés [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] offre une méthode puissante de détermination de la valeur des propriétés de dépendance à l'aide de divers facteurs, grâce à des fonctions telles que la validation de propriété en temps réel, les liaisons tardives et la notification des propriétés connexes des modifications apportées aux valeurs d'autres propriétés.  L'ordre exact et la logique utilisée pour déterminer des valeurs de propriété de dépendance sont relativement complexes.  Connaître cet ordre vous aidera à éviter des paramètres de propriété inutiles et peut vous aider à comprendre pourquoi une tentative destinée à influencer ou anticiper une valeur de propriété de dépendance n'a pas généré la valeur attendue.  
  
<a name="multiple_sets"></a>   
## Des propriétés de dépendance peuvent être définies à plusieurs endroits  
 Ce qui suit est un exemple [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] où la même propriété \(<xref:System.Windows.Controls.Control.Background%2A>\) a trois opérations de définition différentes susceptibles d'influencer la valeur.  
  
 [!code-xml[PropertiesOvwSupport#DPPrecedence](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml#dpprecedence)]  
  
 Ici, quelle couleur sera appliquée selon vous : rouge, vert ou bleu ?  
  
 À l'exception des valeurs animées et de contraintes, les jeux de propriétés locales sont définis selon la priorité la plus élevée.  Si vous définissez une valeur localement, vous pouvez vous attendre à ce que la valeur soit respectée, même au\-delà de tous styles ou modèles de contrôle.  Dans cet exemple, <xref:System.Windows.Controls.Control.Background%2A> est défini sur Rouge localement.  Par conséquent, le style défini dans cette portée, bien qu'il s'agisse d'un style implicite qui s'appliquerait sinon à tous les éléments de ce type dans cette portée, n'est pas la priorité la plus élevée pour transmettre sa valeur à la propriété <xref:System.Windows.Controls.Control.Background%2A>.  Si vous aviez supprimé la valeur locale Red de cette instance de Bouton, le style aurait la priorité et le bouton récupérerait la valeur d'arrière\-plan du style.  Dans le style, les déclencheurs sont prioritaires, de sorte que le bouton sera bleu si la souris est sur lui, et vert sinon.  
  
<a name="listing"></a>   
## Liste des priorités des paramètres de propriétés de dépendance  
 Les éléments suivants sont l'ordre définitif que le système de propriétés utilise lors de l'assignation des valeurs d'exécution des propriétés de dépendance.  La priorité la plus élevée est répertoriée en premier.  Cette liste développe quelques\-unes des généralisations effectuées dans le [Vue d'ensemble des propriétés de dépendance](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md).  
  
1.  **Contrainte du système de propriétés.** Pour plus d'informations sur la contrainte, consultez [Contrainte, Animation et Valeur de base](#animations) plus avant dans cette rubrique.  
  
2.  **Animations actives ou animations avec un comportement Hold.** Afin d'avoir un effet pratique, une animation d'une propriété doit être en mesure d'avoir priorité sur la valeur de base \(non animée\), même si cette valeur a été définie localement.  Pour plus d'informations, consultez [Contrainte, Animation et Valeur de base](#animations) plus avant dans cette rubrique.  
  
3.  **Valeur locale.** Une valeur locale peut être définie grâce à la présence de la propriété wrapper qui est également égale à la définition sous forme d'attribut ou d'élément de propriété en [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], ou par un appel à <xref:System.Windows.DependencyObject.SetValue%2A> [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] à l'aide d'une propriété d'une instance spécifique.  Si vous définissez une valeur locale en utilisant une liaison ou une ressource, celles\-ci se comportent chacune dans la priorité comme si une valeur directe était définie.  
  
4.  **Propriétés de modèle TemplatedParent.** Un élément a un <xref:System.Windows.FrameworkElement.TemplatedParent%2A> s'il a été créé dans le cadre d'un modèle \(un <xref:System.Windows.Controls.ControlTemplate> ou <xref:System.Windows.DataTemplate>\).  Pour plus d'informations sur les modalités d'application, consultez [TemplatedParent](#templatedparent) plus avant dans cette rubrique.  Dans le modèle, la priorité suivante s'applique :  
  
    1.  Déclencheurs du modèle <xref:System.Windows.FrameworkElement.TemplatedParent%2A>.  
  
    2.  Jeux de propriétés \(généralement via les attributs [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]\) dans le modèle <xref:System.Windows.FrameworkElement.TemplatedParent%2A>.  
  
5.  **Style implicite.** Ne s'applique qu'à la propriété `Style`.  La propriété `Style` est remplie par toute ressource de style pourvue d'une clé correspondant au type de cet élément.  Cette ressource de style doit exister dans la page ou l'application ; la recherche d'une ressource de style implicite ne se poursuit pas dans les thèmes.  
  
6.  **Déclencheurs de style.** Les déclencheurs dans les styles de page ou d'application \(ces styles peuvent être explicites ou implicites, mais pas des styles par défaut dont la priorité est inférieure\).  
  
7.  **Déclencheurs de modèle.** Tout déclencheur d'un modèle à l'intérieur d'un style, ou un modèle appliqué directement.  
  
8.  **Accesseurs Set de style.** Valeurs d'un <xref:System.Windows.Setter> dans les styles de page ou d'application.  
  
9. **Style \(thème\) par défaut.** Pour plus d'informations sur les modalités d'application, et comment les styles de thème sont liés aux modèles dans les styles de thème, consultez [Styles \(thème\) par défaut](#themestyles) plus avant dans cette rubrique.  Dans un style par défaut, l'ordre de priorité suivant s'applique :  
  
    1.  Déclencheurs actifs dans le style de thème.  
  
    2.  Accesseurs dans le style de thème.  
  
10. **Héritage.** Quelques propriétés de dépendance héritent leurs valeurs d'élément parents transmis aux éléments enfants, de sorte qu'elles n'ont pas besoin d'être définies spécifiquement sur chaque élément dans une application entière.  Pour plus d'informations, consultez [Héritage de la valeur de propriété](../../../../docs/framework/wpf/advanced/property-value-inheritance.md).  
  
11. **Valeur par défaut des métadonnées de la propriété de dépendance.** Toute propriété de dépendance peut avoir une valeur par défaut définie par l'inscription du système de propriétés de cette propriété particulière.  Par ailleurs, les classes dérivées qui héritent d'une propriété de dépendance peuvent, en option, substituer ces métadonnées \(y compris la valeur par défaut\) sur une base par type.  Consultez [Métadonnées de propriété de dépendance](../../../../docs/framework/wpf/advanced/dependency-property-metadata.md) pour plus d'informations.  Comme l'héritage est vérifié avant la valeur par défaut, pour une propriété héritée, la valeur par défaut d'un élément parent est prioritaire sur un élément enfant.  Par conséquent, si une propriété pouvant être héritée n'est définie nulle part, la valeur par défaut spécifiée à la racine \(ou parent\) est utilisée au lieu de la valeur par défaut de l'élément enfant.  
  
<a name="templatedparent"></a>   
## TemplatedParent  
 TemplatedParent en tant qu'élément de priorité ne s'applique à aucune propriété d'un élément que vous déclarez directement dans la balise d'application standard.  Le concept de TemplatedParent existe uniquement pour les éléments enfants dans une arborescence visuelle qui entre en vigueur via l'application du modèle.  Lorsque le système de propriétés recherche une valeur dans le modèle <xref:System.Windows.FrameworkElement.TemplatedParent%2A>, il recherche le modèle qui a créé cet élément.  Les valeurs de propriété du modèle <xref:System.Windows.FrameworkElement.TemplatedParent%2A> se comportent généralement comme s'ils étaient définis sous forme de valeur locale sur l'élément enfant, mais cette priorité moindre par rapport à la valeur locale existe parce que les modèles sont partagés potentiellement.  Pour plus d'informations, consultez <xref:System.Windows.FrameworkElement.TemplatedParent%2A>.  
  
<a name="style_property"></a>   
## La propriété de style  
 L'ordre de recherche décrit précédemment s'applique à toutes les propriétés de dépendance possibles sauf une : la propriété <xref:System.Windows.FrameworkElement.Style%2A>.  La propriété <xref:System.Windows.FrameworkElement.Style%2A> est unique dans la mesure où elle ne peut pas s'appliquer elle\-même un style, de sorte que les éléments de priorité 5 à 8 ne n'appliquent pas.  De même, l'animation ou la contrainte <xref:System.Windows.FrameworkElement.Style%2A> n'est pas recommandée \(et l'animation <xref:System.Windows.FrameworkElement.Style%2A> requerrait une classe d'animation personnalisée\).  Cela laisse trois modes de définition pour la propriété <xref:System.Windows.FrameworkElement.Style%2A> :  
  
-   **Style explicite.** La propriété <xref:System.Windows.FrameworkElement.Style%2A> est définie directement.  Dans la plupart des scénarios, le style n'est pas défini inline, mais référencé comme une ressource, par clé explicite.  Dans ce cas, la propriété Style elle\-même se comporte comme s'il s'agissait d'une valeur locale, élément de priorité 3.  
  
-   **Style implicite.** La propriété <xref:System.Windows.FrameworkElement.Style%2A> n'est pas définie directement.  Toutefois, le <xref:System.Windows.FrameworkElement.Style%2A> existe à un certain niveau dans la séquence de recherche de la ressource \(page, application\) et est indexé à l'aide d'une clé de ressource correspondant au type auquel le style sera appliqué.  Dans ce cas, la propriété <xref:System.Windows.FrameworkElement.Style%2A> agit en respectant une priorité identifiée dans la séquence comme élément 5.  Cette condition peut être détectée en utilisant <xref:System.Windows.DependencyPropertyHelper> sur la propriété <xref:System.Windows.FrameworkElement.Style%2A> et en recherchant <xref:System.Windows.BaseValueSource> dans les résultats.  
  
-   **Style par défaut**, également appelé **style de thème.** La propriété <xref:System.Windows.FrameworkElement.Style%2A> n'est pas définie directement, et sera lue en fait comme `null` jusqu'au moment de l'exécution.  Dans ce cas, le style provient de l'évaluation du thème lors de l'exécution qui fait partie du moteur de présentation [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 Dans le cas des styles implicites ne figurant pas dans les thèmes, le type doit correspondre exactement — une classe dérivée de `MyButton``Button` n'utilisera pas implicitement de style pour `Button`.  
  
<a name="themestyles"></a>   
## Styles \(thème\) par défaut  
 Chaque contrôle fourni avec [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] possède un style par défaut.  Ce style par défaut varie potentiellement en fonction du thème, c'est pourquoi ce style par défaut est parfois appelé style de thème.  
  
 Les informations les plus importantes que l'on trouve dans un style par défaut pour un contrôle est son modèle de contrôle, lequel existe dans le style de thème comme un accesseur Set pour sa propriété <xref:System.Windows.Controls.Control.Template%2A>.  Si aucun modèle n'existait à partir des styles par défaut, un contrôle sans un modèle personnalisé dans le cadre d'un style personnalisé n'aurait strictement aucun aspect visuel.  Le modèle du style par défaut donne à l'aspect visuel de chaque contrôle une structure de base, et définit également les connexions entre les propriétés définies dans l'arborescence d'éléments visuels du modèle et la classe de contrôle correspondante.  Chaque contrôle expose un jeu de propriétés qui peuvent influencer l'aspect visuel du contrôle sans remplacer complètement le modèle.  Prenons, par exemple, l'aspect visuel par défaut d'un contrôle <xref:System.Windows.Controls.Primitives.Thumb>, qui est un composant d'un <xref:System.Windows.Controls.Primitives.ScrollBar>.  
  
 Un <xref:System.Windows.Controls.Primitives.Thumb> possède certaines propriétés personnalisables.  Le modèle par défaut d'un <xref:System.Windows.Controls.Primitives.Thumb> crée une structure \/ arborescence d'éléments visuels de base avec plusieurs composants <xref:System.Windows.Controls.Border> imbriqués pour créer une apparence de biseau.  Si une propriété qui fait partie du modèle est prévue pour être exposée pour personnalisation par la classe <xref:System.Windows.Controls.Primitives.Thumb>, cette propriété doit alors être exposée par un [TemplateBinding](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md), dans le modèle.  Dans le cas de <xref:System.Windows.Controls.Primitives.Thumb>, différentes propriétés de ces bordures partagent un modèle qui crée une liaison avec des propriétés telles que <xref:System.Windows.Controls.Border.Background%2A> ou <xref:System.Windows.Controls.Border.BorderThickness%2A>.  Mais certaines autres propriétés ou dispositions visuelles sont codées de manière irréversible dans le modèle de contrôle ou sont liées à des valeurs qui proviennent directement du thème et ne peuvent pas être modifiées à moins de remplacer le modèle entier.  En général, si une propriété provient d'un parent basé sur des modèles et n'est pas exposée par une liaison de modèle, elle ne peut pas être ajustée par les styles en l'absence de méthode simple pour la cibler.  Mais cette propriété pourrait quand même être influencée par l'héritage d'une valeur de propriété dans le modèle appliqué, ou par une valeur par défaut.  
  
 Les styles de thème utilisent un type comme clé dans leurs définitions.  Toutefois, lorsque des thèmes sont appliqués à une instance d'élément donnée, la recherche de thèmes pour ce type est effectuée en vérifiant la propriété <xref:System.Windows.FrameworkElement.DefaultStyleKey%2A> sur un contrôle.  Ceci contraste avec l'utilisation du type de littéral, comme le font les styles implicites.  La valeur de <xref:System.Windows.FrameworkElement.DefaultStyleKey%2A> hériterait aux classes dérivées si l'implémenteur ne l'a pas modifiée \(la manière recommandée pour modifier la propriété consiste à ne pas la substituer au niveau de la propriété, mais de modifier sa valeur par défaut dans les métadonnées de propriété\).  Cette indirection permet aux classes de base de définir les styles de thème pour les éléments dérivés qui n'ont pas de style par ailleurs \(ou, plus important encore, qui n'ont pas de modèle dans ce style et n'auraient par conséquent rigoureusement aucun aspect visuel par défaut\).  Vous pouvez ainsi dériver `MyButton` de <xref:System.Windows.Controls.Button> et vous obtiendrez encore le modèle par défaut <xref:System.Windows.Controls.Button>.  Si vous étiez l'auteur du contrôle de `MyButton` et que vous souhaitiez un comportement différent, vous pourriez substituer les métadonnées de propriété de dépendance pour <xref:System.Windows.FrameworkElement.DefaultStyleKey%2A> sur `MyButton` pour retourner une clé différente, puis définir les styles de thème pertinents y compris le modèle pour `MyButton` que vous devez empaqueter avec votre contrôle `MyButton`.  Pour plus d'informations sur les thèmes, les styles et la création de contrôle, consultez [Vue d'ensemble de la création de contrôles](../../../../docs/framework/wpf/controls/control-authoring-overview.md).  
  
<a name="resources"></a>   
## Références à une ressource dynamique et liaison  
 Les références aux ressources dynamiques et les opérations de liaison respectent la priorité de l'emplacement par rapport auquel elles ont été définies.  Par exemple, une ressource dynamique appliquée à une valeur locale agit selon l'élément de priorité 3, une liaison pour un accesseur Set de propriété dans un style de thème est appliqué selon l'élément de priorité 9, et ainsi de suite.  Comme les références à une ressource dynamique et la liaison doivent toutes les deux être en mesure d'obtenir des valeurs de l'état d'exécution de l'application, cela implique que le processus effectif de détermination de la priorité de la valeur de propriété pour une propriété donnée se prolonge également pendant l'exécution.  
  
 Les références à une ressource dynamique ne font pas strictement partie du système de propriétés, mais elles possèdent un ordre de recherche qui leur est propre, lequel interagit avec la séquence indiquée ci\-dessus.  Cette priorité est documentée plus en détail dans les [Ressources XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md).  Le résumé de base de cette priorité est : élément par rapport à la racine de page, application, thème, système.  
  
 Les ressources dynamiques et les liaisons respectent la priorité de l'emplacement par rapport auquel elles ont été définies, mais la valeur est différée.  Une conséquence de cela est que si vous avez attribué une valeur locale à une ressource dynamique ou à une liaison, toute modification apportée à la valeur locale remplacera complètement la ressource dynamique ou la liaison.  Même si vous appelez la méthode <xref:System.Windows.DependencyObject.ClearValue%2A> pour effacer la valeur définie localement, la ressource ou la liaison dynamique ne sera pas restaurée.  En fait, si vous appelez <xref:System.Windows.DependencyObject.ClearValue%2A> sur une propriété pourvue d'une ressource ou d'une liaison dynamique \(sans valeur locale littérale\), elles seront également effacées par l'appel <xref:System.Windows.DependencyObject.ClearValue%2A>.  
  
<a name="setcurrentvalue"></a>   
## SetCurrentValue  
 La méthode <xref:System.Windows.DependencyObject.SetCurrentValue%2A> est un autre moyen de définir une propriété, mais elle ne respecte pas l'ordre de priorité.  Au lieu de cela, <xref:System.Windows.DependencyObject.SetCurrentValue%2A> vous permet de modifier la valeur d'une propriété sans remplacer la source de la valeur précédente.  Vous pouvez utiliser <xref:System.Windows.DependencyObject.SetCurrentValue%2A> chaque fois que vous souhaitez définir une valeur sans donner à cette dernière la priorité d'une valeur locale.  Par exemple, si une propriété est définie par un déclencheur, puis est assignée à une autre valeur via <xref:System.Windows.DependencyObject.SetCurrentValue%2A>, le système de propriétés respectera toujours le déclencheur, et la propriété sera modifiée si l'action du déclencheur se produit.  <xref:System.Windows.DependencyObject.SetCurrentValue%2A> vous permet de modifier la valeur de la propriété sans lui donner de source avec une priorité plus élevée.  De même, vous pouvez utiliser <xref:System.Windows.DependencyObject.SetCurrentValue%2A> pour modifier la valeur d'une propriété sans remplacer de liaison.  
  
<a name="animations"></a>   
## Contrainte, animations et valeur de base  
 La contrainte et l'animation agissent toutes les deux sur une valeur appelée "valeur de base" partout dans ce [!INCLUDE[TLA2#tla_sdk](../../../../includes/tla2sharptla-sdk-md.md)].  La valeur de base est donc toute valeur qui est déterminée via une évaluation montante parmi les éléments jusqu'à ce que l'élément 2 soit atteint.  
  
 Pour une animation, la valeur de base peut avoir un effet sur la valeur animée, si cette animation ne spécifie pas "De" et "À" pour certains comportements, ou si l'animation rétablit délibérément la valeur de base lorsqu'elle se termine.  Pour voir ce comportement en pratique, consultez [Valeurs cibles d'animation From, To et By, exemple](http://go.microsoft.com/fwlink/?LinkID=159988).  Essayez de définir les valeurs locales de la hauteur du rectangle dans l'exemple, de telle sorte que la valeur locale initiale soit différente de tout "De" dans l'animation.  Vous noterez que les animations démarrent immédiatement en utilisant les valeurs "De" et qu'elles remplacent la valeur de base une fois démarrées.  L'animation peut spécifier de retourner à la valeur trouvée avant l'animation une fois celle\-ci terminée en spécifiant Arrêt <xref:System.Windows.Media.Animation.FillBehavior>.  Après, la priorité normale est utilisée pour la détermination de la valeur de base.  
  
 Plusieurs animations peuvent être appliquées à une propriété unique, chacune de ces animations étant susceptible d'avoir été définie à partir de points différents dans la priorité des valeurs.  Toutefois, ces animations vont potentiellement grouper leurs valeurs, plutôt que d'appliquer simplement l'animation à partir de la priorité plus élevée.  Cela dépend de la manière exacte dont les animations sont définies et du type de la valeur animée.  Pour plus d'informations sur l'animation des propriétés, consultez [Vue d'ensemble de l'animation](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).  
  
 La contrainte s'applique au niveau le plus élevé.  Même une animation déjà en cours d'exécution est soumise à une contrainte de valeur.  Certaines propriétés de dépendance existantes dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] possèdent une contrainte intégrée.  Pour une propriété de dépendance personnalisée, vous définissez le comportement de contrainte pour une propriété de dépendance personnalisée en écrivant un <xref:System.Windows.CoerceValueCallback> et en passant le rappel dans le cadre des métadonnées lorsque vous créez la propriété.  Vous pouvez également substituer le comportement de contrainte de propriétés existantes en substituant les métadonnées sur cette propriété dans une classe dérivée.  La contrainte interagit avec la valeur de base de telle sorte que des contraintes dans la contrainte sont appliquées en fonction de l'existence de ces contraintes à ce moment, mais la valeur de base est encore conservée.  Par conséquent, si des contraintes dans la contrainte sont levées ultérieurement, la contrainte retournera la valeur la plus proche possible de cette valeur de base et, potentiellement, l'influence de la contrainte sur une propriété cessera dès que toutes les contraintes sont levées.  Pour plus d'informations sur le comportement de contrainte, consultez [Validation et rappels de propriétés de dépendance](../../../../docs/framework/wpf/advanced/dependency-property-callbacks-and-validation.md).  
  
<a name="triggers"></a>   
## Comportements de déclencheurs  
 Les contrôles définissent souvent des comportements de déclencheur dans le cadre de leur style par défaut dans les thèmes.  La définition de propriétés locales sur les contrôles peut empêcher les déclencheurs d'être en mesure de répondre aux événements utilisateurs, sur le plan visuel ou comportemental.  L'utilisation la plus commune d'un déclencheur de propriété est pour des propriétés de contrôle ou d'état telles que <xref:System.Windows.Controls.Primitives.Selector.IsSelected%2A>.  Par exemple, par défaut lorsqu'un <xref:System.Windows.Controls.Button> est désactivé \(le déclencheur pour <xref:System.Windows.UIElement.IsEnabled%2A> est `false`\), c'est alors la valeur <xref:System.Windows.Controls.Control.Foreground%2A> dans le style de thème qui fait que le contrôle apparaît "en grisé".  Mais si vous avez défini une valeur <xref:System.Windows.Controls.Control.Foreground%2A> locale, la priorité de cette couleur normalement grisée sera annulée par votre jeu de propriétés locales, même dans ce scénario déclenché par propriété.  Soyez prudent lorsque vous définissez des valeurs pour des propriétés possédant des comportements de déclencheur au niveau du thème, et veillez à ne pas interférer indûment avec l'expérience utilisateur prévue pour ce contrôle.  
  
<a name="clearvalue"></a>   
## ClearValue et priorité de valeur  
 La méthode <xref:System.Windows.DependencyObject.ClearValue%2A> est un moyen pratique pour effacer toute valeur appliquée localement d'une propriété de dépendance [](GTMT) définie sur un élément.  Toutefois, le fait d'appeler <xref:System.Windows.DependencyObject.ClearValue%2A> ne garantit pas que la valeur par défaut, établie dans les métadonnées pendant l'inscription de propriété, soit la nouvelle valeur effective.  Tous les autres participants dans la priorité de valeur sont encore actifs.  Seule la valeur définie localement a été supprimée de la séquence de priorité.  Par exemple, si vous appelez <xref:System.Windows.DependencyObject.ClearValue%2A> sur une propriété alors que celle\-ci est également définie par un style de thème, la valeur de thème est alors appliquée comme nouvelle valeur plutôt que la valeur par défaut basée sur les métadonnées.  Si vous souhaitez retirer du processus tous les participants de valeur de propriété et affecter à la valeur la valeur par défaut de métadonnées enregistrée, vous pouvez obtenir définitivement cette valeur par défaut en interrogeant les métadonnées de propriété de dépendance, et vous pouvez ensuite utiliser la valeur par défaut pour définir localement la propriété avec un appel à <xref:System.Windows.DependencyObject.SetValue%2A>.  
  
## Voir aussi  
 <xref:System.Windows.DependencyObject>   
 <xref:System.Windows.DependencyProperty>   
 [Vue d'ensemble des propriétés de dépendance](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)   
 [Propriétés de dépendance personnalisées](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)   
 [Validation et rappels de propriétés de dépendance](../../../../docs/framework/wpf/advanced/dependency-property-callbacks-and-validation.md)