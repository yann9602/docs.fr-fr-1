---
title: FUSION_INSTALL_REFERENCE, structure
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: FUSION_INSTALL_REFERENCE
api_location: fusion.dll
api_type: COM
f1_keywords: FUSION_INSTALL_REFERENCE
helpviewer_keywords: FUSION_INSTALL_REFERENCE structure [.NET Framework fusion]
ms.assetid: ae181ec8-36bf-4ed1-9a02-ca27d417c80b
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 36321606fe208233fb6114fe9568b655f0e1b400
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="fusioninstallreference-structure"></a>FUSION_INSTALL_REFERENCE, structure
Représente une référence qu’une application à un assembly de l’application est installée dans le global assembly cache.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef struct _FUSION_INSTALL_REFERENCE_ {  
    DWORD    cbSize,  
    DWORD    dwFlags,  
    GUID     guidScheme,  
    LPCWSTR  szIdentifier,  
    LPCWSTR  szNonCanonicalData  
} FUSION_INSTALL_REFERENCE, *LPFUSION_INSTALL_REFERENCE;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`cbSize`|La taille de la structure en octets.|  
|`dwFlags`|Réservé pour une future extensibilité. Cette valeur doit être 0 (zéro).|  
|`guidScheme`|L’entité qui ajoute la référence. Ce champ peut avoir une des valeurs suivantes :<br /><br /> -FUSION_REFCOUNT_MSI_GUID : L’assembly est référencé par une application qui a été installée à l’aide de Microsoft Windows Installer. Le `szIdentifier` champ est défini sur `MSI`et le `szNonCanonicalData` champ est défini sur `Windows Installer`. Ce schéma est utilisé pour les assemblys côte à côte de Windows.<br />-FUSION_REFCOUNT_UNINSTALL_SUBKEY_GUID : L’assembly est référencé par une application qui s’affiche dans le **Ajout/Suppression de programmes** interface. Le `szIdentifier` champ fournit le jeton qui enregistre l’application avec le **Ajout/Suppression de programmes** interface.<br />-FUSION_REFCOUNT_FILEPATH_GUID : L’assembly est référencé par une application qui est représentée par un fichier dans le système de fichiers. Le `szIdentifier` champ fournit le chemin d’accès à ce fichier.<br />-FUSION_REFCOUNT_OPAQUE_STRING_GUID : L’assembly est référencé par une application qui est représentée uniquement par une chaîne opaque. Le `szIdentifier` champ fournit cette chaîne opaque. Le global assembly cache ne vérifie pas l’existence de références opaques lorsque vous supprimez cette valeur.<br />-FUSION_REFCOUNT_OSINSTALL_GUID : Cette valeur est réservée.|  
|`szIdentifier`|Une chaîne unique qui identifie l’application qui a installé l’assembly dans le global assembly cache. Sa valeur dépend de la valeur de la `guidScheme` champ.|  
|`szNonCanonicalData`|Chaîne qui est comprise uniquement par l’entité qui ajoute la référence. Le global assembly cache stocke cette chaîne, mais ne l’utilise pas.|  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Fusion.h  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Structures de fusion](../../../../docs/framework/unmanaged-api/fusion/fusion-structures.md)  
 [Global Assembly Cache](../../../../docs/framework/app-domains/gac.md)
