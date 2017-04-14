---
title: "Nombre d&#39;&#233;checs de la validation de la s&#233;curit&#233; et de l&#39;authentification | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0d4e3666-dfc6-421c-baf8-9479c22f7050
caps.latest.revision: 8
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 8
---
# Nombre d&#39;&#233;checs de la validation de la s&#233;curit&#233; et de l&#39;authentification
Nom de compteur : nombre d'échecs de la validation de la sécurité et de l'authentification  
  
## Description  
 Ce compteur est incrémenté à chaque fois qu'un message est rejeté en raison d'un problème de sécurité non couvert par le compteur Appels de sécurité non autorisés.Ces problèmes sont les suivants :  
  
-   Impossibilité de lire le jeton client à partir du message.  
  
-   Échec de l'authentification du jeton client \(par exemple, mot de passe incorrect\).  
  
-   Échec de la vérification de signature \(par exemple, falsification du message\).  
  
-   Le message est un doublon d'un message précédent, ce qui peut se produire lors d'une attaque par relecture.  
  
-   Échec du déchiffrement.  
  
-   Absence de certains éléments requis dans le message \(par exemple, horodateur ou bloc de données chiffrées manquant\).  
  
-   Erreurs lors de la négociation TLSNEGO\/SPNEGO.