---
title: "ICLRDataTarget::SetThreadContext, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDataTarget.SetThreadContext
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICLRDataTarget::SetThreadContext
helpviewer_keywords:
- SetThreadContext method, ICLRDataTarget interface [.NET Framework debugging]
- ICLRDataTarget::SetThreadContext method [.NET Framework debugging]
ms.assetid: 103c8502-81fe-40d7-9c1e-9008d8fb19e1
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e51cbafda76933d58bd60be8db7dd163a2dd59d3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="iclrdatatargetsetthreadcontext-method"></a>ICLRDataTarget::SetThreadContext, méthode
Définit le contexte actuel du thread spécifié dans le processus cible. Cette méthode est appelée par les services d’accès données common language runtime (CLR).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SetThreadContext (  
    [in] ULONG32            threadID,  
    [in] ULONG32            contextSize,  
    [in, size_is(contextSize)]   
         BYTE               *context  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `threadID`  
 [in] L’identificateur de système d’exploitation d’un thread dans le processus cible.  
  
 `contextSize`  
 [in] La taille du contexte.  
  
 `context`  
 [in] Pointeur vers une mémoire tampon contenant le contexte.  
  
 Les données dans le `context` tampon doivent être dans le format de Win32 `CONTEXT` structure. Le contexte spécifie des données de Registre spécifiques au processeur, la définition de Win32 `CONTEXT` structure varie selon l’architecture du processeur. Consultez le fichier d’en-tête WinNT.h pour la définition de Win32 `CONTEXT` structure.  
  
## <a name="remarks"></a>Remarques  
 Cette méthode est implémentée par le writer de l'application de débogage.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** ClrData.idl, ClrData.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [ICLRDataTarget (Interface)](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
