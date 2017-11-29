---
title: "Point de terminaison : nombre d’échecs de la validation de la sécurité et de l’authentification"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5bad60aa-6084-4c7b-aefd-9b581f04382e
caps.latest.revision: "6"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 7d1f05ddc4b0fcf93c87e69932f860f3c7e2ff85
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="endpoint-security-validation-and-authentication-failures"></a><span data-ttu-id="21479-102">Point de terminaison : nombre d’échecs de la validation de la sécurité et de l’authentification</span><span class="sxs-lookup"><span data-stu-id="21479-102">Endpoint: Security Validation and Authentication Failures</span></span>
<span data-ttu-id="21479-103">Nom de compteur : nombre d’échecs de la validation de la sécurité et de l’authentification</span><span class="sxs-lookup"><span data-stu-id="21479-103">Counter name: Security Validation and Authentication Failures</span></span>  
  
## <a name="description"></a><span data-ttu-id="21479-104">Description</span><span class="sxs-lookup"><span data-stu-id="21479-104">Description</span></span>  
 <span data-ttu-id="21479-105">Ce compteur est incrémenté chaque fois qu'un message est rejeté en raison d'un problème de sécurité non couvert par le compteur « Appels de sécurité non autorisés ».</span><span class="sxs-lookup"><span data-stu-id="21479-105">This counter is incremented whenever a message is rejected due to a security problem not covered by the "Security Calls Not Authorized" counter.</span></span> <span data-ttu-id="21479-106">Ces problèmes sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="21479-106">Such problems include:</span></span>  
  
-   <span data-ttu-id="21479-107">Impossibilité de lire le jeton client depuis le message.</span><span class="sxs-lookup"><span data-stu-id="21479-107">Client token cannot be read from the message.</span></span>  
  
-   <span data-ttu-id="21479-108">L'échec de l'authentification du jeton client (en raison d'un mot de passe erroné).</span><span class="sxs-lookup"><span data-stu-id="21479-108">Client token has failed authentication (bad password).</span></span>  
  
-   <span data-ttu-id="21479-109">Impossibilité de vérifier la signature (parce que le message a été falsifié).</span><span class="sxs-lookup"><span data-stu-id="21479-109">Signature verification has failed (the message has been tampered).</span></span>  
  
-   <span data-ttu-id="21479-110">Le message est un doublon d'un message précédent, ce qui peut se produire lors d'une attaque par relecture.</span><span class="sxs-lookup"><span data-stu-id="21479-110">The message is a duplicate from a previous one, which can happen during a replay attack.</span></span>  
  
-   <span data-ttu-id="21479-111">Impossibilité de déchiffrer le message.</span><span class="sxs-lookup"><span data-stu-id="21479-111">A decryption failure has occurred.</span></span>  
  
-   <span data-ttu-id="21479-112">L'absence de certains éléments requis dans le message (horodatage ou bloc des données chiffrées manquant).</span><span class="sxs-lookup"><span data-stu-id="21479-112">Some required elements (missing timestamp or encrypted data block) are missing from the message.</span></span>  
  
-   <span data-ttu-id="21479-113">Erreurs lors de la négociation TLSNEGO/SPNEGO.</span><span class="sxs-lookup"><span data-stu-id="21479-113">Errors have occurred during TLSNEGO/SPNEGO handshake.</span></span>
