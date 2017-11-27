---
title: "ExportNestedType, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IALink.ExportNestedType
- ExportNestedType
api_location: alink.dll
api_type: COM
f1_keywords: ExportNestedType
helpviewer_keywords: ExportNestedType method
ms.assetid: dec7df60-4d30-47c8-99db-72e0419e5f76
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 378d1e8b21b8d3993377ac08ff7006c420117bfe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="exportnestedtype-method"></a>ExportNestedType, méthode
Spécifie les types imbriqués comme étant exportable. Le [ExportType, méthode](../../../../docs/framework/unmanaged-api/alink/exporttype-method.md) peut également exporter les types imbriqués, mais cette méthode est plus rapide.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT ExportNestedType(  
    mdAssembly      AssemblyID,  
    mdToken         FileToken,  
    mdTypeDef       TypeToken,  
    mdExportedType  ParentType,  
    LPCWSTR         pszTypename,  
    DWORD           dwFlags,  
    mdExportedType* pType  
) PURE;   
```  
  
#### <a name="parameters"></a>Paramètres  
 `AssemblyID`  
 ID de l’assembly à exporter à partir de.  
  
 `FileToken`  
 Jeton de fichier ou l’Assembly du fichier qui définit le type à rendre exportable.  
  
 `TypeToken`  
 Type de jeton de type à rendre exportable.  
  
 `ParentType`  
 Jeton de type parent.  
  
 `pszTypename`  
 Nom de type qualifié complet à exporter.  
  
 `dwFlags`  
 `ComType`indicateurs tels que `tdPublic` ou `tdNested`. Cette valeur peut être passée à [DefineExportedType, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).  
  
 `pType`  
 Reçoit le jeton pour le type exporté.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne S_OK si la méthode réussit.  
  
## <a name="requirements"></a>Spécifications  
 Requiert alink.h  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IALink](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [IALink2 (Interface)](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [ALink (API)](../../../../docs/framework/unmanaged-api/alink/index.md)
