---
title: StrongNameFreeBuffer, fonction
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: StrongNameFreeBuffer
api_location:
- mscoree.dll
- mscorsn.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
api_type: DLLExport
f1_keywords: StrongNameFreeBuffer
helpviewer_keywords: StrongNameFreeBuffer function [.NET Framework strong naming]
ms.assetid: eda21ecf-4734-4f92-aaba-9f34884385db
topic_type: apiref
caps.latest.revision: "19"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ef48c79cc7dc0fb7d881e0cced29741431044551
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="strongnamefreebuffer-function"></a><span data-ttu-id="0094c-102">StrongNameFreeBuffer, fonction</span><span class="sxs-lookup"><span data-stu-id="0094c-102">StrongNameFreeBuffer Function</span></span>
<span data-ttu-id="0094c-103">Libère la mémoire qui a été allouée avec un appel précédent à une fonction de nom fort, tel que [StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md), [StrongNameTokenFromPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfrompublickey-function.md), ou [StrongNameSignatureGeneration ](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md).</span><span class="sxs-lookup"><span data-stu-id="0094c-103">Frees memory that was allocated with a previous call to a strong name function such as [StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md), [StrongNameTokenFromPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfrompublickey-function.md), or [StrongNameSignatureGeneration](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md).</span></span>  
  
 <span data-ttu-id="0094c-104">Cette fonction est déconseillée.</span><span class="sxs-lookup"><span data-stu-id="0094c-104">This function has been deprecated.</span></span> <span data-ttu-id="0094c-105">Utilisez le [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) méthode à la place.</span><span class="sxs-lookup"><span data-stu-id="0094c-105">Use the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0094c-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0094c-106">Syntax</span></span>  
  
```  
VOID StrongNameFreeBuffer (   
   [in] BYTE   *pbMemory  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0094c-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="0094c-107">Parameters</span></span>  
 `pbMemory`  
 <span data-ttu-id="0094c-108">[in] Pointeur vers la mémoire à libérer.</span><span class="sxs-lookup"><span data-stu-id="0094c-108">[in] A pointer to the memory to free.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0094c-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="0094c-109">Requirements</span></span>  
 <span data-ttu-id="0094c-110">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0094c-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0094c-111">**En-tête :** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="0094c-111">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="0094c-112">**Bibliothèque :** inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0094c-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0094c-113">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0094c-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0094c-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0094c-114">See Also</span></span>  
 [<span data-ttu-id="0094c-115">StrongNameFreeBuffer (méthode)</span><span class="sxs-lookup"><span data-stu-id="0094c-115">StrongNameFreeBuffer Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md)  
 [<span data-ttu-id="0094c-116">ICLRStrongName Interface</span><span class="sxs-lookup"><span data-stu-id="0094c-116">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
