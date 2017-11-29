---
title: "ICorDebugReferenceValue::Dereference, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugReferenceValue.Dereference
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugReferenceValue::Dereference
helpviewer_keywords:
- ICorDebugReferenceValue::Dereference method [.NET Framework debugging]
- Dereference method [.NET Framework debugging]
ms.assetid: 5ec8cf76-3deb-4ce6-9a49-77a4c35d80b9
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4eb3287612a8301d551a1443d803e60e4d03f7db
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugreferencevaluedereference-method"></a><span data-ttu-id="eb1b9-102">ICorDebugReferenceValue::Dereference, méthode</span><span class="sxs-lookup"><span data-stu-id="eb1b9-102">ICorDebugReferenceValue::Dereference Method</span></span>
<span data-ttu-id="eb1b9-103">Obtient l’objet qui est référencé.</span><span class="sxs-lookup"><span data-stu-id="eb1b9-103">Gets the object that is referenced.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb1b9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="eb1b9-104">Syntax</span></span>  
  
```  
HRESULT Dereference (  
    [out] ICorDebugValue  **ppValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="eb1b9-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="eb1b9-105">Parameters</span></span>  
 `ppValue`  
 <span data-ttu-id="eb1b9-106">[out] Pointeur vers l’adresse d’un ICorDebugValue qui représente l’objet vers lequel pointe cet objet ICorDebugReferenceValue.</span><span class="sxs-lookup"><span data-stu-id="eb1b9-106">[out] A pointer to the address of an ICorDebugValue that represents the object to which this ICorDebugReferenceValue object points.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eb1b9-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="eb1b9-107">Remarks</span></span>  
 <span data-ttu-id="eb1b9-108">Le `ICorDebugValue` objet est valide uniquement lors de sa référence n’a pas été désactivé.</span><span class="sxs-lookup"><span data-stu-id="eb1b9-108">The `ICorDebugValue` object is valid only while its reference has not yet been disabled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eb1b9-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="eb1b9-109">Requirements</span></span>  
 <span data-ttu-id="eb1b9-110">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eb1b9-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eb1b9-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="eb1b9-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="eb1b9-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="eb1b9-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eb1b9-113">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eb1b9-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
