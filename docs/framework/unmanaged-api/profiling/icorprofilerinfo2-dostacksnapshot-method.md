---
title: "ICorProfilerInfo2::DoStackSnapshot, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo2.DoStackSnapshot
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo2::DoStackSnapshot
helpviewer_keywords:
- ICorProfilerInfo2::DoStackSnapshot method [.NET Framework profiling]
- DoStackSnapshot method [.NET Framework profiling]
ms.assetid: 287b11e9-7c52-4a13-ba97-751203fa97f4
topic_type: apiref
caps.latest.revision: "25"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 6a210fc0c1984ee9bc77114ba30c3287ae43b169
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo2dostacksnapshot-method"></a>ICorProfilerInfo2::DoStackSnapshot, méthode
Parcourt les frames managés sur la pile pour le thread spécifié et envoie des informations au profileur via un rappel.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT DoStackSnapshot(  
    [in] ThreadID thread,  
    [in] StackSnapshotCallback *callback,  
    [in] ULONG32 infoFlags,  
    [in] void *clientData,  
    [in, size_is(contextSize), length_is(contextSize)] BYTE context[],  
    [in] ULONG32 contextSize);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `thread`  
 [in] L’ID du thread cible.  
  
 En passant null dans `thread` produit un instantané du thread actuel. Si un `ThreadID` d’un autre thread est passé, le common language runtime (CLR) suspend ce thread, exécute l’instantané et reprend.  
  
 `callback`  
 [in] Un pointeur vers l’implémentation de la [StackSnapshotCallback](../../../../docs/framework/unmanaged-api/profiling/stacksnapshotcallback-function.md) méthode, qui est appelée par le CLR pour fournir au profileur des informations sur chaque frame managé et chaque exécution de frames non managés.  
  
 Le `StackSnapshotCallback` méthode est implémentée par le writer de profileur.  
  
 `infoFlags`  
 [in] Une valeur de la [COR_PRF_SNAPSHOT_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-snapshot-info-enumeration.md) énumération qui spécifie la quantité de données à renvoyer pour chaque frame par `StackSnapshotCallback`.  
  
 `clientData`  
 [in] Un pointeur vers les données client, qui sont transmises directement à la `StackSnapshotCallback` fonction de rappel.  
  
 `context`  
 [in] Un pointeur vers un Win32 `CONTEXT` structure, qui est utilisé pour amorcer le parcours de pile. Win32 `CONTEXT` structure contient des valeurs des registres du processeur et représente l’état de l’UC à un moment donné dans le temps.  
  
 La valeur de départ aide le CLR à déterminer où commencer le parcours de pile, si le haut de la pile est un code non managé d’assistance ; Sinon, la valeur de départ est ignorée. Une valeur de départ doit être fournie pour un parcours asynchrone. Si vous effectuez un parcours synchrone, aucune valeur de départ n’est nécessaire.  
  
 Le `context` paramètre est valide uniquement si l’indicateur COR_PRF_SNAPSHOT_CONTEXT a été passé dans le `infoFlags` paramètre.  
  
 `contextSize`  
 [in] La taille de la `CONTEXT` structure, ce qui est référencé par le `context` paramètre.  
  
