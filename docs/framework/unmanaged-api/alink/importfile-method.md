---
title: "ImportFile, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink.ImportFile
api_location: alink.dll
api_type: COM
f1_keywords: ImportFile
helpviewer_keywords: ImportFile method
ms.assetid: bcbe321f-b83a-4e9a-9f10-8d913e244dc9
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b5d4f93336fe19210086c39b8db6d167b3caa222
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="importfile-method"></a>ImportFile, méthode
Importe les assemblys et modules indépendants.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT ImportFile(  
    LPCWSTR pszFilename,  
    LPCWSTR pszTargetName,  
    BOOL fSmartImport,  
    mdToken* pImportToken,  
    IMetaDataAssemblyImport** ppAssemblyScope,  
    DWORD* pdwCountOfScopes  
) PURE;  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pszFilename`  
 Nom qualifié complet du fichier à importer.  
  
 `pszTargetName`  
 Nom de fichier de sortie facultatif qui peut être utilisé pour renommer le fichier lorsqu’il est lié dans l’assembly.  
  
 `fSmartImport`  
 Si la valeur est TRUE, ImportTypes est utilisé, sinon l’importation doit être effectuée manuellement.  
  
 `pImportToken`  
 Pointeur vers le jeton où un ID de fichier unique sera stocké. Le fichier peut être un assembly ou un fichier.  
  
 `ppAssemblyScope`  
 Reçoit le pointeur vers [IMetaDataAssemblyImport (Interface)](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md). Peut d’être NULL si le fichier n’est pas un assembly.  
  
 `pdwCountOfScopes`  
 Pointeur vers le nombre de fichiers et/ou de portées qui ont été importées.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne S_OK si la méthode réussit.  
  
## <a name="requirements"></a>Configuration requise  
 Requiert alink.h  
  
## <a name="see-also"></a>Voir aussi  
 [IALink, interface](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [IALink2, interface](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [API ALink](../../../../docs/framework/unmanaged-api/alink/index.md)
