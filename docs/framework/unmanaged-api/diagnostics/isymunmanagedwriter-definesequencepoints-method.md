---
title: "ISymUnmanagedWriter::DefineSequencePoints, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.DefineSequencePoints
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::DefineSequencePoints
helpviewer_keywords:
- DefineSequencePoints method [.NET Framework debugging]
- ISymUnmanagedWriter::DefineSequencePoints method [.NET Framework debugging]
ms.assetid: 64202baf-be6b-40ba-8162-8cc6c0c9b8e1
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 836774114798324ac16d3263e58dd56665a9aa49
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedwriterdefinesequencepoints-method"></a><span data-ttu-id="83ca4-102">ISymUnmanagedWriter::DefineSequencePoints, méthode</span><span class="sxs-lookup"><span data-stu-id="83ca4-102">ISymUnmanagedWriter::DefineSequencePoints Method</span></span>
<span data-ttu-id="83ca4-103">Définit un groupe de points de séquence dans la méthode actuelle.</span><span class="sxs-lookup"><span data-stu-id="83ca4-103">Defines a group of sequence points within the current method.</span></span> <span data-ttu-id="83ca4-104">Chaque ligne de début et de la colonne de début définissent le début d’une instruction dans une méthode.</span><span class="sxs-lookup"><span data-stu-id="83ca4-104">Each starting line and starting column define the start of a statement within a method.</span></span> <span data-ttu-id="83ca4-105">Chaque ligne de fin et de colonne de fin définissent la fin d’une instruction dans une méthode.</span><span class="sxs-lookup"><span data-stu-id="83ca4-105">Each ending line and ending column define the end of a statement within a method.</span></span> <span data-ttu-id="83ca4-106">Les tableaux doivent être triés dans l’ordre croissant des offsets.</span><span class="sxs-lookup"><span data-stu-id="83ca4-106">The arrays should be sorted in increasing order of offsets.</span></span> <span data-ttu-id="83ca4-107">Le décalage est mesuré à partir du début de la méthode, en octets.</span><span class="sxs-lookup"><span data-stu-id="83ca4-107">The offset is always measured from the start of the method, in bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83ca4-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="83ca4-108">Syntax</span></span>  
  
```  
HRESULT DefineSequencePoints(  
    [in] ISymUnmanagedDocumentWriter*  document,  
    [in] ULONG32 spCount,  
    [in, size_is(spCount)] ULONG32     offsets[],  
    [in, size_is(spCount)] ULONG32     lines[],  
    [in, size_is(spCount)] ULONG32     columns[],  
    [in, size_is(spCount)] ULONG32     endLines[],  
    [in, size_is(spCount)] ULONG32     endColumns[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="83ca4-109">Paramètres</span><span class="sxs-lookup"><span data-stu-id="83ca4-109">Parameters</span></span>  
 `document`  
 <span data-ttu-id="83ca4-110">[in] L’objet de document pour lequel les points de séquence sont définies.</span><span class="sxs-lookup"><span data-stu-id="83ca4-110">[in] The document object for which the sequence points are being defined.</span></span>  
  
 `spCount`  
 <span data-ttu-id="83ca4-111">[in] A `ULONG32` qui indique la taille de chacun de la `offsets`, `lines`, `columns`, `endLines`, et `endColumns` mémoires tampons.</span><span class="sxs-lookup"><span data-stu-id="83ca4-111">[in] A `ULONG32` that that indicates the size of each of the `offsets`, `lines`, `columns`, `endLines`, and `endColumns` buffers.</span></span>  
  
 `offsets`  
 <span data-ttu-id="83ca4-112">[in] Le décalage des points de séquence mesuré à partir du début de la méthode.</span><span class="sxs-lookup"><span data-stu-id="83ca4-112">[in] The offset of the sequence points measured from the beginning of the method.</span></span>  
  
 `lines`  
 <span data-ttu-id="83ca4-113">[in] Les numéros de ligne de départ des points de séquence.</span><span class="sxs-lookup"><span data-stu-id="83ca4-113">[in] The starting line numbers of the sequence points.</span></span>  
  
 `columns`  
 <span data-ttu-id="83ca4-114">[in] Les numéros de colonne de début des points de séquence.</span><span class="sxs-lookup"><span data-stu-id="83ca4-114">[in] The starting column numbers of the sequence points.</span></span>  
  
 `endLines`  
 <span data-ttu-id="83ca4-115">[in] Les numéros de ligne de fin des points de séquence.</span><span class="sxs-lookup"><span data-stu-id="83ca4-115">[in] The ending line numbers of the sequence points.</span></span> <span data-ttu-id="83ca4-116">Ce paramètre est optionnel.</span><span class="sxs-lookup"><span data-stu-id="83ca4-116">This parameter is optional.</span></span>  
  
 `endColumns`  
 <span data-ttu-id="83ca4-117">[in] Les numéros de colonne de fin des points de séquence.</span><span class="sxs-lookup"><span data-stu-id="83ca4-117">[in] The ending column numbers of the sequence points.</span></span> <span data-ttu-id="83ca4-118">Ce paramètre est optionnel.</span><span class="sxs-lookup"><span data-stu-id="83ca4-118">This parameter is optional.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="83ca4-119">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="83ca4-119">Return Value</span></span>  
 <span data-ttu-id="83ca4-120">S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="83ca4-120">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="83ca4-121">Spécifications</span><span class="sxs-lookup"><span data-stu-id="83ca4-121">Requirements</span></span>  
 <span data-ttu-id="83ca4-122">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="83ca4-122">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83ca4-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="83ca4-123">See Also</span></span>  
 [<span data-ttu-id="83ca4-124">ISymUnmanagedWriter (Interface)</span><span class="sxs-lookup"><span data-stu-id="83ca4-124">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
