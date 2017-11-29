---
title: "Méthode ICorDebugSymbolProvider2::GetFrameProps"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: f07b73f3-188d-43a9-8f7d-44dce2f1ddb7
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3892b8da3286132709792513f055d6ce75bd3fce
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugsymbolprovider2getframeprops-method"></a><span data-ttu-id="2fbee-102">Méthode ICorDebugSymbolProvider2::GetFrameProps</span><span class="sxs-lookup"><span data-stu-id="2fbee-102">ICorDebugSymbolProvider2::GetFrameProps Method</span></span>
<span data-ttu-id="2fbee-103">Retourne l'adresse virtuelle relative de départ d'une méthode et le frame parent en fonction d'une adresse virtuelle relative de code.</span><span class="sxs-lookup"><span data-stu-id="2fbee-103">Returns the method starting relative virtual address of a method and the parent frame given a code relative virtual address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2fbee-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2fbee-104">Syntax</span></span>  
  
```  
HRESULT GetFrameProps(  
   [in] ULONG32 codeRva,  
   [out] ULONG32 *pCodeStartRva,  
   [out] ULONG32 *pParentFrameStartRva  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2fbee-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2fbee-105">Parameters</span></span>  
 `codeRva`  
 <span data-ttu-id="2fbee-106">[in] Adresse virtuelle relative du code.</span><span class="sxs-lookup"><span data-stu-id="2fbee-106">[in] A code relative virtual address.</span></span>  
  
 `pCodeStartRva`  
 <span data-ttu-id="2fbee-107">[out] Pointeur vers l'adresse virtuelle relative de départ de la méthode.</span><span class="sxs-lookup"><span data-stu-id="2fbee-107">[out] A pointer to the method's starting relative virtual address.</span></span>  
  
 `pParentFrameStartRva`  
 <span data-ttu-id="2fbee-108">[out] Pointeur vers l'adresse virtuelle relative de départ du frame.</span><span class="sxs-lookup"><span data-stu-id="2fbee-108">[out] A pointer to the frame's starting relative virtual address.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2fbee-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="2fbee-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2fbee-110">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="2fbee-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2fbee-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="2fbee-111">Requirements</span></span>  
 <span data-ttu-id="2fbee-112">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2fbee-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2fbee-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2fbee-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2fbee-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2fbee-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2fbee-115">**Versions du .NET framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2fbee-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2fbee-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2fbee-116">See Also</span></span>  
 [<span data-ttu-id="2fbee-117">Icordebugsymbolprovider2, Interface</span><span class="sxs-lookup"><span data-stu-id="2fbee-117">ICorDebugSymbolProvider2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-interface.md)  
 [<span data-ttu-id="2fbee-118">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="2fbee-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
