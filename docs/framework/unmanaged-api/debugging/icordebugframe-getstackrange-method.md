---
title: "ICorDebugFrame::GetStackRange, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugFrame.GetStackRange
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugFrame::GetStackRange
helpviewer_keywords:
- GetStackRange method, ICorDebugFrame interface [.NET Framework debugging]
- ICorDebugFrame::GetStackRange method [.NET Framework debugging]
ms.assetid: fab037cb-fda6-40fb-9367-921e435dd5a0
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f1db7617d52e07489ade339b76023e21816835ee
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugframegetstackrange-method"></a><span data-ttu-id="a33d3-102">ICorDebugFrame::GetStackRange, méthode</span><span class="sxs-lookup"><span data-stu-id="a33d3-102">ICorDebugFrame::GetStackRange Method</span></span>
<span data-ttu-id="a33d3-103">Obtient la plage d’adresses absolues de ce frame de pile.</span><span class="sxs-lookup"><span data-stu-id="a33d3-103">Gets the absolute address range of this stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a33d3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a33d3-104">Syntax</span></span>  
  
```  
HRESULT GetStackRange (  
    [out] CORDB_ADDRESS      *pStart,   
    [out] CORDB_ADDRESS      *pEnd  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a33d3-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a33d3-105">Parameters</span></span>  
 `pStart`  
 <span data-ttu-id="a33d3-106">[out] Un pointeur vers un `CORDB_ADDRESS` qui spécifie l’adresse de départ du frame de pile représenté par ce `ICorDebugFrame` objet.</span><span class="sxs-lookup"><span data-stu-id="a33d3-106">[out] A pointer to a `CORDB_ADDRESS` that specifies the starting address of the stack frame represented by this `ICorDebugFrame` object.</span></span>  
  
 `pEnd`  
 <span data-ttu-id="a33d3-107">[out] Un pointeur vers un `CORDB_ADDRESS` qui spécifie l’adresse de fin du frame de pile représenté par ce `ICorDebugFrame` objet.</span><span class="sxs-lookup"><span data-stu-id="a33d3-107">[out] A pointer to a `CORDB_ADDRESS` that specifies the ending address of the stack frame represented by this `ICorDebugFrame` object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a33d3-108">Remarques</span><span class="sxs-lookup"><span data-stu-id="a33d3-108">Remarks</span></span>  
 <span data-ttu-id="a33d3-109">La plage d’adresses de la pile est utile pour regrouper des traces de pile entrelacées issues de plusieurs moteurs de débogage.</span><span class="sxs-lookup"><span data-stu-id="a33d3-109">The address range of the stack is useful for piecing together interleaved stack traces gathered from multiple debugging engines.</span></span> <span data-ttu-id="a33d3-110">La plage numérique ne fournit aucune information sur le contenu du frame de pile.</span><span class="sxs-lookup"><span data-stu-id="a33d3-110">The numeric range provides no information about the contents of the stack frame.</span></span> <span data-ttu-id="a33d3-111">Il n’est significative uniquement pour la comparaison des emplacements de frame de pile.</span><span class="sxs-lookup"><span data-stu-id="a33d3-111">It is meaningful only for comparison of stack frame locations.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a33d3-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="a33d3-112">Requirements</span></span>  
 <span data-ttu-id="a33d3-113">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a33d3-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a33d3-114">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a33d3-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a33d3-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a33d3-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a33d3-116">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a33d3-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
