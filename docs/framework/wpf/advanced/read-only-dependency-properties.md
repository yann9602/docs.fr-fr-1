---
title: "Propri&#233;t&#233;s de d&#233;pendance en lecture seule | Microsoft Docs"
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
  - "propriétés de dépendance, Lecture seule"
  - "propriétés de dépendance en lecture seule"
ms.assetid: f23d6ec9-3780-4c09-a2ff-b2f0a2deddf1
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# Propri&#233;t&#233;s de d&#233;pendance en lecture seule
Cette rubrique décrit les propriétés de dépendance en lecture seule, y compris les propriétés de dépendance en lecture seule existantes et les scénarios et techniques pour créer une propriété de dépendance en lecture seule personnalisée.  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
<a name="prerequisites"></a>   
## Composants requis  
 Cette rubrique suppose que vous maîtrisez les scénarios de base de l'implémentation d'une propriété de dépendance et que vous savez comment les métadonnées sont appliquées à une propriété de dépendance personnalisée.  Consultez [Propriétés de dépendance personnalisées](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md) et [Métadonnées de propriété de dépendance](../../../../docs/framework/wpf/advanced/dependency-property-metadata.md) pour le contexte.  
  
<a name="existing"></a>   
## Propriétés de dépendance en lecture seule existantes  
 Certaines des propriétés de dépendance définies dans l'infrastructure [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] sont en lecture seule.  En règle générale, la définition de propriétés de dépendance en lecture seule s'impose dans la mesure où ces propriétés doivent être utilisées pour déterminer des états, mais lorsque l'état est influencé par divers facteurs, la simple affectation de l'état à la propriété n'est pas désirable d'un point de vue de la conception de l'interface utilisateur.  Par exemple, la propriété <xref:System.Windows.UIElement.IsMouseOver%2A> se limite à un état de surface déterminé par l'entrée à la souris.  Toute tentative de définir par programme cette valeur en circonvenant la vraie entrée de la souris aurait des conséquences imprévisibles et provoquerait une incohérence.  
  
 Du fait que les propriétés de dépendance en lecture seule ne sont pas définissables, ces propriétés ne sont pas adaptées pour de nombreux scénarios pour lesquels elles fournissent normalement une solution \(à savoir, liaison de données, directement stylable en valeur, validation, animation, héritage\).  Bien qu'elles ne soient pas définissables, les propriétés de dépendance offrent néanmoins des fonctions supplémentaires prises en charge par les propriétés de dépendance dans le système de propriétés.  La fonction restante la plus importante est que la propriété de dépendance en lecture seule peut encore être utilisée comme déclencheur de propriété dans un style.  Vous ne pouvez pas activer des déclencheurs avec une propriété [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] normale ; seule une propriété de dépendance le permet.  La propriété <xref:System.Windows.UIElement.IsMouseOver%2A> précitée constitue un exemple parfait de scénario dans lequel il peut être très utile de définir un style pour un contrôle, où une propriété visible, telle qu'un arrière\-plan, un premier plan ou des propriétés similaires d'éléments composés dans le contrôle, change lorsque l'utilisateur place la souris sur une région définie du contrôle.  Les modifications dans une propriété de dépendance en lecture seule peuvent être également détectées par les processus d'invalidation inhérents du système de propriétés, la fonctionnalité de déclenchement de propriété étant prise en charge en interne.  
  
<a name="new"></a>   
## Création de propriétés de dépendance en lecture seule personnalisées  
 Veillez à lire la section ci\-dessus qui explique pourquoi les propriétés de dépendance en lecture seule ne fonctionnent pas dans de nombreux scénarios de propriété de dépendance types.  Mais si vous avez un scénario approprié, vous pouvez créer votre propre propriété de dépendance en lecture seule.  
  
 La majeure partie du processus de création d'une propriété de dépendance en lecture seule est identique à celles décrites dans les rubriques [Propriétés de dépendance personnalisées](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md) et [Implémenter une propriété de dépendance](../../../../docs/framework/wpf/advanced/how-to-implement-a-dependency-property.md).  Il existe trois différences importantes :  
  
-   Lorsque vous inscrivez la propriété, appelez la méthode <xref:System.Windows.DependencyProperty.RegisterReadOnly%2A> au lieu de la méthode <xref:System.Windows.DependencyProperty.Register%2A> normale pour l'inscription de la propriété.  
  
-   Lors de l'implémentation de la propriété de "wrapper" [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)], veillez à ce que le wrapper n'ait pas aussi une implémentation définie pour qu'il n'existe pas d'incohérence dans l'état de lecture seule pour le wrapper public que vous exposez.  
  
-   L'objet retourné par l'inscription en lecture seule est <xref:System.Windows.DependencyPropertyKey> et non pas <xref:System.Windows.DependencyProperty>.  Vous devez toujours stocker ce champ sous la forme d'un membre, mais en général vous ne le convertissez pas en membre public du type.  
  
 Quel que soit le champ ou la valeur privés que vous utilisez, le stockage de la propriété de dépendance en lecture seule peut être naturellement inscriptible en utilisant la logique de votre choix.  Toutefois, la méthode la plus simple pour définir la propriété soit initialement, soit dans le cadre de la logique runtime consiste à utiliser les [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] du système de propriétés, plutôt qu'à circonvenir le système de propriétés et définir le champ de stockage privé directement.  Il existe notamment une signature <xref:System.Windows.DependencyObject.SetValue%2A> qui accepte un paramètre de type <xref:System.Windows.DependencyPropertyKey>.  La manière dont vous définissez par programme cette valeur et l'emplacement où vous la définissez dans votre logique d'application affectent la manière dont vous voulez définir l'accès dans la <xref:System.Windows.DependencyPropertyKey> créée lorsque vous avez inscrit pour la première fois la propriété de dépendance.  Si vous gérez cette logique dans la classe, vous pouvez indiquer qu'elle est privée ou, si elle doit être définie depuis d'autres parties de l'assembly, vous pouvez la définir en interne.  Une approche consiste à appeler <xref:System.Windows.DependencyObject.SetValue%2A> dans un gestionnaire d'événement de classe d'un événement pertinent qui signale à une instance de classe que la valeur de propriété stockée doit être changée.  Une autre approche consiste à lier des propriétés de dépendance ensemble en utilisant des rappels <xref:System.Windows.PropertyChangedCallback> et <xref:System.Windows.CoerceValueCallback> appariés dans le cadre des métadonnées de ces propriétés pendant l'inscription.  
  
 Étant donné que <xref:System.Windows.DependencyPropertyKey> est privé et qu'il n'est pas propagé par le système de propriétés en dehors du code, une propriété de dépendance en lecture seule offre une meilleure sécurité de paramétrage qu'une propriété de dépendance en lecture\-écriture.  Pour une propriété de dépendance en lecture\-écriture, le champ d'identification est explicitement ou implicitement public et la propriété est donc largement définissable.  Pour plus d'informations, consultez [Sécurité de propriété de dépendance](../../../../docs/framework/wpf/advanced/dependency-property-security.md).  
  
## Voir aussi  
 [Vue d'ensemble des propriétés de dépendance](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)   
 [Propriétés de dépendance personnalisées](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)   
 [Application d'un style et création de modèles](../../../../docs/framework/wpf/controls/styling-and-templating.md)