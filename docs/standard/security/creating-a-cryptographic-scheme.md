---
title: "Cr&#233;ation d&#39;un mod&#232;le de chiffrement | Microsoft Docs"
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
  - "chiffrement (.NET Framework), créer des schémas de chiffrement"
  - "chiffrement (.NET Framework), créer des schémas de chiffrement"
ms.assetid: d40c509f-5a5e-46cc-94cb-a951e9ab6843
caps.latest.revision: 8
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 8
---
# Cr&#233;ation d&#39;un mod&#232;le de chiffrement
Les composants de chiffrement de .NET Framework peuvent être combinés pour créer différents modèles permettant de chiffrer et de déchiffrer des données.  
  
 Un simple modèle de chiffrement pour chiffrer et déchiffrer des données peut spécifier les étapes suivantes :  
  
1.  Chaque partie génère une paire de clés publique\/privée.  
  
2.  Les parties échangent leurs clés publiques.  
  
3.  Chaque partie génère une clé secrète pour le chiffrement TripleDES \(par exemple\), et chiffre la clé nouvellement créée à l'aide de la clé publique de l'autre.  
  
4.  Chaque partie envoie les données à l'autre et combine la clé secrète de l'autre avec la sienne, dans un ordre spécifique, pour créer une clé secrète.  
  
5.  Les parties lancent ensuite une conversation à l'aide du chiffrement symétrique.  
  
 La création d'un modèle de chiffrement n'est pas une tâche facile.  Pour plus d'informations sur l'utilisation du chiffrement, consultez la rubrique relative au chiffrement de la documentation du Kit de développement Platform SDK, disponible à l'adresse suivante : http:\/\/msdn.microsoft.com\/library.  
  
## Voir aussi  
 [Services de chiffrement](../../../docs/standard/security/cryptographic-services.md)