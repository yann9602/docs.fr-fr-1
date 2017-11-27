---
title: "ISymENCUnmanagedMethod::GetLineFromOffset, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymENCUnmanagedMethod.GetLineFromOffset
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymENCUnmanagedMethod::GetLineFromOffset
helpviewer_keywords:
- GetLineFromOffset method [.NET Framework debugging]
- ISymENCUnmanagedMethod::GetLineFromOffset method [.NET Framework debugging]
ms.assetid: cc09bad2-fb34-4d13-a521-6ec7b1a1d915
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 2f18357b3a58a5409da93d4d2491997e9ca1cc70
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="isymencunmanagedmethodgetlinefromoffset-method"></a>ISymENCUnmanagedMethod::GetLineFromOffset, méthode
Obtient les informations de ligne associées à un offset. Si le paramètre d’offset (`dwOffset`) n’est pas un point de séquence, cette méthode obtient les informations de ligne associées à l’offset précédent.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetLineFromOffset(  
     [in]  ULONG32   dwOffset,  
     [out] ULONG32*  pline,  
     [out] ULONG32*  pcolumn,  
     [out] ULONG32*  pendLine,  
     [out] ULONG32*  pendColumn,  
     [out] ULONG32*  pdwStartOffset);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `dwOffset`  
 [in] Un `ULONG32` qui contient le décalage.  
  
 `pline`  
 [out] Un pointeur vers un `ULONG32` qui reçoit la ligne.  
  
 `pcolumn`  
 [out] Un pointeur vers un `ULONG32` qui reçoit la colonne.  
  
 `pendLine`  
 [out] Un pointeur vers un `ULONG32` qui reçoit la ligne de fin.  
  
 `pendColumn`  
 [out] Un pointeur vers un `ULONG32` qui reçoit la colonne de fin.  
  
 `pdwStartOffset`  
 [out] Un pointeur vers un `ULONG32` qui reçoit le point de séquence associé.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Voir aussi  
 [ISymENCUnmanagedMethod (Interface)](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)
