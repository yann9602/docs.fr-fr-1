---
title: ASSEMBLYMETADATA, structure
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ASSEMBLYMETADATA
api_location: mscoree.dll
api_type: COM
f1_keywords: ASSEMBLYMETADATA
helpviewer_keywords: ASSEMBLYMETADATA structure [.NET Framework metadata]
ms.assetid: 1af98e57-9145-4d35-bb78-77d1da7c91a5
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5652907abc17868414c554cb5c87b0856d2c5a0c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="assemblymetadata-structure"></a>ASSEMBLYMETADATA, structure
Contient des informations sur l’assembly référencé, y compris sa version et son niveau de prise en charge des paramètres régionaux, des processeurs et systèmes d’exploitation.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef struct {  
    USHORT  usMajorVersion;  
    USHORT  usMinorVersion;  
    USHORT  usBuildNumber;  
    USHORT  usRevisionNumber;  
    LPWSTR  szLocale;  
    ULONG   cbLocale;  
    DWORD*  rdwProcessor[];  
    ULONG   ulProcessor  
    OSINFO* rOS[];  
    ULONG   ulOS;  
} ASSEMBLYMETADATA;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`usMajorVersion`|Numéro de version principale de l’assembly référencé. Cette valeur ne peut pas être zéro. Si tous les bits de `usMajorVersion` sont définis, la version principale n’est pas spécifiée.|  
|`usMinorVersion`|Le numéro de version secondaire de l’assembly référencé. Cette valeur ne peut pas être zéro. Si tous les bits de `usMinorVersion` sont définis, la version secondaire n’est pas spécifiée.|  
|`usBuildNumber`|Le numéro de build de l’assembly référencé. Cette valeur ne peut pas être zéro. Si tous les bits de `usBuildNumber` sont définis, le numéro de build n’est pas spécifié.|  
|`usRevisionNumber`|Le numéro de révision de l’assembly référencé. Cette valeur ne peut pas être zéro. Si tous les bits de `usRevisionNumber` sont définis, le numéro de révision n’est pas spécifié.|  
|`szLocale`|Une liste de noms de paramètres régionaux conformément à la spécification RFC1766, séparée par des points-virgules, spécifiant les paramètres régionaux pris en charge par l’assembly référencé. Une valeur null indique l’indépendance des paramètres régionaux. **Remarque :** dans le .NET Framework version 1.0, vous ne pouvez pas spécifier plusieurs paramètres régionaux.|  
|`cbLocale`|La taille en caractères larges de `szLocale`.|  
|`rdwProcessor`|Un tableau d’identificateurs, tel que défini dans Winnt.h, pour les types de processeurs pris en charge par l’assembly référencé. Une valeur NULL indique l’indépendance des processeurs.|  
|`ulProcessor`|La longueur de la `rdwProcessor` tableau.|  
|`rOS`|Un tableau de [OSINFO](../../../../docs/framework/unmanaged-api/metadata/osinfo-structure.md) instances spécifiant les systèmes d’exploitation pris en charge par l’assembly référencé. Une valeur NULL indique l’indépendance du système d’exploitation.|  
|`ulOS`|La longueur de la `rOS` tableau.|  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor.h  
  
 **Bibliothèque :** utilisé en tant que ressource dans MsCorEE.dll  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Structures de métadonnées](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)  
 [IMetaDataAssemblyEmit (Interface)](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)  
 [OSINFO (Structure)](../../../../docs/framework/unmanaged-api/metadata/osinfo-structure.md)
