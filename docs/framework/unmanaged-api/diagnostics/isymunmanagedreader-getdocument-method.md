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
# <a name="isymunmanagedreadergetdocument-method"></a>ISymUnmanagedReader::GetDocument, méthode
Recherche d’un document. Le langage du document, le fournisseur et le type sont facultatifs.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetDocument (  
    [in]  WCHAR  *url,  
    [in]  GUID   language,  
    [in]  GUID   languageVendor,  
    [in]  GUID   documentType,  
    [out, retval] ISymUnmanagedDocument** pRetVal);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `url`  
 [in] L’URL qui identifie le document.  
  
 `language`  
 [in] Le langage du document. Ce paramètre est optionnel.  
  
 `languageVendor`  
 [in] L’identité du fournisseur de langage du document. Ce paramètre est optionnel.  
  
 `documentType`  
 [in] Le type du document. Ce paramètre est optionnel.  
  
 `pRetVal`  
 [out] Pointeur vers l’interface retournée.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Voir aussi  
 [ISymUnmanagedReader, interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
