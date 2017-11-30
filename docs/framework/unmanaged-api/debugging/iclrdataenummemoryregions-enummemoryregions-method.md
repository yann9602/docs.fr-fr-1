---
title: "ICLRDataEnumMemoryRegions::EnumMemoryRegions, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDataEnumMemoryRegions.EnumMemoryRegions
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICLRDataEnumMemoryRegions::EnumMemoryRegions
helpviewer_keywords:
- ICLRDataEnumMemoryRegions::EnumMemoryRegions method [.NET Framework debugging]
- EnumMemoryRegions method [.NET Framework debugging]
ms.assetid: 22d2e339-f174-40b5-a478-0b744501566f
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1393c5c803020339ef998a57b87ad495220c1046
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="iclrdataenummemoryregionsenummemoryregions-method"></a>ICLRDataEnumMemoryRegions::EnumMemoryRegions, méthode
Énumère les zones de mémoire spécifiées.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT EnumMemoryRegions (  
    [in] ICLRDataEnumMemoryRegionsCallback  *callback,  
    [in] ULONG32                            miniDumpFlags,  
    [in] CLRDataEnumMemoryFlags             clrFlags  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `callback`  
 [in] Un pointeur vers un [ICLRDataEnumMemoryRegionsCallback](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-interface.md) instance qui est appelée par cette méthode pour chaque région de mémoire énumérée, afin d’informer le débogueur du résultat.  
  
 L’énumération de régions de mémoire continue même si le rappel indique un échec.  
  
 `miniDumpFlags`  
 [in] Non utilisé.  
  
 `clrFlags`  
 [in] Une valeur de la [CLRDataEnumMemoryFlags](../../../../docs/framework/unmanaged-api/debugging/clrdataenummemoryflags-enumeration.md) énumération qui spécifie les régions de mémoire à énumérer.  
  
## <a name="remarks"></a>Remarques  
 Cette méthode utilise le [ICLRDataEnumMemoryRegionsCallback](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-interface.md) instance pour informer l’appelant des résultats.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** ClrData.idl, ClrData.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [ICLRDataEnumMemoryRegions (Interface)](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-interface.md)
