---
title: "ICorProfilerInfo::GetAppDomainInfo, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.GetAppDomainInfo
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::GetAppDomainInfo
helpviewer_keywords:
- ICorProfilerInfo::GetAppDomainInfo method [.NET Framework profiling]
- GetAppDomainInfo method [.NET Framework profiling]
ms.assetid: a6bf5a04-e03e-44f0-917a-96f6a6d3cc96
topic_type: apiref
caps.latest.revision: "23"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c31d3c61a868bf741213f6e505d91524cc925207
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfogetappdomaininfo-method"></a><span data-ttu-id="9a169-102">ICorProfilerInfo::GetAppDomainInfo, méthode</span><span class="sxs-lookup"><span data-stu-id="9a169-102">ICorProfilerInfo::GetAppDomainInfo Method</span></span>
<span data-ttu-id="9a169-103">Accepte un ID de domaine d'application</span><span class="sxs-lookup"><span data-stu-id="9a169-103">Accepts an application domain ID.</span></span> <span data-ttu-id="9a169-104">Retourne un nom de domaine d'application et l'ID du processus qui le contient.</span><span class="sxs-lookup"><span data-stu-id="9a169-104">Returns an application domain name and the ID of the process that contains it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a169-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9a169-105">Syntax</span></span>  
  
```  
HRESULT GetAppDomainInfo(  
    [in]  AppDomainID appDomainId,  
    [in]  ULONG       cchName,  
    [out] ULONG       *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
          WCHAR       szName[] ,  
    [out] ProcessID   *pProcessId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9a169-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9a169-106">Parameters</span></span>  
 `appDomainId`  
 <span data-ttu-id="9a169-107">[in] ID du domaine d'application.</span><span class="sxs-lookup"><span data-stu-id="9a169-107">[in] The ID of the application domain.</span></span>  
  
 `cchName`  
 <span data-ttu-id="9a169-108">[in] Longueur, en caractères, de la mémoire tampon de retour `szName`.</span><span class="sxs-lookup"><span data-stu-id="9a169-108">[in] The length, in characters, of the `szName` return buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="9a169-109">[out] Pointeur vers la longueur totale en caractères du nom de domaine d'application.</span><span class="sxs-lookup"><span data-stu-id="9a169-109">[out] A pointer to the total character length of the application domain name.</span></span>  
  
 `szName`  
 <span data-ttu-id="9a169-110">[out] Mémoire tampon de caractères larges fournie par l'appelant.</span><span class="sxs-lookup"><span data-stu-id="9a169-110">[out] A caller-provided wide character buffer.</span></span> <span data-ttu-id="9a169-111">Suite au retour de la méthode, `szName` contient le nom de domaine d'application complet ou partiel.</span><span class="sxs-lookup"><span data-stu-id="9a169-111">When the method returns, `szName` will contain the full or partial application domain name.</span></span>  
  
 `pProcessId`  
 <span data-ttu-id="9a169-112">[out] Pointeur vers l'ID du processus qui contient le domaine d'application.</span><span class="sxs-lookup"><span data-stu-id="9a169-112">[out] A pointer to the ID of the process that contains the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9a169-113">Remarques</span><span class="sxs-lookup"><span data-stu-id="9a169-113">Remarks</span></span>  
 <span data-ttu-id="9a169-114">Suite au retour de cette méthode, vous devez vérifier que la mémoire tampon `szName` est suffisamment grande pour contenir le nom complet du domaine d'application.</span><span class="sxs-lookup"><span data-stu-id="9a169-114">After this method returns, you must verify that the `szName` buffer was large enough to contain the full name of the application domain.</span></span> <span data-ttu-id="9a169-115">Pour ce faire, comparez la valeur vers laquelle `pcchName` pointe à celle du paramètre `cchName`.</span><span class="sxs-lookup"><span data-stu-id="9a169-115">To do this, compare the value that `pcchName` points to with the value of the `cchName` parameter.</span></span> <span data-ttu-id="9a169-116">Si `pcchName` pointe vers une valeur supérieure à `cchName`, allouez une mémoire tampon `szName` plus grande, mettez à jour `cchName` pour refléter la nouvelle taille et rappelez `GetAppDomainInfo`.</span><span class="sxs-lookup"><span data-stu-id="9a169-116">If `pcchName` points to a value that is larger than `cchName`, allocate a larger `szName` buffer, update `cchName` with the new, larger size, and call `GetAppDomainInfo` again.</span></span>  
  
 <span data-ttu-id="9a169-117">Vous pouvez également commencer par appeler `GetAppDomainInfo` avec une mémoire tampon `szName` de longueur nulle pour obtenir la taille correcte de la mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="9a169-117">Alternatively, you can first call `GetAppDomainInfo` with a zero-length `szName` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="9a169-118">Vous pouvez ensuite affecter à la taille de la mémoire tampon la valeur retournée dans `pcchName` et rappeler `GetAppDomainInfo`.</span><span class="sxs-lookup"><span data-stu-id="9a169-118">You can then set the buffer size to the value returned in `pcchName` and call `GetAppDomainInfo` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9a169-119">Spécifications</span><span class="sxs-lookup"><span data-stu-id="9a169-119">Requirements</span></span>  
 <span data-ttu-id="9a169-120">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9a169-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9a169-121">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9a169-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9a169-122">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9a169-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9a169-123">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9a169-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a169-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9a169-124">See Also</span></span>  
 [<span data-ttu-id="9a169-125">ICorProfilerInfo (Interface)</span><span class="sxs-lookup"><span data-stu-id="9a169-125">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="9a169-126">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="9a169-126">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="9a169-127">Profilage</span><span class="sxs-lookup"><span data-stu-id="9a169-127">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
