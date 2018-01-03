---
title: "ImportFileEx, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink2.ImportFileEx
api_location: alink.dll
api_type: COM
f1_keywords: ImportFileEx
helpviewer_keywords: ImportFileEx method
ms.assetid: ad276f3f-b303-46ac-97e0-66a377adaa4f
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: dc2af9db27c5194a1bdcef875b8db8d458d0edfe
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="importfileex-method"></a>ImportFileEx, méthode
Importations indiquées assembly ou module indépendant.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT ImportFileEx(  
    LPCWSTR pszFilename,  
    LPCWSTR pszTargetName,  
    BOOL fSmartImport,  
    DWORD dwOpenFlags,  
    mdToken* pImportToken,  
    IMetaDataAssemblyImport** ppAssemblyScope,  
    DWORD* pdwCountOfScopes  
) PURE;  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pszFilename`  
 Nom qualifié complet du fichier à partir duquel importer.  
  
 `pszTargetName`  
 Nom facultatif du fichier cible.  
  
 `fSmartImport`  
 Si la valeur est TRUE, ImportTypes est utilisé, sinon l’importation doit être effectuée manuellement.  
  
 `dwOpenFlags`  
 Indicateurs à passer à [OpenScope, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md).  
  
 `pImportToken`  
 Reçoit l’ID du fichier en cours d’importation.  
  
 `ppAssemblyScope`  
 Reçoit la portée d’importation assembly [IMetaDataAssemblyImport (Interface)](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface. A la valeur NULL si le fichier n’est pas un assembly.  
  
 `pdwCountOfScopes`  
 Reçoit le nombre de fichiers importés et/ou étendues.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne S_OK si la méthode réussit.  
  
## <a name="requirements"></a>Configuration requise  
 Requiert alink.h.  
  
## <a name="see-also"></a>Voir aussi  
 [IALink2, interface](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [IALink, interface](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [API ALink](../../../../docs/framework/unmanaged-api/alink/index.md)
