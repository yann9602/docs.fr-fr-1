---
title: "CorMethodImpl, énumération"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorMethodImpl
api_location: mscoree.dll
api_type: COM
f1_keywords: CorMethodImpl
helpviewer_keywords: CorMethodImpl enumeration [.NET Framework metadata]
ms.assetid: ffbb3caf-20da-4a4b-8983-77376e72b990
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e82eb50e4850ffbb4d5fc67d9603a3128cf8bcf6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="cormethodimpl-enumeration"></a>CorMethodImpl, énumération
Contient des valeurs qui décrivent les fonctionnalités d’implémentation d’une méthode.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef enum CorMethodImpl {  
  
    miCodeTypeMask      =   0x0003,  
    miIL                =   0x0000,  
    miNative            =   0x0001,  
    miOPTIL             =   0x0002,  
    miRuntime           =   0x0003,  
  
    miManagedMask       =   0x0004,  
    miUnmanaged         =   0x0004,  
    miManaged           =   0x0000,  
  
    miForwardRef        =   0x0010,  
    miPreserveSig       =   0x0080,  
  
    miInternalCall      =   0x1000,  
    miSynchronized      =   0x0020,  
    miNoInlining        =   0x0008,  
    miAggressiveInlining =  0x0100,  
    miNoOptimization     =  0x0040,  
    miMaxMethodImplVal  =   0xffff  
  
} CorMethodImpl;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`miCodeTypeMask`|Indicateurs qui décrivent le type de code.|  
|`miIL`|Spécifie que l’implémentation de méthode est Microsoft intermediate language (MSIL).|  
|`miNative`|Spécifie que l’implémentation de la méthode est native.|  
|`miOPTIL`|Spécifie que l’implémentation de méthode est OPTIL.|  
|`miRuntime`|Spécifie que l’implémentation de méthode est fournie par le common language runtime.|  
|`miManagedMask`|Indicateurs qui indiquent si le code est managé ou non managé.|  
|`miUnmanaged`|Spécifie que l’implémentation de méthode n’est pas gérée.|  
|`miManaged`|Spécifie que l’implémentation de méthode est gérée.|  
|`miForwardRef`|Spécifie que la méthode est définie. Cet indicateur est utilisé principalement dans les scénarios de fusion.|  
|`miPreserveSig`|Spécifie que la signature de méthode ne peut pas être tronquée pour une conversion HRESULT.|  
|`miInternalCall`|Réservé à un usage interne par le common language runtime.|  
|`miSynchronized`|Spécifie que la méthode est à thread unique son corps.|  
|`miNoInlining`|Spécifie que la méthode ne peut pas être inline.|  
|`miAggressiveInlining`|Spécifie que la méthode doit être inline si possible.|  
|`miNoOptimization`|Spécifie que la méthode ne doit pas être optimisée.|  
|`miMaxMethodImplVal`|La valeur valide maximale pour un `CorMethodImpl`.|  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorHdr.h  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations de métadonnées](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
