---
title: "Règles de conception de .NET Framework"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- libraries, .NET Framework class library
- class library design guidelines [.NET Framework], about
- class library design guidelines [.NET Framework]
ms.assetid: 5fbcaf4f-ea2a-4d20-b0d6-e61dee202b4b
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 38c344e4f4ede58fcb39dd638f6aa8e896e63da0
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2017
---
# <a name="framework-design-guidelines"></a>Règles de conception de .NET Framework
Cette section fournit des instructions pour la conception de bibliothèques qui étendent et interagissent avec le .NET Framework. Vise à aider les concepteurs de bibliothèque à garantir la cohérence d’API et la facilité d’utilisation en fournissant un modèle de programmation unifié qui est indépendant du langage de programmation utilisé pour le développement. Nous vous recommandons de suivre ces instructions de conception lors du développement des classes et des composants qui étendent le .NET Framework. Conception de la bibliothèque incohérent la productivité des développeurs néfaste et déconseille d’adoption.  
  
 Les instructions sont organisées comme des recommandations simples ci-après préfixés avec les termes du contrat `Do`, `Consider`, `Avoid`, et `Do not`. Ces recommandations sont destinées à aider les concepteurs de bibliothèque de classes à comprendre les compromis entre différentes solutions. Il peut y avoir enfreindre bon design de bibliothèque que vous ces instructions de conception. Ce cas est rare, et il est important d’avoir une raison justifier votre décision.  
  
 Ces instructions sont extraites à partir du carnet *Framework Design Guidelines : Conventions, idiomes et des modèles pour les bibliothèques .NET réutilisable, 2nd Edition*, Krzysztof Cwalina et Brad Abrams.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Directives de nommage](../../../docs/standard/design-guidelines/naming-guidelines.md)  
 Fournit des instructions pour nommer les assemblys, espaces de noms, types et membres dans les bibliothèques de classes.  
  
 [Instructions pour la conception des types](../../../docs/standard/design-guidelines/type.md)  
 Fournit des instructions pour l’utilisation des classes statiques et abstraites, des interfaces, des énumérations, des structures et des autres types.  
  
 [Instructions de conception des membres](../../../docs/standard/design-guidelines/member.md)  
 Fournit des instructions pour la conception et à l’aide des propriétés, méthodes, constructeurs, champs, événements, opérateurs et paramètres.  
  
 [Conception en vue de l’extensibilité](../../../docs/standard/design-guidelines/designing-for-extensibility.md)  
 Décrit les mécanismes d’extensibilité tels que le sous-classement, à l’aide d’événements, les membres virtuels et les rappels et explique comment choisir les mécanismes qui répondent le mieux aux besoins de votre infrastructure.  
  
 [Instructions de conception pour les exceptions](../../../docs/standard/design-guidelines/exceptions.md)  
 Décrit les règles de conception pour la conception, la levée et l’interception des exceptions.  
  
 [Indications relatives à l’utilisation](../../../docs/standard/design-guidelines/usage-guidelines.md)  
 Fournit des instructions pour à l’aide des types courants tels que des tableaux, des attributs et des collections, prenant en charge la sérialisation et la surcharge des opérateurs d’égalité.  
  
 [Modèles de design courants](../../../docs/standard/design-guidelines/common-design-patterns.md)  
 Fournit des instructions pour le choix et l’implémentation des propriétés de dépendance et le modèle de suppression.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Tous droits réservés.*  
  
 *Réimprimées avec l’autorisation de Pearson éducation, Inc. à partir de [règles de conception d’infrastructure : Conventions, idiomes et des modèles pour les bibliothèques .NET réutilisable, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série de développement Microsoft Windows.*  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble](../../../docs/framework/get-started/overview.md)  
 [Feuille de route pour le .NET Framework](http://msdn.microsoft.com/en-us/0b46b7c6-9163-4f99-8e58-0d1ee7da8c67)  
 [Guide de développement](../../../docs/framework/development-guide.md)
