---
title: IMetaDataConverter, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataConverter
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataConverter
helpviewer_keywords: IMetaDataConverter interface [.NET Framework metadata]
ms.assetid: 9caea662-0167-4267-b14a-2fa42c3be4ea
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: f551a774a860f595cc90a7cca9eee2c726ef50ee
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataconverter-interface"></a>IMetaDataConverter, interface
Fournit des méthodes pour mapper des bibliothèques de types à leurs signatures de métadonnées et effectuer la conversion entre les deux.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetMetaDataFromTypeInfo (méthode)](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-getmetadatafromtypeinfo-method.md)|Obtient un pointeur vers un [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) instance qui représente la signature de métadonnées pour la bibliothèque de types référencée par le `ITypeInfo` instance.|  
|[GetMetaDataFromTypeLib (méthode)](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-getmetadatafromtypelib-method.md)|Obtient un pointeur vers un `IMetaDataImport` instance qui représente la signature de métadonnées pour la bibliothèque de types représentée par le `ITypeLib` instance.|  
|[GetTypeLibFromMetaData (méthode)](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-gettypelibfrommetadata-method.md)|Obtient un pointeur vers un `ITypeLib` instance qui représente la bibliothèque de types qui contient les noms de module et de bibliothèque spécifiés.|  
  
## <a name="requirements"></a>Spécifications  
 **Plateforme :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor.h  
  
 **Bibliothèque :** utilisé en tant que ressource dans MsCorEE.dll  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de métadonnées](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [IMetaDataImport (Interface)](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
