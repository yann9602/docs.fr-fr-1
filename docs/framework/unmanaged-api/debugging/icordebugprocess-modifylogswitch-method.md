---
title: "ICorDebugProcess::ModifyLogSwitch, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess.ModifyLogSwitch
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess::ModifyLogSwitch
helpviewer_keywords:
- ICorDebugProcess::ModifyLogSwitch method [.NET Framework debugging]
- ModifyLogSwitch method [.NET Framework debugging]
ms.assetid: 5fd30875-555e-4e96-877b-5dd266cde7c4
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1458514f304b1373655c52c1460808a402a04641
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugprocessmodifylogswitch-method"></a><span data-ttu-id="408ef-102">ICorDebugProcess::ModifyLogSwitch, méthode</span><span class="sxs-lookup"><span data-stu-id="408ef-102">ICorDebugProcess::ModifyLogSwitch Method</span></span>
<span data-ttu-id="408ef-103">Définit le niveau de gravité du commutateur de journal spécifié.</span><span class="sxs-lookup"><span data-stu-id="408ef-103">Sets the severity level of the specified log switch.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="408ef-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="408ef-104">Syntax</span></span>  
  
```  
HRESULT ModifyLogSwitch(  
    [in] WCHAR *pLogSwitchName,  
    [in] LONG  lLevel);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="408ef-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="408ef-105">Parameters</span></span>  
 `pLogSwitchName`  
 <span data-ttu-id="408ef-106">[in] Un pointeur vers une chaîne qui spécifie le nom du commutateur de journal.</span><span class="sxs-lookup"><span data-stu-id="408ef-106">[in] A pointer to a string that specifies the name of the log switch.</span></span>  
  
 `lLevel`  
 <span data-ttu-id="408ef-107">[in] Le niveau de gravité à définir pour le commutateur de journal spécifié.</span><span class="sxs-lookup"><span data-stu-id="408ef-107">[in] The severity level to be set for the specified log switch.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="408ef-108">Remarques</span><span class="sxs-lookup"><span data-stu-id="408ef-108">Remarks</span></span>  
 <span data-ttu-id="408ef-109">Cette méthode est valide uniquement après que le [ICorDebugManagedCallback::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) rappel s’est produite.</span><span class="sxs-lookup"><span data-stu-id="408ef-109">This method is valid only after the [ICorDebugManagedCallback::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) callback has occurred.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="408ef-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="408ef-110">Requirements</span></span>  
 <span data-ttu-id="408ef-111">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="408ef-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="408ef-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="408ef-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="408ef-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="408ef-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="408ef-114">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="408ef-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
