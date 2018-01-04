---
title: "IMetaDataImport::EnumMembers, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.EnumMembers
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::EnumMembers
helpviewer_keywords:
- IMetaDataImport::EnumMembers method [.NET Framework metadata]
- EnumMembers method [.NET Framework metadata]
ms.assetid: 3fb8e178-342b-4c89-9bcf-f7f834e6cb77
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: aa7dabad0e555fe965cba4e5cbc69c10c9826b8e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportenummembers-method"></a>IMetaDataImport::EnumMembers, méthode
Énumère les jetons MemberRef représentant les membres du type spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT EnumMembers (   
   [in, out]  HCORENUM    *phEnum,   
   [in]  mdTypeDef   cl,   
   [out] mdToken     rMembers[],   
   [in]  ULONG       cMax,   
   [out] ULONG       *pcTokens  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `phEnum`  
 [dans, out] Pointeur vers l’énumérateur.  
  
 `cl`  
 [in] Un jeton TypeDef représentant le type dont les membres doivent être énumérés.  
  
 `rMembers`  
 [out] Tableau utilisé pour stocker les jetons MemberDef.  
  
 `cMax`  
 [in] Taille maximale du tableau `rMembers`.  
  
 `pcTokens`  
 [out] Le nombre réel de jetons MemberDef retournés dans `rMembers`.  
  
## <a name="return-value"></a>Valeur de retour  
  
|HRESULT|Description|  
|-------------|-----------------|  
|`S_OK`|`EnumMembers`retourné avec succès.|  
|`S_FALSE`|Il n’existe pas de jetons MemberDef à énumérer. Dans ce cas, `pcTokens` est égal à zéro.|  
  
## <a name="remarks"></a>Notes  
 Lors de l’énumération des collections de membres pour une classe, `EnumMembers` retourne uniquement les membres définis directement sur la classe. Il ne retourne pas de tous les membres qui hérite de la classe, même si la classe fournit une implémentation pour ces membres hérités. Pour énumérer les membres hérités, l’appelant doit parcourir explicitement la chaîne d’héritage. Notez que les règles pour la chaîne d’héritage peuvent varier en fonction de la langue ou le compilateur qui a émis les métadonnées d’origine.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor.h  
  
 **Bibliothèque :** inclus en tant que ressource dans MsCorEE.dll  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [IMetaDataImport, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [IMetaDataImport2, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
