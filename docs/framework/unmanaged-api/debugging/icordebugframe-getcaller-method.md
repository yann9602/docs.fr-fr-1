---
title: "ICorDebugFrame::GetCaller, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugFrame.GetCaller
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugFrame::GetCaller
helpviewer_keywords:
- GetCaller method, ICorDebugFrame interface [.NET Framework debugging]
- ICorDebugFrame::GetCaller method [.NET Framework debugging]
ms.assetid: bfdc946b-8238-4eb9-8a85-884049fb0fd4
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e0f426823b0076a8d6bee1b39a7cdcdf618dad90
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugframegetcaller-method"></a><span data-ttu-id="cda79-102">ICorDebugFrame::GetCaller, méthode</span><span class="sxs-lookup"><span data-stu-id="cda79-102">ICorDebugFrame::GetCaller Method</span></span>
<span data-ttu-id="cda79-103">Obtient un pointeur vers l’objet ICorDebugFrame dans la chaîne actuelle qui a appelé ce frame.</span><span class="sxs-lookup"><span data-stu-id="cda79-103">Gets a pointer to the ICorDebugFrame object in the current chain that called this frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cda79-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cda79-104">Syntax</span></span>  
  
```  
HRESULT GetCaller (  
    [out] ICorDebugFrame     **ppFrame  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cda79-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="cda79-105">Parameters</span></span>  
 `ppFrame`  
 <span data-ttu-id="cda79-106">[out] Un pointeur vers l’adresse d’un `ICorDebugFrame` objet qui représente le frame appelant.</span><span class="sxs-lookup"><span data-stu-id="cda79-106">[out] A pointer to the address of an `ICorDebugFrame` object that represents the calling frame.</span></span> <span data-ttu-id="cda79-107">Cette valeur est null si le frame appelé correspond au frame extérieur dans la chaîne actuelle.</span><span class="sxs-lookup"><span data-stu-id="cda79-107">This value is null if the called frame is the outermost frame in the current chain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cda79-108">Spécifications</span><span class="sxs-lookup"><span data-stu-id="cda79-108">Requirements</span></span>  
 <span data-ttu-id="cda79-109">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cda79-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cda79-110">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cda79-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cda79-111">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cda79-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cda79-112">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cda79-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
