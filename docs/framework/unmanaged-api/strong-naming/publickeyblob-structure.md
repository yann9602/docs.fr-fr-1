---
title: PublicKeyBlob, structure
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: PublicKeyBlob
api_location: mscoree.dll
api_type: COM
f1_keywords: PublicKeyBlob
helpviewer_keywords: PublicKeyBlob structure [.NET Framework strong naming]
ms.assetid: b9240712-829c-4c8d-9a09-a6e7aa63f63a
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e273570c77b2855d942db580be95b040870a4c01
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="publickeyblob-structure"></a><span data-ttu-id="6d6a5-102">PublicKeyBlob, structure</span><span class="sxs-lookup"><span data-stu-id="6d6a5-102">PublicKeyBlob Structure</span></span>
<span data-ttu-id="6d6a5-103">Représente, en format binaire, la clé publique d’une paire de clés publique/privée.</span><span class="sxs-lookup"><span data-stu-id="6d6a5-103">Represents, in binary format, the public key of a public/private key pair.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d6a5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6d6a5-104">Syntax</span></span>  
  
```  
typedef struct {  
    unsigned int SigAlgId;  
    unsigned int HashAlgId;  
    ULONG cbPublicKey;  
    BYTE PublicKey[1]  
} PublicKeyBlob;   
```  
  
## <a name="members"></a><span data-ttu-id="6d6a5-105">Membres</span><span class="sxs-lookup"><span data-stu-id="6d6a5-105">Members</span></span>  
  
|<span data-ttu-id="6d6a5-106">Membre</span><span class="sxs-lookup"><span data-stu-id="6d6a5-106">Member</span></span>|<span data-ttu-id="6d6a5-107">Description</span><span class="sxs-lookup"><span data-stu-id="6d6a5-107">Description</span></span>|  
|------------|-----------------|  
|`SigAlgId`|<span data-ttu-id="6d6a5-108">L’identificateur de l’algorithme de signature (de type `ALG_ID`, comme défini dans WinCrypt.h) de la clé publique.</span><span class="sxs-lookup"><span data-stu-id="6d6a5-108">The identifier for the signature algorithm (of type `ALG_ID`, as defined in WinCrypt.h) of the public key.</span></span>|  
|`HashAlgId`|<span data-ttu-id="6d6a5-109">L’identificateur de l’algorithme de hachage (de type `ALG_ID`, comme défini dans WinCrypt.h) de la clé publique.</span><span class="sxs-lookup"><span data-stu-id="6d6a5-109">The identifier for the hash algorithm (of type `ALG_ID`, as defined in WinCrypt.h) of the public key.</span></span>|  
|`cbPublicKey`|<span data-ttu-id="6d6a5-110">La longueur de la clé en octets.</span><span class="sxs-lookup"><span data-stu-id="6d6a5-110">The length of the key in bytes.</span></span>|  
|`PublicKey`|<span data-ttu-id="6d6a5-111">Tableau d’octets de longueur variable qui contient la valeur de clé dans le format retourné par CryptoAPI.</span><span class="sxs-lookup"><span data-stu-id="6d6a5-111">A variable-length byte array that contains the key value in the format returned by the CryptoAPI.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6d6a5-112">Remarques</span><span class="sxs-lookup"><span data-stu-id="6d6a5-112">Remarks</span></span>  
 <span data-ttu-id="6d6a5-113">Le `PublicKeyBlob` structure est utilisée par [StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md), [StrongNameSignatureGeneration](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md)et d’autres fonctions de nom fort pour représenter la clé publique d’une paire de clés publique/privée.</span><span class="sxs-lookup"><span data-stu-id="6d6a5-113">The `PublicKeyBlob` structure is used by [StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md), [StrongNameSignatureGeneration](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md), and other strong name functions to represent the public key of a public/private key pair.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d6a5-114">Spécifications</span><span class="sxs-lookup"><span data-stu-id="6d6a5-114">Requirements</span></span>  
 <span data-ttu-id="6d6a5-115">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6d6a5-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6d6a5-116">**En-tête :** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="6d6a5-116">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="6d6a5-117">**Bibliothèque :** inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6d6a5-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6d6a5-118">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d6a5-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d6a5-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6d6a5-119">See Also</span></span>  
 [<span data-ttu-id="6d6a5-120">StrongNameGetPublicKey, fonction</span><span class="sxs-lookup"><span data-stu-id="6d6a5-120">StrongNameGetPublicKey Function</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md)  
 [<span data-ttu-id="6d6a5-121">StrongNameSignatureGeneration (fonction)</span><span class="sxs-lookup"><span data-stu-id="6d6a5-121">StrongNameSignatureGeneration Function</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md)  
 [<span data-ttu-id="6d6a5-122">Structures de noms forts</span><span class="sxs-lookup"><span data-stu-id="6d6a5-122">Strong Naming Structures</span></span>](http://msdn.microsoft.com/en-us/4b041a2f-fd12-4b91-aacd-bc3b34a5124d)
