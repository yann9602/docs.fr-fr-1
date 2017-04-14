---
title: "Interfaces g&#233;n&#233;riques | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "comparaisons d'égalité (.NET Framework)"
  - "interfaces génériques (.NET Framework)"
  - "génériques (.NET Framework), interfaces"
  - "comparaisons de classement (.NET Framework)"
ms.assetid: 88bf5b04-d371-4edb-ba38-01ec7cabaacf
caps.latest.revision: 9
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 9
---
# Interfaces g&#233;n&#233;riques
Cette rubrique donne une vue d'ensemble des interfaces génériques qui fournissent des fonctionnalités communes à plusieurs familles de types génériques.  
  
## Interfaces génériques  
 Les interfaces génériques fournissent des contreparties de type sécurisé aux interfaces non génériques pour les comparaisons de classement et d'égalité, et pour les fonctionnalités partagées par les types de collections génériques.  
  
> [!NOTE]
>  Depuis [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], les paramètres de type de plusieurs interfaces génériques sont marqués comme étant covariants ou contravariants, en fournissant une plus grande flexibilité pour l'affectation et l'utilisation des types qui implémentent ces interfaces.  Voir [Covariance et contravariance](../../../docs/standard/generics/covariance-and-contravariance.md).  
  
### Comparaisons d'égalité et de classement  
 Dans l'espace de noms <xref:System>, les interfaces génériques <xref:System.IComparable%601?displayProperty=fullName> et <xref:System.IEquatable%601?displayProperty=fullName>, comme leurs contreparties non génériques, définissent respectivement des méthodes pour les comparaisons de classement et les comparaisons d'égalité.  Les types implémentent ces interfaces pour offrir la possibilité d'effectuer de telles comparaisons.  
  
 Dans l'espace de noms <xref:System.Collections.Generic>, les interfaces génériques <xref:System.Collections.Generic.IComparer%601> et <xref:System.Collections.Generic.IEqualityComparer%601> offrent un moyen de définir une comparaison de classement ou d'égalité pour les types qui n'implémentent pas les interfaces génériques <xref:System.IComparable%601?displayProperty=fullName> ou <xref:System.IEquatable%601?displayProperty=fullName>, et ils permettent de redéfinir ces relations pour les types qui les implémentent.  Ces interfaces sont utilisées par les méthodes et les constructeurs de nombreuses classes de collection génériques.  Par exemple, vous pouvez passer un objet <xref:System.Collections.Generic.IComparer%601> générique au constructeur de la classe <xref:System.Collections.Generic.SortedDictionary%602> pour spécifier un ordre de tri pour un type qui n'implémente pas l'interface générique <xref:System.IComparable%601?displayProperty=fullName>.  Il existe des surcharges de la méthode statique générique <xref:System.Array.Sort%2A?displayProperty=fullName> et de la méthode d'instance <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=fullName> pour le tri des tableaux et des listes à l'aide  d'implémentations génériques de <xref:System.Collections.Generic.IComparer%601>.  
  
 Les classes génériques <xref:System.Collections.Generic.Comparer%601> et <xref:System.Collections.Generic.EqualityComparer%601> fournissent des classes de base pour les implémentations des interfaces génériques <xref:System.Collections.Generic.IComparer%601> et <xref:System.Collections.Generic.IEqualityComparer%601>, et fournissent également des comparaisons de classement et d'égalité par défaut via leurs propriétés respectives <xref:System.Collections.Generic.Comparer%601.Default%2A?displayProperty=fullName> et <xref:System.Collections.Generic.EqualityComparer%601.Default%2A?displayProperty=fullName>.  
  
### Fonctionnalités des collections  
 L'interface générique <xref:System.Collections.Generic.ICollection%601> est l'interface de base pour les types de collections génériques.  Elle offre des fonctionnalités de base pour l'ajout, la suppression, la copie et l'énumération d'éléments.  <xref:System.Collections.Generic.ICollection%601> hérite à la fois de l'interface générique <xref:System.Collections.Generic.IEnumerable%601> et de l'interface non générique <xref:System.Collections.IEnumerable>.  
  
 L'interface générique <xref:System.Collections.Generic.IList%601> étend l'interface générique <xref:System.Collections.Generic.ICollection%601> avec des méthodes pour la récupération indexée.  
  
 L'interface générique <xref:System.Collections.Generic.IDictionary%602> étend l'interface générique <xref:System.Collections.Generic.ICollection%601> avec des méthodes pour la récupération indexée.  Les types de dictionnaires génériques de la bibliothèque de classes de base du .NET Framework implémentent également l'interface <xref:System.Collections.IDictionary> non générique.  
  
 L'interface générique <xref:System.Collections.Generic.IEnumerable%601> fournit une structure d'énumérateur générique.  L'interface générique <xref:System.Collections.Generic.IEnumerator%601> implémentée par les énumérateurs génériques hérite de l'interface non générique <xref:System.Collections.IEnumerator> ; les membres <xref:System.Collections.IEnumerator.MoveNext%2A> et <xref:System.Collections.IEnumerator.Reset%2A>, qui ne dépendent pas du paramètre de type `T`, apparaissent seulement sur l'interface non générique.  Cela signifie que tout consommateur de l'interface non générique peut également consommer l'interface générique.  
  
## Voir aussi  
 <xref:System.Collections.Generic?displayProperty=fullName>   
 <xref:System.Collections.ObjectModel?displayProperty=fullName>   
 [Génériques](../../../docs/standard/generics/index.md)   
 [Collections génériques dans le .NET Framework](../../../docs/standard/generics/collections.md)   
 [Délégués génériques pour la manipulation de tableaux et de listes](../../../docs/standard/generics/delegates-for-manipulating-arrays-and-lists.md)   
 [Covariance et contravariance](../../../docs/standard/generics/covariance-and-contravariance.md)