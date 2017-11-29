---
title: "ICorDebugFunction2::EnumerateNativeCode, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugFunction2.EnumerateNativeCode
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugFunction2::EnumerateNativeCode
helpviewer_keywords:
- ICorDebugFunction2::EnumerateNativeCode method [.NET Framework debugging]
- EnumerateNativeCode method [.NET Framework debugging]
ms.assetid: d383f5cc-1144-4b6d-b57a-db34d9134ab2
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2553c8d5e2d2e5b27f56487250c5d3f54c2786d9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugfunction2enumeratenativecode-method"></a><span data-ttu-id="dacc8-102">ICorDebugFunction2::EnumerateNativeCode, méthode</span><span class="sxs-lookup"><span data-stu-id="dacc8-102">ICorDebugFunction2::EnumerateNativeCode Method</span></span>
<span data-ttu-id="dacc8-103">Obtient un pointeur d’interface vers un objet ICorDebugCodeEnum qui contient les instructions de code natif dans la fonction référencée par cet objet ICorDebugFunction2.</span><span class="sxs-lookup"><span data-stu-id="dacc8-103">Gets an interface pointer to an ICorDebugCodeEnum object that contains the native code statements in the function referenced by this ICorDebugFunction2 object.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dacc8-104">`EnumerateNativeCode`n’est pas implémentée dans la version actuelle du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="dacc8-104">`EnumerateNativeCode` is not implemented in the current version of the .NET Framework.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dacc8-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dacc8-105">Syntax</span></span>  
  
```  
HRESULT EnumerateNativeCode (  
    [out] ICorDebugCodeEnum   **ppCodeEnum  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="dacc8-106">Spécifications</span><span class="sxs-lookup"><span data-stu-id="dacc8-106">Requirements</span></span>  
 <span data-ttu-id="dacc8-107">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dacc8-107">**Header:** CorDebug.idl, CorDebug.h</span></span>
