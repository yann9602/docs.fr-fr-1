---
title: "SetAssemblyFile, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink.SetAssemblyFile
api_location: alink.dll
api_type: COM
f1_keywords: SetAssemblyFile
helpviewer_keywords: SetAssemblyFile method
ms.assetid: 3a912787-f139-43ca-a841-8bbda3107ecf
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c0be76e93ab41860f7f3416d0baffe3e4daf84c7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="setassemblyfile-method"></a>SetAssemblyFile, méthode
Attribue le nom de l’assembly doit être créé. Pas à utiliser lors de la production de modules indépendants.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SetAssemblyFile(  
    LPCWSTR pszFilename,  
    IMetaDataEmit* pEmitter,  
    AssemblyFlags afFlags,  
    mdAssembly* pAssemblyID  
) PURE;  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pszFilename`  
 Nom qualifié complet du fichier manifeste.  
  
 `pEmitter`  
 Pointeur vers [IMetaDataEmit (Interface)](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) interface.  
  
 `afFlags`  
 Indicateurs tel que défini dans [énumération AssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md).  
  
 `pAssemblyID`  
 Pointeur vers l’ID de l’assembly résultant.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne S_OK si la méthode réussit.  
  
## <a name="requirements"></a>Configuration requise  
 Requiert alink.h.  
  
## <a name="see-also"></a>Voir aussi  
 [IALink, interface](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [IALink2, interface](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [API ALink](../../../../docs/framework/unmanaged-api/alink/index.md)
