---
title: "ICorDebugArrayValue::GetElement, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugArrayValue.GetElement
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugArrayValue::GetElement
helpviewer_keywords:
- GetElement method [.NET Framework debugging]
- ICorDebugArrayValue::GetElement method [.NET Framework debugging]
ms.assetid: 7ac3cba5-c282-402e-b7ef-b46634f5176b
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9aba987aa6f806bfe1608e081aac4cb501cd23fc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugarrayvaluegetelement-method"></a>ICorDebugArrayValue::GetElement, méthode
Obtient la valeur de l’élément de tableau donné.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetElement (  
    [in]  ULONG32          cdim,  
    [in, size_is(cdim), length_is(cdim)]   
         ULONG32           indices[],  
    [out] ICorDebugValue   **ppValue  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `cdim`  
 [in] Le nombre de dimensions de ce `ICorDebugArrayValue` objet.  
  
 Cette valeur est également la taille de la `indices` , car sa taille est égale au nombre de dimensions de la `ICorDebugArrayValue` objet.  
  
 `indices`  
 [in] Un tableau de valeurs d’index, dont chacun spécifie une position dans une dimension de la `ICorDebugArrayValue` objet.  
  
 Cette valeur ne doit pas être null.  
  
 `ppValue`  
 [out] Pointeur vers l’adresse d’un objet ICorDebugValue qui représente la valeur de l’élément spécifié.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
