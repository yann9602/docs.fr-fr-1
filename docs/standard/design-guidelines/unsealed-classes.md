---
title: Classes unsealed
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- classes [.NET Framework], unsealed
- unsealed classes
- inheritance, classes
ms.assetid: 9a3bd505-90f5-4053-9f0d-3cf5fa3d3ebf
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f950d8de2681868fe28e09e4b51bd8156cd12e94
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="unsealed-classes"></a>Classes unsealed
Classes sealed ne peut pas être héritées, et empêchent d’extensibilité. En revanche, les classes qui peuvent être héritées sont appelées classes unsealed.  
  
 **✓ Envisagez** à l’aide des classes unsealed sans aucune ajouté des membres virtuels ou protégés comme un excellent moyen de fournir un peu coûteux encore apprécié extensibilité à une infrastructure.  
  
 Les développeurs souhaitent souvent héritent des classes unsealed afin d’ajouter des membres de commodité telles que les constructeurs personnalisés, les nouvelles méthodes ou les surcharges de méthode. Par exemple, `System.Messaging.MessageQueue` est non scellé, et permet ainsi aux utilisateurs de créer des files d’attente personnalisées cette valeur par défaut pour un chemin d’accès de la file d’attente particulière ou ajouter des méthodes personnalisées qui simplifient l’API pour des scénarios spécifiques.  
  
 Classes sont non scellés par défaut dans les langages de programmation plus, et c’est également la valeur par défaut recommandée pour la plupart des classes dans les infrastructures. L’extensibilité offerte par les types unsealed est bien appréciés par les utilisateurs de l’infrastructure et relativement peu coûteux fournir des coûts relativement faible de test associées aux types unsealed.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Tous droits réservés.*  
  
 *Réimprimées avec l’autorisation de Pearson éducation, Inc. à partir de [règles de conception d’infrastructure : Conventions, idiomes et des modèles pour les bibliothèques .NET réutilisable, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série de développement Microsoft Windows.*  
  
## <a name="see-also"></a>Voir aussi  
 [Règles de conception de .NET Framework](../../../docs/standard/design-guidelines/index.md)  
 [Conception d’extensibilité](../../../docs/standard/design-guidelines/designing-for-extensibility.md)  
 [Le fait de sceller](../../../docs/standard/design-guidelines/sealing.md)
