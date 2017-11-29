---
title: "ICorDebugExceptionObjectValue::EnumerateExceptionCallStack, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugExceptionObjectValue.EnumerateExceptionCallStack
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugExceptionObjectValue::EnumerateExceptionCallStack
helpviewer_keywords:
- EnumerateExceptionCallStack method, ICorDebugExceptionObjectValue interface [.NET Framework debugging]
- ICorDebugExceptionObjectValue::EnumerateExceptionCallStack method [.NET Framework debugging]
ms.assetid: 00c64533-15dd-47f4-bb97-fe80a1ebadef
topic_type: apiref
caps.latest.revision: "3"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 861d2ad5f9ce0fcc11ea7b1743cd369235cbd878
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugexceptionobjectvalueenumerateexceptioncallstack-method"></a><span data-ttu-id="24546-102">ICorDebugExceptionObjectValue::EnumerateExceptionCallStack, méthode</span><span class="sxs-lookup"><span data-stu-id="24546-102">ICorDebugExceptionObjectValue::EnumerateExceptionCallStack Method</span></span>
<span data-ttu-id="24546-103">Obtient un énumérateur pour la pile des appels incorporée dans un objet d’exception.</span><span class="sxs-lookup"><span data-stu-id="24546-103">Gets an enumerator to the call stack embedded in an exception object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24546-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="24546-104">Syntax</span></span>  
  
```  
HRESULT EnumerateExceptionCallStack(  
    [out] ICorDebugExceptionObjectCallStackEnum **ppCallStackEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="24546-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="24546-105">Parameters</span></span>  
 <span data-ttu-id="24546-106">ppCallStackEnum</span><span class="sxs-lookup"><span data-stu-id="24546-106">ppCallStackEnum</span></span>  
 <span data-ttu-id="24546-107">[out] Un pointeur vers l’adresse d’un [ICorDebugExceptionObjectCallStackEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md) objet d’interface qui est un énumérateur de trace de pile pour un objet exception managée.</span><span class="sxs-lookup"><span data-stu-id="24546-107">[out] A pointer to the address of an [ICorDebugExceptionObjectCallStackEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md) interface object that is a stack trace enumerator for a managed exception object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="24546-108">Remarques</span><span class="sxs-lookup"><span data-stu-id="24546-108">Remarks</span></span>  
 <span data-ttu-id="24546-109">Si aucune information de la pile des appels n’est disponible, la méthode retourne `S_OK`, et [ICorDebugExceptionObjectCallStackEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md) est un énumérateur valide avec une longueur de 0.</span><span class="sxs-lookup"><span data-stu-id="24546-109">If no call stack information is available, the method returns `S_OK`, and [ICorDebugExceptionObjectCallStackEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md) is a valid enumerator with a length of 0.</span></span> <span data-ttu-id="24546-110">Si la méthode ne peut pas récupérer les informations de trace de pile, la valeur de retour est `E_FAIL` et aucun énumérateur n’est retournée.</span><span class="sxs-lookup"><span data-stu-id="24546-110">If the method is unable to retrieve stack trace information, the return value is `E_FAIL` and no enumerator is returned.</span></span>  
  
 <span data-ttu-id="24546-111">Le [ICorDebugExceptionObjectCallStackEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md) objet est chargé pour le décodage des données de trace de pile le `_stackTrace` champ de l’objet exception.</span><span class="sxs-lookup"><span data-stu-id="24546-111">The [ICorDebugExceptionObjectCallStackEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md) object is responsible for decoding the stack trace data from the `_stackTrace` field of the exception object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="24546-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="24546-112">Requirements</span></span>  
 <span data-ttu-id="24546-113">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="24546-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="24546-114">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="24546-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="24546-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="24546-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="24546-116">**Versions du .NET framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="24546-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24546-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="24546-117">See Also</span></span>  
 [<span data-ttu-id="24546-118">ICorDebugExceptionObjectValue (Interface)</span><span class="sxs-lookup"><span data-stu-id="24546-118">ICorDebugExceptionObjectValue Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectvalue-interface.md)  
 [<span data-ttu-id="24546-119">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="24546-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
