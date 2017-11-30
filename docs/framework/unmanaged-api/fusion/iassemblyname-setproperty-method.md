---
title: "IAssemblyName::SetProperty, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IAssemblyName.SetProperty
api_location: fusion.dll
api_type: COM
f1_keywords: IAssemblyName::SetProperty
helpviewer_keywords:
- IAssemblyName::SetProperty method [.NET Framework fusion]
- SetProperty method [.NET Framework fusion]
ms.assetid: 496c3add-f60b-4073-943f-d1bcf33330cb
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2b99b9c01d014f7b6c02eedde157fa6fdd4e142a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="iassemblynamesetproperty-method"></a>IAssemblyName::SetProperty, méthode
Définit la valeur de la propriété référencée par l’identificateur de la propriété spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SetProperty (  
    [in] DWORD  PropertyId,  
    [in] LPVOID pvProperty,  
    [in] DWORD  cbProperty  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `PropertyId`  
 [in] Identificateur unique de la propriété dont la valeur sera définie.  
  
 `pvProperty`  
 [in] La valeur à laquelle définir la propriété référencée par `PropertyId`.  
  
 `cbProperty`  
 [in] La taille, en octets, de `pvProperty`.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Fusion.h  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [IAssemblyName (Interface)](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
