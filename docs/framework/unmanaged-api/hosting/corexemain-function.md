---
title: _CorExeMain, fonction
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: _CorExeMain
api_location:
- mscoree.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
api_type: DLLExport
f1_keywords: _CorExeMain
helpviewer_keywords: _CorExeMain function [.NET Framework hosting]
ms.assetid: 898f76e2-16f4-4a63-b7d9-dad2d3824d8a
topic_type: apiref
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5f5c0909db10c7bf8e15a7af998b78e0a193a908
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="corexemain-function"></a>_CorExeMain, fonction
Initialise le common language runtime (CLR), recherche le point d’entrée managé dans l’en-tête CLR de l’assembly exécutable et commence l’exécution.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
__int32 STDMETHODCALLTYPE _CorExeMain ();  
```  
  
## <a name="remarks"></a>Notes  
 Cette fonction est appelée par le chargeur dans les processus créés à partir des assemblys exécutables managés. Pour les assemblys DLL, le chargeur appelle la [_CorDllMain](../../../../docs/framework/unmanaged-api/hosting/cordllmain-function.md) de fonction à la place.  
  
 Le chargeur du système d’exploitation appelle cette méthode, quelle que soit le point d’entrée spécifié dans le fichier image.  
  
 Dans Windows 98, Windows ME, Windows NT et Windows 2000, le `_CorExeMain` est appelée indirectement via une correction dans le chargeur du système d’exploitation. Dans tous les autres versions de Windows, il est appelé directement par le chargeur du système d’exploitation.  
  
 Pour plus d’informations, consultez la section Notes de la [_CorValidateImage](../../../../docs/framework/unmanaged-api/hosting/corvalidateimage-function.md) rubrique.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor.h  
  
 **Bibliothèque :** inclus en tant que ressource dans MsCorEE.dll  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions statiques globales des métadonnées](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
