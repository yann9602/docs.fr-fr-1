---
title: "ISymUnmanagedReader::GetSymAttribute, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedReader.GetSymAttribute
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedReader::GetSymAttribute
helpviewer_keywords:
- GetSymAttribute method [.NET Framework debugging]
- ISymUnmanagedReader::GetSymAttribute method [.NET Framework debugging]
ms.assetid: c675ce7e-76e7-45ff-8273-3b6489a2767c
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9795d5c7937f3c66c799665ba0e07e70c2be0b66
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedreadergetsymattribute-method"></a>ISymUnmanagedReader::GetSymAttribute, méthode
Obtient un attribut personnalisé en fonction de son nom. Contrairement aux attributs personnalisés des métadonnées, ces attributs personnalisés sont conservés dans le magasin de symboles.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetSymAttribute (  
    [in]  mdToken  parent,  
    [in]  WCHAR    *name,  
    [in]  ULONG32  cBuffer,  
    [out] ULONG32  *pcBuffer,  
    [out, size_is (cBuffer),  
        length_is (*pcBuffer)] BYTE buffer[]);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `parent`  
 [in] Le jeton de métadonnées pour l’objet pour lequel l’attribut est demandé.  
  
 `name`  
 [in] Pointeur vers la variable qui indique l’attribut à récupérer.  
  
 `cBuffer`  
 [in] Taille du tableau `buffer`.  
  
 `pcBuffer`  
 [out] Pointeur vers la variable qui reçoit la longueur des données d’attribut.  
  
 `buffer`  
 [out] Pointeur vers la variable qui reçoit les données d’attribut.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur...  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Voir aussi  
 [ISymUnmanagedReader, interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
