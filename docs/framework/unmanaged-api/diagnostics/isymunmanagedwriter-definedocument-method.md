---
title: "ISymUnmanagedWriter::DefineDocument, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.DefineDocument
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::DefineDocument
helpviewer_keywords:
- ISymUnmanagedWriter::DefineDocument method [.NET Framework debugging]
- DefineDocument method [.NET Framework debugging]
ms.assetid: c3bf15b0-3250-4bbe-b9b5-c5d695289b6f
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 638759cb52eb28cc79217da81a867f2593e1ae97
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedwriterdefinedocument-method"></a><span data-ttu-id="80bc5-102">ISymUnmanagedWriter::DefineDocument, méthode</span><span class="sxs-lookup"><span data-stu-id="80bc5-102">ISymUnmanagedWriter::DefineDocument Method</span></span>
<span data-ttu-id="80bc5-103">Définit un document source.</span><span class="sxs-lookup"><span data-stu-id="80bc5-103">Defines a source document.</span></span> <span data-ttu-id="80bc5-104">GUID est fournies pour les langues connus, les fournisseurs et les types de documents.</span><span class="sxs-lookup"><span data-stu-id="80bc5-104">GUIDs are provided for known languages, vendors, and document types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80bc5-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="80bc5-105">Syntax</span></span>  
  
```  
HRESULT DefineDocument(  
    [in]  const WCHAR  *url,  
    [in]  const GUID   *language,  
    [in]  const GUID   *languageVendor,  
    [in]  const GUID   *documentType,  
    [out, retval] ISymUnmanagedDocumentWriter**  pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="80bc5-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="80bc5-106">Parameters</span></span>  
 `url`  
 <span data-ttu-id="80bc5-107">[in] Un pointeur vers un `WCHAR` qui définit l’uniform resource locator (URL) qui identifie le document.</span><span class="sxs-lookup"><span data-stu-id="80bc5-107">[in] A pointer to a `WCHAR` that defines the uniform resource locator (URL) that identifies the document.</span></span>  
  
 `language`  
 <span data-ttu-id="80bc5-108">[in] Pointeur vers un GUID qui définit le langage du document.</span><span class="sxs-lookup"><span data-stu-id="80bc5-108">[in] A pointer to a GUID that defines the document language.</span></span>  
  
 `languageVendor`  
 <span data-ttu-id="80bc5-109">[in] Pointeur vers un GUID qui définit l’identité du fournisseur de langage du document.</span><span class="sxs-lookup"><span data-stu-id="80bc5-109">[in] A pointer to a GUID that defines the identity of the vendor for the document language.</span></span>  
  
 `documentType`  
 <span data-ttu-id="80bc5-110">[in] Pointeur vers un GUID qui définit le type du document.</span><span class="sxs-lookup"><span data-stu-id="80bc5-110">[in] A pointer to a GUID that defines the type of the document.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="80bc5-111">[out] Un pointeur vers retourné [ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="80bc5-111">[out] A pointer to the returned [ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="80bc5-112">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="80bc5-112">Return Value</span></span>  
 <span data-ttu-id="80bc5-113">S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="80bc5-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="80bc5-114">Spécifications</span><span class="sxs-lookup"><span data-stu-id="80bc5-114">Requirements</span></span>  
 <span data-ttu-id="80bc5-115">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="80bc5-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80bc5-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="80bc5-116">See Also</span></span>  
 [<span data-ttu-id="80bc5-117">ISymUnmanagedWriter (Interface)</span><span class="sxs-lookup"><span data-stu-id="80bc5-117">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
