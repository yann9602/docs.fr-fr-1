---
title: "&#201;v&#233;nements de modification de propri&#233;t&#233; | Microsoft Docs"
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
  - "événements de modification (WPF), propriété"
  - "créer des déclencheurs de propriété (WPF)"
  - "propriétés de dépendance (WPF), événements de modification"
  - "événements [WPF], modification dans les valeurs des propriétés"
  - "identifier les événements de modification de propriété (WPF)"
  - "événements de modification de propriété (WPF)"
  - "événements de modification de propriété (WPF), types de"
  - "déclencheurs de propriété (WPF)"
  - "déclencheurs de propriété (WPF), définition de"
  - "modifications de valeurs de propriétés (WPF)"
ms.assetid: 0a7989df-9674-4cc1-bc50-5d8ef5d9c055
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# &#201;v&#233;nements de modification de propri&#233;t&#233;
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] définit plusieurs événements déclenchés en réponse à une modification de la valeur d'une propriété.  La propriété correspond souvent à une [propriété de dépendance](GTMT).  L'événement lui\-même est quelquefois un [événement routé](GTMT) et quelquefois un événement [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] standard.  La définition de l'événement varie selon le scénario, car certaines modifications de propriété sont routées plus convenablement à travers une arborescence d'éléments, alors que d'autres modifications de propriété concernent généralement uniquement l'objet où la propriété a changé.  
  
