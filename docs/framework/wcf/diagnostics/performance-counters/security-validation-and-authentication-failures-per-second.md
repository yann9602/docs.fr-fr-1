---
title: "Nombre d&#39;&#233;checs de validation de la s&#233;curit&#233; et d&#39;authentification par seconde | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 266c3bd3-2ffc-4471-94b7-3675443be1ac
caps.latest.revision: 8
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 8
---
# Nombre d&#39;&#233;checs de validation de la s&#233;curit&#233; et d&#39;authentification par seconde
Nom du compteur : nombre d'échecs de la validation de la sécurité et de l'authentification par seconde.  
  
## Description  
 Ce compteur est incrémenté chaque fois qu'un message est rejeté en raison d'un problème de sécurité non traité par le compteur « Appels de sécurité non autorisés ».Ces problèmes sont les suivants :  
  
-   Impossibilité de lire le jeton client à partir du message.  
  
-   Échec de l'authentification du jeton client \(par exemple, mot de passe incorrect\).  
  
-   Échec de la vérification de signature \(par exemple, falsification du message\).  
  
-   Le message est un doublon d'un message précédent, ce qui peut se produire lors d'une attaque par relecture.  
  
-   Échec du déchiffrement.  
  
-   Absence de certains éléments requis dans le message \(par exemple, horodatage ou bloc des données chiffrées manquant\).  
  
-   Erreurs lors de la négociation TLSNEGO\/SPNEGO.  
  
 Ce compteur de performance est de type [PERF\_COUNTER\_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), dont la valeur est calculée à l'aide de la formule suivante :  
  
 \(N1\-N0\)\/\(\(D1\-D0\)\/F\)