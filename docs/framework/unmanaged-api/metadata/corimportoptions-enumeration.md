---
title: "CorImportOptions, énumération"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorImportOptions
api_location: mscoree.dll
api_type: COM
f1_keywords: CorImportOptions
helpviewer_keywords: CorImportOptions enumeration [.NET Framework metadata]
ms.assetid: 4e5d03cb-97c9-4ff4-8dbd-17d94ee374d3
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e9af7bbb6dd7cfa488f72ec99f9cfd848f04e72f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="corimportoptions-enumeration"></a>CorImportOptions, énumération
Contient des valeurs d'indicateur qui contrôlent le comportement lors de l'importation d'un assembly en dehors de la portée actuelle.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef enum CorImportOptions {  
  
    MDImportOptionDefault                = 0x00000000,  
    MDImportOptionAll                    = 0xFFFFFFFF,  
    MDImportOptionAllTypeDefs            = 0x00000001,  
    MDImportOptionAllMethodDefs          = 0x00000002,  
    MDImportOptionAllFieldDefs           = 0x00000004,  
    MDImportOptionAllProperties          = 0x00000008,  
    MDImportOptionAllEvents              = 0x00000010,  
    MDImportOptionAllCustomAttributes    = 0x00000020,  
    MDImportOptionAllExportedTypes       = 0x00000040  
  
} CorImportOptions;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`MDImportOptionDefault`|Indique le comportement par défaut, qui consiste à ignorer les enregistrements supprimés.|  
|`MDImportOptionAll`|Indique que toutes les métadonnées doivent être énumérés.|  
|`MDImportOptionAllTypeDefs`|Indique que tous les TypeDefs, y compris ceux qui sont supprimés, doivent être énumérés.|  
|`MDImportOptionAllMethodDefs`|Indique que tous les MethodDefs, y compris ceux qui sont supprimés, doivent être énumérés.|  
|`MDImportOptionAllFieldDefs`|Indique que tous les FieldDefs, y compris ceux qui sont supprimés, doivent être énumérés.|  
|`MDImportOptionAllProperties`|Indique que tous les PropertyDefs, y compris ceux qui sont supprimés, doivent être énumérés.|  
|`MDImportOptionAllEvents`|Indique que tous les EventDefs, y compris ceux qui sont supprimés, doivent être énumérés.|  
|`MDImportOptionAllCustomAttributes`|Indique que tous les attributs personnalisés, y compris ceux qui sont supprimés, doivent être énumérés.|  
|`MDImportOptionAllExportedTypes`|Indique que tous les types exportés, y compris ceux qui sont supprimés, doivent être énumérés.|  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorHdr.h  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations de métadonnées](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
