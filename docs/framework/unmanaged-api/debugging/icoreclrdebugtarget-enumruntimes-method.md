---
title: "Méthode ICoreClrDebugTarget::EnumRuntimes"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICoreClrDebugTarget.EnumRuntimes
api_location: mscordbi_macx86.dll
api_type: COM
f1_keywords: ICoreClrDebugTarget::EnumRuntimes
helpviewer_keywords:
- remote debugging API [Silverlight]
- ICorClrDebugTarget::EnumRuntimes method [Silverlight debugging]
- EnumRuntimes method, ICoreClrDebugTarget interface [Silverlight debugging]
- Silverlight, remote debugging
ms.assetid: 316df866-442d-40cc-b049-45e8adcb65d1
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d28e5f3f529f72607e2ddd84789e89f82dcdaba0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icoreclrdebugtargetenumruntimes-method"></a>Méthode ICoreClrDebugTarget::EnumRuntimes
Énumère les CLR (Common Language Runtime) dans le processus spécifié en cours d'exécution sur un ordinateur distant.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT EnumRuntimes (  
      [in] DWORD       dwInternalProcessID,  
      [out] DWORD*     pcRuntimes,  
      [out] CoreClrDebugRuntimeInfo**    ppRuntimes  
    );  
```  
  
#### <a name="parameters"></a>Paramètres  
 `dwInternalProcessID`  
 [in] ID de processus interne du processus pour lequel vous souhaitez énumérer les runtimes. Il s’agit de `m_dwInternalID` correspondant [CoreClrDebugProcInfo](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugprocinfo-structure.md).  
  
 `pcRuntimes`  
 [out] Nombre de runtimes retournés dans `ppRuntimes`. Cette valeur peut être égale à 0 (zéro).  
  
 `ppRuntimes`  
 [out] Un tableau de [CoreClrDebugRuntimeInfo](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugruntimeinfo-structure.md) des structures qui représentent les runtimes chargement dans le processus distant cible.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK  
 Opération réussie.  
  
 S_FALSE  
 `dwInternalProcessID` ne correspond à aucun processus qui s'exécute sur l'ordinateur, probablement parce que le processus a été arrêté. `pcRuntimes` et `ppRuntimes` sont null.  
  
 E_OUTOFMEMORY  
 Impossible d'allouer suffisamment de mémoire pour `ppRuntimes`.  
  
 E_FAIL (ou autres codes de retour E_)  
 Autres échecs.  
  
## <a name="remarks"></a>Remarques  
 Pour libérer la mémoire allouée par cette méthode, appelez le [ICoreClrDebugTarget::FreeMemory](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-freememory-method.md) (méthode).  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CoreClrRemoteDebuggingInterfaces.h  
  
 **Bibliothèque :** mscordbi_macx86.dll  
  
 **Versions du .NET framework :** 3.5 SP1  
  
## <a name="see-also"></a>Voir aussi  
 [ICoreClrDebugTarget (Interface)](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md)
