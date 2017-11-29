---
title: "ICorDebugProcess::IsTransitionStub, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess.IsTransitionStub
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess::IsTransitionStub
helpviewer_keywords:
- ICorDebugProcess::IsTransitionStub method [.NET Framework debugging]
- IsTransitionStub method [.NET Framework debugging]
ms.assetid: f7653317-7e48-4163-be03-f50f1a4b0f70
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 60f6e4116768d2d855edd941df796167754b3ab4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugprocessistransitionstub-method"></a>ICorDebugProcess::IsTransitionStub, méthode
Obtient une valeur qui indique si une adresse est à l’intérieur d’un stub qui provoquera une transition vers du code managé.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT IsTransitionStub(  
    [in]  CORDB_ADDRESS address,  
    [out] BOOL *pbTransitionStub);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `address`  
 [in] A `CORDB_ADDRESS` valeur qui spécifie l’adresse en question.  
  
 `pbTransitionStub`  
 [out] Un pointeur vers une valeur booléenne qui est `true` si l’adresse spécifiée est à l’intérieur d’un stub qui provoquera une transition vers du code managé ; sinon *`pbTransitionStub` est `false`.  
  
## <a name="remarks"></a>Remarques  
 Le `IsTransitionStub` méthode peut être utilisée par le code pas à pas non managé pour décider du moment retourner le contrôle de pas à pas pour l’exécution pas à pas géré.  
  
 Vous pouvez également les stubs de transition identité en examinant les informations contenues dans le fichier exécutable portable (PE).  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
