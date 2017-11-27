---
title: "RUNTIME_INFO_FLAGS, énumération"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: RUNTIME_INFO_FLAGS
api_location: mscoree.dll
api_type: COM
f1_keywords: RUNTIME_INFO_FLAGS
helpviewer_keywords: RUNTIME_INFO_FLAGS enumeration [.NET Framework hosting]
ms.assetid: adba37be-f775-4cdb-8919-5746ce694f33
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 697111efbb4e3f705c881ec677f781b6e3e6959d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="runtimeinfoflags-enumeration"></a>RUNTIME_INFO_FLAGS, énumération
Contient des valeurs qui indiquent les informations sur le common language runtime (CLR) doivent être retournées.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef enum {  
  
    RUNTIME_INFO_UPGRADE_VERSION             = 0x01,  
    RUNTIME_INFO_REQUEST_IA64                = 0x02,  
    RUNTIME_INFO_REQUEST_AMD64               = 0x04,  
    RUNTIME_INFO_REQUEST_X86                 = 0x08,  
    RUNTIME_INFO_DONT_RETURN_DIRECTORY       = 0x10,  
    RUNTIME_INFO_DONT_RETURN_VERSION         = 0x20,  
    RUNTIME_INFO_DONT_SHOW_ERROR_DIALOG      = 0x40,  
    RUNTIME_INFO_IGNORE_ERROR_MODE           = 0x1000  
  
} RUNTIME_INFO_FLAGS;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`RUNTIME_INFO_DONT_RETURN_DIRECTORY`|Indique que les informations d’annuaire ne doivent pas être incluses.|  
|`RUNTIME_INFO_DONT_RETURN_VERSION`|Indique que les informations de version ne doivent pas être incluses.|  
|`RUNTIME_INFO_DONT_SHOW_ERROR_DIALOG`|Indique qu’une boîte de dialogue d’erreur ne doit pas s’afficher en cas d’échec.|  
|`RUNTIME_INFO_IGNORE_ERROR_MODE`|Indique que les effets de l’appel de la [SetErrorMode](http://go.microsoft.com/fwlink/p/?LinkId=255242) fonction avec l’indicateur SEM_FAILCRITICALERRORS doit être substituée. Autrement dit, une boîte de dialogue d’installation doit être affichée en cas d’échec, au lieu d’en cours de suppression.|  
|`RUNTIME_INFO_REQUEST_AMD64`|Indique une demande d’informations sur une version compatible AMD-64 de l’exécution.|  
|`RUNTIME_INFO_REQUEST_IA64`|Indique une demande d’informations sur une version compatible IA-64 de l’exécution.|  
|`RUNTIME_INFO_REQUEST_X86`|Indique une demande d’informations sur une version compatible avec x86 du runtime.|  
|`RUNTIME_INFO_UPGRADE_VERSION`|Indique que les informations de mise à niveau de version doivent être incluses.|  
  
## <a name="remarks"></a>Remarques  
 Les indicateurs d’architecture de plateforme suivants peuvent être spécifiés une seule à la fois et ne peut pas être combinées :  
  
-   RUNTIME_INFO_REQUEST_IA64  
  
-   RUNTIME_INFO_REQUEST_AMD64  
  
-   RUNTIME_INFO_REQUEST_X86  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE.h  
  
 **Bibliothèque :** MSCorEE.dll  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations d’hébergement](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
