---
title: "ISymUnmanagedMethod::GetRanges, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedMethod.GetRanges
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedMethod::GetRanges
helpviewer_keywords:
- ISymUnmanagedMethod::GetRanges method [.NET Framework debugging]
- GetRanges method [.NET Framework debugging]
ms.assetid: a85283d8-379c-417a-9736-ddeeef9bcf50
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 71d24bc83d6a26c800d0d97e885b322cc2b4ccbd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedmethodgetranges-method"></a><span data-ttu-id="d288f-102">ISymUnmanagedMethod::GetRanges, méthode</span><span class="sxs-lookup"><span data-stu-id="d288f-102">ISymUnmanagedMethod::GetRanges Method</span></span>
<span data-ttu-id="d288f-103">Une position donnée dans un document, retourne un tableau de début et fin paires d’offsets qui correspondent aux plages de langage intermédiaire Microsoft (MSIL) qui traite de la position au sein de cette méthode.</span><span class="sxs-lookup"><span data-stu-id="d288f-103">Given a position in a document, returns an array of start and end offset pairs that correspond to the ranges of Microsoft intermediate language (MSIL) that the position covers within this method.</span></span> <span data-ttu-id="d288f-104">Le tableau est un tableau d’entiers et a le format [début, fin, début, fin].</span><span class="sxs-lookup"><span data-stu-id="d288f-104">The array is an array of integers and has the format [start, end, start, end].</span></span> <span data-ttu-id="d288f-105">Le nombre de paires de plage est la longueur du tableau divisée par 2.</span><span class="sxs-lookup"><span data-stu-id="d288f-105">The number of range pairs is the length of the array divided by 2.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d288f-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d288f-106">Syntax</span></span>  
  
```  
HRESULT GetRanges(  
    [in]  ISymUnmanagedDocument* document,  
    [in]  ULONG32                line,  
    [in]  ULONG32                column,  
    [in]  ULONG32                cRanges,  
    [out] ULONG32                *pcRanges,  
    [out, size_is(cRanges),  
        length_is(*pcRanges)] ULONG32 ranges[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d288f-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d288f-107">Parameters</span></span>  
 `document`  
 <span data-ttu-id="d288f-108">[in] Le document pour lequel l’offset est demandé.</span><span class="sxs-lookup"><span data-stu-id="d288f-108">[in] The document for which the offset is requested.</span></span>  
  
 `line`  
 <span data-ttu-id="d288f-109">[in] Ligne du document correspondant aux plages.</span><span class="sxs-lookup"><span data-stu-id="d288f-109">[in] The document line corresponding to the ranges.</span></span>  
  
 `column`  
 <span data-ttu-id="d288f-110">[in] Colonne du document correspondant aux plages.</span><span class="sxs-lookup"><span data-stu-id="d288f-110">[in] The document column corresponding to the ranges.</span></span>  
  
 `cRanges`  
 <span data-ttu-id="d288f-111">[in] Taille du tableau `ranges`.</span><span class="sxs-lookup"><span data-stu-id="d288f-111">[in] The size of the `ranges` array.</span></span>  
  
 `pcRanges`  
 <span data-ttu-id="d288f-112">[out] Un pointeur vers un `ULONG32` qui reçoit la taille de la mémoire tampon requise pour contenir les plages.</span><span class="sxs-lookup"><span data-stu-id="d288f-112">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the ranges.</span></span>  
  
 `ranges`  
 <span data-ttu-id="d288f-113">[out] Pointeur vers la mémoire tampon qui reçoit les plages.</span><span class="sxs-lookup"><span data-stu-id="d288f-113">[out] A pointer to the buffer that receives the ranges.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d288f-114">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="d288f-114">Return Value</span></span>  
 <span data-ttu-id="d288f-115">S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="d288f-115">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d288f-116">Spécifications</span><span class="sxs-lookup"><span data-stu-id="d288f-116">Requirements</span></span>  
 <span data-ttu-id="d288f-117">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="d288f-117">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d288f-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d288f-118">See Also</span></span>  
 [<span data-ttu-id="d288f-119">ISymUnmanagedMethod (Interface)</span><span class="sxs-lookup"><span data-stu-id="d288f-119">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
