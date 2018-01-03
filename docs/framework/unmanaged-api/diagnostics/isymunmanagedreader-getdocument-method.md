---
title: "ISymUnmanagedReader::GetDocument, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedReader.GetDocument
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedReader::GetDocument
helpviewer_keywords:
- ISymUnmanagedReader::GetDocument method [.NET Framework debugging]
- GetDocument method [.NET Framework debugging]
ms.assetid: bb203853-6a6d-4027-b9e9-603a7f28b9d3
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 00ded0e7e88cacbcedb66e1cef27e4f5eaaf4d29
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedreadergetdocument-method"></a><span data-ttu-id="2d6c2-102">ISymUnmanagedReader::GetDocument, méthode</span><span class="sxs-lookup"><span data-stu-id="2d6c2-102">ISymUnmanagedReader::GetDocument Method</span></span>
<span data-ttu-id="2d6c2-103">Recherche d’un document.</span><span class="sxs-lookup"><span data-stu-id="2d6c2-103">Finds a document.</span></span> <span data-ttu-id="2d6c2-104">Le langage du document, le fournisseur et le type sont facultatifs.</span><span class="sxs-lookup"><span data-stu-id="2d6c2-104">The document language, vendor, and type are optional.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d6c2-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2d6c2-105">Syntax</span></span>  
  
```  
HRESULT GetDocument (  
    [in]  WCHAR  *url,  
    [in]  GUID   language,  
    [in]  GUID   languageVendor,  
    [in]  GUID   documentType,  
    [out, retval] ISymUnmanagedDocument** pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2d6c2-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2d6c2-106">Parameters</span></span>  
 `url`  
 <span data-ttu-id="2d6c2-107">[in] L’URL qui identifie le document.</span><span class="sxs-lookup"><span data-stu-id="2d6c2-107">[in] The URL that identifies the document.</span></span>  
  
 `language`  
 <span data-ttu-id="2d6c2-108">[in] Le langage du document.</span><span class="sxs-lookup"><span data-stu-id="2d6c2-108">[in] The document language.</span></span> <span data-ttu-id="2d6c2-109">Ce paramètre est optionnel.</span><span class="sxs-lookup"><span data-stu-id="2d6c2-109">This parameter is optional.</span></span>  
  
 `languageVendor`  
 <span data-ttu-id="2d6c2-110">[in] L’identité du fournisseur de langage du document.</span><span class="sxs-lookup"><span data-stu-id="2d6c2-110">[in] The identity of the vendor for the document language.</span></span> <span data-ttu-id="2d6c2-111">Ce paramètre est optionnel.</span><span class="sxs-lookup"><span data-stu-id="2d6c2-111">This parameter is optional.</span></span>  
  
 `documentType`  
 <span data-ttu-id="2d6c2-112">[in] Le type du document.</span><span class="sxs-lookup"><span data-stu-id="2d6c2-112">[in] The type of the document.</span></span> <span data-ttu-id="2d6c2-113">Ce paramètre est optionnel.</span><span class="sxs-lookup"><span data-stu-id="2d6c2-113">This parameter is optional.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="2d6c2-114">[out] Pointeur vers l’interface retournée.</span><span class="sxs-lookup"><span data-stu-id="2d6c2-114">[out] A pointer to the returned interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2d6c2-115">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="2d6c2-115">Return Value</span></span>  
 <span data-ttu-id="2d6c2-116">S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="2d6c2-116">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2d6c2-117">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="2d6c2-117">Requirements</span></span>  
 <span data-ttu-id="2d6c2-118">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="2d6c2-118">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d6c2-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2d6c2-119">See Also</span></span>  
 [<span data-ttu-id="2d6c2-120">ISymUnmanagedReader, interface</span><span class="sxs-lookup"><span data-stu-id="2d6c2-120">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
