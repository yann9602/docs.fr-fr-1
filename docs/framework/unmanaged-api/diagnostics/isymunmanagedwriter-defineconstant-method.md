---
title: "ISymUnmanagedWriter::DefineConstant, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.DefineConstant
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::DefineConstant
helpviewer_keywords:
- DefineConstant method [.NET Framework debugging]
- ISymUnmanagedWriter::DefineConstant method [.NET Framework debugging]
ms.assetid: 9e986986-2223-4d5f-b040-85d716146924
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9b22b0d9c9de27ba9950a0501193bc682586bfbc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwriterdefineconstant-method"></a><span data-ttu-id="8c08b-102">ISymUnmanagedWriter::DefineConstant, méthode</span><span class="sxs-lookup"><span data-stu-id="8c08b-102">ISymUnmanagedWriter::DefineConstant Method</span></span>
<span data-ttu-id="8c08b-103">Définit un nom pour une valeur constante.</span><span class="sxs-lookup"><span data-stu-id="8c08b-103">Defines a name for a constant value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c08b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8c08b-104">Syntax</span></span>  
  
```  
HRESULT DefineConstant(  
    [in] const WCHAR *name,  
    [in] VARIANT value,  
    [in] ULONG32 cSig,  
    [in, size_is(cSig)] unsigned char signature[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8c08b-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="8c08b-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="8c08b-106">[in] Un pointeur vers un `WCHAR` qui définit le nom de la constante.</span><span class="sxs-lookup"><span data-stu-id="8c08b-106">[in] A pointer to a `WCHAR` that defines the constant name.</span></span>  
  
 `value`  
 <span data-ttu-id="8c08b-107">[in] La valeur de la constante.</span><span class="sxs-lookup"><span data-stu-id="8c08b-107">[in] The value of the constant.</span></span>  
  
 `cSig`  
 <span data-ttu-id="8c08b-108">[in] Taille du tableau `signature`.</span><span class="sxs-lookup"><span data-stu-id="8c08b-108">[in] The size of the `signature` array.</span></span>  
  
 `signature`  
 <span data-ttu-id="8c08b-109">[in] La signature de type pour la constante.</span><span class="sxs-lookup"><span data-stu-id="8c08b-109">[in] The type signature for the constant.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8c08b-110">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="8c08b-110">Return Value</span></span>  
 <span data-ttu-id="8c08b-111">S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="8c08b-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8c08b-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="8c08b-112">Requirements</span></span>  
 <span data-ttu-id="8c08b-113">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="8c08b-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c08b-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8c08b-114">See Also</span></span>  
 [<span data-ttu-id="8c08b-115">ISymUnmanagedWriter, interface</span><span class="sxs-lookup"><span data-stu-id="8c08b-115">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 [<span data-ttu-id="8c08b-116">DefineConstant2, méthode</span><span class="sxs-lookup"><span data-stu-id="8c08b-116">DefineConstant2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-defineconstant2-method.md)
