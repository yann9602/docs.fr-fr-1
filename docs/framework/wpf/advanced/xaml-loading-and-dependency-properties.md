---
title: "Propri&#233;t&#233;s de d&#233;pendance et chargement XAML | Microsoft Docs"
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
  - "propriétés de dépendance personnalisées"
  - "propriétés de dépendance, XAML (chargement et"
  - "charger des données XML"
ms.assetid: 6eea9f4e-45ce-413b-a266-f08238737bf2
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# Propri&#233;t&#233;s de d&#233;pendance et chargement XAML
L'implémentation [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] actuelle de son processeur [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] connaît de manière inhérente la propriété de dépendance.  Le processeur [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] utilise des méthodes de système de propriétés pour les propriétés de dépendance lors du chargement de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] binaire et du traitement des attributs correspondant à des propriétés de dépendance.  Cette fonctionnalité ignore efficacement les wrappers de propriété.  Lorsque vous implémentez des propriétés de dépendance personnalisées, vous devez tenir compte de ce comportement et vous devez éviter de placer dans votre wrapper de propriété tout code autre que les méthodes de système de propriétés <xref:System.Windows.DependencyObject.GetValue%2A> et <xref:System.Windows.DependencyObject.SetValue%2A>.  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
<a name="prerequisites"></a>   
## Composants requis  
 Cette rubrique suppose que vous compreniez les propriétés de dépendance aussi bien comme consommateur que comme auteur et que vous ayez lu [Vue d'ensemble des propriétés de dépendance](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md) et [Propriétés de dépendance personnalisées](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md).  Vous devez également avoir lu [Vue d'ensemble du langage XAML \(WPF\)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md) et [Syntaxe XAML en détail](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md).  
  
<a name="implementation"></a>   
## Performance et implémentation du chargeur XAML WPF  
 Pour des raisons d'implémentation, il revient mois cher, en termes de calculs, d'identifier une propriété comme une propriété de dépendance et d'accéder à la méthode de système de propriétés <xref:System.Windows.DependencyObject.SetValue%2A> pour la définir, plutôt que d'utiliser le wrapper de propriété et son accesseur Set.  Cela est dû au fait qu'un processeur [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] doit déduire l'intégralité du modèle objet du code de stockage uniquement sur la base de la connaissance du type et des relations entre les membres indiqués par la structure du balisage et différentes chaînes.  
  
 Le type est recherché dans une combinaison d'attributs xmlns et d'assembly, mais l'identification des membres, la détermination de ceux qui accepteraient d'être définis comme attribut et la résolution des types pris en charge par les valeurs de propriété nécessiteraient sinon une grande réflexion à l'aide de <xref:System.Reflection.PropertyInfo>.  Du fait que les propriétés de dépendance sur un type donné sont accessibles comme une table de stockage dans le système de propriétés, l'implémentation [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] de son processeur [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] utilise cette table et déduit que toute propriété *ABC* donnée peut être définie plus efficacement en appelant <xref:System.Windows.DependencyObject.SetValue%2A> sur le type dérivé <xref:System.Windows.DependencyObject> contenant, en utilisant l'identificateur de propriété de dépendance *ABCProperty*.  
  
<a name="implications"></a>   
## Implications pour les propriétés de dépendance personnalisées  
 Du fait que l'implémentation [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] actuelle du comportement du processeur [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pour le paramètre de propriété ignore l'intégralité des wrappers, vous ne devez placer aucune logique supplémentaire dans les définitions du wrapper de votre propriété de dépendance personnalisée.  Si vous passez outre cette recommandation, la logique ne sera alors pas exécutée lorsque la propriété est définie en [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] plutôt que dans le code.  
  
 De la même façon, d'autres aspects du processeur [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] qui obtiennent des valeurs de propriété du traitement [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] utilisent également <xref:System.Windows.DependencyObject.GetValue%2A> plutôt que le wrapper.  Par conséquent, vous devez également éviter toute implémentation supplémentaire dans la définition `get` au\-delà de l'appel de <xref:System.Windows.DependencyObject.GetValue%2A>.  
  
 L'exemple suivant illustre une définition de propriété de dépendance recommandée avec les wrappers, où l'identificateur de propriété est stocké comme un champ `public` `static` `readonly`, et les définitions `get` et `set` ne contiennent aucun code au\-delà des méthodes de système de propriétés nécessaires qui définissent le stockage de la propriété de dépendance.  
  
 [!code-csharp[WPFAquariumSln#AGWithWrapper](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#agwithwrapper)]
 [!code-vb[WPFAquariumSln#AGWithWrapper](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#agwithwrapper)]  
  
## Voir aussi  
 [Vue d'ensemble des propriétés de dépendance](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)   
 [Vue d'ensemble du langage XAML \(WPF\)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)   
 [Métadonnées de propriété de dépendance](../../../../docs/framework/wpf/advanced/dependency-property-metadata.md)   
 [Propriétés de dépendance de type collection](../../../../docs/framework/wpf/advanced/collection-type-dependency-properties.md)   
 [Sécurité de propriété de dépendance](../../../../docs/framework/wpf/advanced/dependency-property-security.md)   
 [Modèles de constructeur sécurisé pour DependencyObjects](../../../../docs/framework/wpf/advanced/safe-constructor-patterns-for-dependencyobjects.md)