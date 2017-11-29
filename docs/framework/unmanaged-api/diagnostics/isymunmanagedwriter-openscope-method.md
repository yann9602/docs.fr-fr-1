---
title: "ISymUnmanagedWriter::OpenScope, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.OpenScope
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::OpenScope
helpviewer_keywords:
- OpenScope method, ISymUnmanagedWriter interface [.NET Framework debugging]
- ISymUnmanagedWriter::OpenScope method [.NET Framework debugging]
ms.assetid: dbea0644-3873-4329-90b8-624163e87467
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: f56bc14b096b5086db1fc8d046ed699559381fb0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedwriteropenscope-method"></a><span data-ttu-id="a9d47-102">ISymUnmanagedWriter::OpenScope, méthode</span><span class="sxs-lookup"><span data-stu-id="a9d47-102">ISymUnmanagedWriter::OpenScope Method</span></span>
<span data-ttu-id="a9d47-103">Ouvre une nouvelle portée lexicale dans la méthode actuelle.</span><span class="sxs-lookup"><span data-stu-id="a9d47-103">Opens a new lexical scope in the current method.</span></span> <span data-ttu-id="a9d47-104">La portée devient la nouvelle portée actuelle et est placée sur une pile d’étendues.</span><span class="sxs-lookup"><span data-stu-id="a9d47-104">The scope becomes the new current scope and is pushed onto a stack of scopes.</span></span> <span data-ttu-id="a9d47-105">Les portées doivent former une hiérarchie.</span><span class="sxs-lookup"><span data-stu-id="a9d47-105">Scopes must form a hierarchy.</span></span> <span data-ttu-id="a9d47-106">Frères ne sont pas autorisées à chevaucher.</span><span class="sxs-lookup"><span data-stu-id="a9d47-106">Siblings are not allowed to overlap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9d47-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a9d47-107">Syntax</span></span>  
  
```  
HRESULT OpenScope(  
    [in] ULONG32 startOffset,  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a9d47-108">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a9d47-108">Parameters</span></span>  
 `startOffset`  
 <span data-ttu-id="a9d47-109">[in] Le décalage de la première instruction dans la portée lexicale, en octets, à partir du début de la méthode.</span><span class="sxs-lookup"><span data-stu-id="a9d47-109">[in] The offset of the first instruction in the lexical scope, in bytes, from the beginning of the method.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="a9d47-110">[out] Un pointeur vers un `ULONG32` qui reçoit l’identificateur de portée.</span><span class="sxs-lookup"><span data-stu-id="a9d47-110">[out] A pointer to a `ULONG32` that receives the scope identifier.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a9d47-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="a9d47-111">Return Value</span></span>  
 <span data-ttu-id="a9d47-112">S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="a9d47-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a9d47-113">Remarques</span><span class="sxs-lookup"><span data-stu-id="a9d47-113">Remarks</span></span>  
 <span data-ttu-id="a9d47-114">`ISymUnmanagedWriter::OpenScope`Retourne un identificateur de portée opaque qui peut être utilisé avec [ISymUnmanagedWriter::SetScopeRange](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setscoperange-method.md) pour définir une étendue de début et de fin décalage ultérieurement.</span><span class="sxs-lookup"><span data-stu-id="a9d47-114">`ISymUnmanagedWriter::OpenScope` returns an opaque scope identifier that can be used with [ISymUnmanagedWriter::SetScopeRange](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setscoperange-method.md) to define a scope's starting and ending offset at a later time.</span></span> <span data-ttu-id="a9d47-115">Dans ce cas, les offsets passés à `ISymUnmanagedWriter::OpenScope` et [ISymUnmanagedWriter::CloseScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closescope-method.md) sont ignorés.</span><span class="sxs-lookup"><span data-stu-id="a9d47-115">In this case, the offsets passed to `ISymUnmanagedWriter::OpenScope` and [ISymUnmanagedWriter::CloseScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closescope-method.md) are ignored.</span></span> <span data-ttu-id="a9d47-116">Les identificateurs de portée sont valides uniquement dans la méthode actuelle.</span><span class="sxs-lookup"><span data-stu-id="a9d47-116">Scope identifiers are valid only in the current method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a9d47-117">Spécifications</span><span class="sxs-lookup"><span data-stu-id="a9d47-117">Requirements</span></span>  
 <span data-ttu-id="a9d47-118">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="a9d47-118">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9d47-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a9d47-119">See Also</span></span>  
 [<span data-ttu-id="a9d47-120">ISymUnmanagedWriter (Interface)</span><span class="sxs-lookup"><span data-stu-id="a9d47-120">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
