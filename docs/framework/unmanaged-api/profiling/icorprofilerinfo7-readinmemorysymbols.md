---
title: ICorProfilerInfo7::ReadInMemorySymbols
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
api_name: ICorProfilerInfo7.ReadInMemorySymbols
api_location:
- CorProf.idl
- CorProf.h
- CorGuids.lib
api_type: COM
ms.assetid: 1745a0b9-8332-4777-a670-b549bff3b901
caps.latest.revision: "3"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9ada9f629c3a3c3d8b7c32ebc180c4788b6f6d3f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilerinfo7readinmemorysymbols"></a><span data-ttu-id="a63ed-102">ICorProfilerInfo7::ReadInMemorySymbols</span><span class="sxs-lookup"><span data-stu-id="a63ed-102">ICorProfilerInfo7::ReadInMemorySymbols</span></span>
<span data-ttu-id="a63ed-103">[Prise en charge dans [!INCLUDE[net_v461](../../../../includes/net-v461-md.md)] et versions ultérieures]</span><span class="sxs-lookup"><span data-stu-id="a63ed-103">[Supported in the [!INCLUDE[net_v461](../../../../includes/net-v461-md.md)] and later versions]</span></span>  
  
 <span data-ttu-id="a63ed-104">Lit les octets à partir d’un flux de symbole de mémoire.</span><span class="sxs-lookup"><span data-stu-id="a63ed-104">Reads bytes from an in-memory symbol stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a63ed-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a63ed-105">Syntax</span></span>  
  
```  
HRESULT ReadInMemorySymbols(  
        [in] ModuleID moduleId,  
        [in] DWORD symbolsReadOffset,  
        [out] BYTE* pSymbolBytes,  
        [in] DWORD countSymbolBytes,  
        [out] DWORD* pCountSymbolBytesRead  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a63ed-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a63ed-106">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="a63ed-107">[in] Identificateur du module contenant le flux de données en mémoire.</span><span class="sxs-lookup"><span data-stu-id="a63ed-107">[in] The identifier of the module containing the in-memory stream.</span></span>  
  
 `symbolsReadOffset`  
 <span data-ttu-id="a63ed-108">[in] Offset dans le flux en mémoire à partir duquel commencer la lecture des octets.</span><span class="sxs-lookup"><span data-stu-id="a63ed-108">[in] The offset within the in-memory stream at which to start reading bytes.</span></span>  
  
 `pSymbolBytes`  
 <span data-ttu-id="a63ed-109">[out] Pointeur vers la mémoire tampon à laquelle les données seront copiées.</span><span class="sxs-lookup"><span data-stu-id="a63ed-109">[out] A pointer to the buffer to which the data will be copied.</span></span> <span data-ttu-id="a63ed-110">La mémoire tampon doit avoir `countSymbolBytes` d’espace disponible.</span><span class="sxs-lookup"><span data-stu-id="a63ed-110">The buffer should have `countSymbolBytes` of space available.</span></span>  
  
 `countSymbolBytes`  
 <span data-ttu-id="a63ed-111">[in] Le nombre d’octets à copier.</span><span class="sxs-lookup"><span data-stu-id="a63ed-111">[in] The number of bytes to copy.</span></span>  
  
 `pCountSymbolBytesRead`  
 <span data-ttu-id="a63ed-112">[out] Lorsque la méthode est retournée, contient le nombre réel d’octets lus.</span><span class="sxs-lookup"><span data-stu-id="a63ed-112">[out] When the method returns, contains the actual number of bytes read.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a63ed-113">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="a63ed-113">Return Value</span></span>  
 <span data-ttu-id="a63ed-114">`S_OK`, si un nombre d’octets qui ont été lus.</span><span class="sxs-lookup"><span data-stu-id="a63ed-114">`S_OK`, if a non-zero number of bytes were read.</span></span>  
  
 <span data-ttu-id="a63ed-115">`CORPROF_E_MODULE_IS_DYNAMIC`, si le module a été créé à l’aide de <xref:System.Reflection.Emit>.</span><span class="sxs-lookup"><span data-stu-id="a63ed-115">`CORPROF_E_MODULE_IS_DYNAMIC`, if the module was created using <xref:System.Reflection.Emit>.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a63ed-116">Remarques</span><span class="sxs-lookup"><span data-stu-id="a63ed-116">Remarks</span></span>  
 <span data-ttu-id="a63ed-117">Le `ReadInMemorySymbols` méthode tente de lire `countSymbolBytes` de données, en commençant au décalage `symbolsReadOffset` dans le flux en mémoire.</span><span class="sxs-lookup"><span data-stu-id="a63ed-117">The `ReadInMemorySymbols` method attempts to read `countSymbolBytes` of data starting at offset      `symbolsReadOffset` within the in-memory stream.</span></span> <span data-ttu-id="a63ed-118">Les données sont copiées à `pSymbolBytes`, qui est censé avoir `countSymbolBytes` d’espace disponible.</span><span class="sxs-lookup"><span data-stu-id="a63ed-118">The data is copied to `pSymbolBytes`, which is expected to have `countSymbolBytes` of space available.</span></span>     <span data-ttu-id="a63ed-119">`pCountSymbolsBytesRead`contient le nombre réel d’octets lus, ce qui peut être inférieure à `countSymbolBytes` si la fin du flux est atteinte.</span><span class="sxs-lookup"><span data-stu-id="a63ed-119">`pCountSymbolsBytesRead` contains the actual number of bytes read, which may be less than `countSymbolBytes` if the end of the stream is reached.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a63ed-120">L’implémentation actuelle ne prend pas en charge Reflection.Emit.</span><span class="sxs-lookup"><span data-stu-id="a63ed-120">The current implementation does not support Reflection.Emit.</span></span> <span data-ttu-id="a63ed-121">Si le module a été créé à l’aide de Reflection.Emit, la méthode retourne `CORPROF_E_MODULE_IS_DYNAMIC`.</span><span class="sxs-lookup"><span data-stu-id="a63ed-121">If the module was created by using Reflection.Emit, the method returns `CORPROF_E_MODULE_IS_DYNAMIC`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a63ed-122">Spécifications</span><span class="sxs-lookup"><span data-stu-id="a63ed-122">Requirements</span></span>  
 <span data-ttu-id="a63ed-123">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a63ed-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a63ed-124">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a63ed-124">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a63ed-125">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a63ed-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a63ed-126">**Versions du .NET Framework :** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a63ed-126">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a63ed-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a63ed-127">See Also</span></span>  
 [<span data-ttu-id="a63ed-128">Interface de ICorProfilerInfo7</span><span class="sxs-lookup"><span data-stu-id="a63ed-128">ICorProfilerInfo7 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)
