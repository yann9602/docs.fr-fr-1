---
title: "ISymUnmanagedScope::GetNamespaces, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedScope.GetNamespaces
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedScope::GetNamespaces
helpviewer_keywords:
- GetNamespaces method, ISymUnmanagedScope interface [.NET Framework debugging]
- ISymUnmanagedScope::GetNamespaces method [.NET Framework debugging]
ms.assetid: c44b0440-04bd-460a-84fb-41afecf44503
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 641ce6c4587f9f23743a3c1b5a1aeb6fb77edde7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedscopegetnamespaces-method"></a>ISymUnmanagedScope::GetNamespaces, méthode
Obtient les espaces de noms qui sont utilisés dans cette portée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetNamespaces(  
    [in]  ULONG32  cNameSpaces,  
    [out] ULONG32  *pcNameSpaces,  
    [out, size_is(cNameSpaces),  
        length_is(*pcNameSpaces)]  
        ISymUnmanagedNamespace* namespaces[]);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `cNameSpaces`  
 [in] Taille du tableau `namespaces`.  
  
 `pcNameSpaces`  
 [out] Un pointeur vers un `ULONG32` qui reçoit la taille de la mémoire tampon requise pour contenir les espaces de noms.  
  
 `namespaces`  
 [out] Tableau qui reçoit les espaces de noms.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Voir aussi  
 [ISymUnmanagedScope (Interface)](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)
