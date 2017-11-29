---
title: "ICorDebugNativeFrame::CanSetIP, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugNativeFrame.CanSetIP
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugNativeFrame::CanSetIP
helpviewer_keywords:
- ICorDebugNativeFrame::CanSetIP method [.NET Framework debugging]
- CanSetIP method, ICorDebugNativeFrame interface [.NET Framework debugging]
ms.assetid: 13258ac6-f4e4-4f66-8fc3-f1244417a3c3
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 33b5efe6352d3a0c30179990205315c76f3a704d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugnativeframecansetip-method"></a><span data-ttu-id="ed97e-102">ICorDebugNativeFrame::CanSetIP, méthode</span><span class="sxs-lookup"><span data-stu-id="ed97e-102">ICorDebugNativeFrame::CanSetIP Method</span></span>
<span data-ttu-id="ed97e-103">Obtient une valeur HRESULT qui indique s’il est possible de définir le pointeur d’instruction (IP) à l’emplacement de décalage spécifié dans le code natif.</span><span class="sxs-lookup"><span data-stu-id="ed97e-103">Gets an HRESULT that indicates whether it is safe to set the instruction pointer (IP) to the specified offset location in native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed97e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ed97e-104">Syntax</span></span>  
  
```  
HRESULT CanSetIP (  
    [in] ULONG32            nOffset  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ed97e-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ed97e-105">Parameters</span></span>  
 `nOffset`  
 <span data-ttu-id="ed97e-106">[in] Le paramètre souhaité pour le pointeur d’instruction.</span><span class="sxs-lookup"><span data-stu-id="ed97e-106">[in] The desired setting for the instruction pointer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ed97e-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="ed97e-107">Remarks</span></span>  
 <span data-ttu-id="ed97e-108">Utilisez le `CanSetIP` méthode avant d’appeler le [ICorDebugNativeFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="ed97e-108">Use the `CanSetIP` method prior to calling the [ICorDebugNativeFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md) method.</span></span> <span data-ttu-id="ed97e-109">Si `CanSetIP` retourne un HRESULT autre que S_OK, vous pouvez toujours appeler `ICorDebugNativeFrame::SetIP`, mais il n’existe aucune garantie que le débogueur continue l’exécution sécurisée et correcte du code en cours de débogage.</span><span class="sxs-lookup"><span data-stu-id="ed97e-109">If `CanSetIP` returns any HRESULT other than S_OK, you can still invoke `ICorDebugNativeFrame::SetIP`, but there is no guarantee that the debugger will continue the safe and correct execution of the code being debugged.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ed97e-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="ed97e-110">Requirements</span></span>  
 <span data-ttu-id="ed97e-111">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ed97e-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ed97e-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ed97e-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ed97e-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ed97e-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ed97e-114">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ed97e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed97e-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ed97e-115">See Also</span></span>  
 
