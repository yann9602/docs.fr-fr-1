---
title: "Conception en vue de l'extensibilité"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- extending class libraries
- extensibility with class libraries in .NET Framework
- class library design guidelines [.NET Framework], extensibility
- class library extensibility [.NET Framework]
ms.assetid: 1cdb8740-871a-456c-9bd9-db96ca8d79b3
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: dbee2fb24b9acf9bc2512b399e3a74e66720cc3c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="designing-for-extensibility"></a>Conception en vue de l'extensibilité
Un aspect important de la conception d’une infrastructure consiste à s’assurer de que l’extensibilité de l’infrastructure a été examinée avec soin. Cela nécessite que vous comprenez les coûts et les avantages associés à différents mécanismes d’extensibilité. Ce chapitre vous aide à décider des mécanismes d’extensibilité : sous-classement, les événements, les membres virtuels, les rappels et ainsi de suite, peuvent mieux les exigences de votre infrastructure.  
  
 Il existe de nombreuses façons pour permettre d’extensibilité dans les infrastructures. Elles vont de moins puissants mais moins coûteux à très puissante, mais il est coûteux. Pour tous les besoins d’extensibilité donné, vous devez choisir le mécanisme d’extensibilité moins coûteux qui répond aux exigences. Gardez à l’esprit qu’il est généralement possible d’ajouter plus d’extensibilité ultérieurement, mais prennent immédiatement sans introduire de modifications avec rupture jamais.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Classes unsealed](../../../docs/standard/design-guidelines/unsealed-classes.md)  
 [Membres protégés](../../../docs/standard/design-guidelines/protected-members.md)  
 [Événements et rappels](../../../docs/standard/design-guidelines/events-and-callbacks.md)  
 [Membres virtuels](../../../docs/standard/design-guidelines/virtual-members.md)  
 [Abstractions (Types abstraits et Interfaces)](../../../docs/standard/design-guidelines/abstractions-abstract-types-and-interfaces.md)  
 [Classes de base pour implémenter des Abstractions](../../../docs/standard/design-guidelines/base-classes-for-implementing-abstractions.md)  
 [Le fait de sceller](../../../docs/standard/design-guidelines/sealing.md)  
 *Portions © 2005, 2009 Microsoft Corporation. Tous droits réservés.*  
  
 *Réimprimées avec l’autorisation de Pearson éducation, Inc. à partir de [règles de conception d’infrastructure : Conventions, idiomes et des modèles pour les bibliothèques .NET réutilisable, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série de développement Microsoft Windows.*  
  
## <a name="see-also"></a>Voir aussi  
 [Règles de conception de .NET Framework](../../../docs/standard/design-guidelines/index.md)
