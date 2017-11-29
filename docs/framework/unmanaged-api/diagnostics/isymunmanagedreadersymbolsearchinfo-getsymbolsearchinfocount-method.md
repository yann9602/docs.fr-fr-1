---
title: "ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfoCount, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedReaderSymbolSearchInfo.GetSymbolSearchInfoCount
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfoCount
helpviewer_keywords:
- GetSymbolSearchInfoCount method [.NET Framework debugging]
- ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfoCount method [.NET Framework debugging]
ms.assetid: 4068b6ec-525f-4446-8818-0296178cbd19
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 99ee3e5a2d1f5987377ed7ac224c821cb0906757
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedreadersymbolsearchinfogetsymbolsearchinfocount-method"></a>ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfoCount, méthode
Obtient le nombre d’informations de la recherche de symbole.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetSymbolSearchInfoCount(  
    [out] ULONG32 *pcSearchInfo);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pcSearchInfo`  
 [] out] pointeur vers un `ULONG32` qui reçoit la taille de la mémoire tampon requise pour contenir les informations de recherche.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Voir aussi  
 [ISymUnmanagedReaderSymbolSearchInfo (Interface)](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreadersymbolsearchinfo-interface.md)
