---
title: "ImportTypes, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink.ImportTypes
api_location: alink.dll
api_type: COM
f1_keywords: ImportTypes
helpviewer_keywords: ImportTypes method
ms.assetid: 351d4b4c-c939-486d-9471-51914a55f471
topic_type: apiref
caps.latest.revision: "5"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 39e7cfb3c811a89ae88d6984946f72a9b1f469db
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="importtypes-method"></a>ImportTypes, méthode
Lance l’importation de types de chaque portée importée par [méthode ImportFile](../../../../docs/framework/unmanaged-api/alink/importfile-method.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT ImportTypes(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    HALINKENUM* phEnum,  
    IMetaDataImport** ppImportScope,  
    DWORD* pdwCountOfTypes  
) PURE;  
```  
  
#### <a name="parameters"></a>Paramètres  
 `AssemblyID`  
 ID de l’assembly dans lequel importer.  
  
 `FileToken`  
 ID du fichier à importer à partir de.  
  
 `dwScope`  
 Portée de base zéro à importer.  
  
 `phEnum`  
 Reçoit le handle d’énumérateur pour les types dans cette portée.  
  
 `ppImportScope`  
 Si vous le souhaitez reçoit [IMetaDataImport (Interface)](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface.  
  
 `pdwCountOfTypes`  
 Si vous le souhaitez reçoit le nombre de types dans l’étendue indiquée.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne S_OK si la méthode réussit.  
  
## <a name="requirements"></a>Configuration requise  
 Requiert alink.h  
  
## <a name="see-also"></a>Voir aussi  
 [IALink, interface](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [IALink2, interface](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [API ALink](../../../../docs/framework/unmanaged-api/alink/index.md)
