---
title: "ISymUnmanagedConstant::GetSignature, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedConstant.GetSignature
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedConstant::GetSignature
helpviewer_keywords:
- GetSignature method, ISymUnmanagedConstant interface [.NET Framework debugging]
- ISymUnmanagedConstant::GetSignature method [.NET Framework debugging]
ms.assetid: 3eb41151-a228-43e3-ba8f-e6dd3ceb8542
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 314d9115fdba7d57538e5b24c56863944db517fe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedconstantgetsignature-method"></a><span data-ttu-id="c1332-102">ISymUnmanagedConstant::GetSignature, méthode</span><span class="sxs-lookup"><span data-stu-id="c1332-102">ISymUnmanagedConstant::GetSignature Method</span></span>
<span data-ttu-id="c1332-103">Obtient la signature de la constante.</span><span class="sxs-lookup"><span data-stu-id="c1332-103">Gets the signature of the constant.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1332-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c1332-104">Syntax</span></span>  
  
```  
HRESULT GetSignature(  
    [in]  ULONG32  cSig,  
    [out] ULONG32  *pcSig,  
    [out, size_is(cSig),  
        length_is(*pcSig)] BYTE sig[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c1332-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c1332-105">Parameters</span></span>  
 `cSig`  
 <span data-ttu-id="c1332-106">[in] La longueur de la mémoire tampon qui le `pcSig` paramètre pointe vers.</span><span class="sxs-lookup"><span data-stu-id="c1332-106">[in] The length of the buffer that the `pcSig` parameter points to.</span></span>  
  
 `pcSig`  
 <span data-ttu-id="c1332-107">[out] Un pointeur vers un `ULONG32` qui reçoit la taille, en caractères, de la mémoire tampon requise pour contenir la signature.</span><span class="sxs-lookup"><span data-stu-id="c1332-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the signature.</span></span>  
  
 `sig`  
 <span data-ttu-id="c1332-108">[out] Mémoire tampon qui stocke la signature.</span><span class="sxs-lookup"><span data-stu-id="c1332-108">[out] The buffer that stores the signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c1332-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="c1332-109">Return Value</span></span>  
 <span data-ttu-id="c1332-110">S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="c1332-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c1332-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="c1332-111">Requirements</span></span>  
 <span data-ttu-id="c1332-112">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="c1332-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1332-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c1332-113">See Also</span></span>  
 [<span data-ttu-id="c1332-114">ISymUnmanagedConstant (Interface)</span><span class="sxs-lookup"><span data-stu-id="c1332-114">ISymUnmanagedConstant Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-interface.md)  
 [<span data-ttu-id="c1332-115">GetName (méthode)</span><span class="sxs-lookup"><span data-stu-id="c1332-115">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-getname-method.md)  
 [<span data-ttu-id="c1332-116">GetValue (méthode)</span><span class="sxs-lookup"><span data-stu-id="c1332-116">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-getvalue-method.md)
