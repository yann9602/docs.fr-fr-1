---
title: "ISymUnmanagedDocument::GetDocumentType, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedDocument.GetDocumentType
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedDocument::GetDocumentType
helpviewer_keywords:
- ISymUnmanagedDocument::GetDocumentType method [.NET Framework debugging]
- GetDocumentType method [.NET Framework debugging]
ms.assetid: 2d381ab1-7e7c-4281-af2b-e54d879b3ef8
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3b6e2d81680c2aa5973c0095a6a3ba7cfa158031
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanageddocumentgetdocumenttype-method"></a>ISymUnmanagedDocument::GetDocumentType, méthode
Obtient le type de document de ce document.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetDocumentType(  
    [out, retval] GUID*  pRetVal);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pRetVal`  
 [out] Pointeur vers une variable qui reçoit le type de document.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK si la méthode réussit.  
  
## <a name="see-also"></a>Voir aussi  
 [ISymUnmanagedDocument, interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
