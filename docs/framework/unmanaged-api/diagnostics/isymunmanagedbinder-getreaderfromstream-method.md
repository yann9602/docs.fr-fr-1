---
title: "ISymUnmanagedBinder::GetReaderFromStream, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedBinder.GetReaderFromStream
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedBinder::GetReaderFromStream
helpviewer_keywords:
- ISymUnmanagedBinder::GetReaderFromStream method [.NET Framework debugging]
- GetReaderFromStream method [.NET Framework debugging]
ms.assetid: aa38efd4-de7e-4482-a5d3-adc152093460
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 36d4d0067cd638eb39ce82eb042242b7b08d3647
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedbindergetreaderfromstream-method"></a><span data-ttu-id="23dc8-102">ISymUnmanagedBinder::GetReaderFromStream, méthode</span><span class="sxs-lookup"><span data-stu-id="23dc8-102">ISymUnmanagedBinder::GetReaderFromStream Method</span></span>
<span data-ttu-id="23dc8-103">Une interface de métadonnées et un flux qui contient le magasin de symboles, retourne le correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) structure qui lira le débogage des symboles à partir du magasin de symboles donné.</span><span class="sxs-lookup"><span data-stu-id="23dc8-103">Given a metadata interface and a stream that contains the symbol store, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) structure that will read the debugging symbols from the given symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23dc8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="23dc8-104">Syntax</span></span>  
  
```  
HRESULT GetReaderFromStream(  
    [in]  IUnknown  *importer,  
    [in]  IStream   *pstream,  
    [out,retval] ISymUnmanagedReader **pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="23dc8-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="23dc8-105">Parameters</span></span>  
 `importer`  
 <span data-ttu-id="23dc8-106">[in] Pointeur vers l’interface d’importation de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="23dc8-106">[in] A pointer to the metadata import interface.</span></span>  
  
 `pstream`  
 <span data-ttu-id="23dc8-107">[in] Pointeur vers le flux de données qui contient le magasin de symboles.</span><span class="sxs-lookup"><span data-stu-id="23dc8-107">[in] A pointer to the stream that contains the symbol store.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="23dc8-108">[out] Un pointeur qui est défini à le [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="23dc8-108">[out] A pointer that is set to the returned [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="23dc8-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="23dc8-109">Return Value</span></span>  
 <span data-ttu-id="23dc8-110">S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="23dc8-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="23dc8-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="23dc8-111">Requirements</span></span>  
 <span data-ttu-id="23dc8-112">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="23dc8-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23dc8-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="23dc8-113">See Also</span></span>  
 [<span data-ttu-id="23dc8-114">ISymUnmanagedBinder, interface</span><span class="sxs-lookup"><span data-stu-id="23dc8-114">ISymUnmanagedBinder Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)
