---
title: "Instructions de conception d’infrastructure | Microsoft Docs"
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
  - "bibliothèques, bibliothèque de classes .NET Framework"
  - "classe de règles de conception de bibliothèque (.NET Framework), à propos"
  - "indications de conception de bibliothèques de classes (.NET Framework)"
ms.assetid: 5fbcaf4f-ea2a-4d20-b0d6-e61dee202b4b
caps.latest.revision: 14
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 14
---
# Instructions de conception d’infrastructure
Cette section fournit des instructions pour la conception de bibliothèques qui étendent et interagissent avec le .NET Framework. L’objectif est d’aider les concepteurs de bibliothèques à garantir la cohérence d’API et la facilité d’utilisation en fournissant un modèle de programmation unifié qui est indépendant du langage de programmation utilisé pour le développement. Nous vous recommandons de suivre ces instructions de conception lors du développement de classes et composants qui étendent .NET Framework. Design incohérent des bibliothèques négativement la productivité des développeurs et décourage l’adoption.  
  
 Les directives sont organisées comme précédées avec les termes du contrat de recommandations simples `Do`, `Consider`, `Avoid`, et `Do not`. Ces recommandations sont destinées à aider les concepteurs de bibliothèque de classes à comprendre les compromis entre différentes solutions. Il peut exister d’enfreindre bon design de bibliothèque que vous ces instructions de conception. Ce cas est rare, et il est important d’avoir une raison claire et intéressante pour votre décision.  
  
 Ces instructions sont extraites de l’ouvrage *Framework Design Guidelines : Conventions, langages et des modèles pour les bibliothèques .NET réutilisable, 2nd Edition*, Krzysztof Cwalina et Brad Abrams.  
  
## Dans cette section  
 [Indications concernant l'attribution d'un nom](../../../docs/standard/design-guidelines/naming-guidelines.md)  
 Fournit des instructions pour les noms des assemblys, espaces de noms, types et membres dans les bibliothèques de classes.  
  
 [Conception de type](../../../docs/standard/design-guidelines/type.md)  
 Fournit des instructions pour l’utilisation des classes statiques et abstraites, des interfaces, des énumérations, des structures et des autres types.  
  
 [Règles de conception de membres](../../../docs/standard/design-guidelines/member.md)  
 Fournit des instructions pour la conception et à l’aide des propriétés, méthodes, constructeurs, champs, événements, opérateurs et paramètres.  
  
 [Conception pour l’extensibilité](../../../docs/standard/design-guidelines/designing-for-extensibility.md)  
 Décrit les mécanismes d’extensibilité tels que le sous\-classement, à l’aide d’événements, les membres virtuels et les rappels et explique comment choisir les mécanismes qui répondent le mieux aux besoins de votre infrastructure.  
  
 [Instructions de conception pour les Exceptions](../../../docs/standard/design-guidelines/exceptions.md)  
 Fournit des instructions sur la conception, la levée et l’interception des exceptions.  
  
 [Indications relatives à l'utilisation](../../../docs/standard/design-guidelines/usage-guidelines.md)  
 Fournit des instructions sur l’utilisation de types communs tels que des tableaux, des attributs et des collections, prenant en charge la sérialisation et surcharge des opérateurs d’égalité.  
  
 [Modèles de conception courants](../../../docs/standard/design-guidelines/common-design-patterns.md)  
 Fournit des instructions pour le choix et l’implémentation des propriétés de dépendance et le modèle de suppression.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Tous droits réservés.*  
  
 *Réimprimé avec l’autorisation de Pearson éducation, Inc. à partir de [Framework Design Guidelines : Conventions, langages et des modèles pour les bibliothèques .NET réutilisable, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison\-Wesley Professional dans le cadre de la série de développement de Microsoft Windows.*  
  
## Voir aussi  
 [Vue d'ensemble](../../../docs/framework/get-started/overview.md)   
 [Feuille de route pour le .NET Framework](http://msdn.microsoft.com/fr-fr/0b46b7c6-9163-4f99-8e58-0d1ee7da8c67)   
 [Guide de développement](../../../docs/framework/development-guide.md)