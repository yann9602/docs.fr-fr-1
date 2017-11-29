---
title: "IMetaDataEmit::GetSaveSize, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.GetSaveSize
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::GetSaveSize
helpviewer_keywords:
- IMetaDataEmit::GetSaveSize method [.NET Framework metadata]
- GetSaveSize method [.NET Framework metadata]
ms.assetid: 8aea2e2c-23a3-4cda-9a06-e19f97383830
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 9686e8e2c4e8276e725852cb58fac7ed1973778b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitgetsavesize-method"></a>IMetaDataEmit::GetSaveSize, méthode
Obtient la taille binaire estimée de l’assembly et ses métadonnées dans la portée actuelle.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetSaveSize (  
    [in]  CorSaveSize fSave,  
    [out] DWORD       *pdwSaveSize  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `fSave`  
 [in] Une valeur de la [CorSaveSize](../../../../docs/framework/unmanaged-api/metadata/corsavesize-enumeration.md) énumération qui spécifie s’il faut obtenir une taille exacte ou approximative. Seuls trois valeurs sont valides : cssAccurate, cssQuick et cssDiscardTransientCAs :  
  
-   cssAccurate retourne la taille d’enregistrement exacte, mais prend plus de temps à calculer.  
  
-   cssQuick retourne une taille, remplie pour la sécurité, mais prend moins de temps à calculer.  
  
-   cssDiscardTransientCAs indique à `GetSaveSize` qu’il ne peut lever immédiatement les attributs personnalisés pouvant être éliminées.  
  
 `pdwSaveSize`  
 [out] Pointeur vers la taille qui est requis pour enregistrer le fichier.  
  
## <a name="remarks"></a>Remarques  
 `GetSaveSize`calcule l’espace requis, en octets, pour enregistrer l’assembly et toutes ses métadonnées dans la portée actuelle. (Un appel à la [IMetaDataEmit::SaveToStream](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetostream-method.md) méthode émet ce nombre d’octets.)  
  
 Si l’appelant implémente la [IMapToken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md) interface (via [IMetaDataEmit::SetHandler](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md) ou [IMetaDataEmit::Merge](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-merge-method.md)), `GetSaveSize` effectue deux passes sur les métadonnées pour les optimiser et les compresser. Sinon, aucune optimisation n’est effectuées.  
  
 Si l’optimisation est effectuée, le premier passage trie simplement les structures de métadonnées pour régler les performances des recherches au moment de l’importation. Cette étape se produit généralement lors du déplacement d’enregistrements, avec comme conséquence que les jetons conservés par l’outil pour référence ultérieure sont invalidés. Les métadonnées n’informent pas l’appelant de ces modifications apportées aux jetons jusqu’après la deuxième passe, toutefois. Dans la deuxième passe, différents des optimisations destinées à réduire la taille globale des métadonnées, telles que l’optimisation (liaison anticipée) `mdTypeRef` et `mdMemberRef` jetons lors de la référence est un type ou membre qui est déclaré dans le portée de métadonnées actuelle. Dans cette étape, une autre série de mappages de jetons se produit. Après cette étape, le moteur de métadonnées informe l’appelant, via son `IMapToken` interface, de n’importe quel modifié les valeurs de jeton.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor.h  
  
 **Bibliothèque :** utilisé en tant que ressource dans MSCorEE.dll  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [IMetaDataEmit (Interface)](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [IMetaDataEmit2 (Interface)](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
