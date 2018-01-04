---
title: "ISymUnmanagedMethod::GetSourceStartEnd, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedMethod.GetSourceStartEnd
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedMethod::GetSourceStartEnd
helpviewer_keywords:
- GetSourceStartEnd method [.NET Framework debugging]
- ISymUnmanagedMethod::GetSourceStartEnd method [.NET Framework debugging]
ms.assetid: 2a420900-01f1-4461-8777-3a34a6dc1426
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f2bdc044d4560b616bd6eeb8d642567add1f659f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedmethodgetsourcestartend-method"></a><span data-ttu-id="4133d-102">ISymUnmanagedMethod::GetSourceStartEnd, méthode</span><span class="sxs-lookup"><span data-stu-id="4133d-102">ISymUnmanagedMethod::GetSourceStartEnd Method</span></span>
<span data-ttu-id="4133d-103">Obtient les positions de document de début et de fin de la source de cette méthode.</span><span class="sxs-lookup"><span data-stu-id="4133d-103">Gets the start and end document positions for the source of this method.</span></span> <span data-ttu-id="4133d-104">La première position du tableau correspond au début, et la deuxième position du tableau est à la fin.</span><span class="sxs-lookup"><span data-stu-id="4133d-104">The first array position is the start, and the second array position is the end.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4133d-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4133d-105">Syntax</span></span>  
  
```  
HRESULT GetSourceStartEnd(  
    [in]  ISymUnmanagedDocument  *docs[2],  
    [in]  ULONG32                lines[2],  
    [in]  ULONG32                columns[2],  
    [out] BOOL                   *pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4133d-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="4133d-106">Parameters</span></span>  
 `docs`  
 <span data-ttu-id="4133d-107">[in] Le début et de fin de documents sources.</span><span class="sxs-lookup"><span data-stu-id="4133d-107">[in] The starting and ending source documents.</span></span>  
  
 `lines`  
 <span data-ttu-id="4133d-108">[in] Documents de sources de début et de fin de ligne qui correspond.</span><span class="sxs-lookup"><span data-stu-id="4133d-108">[in] The starting and ending lines in the corresponding source documents.</span></span>  
  
 `columns`  
 <span data-ttu-id="4133d-109">[in] Documents de sources de début et fin des colonnes, qui correspond.</span><span class="sxs-lookup"><span data-stu-id="4133d-109">[in] The starting and ending columns in the corresponding source documents.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="4133d-110">[out] `true` si les positions ont été définies ; sinon, `false`.</span><span class="sxs-lookup"><span data-stu-id="4133d-110">[out] `true` if positions were defined; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4133d-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="4133d-111">Return Value</span></span>  
 <span data-ttu-id="4133d-112">S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="4133d-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4133d-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="4133d-113">Requirements</span></span>  
 <span data-ttu-id="4133d-114">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="4133d-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4133d-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4133d-115">See Also</span></span>  
 [<span data-ttu-id="4133d-116">ISymUnmanagedMethod, interface</span><span class="sxs-lookup"><span data-stu-id="4133d-116">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
