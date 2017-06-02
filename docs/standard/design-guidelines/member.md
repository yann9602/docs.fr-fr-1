---
title: "R&#232;gles de conception de membres | Microsoft Docs"
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
  - "instructions de conception de membres (.NET Framework), à propos des règles de conception de membres"
  - "membres (.NET Framework), les règles de conception"
  - "indications de conception de bibliothèques de classes (.NET Framework), membres"
  - "règles de conception de membres (.NET Framework)"
ms.assetid: 0ce93180-1d7b-4f8c-9306-f828b2d66b8f
caps.latest.revision: 14
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 14
---
# R&#232;gles de conception de membres
Méthodes, propriétés, événements, constructeurs et les champs sont collectivement en tant que membres. Les membres sont finalement le moyen par lequel les fonctionnalités de framework sont exposées aux utilisateurs finaux d’une infrastructure.  
  
 Les membres peuvent être virtuel ou non virtuel, concret ou abstrait, statique ou instance et peuvent avoir plusieurs portées différentes d’accessibilité. Cette variété de tous les incroyable expressivité mais en même temps nécessite soins part du Concepteur de framework.  
  
 Ce chapitre propose des conseils de base à suivre lorsque vous concevez des membres de n’importe quel type.  
  
## Dans cette section  
 [Surcharge de membre](../../../docs/standard/design-guidelines/member-overloading.md)  
 [Conception des propriétés](../../../docs/standard/design-guidelines/property.md)  
 [Conception de constructeurs](../../../docs/standard/design-guidelines/constructor.md)  
 [Conception d’événements](../../../docs/standard/design-guidelines/event.md)  
 [Conception de champs](../../../docs/standard/design-guidelines/field.md)  
 [méthodes d’extension.](../../../docs/standard/design-guidelines/extension-methods.md)  
 [Surcharges d’opérateur](../../../docs/standard/design-guidelines/operator-overloads.md)  
 [Conception de paramètres](../../../docs/standard/design-guidelines/parameter-design.md)  
 *Portions © 2005, 2009 Microsoft Corporation. Tous droits réservés.*  
  
 *Réimprimé avec l’autorisation de Pearson éducation, Inc. à partir de [Framework Design Guidelines : Conventions, langages et des modèles pour les bibliothèques .NET réutilisable, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison\-Wesley Professional dans le cadre de la série de développement de Microsoft Windows.*  
  
## Voir aussi  
 [Instructions de conception d’infrastructure](../../../docs/standard/design-guidelines/index.md)