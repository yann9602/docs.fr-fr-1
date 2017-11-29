---
title: Sceller
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- limiting extensibility
- classes [.NET Framework], sealing
- preventing customization
- sealed classes
ms.assetid: cc42267f-bb7a-427a-845e-df97408528d4
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8caa253a3f17c58f542317de579c4f7832c4efac
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="sealing"></a>Sceller
Une des fonctionnalités des infrastructures d’orientée objet est que les développeurs peuvent étendre et personnalisez-les de manières inattendues par les concepteurs de framework. Il s’agit la puissance et le risque de conception extensible. Lorsque vous concevez votre infrastructure, il est donc très important de concevoir soigneusement pour l’extensibilité lorsqu’il est nécessaire et pour limiter l’extensibilité lorsqu’il est dangereux.  
  
 Scellement d’un mécanisme puissant qui empêche d’extensibilité. Vous pouvez sceller à la classe ou des membres individuels. Le fait de sceller une classe d’empêche les utilisateurs d’hériter de la classe. Le fait de sceller un membre d’empêche les utilisateurs de substituer un membre particulier.  
  
 **X ne sont pas** sceller des classes sans avoir une bonne raison de le faire.  
  
 Le fait de sceller une classe, car vous ne savez pas un scénario d’extensibilité n’est pas une bonne raison. Les utilisateurs de Framework tels que d’hériter des classes pour différentes raisons identifiable, telles que l’ajout de membres de commodité. Consultez [Classes Unsealed](../../../docs/standard/design-guidelines/unsealed-classes.md) pour obtenir des exemples de raisons identifiable les utilisateurs souhaitent hériter d’un type.  
  
 Raisons pour sceller une classe sont les suivantes :  
  
-   La classe est une classe statique. Consultez [conception d’une classe statique](../../../docs/standard/design-guidelines/static-class.md).  
  
-   La classe stocke des secrets de sécurité sensibles dans des membres protégés hérités.  
  
-   La classe hérite de nombreux membres virtuels et le coût de leur scellement individuellement serait dépassent les avantages de la classe non scellés.  
  
-   La classe est un attribut qui nécessite la recherche d’exécution très rapide. Les attributs sealed ont des niveaux de performance légèrement plus élevées que celles non scellés. consultez [attributs](../../../docs/standard/design-guidelines/attributes.md).  
  
 **X ne sont pas** déclarer les membres virtuels ou protégés sur les types sealed.  
  
 Par définition, les types sealed ne peut pas être héritées. Cela signifie que les membres protégés sur les types sealed ne peut pas être appelées, et les méthodes virtuelles sur les types sealed ne peut pas être substituées.  
  
 **✓ Envisagez** sceller les membres que vous substituez.  
  
 Des problèmes qui peuvent résulter de présentation des membres virtuels (présentés dans [membres virtuels](../../../docs/standard/design-guidelines/virtual-members.md)) s’appliquent aux substitutions, bien qu’à un degré moindre. Le fait de sceller un remplacement vous protège ces problèmes, en commençant à partir de ce point dans la hiérarchie d’héritage.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Tous droits réservés.*  
  
 *Réimprimées avec l’autorisation de Pearson éducation, Inc. à partir de [règles de conception d’infrastructure : Conventions, idiomes et des modèles pour les bibliothèques .NET réutilisable, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série de développement Microsoft Windows.*  
  
## <a name="see-also"></a>Voir aussi  
 [Règles de conception de .NET Framework](../../../docs/standard/design-guidelines/index.md)  
 [Conception d’extensibilité](../../../docs/standard/design-guidelines/designing-for-extensibility.md)  
 [Classes unsealed](../../../docs/standard/design-guidelines/unsealed-classes.md)
