---
title: "Conception pour l’extensibilit&#233; | Microsoft Docs"
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
  - "extension des bibliothèques de classes"
  - "extensibilité avec les bibliothèques de classes .NET Framework"
  - "indications de conception de bibliothèques de classes (.NET Framework), d’extensibilité"
  - "extensibilité des bibliothèques de classes (.NET Framework)"
ms.assetid: 1cdb8740-871a-456c-9bd9-db96ca8d79b3
caps.latest.revision: 11
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 11
---
# Conception pour l’extensibilit&#233;
Un aspect important de la conception d’une infrastructure de s’assurer de que l’extensibilité de l’infrastructure a été examinée avec soin. Cela nécessite que vous comprenez les coûts et les avantages offerts par les différents mécanismes d’extensibilité. Ce chapitre vous aide à décider des mécanismes d’extensibilité : sous\-classement, événements, les membres virtuels, les rappels et ainsi de suite, peuvent satisfaire au mieux les besoins de votre infrastructure.  
  
 Il existe de nombreuses façons pour permettre l’extensibilité dans les infrastructures. Elles vont de moins puissants mais moins coûteuse à très puissante, mais elle est coûteuse. Pour tous les besoins d’extensibilité donné, vous devez choisir le mécanisme d’extensibilité moins coûteux qui répond aux exigences. N’oubliez pas qu’il est généralement possible d’ajouter plus d’extensibilité plus loin, mais prennent immédiatement sans introduire de modifications avec rupture jamais.  
  
## Dans cette section  
 [Classes unsealed](../../../docs/standard/design-guidelines/unsealed-classes.md)  
 [Membres protégés](../../../docs/standard/design-guidelines/protected-members.md)  
 [Événements et rappels](../../../docs/standard/design-guidelines/events-and-callbacks.md)  
 [Membres virtuels](../../../docs/standard/design-guidelines/virtual-members.md)  
 [Abstractions \(Types et Interfaces abstraits\)](../../../docs/standard/design-guidelines/abstractions-abstract-types-and-interfaces.md)  
 [Classes de base pour l’implémentation d’Abstractions](../../../docs/standard/design-guidelines/base-classes-for-implementing-abstractions.md)  
 [Le fait de sceller](../../../docs/standard/design-guidelines/sealing.md)  
 *Portions © 2005, 2009 Microsoft Corporation. Tous droits réservés.*  
  
 *Réimprimé avec l’autorisation de Pearson éducation, Inc. à partir de [Framework Design Guidelines : Conventions, langages et des modèles pour les bibliothèques .NET réutilisable, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison\-Wesley Professional dans le cadre de la série de développement de Microsoft Windows.*  
  
## Voir aussi  
 [Instructions de conception d’infrastructure](../../../docs/standard/design-guidelines/index.md)