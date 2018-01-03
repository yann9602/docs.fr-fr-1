---
title: Fonction CreateInstallReferenceEnum
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CreateInstallReferenceEnum
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type: DLLExport
f1_keywords: CreateInstallReference
helpviewer_keywords: CreateInstallReference function [.NET Framework fusion]
ms.assetid: 80dbbbf8-54fc-4894-b74a-0179d3201083
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a0c902cf5d9d8b6295cab95552aae6775c5bf889
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="createinstallreferenceenum-function"></a>Fonction CreateInstallReferenceEnum
Obtient un pointeur vers un [IInstallReferenceEnum](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md) instance qui représente une liste de références d’une application à l’assembly spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT CreateInstallReferenceEnum (  
    [out] IInstallReferenceEnum **ppRefEnum,  
    [in]  IAssemblyName         *pName,  
    [in]  DWORD                 dwFlags,  
    [in]  LPVOID                pvReserved  
 );  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppRefEnum`  
 [out] Retourné `IInstallReferenceEnum` pointeur.  
  
 `pName`  
 [in] Le [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) qui identifie l’assembly pour lequel énumérer des références.  
  
 `dwFlags`  
 [in] Indicateurs qui influencent le comportement de l’énumérateur.  
  
 `pvReserved`  
 [in] Réservé pour une future extensibilité. `pvReserved`doit être une référence null.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Fusion.h  
  
 **Bibliothèque :** Fusion.dll et Mscorwks.dll. Utilisez le fichier Fusion.dll plutôt que Mscorwks.dll pour garantir que vous ciblez la version appropriée du .NET Framework.  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [IInstallReferenceEnum, interface](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md)  
 [IAssemblyName, interface](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)  
 [Fonctions statiques globales de fusion](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
