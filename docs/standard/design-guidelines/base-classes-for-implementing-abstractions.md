---
title: "Classes de base pour l’impl&#233;mentation d’Abstractions | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "abstractions (.NET Framework)"
  - "classes de base, abstractions"
ms.assetid: 37a2d9a4-9721-482a-a40f-eee2c1d97875
caps.latest.revision: 9
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 9
---
# Classes de base pour l’impl&#233;mentation d’Abstractions
Strictement parlant, une classe est une classe de base lorsqu’une autre classe est dérivée. Toutefois, dans cette section, une classe de base est une classe conçue principalement pour fournir une abstraction commune ou pour d’autres classes de réutiliser une partie mise en œuvre via l’héritage par défaut. Classes de base se situent généralement au milieu des hiérarchies d’héritage entre une abstraction à la racine d’une hiérarchie et plusieurs implémentations personnalisées en bas.  
  
 Ils servent d’aides à la mise en œuvre pour implémenter des abstractions. Par exemple, une des abstractions de l’infrastructure pour des collections ordonnées d’éléments est le <xref:System.Collections.Generic.IList%601> interface. L’implémentation de <xref:System.Collections.Generic.IList%601> n’est pas simple, et par conséquent, le Framework fournit plusieurs classes de base, telles que <xref:System.Collections.ObjectModel.Collection%601> et <xref:System.Collections.ObjectModel.KeyedCollection%602>, faisant office de programmes d’assistance pour l’implémentation des regroupements personnalisés.  
  
 Classes de base ne sont généralement pas adaptées pour servir les abstractions par eux\-mêmes, car ils ont tendance à contiennent trop d’implémentation. Par exemple, la `Collection<T>` classe de base contient un grand nombre d’implémentation lié au fait qu’il implémente non générique `IList` interface \(pour mieux s’intégrer avec les collections non génériques\) et le fait qu’il est une collection d’éléments stockés dans la mémoire dans un de ses champs.  
  
 Comme indiqué précédemment, les classes de base peuvent fournir une aide précieuse pour les utilisateurs qui ont besoin pour implémenter des abstractions, mais en même temps, ils peuvent être une responsabilité importante. Ils ajouter la surface d’exposition et augmenter la profondeur des hiérarchies d’héritage et donc conceptuellement compliquent l’infrastructure. Par conséquent, les classes de base doivent être utilisées uniquement si elles fournissent une valeur ajoutée significative pour les utilisateurs de l’infrastructure. Ils doivent être évités si leur valeur uniquement pour les implémenteurs de l’infrastructure, dans lequel cas délégation vers une implémentation interne au lieu de l’héritage à partir d’une classe de base fortement convient.  
  
 **✓ envisagez** les classes de base en abstraite même si elles ne contiennent pas les membres abstraits. Clairement aux utilisateurs que la classe est conçue uniquement pour être héritée.  
  
 **✓ envisagez** placer les classes de base dans un espace de noms distinct à partir des types généraux de scénario. Par définition, les classes de base sont destinées aux scénarios d’extensibilité avancés et ne sont donc pas intéressants pour la majorité des utilisateurs.  
  
 **X éviter** d’affectation de noms des classes de base avec un suffixe « Base » si la classe est destinée à être utilisée dans les API publiques.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Tous droits réservés.*  
  
 *Réimprimé avec l’autorisation de Pearson éducation, Inc. à partir de [Framework Design Guidelines : Conventions, langages et des modèles pour les bibliothèques .NET réutilisable, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison\-Wesley Professional dans le cadre de la série de développement de Microsoft Windows.*  
  
## Voir aussi  
 [Instructions de conception d’infrastructure](../../../docs/standard/design-guidelines/index.md)   
 [Conception pour l’extensibilité](../../../docs/standard/design-guidelines/designing-for-extensibility.md)