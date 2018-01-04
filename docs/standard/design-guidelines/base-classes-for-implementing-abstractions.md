---
title: "Classes de base pour l'implémentation d'abstractions"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- abstractions [.NET Framework]
- base classes, abstractions
ms.assetid: 37a2d9a4-9721-482a-a40f-eee2c1d97875
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 96264456ac6afc569c46caf5faed6c37ea22bc8e
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2017
---
# <a name="base-classes-for-implementing-abstractions"></a>Classes de base pour l'implémentation d'abstractions
En principe, une classe devient une classe de base lorsqu’une autre classe est dérivée à partir de celui-ci. Pour les besoins de cette section, toutefois, une classe de base est une classe principalement conçue pour fournir une abstraction commune ou pour d’autres classes de réutiliser une partie mise en œuvre via l’héritage par défaut. Classes de base se situent généralement au milieu des hiérarchies d’héritage entre une abstraction à la racine d’une hiérarchie et plusieurs implémentations personnalisées en bas.  
  
 Ces dernières servent de programmes d’assistance de mise en œuvre pour implémenter des abstractions. Par exemple, une des abstractions de l’infrastructure pour les collections ordonnées d’éléments est la <xref:System.Collections.Generic.IList%601> interface. Mise en œuvre <xref:System.Collections.Generic.IList%601> n’est pas simple, et par conséquent, le Framework fournit plusieurs classes de base, telles que <xref:System.Collections.ObjectModel.Collection%601> et <xref:System.Collections.ObjectModel.KeyedCollection%602>, qui sert de programmes d’assistance pour l’implémentation des regroupements personnalisés.  
  
 Classes de base ne sont généralement pas adaptées pour servir des abstractions par eux-mêmes, car ils ont tendance à contenir trop de mise en œuvre. Par exemple, le `Collection<T>` classe de base contient un grand nombre d’implémentation lié au fait qu’il implémente non générique `IList` interface (pour mieux intégrer avec les collections non génériques) et au fait qu’il est une collection d’éléments stockés dans mémoire dans un de ses champs.  
  
 Comme nous l’avons vu précédemment, classes de base peuvent fournir une aide précieuse pour les utilisateurs qui ont besoin d’implémenter des abstractions, mais en même temps, ils peuvent être une responsabilité importante. Ils ajouter la surface d’exposition et augmentent la profondeur de hiérarchies d’héritage et donc conceptuellement compliquent l’infrastructure. Par conséquent, les classes de base doivent être utilisés uniquement si ils fournissent une valeur ajoutée significative pour les utilisateurs de l’infrastructure. Ils doivent être évités s’ils fournissent la valeur uniquement pour les implémenteurs de l’infrastructure, dans lequel cas délégation vers une implémentation interne au lieu de l’héritage à partir d’une classe de base doit être fortement considérée comme.  
  
 **✓ Envisagez** les classes de base en abstraite même s’ils ne contiennent aucun membre abstrait. Clairement aux utilisateurs de la classe conçue uniquement pour être héritée.  
  
 **✓ Envisagez** en plaçant des classes de base dans un espace de noms distinct à partir des types de scénario principal. Par définition, les classes de base sont destinées aux scénarios d’extensibilité avancés et par conséquent ne sont pas utiles pour la majorité des utilisateurs.  
  
 **X Évitez** d’affectation de noms des classes de base avec un suffixe « Base » si la classe est destinée à être utilisée dans les API publiques.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Tous droits réservés.*  
  
 *Réimprimées avec l’autorisation de Pearson éducation, Inc. à partir de [règles de conception d’infrastructure : Conventions, idiomes et des modèles pour les bibliothèques .NET réutilisable, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série de développement Microsoft Windows.*  
  
## <a name="see-also"></a>Voir aussi  
 [Règles de conception de .NET Framework](../../../docs/standard/design-guidelines/index.md)  
 [Conception en vue de l’extensibilité](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
