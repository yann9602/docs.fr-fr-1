---
title: "ICorDebugInternalFrame::GetFrameType, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugInternalFrame.GetFrameType
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugInternalFrame::GetFrameType
helpviewer_keywords:
- GetFrameType method [.NET Framework debugging]
- ICorDebugInternalFrame::GetFrameType method [.NET Framework debugging]
ms.assetid: da278a29-dc2e-4bf7-96ce-801bdc4d7025
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d9d3dd087662c938b2f733458d1e92cff577e9f7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebuginternalframegetframetype-method"></a><span data-ttu-id="89232-102">ICorDebugInternalFrame::GetFrameType, méthode</span><span class="sxs-lookup"><span data-stu-id="89232-102">ICorDebugInternalFrame::GetFrameType Method</span></span>
<span data-ttu-id="89232-103">Obtient le type de ce frame interne.</span><span class="sxs-lookup"><span data-stu-id="89232-103">Gets the type of this internal frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89232-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="89232-104">Syntax</span></span>  
  
```  
HRESULT GetFrameType (  
    [out] CorDebugInternalFrameType  *pType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="89232-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="89232-105">Parameters</span></span>  
 `pType`  
 <span data-ttu-id="89232-106">[out] Un pointeur vers une valeur de l’énumération CorDebugInternalFrameType qui indique le type de frame interne représenté par cet `ICorDebugInternalFrame` objet.</span><span class="sxs-lookup"><span data-stu-id="89232-106">[out] A pointer to a value of the CorDebugInternalFrameType enumeration that indicates the type of internal frame represented by this `ICorDebugInternalFrame` object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="89232-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="89232-107">Remarks</span></span>  
 <span data-ttu-id="89232-108">Le type de frame interne ne sera jamais STUBFRAME_NONE.</span><span class="sxs-lookup"><span data-stu-id="89232-108">The internal frame type will never be STUBFRAME_NONE.</span></span> <span data-ttu-id="89232-109">Débogueurs en douceur doivent ignorer les types de frame interne non reconnu.</span><span class="sxs-lookup"><span data-stu-id="89232-109">Debuggers should gracefully ignore unrecognized internal frame types.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="89232-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="89232-110">Requirements</span></span>  
 <span data-ttu-id="89232-111">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="89232-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="89232-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="89232-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="89232-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="89232-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="89232-114">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="89232-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
