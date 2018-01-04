---
title: StrongNameHashSize, fonction
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: StrongNameHashSize
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: StrongNameHashSize
helpviewer_keywords: StrongNameHashSize function [.NET Framework strong naming]
ms.assetid: 738c98d7-a60c-45fe-a296-220af05e6991
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 20a0d5fc284dde7b127f1f177a448a95701ac8b7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="strongnamehashsize-function"></a><span data-ttu-id="2e630-102">StrongNameHashSize, fonction</span><span class="sxs-lookup"><span data-stu-id="2e630-102">StrongNameHashSize Function</span></span>
<span data-ttu-id="2e630-103">Obtient la taille de mémoire tampon requise pour un hachage à l’aide de l’algorithme de hachage spécifié.</span><span class="sxs-lookup"><span data-stu-id="2e630-103">Gets the buffer size required for a hash, using the specified hash algorithm.</span></span>  
  
 <span data-ttu-id="2e630-104">Cette fonction est déconseillée.</span><span class="sxs-lookup"><span data-stu-id="2e630-104">This function has been deprecated.</span></span> <span data-ttu-id="2e630-105">Utilisez le [ICLRStrongName::StrongNameHashSize](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamehashsize-method.md) méthode à la place.</span><span class="sxs-lookup"><span data-stu-id="2e630-105">Use the [ICLRStrongName::StrongNameHashSize](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamehashsize-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e630-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2e630-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameHashSize (  
    [in]  ULONG   ulHashAlg,  
    [out] DWORD   *pcbSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2e630-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2e630-107">Parameters</span></span>  
 `ulHashAlg`  
 <span data-ttu-id="2e630-108">[in] L’algorithme de hachage utilisé pour calculer la taille du tampon.</span><span class="sxs-lookup"><span data-stu-id="2e630-108">[in] The hash algorithm used to compute the buffer size.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="2e630-109">[out] La taille de la mémoire tampon retournée, en octets.</span><span class="sxs-lookup"><span data-stu-id="2e630-109">[out] The returned buffer size, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2e630-110">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="2e630-110">Return Value</span></span>  
 <span data-ttu-id="2e630-111">`true`de réussite ; dans le cas contraire, `false`.</span><span class="sxs-lookup"><span data-stu-id="2e630-111">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2e630-112">Notes</span><span class="sxs-lookup"><span data-stu-id="2e630-112">Remarks</span></span>  
 <span data-ttu-id="2e630-113">Si le `StrongNameHashSize` (fonction) ne pas aboutir, appelez le [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) fonction pour récupérer la dernière erreur générée.</span><span class="sxs-lookup"><span data-stu-id="2e630-113">If the `StrongNameHashSize` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2e630-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="2e630-114">Requirements</span></span>  
 <span data-ttu-id="2e630-115">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2e630-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2e630-116">**En-tête :** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="2e630-116">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="2e630-117">**Bibliothèque :** inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2e630-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2e630-118">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2e630-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e630-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2e630-119">See Also</span></span>  
 [<span data-ttu-id="2e630-120">StrongNameHashSize, méthode</span><span class="sxs-lookup"><span data-stu-id="2e630-120">StrongNameHashSize Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamehashsize-method.md)  
 [<span data-ttu-id="2e630-121">ICLRStrongName, interface</span><span class="sxs-lookup"><span data-stu-id="2e630-121">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
