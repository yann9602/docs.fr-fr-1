---
title: AddFile Method1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IALink.AddFile
- AddFile
api_location: alink.dll
api_type: COM
f1_keywords: AddFile
helpviewer_keywords: AddFile method
ms.assetid: 9e707abb-f905-4568-9356-12aa21d1b11c
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 943ff2901ee0888860941e86d589060de729907d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="addfile-method1"></a>AddFile Method1
Ajoute des fichiers à l’assembly. Peut également être utilisé pour créer des modules indépendants.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT AddFile(  
    mdAssembly      AssemblyID,  
    LPCWSTR         pszFilename,  
    DWORD           dwFlags,  
    IMetaDataEmit*  pEmitter,  
    mdFile*         pFileToken  
) PURE;  
```  
  
#### <a name="parameters"></a>Paramètres  
 `AssemblyID`  
 ID unique de l’assembly à augmenter.  
  
 `pszFilename`  
 Nom qualifié complet du fichier à ajouter.  
  
 `dwFlags`  
 Indicateurs de COM + FileDef tels que `ffContainsNoMetaData` et `ffWriteable`. `dwFlags`est passé à [DefineFile, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).  
  
 `pEmitter`  
 [IMetaDataEmit (Interface)](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) interface à utiliser pour émettre des métadonnées, si nécessaire.  
  
 `pFileToken`  
 Pointeur vers l’emplacement de stockage de l’ID unique du fichier ajouté.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne S_OK si la méthode réussit.  
  
## <a name="requirements"></a>Configuration requise  
 Requiert alink.h.  
  
## <a name="see-also"></a>Voir aussi  
 [IALink, interface](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [IALink2, interface](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [API ALink](../../../../docs/framework/unmanaged-api/alink/index.md)
