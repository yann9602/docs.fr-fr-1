---
title: "ICorDebugReferenceValue::GetValue, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugReferenceValue.GetValue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugReferenceValue::GetValue
helpviewer_keywords:
- GetValue method, ICorDebugReferenceValue interface [.NET Framework debugging]
- ICorDebugReferenceValue::GetValue method [.NET Framework debugging]
ms.assetid: 5da07f99-6c70-46ec-b997-5ab6fb7106cd
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: bb11810c14f383b74c565b3bd30602c22b026e62
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugreferencevaluegetvalue-method"></a><span data-ttu-id="df865-102">ICorDebugReferenceValue::GetValue, méthode</span><span class="sxs-lookup"><span data-stu-id="df865-102">ICorDebugReferenceValue::GetValue Method</span></span>
<span data-ttu-id="df865-103">Obtient l’adresse mémoire actuelle de l’objet référencé.</span><span class="sxs-lookup"><span data-stu-id="df865-103">Gets the current memory address of the referenced object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df865-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="df865-104">Syntax</span></span>  
  
```  
HRESULT GetValue (  
    [out] CORDB_ADDRESS   *pValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="df865-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="df865-105">Parameters</span></span>  
 `pValue`  
 <span data-ttu-id="df865-106">[out] Un pointeur vers un `CORDB_ADDRESS` valeur qui spécifie l’adresse de l’objet vers lequel pointe cet objet ICorDebugReferenceValue.</span><span class="sxs-lookup"><span data-stu-id="df865-106">[out] A pointer to a `CORDB_ADDRESS` value that specifies the address of the object to which this ICorDebugReferenceValue object points.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="df865-107">Spécifications</span><span class="sxs-lookup"><span data-stu-id="df865-107">Requirements</span></span>  
 <span data-ttu-id="df865-108">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="df865-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="df865-109">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="df865-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="df865-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="df865-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="df865-111">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="df865-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
