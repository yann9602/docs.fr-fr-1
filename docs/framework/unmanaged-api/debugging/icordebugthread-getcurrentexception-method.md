---
title: "ICorDebugThread::GetCurrentException, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread.GetCurrentException
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread::GetCurrentException
helpviewer_keywords:
- ICorDebugThread::GetCurrentException method [.NET Framework debugging]
- GetCurrentException method [.NET Framework debugging]
ms.assetid: 331ed465-a195-4359-8584-b82c6098b29b
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c18e2dfa68d425e5ec23d4573428018bc971f8b2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugthreadgetcurrentexception-method"></a>ICorDebugThread::GetCurrentException, méthode
Obtient un pointeur d’interface vers un objet ICorDebugValue qui représente une exception levée par le code managé.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetCurrentException (  
    [out] ICorDebugValue **ppExceptionObject  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppExceptionObject`  
 [out] Un pointeur vers l’adresse d’un `ICorDebugValue` objet qui représente l’exception levée par le code managé.  
  
## <a name="remarks"></a>Notes  
 L’objet exception existe à partir de l’heure de l’exception est levée jusqu'à la fin de la `catch` bloc. Une évaluation de fonction, qui est effectuée par les méthodes ICorDebugEval, efface l’objet exception sur le programme d’installation et restaurez-la à la fin.  
  
 Les exceptions peuvent être imbriquées (par exemple, si une exception est levée dans un filtre ou dans une évaluation de fonction), afin qu’il peut y avoir plusieurs exceptions en attente sur un thread unique. `GetCurrentException`Retourne l’exception la plus récente.  
  
 L’objet exception et le type peuvent changer pendant toute la vie de l’exception. Par exemple, après qu’une exception de type x est levée, le common language runtime (CLR) peut manquer de mémoire et promouvoir en une exception de mémoire insuffisante.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
