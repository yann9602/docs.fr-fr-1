---
title: "ICorDebugEval2::NewStringWithLength, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugEval2.NewStringWithLength
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugEval2::NewStringWithLength
helpviewer_keywords:
- NewStringWithLength method [.NET Framework debugging]
- ICorDebugEval2::NewStringWithLength method [.NET Framework debugging]
ms.assetid: d5f54a34-6335-4708-b407-a756ec70fab4
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b794482e491dc9825b0311cf1731d159082bd1f1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugeval2newstringwithlength-method"></a><span data-ttu-id="371ed-102">ICorDebugEval2::NewStringWithLength, méthode</span><span class="sxs-lookup"><span data-stu-id="371ed-102">ICorDebugEval2::NewStringWithLength Method</span></span>
<span data-ttu-id="371ed-103">Crée une chaîne de la longueur spécifiée, avec le contenu spécifié.</span><span class="sxs-lookup"><span data-stu-id="371ed-103">Creates a string of the specified length, with the specified contents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="371ed-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="371ed-104">Syntax</span></span>  
  
```  
HRESULT NewStringWithLength (  
    [in] LPCWSTR               string,  
    [in] UINT                  uiLength  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="371ed-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="371ed-105">Parameters</span></span>  
 `string`  
 <span data-ttu-id="371ed-106">[in] Pointeur vers la valeur de chaîne.</span><span class="sxs-lookup"><span data-stu-id="371ed-106">[in] A pointer to the string value.</span></span>  
  
 `uiLength`  
 <span data-ttu-id="371ed-107">[in] Longueur de la chaîne.</span><span class="sxs-lookup"><span data-stu-id="371ed-107">[in] Length of the string.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="371ed-108">Remarques</span><span class="sxs-lookup"><span data-stu-id="371ed-108">Remarks</span></span>  
 <span data-ttu-id="371ed-109">Si à la fin de la chaîne de caractère null est censé être dans la chaîne managée, l’appelant de la `NewStringWithLength` méthode doit garantir que la longueur de chaîne inclut le caractère null de fin.</span><span class="sxs-lookup"><span data-stu-id="371ed-109">If the string's trailing null character is expected to be in the managed string, the caller of the `NewStringWithLength` method must ensure that the string length includes the trailing null character.</span></span>  
  
 <span data-ttu-id="371ed-110">La chaîne est toujours créée dans le domaine d’application dans lequel le thread est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="371ed-110">The string is always created in the application domain in which the thread is currently executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="371ed-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="371ed-111">Requirements</span></span>  
 <span data-ttu-id="371ed-112">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="371ed-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="371ed-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="371ed-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="371ed-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="371ed-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="371ed-115">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="371ed-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
