---
title: "Param&#232;tres d’affectation de noms | Microsoft Docs"
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
  - "paramètres, noms"
  - "noms (.NET Framework), paramètres"
ms.assetid: ca3c956e-725a-441b-b4e3-eab5d472f41c
caps.latest.revision: 9
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 9
---
# Param&#232;tres d’affectation de noms
Au\-delà de la raison évidente de lisibilité, il est important de suivre les instructions pour les noms de paramètre, car les paramètres sont affichés dans la documentation et dans le concepteur lorsque les outils de conception visuelle fournissent Intellisense et la classe de fonctionnalités de navigation.  
  
 **✓ faire** utilisez la casse mixte dans les noms de paramètre.  
  
 **✓ faire** utiliser des noms de paramètres descriptifs.  
  
 **✓ envisagez** à l’aide de noms basés sur la signification du paramètre plutôt que le type de paramètre.  
  
### Paramètres de la surcharge d’opérateur d’affectation de noms  
 **✓ faire** utiliser `left` et `right` pour les noms de paramètre opérateur binaire surcharge s’il n’existe pas de signification pour les paramètres.  
  
 **✓ faire** utiliser `value` pour unaire surcharge d’opérateur les noms de paramètres s’il n’existe pas de signification pour les paramètres.  
  
 **✓ envisagez** des noms significatifs pour l’opérateur de surcharge paramètres si cela ajoute une valeur ajoutée significative.  
  
 **X ne pas** abréviations d’utilisation ou d’index numérique pour l’opérateur surcharge les noms de paramètres.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Tous droits réservés.*  
  
 *Réimprimé avec l’autorisation de Pearson éducation, Inc. à partir de [Framework Design Guidelines : Conventions, langages et des modèles pour les bibliothèques .NET réutilisable, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison\-Wesley Professional dans le cadre de la série de développement de Microsoft Windows.*  
  
## Voir aussi  
 [Instructions de conception d’infrastructure](../../../docs/standard/design-guidelines/index.md)   
 [Indications concernant l'attribution d'un nom](../../../docs/standard/design-guidelines/naming-guidelines.md)