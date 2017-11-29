---
title: "ICorDebugArrayValue::GetElementAtPosition, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugArrayValue.GetElementAtPosition
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugArrayValue::GetElementAtPosition
helpviewer_keywords:
- GetElementAtPosition method [.NET Framework debugging]
- ICorDebugArrayValue::GetElementAtPosition method [.NET Framework debugging]
ms.assetid: 6fd5eaa4-1997-4910-82f5-3887480db764
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 20af0afa395dd69dc8967aa9f39a8bf99eacf530
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugarrayvaluegetelementatposition-method"></a><span data-ttu-id="9ef9e-102">ICorDebugArrayValue::GetElementAtPosition, méthode</span><span class="sxs-lookup"><span data-stu-id="9ef9e-102">ICorDebugArrayValue::GetElementAtPosition Method</span></span>
<span data-ttu-id="9ef9e-103">Obtient l’élément à la position donnée, en traitant le tableau comme un tableau unidimensionnel de base zéro.</span><span class="sxs-lookup"><span data-stu-id="9ef9e-103">Gets the element at the given position, treating the array as a zero-based, single-dimensional array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ef9e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9ef9e-104">Syntax</span></span>  
  
```  
HRESULT GetElementAtPosition (  
    [in]  ULONG32          nPosition,  
    [out] ICorDebugValue   **ppValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9ef9e-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9ef9e-105">Parameters</span></span>  
 `nPosition`  
 <span data-ttu-id="9ef9e-106">[in] La position de l’élément à récupérer.</span><span class="sxs-lookup"><span data-stu-id="9ef9e-106">[in] The position of the element to be retrieved.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="9ef9e-107">[out] Pointeur vers l’adresse d’un objet ICorDebugValue qui représente la valeur de l’élément.</span><span class="sxs-lookup"><span data-stu-id="9ef9e-107">[out] A pointer to the address of an ICorDebugValue object that represents the value of the element.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9ef9e-108">Remarques</span><span class="sxs-lookup"><span data-stu-id="9ef9e-108">Remarks</span></span>  
 <span data-ttu-id="9ef9e-109">La disposition d’un tableau multidimensionnel suit le style C++ de disposition de tableau.</span><span class="sxs-lookup"><span data-stu-id="9ef9e-109">The layout of a multi-dimension array follows the C++ style of array layout.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9ef9e-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="9ef9e-110">Requirements</span></span>  
 <span data-ttu-id="9ef9e-111">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9ef9e-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ef9e-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9ef9e-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9ef9e-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9ef9e-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9ef9e-114">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9ef9e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
