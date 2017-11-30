---
title: "ISymUnmanagedSymbolSearchInfo::GetSearchPath, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedSymbolSearchInfo.GetSearchPath
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedSymbolSearchInfo::GetSearchPath
helpviewer_keywords:
- GetSearchPath method [.NET Framework debugging]
- ISymUnmanagedSymbolSearchInfo::GetSearchPath method [.NET Framework debugging]
ms.assetid: b588d470-53c2-4492-be8c-957323eaca0b
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c896c8bc8aa852fb69f182e484243a0c379e0a1e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedsymbolsearchinfogetsearchpath-method"></a>ISymUnmanagedSymbolSearchInfo::GetSearchPath, méthode
Obtient le chemin de recherche.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetSearchPathLength(  
    [out] ULONG32 *pcchPath);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pcchPath`  
 [out] Un pointeur vers un `ULONG32` qui reçoit la taille, en caractères, de la mémoire tampon requise pour contenir le chemin de recherche.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Voir aussi  
 [ISymUnmanagedSymbolSearchInfo (Interface)](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-interface.md)