## <a name="remarks"></a>Remarques  
 Le passage de null pour `thread` produit un instantané du thread actuel. Les instantanés peuvent provenir d’autres threads uniquement si le thread cible est interrompu à la fois.  
  
 Lorsque le profileur souhaite parcourir la pile, il appelle `DoStackSnapshot`. Avant que le CLR est retournée à partir de cet appel, il appelle votre `StackSnapshotCallback` plusieurs fois, une fois pour chaque frame managé (ou exécution de frames non managés) sur la pile. Lorsque des frames non managés sont trouvés, vous devez vous-même les parcourir.  
  
 L’ordre dans lequel la pile est parcourue est l’inverse de la façon dont les images ont été placés sur la pile : Terminal (dernier push) en premier lieu, le principal (premier push) image dernier.  
  
 Pour plus d’informations sur la façon de programmer le profileur pour parcourir des piles managées, consultez [parcours de la pile du profileur dans .NET Framework 2.0 : notions de base et d’autres fonctionnalités](http://go.microsoft.com/fwlink/?LinkId=73638).  
  
 Un parcours de pile peut être synchrone ou asynchrone, comme expliqué dans les sections suivantes.  
  
## <a name="synchronous-stack-walk"></a>Parcours de pile synchrone  
 Un parcours de pile synchrone implique le parcours de la pile du thread actuel en réponse à un rappel. Il ne nécessite pas d’amorçage ou à suspendre.  
  
 Vous apportez synchrone, appelez en réponse à l’appel d’une de du votre profileur CLR [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) (ou [ICorProfilerCallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)) méthodes, vous appelez `DoStackSnapshot` pour parcourir la pile de la thread en cours. Cela est utile lorsque vous souhaitez voir à quoi la pile ressemble à une notification comme [ICorProfilerCallback::ObjectAllocated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectallocated-method.md). Vous appelez uniquement `DoStackSnapshot` depuis votre `ICorProfilerCallback` méthode, en passant null dans les `context` et `thread` paramètres.  
  
## <a name="asynchronous-stack-walk"></a>Parcours de pile asynchrone  
 Un parcours de pile asynchrone implique le parcours de la pile d’un autre thread ou de parcourir la pile du thread actuel, pas en réponse à un rappel, mais par piratage du pointeur d’instruction du thread actuel. Un parcours asynchrone requiert une valeur initiale si le haut de la pile est le code non managé qui ne fait pas partie d’une plateforme de code non managé (PInvoke) ou appel COM, mais code d’assistance dans le CLR lui-même. Par exemple, le code qui effectue juste-à-temps (JIT) la compilation ou le garbage collection est code d’assistance.  
  
 Vous obtenez une valeur de départ en directement en suspendant le thread cible et parcourez sa pile vous-même, jusqu'à ce que vous trouviez le tout premier frame managé. Une fois que le thread cible est suspendu, obtenir le contexte de Registre actuel du thread cible. Ensuite, déterminez si le contexte de Registre pointe au code non managé en appelant [ICorProfilerInfo::GetFunctionFromIP](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getfunctionfromip-method.md) , si elle retourne un `FunctionID` égale à zéro, le frame est de code non managé. Maintenant, parcourez la pile jusqu'à ce que le premier frame managé, puis calculez le contexte de la valeur initiale basé sur le contexte de Registre pour ce frame.  
  
 Appelez `DoStackSnapshot` avec votre contexte de valeur de départ pour commencer le parcours de pile asynchrone. Si vous ne fournissez pas d’une valeur initiale, `DoStackSnapshot` peut ignorer les frames managés en haut de la pile et, par conséquent, vous donne un parcours de pile incomplet. Si vous fournissez une valeur initiale, elle doit pointer vers la compilation JIT ou Native Image Generator (Ngen.exe)-généré le code ; dans le cas contraire, `DoStackSnapshot` renvoie le code d’échec CORPROF_E_STACKSNAPSHOT_UNMANAGED_CTX.  
  
 Parcours de pile asynchrones peuvent facilement provoquer des blocages ou violations d’accès, sauf si vous suivez ces instructions :  
  
-   Lorsque vous interrompez directement des threads, n’oubliez pas que seul un thread qui n’a jamais exécuté du code managé peut suspendre un autre thread.  
  
-   Bloquez toujours dans votre [ICorProfilerCallback::ThreadDestroyed](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threaddestroyed-method.md) rappel jusqu'à ce que le parcours de pile de ce thread est terminé.  
  
-   Ne contiennent pas un verrou pendant que votre profileur appelle une fonction CLR qui peut déclencher une garbage collection. Autrement dit, ne détiennent pas de verrou si le thread propriétaire peut effectuer un appel qui déclenche un garbage collection.  
  
 Il existe également un risque d’interblocage si vous appelez `DoStackSnapshot` à partir d’un thread que votre profileur a créé afin que vous pouvez parcourir la pile d’un thread cible distinct. La première fois que le thread que vous avez créé entre certaines `ICorProfilerInfo*` méthodes (y compris `DoStackSnapshot`), le CLR exécute une initialisation par thread, spécifique au CLR sur ce thread. Si votre profileur a interrompu le thread cible dont vous essayez de parcourir la pile, et si ce thread cible est produit qu’il possède un verrou nécessaires pour effectuer cette initialisation par thread, un interblocage se produit. Pour éviter cet interblocage, faites un appel initial à `DoStackSnapshot` depuis votre thread créés par le profileur pour parcourir thread cible distinct, mais n’interrompez pas le thread cible au préalable. Cet appel initial garantit que l’initialisation par thread peut s’effectuer sans blocage. Si `DoStackSnapshot` réussit et signale au moins une frame, après ce point, il sera sécurisé pour interrompre tout thread cible et l’appel de ce thread créés par le Générateur de profils `DoStackSnapshot` pour parcourir la pile de ce thread cible.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [ICorProfilerInfo (Interface)](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [ICorProfilerInfo2 (Interface)](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
