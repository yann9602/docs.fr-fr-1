---
title: "ISymUnmanagedVariable::GetAddressKind, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedVariable.GetAddressKind
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedVariable::GetAddressKind
helpviewer_keywords:
- GetAddressKind method [.NET Framework debugging]
- ISymUnmanagedVariable::GetAddressKind method [.NET Framework debugging]
ms.assetid: a71563c0-62f2-4eb4-970c-825d61827613
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5c4651641e3c430379b11698acf29eae450b02b2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedvariablegetaddresskind-method"></a><span data-ttu-id="12c69-102">ISymUnmanagedVariable::GetAddressKind, méthode</span><span class="sxs-lookup"><span data-stu-id="12c69-102">ISymUnmanagedVariable::GetAddressKind Method</span></span>
<span data-ttu-id="12c69-103">Obtient le type d’adresse de cette variable.</span><span class="sxs-lookup"><span data-stu-id="12c69-103">Gets the kind of address of this variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12c69-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="12c69-104">Syntax</span></span>  
  
```  
HRESULT GetAddressKind(  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="12c69-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="12c69-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="12c69-106">[out] Un pointeur vers un `ULONG32` qui reçoit la valeur.</span><span class="sxs-lookup"><span data-stu-id="12c69-106">[out] A pointer to a `ULONG32` that receives the value.</span></span> <span data-ttu-id="12c69-107">Les valeurs possibles sont définies dans le [CorSymAddrKind](../../../../docs/framework/unmanaged-api/diagnostics/corsymaddrkind-enumeration.md) énumération.</span><span class="sxs-lookup"><span data-stu-id="12c69-107">The possible values are defined in the [CorSymAddrKind](../../../../docs/framework/unmanaged-api/diagnostics/corsymaddrkind-enumeration.md) enumeration.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="12c69-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="12c69-108">Return Value</span></span>  
 <span data-ttu-id="12c69-109">S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="12c69-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="12c69-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="12c69-110">Requirements</span></span>  
 <span data-ttu-id="12c69-111">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="12c69-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12c69-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="12c69-112">See Also</span></span>  
 [<span data-ttu-id="12c69-113">ISymUnmanagedVariable, interface</span><span class="sxs-lookup"><span data-stu-id="12c69-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
