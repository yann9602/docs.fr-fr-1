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
ms.openlocfilehash: 7fcc18b1441093a3e3a1a0e813ccfb4ba3ad507b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedreadergetdocument-method"></a><span data-ttu-id="62d03-102">ISymUnmanagedReader::GetDocument, méthode</span><span class="sxs-lookup"><span data-stu-id="62d03-102">ISymUnmanagedReader::GetDocument Method</span></span>
<span data-ttu-id="62d03-103">Recherche d’un document.</span><span class="sxs-lookup"><span data-stu-id="62d03-103">Finds a document.</span></span> <span data-ttu-id="62d03-104">Le langage du document, le fournisseur et le type sont facultatifs.</span><span class="sxs-lookup"><span data-stu-id="62d03-104">The document language, vendor, and type are optional.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62d03-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="62d03-105">Syntax</span></span>  
  
```  
HRESULT GetDocument (  
    [in]  WCHAR  *url,  
    [in]  GUID   language,  
    [in]  GUID   languageVendor,  
    [in]  GUID   documentType,  
    [out, retval] ISymUnmanagedDocument** pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="62d03-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="62d03-106">Parameters</span></span>  
 `url`  
 <span data-ttu-id="62d03-107">[in] L’URL qui identifie le document.</span><span class="sxs-lookup"><span data-stu-id="62d03-107">[in] The URL that identifies the document.</span></span>  
  
 `language`  
 <span data-ttu-id="62d03-108">[in] Le langage du document.</span><span class="sxs-lookup"><span data-stu-id="62d03-108">[in] The document language.</span></span> <span data-ttu-id="62d03-109">Ce paramètre est optionnel.</span><span class="sxs-lookup"><span data-stu-id="62d03-109">This parameter is optional.</span></span>  
  
 `languageVendor`  
 <span data-ttu-id="62d03-110">[in] L’identité du fournisseur de langage du document.</span><span class="sxs-lookup"><span data-stu-id="62d03-110">[in] The identity of the vendor for the document language.</span></span> <span data-ttu-id="62d03-111">Ce paramètre est optionnel.</span><span class="sxs-lookup"><span data-stu-id="62d03-111">This parameter is optional.</span></span>  
  
 `documentType`  
 <span data-ttu-id="62d03-112">[in] Le type du document.</span><span class="sxs-lookup"><span data-stu-id="62d03-112">[in] The type of the document.</span></span> <span data-ttu-id="62d03-113">Ce paramètre est optionnel.</span><span class="sxs-lookup"><span data-stu-id="62d03-113">This parameter is optional.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="62d03-114">[out] Pointeur vers l’interface retournée.</span><span class="sxs-lookup"><span data-stu-id="62d03-114">[out] A pointer to the returned interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="62d03-115">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="62d03-115">Return Value</span></span>  
 <span data-ttu-id="62d03-116">S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="62d03-116">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="62d03-117">Spécifications</span><span class="sxs-lookup"><span data-stu-id="62d03-117">Requirements</span></span>  
 <span data-ttu-id="62d03-118">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="62d03-118">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62d03-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="62d03-119">See Also</span></span>  
 [<span data-ttu-id="62d03-120">ISymUnmanagedReader (Interface)</span><span class="sxs-lookup"><span data-stu-id="62d03-120">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
