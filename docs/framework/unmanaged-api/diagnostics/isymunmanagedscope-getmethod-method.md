---
title: "ISymUnmanagedScope::GetMethod, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedScope.GetMethod
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedScope::GetMethod
helpviewer_keywords:
- GetMethod method, ISymUnmanagedScope interface [.NET Framework debugging]
- ISymUnmanagedScope::GetMethod method [.NET Framework debugging]
ms.assetid: a61866ee-221a-45b9-a1b7-395825b77872
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: bb062ad7ab485a1631a9cbe15f904b21226cb502
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedscopegetmethod-method"></a><span data-ttu-id="62737-102">ISymUnmanagedScope::GetMethod, méthode</span><span class="sxs-lookup"><span data-stu-id="62737-102">ISymUnmanagedScope::GetMethod Method</span></span>
<span data-ttu-id="62737-103">Obtient la méthode qui contient cette portée.</span><span class="sxs-lookup"><span data-stu-id="62737-103">Gets the method that contains this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62737-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="62737-104">Syntax</span></span>  
  
```  
HRESULT GetMethod(  
    [out, retval] ISymUnmanagedMethod** pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="62737-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="62737-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="62737-106">[out] Un pointeur vers retourné [ISymUnmanagedMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="62737-106">[out] A pointer to the returned [ISymUnmanagedMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="62737-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="62737-107">Return Value</span></span>  
 <span data-ttu-id="62737-108">S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="62737-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="62737-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="62737-109">Requirements</span></span>  
 <span data-ttu-id="62737-110">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="62737-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62737-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="62737-111">See Also</span></span>  
 [<span data-ttu-id="62737-112">ISymUnmanagedScope (Interface)</span><span class="sxs-lookup"><span data-stu-id="62737-112">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)
