---
title: "ICorDebugHeapValue2::CreateHandle, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugHeapValue2.CreateHandle
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugHeapValue2::CreateHandle
helpviewer_keywords:
- CreateHandle method [.NET Framework debugging]
- ICorDebugHeapValue2::CreateHandle method [.NET Framework debugging]
ms.assetid: fbc418e8-fa22-420d-84ec-e0e1800db041
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: eeef3215c3740cdaa7d1b78b73fde9e76d7b40c5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugheapvalue2createhandle-method"></a>ICorDebugHeapValue2::CreateHandle, méthode
Crée un handle du type spécifié pour la valeur de tas représentée par cet objet ICorDebugHeapValue2.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT CreateHandle (  
    [in] CorDebugHandleType      type,   
    [out] ICorDebugHandleValue   **ppHandle  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `type`  
 [in] Valeur de l’énumération CorDebugHandleType qui spécifie le type de handle doit être créé.  
  
 `ppHandle`  
 [out] Pointeur vers l’adresse d’un objet ICorDebugHandleValue qui représente le nouveau handle pour cette valeur de tas.  
  
## <a name="remarks"></a>Notes  
 Le handle sera créé dans le domaine d’application qui est associé à la valeur du segment de mémoire et n’est plus valide si le domaine d’application est déchargé.  
  
 Plusieurs appels à cette fonction pour la même valeur de tas créent plusieurs handles. Étant donné que les handles influent sur les performances du garbage collector, le débogueur doit se limiter à un petit nombre de handles (environ 256) qui sont actifs à la fois.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
