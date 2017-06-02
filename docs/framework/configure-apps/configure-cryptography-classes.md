---
title: "Configuration de classes de chiffrement | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
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
  - "configuration d'applications .NET Framework, chiffrement"
  - "fichiers de configuration (.NET Framework), chiffrement"
  - "algorithmes de chiffrement"
  - "chiffrement, classes"
  - "chiffrement par défaut"
  - "sécurité (.NET Framework), chiffrement"
ms.assetid: eee3ccb8-2c0d-4f35-b38d-6892a46c14e5
caps.latest.revision: 9
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 9
---
# Configuration de classes de chiffrement
Le [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] permet aux administrateurs d'ordinateur de configurer les algorithmes de chiffrement par défaut et les implémentations d'algorithme que peuvent utiliser le .NET Framework et les applications écrites de façon adéquate.  Par exemple, une entreprise possédant sa propre implémentation d'un algorithme de chiffrement peut en faire l'implémentation par défaut au lieu de conserver celle qui est fournie avec le [!INCLUDE[winsdkshort](../../../includes/winsdkshort-md.md)].  Bien que la liaison explicite à une implémentation particulière soit toujours possible pour les applications managées utilisant le chiffrement, il est recommandé que ces dernières créent des objets de chiffrement au moyen du système de configuration de chiffrement.  
  
## Dans cette section  
 [Mappage de noms d'algorithmes à des classes de chiffrement](../../../docs/framework/configure-apps/map-algorithm-names-to-cryptography-classes.md)  
 Décrit comment mapper un nom d'algorithme à une classe de chiffrement.  
  
 [Mappage d'identificateurs d'objet à des algorithmes de chiffrement](../../../docs/framework/configure-apps/map-object-identifiers-to-cryptography-algorithms.md)  
 Décrit comment mapper un identificateur d'objet à un algorithme de chiffrement.  
  
## Rubriques connexes  
 [Services de chiffrement](../../../docs/standard/security/cryptographic-services.md)  
 Offre une vue d'ensemble des services de chiffrement fournis par le [!INCLUDE[winsdkshort](../../../includes/winsdkshort-md.md)].  
  
 [Schéma des paramètres de chiffrement](../../../docs/framework/configure-apps/file-schema/cryptography/index.md)  
 Décrit des éléments qui mappent des noms d'algorithmes conviviaux à des classes implémentant des algorithmes de chiffrement.