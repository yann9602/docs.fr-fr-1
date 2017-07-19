---
title: "Point de terminaison&#160;: nombre d&#39;&#233;checs de la validation de la s&#233;curit&#233; et de l&#39;authentification | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5bad60aa-6084-4c7b-aefd-9b581f04382e
caps.latest.revision: 6
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 6
---
# Point de terminaison&#160;: nombre d&#39;&#233;checs de la validation de la s&#233;curit&#233; et de l&#39;authentification
Nom de compteur : nombre d'échecs de la validation de la sécurité et de l'authentification  
  
## Description  
 Ce compteur est incrémenté à chaque fois qu'un message est rejeté en raison d'un problème de sécurité non couvert par le compteur Appels de sécurité non autorisés.Ces problèmes sont les suivants :  
  
-   Impossibilité de lire le jeton client depuis le message.  
  
-   L'échec de l'authentification du jeton client \(en raison d'un mot de passe erroné\).  
  
-   L'impossibilité de vérifier la signature \(parce que le message a été falsifié\).  
  
-   Le message est un doublon d'un message précédent, ce qui peut se produire lors d'une attaque par relecture.  
  
-   Impossibilité de déchiffrer le message.  
  
-   L'absence de certains éléments requis dans le message \(horodatage ou bloc des données chiffrées manquant\).  
  
-   Erreurs lors de la négociation TLSNEGO\/SPNEGO.