---
title: "ISymUnmanagedMethod::GetSequencePoints, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedMethod.GetSequencePoints
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedMethod::GetSequencePoints
helpviewer_keywords:
- ISymUnmanagedMethod::GetSequencePoints method [.NET Framework debugging]
- GetSequencePoints method [.NET Framework debugging]
ms.assetid: f909ac48-3d8f-49fb-a369-e3d9959151cd
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 3cde9de634534acdeafa40bd7a94c46624e49604
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedmethodgetsequencepoints-method"></a><span data-ttu-id="9d8a9-102">ISymUnmanagedMethod::GetSequencePoints, méthode</span><span class="sxs-lookup"><span data-stu-id="9d8a9-102">ISymUnmanagedMethod::GetSequencePoints Method</span></span>
<span data-ttu-id="9d8a9-103">Obtient tous les points de séquence au sein de cette méthode.</span><span class="sxs-lookup"><span data-stu-id="9d8a9-103">Gets all the sequence points within this method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d8a9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9d8a9-104">Syntax</span></span>  
  
```  
HRESULT GetSequencePoints(  
    [in]  ULONG32  cPoints,  
    [out] ULONG32  *pcPoints,  
    [in, size_is(cPoints)] ULONG32  offsets[],  
    [in, size_is(cPoints)] ISymUnmanagedDocument* documents[],  
    [in, size_is(cPoints)] ULONG32  lines[],  
    [in, size_is(cPoints)] ULONG32  columns[],  
    [in, size_is(cPoints)] ULONG32  endLines[],  
    [in, size_is(cPoints)] ULONG32  endColumns[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9d8a9-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9d8a9-105">Parameters</span></span>  
 `cPoints`  
 <span data-ttu-id="9d8a9-106">[in] A `ULONG32` qui reçoit la taille de la `offsets`, `documents`, `lines`, `columns`, `endLines`, et `endColumns` tableaux.</span><span class="sxs-lookup"><span data-stu-id="9d8a9-106">[in] A `ULONG32` that receives the size of the `offsets`, `documents`, `lines`, `columns`, `endLines`, and `endColumns` arrays.</span></span>  
  
 `pcPoints`  
 <span data-ttu-id="9d8a9-107">[out] Un pointeur vers un `ULONG32` qui reçoit la longueur de la mémoire tampon requise pour contenir les points de séquence.</span><span class="sxs-lookup"><span data-stu-id="9d8a9-107">[out] A pointer to a `ULONG32` that receives the length of the buffer required to contain the sequence points.</span></span>  
  
 `offsets`  
 <span data-ttu-id="9d8a9-108">[in] Tableau dans lequel stocker le Microsoft intermediate language (MSIL) offsets à partir du début de la méthode pour les points de séquence.</span><span class="sxs-lookup"><span data-stu-id="9d8a9-108">[in] An array in which to store the Microsoft intermediate language (MSIL) offsets from the beginning of the method for the sequence points.</span></span>  
  
 `documents`  
 <span data-ttu-id="9d8a9-109">[in] Tableau dans lequel stocker les documents dans laquelle se trouvent les points de séquence.</span><span class="sxs-lookup"><span data-stu-id="9d8a9-109">[in] An array in which to store the documents in which the sequence points are located.</span></span>  
  
 `lines`  
 <span data-ttu-id="9d8a9-110">[in] Tableau dans lequel stocker les lignes des documents auxquelles figurent les points de séquence.</span><span class="sxs-lookup"><span data-stu-id="9d8a9-110">[in] An array in which to store the lines in the documents at which the sequence points are located.</span></span>  
  
 `columns`  
 <span data-ttu-id="9d8a9-111">[in] Tableau dans lequel stocker les colonnes des documents auxquelles figurent les points de séquence.</span><span class="sxs-lookup"><span data-stu-id="9d8a9-111">[in] An array in which to store the columns in the documents at which the sequence points are located.</span></span>  
  
 `endLines`  
 <span data-ttu-id="9d8a9-112">[in] Tableau de lignes des documents auxquelles la séquence de points de terminaison.</span><span class="sxs-lookup"><span data-stu-id="9d8a9-112">[in] The array of lines in the documents at which the sequence points end.</span></span>  
  
 `endColumns`  
 <span data-ttu-id="9d8a9-113">[in] Tableau de colonnes des documents auxquelles la séquence de points de terminaison.</span><span class="sxs-lookup"><span data-stu-id="9d8a9-113">[in] The array of columns in the documents at which the sequence points end.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9d8a9-114">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="9d8a9-114">Return Value</span></span>  
 <span data-ttu-id="9d8a9-115">S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="9d8a9-115">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d8a9-116">Spécifications</span><span class="sxs-lookup"><span data-stu-id="9d8a9-116">Requirements</span></span>  
 <span data-ttu-id="9d8a9-117">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="9d8a9-117">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d8a9-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9d8a9-118">See Also</span></span>  
 [<span data-ttu-id="9d8a9-119">ISymUnmanagedMethod (Interface)</span><span class="sxs-lookup"><span data-stu-id="9d8a9-119">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
