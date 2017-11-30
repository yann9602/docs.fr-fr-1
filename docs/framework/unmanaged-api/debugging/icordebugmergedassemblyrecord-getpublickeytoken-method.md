---
title: "ICorDebugMergedAssemblyRecord::GetPublicKeyToken, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 72020b72-9611-4bc3-b1e7-5a16b023bfa3
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4c286981def6f12f8e5b8fa5397f23535d4d4623
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmergedassemblyrecordgetpublickeytoken-method"></a><span data-ttu-id="8382e-102">ICorDebugMergedAssemblyRecord::GetPublicKeyToken, méthode</span><span class="sxs-lookup"><span data-stu-id="8382e-102">ICorDebugMergedAssemblyRecord::GetPublicKeyToken Method</span></span>
<span data-ttu-id="8382e-103">Obtient le jeton de clé publique de l'assembly.</span><span class="sxs-lookup"><span data-stu-id="8382e-103">Gets the assembly's public key token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8382e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8382e-104">Syntax</span></span>  
  
```  
HRESULT GetPublicKeyToken(  
   [in] ULONG32 cbPublicKeyToken,   
   [out] ULONG32 *pcbPublicKeyToken,   
   [out, size_is(cbPublicKeyToken), length_is(*pcbPublicKeyToken)] BYTE pbPublicKeyToken[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8382e-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="8382e-105">Parameters</span></span>  
 `cbPublicKeyToken`  
 <span data-ttu-id="8382e-106">[in] Nombre maximal d'octets dans le tableau `pbPublicKeyToken`.</span><span class="sxs-lookup"><span data-stu-id="8382e-106">[in] The maximum number of bytes in the `pbPublicKeyToken` array.</span></span>  
  
 `pcbPublicKeyToken`  
 <span data-ttu-id="8382e-107">[out] Pointeur vers le nombre réel d'octets écrits dans le tableau `pbPublicKeyToken`.</span><span class="sxs-lookup"><span data-stu-id="8382e-107">[out] A pointer to the actual number of bytes written to the `pbPublicKeyToken` array.</span></span>  
  
 `pbPublicKeyToken`  
 <span data-ttu-id="8382e-108">[in] Pointeur vers un tableau d'octets contenant le jeton de clé publique de l'assembly.</span><span class="sxs-lookup"><span data-stu-id="8382e-108">[out] A pointer to a byte array that contains the assembly's public key token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8382e-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="8382e-109">Remarks</span></span>  
 <span data-ttu-id="8382e-110">Le jeton de clé publique d'un assembly se compose des huit derniers octets d'un hachage SHA1 de sa clé publique.</span><span class="sxs-lookup"><span data-stu-id="8382e-110">An assembly's public key token is the last eight bytes of a SHA1 hash of its public key.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8382e-111">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="8382e-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8382e-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="8382e-112">Requirements</span></span>  
 <span data-ttu-id="8382e-113">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8382e-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8382e-114">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8382e-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8382e-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8382e-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8382e-116">**Versions du .NET framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8382e-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8382e-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8382e-117">See Also</span></span>  
 [<span data-ttu-id="8382e-118">Icordebugmergedassemblyrecord, Interface</span><span class="sxs-lookup"><span data-stu-id="8382e-118">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)  
 [<span data-ttu-id="8382e-119">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="8382e-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
