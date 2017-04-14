---
title: "Classes unsealed | Microsoft Docs"
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
  - "classes (.NET Framework), non scellés"
  - "classes unsealed"
  - "héritage, classes"
ms.assetid: 9a3bd505-90f5-4053-9f0d-3cf5fa3d3ebf
caps.latest.revision: 9
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 9
---
# Classes unsealed
Les classes sealed ne peut pas être héritées, et ils empêchent d’extensibilité. En revanche, les classes qui peuvent être héritées sont appelées des classes unsealed.  
  
 **✓ envisagez** à l’aide des classes unsealed sans aucune ajouté des membres virtuels ou protégés comme un excellent moyen de fournir le bon marché encore très apprécié extensibilité à une infrastructure.  
  
 Les développeurs souhaitent souvent héritent des classes unsealed afin d’ajouter des membres de commodité telles que les constructeurs personnalisés, de nouvelles méthodes ou les surcharges de méthode. Par exemple,  `System.Messaging.MessageQueue` est non scellé permettant ainsi aux utilisateurs de créer des files d’attente personnalisées par défaut à un chemin d’accès de la file d’attente particulière ou pour ajouter des méthodes personnalisées qui simplifient l’API pour des scénarios spécifiques.  
  
 Les classes sont verrouillés par défaut dans les langages de programmation plus, et c’est également la valeur par défaut recommandée pour la plupart des classes dans les infrastructures. L’extensibilité offerte par les types non scellés est bien appréciés par les utilisateurs de l’infrastructure et relativement peu coûteux fournir des coûts de test relativement faible associées aux types non scellés.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Tous droits réservés.*  
  
 *Réimprimé avec l’autorisation de Pearson éducation, Inc. à partir de [Framework Design Guidelines : Conventions, langages et des modèles pour les bibliothèques .NET réutilisable, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison\-Wesley Professional dans le cadre de la série de développement de Microsoft Windows.*  
  
## Voir aussi  
 [Instructions de conception d’infrastructure](../../../docs/standard/design-guidelines/index.md)   
 [Conception pour l’extensibilité](../../../docs/standard/design-guidelines/designing-for-extensibility.md)   
 [Le fait de sceller](../../../docs/standard/design-guidelines/sealing.md)