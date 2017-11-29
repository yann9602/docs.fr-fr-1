---
title: ICorDebugRemoteTarget, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugRemoteTarget
api_location: CorDebug.dll
api_type: COM
f1_keywords: ICorDebugRemoteTarget
helpviewer_keywords: ICorDebugRemoteTarget interface [.NET Framework debugging]
ms.assetid: bd9936a6-cc24-4869-8761-0988664464e6
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 38357072b3a6e8e8a326a16600b2d7ed56cdcb2e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugremotetarget-interface"></a><span data-ttu-id="dd06c-102">ICorDebugRemoteTarget, interface</span><span class="sxs-lookup"><span data-stu-id="dd06c-102">ICorDebugRemoteTarget Interface</span></span>
<span data-ttu-id="dd06c-103">Fournit des méthodes qui permettent aux développeurs de déboguer les applications Silverlight dans l’environnement du common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="dd06c-103">Provides methods that enable developers to debug Silverlight-based applications in the common language runtime (CLR) environment.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd06c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dd06c-104">Syntax</span></span>  
  
```  
interface ICorDebugRemoteTarget  : IUnknown  
{  
    HRESULT GetHostName (  
        [in]  ULONG32                    cchHostName,  
        [out] ULONG32*                   pcchHostName,  
        [out, size_is(cchHostName),  
              length_is(*pcchHostName)]  
                  WCHAR szHostName[]  
        );  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="dd06c-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="dd06c-105">Methods</span></span>  
  
|<span data-ttu-id="dd06c-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="dd06c-106">Method</span></span>|<span data-ttu-id="dd06c-107">Description</span><span class="sxs-lookup"><span data-stu-id="dd06c-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="dd06c-108">ICorDebugRemoteTarget::GetHostName (méthode)</span><span class="sxs-lookup"><span data-stu-id="dd06c-108">ICorDebugRemoteTarget::GetHostName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-gethostname-method.md)|<span data-ttu-id="dd06c-109">Retourne le nom d’hôte ou l’adresse IP d’un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="dd06c-109">Returns the host name or the IP address of a remote machine.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dd06c-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="dd06c-110">Remarks</span></span>  
 <span data-ttu-id="dd06c-111">Débogage en mode mixte (code managé et natif) n’est pas pris en charge sur Windows 95, Windows 98 ou Windows Millennium Edition ou sur les plateformes non-x86 (par exemple, ia64 et AMD64).</span><span class="sxs-lookup"><span data-stu-id="dd06c-111">Mixed-mode (that is, managed and native code) debugging is not supported on Windows 95, Windows 98, or Windows ME, or on non-x86 platforms (such as IA-64 and AMD64).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dd06c-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="dd06c-112">Requirements</span></span>  
 <span data-ttu-id="dd06c-113">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dd06c-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dd06c-114">**En-tête :** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="dd06c-114">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="dd06c-115">**Bibliothèque :** : CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dd06c-115">**Library:** : CorGuids.lib</span></span>  
  
 <span data-ttu-id="dd06c-116">**Versions du .NET framework :** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="dd06c-116">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd06c-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dd06c-117">See Also</span></span>  
 [<span data-ttu-id="dd06c-118">ICorDebugRemote (Interface)</span><span class="sxs-lookup"><span data-stu-id="dd06c-118">ICorDebugRemote Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-interface.md)  
 [<span data-ttu-id="dd06c-119">ICorDebug (Interface)</span><span class="sxs-lookup"><span data-stu-id="dd06c-119">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
 [<span data-ttu-id="dd06c-120">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="dd06c-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
