---
title: "Op&#233;rateurs d&#39;&#233;galit&#233; | Microsoft Docs"
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
  - "indications de conception de bibliothèques de classes (.NET Framework), Equals (méthode)"
  - "indications de conception de bibliothèques de classes (.NET Framework), opérateur d’égalité"
  - "opérateur d’égalité (==) (.NET Framework)"
  - "Equals (méthode)"
  - "== (opérateur) (égalité) (.NET Framework)"
ms.assetid: bc496a91-fefb-4ce0-ab4c-61f09964119a
caps.latest.revision: 13
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 13
---
# Op&#233;rateurs d&#39;&#233;galit&#233;
Cette section décrit les opérateurs d’égalité de surcharge et fait référence à `operator==` et `operator!=` en tant qu’opérateurs d’égalité.  
  
 **X ne pas** surcharger les opérateurs d’égalité et pas l’autre.  
  
 **✓ faire** vous assurer que <xref:System.Object.Equals%2A?displayProperty=fullName> et les opérateurs d’égalité ont exactement la même sémantique et des caractéristiques similaires.  
  
 Cela signifie souvent que `Object.Equals` doit être remplacée lorsque les opérateurs d’égalité sont surchargés.  
  
 **X éviter** lever des exceptions d’opérateurs d’égalité.  
  
 Par exemple, retourne false si l’un des arguments est null au lieu de lever `NullReferenceException`.  
  
## Opérateurs d’égalité sur les Types valeur  
 **✓ faire** surcharger les opérateurs d’égalité sur les types valeur, si l’égalité est explicite.  
  
 Dans la plupart des langages de programmation, il n’existe aucune implémentation par défaut de `operator==` pour les types valeur.  
  
## Opérateurs d’égalité sur les Types référence  
 **X éviter** la surcharge des opérateurs d’égalité sur les types référence mutables.  
  
 Les opérateurs d’égalité intégrés pour les types référence pour de nombreuses langues. Les opérateurs intégrés implémentent généralement l’égalité des références, et de nombreux développeurs sont surpris lorsque le comportement par défaut est modifié à l’égalité des valeurs.  
  
 Ce problème est atténué pour les types référence immuable, car l’immuabilité complique les choses à remarquer la différence entre l’égalité des références et l’égalité des valeurs.  
  
 **X éviter** la surcharge des opérateurs d’égalité sur les types référence si l’implémentation est beaucoup plus lente que celui de l’égalité des références.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Tous droits réservés.*  
  
 *Réimprimé avec l’autorisation de Pearson éducation, Inc. à partir de [Framework Design Guidelines : Conventions, langages et des modèles pour les bibliothèques .NET réutilisable, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison\-Wesley Professional dans le cadre de la série de développement de Microsoft Windows.*  
  
## Voir aussi  
 [Instructions de conception d’infrastructure](../../../docs/standard/design-guidelines/index.md)   
 [Indications relatives à l'utilisation](../../../docs/standard/design-guidelines/usage-guidelines.md)