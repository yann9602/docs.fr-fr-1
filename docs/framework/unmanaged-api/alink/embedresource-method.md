---
title: "EmbedResource, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IALink.EmbedResource
- EmbedResource
api_location: alink.dll
api_type: COM
f1_keywords: EmbedResource
helpviewer_keywords: EmbedResource method
ms.assetid: 667bd954-6dc6-4020-a3cb-0e8224179993
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 98dbd32452184bf4f832bd66ffebb0fcf3d5bb0b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="embedresource-method"></a>EmbedResource, méthode
Déclare une ressource incorporée. Cette méthode n’incorpore pas réellement la ressource.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT EmbedResource(  
    mdAssembly  AssemblyID,  
    mdToken     FileToken,  
    LPCWSTR     pszResourceName,  
    DWORD       dwOffset,  
    DWORD       dwFlags  
) PURE;  
```  
  
#### <a name="parameters"></a>Paramètres  
 `AssemblyID`  
 ID de l’assembly.  
  
 `FileToken`  
 ID de jeton ou l’assembly du fichier qui contient la ressource de fichier.  
  
 `pszResourceName`  
 Nom de la ressource.  
  
 `dwOffset`  
 Décalage de la ressource adresse RVA.  
  
 `dwFlags`  
 Accessibilité indicateurs tels que `mrPublic` et `mrPrivate`. Ces indicateurs peuvent être passés à [DefineExportedType, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne S_OK si la méthode réussit.  
  
## <a name="requirements"></a>Spécifications  
 Requiert alink.h.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface IALink](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [IALink2 (Interface)](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [ALink (API)](../../../../docs/framework/unmanaged-api/alink/index.md)
