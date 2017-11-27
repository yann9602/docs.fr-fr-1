---
title: "Vue d’ensemble des propriétés de dépendance"
description: "Une propriété qui est sauvegardée par le système de propriétés WPF est appelée une propriété de dépendance. Cette vue d’ensemble décrit le système de propriétés WPF et les fonctionnalités d’une propriété de dépendance."
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology: dotnet-wpf
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- properties [WPF], attached
- properties [WPF], overview
- styles [WPF]
- attached properties [WPF]
- data binding [WPF]
- dependency properties [WPF]
- resources [WPF], references to
ms.assetid: d119d00c-3afb-48d6-87a0-c4da4f83dee5
caps.latest.revision: "30"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: aa1ad02de74cc73ea67267de7548442078a2f5db
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="dependency-properties-overview"></a>Vue d’ensemble des propriétés de dépendance

[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] fournit un ensemble de services qui peuvent être utilisés pour étendre la fonctionnalité d’une propriété [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)]. Collectivement, ces services sont généralement appelés « système de propriétés [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ». Une propriété stockée par le système de propriétés [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] est appelée « propriété de dépendance ». Cette vue d’ensemble décrit le système de propriétés [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] et les fonctionnalités d’une propriété de dépendance, notamment comment utiliser les propriétés de dépendance existantes en XAML et dans le code. Elle introduit également des aspects spécialisés des propriétés de dépendance, tels que les métadonnées de propriétés de dépendance et comment créer votre propre propriété de dépendance dans une classe personnalisée.

## <a name="prerequisites"></a>Prérequis
Cette rubrique part du principe que vous avez une connaissance de base du [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] et de la programmation orientée objet. Pour pouvoir suivre les exemples de cette rubrique, vous devez également comprendre [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] et savoir comment écrire des applications [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Pour plus d’informations, consultez [procédure pas à pas : Ma première application de bureau WPF](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md).  
  
## <a name="dependency-properties-and-clr-properties"></a>Propriétés de dépendance et propriétés CLR
 Dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], les propriétés sont généralement exposées en tant que propriétés [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)]. À un niveau basique, vous pourriez interagir directement avec ces propriétés et ne jamais savoir qu’elles sont implémentées en tant que propriétés de dépendance. Toutefois, vous devez vous familiariser avec toutes ou une partie des fonctionnalités du système de propriétés [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], afin de pouvoir tirer parti de ces fonctionnalités.

Les propriétés de dépendance ont pour but de fournir un moyen de calculer la valeur d’une propriété en fonction de la valeur d’autres entrées. Ces autres entrées peuvent inclure des propriétés système telles que des thèmes et des préférences de l’utilisateur, des mécanismes de détermination de propriété juste-à-temps tels que la liaison de données et les animations/plans conceptuels, des modèles à plusieurs usages comme les ressources et les styles, ou des valeurs connues par l’intermédiaire de relations parent-enfant avec d’autres éléments dans l’arborescence d’éléments. En outre, une propriété de dépendance peut être implémentée pour fournir une validation autonome, des valeurs par défaut, des rappels qui surveillent les modifications apportées à d’autres propriétés, et un système capable de forcer des valeurs de propriétés en fonction d’informations d’exécution potentielles. Les classes dérivées peuvent également changer certaines caractéristiques spécifiques d’une propriété existante en substituant les métadonnées de propriété de dépendance, plutôt qu’en substituant l’implémentation réelle des propriétés existantes ou en créant de nouvelles propriétés.

Dans la référence du SDK, vous pouvez identifier quelle propriété est une propriété de dépendance par la présence de la section Informations sur les propriétés de dépendance dans la page de référence managée de cette propriété. La section d’informations sur les propriétés de dépendance inclut un lien vers le <xref:System.Windows.DependencyProperty> identificateur de champ pour cette propriété de dépendance et inclut également une liste des options de métadonnées qui sont définies pour cette propriété, les informations de substitution par classe et d’autres détails.

