---
title: "Abstractions (Types et Interfaces abstraits) | Microsoft Docs"
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
  - "interfaces (.NET Framework), abstract"
  - "interfaces abstraites (.NET Framework)"
  - "types abstraits (.NET Framework)"
  - "types (.NET Framework), abstract"
ms.assetid: 0a632bc7-9b03-44ee-8842-c82f88672a45
caps.latest.revision: 10
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 10
---
# Abstractions (Types et Interfaces abstraits)
Une abstraction est un type qui décrit un contrat, mais ne fournit pas une implémentation complète du contrat. Abstractions sont généralement implémentées comme des classes abstraites ou des interfaces, et ils sont livrés avec un ensemble bien défini de documentation de référence qui décrivent la sémantique des types qui implémente le contrat requise. Certaines des abstractions plus importantes dans le .NET Framework incluent <xref:System.IO.Stream>, <xref:System.Collections.Generic.IEnumerable%601>, et <xref:System.Object>.  
  
 Vous pouvez étendre des infrastructures en implémentant un type concret qui prend en charge le contrat d’une abstraction et en utilisant ce type concret avec framework API consommatrice \(fonctionnant sur\) l’abstraction.  
  
 Une abstraction pertinentes et utile qui est capable de supporter l’épreuve du temps est très difficile de concevoir. La principale difficulté consiste à obtenir l’ensemble correct de membres, pas plus et moins non. Si une abstraction comporte trop de membres, il devient difficile, voire même d’implémenter. S’il a trop peu de membres pour la fonctionnalité Promise, il devient inutile dans de nombreux scénarios intéressants.  
  
 Un trop grand nombre d’abstractions dans une infrastructure également affectent la facilité d’utilisation de l’infrastructure. Il est souvent très difficile de comprendre une abstraction sans avoir à comprendre comment il s’adapte à l’image supérieure des implémentations concrètes et les API d’exploitation sur l’abstraction. En outre, les noms des abstractions et leurs membres sont nécessairement abstraites, qui les rend difficiles à déchiffrer et difficiles à réaliser sans avoir cerné le contexte plus large de leur utilisation.  
  
 Toutefois, les abstractions offrent une extensibilité extrêmement puissante répondant aux autres mécanismes d’extensibilité ne peut pas souvent. Ils sont au cœur de nombreux modèles architecturaux, tels que les plug\-ins, inversion de contrôle \(IoC\), pipelines et ainsi de suite. Ils sont également extrêmement importants pour la testabilité des infrastructures. Abstractions bon permettent d’indiquer d’éliminer les dépendances importantes pour les besoins de test unitaire. En résumé, les abstractions sont responsables de la richesse des infrastructures orienté objet modernes demandée.  
  
 **X ne pas** fournissent des abstractions que si elles sont testées par le développement de plusieurs implémentations concrètes et API consommant les abstractions.  
  
 **✓ faire** avec soin de choisir entre une classe abstraite et une interface lors de la conception d’une abstraction.  
  
 **✓ envisagez** fournissant des tests de référence pour les implémentations concrètes d’abstractions. Ces tests doivent permettre aux utilisateurs de vérifier si leurs implémentations implémentent correctement le contrat.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Tous droits réservés.*  
  
 *Réimprimé avec l’autorisation de Pearson éducation, Inc. à partir de [Framework Design Guidelines : Conventions, langages et des modèles pour les bibliothèques .NET réutilisable, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison\-Wesley Professional dans le cadre de la série de développement de Microsoft Windows.*  
  
## Voir aussi  
 [Instructions de conception d’infrastructure](../../../docs/standard/design-guidelines/index.md)   
 [Conception pour l’extensibilité](../../../docs/standard/design-guidelines/designing-for-extensibility.md)