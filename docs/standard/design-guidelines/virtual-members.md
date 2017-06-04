---
title: "Membres virtuels | Microsoft Docs"
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
  - "membres substituables"
  - "membres virtuels"
  - "membres (.NET Framework), virtuels"
ms.assetid: 8ff4eb97-0364-43ec-8a02-934b5cd94d19
caps.latest.revision: 9
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 9
---
# Membres virtuels
Les membres virtuels peuvent être remplacées, ce qui modifie le comportement de la sous\-classe. Ils sont très similaires aux rappels en termes d’extensibilité qu’ils fournissent, mais qu’ils sont mieux en termes de performances de l’exécution et la consommation de mémoire. En outre, les membres virtuels se sentent plus naturelles dans les scénarios qui requièrent la création d’une relation type d’un type existant \(spécialisation\).  
  
 Les membres virtuels plus performant que les rappels et les événements, mais n’effectuent pas de meilleures performances que les méthodes non virtuelles.  
  
 Le principal inconvénient des membres virtuels est que le comportement d’un membre virtuel peut uniquement être modifié au moment de la compilation. Le comportement d’un rappel peut être modifié lors de l’exécution.  
  
 Les membres virtuels, telles que les rappels \(et peut\-être plus que les rappels\), sont coûteuses à concevoir, tester et mettre à jour, car un appel à un membre virtuel peut être substitué de manière imprévisible et peut exécuter du code arbitraire. En outre, beaucoup plus d’effort est généralement requis pour définir clairement le contrat des membres virtuels, ce qui augmente le coût de conception et de les documenter.  
  
 **X ne pas** afficher les membres virtuels sauf si vous avez une bonne raison à cela et que vous êtes conscient de tous les coûts liés à la conception, de test et de maintenance des membres virtuels.  
  
 Les membres virtuels sont moins flexibles en termes de modifications qui peuvent être effectuées pour les sans perdre la compatibilité. En outre, ils sont plus lentes que les membres non virtuelle, principalement parce que les appels aux membres virtuels ne sont pas inline.  
  
 **✓ envisagez** limiter l’extensibilité à celles qui sont absolument nécessaires.  
  
 **✓ faire** préférer accessibilité protégée d’une accessibilité publique pour les membres virtuels. Les membres publics doivent fournir l’extensibilité \(si nécessaire\) en appelant un membre virtuel protégé.  
  
 Les membres publics d’une classe doivent fournir le jeu de fonctionnalités pour les consommateurs directs de cette classe. Les membres virtuels sont conçus pour être substitué dans les sous\-classes et accessibilité protégée est un excellent moyen pour définir l’étendue tous les points d’extensibilité virtuel où elles peuvent être utilisées.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Tous droits réservés.*  
  
 *Réimprimé avec l’autorisation de Pearson éducation, Inc. à partir de [Framework Design Guidelines : Conventions, langages et des modèles pour les bibliothèques .NET réutilisable, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison\-Wesley Professional dans le cadre de la série de développement de Microsoft Windows.*  
  
## Voir aussi  
 [Instructions de conception d’infrastructure](../../../docs/standard/design-guidelines/index.md)   
 [Conception pour l’extensibilité](../../../docs/standard/design-guidelines/designing-for-extensibility.md)