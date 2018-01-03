---
title: "ISymUnmanagedMethod::GetRanges, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedMethod.GetRanges
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedMethod::GetRanges
helpviewer_keywords:
- ISymUnmanagedMethod::GetRanges method [.NET Framework debugging]
- GetRanges method [.NET Framework debugging]
ms.assetid: a85283d8-379c-417a-9736-ddeeef9bcf50
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1e17b411e39e522006092d79380566484f8fab67
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedmethodgetranges-method"></a>ISymUnmanagedMethod::GetRanges, méthode
Une position donnée dans un document, retourne un tableau de début et fin paires d’offsets qui correspondent aux plages de langage intermédiaire Microsoft (MSIL) qui traite de la position au sein de cette méthode. Le tableau est un tableau d’entiers et a le format [début, fin, début, fin]. Le nombre de paires de plage est la longueur du tableau divisée par 2.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetRanges(  
    [in]  ISymUnmanagedDocument* document,  
    [in]  ULONG32                line,  
    [in]  ULONG32                column,  
    [in]  ULONG32                cRanges,  
    [out] ULONG32                *pcRanges,  
    [out, size_is(cRanges),  
        length_is(*pcRanges)] ULONG32 ranges[]);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `document`  
 [in] Le document pour lequel l’offset est demandé.  
  
 `line`  
 [in] Ligne du document correspondant aux plages.  
  
 `column`  
 [in] Colonne du document correspondant aux plages.  
  
 `cRanges`  
 [in] Taille du tableau `ranges`.  
  
 `pcRanges`  
 [out] Un pointeur vers un `ULONG32` qui reçoit la taille de la mémoire tampon requise pour contenir les plages.  
  
 `ranges`  
 [out] Pointeur vers la mémoire tampon qui reçoit les plages.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Voir aussi  
 [ISymUnmanagedMethod, interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
