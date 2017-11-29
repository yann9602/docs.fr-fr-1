---
title: "ICorDebugAppDomain::GetObject, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugAppDomain.GetObject
api_location: corguids.lib
api_type: COM
f1_keywords: ICorDebugAppDomain::GetObject
helpviewer_keywords:
- ICorDebugAppDomain::GetObject method [.NET Framework debugging]
- GetObject method, ICorDebugAppDomain interface [.NET Framework debugging]
ms.assetid: 78232e6f-ae18-4cfa-a6cd-e79471cf9d76
topic_type: apiref
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c4f923d8e9bf9762d5208dd6e9be527a50a688b1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugappdomaingetobject-method"></a><span data-ttu-id="48fc2-102">ICorDebugAppDomain::GetObject, méthode</span><span class="sxs-lookup"><span data-stu-id="48fc2-102">ICorDebugAppDomain::GetObject Method</span></span>
<span data-ttu-id="48fc2-103">Obtient un pointeur d’interface vers le domaine d’application du common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="48fc2-103">Gets an interface pointer to the common language runtime (CLR) application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48fc2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="48fc2-104">Syntax</span></span>  
  
```  
HRESULT GetObject (  
    [out] ICorDebugValue   **ppObject  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="48fc2-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="48fc2-105">Parameters</span></span>  
 `ppObject`  
 <span data-ttu-id="48fc2-106">[out] Pointeur vers l’adresse d’un objet d’interface ICorDebugValue qui représente le domaine d’application CLR.</span><span class="sxs-lookup"><span data-stu-id="48fc2-106">[out] A pointer to the address of an ICorDebugValue interface object that represents the CLR application domain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="48fc2-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="48fc2-107">Return Value</span></span>  
 <span data-ttu-id="48fc2-108">Si managé <xref:System.AppDomain?displayProperty=nameWithType> objet n’a pas été construit pour ce domaine d’application, la méthode retourne `S_FALSE` et place `NULL` dans `*ppObject`.</span><span class="sxs-lookup"><span data-stu-id="48fc2-108">If a managed <xref:System.AppDomain?displayProperty=nameWithType> object hasn't been constructed for this application domain, the method returns `S_FALSE` and places `NULL` in `*ppObject`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="48fc2-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="48fc2-109">Remarks</span></span>  
 <span data-ttu-id="48fc2-110">Chaque domaine d’application dans un processus peut avoir managé <xref:System.AppDomain?displayProperty=nameWithType> objet dans le runtime qui le représente.</span><span class="sxs-lookup"><span data-stu-id="48fc2-110">Each application domain in a process may have a managed <xref:System.AppDomain?displayProperty=nameWithType> object in the runtime that represents it.</span></span> <span data-ttu-id="48fc2-111">Cette fonction obtient un objet d’interface ICorDebugValue qui correspond à cet gérés <xref:System.AppDomain?displayProperty=nameWithType> objet.</span><span class="sxs-lookup"><span data-stu-id="48fc2-111">This function gets an ICorDebugValue interface object that corresponds to this managed <xref:System.AppDomain?displayProperty=nameWithType> object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="48fc2-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="48fc2-112">Requirements</span></span>  
 <span data-ttu-id="48fc2-113">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="48fc2-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="48fc2-114">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="48fc2-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="48fc2-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="48fc2-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="48fc2-116">**Versions du .NET framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="48fc2-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>
