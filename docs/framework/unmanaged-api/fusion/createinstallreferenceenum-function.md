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
ms.openlocfilehash: 07c7ec72a66b37798e6e2af523bb024e9dd63d9a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
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
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Fusion.h  
  
 **Bibliothèque :** Fusion.dll et Mscorwks.dll. Utilisez le fichier Fusion.dll plutôt que Mscorwks.dll pour garantir que vous ciblez la version appropriée du .NET Framework.  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [IInstallReferenceEnum (Interface)](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md)  
 [IAssemblyName (Interface)](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)  
 [Fonctions statiques globales de fusion](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
