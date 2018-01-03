---
title: "ICorDebugThread2::GetActiveFunctions, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread2.GetActiveFunctions
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread2::GetActiveFunctions
helpviewer_keywords:
- GetActiveFunctions method [.NET Framework debugging]
- ICorDebugThread2::GetActiveFunctions method [.NET Framework debugging]
ms.assetid: 27fae01a-ecec-423a-973e-24f8de55826c
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ecd9446f642011b21f784019f583f49e3a70433a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugthread2getactivefunctions-method"></a>ICorDebugThread2::GetActiveFunctions, méthode
Obtient des informations sur la fonction active dans chacun des frames de ce thread.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetActiveFunctions (  
    [in]   ULONG32             cFunctions,  
    [out]  ULONG32             *pcFunctions,  
    [in, out, size_is(cFunctions), length_is(*pcFunctions)]  
        COR_ACTIVE_FUNCTION    pFunctions[]  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `cFunctions`  
 [in] Taille du tableau `pFunctions`.  
  
 `pcFunctions`  
 [out] Un pointeur vers le nombre d’objets retournés dans le `pFunctions` tableau. Le nombre d’objets renvoyés est égal au nombre de frames managés sur la pile.  
  
 `pFunctions`  
 [dans, out] Tableau d’objets COR_ACTIVE_FUNCTION, dont chacun contient des informations sur les fonctions actives dans les frames de ce thread.  
  
 Le premier élément sera utilisé pour le frame terminal et ainsi de suite jusqu’à la racine de la pile.  
  
## <a name="remarks"></a>Notes  
 Si `pFunctions` a la valeur null en entrée, `GetActiveFunctions` retourne uniquement le nombre de fonctions qui se trouvent sur la pile. Autrement dit, si `pFunctions` a la valeur null en entrée, `GetActiveFunctions` retourne une valeur uniquement dans `pcFunctions`.  
  
 Le `GetActiveFunctions` méthode est une optimisation sur l’obtention des informations mêmes des frames dans une trace de pile et inclut uniquement les frames qui auraient eu un objet ICorDebugILFrame pour eux dans la trace de pile complet.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
