---
title: "IMetaDataImport::GetEventProps, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetEventProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetEventProps
helpviewer_keywords:
- IMetaDataImport::GetEventProps method [.NET Framework metadata]
- GetEventProps method [.NET Framework metadata]
ms.assetid: 5eaf3b4a-92b7-4d5b-97e0-1e83721e0052
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 9f616e00d79aec864bbb50b168a17e3f131a1aa1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportgeteventprops-method"></a>IMetaDataImport::GetEventProps, méthode
Obtient les informations de métadonnées pour l’événement représenté par le jeton d’événement spécifié, y compris le type déclarant, l’ajouter et supprimer des méthodes pour les délégués et tous les indicateurs et autres données associées.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetEventProps (  
   [in]  mdEvent       ev,  
   [out] mdTypeDef     *pClass,   
   [out] LPCWSTR       szEvent,   
   [in]  ULONG         cchEvent,   
   [out] ULONG         *pchEvent,   
   [out] DWORD         *pdwEventFlags,  
   [out] mdToken       *ptkEventType,  
   [out] mdMethodDef   *pmdAddOn,   
   [out] mdMethodDef   *pmdRemoveOn,   
   [out] mdMethodDef   *pmdFire,   
   [out] mdMethodDef   rmdOtherMethod[],   
   [in]  ULONG         cMax,  
   [out] ULONG         *pcOtherMethod  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ev`  
 [in] Le jeton de métadonnées d’événement représentant l’événement pour lequel obtenir les métadonnées.  
  
 `pClass`  
 [out] Pointeur vers le jeton TypeDef représentant la classe qui déclare l’événement.  
  
 `szEvent`  
 [out] Le nom de l’événement référencé par `ev`.  
  
 `pchEvent`  
 [in] La longueur requise en caractères larges de `szEvent`.  
  
 `pdwEventFlags`  
 [out] La longueur retournée en caractères larges de `szEvent`.  
  
 `ptkEventType`  
 [out] Un pointeur vers un TypeRef ou TypeDef métadonnées jeton représentant le <xref:System.Delegate> type de l’événement.  
  
 `pmdAddOn`  
 [out] Pointeur vers le jeton de métadonnées représentant la méthode qui ajoute des gestionnaires pour l’événement.  
  
 `pmdRemoveOn`  
 [out] Pointeur vers le jeton de métadonnées représentant la méthode qui supprime les gestionnaires pour l’événement.  
  
 `pmdFire`  
 [out] Pointeur vers le jeton de métadonnées représentant la méthode qui déclenche l’événement.  
  
 `rmdOtherMethod`  
 [out] Tableau de pointeurs de jetons à d’autres méthodes associées à l’événement.  
  
 `cMax`  
 [in] Taille maximale du tableau `rmdOtherMethod`.  
  
 `pcOtherMethod`  
 [out] Le nombre de jetons retournés dans `rmdOtherMethod`.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor.h  
  
 **Bibliothèque :** inclus en tant que ressource dans MsCorEE.dll  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [IMetaDataImport (Interface)](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [IMetaDataImport2 (Interface)](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