## Identification d'un événement de modification de propriété  
 Les événements qui signalent une modification de propriété ne sont pas tous identifiés explicitement en tant qu'événements de modification de propriété, du fait d'un modèle de signature ou d'affectation de noms.  En général, la description de l'événement dans la documentation [!INCLUDE[TLA#tla_sdk](../../../../includes/tlasharptla-sdk-md.md)] indique si l'événement est attaché directement à une modification de valeur de propriété et fournit des références croisées entre la propriété et l'événement.  
  
### Événements RoutedPropertyChanged  
 Certains événements utilisent un type de données d'événement et un délégué utilisés explicitement pour les événements de modification de propriété.  Le type de données d'événement est <xref:System.Windows.RoutedPropertyChangedEventArgs%601> et le délégué est <xref:System.Windows.RoutedPropertyChangedEventHandler%601>.  Les données d'événement et le délégué comportent tous les deux un paramètre de type générique utilisé pour spécifier le type réel de la propriété changeante lorsque vous définissez le gestionnaire.  Les données d'événement contiennent deux propriétés, <xref:System.Windows.RoutedPropertyChangedEventArgs%601.OldValue%2A> et <xref:System.Windows.RoutedPropertyChangedEventArgs%601.NewValue%2A>, passées sous la forme d'un argument de type dans les données d'événement.  
  
 La partie "routée" du nom indique que l'événement de modification de propriété est inscrit en tant qu'événement routé.  L'avantage de router un événement de modification de propriété réside dans le fait que le niveau supérieur d'un contrôle peut recevoir des événements de modification de propriété si les propriétés dans les éléments enfants \(les parties composites du contrôle\) changent de valeur.  Par exemple, vous pouvez créer un contrôle qui incorpore un contrôle <xref:System.Windows.Controls.Primitives.RangeBase> tel que <xref:System.Windows.Controls.Slider>.  Si la valeur de la propriété <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> change sur la partie de curseur, vous pouvez gérer cette modification dans le contrôle parent plutôt que dans la partie.  
  
 Étant donné que vous disposez d'une ancienne valeur et d'une nouvelle valeur, il peut être tentant d'utiliser ce gestionnaire d'événements en tant que validateur de la valeur de propriété.  Toutefois, ce n'est pas l'objectif de conception de la plupart des événements de modification de propriété.  En général, les valeurs sont fournies afin que vous puissiez agir dessus dans d'autres parties logiques du code. Toutefois, il n'est pas recommandé de modifier les valeurs dans le gestionnaire d'événements, car cette opération risque de provoquer une récursivité involontaire selon l'implémentation du gestionnaire.  
  
 Si la propriété est une propriété de dépendance personnalisée ou si vous travaillez avec une classe dérivée où vous avez défini le code d'instanciation, il existe un mécanisme beaucoup plus efficace, intégré au système de propriétés [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pour suivre les modifications : les rappels de système de propriétés <xref:System.Windows.CoerceValueCallback> et <xref:System.Windows.PropertyChangedCallback>.  Pour plus d'informations sur l'utilisation du système de propriétés [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] à des fins de validation et de forçage de type, consultez [Validation et rappels de propriétés de dépendance](../../../../docs/framework/wpf/advanced/dependency-property-callbacks-and-validation.md) et [Propriétés de dépendance personnalisées](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md).  
  
### Événements DependencyPropertyChanged  
 Une autre paire de types qui font partie d'un scénario d'un événement de modification de propriétés est <xref:System.Windows.DependencyPropertyChangedEventArgs> et <xref:System.Windows.DependencyPropertyChangedEventHandler>.  Les événements relatifs à ces modifications de propriété ne sont pas routés ; il s'agit d'événements [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] standard.  <xref:System.Windows.DependencyPropertyChangedEventArgs> est un type de rapport de données d'événement inhabituel, car il ne dérive pas de <xref:System.EventArgs> ; <xref:System.Windows.DependencyPropertyChangedEventArgs> est une structure et non une classe.  
  
 Les événements qui utilisent <xref:System.Windows.DependencyPropertyChangedEventArgs> et <xref:System.Windows.DependencyPropertyChangedEventHandler> sont un peu plus courants que les événements `RoutedPropertyChanged`.  Un exemple d'événement qui utilise ces types est <xref:System.Windows.UIElement.IsMouseCapturedChanged>.  
  
 Comme <xref:System.Windows.RoutedPropertyChangedEventArgs%601>, <xref:System.Windows.DependencyPropertyChangedEventArgs> signale également une ancienne valeur et une nouvelle pour la propriété.  En outre, les mêmes considérations relatives à l'utilisation des valeurs s'appliquent ; il n'est généralement pas recommandé de remodifier les valeurs dans l'expéditeur en réponse à l'événement.  
  
## Déclencheurs de propriété  
 Un déclencheur de propriété constitue un concept étroitement lié à un événement de modification de propriété.  Un déclencheur de propriété est créé dans un style ou un modèle et il permet de créer un comportement conditionnel basé sur la valeur de la propriété où le déclencheur de propriété est assigné.  
  
 La propriété du déclencheur de propriété doit être une propriété de dépendance.  Il peut s'agir \(c'est fréquemment le cas\) d'une propriété de dépendance en lecture seule.  Vous pouvez savoir quand une propriété de dépendance exposée par un contrôle est au moins partiellement destinée à être un déclencheur de propriété si le nom de la propriété commence par "Is".  En effet, les propriétés qui ont cette désignation sont souvent des propriétés de dépendance booléennes en lecture seule où le rôle principal de la propriété vise à indiquer l'état du contrôle qui peut avoir des conséquences sur l'interface utilisateur en temps réel ; dans ce cas il s'agit d'un déclencheur de propriété.  
  
 Certaines de ces propriétés ont également un événement de modification de propriété dédié.  Par exemple, la propriété <xref:System.Windows.UIElement.IsMouseCaptured%2A> comporte un événement de modification de propriété <xref:System.Windows.UIElement.IsMouseCapturedChanged>.  La propriété elle\-même est en lecture seule, sa valeur étant ajustée par le système d'entrée. Le système d'entrée déclenche <xref:System.Windows.UIElement.IsMouseCapturedChanged> à chaque modification en temps réel.  
  
 Par rapport à un vrai événement de modification de propriété, l'utilisation d'un déclencheur de propriété afin d'agir sur une modification de propriété présente des restrictions.  
  
 Les déclencheurs de propriété passent par une logique de correspondance exacte.  Vous spécifiez une propriété et une valeur qui indique la valeur spécifique pour laquelle le déclencheur doit agir.  Par exemple : `<Setter Property="IsMouseCaptured" Value="true"> ... </Setter>`.  En raison de cette restriction, l'utilisation d'un déclencheur de propriété s'applique généralement aux propriétés booléennes ou aux propriétés qui prennent une valeur d'énumération dédiée, où la plage de valeurs possibles est suffisamment gérable pour définir un déclencheur pour chaque cas.  Des déclencheurs de propriété peuvent également exister uniquement pour des valeurs spéciales, comme dans le cas où un compteur d'éléments atteint zéro ; il n'existe pas de déclencheur prenant en compte les cas où la propriété est à nouveau affectée à une valeur différente de zéro \(au lieu d'utiliser des déclencheurs pour tous les cas, vous pouvez avoir besoin d'un gestionnaire d'événements de code ou d'un comportement par défaut qui revient de l'état du déclencheur lorsque la valeur est différente de zéro\).  
  
 La syntaxe du déclencheur de propriété est similaire à une instruction "if" dans un programme.  Si la condition de déclencheur est vraie, le "corps" \(body\) du déclencheur de propriété est "exécuté".  Le "corps" d'un déclencheur de propriété n'est pas du code. Il s'agit d'une balise  dont l'utilisation est limitée à un ou plusieurs éléments <xref:System.Windows.Setter> pour définir d'autres propriétés de l'objet où le style ou le modèle est appliqué.  
  
 Pour compenser la condition "if" d'un déclencheur de propriété comportant un nombre important de valeurs possibles, il est généralement recommandé de définir la même valeur de propriété comme valeur par défaut en utilisant <xref:System.Windows.Setter>.  Ainsi, l'accesseur Set <xref:System.Windows.Trigger> contenu est prioritaire lorsque la condition du déclencheur est vraie, tandis que le <xref:System.Windows.Setter> qui ne se trouve pas dans <xref:System.Windows.Trigger> est prioritaire lorsque la condition du déclencheur est fausse.  
  
 Les déclencheurs de propriété sont généralement appropriés pour les scénarios où une ou plusieurs propriétés d'apparence doivent changer, selon l'état d'une autre propriété dans un même élément.  
  
 Pour plus d'informations sur les déclencheurs de propriété, consultez [Application d'un style et création de modèles](../../../../docs/framework/wpf/controls/styling-and-templating.md).  
  
## Voir aussi  
 [Vue d'ensemble des événements routés](../../../../docs/framework/wpf/advanced/routed-events-overview.md)   
 [Vue d'ensemble des propriétés de dépendance](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)