---
title: "ICorProfilerInfo2::GetStringLayout, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo2.GetStringLayout
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo2::GetStringLayout
helpviewer_keywords:
- GetStringLayout method [.NET Framework profiling]
- ICorProfilerInfo2::GetStringLayout method [.NET Framework profiling]
ms.assetid: 43189651-a535-4803-a1d1-f1c427ace2ca
topic_type: apiref
caps.latest.revision: "17"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1ad91829fab31b47a1dd51bb6cc9118c2ebe4c3a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo2getstringlayout-method"></a><span data-ttu-id="686da-102">ICorProfilerInfo2::GetStringLayout, méthode</span><span class="sxs-lookup"><span data-stu-id="686da-102">ICorProfilerInfo2::GetStringLayout Method</span></span>
<span data-ttu-id="686da-103">Obtient des informations sur la disposition d'un objet string.</span><span class="sxs-lookup"><span data-stu-id="686da-103">Gets information about the layout of a string object.</span></span> <span data-ttu-id="686da-104">Cette méthode est déconseillée dans le [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]et est remplacé par le [ICorProfilerInfo3::GetStringLayout2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getstringlayout2-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="686da-104">This method is deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)], and is superseded by the [ICorProfilerInfo3::GetStringLayout2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getstringlayout2-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="686da-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="686da-105">Syntax</span></span>  
  
```  
HRESULT GetStringLayout(  
    [out] ULONG *pBufferLengthOffset,  
    [out] ULONG *pStringLengthOffset,  
    [out] ULONG *pBufferOffset);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="686da-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="686da-106">Parameters</span></span>  
 `pBufferLengthOffset`  
 <span data-ttu-id="686da-107">[out] Un pointeur vers l’offset de l’emplacement, relatif à la `ObjectID` pointeur, qui stocke la longueur de la chaîne.</span><span class="sxs-lookup"><span data-stu-id="686da-107">[out] A pointer to the offset of the location, relative to the `ObjectID` pointer, that stores the length of the string.</span></span> <span data-ttu-id="686da-108">La longueur est stockée comme un `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="686da-108">The length is stored as a `DWORD`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="686da-109">Ce paramètre retourne la longueur de la chaîne proprement dite, mais pas la longueur de la mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="686da-109">This parameter returns the length of the string itself, not the length of the buffer.</span></span> <span data-ttu-id="686da-110">La longueur de la mémoire tampon n’est plus disponible.</span><span class="sxs-lookup"><span data-stu-id="686da-110">The length of the buffer is no longer available.</span></span>  
  
 `PStringLengthOffset`  
 <span data-ttu-id="686da-111">[out] Un pointeur vers l’offset de l’emplacement, relatif à la `ObjectID` pointeur, qui stocke la longueur de la chaîne.</span><span class="sxs-lookup"><span data-stu-id="686da-111">[out] A pointer to the offset of the location, relative to the `ObjectID` pointer, that stores the length of the string itself.</span></span> <span data-ttu-id="686da-112">La longueur est stockée comme un `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="686da-112">The length is stored as a `DWORD`.</span></span>  
  
 `pBufferOffset`  
 <span data-ttu-id="686da-113">[out] Un pointeur vers l’offset de la mémoire tampon, relative à la `ObjectID` pointeur, qui stocke la chaîne de caractères larges.</span><span class="sxs-lookup"><span data-stu-id="686da-113">[out] A pointer to the offset of the buffer, relative to the `ObjectID` pointer, that stores the string of wide characters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="686da-114">Notes</span><span class="sxs-lookup"><span data-stu-id="686da-114">Remarks</span></span>  
 <span data-ttu-id="686da-115">Le `GetStringLayout` méthode obtient les offsets, relatif à la `ObjectID` pointeur, des emplacements dans lesquels sont stockés les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="686da-115">The `GetStringLayout` method gets the offsets, relative to the `ObjectID` pointer, of the locations in which the following are stored:</span></span>  
  
-   <span data-ttu-id="686da-116">La longueur de la mémoire tampon de la chaîne.</span><span class="sxs-lookup"><span data-stu-id="686da-116">The length of the string's buffer.</span></span>  
  
-   <span data-ttu-id="686da-117">La longueur de la chaîne.</span><span class="sxs-lookup"><span data-stu-id="686da-117">The length of the string itself.</span></span>  
  
-   <span data-ttu-id="686da-118">Mémoire tampon qui contient la chaîne réelle de caractères larges.</span><span class="sxs-lookup"><span data-stu-id="686da-118">The buffer that contains the actual string of wide characters.</span></span>  
  
 <span data-ttu-id="686da-119">Les chaînes peuvent être se terminant par null.</span><span class="sxs-lookup"><span data-stu-id="686da-119">Strings may be null-terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="686da-120">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="686da-120">Requirements</span></span>  
 <span data-ttu-id="686da-121">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="686da-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="686da-122">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="686da-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="686da-123">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="686da-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="686da-124">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="686da-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="686da-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="686da-125">See Also</span></span>  
 [<span data-ttu-id="686da-126">ICorProfilerInfo, interface</span><span class="sxs-lookup"><span data-stu-id="686da-126">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="686da-127">ICorProfilerInfo2, interface</span><span class="sxs-lookup"><span data-stu-id="686da-127">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
