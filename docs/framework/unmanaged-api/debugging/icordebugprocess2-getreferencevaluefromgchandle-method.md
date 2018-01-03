---
title: "ICorDebugProcess2::GetReferenceValueFromGCHandle, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess2.GetReferenceValueFromGCHandle
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess2::GetReferenceValueFromGCHandle
helpviewer_keywords:
- GetReferenceValueFromGCHandle method [.NET Framework debugging]
- ICorDebugProcess2::GetReferenceValueFromGCHandle method [.NET Framework debugging]
ms.assetid: 8bdd7f4c-19f2-4ede-875e-603773e8c128
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0ac4cc32be6914ea858d32b8699a695588f0a1e0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocess2getreferencevaluefromgchandle-method"></a><span data-ttu-id="c3a79-102">ICorDebugProcess2::GetReferenceValueFromGCHandle, méthode</span><span class="sxs-lookup"><span data-stu-id="c3a79-102">ICorDebugProcess2::GetReferenceValueFromGCHandle Method</span></span>
<span data-ttu-id="c3a79-103">Obtient un pointeur de référence à l’objet managé spécifié qui a un garbage collection à gérer.</span><span class="sxs-lookup"><span data-stu-id="c3a79-103">Gets a reference pointer to the specified managed object that has a garbage collection handle.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3a79-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c3a79-104">Syntax</span></span>  
  
```  
HRESULT GetReferenceValueFromGCHandle (  
    [in]  UINT_PTR                 handle,  
    [out] ICorDebugReferenceValue  **pOutValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c3a79-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c3a79-105">Parameters</span></span>  
 `handle`  
 <span data-ttu-id="c3a79-106">[in] Pointeur vers un objet managé qui a un handle de garbage collection.</span><span class="sxs-lookup"><span data-stu-id="c3a79-106">[in] A pointer to a managed object that has a garbage collection handle.</span></span> <span data-ttu-id="c3a79-107">Cette valeur est un <xref:System.IntPtr> de l’objet et peuvent être récupérés à partir de la <xref:System.Runtime.InteropServices.GCHandle> pour l’objet managé.</span><span class="sxs-lookup"><span data-stu-id="c3a79-107">This value is a <xref:System.IntPtr> object and can be retrieved from the <xref:System.Runtime.InteropServices.GCHandle> for the managed object.</span></span>  
  
 `pOutValue`  
 <span data-ttu-id="c3a79-108">[out] Pointeur vers l’adresse d’un objet ICorDebugReferenceValue qui représente une référence à l’objet managé spécifié.</span><span class="sxs-lookup"><span data-stu-id="c3a79-108">[out] A pointer to the address of an ICorDebugReferenceValue object that represents a reference to the specified managed object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c3a79-109">Notes</span><span class="sxs-lookup"><span data-stu-id="c3a79-109">Remarks</span></span>  
 <span data-ttu-id="c3a79-110">Ne confondez pas la valeur de référence retournée avec une valeur de référence de garbage collection.</span><span class="sxs-lookup"><span data-stu-id="c3a79-110">Do not confuse the returned reference value with a garbage collection reference value.</span></span>  
  
 <span data-ttu-id="c3a79-111">La référence retournée se comporte comme une référence normale.</span><span class="sxs-lookup"><span data-stu-id="c3a79-111">The returned reference behaves like a normal reference.</span></span> <span data-ttu-id="c3a79-112">Il est désactivé lors de l’exécution de code se poursuit après un point d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="c3a79-112">It is disabled when code execution continues after a breakpoint.</span></span> <span data-ttu-id="c3a79-113">La durée de vie de l’objet cible n’est pas affectée par la durée de vie de la valeur de référence.</span><span class="sxs-lookup"><span data-stu-id="c3a79-113">The lifetime of the target object is not affected by the lifetime of the reference value.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c3a79-114">Le `GetReferenceValueFromGCHandle` méthode ne valide pas le handle.</span><span class="sxs-lookup"><span data-stu-id="c3a79-114">The `GetReferenceValueFromGCHandle` method does not validate the handle.</span></span> <span data-ttu-id="c3a79-115">Par conséquent, le `GetReferenceValueFromGCHandle` méthode peut potentiellement endommager le débogueur et le code en cours de débogage si un handle non valide est passé.</span><span class="sxs-lookup"><span data-stu-id="c3a79-115">Therefore, the `GetReferenceValueFromGCHandle` method can potentially corrupt both the debugger and the code being debugged if an invalid handle is passed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c3a79-116">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="c3a79-116">Requirements</span></span>  
 <span data-ttu-id="c3a79-117">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c3a79-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c3a79-118">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c3a79-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c3a79-119">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c3a79-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c3a79-120">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c3a79-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
