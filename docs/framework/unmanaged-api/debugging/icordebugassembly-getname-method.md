---
title: "ICorDebugAssembly::GetName, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugAssembly.GetName
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugAssembly::GetName
helpviewer_keywords:
- ICorDebugAssembly::GetName method [.NET Framework debugging]
- GetName method, ICorDebugAssembly interface [.NET Framework debugging]
ms.assetid: cdeda721-b214-4503-a291-c70b68b5f36b
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cf2b84a6ab7cc1745fbf7330e66f94ea04635892
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugassemblygetname-method"></a><span data-ttu-id="a73a4-102">ICorDebugAssembly::GetName, méthode</span><span class="sxs-lookup"><span data-stu-id="a73a4-102">ICorDebugAssembly::GetName Method</span></span>
<span data-ttu-id="a73a4-103">Obtient le nom de l’assembly que cela `ICorDebugAssembly` représente l’instance.</span><span class="sxs-lookup"><span data-stu-id="a73a4-103">Gets the name of the assembly that this `ICorDebugAssembly` instance represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a73a4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a73a4-104">Syntax</span></span>  
  
```  
HRESULT GetName (  
    [in] ULONG32  cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a73a4-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a73a4-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="a73a4-106">[in] Taille du tableau `szName`.</span><span class="sxs-lookup"><span data-stu-id="a73a4-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="a73a4-107">[out] Pointeur vers un entier qui spécifie la longueur réelle du nom.</span><span class="sxs-lookup"><span data-stu-id="a73a4-107">[out] A pointer to an integer that specifies the actual length of the name.</span></span>  
  
 `szName`  
 <span data-ttu-id="a73a4-108">[out] Tableau qui stocke le nom.</span><span class="sxs-lookup"><span data-stu-id="a73a4-108">[out] An array that stores the name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a73a4-109">Notes</span><span class="sxs-lookup"><span data-stu-id="a73a4-109">Remarks</span></span>  
 <span data-ttu-id="a73a4-110">Le `GetName` méthode retourne le chemin d’accès et le nom complet de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="a73a4-110">The `GetName` method returns the full path and file name of the assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a73a4-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="a73a4-111">Requirements</span></span>  
 <span data-ttu-id="a73a4-112">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a73a4-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a73a4-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a73a4-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a73a4-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a73a4-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a73a4-115">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a73a4-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
