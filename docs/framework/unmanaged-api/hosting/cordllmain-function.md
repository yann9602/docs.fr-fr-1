---
title: _CorDllMain, fonction
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: _CorDllMain
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: _CorDllMain
helpviewer_keywords: _CorDllMain function [.NET Framework hosting]
ms.assetid: bc7b51cf-39d3-48ec-a5cb-2f179fbefff8
topic_type: apiref
caps.latest.revision: "23"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 985f2284026054217671de767c316b1fba35c098
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="cordllmain-function"></a>_CorDllMain, fonction
Initialise le common language runtime (CLR), recherche le point d’entrée managé dans l’en-tête CLR de l’assembly DLL et commence l’exécution.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
BOOL STDMETHODCALLTYPE _CorDllMain (  
   [in] HINSTANCE hInst,  
   [in] DWORD     dwReason,  
   [in] LPVOID    lpReserved  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `hInst`  
 [in] Le handle d’instance du module chargé.  
  
 `dwReason`  
 [in] Indique la raison pour laquelle la fonction de point d’entrée DLL est appelée. Ce paramètre peut prendre l’une des valeurs suivantes : DLL_PROCESS_ATTACH, DLL_THREAD_ATTACH, DLL_THREAD_ATTACH ou DLL_PROCESS_DETACH. Pour obtenir une description de ces valeurs, consultez le `DllMain` documentation dans le Kit de développement de plate-forme.  
  
 `lpReserved`  
 [in] Non utilisé.  
  
## <a name="return-value"></a>Valeur de retour  
 Cette méthode retourne `true` de réussite et `false` si une erreur se produit.  
  
## <a name="remarks"></a>Notes  
 Cette fonction est appelée par le chargeur du système d’exploitation pour les assemblys de DLL. Pour les assemblys exécutables, le chargeur appelle la [_CorExeMain](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md) de fonction à la place.  
  
 Le chargeur du système d’exploitation appelle cette méthode, quelle que soit le point d’entrée spécifié dans le fichier DLL.  
  
 Dans Windows 98, Windows ME, Windows NT et Windows 2000, le `_CorDllMain` fonction est appelée indirectement via une fixupin le chargeur du système d’exploitation. Dans tous les autres versions de Windows, il est appelé directement par le chargeur du système d’exploitation.  
  
 Pour plus d’informations, consultez la section Notes de la [_CorValidateImage](../../../../docs/framework/unmanaged-api/hosting/corvalidateimage-function.md) rubrique.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor.h  
  
 **Bibliothèque :** inclus en tant que ressource dans MsCorEE.dll  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions statiques globales des métadonnées](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
