---
title: "ICorDebugType::GetBase, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugType.GetBase
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugType::GetBase
helpviewer_keywords:
- ICorDebugType::GetBase method [.NET Framework debugging]
- GetBase method [.NET Framework debugging]
ms.assetid: f24e1af9-c220-4f79-ae62-4153ec17ea81
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c28c88988155cf5e00897858d4306e4cb2ea78a3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugtypegetbase-method"></a><span data-ttu-id="37b4b-102">ICorDebugType::GetBase, méthode</span><span class="sxs-lookup"><span data-stu-id="37b4b-102">ICorDebugType::GetBase Method</span></span>
<span data-ttu-id="37b4b-103">Obtient un pointeur d’interface vers ICorDebugType qui représente le type de base, s’il en existe, du type représenté par ce `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="37b4b-103">Gets an interface pointer to an ICorDebugType that represents the base type, if one exists, of the type represented by this `ICorDebugType`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37b4b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="37b4b-104">Syntax</span></span>  
  
```  
HRESULT GetBase (  
    [out] ICorDebugType   **pBase  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="37b4b-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="37b4b-105">Parameters</span></span>  
 `pBase`  
 <span data-ttu-id="37b4b-106">[out] Un pointeur vers l’adresse d’un `ICorDebugType` objet qui représente le type de base.</span><span class="sxs-lookup"><span data-stu-id="37b4b-106">[out] A pointer to the address of an `ICorDebugType` object that represents the base type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="37b4b-107">Notes</span><span class="sxs-lookup"><span data-stu-id="37b4b-107">Remarks</span></span>  
 <span data-ttu-id="37b4b-108">Recherche le type de base pour un type est utile pour implémenter des fonctionnalités communes du débogueur, telles que l’impression de tous les champs d’un objet ou ses classes parent.</span><span class="sxs-lookup"><span data-stu-id="37b4b-108">Looking up the base type for a type is useful to implement common debugger functionality, such as printing out all the fields of an object or its parent classes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="37b4b-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="37b4b-109">Requirements</span></span>  
 <span data-ttu-id="37b4b-110">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="37b4b-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="37b4b-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="37b4b-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="37b4b-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="37b4b-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="37b4b-113">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="37b4b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
