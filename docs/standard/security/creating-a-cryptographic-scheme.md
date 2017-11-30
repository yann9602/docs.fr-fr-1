---
title: "Création d'un modèle de chiffrement"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- encryption [.NET Framework], creating cryptographic schemes
- cryptography [.NET Framework], creating cryptographic schemes
ms.assetid: d40c509f-5a5e-46cc-94cb-a951e9ab6843
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 3e3c4a832f70fae7808bf71016cb9f6648332f01
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="creating-a-cryptographic-scheme"></a><span data-ttu-id="76b15-102">Création d'un modèle de chiffrement</span><span class="sxs-lookup"><span data-stu-id="76b15-102">Creating a Cryptographic Scheme</span></span>
<span data-ttu-id="76b15-103">Les composants de chiffrement de .NET Framework peuvent être combinés pour créer différents modèles permettant de chiffrer et de déchiffrer des données.</span><span class="sxs-lookup"><span data-stu-id="76b15-103">The cryptographic components of the .NET Framework can be combined to create different schemes to encrypt and decrypt data.</span></span>  
  
 <span data-ttu-id="76b15-104">Un simple modèle de chiffrement pour chiffrer et déchiffrer des données peut spécifier les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="76b15-104">A simple cryptographic scheme for encrypting and decrypting data might specify the following steps:</span></span>  
  
1.  <span data-ttu-id="76b15-105">Chaque partie génère une paire de clés publique/privée.</span><span class="sxs-lookup"><span data-stu-id="76b15-105">Each party generates a public/private key pair.</span></span>  
  
2.  <span data-ttu-id="76b15-106">Les parties échangent leurs clés publiques.</span><span class="sxs-lookup"><span data-stu-id="76b15-106">The parties exchange their public keys.</span></span>  
  
3.  <span data-ttu-id="76b15-107">Chaque partie génère une clé secrète pour le chiffrement TripleDES (par exemple), et chiffre la clé nouvellement créée à l'aide de la clé publique de l'autre.</span><span class="sxs-lookup"><span data-stu-id="76b15-107">Each party generates a secret key for TripleDES encryption, for example, and encrypts the newly created key using the other's public key.</span></span>  
  
4.  <span data-ttu-id="76b15-108">Chaque partie envoie les données à l'autre et combine la clé secrète de l'autre avec la sienne, dans un ordre spécifique, pour créer une clé secrète.</span><span class="sxs-lookup"><span data-stu-id="76b15-108">Each party sends the data to the other and combines the other's secret key with its own, in a particular order, to create a new secret key.</span></span>  
  
5.  <span data-ttu-id="76b15-109">Les parties lancent ensuite une conversation à l'aide du chiffrement symétrique.</span><span class="sxs-lookup"><span data-stu-id="76b15-109">The parties then initiate a conversation using symmetric encryption.</span></span>  
  
 <span data-ttu-id="76b15-110">La création d'un modèle de chiffrement n'est pas une tâche facile.</span><span class="sxs-lookup"><span data-stu-id="76b15-110">Creating a cryptographic scheme is not a trivial task.</span></span> <span data-ttu-id="76b15-111">Pour plus d'informations sur l'utilisation du chiffrement, consultez la rubrique relative au chiffrement de la documentation du Kit de développement Platform SDK, disponible à l'adresse suivante : http://msdn.microsoft.com/library.</span><span class="sxs-lookup"><span data-stu-id="76b15-111">For more information on using cryptography, see the Cryptography topic in the Platform SDK documentation at http://msdn.microsoft.com/library.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76b15-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="76b15-112">See Also</span></span>  
 [<span data-ttu-id="76b15-113">Cryptographic Services</span><span class="sxs-lookup"><span data-stu-id="76b15-113">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)
