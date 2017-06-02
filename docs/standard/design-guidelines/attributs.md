---
title: "Attributes1 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "attributs (.NET Framework), à propos"
  - "indications de conception de bibliothèques de classes (.NET Framework), attributs"
ms.assetid: ee0038ef-b247-4747-a650-3c5c5cd58d8b
caps.latest.revision: 16
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
---
# Attributs
<xref:System.Attribute?displayProperty=fullName> une classe de base est utilisée pour définir des attributs personnalisés.  
  
 Les attributs sont des annotations qui peuvent être ajoutées aux éléments de programmation tels que les assemblys, types, membres et paramètres. Ils sont stockés dans les métadonnées de l’assembly et sont accessibles lors de l’exécution à l’aide de l’API de réflexion. Par exemple, le Framework définit le <xref:System.ObsoleteAttribute>, qui peut être appliqué à un type ou un membre pour indiquer que le type ou membre a été déconseillé.  
  
 Attributs peuvent avoir une ou plusieurs propriétés qui contiennent des données supplémentaires relatives à l’attribut. Par exemple, `ObsoleteAttribute` peut contenir plus d’informations sur la version dans laquelle un type ou un membre a été déconseillé et la description des nouvelles API en remplaçant l’API obsolète.  
  
 Certaines propriétés d’un attribut doivent être spécifiées lorsque l’attribut est appliqué. Ils sont appelés les propriétés requises ou les arguments requis, car ils sont représentés en tant que paramètres de constructeur de position. Par exemple, le <xref:System.Diagnostics.ConditionalAttribute.ConditionString%2A> propriété de la <xref:System.Diagnostics.ConditionalAttribute> est une propriété obligatoire.  
  
 Les propriétés qui n’ont pas nécessairement être spécifié lorsque l’attribut est appliqué sont appelées propriétés facultatives \(ou les arguments facultatifs\). Ils sont représentés par les propriétés définissables. Les compilateurs fournissent une syntaxe spéciale pour définir ces propriétés lorsqu’un attribut est appliqué. Par exemple, le <xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=fullName> propriété représente un argument facultatif.  
  
 **✓ faire** nom des classes d’attributs personnalisés avec le suffixe « Attribut ».  
  
 **✓ faire** appliquer les <xref:System.AttributeUsageAttribute> aux attributs personnalisés.  
  
 **✓ faire** fournissent des propriétés définies pour les arguments facultatifs.  
  
 **✓ faire** fournissent des propriétés get\-only pour les arguments requis.  
  
 **✓ faire** fournissent des paramètres de constructeur pour initialiser les propriétés qui correspondent aux arguments requis. Chaque paramètre doit avoir le même nom \(mais avec une casse différente\) en tant que la propriété correspondante.  
  
 **X éviter** fournissant des paramètres de constructeur pour initialiser les propriétés qui correspondent aux arguments facultatifs.  
  
 En d’autres termes, n’ont pas de propriétés qui peuvent être définies avec un constructeur et un accesseur Set. Cette règle rend très explicite les arguments sont facultatifs et qui sont nécessaire et évite d’avoir deux façons de faire la même chose.  
  
 **X éviter** la surcharge des constructeurs d’attributs personnalisés.  
  
 Avoir un seul constructeur clairement à l’utilisateur quels sont les arguments requis et facultatifs.  
  
 **✓ faire** sceller des classes d’attributs personnalisés, si possible. Cela accélère la recherche de l’attribut.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Tous droits réservés.*  
  
 *Réimprimé avec l’autorisation de Pearson éducation, Inc. à partir de [Framework Design Guidelines : Conventions, langages et des modèles pour les bibliothèques .NET réutilisable, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison\-Wesley Professional dans le cadre de la série de développement de Microsoft Windows.*  
  
## Voir aussi  
 [Instructions de conception d’infrastructure](../../../docs/standard/design-guidelines/index.md)   
 [Indications relatives à l'utilisation](../../../docs/standard/design-guidelines/usage-guidelines.md)