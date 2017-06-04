---
title: "Collections and Collection Types for XAML | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 58f8e7c6-9a41-4f25-8551-c042f1315baa
caps.latest.revision: 2
author: "wadepickett"
ms.author: "wpickett"
manager: "wpickett"
caps.handback.revision: 2
---
# Collections and Collection Types for XAML
Cette rubrique explique comment modifier les propriétés des types conçus pour prendre en charge une collection, et prendre en charge la syntaxe XAML pour instancier des éléments de collection en tant qu'enfants d'élément d'un élément objet parent ou d'élément de propriété.  
  
## Concepts de collection XAML  
 Conceptuellement, toute relation en XAML où il y a plusieurs éléments enfants dans la portée d'un élément d'élément objet XAML ou de propriété XAML doit être implémentée en tant que collection.  Cette collection doit être associée à une propriété XAML particulière du type XAML qui est le parent de cette relation.  La propriété doit être une collection parce qu'un processeur XAML compte assigner chaque élément dans le balisage pour être un élément récemment ajouté de la propriété de collection de stockage.  
  
 Au niveau de langage XAML, les spécifications précises de la prise en charge des collections ne sont pas complètement définies.  Le concept d'une collection peut être ou une liste ou un dictionnaire \(mais pas les deux\) est défini au niveau de langage XAML, mais que les types de stockage représentent des listes ou des dictionnaires n'est pas défini par le langage XAML.  
  
 Dans les services XAML.NET Framework, le concept de la prise en charge des collections XAML est plus précis en termes de types de stockage du .NET Framework.  Spécifiquement, la prise en charge XAML des collections est basé sur plusieurs concepts et API.NET Framework utilisés pour la programmation.NET Framework de listes et de dictionnaires en général.  
  
1.  l'interface d' <xref:System.Collections.IList> indique une collection de listes.  
  
2.  l'interface d' <xref:System.Collections.IDictionary> indique une collection dicionary.  
  
3.  <xref:System.Array> représente des méthodes d' <xref:System.Collections.IList> d'un tableau, et prend en charge d'un tableau.  
  
 Dans chacun de ces concepts de collection, un processeur XAML des services XAML.NET Framework compte appeler la méthode d' `Add` sur une instance spécifique du type de propriété de collection.  Ou, dans un scénario de sérialisation, un processeur XAML produit des instances distinctes de type XAML pour chaque élément trouvé dans la liste, le dictionnaire ou tableau basé sur le concept spécifique de chaque collection des « éléments ».  Ces options sont les suivantes : <xref:System.Collections.IList.Item%2A>; <xref:System.Collections.IDictionary.Item%2A>; <xref:System.Array.System%23Collections%23IList%23Item%2A> explicite pour <xref:System.Array>.  
  
## collections génériques  
 Les collections génériques peuvent être utiles pour général programmation .NET Framework, et peuvent également être utilisées pour les propriétés de collection XAML.  Toutefois, les interfaces <xref:System.Collections.Generic.IList%601> et <xref:System.Collections.Generic.IDictionary%602> génériques ne sont pas reconnues par les processeurs XAML des services XAML.NET Framework comme étant équivalentes pour <xref:System.Collections.IList> non générique ou à <xref:System.Collections.IDictionary>.  Plutôt qu'implémenter les interfaces, une approche recommandée pour les types de propriété de collections génériques consiste à dériver des classes <xref:System.Collections.Generic.List%601> ou <xref:System.Collections.Generic.Dictionary%602>.  Ces classes implémentent les interfaces non génériques et sont donc la prise en charge prévu des collections de XAML dans l'implémentation de base.  
  
## Collection en lecture seule et logique d'initialisation  
 Dans la programmation.NET Framework, il s'agit d'un modèle de design courant pour effectuer une propriété qui contient une valeur d'une collection en tant que collection en lecture seule.  Ce modèle permet l'instance qui possède la propriété de collection pour mieux contrôler ce qui arrive à la collection.  Spécifiquement, le modèle empêché le remplacement accidentel de la collection préexistante entière en définissant la propriété.  Dans ce modèle, tout accès à la collection par les appelants doit plutôt être effectuée en appelant les méthodes ou les propriétés comme pris en charge par le type de collection et\/ou les interfaces appropriées de collection telles qu' <xref:System.Collections.IList>.  
  
 À l'aide de ce modèle implique que toute classe qui expose une propriété en lecture seule de collection doit d'abord initialiser cette propriété pour gérer une collection vide.  En général l'initialisation est exécutée dans le cadre de le comportement de construction pour la classe.  Pour être utile pour XAML, il est important d'un tel logique est toujours référencée par le constructeur par défaut, car XAML appelle généralement le constructeur par défaut avant de traiter les propriétés \(des propriétés de collection ou autre\).  
  
## prise en charge et collections de système de type XAML  
 En plus de les mécanismes de base d'analyser le code XAML et remplir ou de sérialiser propriétés de collection, le système de type XAML tel qu'il est implémenté dans les services XAML.NET Framework inclut plusieurs fonctionnalités de conception qui se rapportent à des collections en XAML.  
  
1.  <xref:System.Xaml.XamlType.IsCollection%2A> retourne la valeur true si le type XAML est stocké par un type qui fournit la prise en charge des collections XAML.  
  
2.  <xref:System.Xaml.XamlType.IsDictionary%2A> et <xref:System.Xaml.XamlType.IsArray%2A> peuvent plus efficacement les identifier le mode de collecte le type XAML prend en charge.  Pour les processeurs XAML personnalisés basés sur les services XAML.NET Framework et le système de type XAML mais pas sur des implémentations existantes d' <xref:System.Xaml.XamlWriter> , savoir à quel mode de collection est utilisé peut être nécessaire afin de savoir que méthode pour appeler pour le traitement de collection.  
  
3.  Toutes les valeurs de propriété précédentes est potentiellement influencée par les substitutions d' <xref:System.Xaml.XamlType.LookupCollectionKind%2A> sur un type XAML.