---
title: "ISymUnmanagedBinder3::GetReaderFromCallback, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedBinder3.GetReaderFromCallback
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedBinder3::GetReaderFromCallback
helpviewer_keywords:
- GetReaderFromCallback method [.NET Framework debugging]
- ISymUnmanagedBinder3::GetReaderFromCallback method [.NET Framework debugging]
ms.assetid: 4ef83bd2-3d8e-499e-8a12-d9d6fd6ced30
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5e748742c1c67df0b33818e3f6f3c5786e07c65f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedbinder3getreaderfromcallback-method"></a>ISymUnmanagedBinder3::GetReaderFromCallback, méthode
Permet à l’utilisateur d’implémenter ou de fournir via un rappel un `IID_IDiaReadExeAtRVACallback` ou `IID_IDiaReadExeAtOffsetCallback` pour obtenir les informations de répertoire de débogage à partir de la mémoire.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetReaderFromCallback(  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *fileName,  
    [in]  const WCHAR  *searchPath,  
    [in]  ULONG32      searchPolicy,  
    [in]  IUnknown     *callback,  
    [out,retval] ISymUnmanagedReader  **pRetVal);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `importer`  
 [in] Pointeur vers l’interface d’importation de métadonnées.  
  
 `fileName`  
 [in] Pointeur vers le nom de fichier.  
  
 `searchPath`  
 [in] Pointeur vers le chemin de recherche.  
  
 `searchPolicy`  
 [in] Une valeur de la [CorSymSearchPolicyAttributes](../../../../docs/framework/unmanaged-api/diagnostics/corsymsearchpolicyattributes-enumeration.md) énumération qui spécifie la stratégie à utiliser lorsque vous effectuez une recherche pour un lecteur de symboles.  
  
 `callback`  
 [in] Pointeur vers la fonction de rappel.  
  
 `pRetVal`  
 [out] Un pointeur qui est défini à le [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) interface.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** CorSym.idl  
  
## <a name="see-also"></a>Voir aussi  
 [ISymUnmanagedBinder3 (Interface)](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-interface.md)
