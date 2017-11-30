---
title: "ISymUnmanagedReader2::GetMethodByVersionPreRemap, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedReader2.GetMethodByVersionPreRemap
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedReader2::GetMethodByVersionPreRemap
helpviewer_keywords:
- GetMethodByVersionPreRemap method [.NET Framework debugging]
- ISymUnmanagedReader2::GetMethodByVersionPreRemap method [.NET Framework debugging]
ms.assetid: 0d144ed4-bdb0-4cac-960c-cb90f4dca173
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 69a203424320a176cd285c23d98111e71709042a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedreader2getmethodbyversionpreremap-method"></a>ISymUnmanagedReader2::GetMethodByVersionPreRemap, méthode
Obtient une méthode de lecteur de symboles, en fonction d’un jeton de méthode et un numéro de version modifier et continuer. Numéros de version commencent à 1 et sont incrémentés à chaque fois que la méthode est modifiée à la suite d’une opération modifier et continuer.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetMethodByVersionPreRemap(  
    [in]  mdMethodDef token,  
    [in]  int version,  
    [out, retval] ISymUnmanagedMethod** pRetVal);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `token`  
 [in] Le jeton de métadonnées de méthode.  
  
 `version`  
 [in] La version de la méthode.  
  
 `pRetVal`  
 [out] Un pointeur vers retourné [ISymUnmanagedMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md) interface.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** CorSym.idl. CorSym.h  
  
## <a name="see-also"></a>Voir aussi  
 [ISymUnmanagedReader2 (Interface)](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-interface.md)
