---
title: "Événements de changement de propriété"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- dependency properties [WPF], change events
- property value changes [WPF]
- change events [WPF], property
- events [WPF], change in property values
- creating property triggers [WPF]
- property change events [WPF], types of
- property change events [WPF]
- property triggers [WPF]
- identifying changed property events [WPF]
- property triggers [WPF], definition of
ms.assetid: 0a7989df-9674-4cc1-bc50-5d8ef5d9c055
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 46a11b072731daf420e35bc9c9cfd7d4fced1fe5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="property-change-events"></a>Événements de changement de propriété
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] définit plusieurs événements déclenchés en réponse au changement de la valeur d’une propriété. Souvent, la propriété est une propriété de dépendance. L’événement lui-même est parfois un événement routé et parfois un événement [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] standard. La définition de l’événement varie selon le scénario, car certains changements de propriété sont routés de façon plus appropriée à travers une arborescence d’éléments, tandis que d’autres changements de propriété ne concernent en général que l’objet sur lequel la propriété a changé.  
  
## <a name="identifying-a-property-change-event"></a>Identification d’un événement de changement de propriété  
 Les événements qui signalent un changement de propriété ne sont pas tous explicitement identifiés comme événement de changement de propriété, selon le modèle de signature ou le modèle de renommage. En règle générale, la description de l’événement dans la documentation du [!INCLUDE[TLA#tla_sdk](../../../../includes/tlasharptla-sdk-md.md)] indique si l’événement est directement lié à un changement de valeur de propriété et fournit des références croisées entre la propriété et l’événement.  
  
### <a name="routedpropertychanged-events"></a>Événements RoutedPropertyChanged  
 Certains événements utilisent un type de données d’événement et un délégué destinés explicitement aux événements de changement de propriété. Le type de données d’événement est <xref:System.Windows.RoutedPropertyChangedEventArgs%601>, et le délégué est <xref:System.Windows.RoutedPropertyChangedEventHandler%601>. Les données d’événement et le délégué ont tous deux un paramètre de type générique utilisé pour spécifier le type réel de la propriété changée quand vous définissez le gestionnaire. Les données d’événement contient deux propriétés, <xref:System.Windows.RoutedPropertyChangedEventArgs%601.OldValue%2A> et <xref:System.Windows.RoutedPropertyChangedEventArgs%601.NewValue%2A>, qui sont toutes deux puis passé comme argument de type de l’événement données.  
  
 La partie « Routed » du nom indique que l’événement de changement de propriété est inscrit comme événement routé. L’avantage du routage d’un événement de changement de propriété est que le niveau supérieur d’un contrôle peut recevoir des événements de changement de propriété si la valeur des propriétés sur les éléments enfants (parties composites du contrôle) changent. Par exemple, vous pouvez créer un contrôle qui incorpore un <xref:System.Windows.Controls.Primitives.RangeBase> contrôle tel qu’un <xref:System.Windows.Controls.Slider>. Si la valeur de la <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> modifications apportées aux propriétés sur la partie de curseur, vous souhaiterez peut-être gérer cette modification sur le contrôle parent plutôt que sur la partie.  
  
 Comme vous avez une ancienne valeur et une nouvelle valeur, vous pouvez également utiliser ce gestionnaire d’événements comme validateur de la valeur de propriété. Toutefois, la plupart des événements de changement de propriété ne sont pas conçus dans cet objectif. En règle générale, les valeurs sont fournies pour pouvoir agir sur ces valeurs dans d’autres zones logiques de votre code, mais nous ne recommandons pas de changer les valeurs dans le gestionnaire d’événements, car cela peut entraîner une récursivité involontaire selon la façon dont votre gestionnaire est implémenté.  
  
 Si la propriété est une propriété de dépendance personnalisée, ou si vous travaillez avec une classe dérivée où vous avez défini le code d’instanciation, il est un mécanisme beaucoup plus efficace pour le suivi des modifications de propriété qui est intégrée à la [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] système de propriétés : le rappels de système de propriété <xref:System.Windows.CoerceValueCallback> et <xref:System.Windows.PropertyChangedCallback>. Pour plus d’informations sur l’utilisation du système de propriétés [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pour la validation et le forçage de type, consultez [Validation et rappels de propriétés de dépendance](../../../../docs/framework/wpf/advanced/dependency-property-callbacks-and-validation.md) et [Propriétés de dépendance personnalisées](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md).  
  
### <a name="dependencypropertychanged-events"></a>Événements DependencyPropertyChanged  
 Une autre paire de types qui font partie d’un scénario d’événement de modification de propriété est <xref:System.Windows.DependencyPropertyChangedEventArgs> et <xref:System.Windows.DependencyPropertyChangedEventHandler>. Les événements pour ces changements de propriété ne sont pas routés, ce sont des événements [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] standard. <xref:System.Windows.DependencyPropertyChangedEventArgs>est un type de rapport, car il ne dérive pas de données événement inhabituel <xref:System.EventArgs>; <xref:System.Windows.DependencyPropertyChangedEventArgs> est une structure, et non une classe.  
  
 Les événements qui utilisent <xref:System.Windows.DependencyPropertyChangedEventArgs> et <xref:System.Windows.DependencyPropertyChangedEventHandler> sont légèrement plus courantes que `RoutedPropertyChanged` événements. Est un exemple d’événement qui utilise ces types <xref:System.Windows.UIElement.IsMouseCapturedChanged>.  
  
 Comme <xref:System.Windows.RoutedPropertyChangedEventArgs%601>, <xref:System.Windows.DependencyPropertyChangedEventArgs> signale également une valeur ancienne et nouvelle pour la propriété. Par ailleurs, les mêmes considérations sur ce que vous pouvez faire avec les valeurs s’appliquent : il n’est généralement pas recommandé d’essayer de changer les valeurs dans l’expéditeur en réponse à l’événement.  
  
## <a name="property-triggers"></a>Déclencheurs de propriété  
 Le déclencheur de propriété est un concept étroitement lié à celui de l’événement de changement de propriété. Un déclencheur de propriété est créé dans un style ou un modèle, et vous permet de créer un comportement conditionnel basé sur la valeur de la propriété à laquelle le déclencheur de propriété est attribué.  
  
 La propriété d’un déclencheur de propriété doit être une propriété de dépendance. Elle peut être (et l’est souvent) une propriété de dépendance en lecture seule. Quand le nom de la propriété commence par « Is », cela signifie que la propriété de dépendance exposée par un contrôle est au moins partiellement conçue comme un déclencheur de propriété. Les propriétés qui ont cette désignation sont souvent des propriétés de dépendance booléennes en lecture seule dont l’objectif principal est de signaler l’état du contrôle susceptible d’avoir des conséquences sur l’interface utilisateur en temps réel et qui est donc un potentiel déclencheur de propriété.  
  
 Certaines de ces propriétés ont également un événement de changement de propriété dédié. Par exemple, la propriété <xref:System.Windows.UIElement.IsMouseCaptured%2A> a un événement de modification de propriété <xref:System.Windows.UIElement.IsMouseCapturedChanged>. La propriété elle-même est en lecture seule, sa valeur étant ajustée par le système d’entrée et le système d’entrée déclenche <xref:System.Windows.UIElement.IsMouseCapturedChanged> sur chaque modification en temps réel.  
  
 Par rapport à un événement de changement de propriété avec la valeur true, l’utilisation d’un déclencheur de propriété pour agir quand une propriété change présente certaines limitations.  
  
 Les déclencheurs de propriété suivent une logique de correspondance exacte. Vous spécifiez une propriété et une valeur qui est la valeur spécifique pour laquelle le déclencheur doit agir. Par exemple : `<Setter Property="IsMouseCaptured" Value="true"> ... </Setter>`. En raison de cette limitation, la majorité des utilisations de déclencheur de propriété sont réservées aux propriétés booléennes ou aux propriétés qui prennent une valeur d’énumération dédiée, où la plage de valeurs possibles est suffisamment gérable pour définir un déclencheur pour chaque cas. Les déclencheurs de propriété peuvent aussi exister uniquement pour des valeurs spéciales, comme quand un nombre d’éléments atteint zéro et qu’il n’y a pas de déclencheur quand la valeur de propriété redevient différente de zéro (ici, au lieu d’avoir des déclencheurs pour tous les cas, vous avez besoin d’un gestionnaire d’événements de code ou d’un comportement par défaut qui rétablit l’état du déclencheur quand la valeur est différente de zéro).  
  
 La syntaxe du déclencheur de propriété est analogue à une instruction « if » en programmation. Si la condition de déclenchement est true, le « corps » du déclencheur de propriété est « exécuté ». Le « corps » d’un déclencheur de propriété n’est pas du code, mais un balisage. Ce balisage est limité à un ou plusieurs <xref:System.Windows.Setter> éléments pour définir d’autres propriétés de l’objet où le style ou le modèle est appliqué.  
  
 Pour compenser la condition « if » d’un déclencheur de propriété qui possède un large éventail de valeurs possibles, il est généralement recommandé de définir cette même valeur de propriété à une valeur par défaut en utilisant un <xref:System.Windows.Setter>. De cette manière, le <xref:System.Windows.Trigger> setter de relation contenant-contenu a la priorité lorsque la condition de déclenchement est true et le <xref:System.Windows.Setter> qui n’est pas dans un <xref:System.Windows.Trigger> a la priorité à chaque fois que la condition de déclencheur est false.  
  
 Les déclencheurs de propriété sont généralement appropriés quand une ou plusieurs propriétés d’apparence doivent changer en fonction de l’état d’une autre propriété sur le même élément.  
  
 Pour plus d’informations sur les déclencheurs de propriété, consultez [Application d’un style et création de modèles](../../../../docs/framework/wpf/controls/styling-and-templating.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble des événements routés](../../../../docs/framework/wpf/advanced/routed-events-overview.md)  
 [Vue d’ensemble des propriétés de dépendance](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)
