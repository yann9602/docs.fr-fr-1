---
title: "&#201;v&#233;nements et rappels | Microsoft Docs"
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
  - "événements (.NET Framework), d’extensibilité"
  - "méthodes (.NET Framework), le rappel"
  - "méthodes de rappel"
  - "rappels"
ms.assetid: 48b55c60-495f-4089-9396-97f9122bba7c
caps.latest.revision: 10
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 10
---
# &#201;v&#233;nements et rappels
Les rappels sont des points d’extensibilité qui permettent une infrastructure effectuer un rappel dans le code de l’utilisateur via un délégué. Ces délégués sont généralement transmis à l’infrastructure via un paramètre d’une méthode.  
  
 Les événements sont un cas spécial de rappels qui prend en charge la syntaxe pratique et cohérente pour alimenter le délégué \(Gestionnaire d’événements\). En outre, la saisie semi\-automatique des instructions et des concepteurs de Visual Studio fournissent aide sur les API basées sur des événements. \(Consultez [Conception d’événements](../../../docs/standard/design-guidelines/event.md).\)  
  
 **✓ envisagez** utilisant des rappels pour permettre aux utilisateurs de fournir un code personnalisé doit être exécuté par l’infrastructure.  
  
 **✓ envisagez** à l’aide des événements pour permettre aux utilisateurs de personnaliser le comportement d’une infrastructure sans la nécessité de comprendre la conception orientée objet.  
  
 **✓ faire** de préférence des événements via des rappels ordinaires, car ils sont plus familiers à un grand nombre de développeurs et sont intégrés à la saisie semi\-automatique des instructions Visual Studio.  
  
 **X éviter** à l’aide de rappels dans les API sensibles aux performances.  
  
 **✓ faire** utilise la nouvelle `Func<...>`, `Action<...>`, ou `Expression<...>` types au lieu des délégués personnalisés lors de la définition d’API avec des rappels.  
  
 `Func<...>` et `Action<...>` représentent les délégués génériques.`Expression<...>` représente les définitions de fonction qui peuvent être compilées et appelées par la suite à l’exécution, mais peut également être sérialisées et transmies à un processus distants.  
  
 **✓ faire** mesurer et comprendre les implications en matière de performances de `Expression<...>`, au lieu d’utiliser `Func<...>` et `Action<...>` délégués.  
  
 `Expression<...>` les types sont dans la plupart des cas logiquement équivalent à `Func<...>` et `Action<...>` délégués. La principale différence est que les délégués sont destinés à être utilisé dans des scénarios de traitement locale. les expressions sont destinées aux cas où il est possible d’évaluer l’expression dans un ordinateur ou un processus distant et profitable.  
  
 **✓ faire** comprendre qu’en appelant un délégué, vous exécutez du code arbitraire et qui peuvent avoir des répercussions de sécurité, d’exactitude et de compatibilité.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Tous droits réservés.*  
  
 *Réimprimé avec l’autorisation de Pearson éducation, Inc. à partir de [Framework Design Guidelines : Conventions, langages et des modèles pour les bibliothèques .NET réutilisable, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison\-Wesley Professional dans le cadre de la série de développement de Microsoft Windows.*  
  
## Voir aussi  
 [Conception pour l’extensibilité](../../../docs/standard/design-guidelines/designing-for-extensibility.md)   
 [Instructions de conception d’infrastructure](../../../docs/standard/design-guidelines/index.md)