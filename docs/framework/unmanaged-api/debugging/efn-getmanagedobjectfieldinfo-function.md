---
title: _EFN_GetManagedObjectFieldInfo, fonction
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: _EFN_GetManagedObjectFieldInfo
api_location: mscordbi.dll
api_type: COM
f1_keywords: _EFN_GetManagedObjectFieldInfo
helpviewer_keywords: _EFN_GetManagedObjectFieldInfo function [.NET Framework debugging]
ms.assetid: 3b93bcff-62a4-47b2-babc-6bcf4216119a
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4822cab8816e97bd1d13c36ea7b63dc9a6f679d0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="efngetmanagedobjectfieldinfo-function"></a>_EFN_GetManagedObjectFieldInfo, fonction
Obtient l'offset du début d'un objet jusqu'à un champ, ainsi que la valeur du champ, à l'aide du pointeur d'objet et du nom de champ fournis.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT _EFN_GetManagedObjectFieldInfo(  
    [in]  PDEBUG_CLIENT Client,  
    [in]  ULONG64       objAddr,  
    [in]  __out_ecount (mdNameLen) PSTR szFieldName,  
    [out] PULONG64      pValue,  
    [out] PULONG        pOffset  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `Client`  
 [in] Pointeur vers le client de débogage.  
  
 `objAddr`  
 [in] Un pointeur d’objet managé.  
  
 szFieldName  
 [in] Un pointeur d’objet managé pour le nom du champ.  
  
 `pValue`  
 [out] La valeur du champ. Ce paramètre peut avoir la valeur Null.  
  
 `pOffset`  
 [out] Le décalage à partir de `objAddr` au champ. Ce paramètre peut avoir la valeur Null.  
  
## <a name="remarks"></a>Notes  
 Si le décalage est 0, aucun offset n’est écrit.  
  
 S’il n’existe aucun code managé sur le thread actuellement dans le contexte, la fonction retourne les HRESULT SOS_E_NOMANAGEDCODE avec une valeur d’environnement 0xa0 et un code d’erreur de 0 x 1000.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** SOS_Stacktrace.h  
  
 **Version du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions statiques globales de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
