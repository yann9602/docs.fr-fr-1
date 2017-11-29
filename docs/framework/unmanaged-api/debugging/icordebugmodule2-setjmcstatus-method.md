---
title: "ICorDebugModule2::SetJMCStatus, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugModule2.SetJMCStatus
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugModule2::SetJMCStatus
helpviewer_keywords:
- SetJMCStatus method, ICorDebugModule2 interface [.NET Framework debugging]
- ICorDebugModule2::SetJMCStatus method [.NET Framework debugging]
ms.assetid: 8c6d2089-4dbb-4715-b9e9-2a4491c8c9ce
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ca4b53acc69d0a56b94526de0c3b16fd1abde077
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugmodule2setjmcstatus-method"></a><span data-ttu-id="267c5-102">ICorDebugModule2::SetJMCStatus, méthode</span><span class="sxs-lookup"><span data-stu-id="267c5-102">ICorDebugModule2::SetJMCStatus Method</span></span>
<span data-ttu-id="267c5-103">Définit l’état d’uniquement mon Code (JMC) de toutes les méthodes de toutes les classes dans ce ICorDebugModule2 à la valeur spécifiée, à l’exception de celles figurant dans le `pTokens` tableau, il définit la valeur opposée.</span><span class="sxs-lookup"><span data-stu-id="267c5-103">Sets the Just My Code (JMC) status of all methods of all the classes in this ICorDebugModule2 to the specified value, except those in the `pTokens` array, which it sets to the opposite value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="267c5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="267c5-104">Syntax</span></span>  
  
```  
HRESULT SetJMCStatus (  
    [in] BOOL                        bIsJustMyCode,  
    [in] ULONG32                     cTokens,  
    [in, size_is(cTokens)] mdToken   pTokens[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="267c5-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="267c5-105">Parameters</span></span>  
 `bIsJustMycode`  
 <span data-ttu-id="267c5-106">[in] La valeur `true` si le code doit être débogué ; sinon, la valeur `false`.</span><span class="sxs-lookup"><span data-stu-id="267c5-106">[in] Set to `true` if the code is to be debugged; otherwise, set to `false`.</span></span>  
  
 `cTokens`  
 <span data-ttu-id="267c5-107">[in] Taille du tableau `pTokens`.</span><span class="sxs-lookup"><span data-stu-id="267c5-107">[in] The size of the `pTokens` array.</span></span>  
  
 `pTokens`  
 <span data-ttu-id="267c5-108">[in] Un tableau de `mdToken` valeurs, chacune d’elles fait référence à une méthode qui aura son statut JMC !`bIsJustMycode`.</span><span class="sxs-lookup"><span data-stu-id="267c5-108">[in] An array of `mdToken` values, each of which refers to a method that will have its JMC status set to !`bIsJustMycode`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="267c5-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="267c5-109">Remarks</span></span>  
 <span data-ttu-id="267c5-110">L’état JMC de chaque méthode qui est spécifiée dans le `pTokens` tableau est défini à l’opposé de le `bIsJustMycode` valeur.</span><span class="sxs-lookup"><span data-stu-id="267c5-110">The JMC status of each method that is specified in the `pTokens` array is set to the opposite of the `bIsJustMycode` value.</span></span> <span data-ttu-id="267c5-111">L’état de toutes les autres méthodes dans ce module est défini sur la `bIsJustMycode` valeur.</span><span class="sxs-lookup"><span data-stu-id="267c5-111">The status of all other methods in this module is set to the `bIsJustMycode` value.</span></span>  
  
 <span data-ttu-id="267c5-112">Le `SetJMCStatus` méthode efface tous les paramètres JMC précédents dans ce module.</span><span class="sxs-lookup"><span data-stu-id="267c5-112">The `SetJMCStatus` method erases all previous JMC settings in this module.</span></span>  
  
 <span data-ttu-id="267c5-113">Le `SetJMCStatus` méthode retourne un HRESULT S_OK si toutes les fonctions ont été définies correctement.</span><span class="sxs-lookup"><span data-stu-id="267c5-113">The `SetJMCStatus` method returns an S_OK HRESULT if all functions were set successfully.</span></span> <span data-ttu-id="267c5-114">Il retourne un HRESULT CORDBG_E_FUNCTION_NOT_DEBUGGABLE si certaines fonctions qui sont marqués `true` ne sont pas débogable.</span><span class="sxs-lookup"><span data-stu-id="267c5-114">It returns a CORDBG_E_FUNCTION_NOT_DEBUGGABLE HRESULT if some functions that are marked `true` are not debuggable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="267c5-115">Spécifications</span><span class="sxs-lookup"><span data-stu-id="267c5-115">Requirements</span></span>  
 <span data-ttu-id="267c5-116">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="267c5-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="267c5-117">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="267c5-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="267c5-118">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="267c5-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="267c5-119">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="267c5-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
