---
title: "ISymUnmanagedWriter::SetScopeRange, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.SetScopeRange
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::SetScopeRange
helpviewer_keywords:
- SetScopeRange method [.NET Framework debugging]
- ISymUnmanagedWriter::SetScopeRange method [.NET Framework debugging]
ms.assetid: d4d98676-444b-46ca-bfe6-0d827385cd22
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9afb0038adc4273033fb9f1db1ebc57f43eae779
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwritersetscoperange-method"></a><span data-ttu-id="bca44-102">ISymUnmanagedWriter::SetScopeRange, méthode</span><span class="sxs-lookup"><span data-stu-id="bca44-102">ISymUnmanagedWriter::SetScopeRange Method</span></span>
<span data-ttu-id="bca44-103">Définit la plage d'offsets pour la portée lexicale spécifiée.</span><span class="sxs-lookup"><span data-stu-id="bca44-103">Defines the offset range for the specified lexical scope.</span></span> <span data-ttu-id="bca44-104">La portée devient la nouvelle portée actuelle et est placée sur une pile d’étendues.</span><span class="sxs-lookup"><span data-stu-id="bca44-104">The scope becomes the new current scope and is pushed onto a stack of scopes.</span></span> <span data-ttu-id="bca44-105">Les portées doivent former une hiérarchie.</span><span class="sxs-lookup"><span data-stu-id="bca44-105">Scopes must form a hierarchy.</span></span> <span data-ttu-id="bca44-106">Frères ne sont pas autorisées à chevaucher.</span><span class="sxs-lookup"><span data-stu-id="bca44-106">Siblings are not allowed to overlap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bca44-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bca44-107">Syntax</span></span>  
  
```  
HRESULT OpenScope(  
    [in] ULONG32  scopeID,  
    [in] ULONG32  startOffset,  
    [in] ULONG32  endOffset);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bca44-108">Paramètres</span><span class="sxs-lookup"><span data-stu-id="bca44-108">Parameters</span></span>  
 `scopeId`  
 <span data-ttu-id="bca44-109">[in] Identificateur de l’étendue dans l’étendue.</span><span class="sxs-lookup"><span data-stu-id="bca44-109">[in] The scope identifier for the scope.</span></span>  
  
 `startOffset`  
 <span data-ttu-id="bca44-110">[in] Offset, en octets, de la première instruction dans la portée lexicale à partir du début de la méthode.</span><span class="sxs-lookup"><span data-stu-id="bca44-110">[in] The offset, in bytes, of the first instruction in the lexical scope from the beginning of the method.</span></span>  
  
 `endOffset`  
 <span data-ttu-id="bca44-111">[in] Offset, en octets, de la dernière instruction dans la portée lexicale à partir du début de la méthode.</span><span class="sxs-lookup"><span data-stu-id="bca44-111">[in] The offset, in bytes, of the last instruction in the lexical scope from the beginning of the method.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bca44-112">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="bca44-112">Return Value</span></span>  
 <span data-ttu-id="bca44-113">S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="bca44-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bca44-114">Notes</span><span class="sxs-lookup"><span data-stu-id="bca44-114">Remarks</span></span>  
 <span data-ttu-id="bca44-115">[ISymUnmanagedWriter::OpenScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openscope-method.md) retourne un identificateur de portée opaque qui peut être utilisé avec `ISymUnmanagedWriter::SetScopeRange` pour définir une étendue de début et de fin décalage ultérieurement.</span><span class="sxs-lookup"><span data-stu-id="bca44-115">[ISymUnmanagedWriter::OpenScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openscope-method.md) returns an opaque scope identifier that can be used with `ISymUnmanagedWriter::SetScopeRange` to define a scope's starting and ending offset at a later time.</span></span> <span data-ttu-id="bca44-116">Dans ce cas, les offsets passés à `ISymUnmanagedWriter::OpenScope` et [ISymUnmanagedWriter::CloseScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closescope-method.md) sont ignorés.</span><span class="sxs-lookup"><span data-stu-id="bca44-116">In this case, the offsets passed to `ISymUnmanagedWriter::OpenScope` and [ISymUnmanagedWriter::CloseScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closescope-method.md) are ignored.</span></span> <span data-ttu-id="bca44-117">Les identificateurs de portée sont valides uniquement dans la méthode actuelle.</span><span class="sxs-lookup"><span data-stu-id="bca44-117">Scope identifiers are only valid in the current method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bca44-118">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="bca44-118">Requirements</span></span>  
 <span data-ttu-id="bca44-119">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="bca44-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bca44-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bca44-120">See Also</span></span>  
 [<span data-ttu-id="bca44-121">ISymUnmanagedWriter, interface</span><span class="sxs-lookup"><span data-stu-id="bca44-121">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
