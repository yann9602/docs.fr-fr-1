---
title: "Événements et rappels"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- events [.NET Framework], extensibility
- methods [.NET Framework], callback
- callback methods
- callbacks
ms.assetid: 48b55c60-495f-4089-9396-97f9122bba7c
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 39dd4e31e84e455b72ce53bd8abffd650ce77dfc
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2017
---
# <a name="events-and-callbacks"></a>Événements et rappels
Les rappels sont des points d’extensibilité qui autorisent une infrastructure rappeler dans le code de l’utilisateur via un délégué. Ces délégués sont généralement transmis à l’infrastructure via un paramètre d’une méthode.  
  
 Les événements sont un cas spécial de rappels qui prend en charge la syntaxe pratique et cohérente pour fournir le délégué (un gestionnaire d’événements). En outre, saisie semi-automatique des instructions et les concepteurs de Visual Studio fournissent de l’aide à l’aide d’API basées sur des événements. (Consultez [événement conception](../../../docs/standard/design-guidelines/event.md).)  
  
 **✓ Envisagez** à l’aide des rappels pour permettre aux utilisateurs de fournir un code personnalisé doit être exécuté par l’infrastructure.  
  
 **✓ Envisagez** à l’aide d’événements pour permettre aux utilisateurs de personnaliser le comportement d’une infrastructure sans avoir besoin pour comprendre la conception orientée objet.  
  
 **✓ FAIRE** de préférence des événements via des rappels ordinaires, car ils sont plus facile pour un grand nombre de développeurs et sont intégrés à la fin de l’instruction Visual Studio.  
  
 **X Évitez** à l’aide de rappels dans les API sensibles aux performances.  
  
 **✓ FAIRE** utiliser la nouvelle `Func<...>`, `Action<...>`, ou `Expression<...>` types à la place des délégués personnalisés lors de la définition d’API avec des rappels.  
  
 `Func<...>`et `Action<...>` représentent des délégués génériques. `Expression<...>`représente les définitions de fonction qui peuvent être compilées et appelées par la suite lors de l’exécution, mais peut également être sérialisées et passées à des processus à distance.  
  
 **✓ FAIRE** mesurer et comprendre les implications en matière de performances de l’utilisation de `Expression<...>`, au lieu d’utiliser `Func<...>` et `Action<...>` délégués.  
  
 `Expression<...>`les types sont dans la plupart des cas logiquement équivalente à `Func<...>` et `Action<...>` délégués. La principale différence est que les délégués sont destinées à être utilisée dans des scénarios de processus locale. les expressions sont destinées aux cas où il est bénéfique et permet d’évaluer l’expression dans un processus distant ou un ordinateur.  
  
 **✓ FAIRE** comprendre que par l’appel d’un délégué, vous exécutez du code arbitraire et qui pourraient avoir des répercussions de sécurité, d’exactitude et de compatibilité.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Tous droits réservés.*  
  
 *Réimprimées avec l’autorisation de Pearson éducation, Inc. à partir de [règles de conception d’infrastructure : Conventions, idiomes et des modèles pour les bibliothèques .NET réutilisable, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série de développement Microsoft Windows.*  
  
## <a name="see-also"></a>Voir aussi  
 [Conception en vue de l’extensibilité](../../../docs/standard/design-guidelines/designing-for-extensibility.md)  
 [Règles de conception de .NET Framework](../../../docs/standard/design-guidelines/index.md)
