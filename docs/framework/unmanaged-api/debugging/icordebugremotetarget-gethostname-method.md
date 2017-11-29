---
title: "ICorDebugRemoteTarget::GetHostName, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugRemoteTarget.GetHostName
api_location: CorDebug.dll
api_type: COM
f1_keywords: ICorDebugRemoteTarget::GetHostName
helpviewer_keywords:
- ICorDebugRemoteTarget::GetHostName method [.NET Framework debugging]
- GetHostName method, ICorDebugRemoteTarget interface [.NET Framework debugging]
ms.assetid: 1c7276f7-7e54-470c-808c-e13745ac07a1
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2af5d75145b9fdd2d370b76f798c5e350d8bec50
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugremotetargetgethostname-method"></a><span data-ttu-id="d9ce2-102">ICorDebugRemoteTarget::GetHostName, méthode</span><span class="sxs-lookup"><span data-stu-id="d9ce2-102">ICorDebugRemoteTarget::GetHostName Method</span></span>
<span data-ttu-id="d9ce2-103">Retourne le nom de domaine complet ou l’adresse IPv4 de l’ordinateur cible de débogage distant.</span><span class="sxs-lookup"><span data-stu-id="d9ce2-103">Returns the fully qualified domain name or IPv4 address of the remote debugging target machine.</span></span> <span data-ttu-id="d9ce2-104">IPv6 n’est pas pris en charge pour l’instant.</span><span class="sxs-lookup"><span data-stu-id="d9ce2-104">IPV6 is not supported at this time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9ce2-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d9ce2-105">Syntax</span></span>  
  
```  
HRESULT GetHostName (  
    [in] ULONG32      cchHostName,  
    [out] ULONG32*    pcchHostName,  
    [out, size_is(cchHostName), length_is(*pcchHostName)]  
            WCHAR szHostName[]  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d9ce2-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d9ce2-106">Parameters</span></span>  
 `cchHostName`  
 <span data-ttu-id="d9ce2-107">[in] La taille, en caractères, de la `szHostName` mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="d9ce2-107">[in] The size, in characters, of the `szHostName` buffer.</span></span> <span data-ttu-id="d9ce2-108">Si ce paramètre est 0 (zéro), `szHostName` doit être null.</span><span class="sxs-lookup"><span data-stu-id="d9ce2-108">If this parameter is 0 (zero), `szHostName` must be null.</span></span>  
  
 `pcchHostName`  
 <span data-ttu-id="d9ce2-109">[out] Le nombre de caractères, y compris une marque de fin null, dans le nom d’hôte ou adresse IP.</span><span class="sxs-lookup"><span data-stu-id="d9ce2-109">[out] The number of characters, including a null terminator, in the host name or IP address.</span></span> <span data-ttu-id="d9ce2-110">Ce paramètre peut avoir la valeur Null.</span><span class="sxs-lookup"><span data-stu-id="d9ce2-110">This parameter can be null.</span></span>  
  
 `szHostName`  
 <span data-ttu-id="d9ce2-111">[out] Mémoire tampon qui contient le nom d’hôte ou adresse IP.</span><span class="sxs-lookup"><span data-stu-id="d9ce2-111">[out] Buffer that contains the host name or IP address.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d9ce2-112">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="d9ce2-112">Return Value</span></span>  
 <span data-ttu-id="d9ce2-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="d9ce2-113">S_OK</span></span>  
 <span data-ttu-id="d9ce2-114">Le nom d’hôte ou l’adresse IP a été retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="d9ce2-114">The host name or IP address was successfully returned.</span></span>  
  
 <span data-ttu-id="d9ce2-115">E_FAIL (ou autres codes de retour E_)</span><span class="sxs-lookup"><span data-stu-id="d9ce2-115">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="d9ce2-116">Impossible de retourner le nom d’hôte ou adresse IP.</span><span class="sxs-lookup"><span data-stu-id="d9ce2-116">Unable to return the host name or IP address.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d9ce2-117">Remarques</span><span class="sxs-lookup"><span data-stu-id="d9ce2-117">Remarks</span></span>  
 <span data-ttu-id="d9ce2-118">Cette méthode est implémentée par le writer du débogueur.</span><span class="sxs-lookup"><span data-stu-id="d9ce2-118">This method is implemented by the debugger writer.</span></span> <span data-ttu-id="d9ce2-119">Elle doit suivre le paradigme appel plusieurs : sur le premier appel, l’appelant passe la valeur null à la fois aux `cchHostName` et `szHostName`, et `pcchHostName` retourne la taille de la mémoire tampon requise.</span><span class="sxs-lookup"><span data-stu-id="d9ce2-119">It must follow the multiple call paradigm: On the first call, the caller passes null to both `cchHostName` and `szHostName`, and `pcchHostName` returns the size of the required buffer .</span></span> <span data-ttu-id="d9ce2-120">Sur le deuxième appel, la taille qui a été retournée précédemment est passée dans `cchHostName`, et une mémoire tampon de taille appropriée est passé dans `szHostName`.</span><span class="sxs-lookup"><span data-stu-id="d9ce2-120">On the second call, the size that was previously returned is passed in `cchHostName`, and an appropriately sized buffer is passed in `szHostName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d9ce2-121">Spécifications</span><span class="sxs-lookup"><span data-stu-id="d9ce2-121">Requirements</span></span>  
 <span data-ttu-id="d9ce2-122">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d9ce2-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d9ce2-123">**En-tête :** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="d9ce2-123">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="d9ce2-124">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d9ce2-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d9ce2-125">**Versions du .NET framework :** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="d9ce2-125">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9ce2-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d9ce2-126">See Also</span></span>  
 [<span data-ttu-id="d9ce2-127">ICorDebugRemoteTarget (Interface)</span><span class="sxs-lookup"><span data-stu-id="d9ce2-127">ICorDebugRemoteTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)  
 [<span data-ttu-id="d9ce2-128">ICorDebug (Interface)</span><span class="sxs-lookup"><span data-stu-id="d9ce2-128">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
