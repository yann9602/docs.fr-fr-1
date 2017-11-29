---
title: "Propriétés de dépendance et chargement XAML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom dependency properties [WPF]
- dependency properties [WPF], XAML loading and
- loading XML data [WPF]
ms.assetid: 6eea9f4e-45ce-413b-a266-f08238737bf2
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 97970a8a292eee43b01b1eab235376ae9b8e6fad
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="xaml-loading-and-dependency-properties"></a>Propriétés de dépendance et chargement XAML
L’implémentation [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] actuelle de son processeur [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] connaît de manière inhérente la propriété de dépendance. Le processeur [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] utilise des méthodes de système de propriétés pour les propriétés de dépendance durant le chargement de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] binaire et le traitement des attributs correspondant à des propriétés de dépendance. Cette fonctionnalité ignore efficacement les wrappers de propriété. Lorsque vous implémentez les propriétés de dépendance personnalisées, vous devez prendre en compte pour ce comportement et doit éviter de placer tout autre code dans votre wrapper de propriété autre que les méthodes de système de propriétés <xref:System.Windows.DependencyObject.GetValue%2A> et <xref:System.Windows.DependencyObject.SetValue%2A>.  
  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Conditions préalables  
 Cette rubrique part du principe que vous savez ce que sont les propriétés de dépendance, comme consommateur et comme auteur, et que vous avez lu [Vue d’ensemble des propriétés de dépendance](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md) et [Propriétés de dépendance personnalisées](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md). Vous devez également avoir lu [Vue d’ensemble du langage XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md) et [Syntaxe XAML en détail](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md).  
  
<a name="implementation"></a>   
## <a name="the-wpf-xaml-loader-implementation-and-performance"></a>Performance et implémentation du chargeur XAML WPF  
 Pour des raisons d’implémentation, il est moins sollicite identifier une propriété comme une propriété de dépendance et d’accéder au système de la propriété <xref:System.Windows.DependencyObject.SetValue%2A> pour définir, plutôt que d’utiliser le wrapper de propriété et sa méthode setter. Cela est dû au fait qu’un processeur [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] doit déduire l’intégralité du modèle objet du code de stockage uniquement sur la base de la connaissance du type et des relations entre les membres indiqués par la structure du balisage et différentes chaînes.  
  
 Le type est recherché par une combinaison des xmlns et attributs de l’assembly, mais l’identification des membres, la détermination de qui peuvent prendre en charge définie en tant qu’attribut, et de résoudre les types qui prennent en charge par les valeurs de propriété sont autrement une grande réflexion à l’aide de <xref:System.Reflection.PropertyInfo>. Étant donné que les propriétés de dépendance sur un type donné sont accessibles comme une table de stockage via le système de propriétés, les [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] implémentation de sa [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processeur utilise cette table et déduit que toute propriété *ABC* peut être définie plus efficacement en appelant <xref:System.Windows.DependencyObject.SetValue%2A> sur le contenant <xref:System.Windows.DependencyObject> type dérivé, à l’aide de l’identificateur de propriété de dépendance *ABCProperty*.  
  
<a name="implications"></a>   
## <a name="implications-for-custom-dependency-properties"></a>Implications pour les propriétés de dépendance personnalisées  
 Du fait que l’implémentation [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] actuelle du comportement du processeur [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pour le paramètre de propriété ignore l’intégralité des wrappers, vous ne devez placer aucune logique supplémentaire dans les définitions du wrapper de votre propriété de dépendance personnalisée. Si vous intégrez cette logique dans la définition du jeu, la logique n’est pas exécutée quand la propriété est définie en [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] plutôt que dans le code.  
  
 De même, d’autres aspects de la [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processeur qui obtiennent des valeurs de propriété à partir de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] traitement également utilisez <xref:System.Windows.DependencyObject.GetValue%2A> au lieu d’utiliser le wrapper. Par conséquent, vous devez également éviter toute implémentation supplémentaire dans le `get` définition au-delà de la <xref:System.Windows.DependencyObject.GetValue%2A> appeler.  
  
 L’exemple suivant illustre une définition de propriété de dépendance recommandée avec les wrappers, où l’identificateur de propriété est stocké comme champ `public` `static` `readonly`, et les définitions `get` et `set` ne contiennent aucun code au-delà des méthodes de système de propriétés nécessaires qui définissent le stockage de la propriété de dépendance.  
  
 [!code-csharp[WPFAquariumSln#AGWithWrapper](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#agwithwrapper)]
 [!code-vb[WPFAquariumSln#AGWithWrapper](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#agwithwrapper)]  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble des propriétés de dépendance](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
 [Vue d’ensemble du langage XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [Métadonnées de propriété de dépendance](../../../../docs/framework/wpf/advanced/dependency-property-metadata.md)  
 [Propriétés de dépendance de type collection](../../../../docs/framework/wpf/advanced/collection-type-dependency-properties.md)  
 [Sécurité de propriété de dépendance](../../../../docs/framework/wpf/advanced/dependency-property-security.md)  
 [Modèles de constructeur sécurisé pour DependencyObjects](../../../../docs/framework/wpf/advanced/safe-constructor-patterns-for-dependencyobjects.md)
