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
ms.openlocfilehash: 930b55c98609e5f3bc33f30da766c4556fbe5512
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedvariablegetaddresskind-method"></a><span data-ttu-id="8d6d1-102">ISymUnmanagedVariable::GetAddressKind, méthode</span><span class="sxs-lookup"><span data-stu-id="8d6d1-102">ISymUnmanagedVariable::GetAddressKind Method</span></span>
<span data-ttu-id="8d6d1-103">Obtient le type d’adresse de cette variable.</span><span class="sxs-lookup"><span data-stu-id="8d6d1-103">Gets the kind of address of this variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d6d1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8d6d1-104">Syntax</span></span>  
  
```  
HRESULT GetAddressKind(  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8d6d1-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="8d6d1-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="8d6d1-106">[out] Un pointeur vers un `ULONG32` qui reçoit la valeur.</span><span class="sxs-lookup"><span data-stu-id="8d6d1-106">[out] A pointer to a `ULONG32` that receives the value.</span></span> <span data-ttu-id="8d6d1-107">Les valeurs possibles sont définies dans le [CorSymAddrKind](../../../../docs/framework/unmanaged-api/diagnostics/corsymaddrkind-enumeration.md) énumération.</span><span class="sxs-lookup"><span data-stu-id="8d6d1-107">The possible values are defined in the [CorSymAddrKind](../../../../docs/framework/unmanaged-api/diagnostics/corsymaddrkind-enumeration.md) enumeration.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8d6d1-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="8d6d1-108">Return Value</span></span>  
 <span data-ttu-id="8d6d1-109">S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="8d6d1-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8d6d1-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="8d6d1-110">Requirements</span></span>  
 <span data-ttu-id="8d6d1-111">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="8d6d1-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d6d1-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8d6d1-112">See Also</span></span>  
 [<span data-ttu-id="8d6d1-113">ISymUnmanagedVariable (Interface)</span><span class="sxs-lookup"><span data-stu-id="8d6d1-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
