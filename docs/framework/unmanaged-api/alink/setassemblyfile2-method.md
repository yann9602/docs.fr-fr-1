---
title: "SetAssemblyFile2, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink2.SetAssemblyFile2
api_location: alink.dll
api_type: COM
f1_keywords: SetAssemblyFile2
helpviewer_keywords: SetAssemblyFile2 method
ms.assetid: eedb9125-1ef1-4000-abfc-7de86e5a1f17
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 671fb857015a5babd388366066d282cb87462c18
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="setassemblyfile2-method"></a>SetAssemblyFile2, méthode
Définit le nom et les options pour un nouvel assembly. N’appelez pas cette méthode lorsque vous générez des modules indépendants.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SetAssemblyFile2(  
    LPCWSTR pszFilename,  
    IMetaDataEmit2* pEmitter,  
    AssemblyFlags   afFlags,  
    mdAssembly* pAssemblyID  
) PURE;  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pszFilename`  
 Nom du fichier manifeste.  
  
 `pEmitter`  
 [IMetaDataEmit2 (Interface)](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md) interface pour ce fichier.  
  
 `afFlags`  
 Les options sont représentées par [énumération AssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md).  
  
 `pAssemblyID`  
 Reçoit l’ID unique de l’assembly en cours de construction.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne S_OK si la méthode réussit.  
  
## <a name="requirements"></a>Configuration requise  
 Requiert alink.h.  
  
## <a name="see-also"></a>Voir aussi  
 [IALink2, interface](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [IALink, interface](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [API ALink](../../../../docs/framework/unmanaged-api/alink/index.md)
