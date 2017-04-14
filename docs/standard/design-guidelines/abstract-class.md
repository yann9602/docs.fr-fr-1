---
title: "Conception de classes abstraites | Microsoft Docs"
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
  - "Tapez les instructions de conception, classes abstraites"
  - "classes abstraites, règles de conception"
  - "indications de conception de bibliothèques de classes (.NET Framework), classes"
  - "classes (.NET Framework), abstract"
  - "classes (.NET Framework), les règles de conception"
  - "conception de type, classes"
ms.assetid: d3646e6d-5c1f-4922-8fb0-ec5effb30d60
caps.latest.revision: 13
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 13
---
# Conception de classes abstraites
**X ne pas** définir de constructeurs internes publics ou protégés dans les types abstraits.  
  
 Les constructeurs doivent être publiques uniquement si les utilisateurs doivent créer des instances du type. Étant donné que vous ne peut pas créer d’instances d’un type abstrait, un type abstrait doté d’un constructeur public est correctement conçu et trompeur pour les utilisateurs.  
  
 **✓ faire** définir un document protégé ou un constructeur interne dans les classes abstraites.  
  
 Un constructeur protégé est plus courant et il permet simplement de la classe de base pour son propre initialisation lorsque des sous\-types sont créés.  
  
 Un constructeur interne peut être utilisé pour limiter les implémentations concrètes de la classe abstraite à l’assembly de définition de la classe.  
  
 **✓ faire** fournir au moins un type concret qui hérite de chaque classe abstraite que vous avez effectuées.  
  
 Faire Ceci contribue à valider la conception de la classe abstraite. Par exemple,  <xref:System.IO.FileStream?displayProperty=fullName> est une implémentation de la <xref:System.IO.Stream?displayProperty=fullName> classe abstraite.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Tous droits réservés.*  
  
 *Réimprimé avec l’autorisation de Pearson éducation, Inc. à partir de [Framework Design Guidelines : Conventions, langages et des modèles pour les bibliothèques .NET réutilisable, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison\-Wesley Professional dans le cadre de la série de développement de Microsoft Windows.*  
  
## Voir aussi  
 [Conception de type](../../../docs/standard/design-guidelines/type.md)   
 [Instructions de conception d’infrastructure](../../../docs/standard/design-guidelines/index.md)