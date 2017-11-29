---
title: "ICorDebugArrayValue::HasBaseIndicies, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugArrayValue.HasBaseIndicies
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugArrayValue::HasBaseIndicies
helpviewer_keywords:
- HasBaseIndicies method [.NET Framework debugging]
- ICorDebugArrayValue::HasBaseIndicies method [.NET Framework debugging]
ms.assetid: aa26df07-e0a6-4608-bdef-d4afafec89aa
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 256429bfed350181aa13ee2c119eb5c9541ce231
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugarrayvaluehasbaseindicies-method"></a><span data-ttu-id="095b1-102">ICorDebugArrayValue::HasBaseIndicies, méthode</span><span class="sxs-lookup"><span data-stu-id="095b1-102">ICorDebugArrayValue::HasBaseIndicies Method</span></span>
<span data-ttu-id="095b1-103">Obtient une valeur qui indique si toutes les dimensions de ce tableau ont un index de base de zéro.</span><span class="sxs-lookup"><span data-stu-id="095b1-103">Gets a value that indicates whether any dimensions of this array have a base index of non-zero.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="095b1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="095b1-104">Syntax</span></span>  
  
```  
HRESULT HasBaseIndicies (  
    [out] BOOL    *pbHasBaseIndicies  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="095b1-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="095b1-105">Parameters</span></span>  
 `pbHasBaseIndicies`  
 <span data-ttu-id="095b1-106">[out] Un pointeur vers une valeur booléenne qui est `true` si une ou plusieurs dimensions de ce `ICorDebugArrayValue` objet possède un index de base de zéro ; sinon, la valeur booléenne est `false`.</span><span class="sxs-lookup"><span data-stu-id="095b1-106">[out] A pointer to a Boolean value that is `true` if one or more dimensions of this `ICorDebugArrayValue` object have a base index of non-zero; otherwise, the Boolean value is `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="095b1-107">Spécifications</span><span class="sxs-lookup"><span data-stu-id="095b1-107">Requirements</span></span>  
 <span data-ttu-id="095b1-108">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="095b1-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="095b1-109">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="095b1-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="095b1-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="095b1-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="095b1-111">**Versions du .NET framework :**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="095b1-111">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>
