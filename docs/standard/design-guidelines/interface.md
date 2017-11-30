---
title: Conception d'interfaces
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- interfaces [.NET Framework], design guidelines
- type design guidelines, interfaces
- class library design guidelines [.NET Framework], interfaces
ms.assetid: a016bd18-6710-4358-9438-9f190a295392
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d04011622321638e1f3b0c5f4d270f840c7070e1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="interface-design"></a>Conception d'interfaces
Bien que la plupart des API sont mieux modélisées au moyen des classes et structs, il existe des cas dans lesquels les interfaces sont plus appropriées ou sont la seule option.  
  
 Le CLR ne prend pas en charge l’héritage multiple (par exemple, les classes CLR ne peut pas hériter de plusieurs classes de base), mais il n’autorise pas les types d’implémenter une ou plusieurs interfaces en plus de l’héritage d’une classe de base. Par conséquent, les interfaces sont souvent utilisées pour obtenir l’effet de l’héritage multiple. Par exemple, <xref:System.IDisposable> est une interface qui permet aux types de prise en charge disposability indépendant de toute autre hiérarchie d’héritage dans lequel ils souhaitent participer.  
  
 L’autre situation qui vous définissez une interface est appropriée est pour la création d’une interface commune qui peut être pris en charge par plusieurs types, y compris certains types de valeur. Types valeur ne peut pas hériter des types autres que <xref:System.ValueType>, mais elles peuvent implémenter des interfaces, donc à l’aide d’une interface est la seule option afin de fournir un type de base commun.  
  
 **✓ FAIRE** définir une interface si vous avez besoin de certaines API courantes pour être pris en charge par un ensemble de types qui inclut les types de valeur.  
  
 **✓ Envisagez** définissant une interface si vous avez besoin prendre en charge ses fonctionnalités sur les types qui héritent déjà d’un autre type.  
  
 **X Évitez** à l’aide des interfaces de marqueur (interfaces sans membres).  
  
 Si vous avez besoin marquer une classe comme ayant une caractéristique spécifique (marqueur), utilisez en général, un attribut personnalisé plutôt qu’une interface.  
  
 **✓ FAIRE** fournir au moins un type qui est une implémentation d’une interface.  
  
 Effectuant cette vous aide à la validation de la conception de l’interface. Par exemple, <xref:System.Collections.Generic.List%601> est une implémentation de la <xref:System.Collections.Generic.IList%601> interface.  
  
 **✓ FAIRE** fournissent au moins une API qui consomme chaque interface que vous définissez (une méthode qui prend l’interface comme paramètre ou une propriété de type interface).  
  
 Effectuant cette vous aide à valider la conception de l’interface. Par exemple, <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> consomme la <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> interface.  
  
 **X ne sont pas** ajouter des membres à une interface qui existait précédemment.  
  
 Cela compromettrait les implémentations de l’interface. Vous devez créer une nouvelle interface afin d’éviter les problèmes de versioning.  
  
 Sauf pour les cas décrits dans ces instructions, vous devez, en général, choisir les classes plutôt que des interfaces lors de la conception de bibliothèques réutilisables de code managé.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Tous droits réservés.*  
  
 *Réimprimées avec l’autorisation de Pearson éducation, Inc. à partir de [règles de conception d’infrastructure : Conventions, idiomes et des modèles pour les bibliothèques .NET réutilisable, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série de développement Microsoft Windows.*  
  
## <a name="see-also"></a>Voir aussi  
 [Règles de conception de type](../../../docs/standard/design-guidelines/type.md)  
 [Règles de conception de .NET Framework](../../../docs/standard/design-guidelines/index.md)
