---
title: "ISymUnmanagedReader::GetMethodsFromDocumentPosition, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedReader.GetMethodsFromDocumentPosition
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedReader::GetMethodsFromDocumentPosition
helpviewer_keywords:
- GetMethodsFromDocumentPosition method [.NET Framework debugging]
- ISymUnmanagedReader::GetMethodsFromDocumentPosition method [.NET Framework debugging]
ms.assetid: 83605f1e-e4f3-49e6-859b-f13cad68bb54
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cdf3762c40e5ec4da84a27ed7abcb15981b81379
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedreadergetmethodsfromdocumentposition-method"></a>ISymUnmanagedReader::GetMethodsFromDocumentPosition, méthode
Retourne un tableau de méthodes, chacune contenant le point d’arrêt à la position donnée dans un document.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetMethodsFromDocumentPosition (  
    [in]  ISymUnmanagedDocument* document,  
    [in]  ULONG32 line,  
    [in]  ULONG32 column,  
    [in]  ULONG32 cMethod,  
    [out] ULONG32* pcMethod,  
    [out, size_is (cMethod),  
        length_is (*pcMethod)] ISymUnmanagedMethod* pRetVal[]);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `document`  
 [in] Le document spécifié.  
  
 `line`  
 [in] La ligne du document spécifié.  
  
 `column`  
 [in] La colonne du document spécifié.  
  
 `cMethod`  
 [in] Taille du tableau `pRetVal`.  
  
 `pcMethod`  
 [out] Un pointeur vers une variable qui reçoit le nombre d’éléments retournés dans le `pRetVal` tableau.  
  
 `pRetVal`  
 [out] Un tableau de pointeurs, chacun pointant vers un [ISymUnmanagedMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md) objet qui représente une méthode qui contient le point d’arrêt.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Voir aussi  
 [ISymUnmanagedReader, interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
