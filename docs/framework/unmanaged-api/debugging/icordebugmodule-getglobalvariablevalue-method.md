---
title: "ICorDebugModule::GetGlobalVariableValue, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugModule.GetGlobalVariableValue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugModule::GetGlobalVariableValue
helpviewer_keywords:
- ICorDebugModule::GetGlobalVariableValue method [.NET Framework debugging]
- GetGlobalVariableValue method [.NET Framework debugging]
ms.assetid: bbc0881c-6a59-41a0-b5ee-2f3d1b71684c
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 00fb56353652e2fdeac7d7b42c030d9105cc9aca
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugmodulegetglobalvariablevalue-method"></a><span data-ttu-id="9b056-102">ICorDebugModule::GetGlobalVariableValue, méthode</span><span class="sxs-lookup"><span data-stu-id="9b056-102">ICorDebugModule::GetGlobalVariableValue Method</span></span>
<span data-ttu-id="9b056-103">Obtient la valeur de la variable globale spécifiée.</span><span class="sxs-lookup"><span data-stu-id="9b056-103">Gets the value of the specified global variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b056-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9b056-104">Syntax</span></span>  
  
```  
HRESULT GetGlobalVariableValue(  
    [in]  mdFieldDef      fieldDef,  
    [out] ICorDebugValue  **ppValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9b056-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9b056-105">Parameters</span></span>  
 `fieldDef`  
 <span data-ttu-id="9b056-106">[in] Un `mdFieldDef` jeton qui référence les métadonnées décrivant la variable globale.</span><span class="sxs-lookup"><span data-stu-id="9b056-106">[in] An `mdFieldDef` token that references the metadata describing the global variable.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="9b056-107">[out] Pointeur vers l’adresse d’un objet ICorDebugValue qui représente la valeur de la variable globale spécifiée.</span><span class="sxs-lookup"><span data-stu-id="9b056-107">[out] A pointer to the address of an ICorDebugValue object that represents the value of the specified global variable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9b056-108">Spécifications</span><span class="sxs-lookup"><span data-stu-id="9b056-108">Requirements</span></span>  
 <span data-ttu-id="9b056-109">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9b056-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9b056-110">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9b056-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9b056-111">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9b056-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9b056-112">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9b056-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
