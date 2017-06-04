---
title: "Le fait de sceller | Microsoft Docs"
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
  - "limiter l’extensibilité"
  - "classes (.NET Framework), le fait de sceller"
  - "empêcher la personnalisation"
  - "classes sealed"
ms.assetid: cc42267f-bb7a-427a-845e-df97408528d4
caps.latest.revision: 10
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 10
---
# Le fait de sceller
L’une des fonctionnalités des infrastructures orientée objet est que les développeurs peuvent étendre et personnaliser les de manière inattendue par les concepteurs de framework. C’est la puissance et le risque de conception extensible. Lorsque vous concevez votre infrastructure, il est donc très important de concevoir soigneusement pour l’extensibilité lorsqu’il est nécessaire et pour limiter l’extensibilité lorsqu’il est dangereux.  
  
 Le scellement d’un mécanisme puissant qui empêche d’extensibilité. Vous pouvez sceller la classe ou des membres. Sceller une classe empêche les utilisateurs d’hériter de la classe. Le scellement d’un membre empêche les utilisateurs de remplacer un membre particulier.  
  
 **X ne pas** sceller des classes sans avoir une bonne raison de le faire.  
  
 Sceller une classe, car vous ne pouvez pas considérer un scénario d’extensibilité n’est pas une bonne raison. Les utilisateurs de Framework comme héritent des classes pour diverses raisons identifiable, telles que l’ajout de membres de commodité. Consultez [Classes unsealed](../../../docs/standard/design-guidelines/unsealed-classes.md) pour obtenir des exemples de raisons identifiable, les utilisateurs veulent d’hériter d’un type.  
  
 Bonnes raisons pour sceller une classe sont les suivantes :  
  
-   La classe est une classe statique. Consultez [Conception de classes statiques](../../../docs/standard/design-guidelines/static-class.md).  
  
-   La classe stocke des secrets sensibles à la sécurité dans les membres protégés hérités.  
  
-   La classe hérite de nombreux membres virtuels et le coût de leur scellement individuellement serait dépassent les avantages de la classe non scellés.  
  
-   La classe est un attribut qui nécessite une recherche très rapides à l’exécution. Attributs sealed ont des niveaux de performances légèrement supérieures que celles non scellés. Consultez [Attributs](../../../docs/standard/design-guidelines/attributs.md).  
  
 **X ne pas** déclarer les membres virtuels ou protégés sur les types sealed.  
  
 Par définition, les types sealed ne peut pas être héritées. Cela signifie que les membres protégés sur les types sealed ne peut pas être appelées, et les méthodes virtuelles sur les types sealed ne peut pas être substituées.  
  
 **✓ envisagez** sceller les membres que vous substituez.  
  
 Des problèmes qui peuvent résulter de présentation des membres virtuels \(section [Membres virtuels](../../../docs/standard/design-guidelines/virtual-members.md)\) s’appliquent aux remplacements, bien qu’à un degré légèrement moindre. Le fait de sceller un remplacement vous protège ces problèmes à partir de ce point dans la hiérarchie d’héritage.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Tous droits réservés.*  
  
 *Réimprimé avec l’autorisation de Pearson éducation, Inc. à partir de [Framework Design Guidelines : Conventions, langages et des modèles pour les bibliothèques .NET réutilisable, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison\-Wesley Professional dans le cadre de la série de développement de Microsoft Windows.*  
  
## Voir aussi  
 [Instructions de conception d’infrastructure](../../../docs/standard/design-guidelines/index.md)   
 [Conception pour l’extensibilité](../../../docs/standard/design-guidelines/designing-for-extensibility.md)   
 [Classes unsealed](../../../docs/standard/design-guidelines/unsealed-classes.md)