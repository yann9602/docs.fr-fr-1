---
title: GetScope Method1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink.GetScope
api_location: alink.dll
api_type: COM
f1_keywords: GetScope
helpviewer_keywords: GetScope method
ms.assetid: e1555328-2c71-4ece-b357-9eb6d3a8efc4
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4cb51efc3f431dac4a10cc7582e2b43500ccba15
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="getscope-method1"></a>GetScope Method1
Obtient une portée d’importation.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetScope(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    IMetaDataImport** ppImportScope  
) PURE;  
```  
  
#### <a name="parameters"></a>Paramètres  
 `AssemblyID`  
 ID unique de l’assembly dans lequel importer.  
  
 `FileToken`  
 ID unique du fichier à importer à partir de.  
  
 `dwScope`  
 Portée de base zéro à importer.  
  
 `ppImportScope`  
 Reçoit [IMetaDataImport (Interface)](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface pour l’étendue.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne S_OK si la méthode réussit.  
  
## <a name="requirements"></a>Configuration requise  
 Requiert alink.h  
  
## <a name="see-also"></a>Voir aussi  
 [IALink, interface](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [IALink2, interface](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [API ALink](../../../../docs/framework/unmanaged-api/alink/index.md)
