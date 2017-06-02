---
title: "Ressources d’affectation de noms | Microsoft Docs"
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
  - "ressources localisées de noms [.NET Framework]"
  - "localisation, les règles de dénomination"
  - "noms de ressources"
  - "applications globales, règles de dénomination"
  - "applications internationales, règles de dénomination"
ms.assetid: 8b0e97f3-7877-44fd-bc76-e05d36d5d79c
caps.latest.revision: 9
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 9
---
# Ressources d’affectation de noms
Étant donné que les ressources localisables peuvent être référencés via certains objets comme s’ils étaient des propriétés, les instructions d’affectation de noms pour les ressources sont similaires aux indications de la propriété.  
  
 **✓ faire** utilisent la casse Pascal dans les clés de ressources.  
  
 **✓ faire** fournir descriptif au lieu d’identificateurs courts.  
  
 **X ne pas** utiliser des mots clés spécifiques au langage principal langage CLR.  
  
 **✓ faire** utiliser uniquement des caractères alphanumériques et des traits de soulignement dans les noms des ressources.  
  
 **✓ faire** utiliser la convention d’affectation de noms suivante pour les ressources de message d’exception.  
  
 L’identificateur de ressource doit être un identificateur court de l’exception ainsi que le nom de type d’exception :  
  
 `ArgumentExceptionIllegalCharacters`   
 `ArgumentExceptionInvalidName`   
 `ArgumentExceptionFileNameIsMalformed`  
  
 *Portions © 2005, 2009 Microsoft Corporation. Tous droits réservés.*  
  
 *Réimprimé avec l’autorisation de Pearson éducation, Inc. à partir de [Framework Design Guidelines : Conventions, langages et des modèles pour les bibliothèques .NET réutilisable, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison\-Wesley Professional dans le cadre de la série de développement de Microsoft Windows.*  
  
## Voir aussi  
 [Instructions de conception d’infrastructure](../../../docs/standard/design-guidelines/index.md)   
 [Indications concernant l'attribution d'un nom](../../../docs/standard/design-guidelines/naming-guidelines.md)