---
title: Collections et types de collections pour XAML
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 58f8e7c6-9a41-4f25-8551-c042f1315baa
caps.latest.revision: "2"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: 991360433b5fb09c13e59f63be94e0fa0ec94b61
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="collections-and-collection-types-for-xaml"></a>Collections et types de collections pour XAML
Cette rubrique décrit comment définir les propriétés des types qui sont destinés à prendre en charge une collection et pour prendre en charge la syntaxe XAML pour l’instanciation des éléments de collection en tant qu’éléments enfants d’un élément de propriété ou un élément d’objet parent.  
  
## <a name="xaml-collection-concepts"></a>Concepts de Collection XAML  
 Point de vue conceptuel, une relation en XAML dans lequel il existe plusieurs des éléments enfants de l’étendue d’un élément d’objet XAML ou élément de propriété XAML doit être implémentée comme une collection. Cette collection doit être associée à une propriété XAML particulière du type XAML qui est le parent de cette relation. La propriété doit être une collection, car un processeur XAML attend assigner chaque élément dans le balisage pour un élément qui vient d’être ajouté de la propriété de collection de stockage.  
  
 Au niveau du langage XAML, spécifications exactes de prise en charge de la collection n’ont pas été complètement définies. Le concept qu’une collection peut être une liste ou un dictionnaire (mais pas les deux) est défini au niveau du langage XAML, mais les types de stockage représentent deux listes ou des dictionnaires n’est pas définie par le langage XAML.  
  
 Dans les Services XAML .NET Framework, le concept de prise en charge de la collection XAML est plus clairement défini en termes de types de stockage de .NET Framework. Plus précisément, la prise en charge XAML pour les collections est basée sur plusieurs concepts du .NET Framework et des API qui est utilisés pour les listes et les dictionnaires de programmation générale de .NET Framework.  
  
1.  Le <xref:System.Collections.IList> interface indique une collection de listes.  
  
2.  Le <xref:System.Collections.IDictionary> interface indique une collection dicionary.  
  
3.  <xref:System.Array>représente un tableau et un tableau prend en charge <xref:System.Collections.IList> méthodes.  
  
 Dans chacun de ces concepts de la collection, un processeur XAML des Services XAML .NET Framework s’attend à appeler le `Add` méthode sur une instance spécifique de la collection du type de propriété. Ou bien, dans un scénario de sérialisation, un processeur XAML produit des instances de type XAML distinctes pour chaque élément trouvé dans la liste, un dictionnaire ou un tableau basé sur un concept spécifique de chaque collection de « Éléments ». Il s’agit : <xref:System.Collections.IList.Item%2A>; <xref:System.Collections.IDictionary.Item%2A>; explicites <xref:System.Array.System%23Collections%23IList%23Item%2A> pour <xref:System.Array>.  
  
## <a name="generic-collections"></a>Collections génériques  
 Collections génériques peuvent être utiles pour la programmation .NET Framework généraux et peuvent également être utilisées pour les propriétés de collection XAML. Toutefois, le type générique des interfaces <xref:System.Collections.Generic.IList%601> et <xref:System.Collections.Generic.IDictionary%602> ne sont pas identifiées par les processeurs XAML des Services XAML .NET Framework comme étant équivalent à non générique <xref:System.Collections.IList> ou <xref:System.Collections.IDictionary>. Au lieu de l’implémentation des interfaces, une approche recommandée pour les types de propriété de collection générique est dériver les classes <xref:System.Collections.Generic.List%601> ou <xref:System.Collections.Generic.Dictionary%602>. Ces classes implémentent les interfaces non génériques et donc incluent la prise en charge attendue pour les collections XAML dans l’implémentation de base.  
  
## <a name="read-only-collections-and-initialization-logic"></a>Collections en lecture seule et la logique d’initialisation  
 Dans la programmation .NET Framework, il est courant de conception pour effectuer n’importe quelle propriété qui conserve une valeur d’une collection sous la forme d’une collection en lecture seule. Ce modèle permet à l’instance qui possède la propriété de collection afin de mieux contrôler ce qui se passe à la collection... Plus précisément, le modèle empêche le remplacement accidentel de l’ensemble existant en définissant la propriété. Dans ce modèle, l’accès à la collection par les appelants doivent plutôt être effectuées en appelant des méthodes ou propriétés prises en charge par le type de collection et/ou les interfaces de collection pertinentes telles que <xref:System.Collections.IList>.  
  
 À l’aide de ce modèle implique que n’importe quelle classe qui expose une propriété de collection en lecture seule doit d’abord initialiser cette propriété pour stocker une collection vide. En règle générale, l’initialisation est exécutée en tant que partie du comportement de construction de la classe. Pour être utile pour XAML, il est important que cette logique est toujours référencée par le constructeur par défaut, car XAML appelle généralement le constructeur par défaut avant le traitement des propriétés (propriétés de la collection ou autre).  
  
## <a name="xaml-type-system-support-and-collections"></a>Collections et la prise en charge de système de Type XAML  
 Au-delà des mécanismes de base de l’analyse XAML et de remplissage ou de sérialisation des propriétés de la collection, le système de type XAML tel qu’implémenté dans les Services XAML .NET Framework inclut plusieurs fonctionnalités de conception qui se rapportent à des collections dans XAML.  
  
1.  <xref:System.Xaml.XamlType.IsCollection%2A>Retourne la valeur true si le type XAML est sauvegardé par un type qui fournit la prise en charge de la collection XAML.  
  
2.  <xref:System.Xaml.XamlType.IsDictionary%2A>et <xref:System.Xaml.XamlType.IsArray%2A> peut identifier plus précisément quel mode de collecte prend en charge de type XAML. Pour XAML personnalisé processeurs qui sont basées sur les Services XAML .NET Framework et le code XAML système de type, mais pas basé sur <xref:System.Xaml.XamlWriter> implémentations, le fait de savoir quel mode de collecte est utilisé peut être nécessaire afin de déterminer la méthode à appeler pour traitement de la collection.  
  
3.  Chacune des valeurs de propriété précédentes sont potentiellement plus influencées par les substitutions de <xref:System.Xaml.XamlType.LookupCollectionKind%2A> sur un type XAML.