## <a name="dependency-properties-back-clr-properties"></a>Propriétés de dépendance sauvegarder propriétés CLR
Les propriétés de dépendance et le système de propriétés [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] étendent la fonctionnalité de propriété en fournissant un type qui stocke une propriété, en guise d’implémentation alternative au modèle standard de stockage de la propriété avec un champ privé. Le nom de ce type est <xref:System.Windows.DependencyProperty>. L’autre type important qui définit le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] système de propriétés est <xref:System.Windows.DependencyObject>. <xref:System.Windows.DependencyObject>définit la classe de base qui peut enregistrer et posséder une propriété de dépendance.

Voici un résumé de la terminologie employée dans cette documentation de [!INCLUDE[TLA#tla_sdk](../../../../includes/tlasharptla-sdk-md.md)] quand il est question des propriétés de dépendance :

- **Propriété de dépendance :** une propriété qui est sauvegardée par un <xref:System.Windows.DependencyProperty>.

- **Identificateur de propriété de dépendance :** A <xref:System.Windows.DependencyProperty> instance, ce qui est obtenu en tant que valeur de retour lors de l’inscription d’une propriété de dépendance, puis stockée comme un membre statique d’une classe. Cet identificateur est utilisé comme paramètre pour la plupart des [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] qui interagissent avec le système de propriétés [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].

- **« wrapper » CLR :** implémentations get et set pour la propriété. Ces implémentations incorporent l’identificateur de propriété de dépendance en l’utilisant dans le <xref:System.Windows.DependencyObject.GetValue%2A> et <xref:System.Windows.DependencyObject.SetValue%2A> des appels, et offrir ainsi le stockage pour la propriété à l’aide de la [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] système de propriétés.

L’exemple suivant définit la `IsSpinning` propriété de dépendance et montre la relation entre la <xref:System.Windows.DependencyProperty> identificateur à la propriété qu’il stocke.

[!code-csharp[PropertiesOvwSupport#DPFormBasic](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml.cs#dpformbasic)]
[!code-vb[PropertiesOvwSupport#DPFormBasic](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page4.xaml.vb#dpformbasic)]  
  
La convention d’affectation de noms de la propriété et sa sauvegarde <xref:System.Windows.DependencyProperty> champ est important. Le nom du champ est toujours le nom de la propriété, auquel est ajouté le suffixe `Property`. Pour plus d’informations sur cette convention et sur sa raison d’être, consultez [Propriétés de dépendance personnalisées](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md).  

## <a name="setting-property-values"></a>Définition des valeurs de propriété
Vous pouvez définir des propriétés dans le code ou en XAML.

### <a name="setting-property-values-in-xaml"></a>Définition des valeurs de propriété en XAML 
L’exemple XAML suivant spécifie le rouge comme couleur d’arrière-plan d’un bouton. Cet exemple illustre un cas où la valeur de chaîne simple d’un attribut XAML est convertie en type par l’analyseur XAML WPF dans un [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] type (un <xref:System.Windows.Media.Color>, par le biais d’un <xref:System.Windows.Media.SolidColorBrush>) dans le code généré.

[!code-xaml[PropertiesOvwSupport#MostBasicProperty](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/Page1.xaml#mostbasicproperty)]

XAML prend en charge diverses formes de syntaxe pour définir les propriétés. La syntaxe à utiliser pour une propriété particulière varie en fonction du type de valeur utilisé par une propriété, ainsi que d’autres facteurs tels que la présence d’un convertisseur de type. Pour plus d’informations sur la syntaxe XAML pour la définition de propriété, consultez [Vue d’ensemble du langage XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md) et [Syntaxe XAML en détail](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md).

En guise d’exemple de syntaxe de non-attribut, l’exemple XAML suivant montre un autre arrière-plan de bouton. Cette fois-ci, au lieu de définir une couleur unie, l’arrière-plan est défini sur une image, avec un élément représentant cette image et la source de cette image spécifiée en tant qu’attribut de l’élément imbriqué. Il s’agit d’un exemple de syntaxe d’éléments de propriété.

[!code-xaml[PropertiesOvwSupport#PESyntaxProperty](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/Page1.xaml#pesyntaxproperty)]

### <a name="setting-properties-in-code"></a>Définition des propriétés de code
 Pour définir des valeurs de propriétés de dépendance dans le code, il suffit généralement d’un appel à l’implémentation Set exposée par le « wrapper » [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)].

[!code-csharp[PropertiesOvwSupport#ProceduralPropertySet](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/Page1.xaml.cs#proceduralpropertyset)]
[!code-vb[PropertiesOvwSupport#ProceduralPropertySet](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page1.xaml.vb#proceduralpropertyset)]

Pour obtenir une valeur de propriété, il suffit aussi généralement d’appeler l’implémentation « wrapper » Get :

[!code-csharp[PropertiesOvwSupport#ProceduralPropertyGet](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/Page1.xaml.cs#proceduralpropertyget)]
 [!code-vb[PropertiesOvwSupport#ProceduralPropertyGet](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page1.xaml.vb#proceduralpropertyget)]

Vous pouvez également appeler le système de propriétés [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] <xref:System.Windows.DependencyObject.GetValue%2A> et <xref:System.Windows.DependencyObject.SetValue%2A> directement. Ce n’est généralement pas nécessaire si vous utilisez des propriétés existantes (les wrappers sont plus pratiques et fournissent une meilleure exposition de la propriété pour les outils de développement), mais appeler les [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] directement convient pour certains scénarios.

Vous pouvez aussi définir les propriétés en XAML et y accéder ultérieurement dans le code, par l’intermédiaire du code-behind. Pour plus d’informations, consultez [Code-behind et XAML dans WPF](../../../../docs/framework/wpf/advanced/code-behind-and-xaml-in-wpf.md).

## <a name="property-functionality-provided-by-a-dependency-property"></a>Fonctionnalités de propriété fournies par une propriété de dépendance
Une propriété de dépendance fournit une fonctionnalité qui étend la fonctionnalité d’une propriété, par opposition à une propriété qui est stockée par un champ. Souvent, cette fonctionnalité représente ou prend en charge une fonctionnalité spécifique de l’ensemble de fonctionnalités [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] global :

- [Ressources](#resources)

- [Liaison de données](#data-binding)

- [Styles](#styles)

- [Animations](#animations)

- [Substitutions de métadonnées](#metadata-overrides)

- [Héritage de valeur de propriété](#property-value-inheritance)

- [Intégration du concepteur WPF](#wpf-designer-integration)

### <a name="resources"></a>Ressources
Une valeur de propriété de dépendance peut être définie en référençant une ressource. Les ressources sont généralement spécifiées en tant que valeur de propriété `Resources` d’un élément racine de page ou de l’application (ces emplacements autorisent l’accès le plus commode à la ressource). L’exemple suivant montre comment définir un <xref:System.Windows.Media.SolidColorBrush> ressource.

[!code-xaml[PropertiesOvwSupport#ResourcesResource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page2.xaml#resourcesresource)]

Une fois la ressource définie, vous pouvez la référencer et l’utiliser pour fournir une valeur de propriété :

[!code-xaml[PropertiesOvwSupport#ResourcesReference](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page2.xaml#resourcesreference)]

Cette ressource particulière est référencée en tant qu’[Extension de balisage DynamicResource](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md) (en XAML WPF, vous pouvez utiliser une référence de ressource statique ou dynamique). Pour utiliser une référence de ressource dynamique, vous devez définir une propriété de dépendance. C’est donc spécifiquement l’usage de référence de ressource dynamique qui est activée par le système de propriétés [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Pour plus d’informations, consultez [Ressources XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md).

> [!NOTE]
> Les ressources sont traitées comme une valeur locale, ce qui signifie que si vous définissez une autre valeur locale, vous supprimez la référence de ressource. Pour plus d’informations, consultez [Priorité de la valeur de propriété de dépendance](../../../../docs/framework/wpf/advanced/dependency-property-value-precedence.md).

### <a name="data-binding"></a>Liaison de données
Une propriété de dépendance peut référencer une valeur par l’intermédiaire d’une liaison de données. Liaison de données fonctionne via une syntaxe d’extension de balisage spécifique en XAML, ou la <xref:System.Windows.Data.Binding> objet dans le code. Avec la liaison de données, la détermination de valeur de propriété finale est différée jusqu’au moment de l’exécution, quand la valeur est obtenue à partir d’une source de données.

L’exemple suivant définit la <xref:System.Windows.Controls.ContentControl.Content%2A> propriété pour un <xref:System.Windows.Controls.Button>, à l’aide d’une liaison déclarée en XAML. La liaison utilise un contexte de données hérité et un <xref:System.Windows.Data.XmlDataProvider> source de données (non affichée). La liaison elle-même spécifie la propriété source souhaitée par <xref:System.Windows.Data.Binding.XPath%2A> au sein de la source de données.

[!code-xaml[PropertiesOvwSupport#BasicInlineBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#basicinlinebinding)]

> [!NOTE]
> Les liaisons sont traitées comme une valeur locale, ce qui signifie que si vous définissez une autre valeur locale, vous supprimez la liaison. Pour plus d’informations, consultez [Priorité de la valeur de propriété de dépendance](../../../../docs/framework/wpf/advanced/dependency-property-value-precedence.md).

Propriétés de dépendance, ou la <xref:System.Windows.DependencyObject> de classe, pas en mode natif ne prennent en charge <xref:System.ComponentModel.INotifyPropertyChanged> pour générer des notifications de modifications de <xref:System.Windows.DependencyObject> valeur de propriété pour les opérations de liaison de données source. Pour plus d’informations sur la façon de créer (pour une utilisation dans la liaison de données)' des propriétés capables de signaler des changements de cible de liaison de données, consultez [Vue d’ensemble de la liaison de données](../../../../docs/framework/wpf/data/data-binding-overview.md).

### <a name="styles"></a>Styles
Les styles et modèles sont deux des principaux scénarios justifiant l’utilisation de propriétés de dépendance. Les styles sont particulièrement utiles pour configurer des propriétés qui définissent l’[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] de l’application. Ils sont généralement définis en tant que ressources en XAML. Ils interagissent avec le système de propriétés car ils contiennent généralement des « méthodes setter » pour des propriétés particulières, ainsi que des « déclencheurs » qui changent une valeur de propriété d’après la valeur en temps réel d’une autre propriété.

L’exemple suivant crée un style très simple (qui serait défini à l’intérieur d’un <xref:System.Windows.FrameworkElement.Resources%2A> dictionnaire, ne pas indiqué), puis applique ce style directement à la <xref:System.Windows.FrameworkElement.Style%2A> propriété pour un <xref:System.Windows.Controls.Button>. La méthode setter dans le style attribue le <xref:System.Windows.Controls.Control.Background%2A> propriété pour l’élément <xref:System.Windows.Controls.Button> en vert.

[!code-xaml[PropertiesOvwSupport#SimpleStyleDef](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#simplestyledef)]

[!code-xaml[PropertiesOvwSupport#SimpleStyle](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#simplestyle)]

Pour plus d’informations, consultez [Application d’un style et création de modèles](../../../../docs/framework/wpf/controls/styling-and-templating.md).

### <a name="animations"></a>Animations
Les propriétés de dépendance peuvent être animées. Quand une animation est appliquée et s’exécute, la valeur animée opère à une priorité plus élevée que toute autre valeur (par exemple une valeur locale) qu’aurait normalement la propriété.

L’exemple suivant réalise une animation le <xref:System.Windows.Controls.Control.Background%2A> sur un <xref:System.Windows.Controls.Button> propriété (techniquement, le <xref:System.Windows.Controls.Control.Background%2A> s’anime à l’aide de la syntaxe d’élément de propriété pour spécifier une valeur vide <xref:System.Windows.Media.SolidColorBrush> comme le <xref:System.Windows.Controls.Control.Background%2A>, le <xref:System.Windows.Media.SolidColorBrush.Color%2A> propriété de ce <xref:System.Windows.Media.SolidColorBrush> est la propriété qui est directement animée).

[!code-xaml[PropertiesOvwSupport#MiniAnimate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#minianimate)]

Pour plus d’informations sur l’animation de propriétés, consultez [Vue d’ensemble des animations](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md) et [Vue d’ensemble des plans conceptuels](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md).

### <a name="metadata-overrides"></a>Substitutions de métadonnées
Vous pouvez changer certains comportements d’une propriété de dépendance en substituant les métadonnées de cette propriété quand vous dérivez de la classe qui inscrit initialement la propriété de dépendance. Substitution de métadonnées repose sur la <xref:System.Windows.DependencyProperty> identificateur. Elle ne nécessite pas la réimplémentation de la propriété. Le changement de métadonnées est géré de manière native par le système de propriétés. Chaque classe contient potentiellement des métadonnées individuelles pour toutes les propriétés qui sont héritées des classes de base, sur la base de chaque type.

L’exemple suivant substitue les métadonnées pour une propriété de dépendance <xref:System.Windows.FrameworkElement.DefaultStyleKey%2A>. La substitution de ces métadonnées de propriété de dépendance particulières fait partie d’un modèle d’implémentation qui crée des contrôles capables d’utiliser les styles par défaut de thèmes.

[!code-csharp[PropertiesOvwSupport#OverrideMetadata](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml.cs#overridemetadata)]
[!code-vb[PropertiesOvwSupport#OverrideMetadata](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page3.xaml.vb#overridemetadata)]

Pour plus d’informations sur la substitution ou l’obtention de métadonnées de propriété, consultez [Métadonnées de propriété de dépendance](../../../../docs/framework/wpf/advanced/dependency-property-metadata.md).

### <a name="property-value-inheritance"></a>Héritage de valeur de propriété
Un élément peut hériter de la valeur d’une propriété de dépendance de son parent dans l’arborescence d’objets.

> [!NOTE]
> Le comportement d’héritage de valeur de propriété n’est pas activé globalement pour toutes les propriétés de dépendance, car le temps de calcul pour l’héritage a un certain impact sur les performances. L’héritage de valeur de propriété est en général activé uniquement pour les propriétés où un scénario particulier suggère que l’héritage de valeur de propriété est appropriée. Vous pouvez déterminer si une propriété de dépendance hérite en consultant la section **Informations sur les propriétés de dépendance** de cette propriété de dépendance dans la référence du SDK.

L’exemple suivant montre une liaison et définit le <xref:System.Windows.FrameworkElement.DataContext%2A> propriété qui spécifie la source de la liaison, ce qui n’était pas indiquée dans l’exemple précédent de la liaison. Les liaisons suivantes dans les objets enfants n’avez pas besoin de spécifier la source, ils peuvent utiliser la valeur héritée de <xref:System.Windows.FrameworkElement.DataContext%2A> dans le parent <xref:System.Windows.Controls.StackPanel> objet. (Un objet enfant impossible à la place également de spécifier directement son propre <xref:System.Windows.FrameworkElement.DataContext%2A> ou un <xref:System.Windows.Data.Binding.Source%2A> dans le <xref:System.Windows.Data.Binding>et à ne pas utiliser délibérément la valeur héritée pour le contexte de données de ses liaisons.)

[!code-xaml[PropertiesOvwSupport#InheritanceContext](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#inheritancecontext)]

Pour plus d’informations, consultez [Héritage de valeur de propriété](../../../../docs/framework/wpf/advanced/property-value-inheritance.md).

### <a name="wpf-designer-integration"></a>Intégration du Concepteur WPF
Un contrôle personnalisé avec des propriétés qui sont implémentées comme propriétés de dépendance reçoit la prise en charge du [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)] appropriée. La possibilité de modifier des propriétés de dépendance directes et jointes avec la fenêtre **Propriétés** constitue un bon exemple. Pour plus d’informations, consultez [Vue d’ensemble de la création de contrôles](../../../../docs/framework/wpf/controls/control-authoring-overview.md).

## <a name="dependency-property-value-precedence"></a>Priorité de valeur de propriété de dépendance
Quand vous obtenez la valeur d’une propriété de dépendance, vous obtenez potentiellement une valeur qui a été définie pour cette propriété par l’intermédiaire de l’une des autres entrées basées sur des propriétés qui participent au système de propriétés [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Il existe une priorité de valeur de propriété de dépendance, afin que différents scénarios d’obtention des valeurs par les propriétés puissent interagir de manière prévisible.

Prenons l'exemple suivant. L’exemple inclut un style qui s’applique à tous les boutons et leurs <xref:System.Windows.Controls.Control.Background%2A> propriétés, mais spécifie aussi un bouton avec un définie localement <xref:System.Windows.Controls.Control.Background%2A> valeur.

> [!NOTE]
> La documentation du SDK utilise les termes « valeur locale » ou « valeur localement définie » occasionnellement lors de la discussion des propriétés de dépendance. Une valeur localement définie est une valeur de propriété qui est définie directement sur une instance d’objet dans le code, ou en tant qu’attribut d’élément en XAML.  
  
En principe, pour le premier bouton, la propriété est définie à deux reprises, mais une seule valeur est applicable : celle ayant la priorité la plus élevée. Une valeur localement définie a la priorité la plus élevée (sauf une animation en cours d’exécution, mais aucune animation n’est applicable dans cet exemple). La valeur localement définie est donc utilisée au lieu de la valeur du Style Setter pour l’arrière-plan du premier bouton. Le deuxième bouton n’a aucune valeur locale (et aucune autre valeur ayant une priorité supérieure à celle d’un Style Setter). Par conséquent, l’arrière-plan de ce bouton provient du Style Setter.

[!code-xaml[PropertiesOvwSupport#MiniPrecedence](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#miniprecedence)]  

### <a name="why-does-dependency-property-precedence-exist"></a>Pourquoi existe-t-il la propriété de dépendance ?
En règle générale, vous ne souhaitez pas que des styles s’appliquent en permanence et qu’ils dissimulent même la valeur définie localement d’un élément spécifique (sinon, il serait très difficile d’utiliser des styles ou des éléments en général). Par conséquent, les valeurs qui proviennent de styles opèrent à une priorité plus faible que les valeurs définies localement. Pour obtenir une liste plus complète de propriétés de dépendance et pour savoir d’où la valeur effective d’une propriété de dépendance peut provenir, consultez [Priorité de la valeur de propriété de dépendance](../../../../docs/framework/wpf/advanced/dependency-property-value-precedence.md).

> [!NOTE]
> Un certain nombre de propriétés définies sur des éléments [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ne sont pas des propriétés de dépendance. De manière générale, les propriétés ont été implémentées en tant que propriétés de dépendance uniquement quand il fallait prendre en charge au moins l’un des scénarios activés par le système de propriétés : liaison de données, styles, animation, prise en charge de valeur par défaut, héritage, propriétés jointes ou invalidation.

## <a name="learning-more-about-dependency-properties"></a>En savoir plus sur les propriétés de dépendance  

- Une propriété jointe est un type de propriété qui prend en charge une syntaxe spécialisée en XAML. Souvent, une propriété jointe n’a pas de correspondance 1:1 avec une propriété [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)], et n’est pas nécessairement une propriété de dépendance. L’objectif par défaut d’une propriété jointe est de permettre aux éléments enfants de signaler des valeurs de propriété à un élément parent, même si l’élément parent et l’élément enfant n’ont pas tous deux cette propriété dans leur liste de membres de classe. Le scénario principal consiste à permettre aux éléments enfants d’informer le parent de façon dont ils doivent être présentés dans [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]; pour obtenir un exemple, consultez <xref:System.Windows.Controls.DockPanel.Dock%2A> ou <xref:System.Windows.Controls.Canvas.Left%2A>. Pour plus d’informations, consultez [Vue d’ensemble des propriétés jointes](../../../../docs/framework/wpf/advanced/attached-properties-overview.md).

- Les développeurs de composants ou d’applications peuvent souhaiter créer leur propre propriété de dépendance, afin d’activer des fonctionnalités telles que la liaison de données ou la prise en charge des styles, ou pour prendre en charge l’invalidation et le forçage de valeur. Pour plus d’informations, consultez [Propriétés de dépendance personnalisées](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md).

- Les propriétés de dépendance doivent généralement être considérées comme des propriétés publiques, accessibles ou au moins détectables par tout appelant qui a accès à une instance. Pour plus d’informations, consultez [Sécurité des propriétés de dépendance](../../../../docs/framework/wpf/advanced/dependency-property-security.md).

## <a name="see-also"></a>Voir aussi
 [Propriétés de dépendance personnalisées](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)  
 [Propriétés de dépendance en lecture seule](../../../../docs/framework/wpf/advanced/read-only-dependency-properties.md)  
 [Vue d’ensemble du langage XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [Architecture de WPF](../../../../docs/framework/wpf/advanced/wpf-architecture.md)
