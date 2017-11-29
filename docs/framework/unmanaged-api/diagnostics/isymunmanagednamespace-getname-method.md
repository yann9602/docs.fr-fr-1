---
title: "ISymUnmanagedNamespace::GetName, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedNamespace.GetName
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedNamespace::GetName
helpviewer_keywords:
- ISymUnmanagedNamespace::GetName method [.NET Framework debugging]
- GetName method, ISymUnmanagedNamespace interface [.NET Framework debugging]
ms.assetid: 657bf91d-005a-4ea4-9298-04d1291c0bc3
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: abb21c7d5f239b19396d3182b97d9502cfa3da15
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagednamespacegetname-method"></a>ISymUnmanagedNamespace::GetName, méthode
Obtient le nom de cet espace de noms.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetName(  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
        length_is(*pcchName)] WCHAR szName[]);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `cchName`  
 [in] A `ULONG32` qui indique la taille de la `szName` mémoire tampon.  
  
 `pcchName`  
 [out] Un pointeur vers un `ULONG32` qui reçoit la taille, en caractères, de la mémoire tampon requise pour contenir le nom de l’espace de noms, y compris le caractère null de fin.  
  
 `szName`  
 [out] Pointeur vers une mémoire tampon qui contient le nom de l’espace de noms.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Voir aussi  
 [ISymUnmanagedNamespace (Interface)](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md)
