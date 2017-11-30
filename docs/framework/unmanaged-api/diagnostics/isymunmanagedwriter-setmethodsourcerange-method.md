---
title: "ISymUnmanagedWriter::SetMethodSourceRange, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.SetMethodSourceRange
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::SetMethodSourceRange
helpviewer_keywords:
- SetMethodSourceRange method [.NET Framework debugging]
- ISymUnmanagedWriter::SetMethodSourceRange method [.NET Framework debugging]
ms.assetid: c698b86e-ace7-4b21-9549-f52d6a034959
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 85ed0a73b4862702895e737f2df639b8da7f7679
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedwritersetmethodsourcerange-method"></a><span data-ttu-id="16dae-102">ISymUnmanagedWriter::SetMethodSourceRange, méthode</span><span class="sxs-lookup"><span data-stu-id="16dae-102">ISymUnmanagedWriter::SetMethodSourceRange Method</span></span>
<span data-ttu-id="16dae-103">Spécifie les véritables début et la fin d’une méthode dans un fichier source.</span><span class="sxs-lookup"><span data-stu-id="16dae-103">Specifies the true start and end of a method within a source file.</span></span> <span data-ttu-id="16dae-104">Utilisez cette méthode pour spécifier l’étendue d’une méthode indépendamment des points de séquence qui existent dans la méthode.</span><span class="sxs-lookup"><span data-stu-id="16dae-104">Use this method to specify the extent of a method independently of the sequence points that exist within the method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16dae-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="16dae-105">Syntax</span></span>  
  
```  
HRESULT SetMethodSourceRange(  
    [in] ISymUnmanagedDocumentWriter  *startDoc,  
    [in] ULONG32                      startLine,  
    [in] ULONG32                      startColumn,  
    [in] ISymUnmanagedDocumentWriter  *endDoc,  
    [in] ULONG32                      endLine,  
    [in] ULONG32                      endColumn);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="16dae-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="16dae-106">Parameters</span></span>  
 `startDoc`  
 <span data-ttu-id="16dae-107">[in] Pointeur vers le document contenant la position de départ.</span><span class="sxs-lookup"><span data-stu-id="16dae-107">[in] A pointer to the document containing the starting position.</span></span>  
  
 `startLine`  
 <span data-ttu-id="16dae-108">[in] Le numéro de ligne de départ.</span><span class="sxs-lookup"><span data-stu-id="16dae-108">[in] The starting line number.</span></span>  
  
 `startColumn`  
 <span data-ttu-id="16dae-109">[in] La colonne de départ.</span><span class="sxs-lookup"><span data-stu-id="16dae-109">[in] The starting column.</span></span>  
  
 `endDoc`  
 <span data-ttu-id="16dae-110">[in] Pointeur vers le document contenant la position de fin.</span><span class="sxs-lookup"><span data-stu-id="16dae-110">[in] A pointer to the document containing the ending position.</span></span>  
  
 `endLine`  
 <span data-ttu-id="16dae-111">[in] Le numéro de ligne de fin.</span><span class="sxs-lookup"><span data-stu-id="16dae-111">[in] The ending line number.</span></span>  
  
 `endColumn`  
 <span data-ttu-id="16dae-112">[in] Le numéro de colonne de fin.</span><span class="sxs-lookup"><span data-stu-id="16dae-112">[in] The ending column number.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="16dae-113">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="16dae-113">Return Value</span></span>  
 <span data-ttu-id="16dae-114">S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="16dae-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="16dae-115">Spécifications</span><span class="sxs-lookup"><span data-stu-id="16dae-115">Requirements</span></span>  
 <span data-ttu-id="16dae-116">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="16dae-116">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16dae-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="16dae-117">See Also</span></span>  
 [<span data-ttu-id="16dae-118">ISymUnmanagedWriter (Interface)</span><span class="sxs-lookup"><span data-stu-id="16dae-118">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
