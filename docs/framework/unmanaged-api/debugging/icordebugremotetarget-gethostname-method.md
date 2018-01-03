---
title: "ICorDebugRemoteTarget::GetHostName, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugRemoteTarget.GetHostName
api_location: CorDebug.dll
api_type: COM
f1_keywords: ICorDebugRemoteTarget::GetHostName
helpviewer_keywords:
- ICorDebugRemoteTarget::GetHostName method [.NET Framework debugging]
- GetHostName method, ICorDebugRemoteTarget interface [.NET Framework debugging]
ms.assetid: 1c7276f7-7e54-470c-808c-e13745ac07a1
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 45fa4afebda00cb2549a5c18ba81c6bb4e8210e0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugremotetargetgethostname-method"></a>ICorDebugRemoteTarget::GetHostName, méthode
Retourne le nom de domaine complet ou l’adresse IPv4 de l’ordinateur cible de débogage distant. IPv6 n’est pas pris en charge pour l’instant.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetHostName (  
    [in] ULONG32      cchHostName,  
    [out] ULONG32*    pcchHostName,  
    [out, size_is(cchHostName), length_is(*pcchHostName)]  
            WCHAR szHostName[]  
```  
  
#### <a name="parameters"></a>Paramètres  
 `cchHostName`  
 [in] La taille, en caractères, de la `szHostName` mémoire tampon. Si ce paramètre est 0 (zéro), `szHostName` doit être null.  
  
 `pcchHostName`  
 [out] Le nombre de caractères, y compris une marque de fin null, dans le nom d’hôte ou adresse IP. Ce paramètre peut avoir la valeur Null.  
  
 `szHostName`  
 [out] Mémoire tampon qui contient le nom d’hôte ou adresse IP.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK  
 Le nom d’hôte ou l’adresse IP a été retourné avec succès.  
  
 E_FAIL (ou autres codes de retour E_)  
 Impossible de retourner le nom d’hôte ou adresse IP.  
  
## <a name="remarks"></a>Notes  
 Cette méthode est implémentée par le writer du débogueur. Elle doit suivre le paradigme appel plusieurs : sur le premier appel, l’appelant passe la valeur null à la fois aux `cchHostName` et `szHostName`, et `pcchHostName` retourne la taille de la mémoire tampon requise. Sur le deuxième appel, la taille qui a été retournée précédemment est passée dans `cchHostName`, et une mémoire tampon de taille appropriée est passé dans `szHostName`.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :** 3.5 SP1  
  
## <a name="see-also"></a>Voir aussi  
 [ICorDebugRemoteTarget, interface](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)  
 [ICorDebug, interface](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
