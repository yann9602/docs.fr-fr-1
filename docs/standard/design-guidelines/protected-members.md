---
title: "Membres prot&#233;g&#233;s | Microsoft Docs"
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
  - "membres (.NET Framework), protégés"
  - "membres protégés"
  - "classes (.NET Framework), non scellés"
  - "membres de classes (.NET Framework), protégés"
  - "classes unsealed"
  - "personnalisation du comportement de classe"
ms.assetid: aa0b58ee-3956-494d-ab48-471ae5db8740
caps.latest.revision: 9
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 9
---
# Membres prot&#233;g&#233;s
Les membres protégés par elles\-mêmes ne fournissent pas tout extensibilité, mais elles peuvent rendre extensibilité via le sous\-classement plus puissant. Ils permettent d’exposer les options de personnalisation avancée sans compliquer inutilement l’interface publique principale.  
  
 Concepteurs doivent être prudent avec les membres protégés, car le nom « protégé » peut donner un faux sentiment de sécurité. Toute personne est en mesure de sous\-classe d’une classe non verrouillée et les membres de l’accès protégé, et donc les mêmes pratiques de codage défensifs utilisés pour les membres publics s’appliquent aux membres protégés.  
  
 **✓ envisagez** à l’aide de membres pour la personnalisation avancée protégés.  
  
 **✓ faire** traite les membres protégés dans les classes unsealed public pour les besoins de sécurité, la documentation et compatibilité analysis.  
  
 Toute personne peut hériter d’une classe et accéder aux membres protégés.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Tous droits réservés.*  
  
 *Réimprimé avec l’autorisation de Pearson éducation, Inc. à partir de [Framework Design Guidelines : Conventions, langages et des modèles pour les bibliothèques .NET réutilisable, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison\-Wesley Professional dans le cadre de la série de développement de Microsoft Windows.*  
  
## Voir aussi  
 [Instructions de conception d’infrastructure](../../../docs/standard/design-guidelines/index.md)   
 [Conception pour l’extensibilité](../../../docs/standard/design-guidelines/designing-for-extensibility.md)