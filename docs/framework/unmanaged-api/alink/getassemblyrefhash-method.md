---
title: "GetAssemblyRefHash, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink.GetAssemblyRefHash
api_location: alink.dll
api_type: COM
f1_keywords: GetAssemblyRefHash
helpviewer_keywords: GetAssemblyRefHash method
ms.assetid: 091a18bd-e901-46f6-b999-74d71c8a7c41
topic_type: apiref
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 99ae38025f223d669a428738783676ebc0687554
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="getassemblyrefhash-method"></a><span data-ttu-id="36d4c-102">GetAssemblyRefHash, méthode</span><span class="sxs-lookup"><span data-stu-id="36d4c-102">GetAssemblyRefHash Method</span></span>
<span data-ttu-id="36d4c-103">Récupère un objet blob de hachage pour un assembly donné.</span><span class="sxs-lookup"><span data-stu-id="36d4c-103">Retrieves a hash blob for a given assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36d4c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="36d4c-104">Syntax</span></span>  
  
```  
HRESULT GetAssemblyRefHash(  
    mdToken FileToken,  
    const void** ppvHash,  
    DWORD* pcbHash  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="36d4c-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="36d4c-105">Parameters</span></span>  
 `FileToken`  
 <span data-ttu-id="36d4c-106">ID de l’assembly à laquelle fait référence le code de hachage.</span><span class="sxs-lookup"><span data-stu-id="36d4c-106">ID of assembly to which the hash will refer.</span></span>  
  
 `ppvHash`  
 <span data-ttu-id="36d4c-107">Reçoit le blob de hachage obtenue.</span><span class="sxs-lookup"><span data-stu-id="36d4c-107">Receives the resulting hash blob.</span></span>  
  
 `pcbHash`  
 <span data-ttu-id="36d4c-108">Reçoit la taille, en octets, de l’objet blob de hachage.</span><span class="sxs-lookup"><span data-stu-id="36d4c-108">Receives size, in bytes, of hash blob.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="36d4c-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="36d4c-109">Return Value</span></span>  
 <span data-ttu-id="36d4c-110">Retourne S_OK si la méthode réussit.</span><span class="sxs-lookup"><span data-stu-id="36d4c-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="36d4c-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="36d4c-111">Requirements</span></span>  
 <span data-ttu-id="36d4c-112">Requiert alink.h</span><span class="sxs-lookup"><span data-stu-id="36d4c-112">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36d4c-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="36d4c-113">See Also</span></span>  
 [<span data-ttu-id="36d4c-114">IALink, interface</span><span class="sxs-lookup"><span data-stu-id="36d4c-114">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="36d4c-115">IALink2, interface</span><span class="sxs-lookup"><span data-stu-id="36d4c-115">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="36d4c-116">API ALink</span><span class="sxs-lookup"><span data-stu-id="36d4c-116">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
