---
title: "ICorProfilerInfo::GetModuleInfo, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.GetModuleInfo
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::GetModuleInfo
helpviewer_keywords:
- GetModuleInfo method [.NET Framework profiling]
- ICorProfilerInfo::GetModuleInfo method [.NET Framework profiling]
ms.assetid: 5a90d16f-7929-4987-8f83-a631becf564d
topic_type: apiref
caps.latest.revision: "20"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a8309b57f2940805e23010feac17b6d37f1a58af
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfogetmoduleinfo-method"></a>ICorProfilerInfo::GetModuleInfo, méthode
Pour un ID de module donné, retourne le nom de fichier du module et l'ID de l'assembly parent du module.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetModuleInfo(  
    [in]  ModuleID   moduleId,  
    [out] LPCBYTE    *ppBaseLoadAddress,  
    [in]  ULONG      cchName,  
    [out] ULONG      *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
          WCHAR      szName[] ,  
    [out] AssemblyID *pAssemblyId);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `moduleId`  
 [in] ID du module pour lequel les informations sont récupérées.  
  
 `ppBaseLoadAddress`  
 [out] Adresse de base à laquelle le module est chargé.  
  
 `cchName`  
 [in] Longueur, en caractères, de la mémoire tampon de retour `szName`.  
  
 `pcchName`  
 [out] Pointeur vers la longueur de caractère totale du nom de fichier du module qui est retourné.  
  
 `szName`  
 [out] Mémoire tampon de caractères larges fournie par l'appelant. Suite au retour de la méthode, cette mémoire tampon contient le nom de fichier du module.  
  
 `pAssemblyId`  
 [out] Pointeur vers l'ID de l'assembly parent du module.  
  
## <a name="remarks"></a>Notes  
 Pour les modules dynamiques, le paramètre `szName` est une chaîne vide et l'adresse de base est 0 (zéro).  
  
 Bien que le `GetModuleInfo` méthode puisse être appelée dès que l’ID du module existe, l’ID de l’assembly parent ne sera pas disponible tant que le profileur reçoit le [ICorProfilerCallback::ModuleAttachedToAssembly](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleattachedtoassembly-method.md) rappel.  
  
 Suite au retour de `GetModuleInfo`, vous devez vérifier que la mémoire tampon `szName` est suffisamment grande pour contenir le nom de fichier complet du module. Pour ce faire, comparez la valeur vers laquelle `pcchName` pointe à celle du paramètre `cchName`. Si `pcchName` pointe vers une valeur supérieure à `cchName`, allouez une mémoire tampon `szName` plus grande, mettez à jour `cchName` pour refléter la nouvelle taille et rappelez `GetModuleInfo`.  
  
 Vous pouvez également commencer par appeler `GetModuleInfo` avec une mémoire tampon `szName` de longueur nulle pour obtenir la taille correcte de la mémoire tampon. Vous pouvez ensuite affecter à la taille de la mémoire tampon la valeur retournée dans `pcchName` et rappeler `GetModuleInfo`.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [ICorProfilerInfo, interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [Interfaces de profilage](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [Profilage](../../../../docs/framework/unmanaged-api/profiling/index.md)  
 [GetModuleInfo2, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getmoduleinfo2-method.md)
