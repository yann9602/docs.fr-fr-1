---
title: "ICorDebugType::GetStaticFieldValue, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugType.GetStaticFieldValue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugType::GetStaticFieldValue
helpviewer_keywords:
- GetStaticFieldValue method, ICorDebugType interface [.NET Framework debugging]
- ICorDebugType::GetStaticFieldValue method [.NET Framework debugging]
ms.assetid: 62eb5d55-53ee-4fb3-8d47-7b6c96808f9e
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 34a37ef9a28dd0e6325db9bee61146f14d4638a6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugtypegetstaticfieldvalue-method"></a><span data-ttu-id="baeaf-102">ICorDebugType::GetStaticFieldValue, méthode</span><span class="sxs-lookup"><span data-stu-id="baeaf-102">ICorDebugType::GetStaticFieldValue Method</span></span>
<span data-ttu-id="baeaf-103">Obtient un pointeur d’interface vers un objet ICorDebugValue qui contient la valeur du champ statique référencé par le champ spécifié de jeton dans le frame de pile spécifié.</span><span class="sxs-lookup"><span data-stu-id="baeaf-103">Gets an interface pointer to an ICorDebugValue object that contains the value of the static field referenced by the specified field token in the specified stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="baeaf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="baeaf-104">Syntax</span></span>  
  
```  
HRESULT GetStaticFieldValue (  
    [in]  mdFieldDef        fieldDef,  
    [in]  ICorDebugFrame    *pFrame,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="baeaf-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="baeaf-105">Parameters</span></span>  
 `fieldDef`  
 <span data-ttu-id="baeaf-106">[in] Un `mdFieldDef` jeton qui spécifie le champ statique.</span><span class="sxs-lookup"><span data-stu-id="baeaf-106">[in] An `mdFieldDef` token that specifies the static field.</span></span>  
  
 `pFrame`  
 <span data-ttu-id="baeaf-107">[in] Pointeur vers un ICorDebugFrame qui représente le frame de pile.</span><span class="sxs-lookup"><span data-stu-id="baeaf-107">[in] A pointer to an ICorDebugFrame that represents the stack frame.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="baeaf-108">[out] Un pointeur vers l’adresse d’un `ICorDebugValue` qui contient la valeur du champ statique.</span><span class="sxs-lookup"><span data-stu-id="baeaf-108">[out] A pointer to the address of an `ICorDebugValue` that contains the value of the static field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="baeaf-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="baeaf-109">Remarks</span></span>  
 <span data-ttu-id="baeaf-110">Le `GetStaticFieldValue` méthode peut être utilisée uniquement si le type est ELEMENT_TYPE_CLASS ou ELEMENT_TYPE_VALUETYPE, comme indiqué par le [ICorDebugType::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="baeaf-110">The `GetStaticFieldValue` method may be used only if the type is ELEMENT_TYPE_CLASS or ELEMENT_TYPE_VALUETYPE, as indicated by the [ICorDebugType::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md) method.</span></span>  
  
 <span data-ttu-id="baeaf-111">Pour les types non génériques, l’opération effectuée par `GetStaticFieldValue` est identique à l’appel [ICorDebugClass::GetStaticFieldValue](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-getstaticfieldvalue-method.md) sur l’objet ICorDebugClass qui est retourné par [ICorDebugType::GetClass](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getclass-method.md).</span><span class="sxs-lookup"><span data-stu-id="baeaf-111">For non-generic types, the operation performed by `GetStaticFieldValue` is identical to calling [ICorDebugClass::GetStaticFieldValue](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-getstaticfieldvalue-method.md) on the ICorDebugClass object that is returned by [ICorDebugType::GetClass](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getclass-method.md).</span></span>  
  
 <span data-ttu-id="baeaf-112">Pour les types génériques, une valeur de champ statique sera par rapport à une instanciation particulière.</span><span class="sxs-lookup"><span data-stu-id="baeaf-112">For generic types, a static field value will be relative to a particular instantiation.</span></span> <span data-ttu-id="baeaf-113">En outre, si le champ statique peut être relatif à un thread, un contexte ou un domaine d’application, puis le frame de pile pour déterminer le débogueur la valeur appropriée.</span><span class="sxs-lookup"><span data-stu-id="baeaf-113">Also, if the static field could possibly be relative to a thread, a context, or an application domain, then the stack frame will help the debugger determine the proper value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="baeaf-114">Remarques</span><span class="sxs-lookup"><span data-stu-id="baeaf-114">Remarks</span></span>  
 <span data-ttu-id="baeaf-115">`GetStaticFieldValue`peut être utilisé uniquement lorsqu’un appel à `ICorDebugType::GetType` retourne la valeur ELEMENT_TYPE_CLASS ou un ELEMENT_TYPE_VALUETYPE.</span><span class="sxs-lookup"><span data-stu-id="baeaf-115">`GetStaticFieldValue` can be used only when a call to `ICorDebugType::GetType` returns a value of ELEMENT_TYPE_CLASS or ELEMENT_TYPE_VALUETYPE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="baeaf-116">Spécifications</span><span class="sxs-lookup"><span data-stu-id="baeaf-116">Requirements</span></span>  
 <span data-ttu-id="baeaf-117">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="baeaf-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="baeaf-118">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="baeaf-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="baeaf-119">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="baeaf-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="baeaf-120">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="baeaf-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
