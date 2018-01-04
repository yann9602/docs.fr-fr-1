---
title: Attributes1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- attributes [.NET Framework], about
- class library design guidelines [.NET Framework], attributes
ms.assetid: ee0038ef-b247-4747-a650-3c5c5cd58d8b
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 89e892a379c7540cf67488471ae5281a4c4b86f4
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2017
---
# <a name="attributes"></a>Attributs
<xref:System.Attribute?displayProperty=nameWithType>une classe de base est utilisée pour définir des attributs personnalisés.  
  
 Les attributs sont des annotations qui peuvent être ajoutées aux éléments de programmation tels que des assemblys, types, membres et paramètres. Ils sont stockés dans les métadonnées de l’assembly et sont accessibles lors de l’exécution à l’aide de l’API de réflexion. Par exemple, le Framework définit le <xref:System.ObsoleteAttribute>, ce qui peut être appliqué à un type ou un membre pour indiquer que le type ou membre a été déconseillé.  
  
 Attributs peuvent avoir une ou plusieurs propriétés qui contiennent des données supplémentaires liées à l’attribut. Par exemple, `ObsoleteAttribute` pourrait exécuter plus d’informations sur la version dans lequel un type ou un membre a été déconseillé et la description de nouvelles API en remplaçant l’API obsolète.  
  
 Certaines propriétés d’un attribut doivent être spécifiées lorsque l’attribut est appliqué. Ils sont appelés les propriétés requises ou les arguments requis, car ils sont représentés en tant que paramètres du constructeur de position. Par exemple, le <xref:System.Diagnostics.ConditionalAttribute.ConditionString%2A> propriété de la <xref:System.Diagnostics.ConditionalAttribute> est une propriété obligatoire.  
  
 Les propriétés qui n’ont pas nécessairement être spécifié lorsque l’attribut est appliqué sont appelées propriétés facultatives (ou les arguments facultatifs). Ils sont représentés par les propriétés définissables. Les compilateurs fournissent une syntaxe spéciale pour définir ces propriétés lorsqu’un attribut est appliqué. Par exemple, le <xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=nameWithType> propriété représente un argument facultatif.  
  
 **✓ FAIRE** nommez des classes d’attributs personnalisés avec le suffixe « Attribut ».  
  
 **✓ FAIRE** appliquer le <xref:System.AttributeUsageAttribute> à des attributs personnalisés.  
  
 **✓ FAIRE** fournir les propriétés définissables pour les arguments facultatifs.  
  
 **✓ FAIRE** fournissent des propriétés get uniquement pour les arguments requis.  
  
 **✓ FAIRE** fournissent des paramètres du constructeur pour initialiser les propriétés qui correspondent aux arguments requis. Chaque paramètre doit avoir le même nom (mais avec une casse différente) en tant que la propriété correspondante.  
  
 **X Évitez** fournissant les paramètres du constructeur pour initialiser les propriétés qui correspondent aux arguments facultatifs.  
  
 En d’autres termes, n’ont pas de propriétés qui peuvent être définies avec un constructeur et un accesseur Set. Cette règle rend très explicite les arguments sont facultatifs et qui sont nécessaire et évite d’avoir deux façons de faire la même chose.  
  
 **X Évitez** surcharge des constructeurs d’attribut personnalisé.  
  
 Avoir qu’un seul constructeur clairement à l’utilisateur qui sont obligatoires et facultatifs.  
  
 **✓ FAIRE** sceller des classes d’attributs personnalisés, si possible. Cela accélère la recherche de l’attribut.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Tous droits réservés.*  
  
 *Réimprimées avec l’autorisation de Pearson éducation, Inc. à partir de [règles de conception d’infrastructure : Conventions, idiomes et des modèles pour les bibliothèques .NET réutilisable, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série de développement Microsoft Windows.*  
  
## <a name="see-also"></a>Voir aussi  
 [Règles de conception de .NET Framework](../../../docs/standard/design-guidelines/index.md)  
 [Indications relatives à l’utilisation](../../../docs/standard/design-guidelines/usage-guidelines.md)
