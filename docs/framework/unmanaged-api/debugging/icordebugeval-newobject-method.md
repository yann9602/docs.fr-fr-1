---
title: "ICorDebugEval::NewObject, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugEval.NewObject
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugEval::NewObject
helpviewer_keywords:
- NewObject method [.NET Framework debugging]
- ICorDebugEval::NewObject method [.NET Framework debugging]
ms.assetid: ce3025e8-defa-4c5e-8298-f49d71fa5736
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 98c885e7ffd4b35bcc3af34757509910c78c0c90
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugevalnewobject-method"></a><span data-ttu-id="dbc58-102">ICorDebugEval::NewObject, méthode</span><span class="sxs-lookup"><span data-stu-id="dbc58-102">ICorDebugEval::NewObject Method</span></span>
<span data-ttu-id="dbc58-103">Alloue une nouvelle instance de l’objet et appelle la méthode du constructeur spécifié.</span><span class="sxs-lookup"><span data-stu-id="dbc58-103">Allocates a new object instance and calls the specified constructor method.</span></span>  
  
 <span data-ttu-id="dbc58-104">Cette méthode est obsolète dans le .NET Framework version 2.0.</span><span class="sxs-lookup"><span data-stu-id="dbc58-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="dbc58-105">Utilisez [ICorDebugEval2::NewParameterizedObject](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobject-method.md) à la place.</span><span class="sxs-lookup"><span data-stu-id="dbc58-105">Use [ICorDebugEval2::NewParameterizedObject](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobject-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dbc58-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dbc58-106">Syntax</span></span>  
  
```  
HRESULT NewObject (  
    [in] ICorDebugFunction  *pConstructor,  
    [in] ULONG32            nArgs,  
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dbc58-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="dbc58-107">Parameters</span></span>  
 `pConstructor`  
 <span data-ttu-id="dbc58-108">[in] Le constructeur à appeler.</span><span class="sxs-lookup"><span data-stu-id="dbc58-108">[in] The constructor to be called.</span></span>  
  
 `nArgs`  
 <span data-ttu-id="dbc58-109">[in] Taille du tableau `ppArgs`.</span><span class="sxs-lookup"><span data-stu-id="dbc58-109">[in] The size of the `ppArgs` array.</span></span>  
  
 `ppArgs`  
 <span data-ttu-id="dbc58-110">[in] Tableau d’objets ICorDebugValue, chacune représentant un argument à passer au constructeur.</span><span class="sxs-lookup"><span data-stu-id="dbc58-110">[in] An array of ICorDebugValue objects, each of which represents an argument to be passed to the constructor.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dbc58-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="dbc58-111">Requirements</span></span>  
 <span data-ttu-id="dbc58-112">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dbc58-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dbc58-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dbc58-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dbc58-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dbc58-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dbc58-115">**Versions du .NET framework :** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="dbc58-115">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dbc58-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dbc58-116">See Also</span></span>  
 [<span data-ttu-id="dbc58-117">NewParameterizedObject, méthode</span><span class="sxs-lookup"><span data-stu-id="dbc58-117">NewParameterizedObject Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobject-method.md)
