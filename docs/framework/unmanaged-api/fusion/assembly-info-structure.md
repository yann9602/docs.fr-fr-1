---
title: ASSEMBLY_INFO, structure
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ASSEMBLY_INFO
api_location: fusion.dll
api_type: COM
f1_keywords: ASSEMBLY_INFO
helpviewer_keywords: ASSEMBLY_INFO structure [.NET Framework fusion]
ms.assetid: b3cbb47c-457f-4083-8895-49562ca99ab8
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 215d80c3d207c2f50cfbd74386915b0467692b57
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="assemblyinfo-structure"></a>ASSEMBLY_INFO, structure
Contient des informations sur un assembly qui est enregistré dans le global assembly cache.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef struct _ASSEMBLY_INFO {  
    ULONG           cbAssemblyInfo;  
    DWORD           dwAssemblyFlags;  
    ULARGE_INTEGER  uliAssemblySizeInKB;  
    LPWSTR          pszCurrentAssemblyPathBuf;  
    ULONG           cchBuf;  
} ASSEMBLY_INFO;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`cbAssemblyInfo`|La taille, en octets, de la structure. Ce champ est réservé pour une future extensibilité.|  
|`dwAssemblyFlags`|Indicateurs qui indiquent les détails de l’installation sur l’assembly. Les valeurs suivantes sont prises en charge :<br /><br /> -La valeur ASSEMBLYINFO_FLAG_INSTALLED, ce qui indique que l’assembly est installé. La version actuelle du .NET Framework définit toujours `dwAssemblyFlags` à cette valeur.<br />-La valeur ASSEMBLYINFO_FLAG_PAYLOADRESIDENT, ce qui indique que l’assembly est un résident de charge utile. La version actuelle du .NET Framework n’affecte jamais `dwAssemblyFlags` à cette valeur.|  
|`uliAssemblySizeInKB`|La taille totale, en kilo-octets, des fichiers contenant l’assembly.|  
|`pszCurrentAssemblyPathBuf`|Pointeur vers une mémoire tampon de chaîne qui contient le chemin d’accès actuel dans le fichier manifeste. Le chemin d’accès doit se terminer par un caractère null.|  
|`cchBuf`|Le nombre de caractères larges, y compris la marque de fin null, qui `pszCurrentAssemblyPathBuf` contient.|  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Fusion.h  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Structures de fusion](../../../../docs/framework/unmanaged-api/fusion/fusion-structures.md)  
 [Global Assembly Cache](../../../../docs/framework/app-domains/gac.md)
