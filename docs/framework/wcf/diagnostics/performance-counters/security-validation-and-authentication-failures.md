---
title: "Nombre d’échecs de la validation de la sécurité et de l’authentification"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0d4e3666-dfc6-421c-baf8-9479c22f7050
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: c1d448d709c7ad20e9d08a291f5a38546cd93ce4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="security-validation-and-authentication-failures"></a><span data-ttu-id="62c3f-102">Nombre d’échecs de la validation de la sécurité et de l’authentification</span><span class="sxs-lookup"><span data-stu-id="62c3f-102">Security Validation and Authentication Failures</span></span>
<span data-ttu-id="62c3f-103">Nom de compteur : nombre d’échecs de la validation de la sécurité et de l’authentification</span><span class="sxs-lookup"><span data-stu-id="62c3f-103">Counter name: Security Validation and Authentication Failures</span></span>  
  
## <a name="description"></a><span data-ttu-id="62c3f-104">Description</span><span class="sxs-lookup"><span data-stu-id="62c3f-104">Description</span></span>  
 <span data-ttu-id="62c3f-105">Ce compteur est incrémenté chaque fois qu'un message est rejeté en raison d'un problème de sécurité non couvert par le compteur « Appels de sécurité non autorisés ».</span><span class="sxs-lookup"><span data-stu-id="62c3f-105">This counter is incremented whenever a message is rejected due to a security problem not covered by the "Security Calls Not Authorized" counter.</span></span> <span data-ttu-id="62c3f-106">Ces problèmes sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="62c3f-106">Such problems include:</span></span>  
  
-   <span data-ttu-id="62c3f-107">Impossibilité de lire le jeton client depuis le message.</span><span class="sxs-lookup"><span data-stu-id="62c3f-107">Client token cannot be read from the message.</span></span>  
  
-   <span data-ttu-id="62c3f-108">Échec de l'authentification du jeton client (par exemple, mot de passe incorrect).</span><span class="sxs-lookup"><span data-stu-id="62c3f-108">Client token has failed authentication (for example, bad password).</span></span>  
  
-   <span data-ttu-id="62c3f-109">Échec de la vérification de signature (par exemple, falsification du message).</span><span class="sxs-lookup"><span data-stu-id="62c3f-109">Signature verification has failed (for example, the message has been tampered).</span></span>  
  
-   <span data-ttu-id="62c3f-110">Le message est un doublon d'un message précédent, ce qui peut se produire lors d'une attaque par relecture.</span><span class="sxs-lookup"><span data-stu-id="62c3f-110">The message is a duplicate from a previous one, which can happen during a replay attack.</span></span>  
  
-   <span data-ttu-id="62c3f-111">Impossibilité de déchiffrer le message.</span><span class="sxs-lookup"><span data-stu-id="62c3f-111">A decryption failure has occurred.</span></span>  
  
-   <span data-ttu-id="62c3f-112">Absence de certains éléments requis dans le message (par exemple, horodatage ou bloc des données chiffrées manquant).</span><span class="sxs-lookup"><span data-stu-id="62c3f-112">Some required elements (for example, missing timestamp or encrypted data block) are missing from the message.</span></span>  
  
-   <span data-ttu-id="62c3f-113">Erreurs lors de la négociation TLSNEGO/SPNEGO.</span><span class="sxs-lookup"><span data-stu-id="62c3f-113">Errors have occurred during TLSNEGO/SPNEGO handshake.</span></span>
