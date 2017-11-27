---
title: "ISymUnmanagedReader::GetDocuments, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedReader.GetDocuments
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedReader::GetDocuments
helpviewer_keywords:
- GetDocuments method [.NET Framework debugging]
- ISymUnmanagedReader::GetDocuments method [.NET Framework debugging]
ms.assetid: e3b73a3f-d089-4101-a9a9-5e0765d05b61
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 27268b7f32f2c9aa667790c6d4516f1b8e015f96
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedreadergetdocuments-method"></a><span data-ttu-id="746dd-102">ISymUnmanagedReader::GetDocuments, méthode</span><span class="sxs-lookup"><span data-stu-id="746dd-102">ISymUnmanagedReader::GetDocuments Method</span></span>
<span data-ttu-id="746dd-103">Retourne un tableau de tous les documents définis dans le magasin de symboles.</span><span class="sxs-lookup"><span data-stu-id="746dd-103">Returns an array of all the documents defined in the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="746dd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="746dd-104">Syntax</span></span>  
  
```  
HRESULT GetDocuments (  
    [in]  ULONG32  cDocs,  
    [out] ULONG32  *pcDocs,  
    [out, size_is (cDocs),  
        length_is (*pcDocs)] ISymUnmanagedDocument *pDocs[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="746dd-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="746dd-105">Parameters</span></span>  
 `cDocs`  
 <span data-ttu-id="746dd-106">[in] Taille du tableau `pDocs`.</span><span class="sxs-lookup"><span data-stu-id="746dd-106">[in] The size of the `pDocs` array.</span></span>  
  
 `pcDocs`  
 <span data-ttu-id="746dd-107">[out] Pointeur vers une variable qui reçoit la longueur du tableau.</span><span class="sxs-lookup"><span data-stu-id="746dd-107">[out] A pointer to a variable that receives the array length.</span></span>  
  
 `pDocs`  
 <span data-ttu-id="746dd-108">[out] Pointeur vers une variable qui reçoit le tableau de documents.</span><span class="sxs-lookup"><span data-stu-id="746dd-108">[out] A pointer to a variable that receives the document array.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="746dd-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="746dd-109">Return Value</span></span>  
 <span data-ttu-id="746dd-110">S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="746dd-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="746dd-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="746dd-111">Requirements</span></span>  
 <span data-ttu-id="746dd-112">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="746dd-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="746dd-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="746dd-113">See Also</span></span>  
 [<span data-ttu-id="746dd-114">ISymUnmanagedReader (Interface)</span><span class="sxs-lookup"><span data-stu-id="746dd-114">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
