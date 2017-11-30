---
title: "ICorDebugModule::GetClassFromToken, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugModule.GetClassFromToken
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugModule::GetClassFromToken
helpviewer_keywords:
- GetClassFromToken method, ICorDebugModule interface [.NET Framework debugging]
- ICorDebugModule::GetClassFromToken method [.NET Framework debugging]
ms.assetid: 622a4d3c-0425-4c54-a7e4-0735377cdad2
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: bd483eebc66b1274c0d28c46b3ccb1b1272f74b1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugmodulegetclassfromtoken-method"></a><span data-ttu-id="4f6d4-102">ICorDebugModule::GetClassFromToken, méthode</span><span class="sxs-lookup"><span data-stu-id="4f6d4-102">ICorDebugModule::GetClassFromToken Method</span></span>
<span data-ttu-id="4f6d4-103">Obtient la classe spécifiée par le jeton de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="4f6d4-103">Gets the class specified by the metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f6d4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4f6d4-104">Syntax</span></span>  
  
```  
HRESULT GetClassFromToken(  
    [in]  mdTypeDef        typeDef,  
    [out] ICorDebugClass **ppClass  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4f6d4-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="4f6d4-105">Parameters</span></span>  
 `typedef`  
 <span data-ttu-id="4f6d4-106">[in] Un `mdTypeDef` jeton de métadonnées qui référence les métadonnées d’une classe.</span><span class="sxs-lookup"><span data-stu-id="4f6d4-106">[in] An `mdTypeDef` metadata token that references the metadata of a class.</span></span>  
  
 `ppClass`  
 <span data-ttu-id="4f6d4-107">[out] Pointeur vers l’adresse d’un objet ICorDebugClass qui représente la classe.</span><span class="sxs-lookup"><span data-stu-id="4f6d4-107">[out] A pointer to the address of an ICorDebugClass object that represents the class.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4f6d4-108">Spécifications</span><span class="sxs-lookup"><span data-stu-id="4f6d4-108">Requirements</span></span>  
 <span data-ttu-id="4f6d4-109">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4f6d4-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4f6d4-110">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4f6d4-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4f6d4-111">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4f6d4-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4f6d4-112">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4f6d4-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
