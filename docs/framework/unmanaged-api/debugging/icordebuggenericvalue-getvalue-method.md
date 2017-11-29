---
title: "ICorDebugGenericValue::GetValue, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugGenericValue.GetValue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugGenericValue::GetValue
helpviewer_keywords:
- ICorDebugGenericValue::GetValue method [.NET Framework debugging]
- GetValue method, ICorDebugGenericValue interface [.NET Framework debugging]
ms.assetid: 4e95d7cb-144d-4ccf-8a69-d605f4744be2
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2432d79c6f17c7374d2beb400e93ae4088a8b1ae
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebuggenericvaluegetvalue-method"></a><span data-ttu-id="25288-102">ICorDebugGenericValue::GetValue, méthode</span><span class="sxs-lookup"><span data-stu-id="25288-102">ICorDebugGenericValue::GetValue Method</span></span>
<span data-ttu-id="25288-103">Copie la valeur de ce générique dans la mémoire tampon spécifiée.</span><span class="sxs-lookup"><span data-stu-id="25288-103">Copies the value of this generic into the specified buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25288-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="25288-104">Syntax</span></span>  
  
```  
HRESULT GetValue (  
    [out] void     *pTo  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="25288-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="25288-105">Parameters</span></span>  
 `pTo`  
 <span data-ttu-id="25288-106">[out] Pointeur vers la valeur est représentée par cet objet ICorDebugGenericValue.</span><span class="sxs-lookup"><span data-stu-id="25288-106">[out] A pointer to the value that is represented by this ICorDebugGenericValue object.</span></span> <span data-ttu-id="25288-107">La valeur peut être un type simple ou un type référence (autrement dit, un pointeur).</span><span class="sxs-lookup"><span data-stu-id="25288-107">The value may be a simple type or a reference type (that is, a pointer).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="25288-108">Spécifications</span><span class="sxs-lookup"><span data-stu-id="25288-108">Requirements</span></span>  
 <span data-ttu-id="25288-109">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="25288-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="25288-110">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="25288-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="25288-111">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="25288-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="25288-112">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="25288-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
