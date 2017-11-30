---
title: Abstractions (Types et interfaces abstraits)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- interfaces [.NET Framework], abstract
- abstract interfaces [.NET Framework]
- abstract types [.NET Framework]
- types [.NET Framework], abstract
ms.assetid: 0a632bc7-9b03-44ee-8842-c82f88672a45
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d601ab89b08dd9e9bd0b27d2cfb1c495c33a2786
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="abstractions-abstract-types-and-interfaces"></a>Abstractions (Types et interfaces abstraits)
Une abstraction est un type qui décrit un contrat, mais ne fournit pas une implémentation complète du contrat. Abstractions sont généralement implémentées en tant que classes abstraites ou interfaces, et ils sont livrés avec un ensemble bien défini de la documentation de référence décrivant les sémantiques requises des types qui implémente le contrat. Voici quelques-uns des abstractions plus importantes dans le .NET Framework <xref:System.IO.Stream>, <xref:System.Collections.Generic.IEnumerable%601>, et <xref:System.Object>.  
  
 Vous pouvez étendre des infrastructures en implémentant un type concret qui prend en charge le contrat d’une abstraction et de l’utilisation de ce type concret avec framework API consommation (exploitation de) l’abstraction.  
  
 Une abstraction pertinentes et utile qui est capable de supporter le test de temps est très difficile de concevoir. La principale difficulté consiste à obtenir l’ensemble approprié de membres, pas plus et moins non. Si une abstraction comporte trop de membres, il devient difficile, voire même d’implémenter. S’il a trop peu de membres pour la fonctionnalité Promise, elle devient inutile dans de nombreux scénarios intéressants.  
  
 Les abstractions trop nombreux dans une infrastructure affectent également négatif facilité d’utilisation de l’infrastructure. Il est souvent très difficile à comprendre une abstraction sans avoir à comprendre comment elle s’adapte à l’image supérieure des implémentations concrètes et les API d’exploitation sur l’abstraction. En outre, les noms des abstractions et leurs membres sont nécessairement abstraites, qui les rend difficiles à déchiffrer et difficiles à réaliser sans premier comprendre le contexte plus large de leur utilisation.  
  
 Toutefois, les abstractions fournissent extrêmement puissante d’extensibilité que les autres mécanismes d’extensibilité ne peuvent pas correspondre souvent. Elles sont au cœur de nombreux modèles d’architecture, tels que les plug-ins, inversion de contrôle (IoC), pipelines et ainsi de suite. Ils sont également extrêmement importants pour la testabilité des infrastructures. Abstractions bon rendent possible d’extraire des dépendances importantes à des fins de test unitaire. En résumé, les abstractions sont responsables de la richesse précieuses des infrastructures et orienté objet modernes.  
  
 **X ne sont pas** fournissent des abstractions, sauf si elles sont testées par le développement de plusieurs implémentations concrètes et consomme les abstractions des API.  
  
 **✓ FAIRE** choisir entre une classe abstraite et une interface avec soin lors de la conception d’une abstraction.  
  
 **✓ Envisagez** fournissant des tests de référence pour les implémentations concrètes d’abstractions. Ces tests doivent permettre aux utilisateurs de vérifier si leurs implémentations implémentent correctement le contrat.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Tous droits réservés.*  
  
 *Réimprimées avec l’autorisation de Pearson éducation, Inc. à partir de [règles de conception d’infrastructure : Conventions, idiomes et des modèles pour les bibliothèques .NET réutilisable, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série de développement Microsoft Windows.*  
  
## <a name="see-also"></a>Voir aussi  
 [Règles de conception de .NET Framework](../../../docs/standard/design-guidelines/index.md)  
 [Conception d’extensibilité](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
