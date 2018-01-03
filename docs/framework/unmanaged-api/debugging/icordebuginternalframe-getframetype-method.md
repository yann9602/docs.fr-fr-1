---
title: "ICorDebugInternalFrame::GetFrameType, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugInternalFrame.GetFrameType
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugInternalFrame::GetFrameType
helpviewer_keywords:
- GetFrameType method [.NET Framework debugging]
- ICorDebugInternalFrame::GetFrameType method [.NET Framework debugging]
ms.assetid: da278a29-dc2e-4bf7-96ce-801bdc4d7025
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 476903ae8f1461a46d685bc3e549c3b6553d5c68
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebuginternalframegetframetype-method"></a>ICorDebugInternalFrame::GetFrameType, méthode
Obtient le type de ce frame interne.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetFrameType (  
    [out] CorDebugInternalFrameType  *pType  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pType`  
 [out] Un pointeur vers une valeur de l’énumération CorDebugInternalFrameType qui indique le type de frame interne représenté par cet `ICorDebugInternalFrame` objet.  
  
## <a name="remarks"></a>Notes  
 Le type de frame interne ne sera jamais STUBFRAME_NONE. Débogueurs en douceur doivent ignorer les types de frame interne non reconnu.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
