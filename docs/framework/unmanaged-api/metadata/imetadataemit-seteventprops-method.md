---
title: "IMetaDataEmit::SetEventProps, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.SetEventProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::SetEventProps
helpviewer_keywords:
- IMetaDataEmit::SetEventProps method [.NET Framework metadata]
- SetEventProps method [.NET Framework metadata]
ms.assetid: 3b039e50-63ec-4730-99ff-2327408de477
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 167e56052550fa844d1265802455b3cbf6368ba3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitseteventprops-method"></a>IMetaDataEmit::SetEventProps, méthode
Définit ou met à jour la fonctionnalité spécifiée d’un événement défini par un appel antérieur à [IMetaDataEmit::DefineEvent](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineevent-method.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SetEventProps (  
    [in]  mdEvent     ev,   
    [in]  DWORD       dwEventFlags,   
    [in]  mdToken     tkEventType,   
    [in]  mdMethodDef mdAddOn,   
    [in]  mdMethodDef mdRemoveOn,   
    [in]  mdMethodDef mdFire,   
    [in]  mdMethodDef rmdOtherMethods[]   
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ev`  
 [in] Le jeton d’événement.  
  
 `dwEventFlags`  
 [in] Indicateurs d’événement. Il s’agit d’un masque de bits de `CorEventAttr` valeurs.  
  
 `tkEventType`  
 [in] Le jeton pour la classe d’événements. Il s’agit soit un `mdTypeDef` ou un `mdTypeRef` jeton.  
  
 `mdAddOn`  
 [in] La méthode utilisée pour s’abonner à l’événement, ou null.  
  
 `mdRemoveOn`  
 [in] La méthode utilisée pour annuler l’abonnement à l’événement, ou null.  
  
 `mdFire`  
 [in] La méthode utilisée (par une classe dérivée) pour déclencher l’événement.  
  
 `rmdOtherMethods[]`  
 [in] Tableau de jetons pour les autres méthodes associées à l’événement. Le dernier élément du tableau doit être `mdMethodDefNil`.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor.h  
  
 **Bibliothèque :** utilisé en tant que ressource dans MSCorEE.dll  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [IMetaDataEmit (Interface)](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [IMetaDataEmit2 (Interface)](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
