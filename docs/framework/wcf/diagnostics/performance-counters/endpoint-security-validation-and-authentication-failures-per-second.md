---
title: "Point de terminaison : nombre d’échecs de la validation de la sécurité et de l’authentification par seconde"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 89a70b90-d7e4-4b03-9b84-4dc88ce3d605
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: c6b50aa00fe59d0ad23d5ca0b77c7b89f97a0d1e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="endpoint-security-validation-and-authentication-failures-per-second"></a><span data-ttu-id="a15c9-102">Point de terminaison : nombre d’échecs de la validation de la sécurité et de l’authentification par seconde</span><span class="sxs-lookup"><span data-stu-id="a15c9-102">Endpoint: Security Validation and Authentication Failures Per Second</span></span>
<span data-ttu-id="a15c9-103">Nom du compteur : Nombre d’échecs de validation de la sécurité et d’authentification par seconde</span><span class="sxs-lookup"><span data-stu-id="a15c9-103">Counter name: Security Validation and Authentication Failures Per Second</span></span>  
  
## <a name="description"></a><span data-ttu-id="a15c9-104">Description</span><span class="sxs-lookup"><span data-stu-id="a15c9-104">Description</span></span>  
 <span data-ttu-id="a15c9-105">Ce compteur est incrémenté chaque fois qu'un message est rejeté en raison d'un problème de sécurité non couvert par le compteur « Appels de sécurité non autorisés ».</span><span class="sxs-lookup"><span data-stu-id="a15c9-105">This counter is incremented whenever a message is rejected due to a security problem not covered by the "Security Calls Not Authorized" counter.</span></span> <span data-ttu-id="a15c9-106">Ces problèmes sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="a15c9-106">Such problems include:</span></span>  
  
-   <span data-ttu-id="a15c9-107">Impossibilité de lire le jeton client depuis le message.</span><span class="sxs-lookup"><span data-stu-id="a15c9-107">Client token cannot be read from the message.</span></span>  
  
-   <span data-ttu-id="a15c9-108">Échec de l'authentification du jeton client (par exemple, mot de passe incorrect).</span><span class="sxs-lookup"><span data-stu-id="a15c9-108">Client token has failed authentication (for example, bad password).</span></span>  
  
-   <span data-ttu-id="a15c9-109">Échec de la vérification de signature (par exemple, falsification du message).</span><span class="sxs-lookup"><span data-stu-id="a15c9-109">Signature verification has failed (for example, the message has been tampered).</span></span>  
  
-   <span data-ttu-id="a15c9-110">Le message est un doublon d'un message précédent, ce qui peut se produire lors d'une attaque par relecture.</span><span class="sxs-lookup"><span data-stu-id="a15c9-110">The message is a duplicate from a previous one, which can happen during a replay attack.</span></span>  
  
-   <span data-ttu-id="a15c9-111">Impossibilité de déchiffrer le message.</span><span class="sxs-lookup"><span data-stu-id="a15c9-111">A decryption failure has occurred.</span></span>  
  
-   <span data-ttu-id="a15c9-112">Absence de certains éléments requis dans le message (par exemple, horodatage ou bloc des données chiffrées manquant).</span><span class="sxs-lookup"><span data-stu-id="a15c9-112">Some required elements (for example, missing timestamp or encrypted data block) are missing from the message.</span></span>  
  
-   <span data-ttu-id="a15c9-113">Erreurs lors de la négociation TLSNEGO/SPNEGO.</span><span class="sxs-lookup"><span data-stu-id="a15c9-113">Errors have occurred during TLSNEGO/SPNEGO handshake.</span></span>  
  
 <span data-ttu-id="a15c9-114">Ce compteur est de type de compteur de performances [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), dont la valeur est calculée à l’aide de la formule suivante :</span><span class="sxs-lookup"><span data-stu-id="a15c9-114">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula:</span></span>  
  
 <span data-ttu-id="a15c9-115">(N1-N0)/((D1-D0)/F)</span><span class="sxs-lookup"><span data-stu-id="a15c9-115">(N1-N0)/((D1-D0)/F)</span></span>
