---
title: "ICorDebugProcess7::SetWriteableMetadataUpdateMode, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: cpp
api_name: ICorDebugProcess7.SetWriteableMetadataUpdateMode
api_location: mscordbi.dll
api_type: COM
ms.assetid: 8589bba7-7304-45ba-9e31-7bf43dfd5c19
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 635792962e259f181a1ff3e0c46438951e4223db
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugprocess7setwriteablemetadataupdatemode-method"></a><span data-ttu-id="26d7e-102">ICorDebugProcess7::SetWriteableMetadataUpdateMode, méthode</span><span class="sxs-lookup"><span data-stu-id="26d7e-102">ICorDebugProcess7::SetWriteableMetadataUpdateMode Method</span></span>
<span data-ttu-id="26d7e-103">[Pris en charge dans .NET Framework 4.5.2 et ultérieur]</span><span class="sxs-lookup"><span data-stu-id="26d7e-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="26d7e-104">Configure la façon dont le débogueur gère les mises à jour en mémoire des métadonnées dans le processus cible.</span><span class="sxs-lookup"><span data-stu-id="26d7e-104">Configures how the debugger handles in-memory updates to metadata within the target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26d7e-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="26d7e-105">Syntax</span></span>  
  
```cpp
HRESULT SetWriteableMetadataUpdateMode(  
   WriteableMetadataUpdateMode flags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="26d7e-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="26d7e-106">Parameters</span></span>  
 `flags`  
 <span data-ttu-id="26d7e-107">A [WriteableMetadataUpdateMode](../../../../docs/framework/unmanaged-api/debugging/writeablemetadataupdatemode-enumeration.md) valeur d’énumération qui spécifie si les mises à jour en mémoire des métadonnées dans le processus cible sont visibles (`WriteableMetadataUpdateMode::AlwaysShowUpdates`) ou n’est pas visible (`WriteableMetadataUpdateMode::LegacyCompatPolicy`) pour le débogueur.</span><span class="sxs-lookup"><span data-stu-id="26d7e-107">A [WriteableMetadataUpdateMode](../../../../docs/framework/unmanaged-api/debugging/writeablemetadataupdatemode-enumeration.md) enumeration value that specifies whether in-memory updates to metadata in the target process are visible (`WriteableMetadataUpdateMode::AlwaysShowUpdates`) or not visible (`WriteableMetadataUpdateMode::LegacyCompatPolicy`) to the debugger.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="26d7e-108">Remarques</span><span class="sxs-lookup"><span data-stu-id="26d7e-108">Remarks</span></span>  
 <span data-ttu-id="26d7e-109">Les mises à jour apportées aux métadonnées du processus cible peuvent provenir de Modifier et continuer, d'un profileur ou de <xref:System.Reflection.Emit?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="26d7e-109">Updates to the metadata of the target process can come from Edit and Continue, a profiler, or <xref:System.Reflection.Emit?displayProperty=nameWithType>.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="26d7e-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="26d7e-110">Requirements</span></span>  
 <span data-ttu-id="26d7e-111">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="26d7e-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="26d7e-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="26d7e-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="26d7e-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="26d7e-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="26d7e-114">**Versions du .NET framework :**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="26d7e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26d7e-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="26d7e-115">See Also</span></span>  
 [<span data-ttu-id="26d7e-116">Icordebugprocess7, Interface</span><span class="sxs-lookup"><span data-stu-id="26d7e-116">ICorDebugProcess7 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess7-interface.md)  
 [<span data-ttu-id="26d7e-117">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="26d7e-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
