---
title: "ISymUnmanagedWriter::CloseScope, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.CloseScope
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::CloseScope
helpviewer_keywords:
- CloseScope method [.NET Framework debugging]
- ISymUnmanagedWriter::CloseScope method [.NET Framework debugging]
ms.assetid: 6dade525-7770-4cb4-bafd-4bb995ad0d87
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d47be1d220729ed32fcf77a77e611003085c15d6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwriterclosescope-method"></a><span data-ttu-id="e39c0-102">ISymUnmanagedWriter::CloseScope, méthode</span><span class="sxs-lookup"><span data-stu-id="e39c0-102">ISymUnmanagedWriter::CloseScope Method</span></span>
<span data-ttu-id="e39c0-103">Ferme la portée lexicale actuelle.</span><span class="sxs-lookup"><span data-stu-id="e39c0-103">Closes the current lexical scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e39c0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e39c0-104">Syntax</span></span>  
  
```  
HRESULT CloseScope(  
    [in] ULONG32 endOffset);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e39c0-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e39c0-105">Parameters</span></span>  
 `endOffset`  
 <span data-ttu-id="e39c0-106">[in] Le décalage à partir du début de la méthode du point à la fin de la dernière instruction dans la portée lexicale, en octets.</span><span class="sxs-lookup"><span data-stu-id="e39c0-106">[in] The offset from the beginning of the method of the point at the end of the last instruction in the lexical scope, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e39c0-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="e39c0-107">Return Value</span></span>  
 <span data-ttu-id="e39c0-108">S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="e39c0-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e39c0-109">Notes</span><span class="sxs-lookup"><span data-stu-id="e39c0-109">Remarks</span></span>  
 <span data-ttu-id="e39c0-110">Une fois qu’une portée est fermée, aucuns plus de variables ne peuvent être définies qu’il contient.</span><span class="sxs-lookup"><span data-stu-id="e39c0-110">Once a scope is closed, no more variables can be defined within it.</span></span>  
  
 <span data-ttu-id="e39c0-111">[ISymUnmanagedWriter::OpenScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openscope-method.md) retourne un identificateur de portée opaque qui peut être utilisé avec [ISymUnmanagedWriter::SetScopeRange](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setscoperange-method.md) pour définir ultérieurement une étendue de démarrage et le décalage de fin.</span><span class="sxs-lookup"><span data-stu-id="e39c0-111">[ISymUnmanagedWriter::OpenScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openscope-method.md) returns an opaque scope identifier that can be used with [ISymUnmanagedWriter::SetScopeRange](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setscoperange-method.md) to later define a scope's starting and ending offset.</span></span> <span data-ttu-id="e39c0-112">Dans ce cas, les offsets passés à `ISymUnmanagedWriter::OpenScope` et `ISymUnmanagedWriter::CloseScope` sont ignorés.</span><span class="sxs-lookup"><span data-stu-id="e39c0-112">In this case, the offsets passed to `ISymUnmanagedWriter::OpenScope` and `ISymUnmanagedWriter::CloseScope` are ignored.</span></span> <span data-ttu-id="e39c0-113">Les identificateurs de portée sont valides uniquement dans la méthode actuelle.</span><span class="sxs-lookup"><span data-stu-id="e39c0-113">Scope identifiers are valid only in the current method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e39c0-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="e39c0-114">Requirements</span></span>  
 <span data-ttu-id="e39c0-115">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="e39c0-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e39c0-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e39c0-116">See Also</span></span>  
 [<span data-ttu-id="e39c0-117">ISymUnmanagedWriter, interface</span><span class="sxs-lookup"><span data-stu-id="e39c0-117">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
