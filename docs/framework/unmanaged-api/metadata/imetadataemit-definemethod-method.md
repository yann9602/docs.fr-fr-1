---
title: "IMetaDataEmit::DefineMethod, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.DefineMethod
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::DefineMethod
helpviewer_keywords:
- DefineMethod method [.NET Framework metadata]
- IMetaDataEmit::DefineMethod method [.NET Framework metadata]
ms.assetid: 3e2102c5-48b7-4c0e-b805-7e2b5e156e3d
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: de55ee714dcba512befae3d2311a9880a08ba29f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitdefinemethod-method"></a>IMetaDataEmit::DefineMethod, méthode
Crée une définition pour une méthode ou une fonction globale avec la signature spécifiée et retourne un jeton pour cette définition de méthode.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT DefineMethod (      
    [in]  mdTypeDef         td,   
    [in]  LPCWSTR           szName,   
    [in]  DWORD             dwMethodFlags,   
    [in]  PCCOR_SIGNATURE   pvSigBlob,   
    [in]  ULONG             cbSigBlob,   
    [in]  ULONG             ulCodeRVA,   
    [in]  DWORD             dwImplFlags,   
    [out] mdMethodDef      *pmd  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `td`  
 [in] Le `mdTypedef` jeton de la classe parente ou l’interface parente de la méthode. Définissez `td` à `mdTokenNil`, si vous définissez une fonction globale.  
  
 `szName`  
 [in] Nom de membre en Unicode.  
  
 `dwMethodFlags`  
 [in] Une valeur de la [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) énumération qui spécifie les attributs de la méthode ou une fonction globale.  
  
 `pvSigBlob`  
 [in] La signature de méthode. La signature est rendue persistante fourni. Si vous devez spécifier des informations supplémentaires pour tous les paramètres, utilisez le [IMetaDataEmit::SetParamProps](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setparamprops-method.md) (méthode).  
  
 `cbSigBlob`  
 [in] Le nombre d’octets dans `pvSigBlob`.  
  
 `ulCodeRVA`  
 [in] L’adresse du code.  
  
 `dwImplFlags`  
 [in] Une valeur de la [CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) énumération qui spécifie les fonctionnalités d’implémentation de la méthode.  
  
 `pmd`  
 [out] Jeton membre.  
  
## <a name="remarks"></a>Remarques  
 L’API de métadonnées garantit la persistance des méthodes dans le même ordre que l’appelant les émet pour une classe englobante donnée ou une interface, ce qui est spécifié dans le `td` paramètre.  
  
 Informations supplémentaires concernant l’utilisation de `DefineMethod` et paramètres particuliers sont répertoriés ci-dessous.  
  
## <a name="slots-in-the-v-table"></a>Emplacements dans la V-table  
 Le runtime utilise des définitions de méthode pour configurer les emplacements vtable. Dans le cas où un ou plusieurs emplacements doivent être ignorés, par exemple pour conserver la parité avec une disposition d’interface COM, une méthode factice est définie pour accepter l’emplacement ou les emplacements dans la v-table ; définir le `dwMethodFlags` à la `mdRTSpecialName` valeur de la [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) énumération et spécifiez le nom de :  
  
 _VtblGap\<*SequenceNumber*>\<\_*NombreEmplacements*>  
  
 où *SequenceNumber* est le numéro de séquence de la méthode et *NombreEmplacements* est le nombre d’emplacements à ignorer dans la v-table. Si *NombreEmplacements* est omis, 1 est supposé. Ces méthodes factices ne peuvent pas être appelées à partir du code managé ou non managé et toute tentative de les appeler à partir du code managé ou non managé, génère une exception. Son seul objectif consiste à mettre l’espace dans la v-table générés par le runtime pour l’intégration de COM.  
  
## <a name="duplicate-methods"></a>Méthodes en double  
 Vous ne devez pas définir des méthodes dupliquées. Autrement dit, vous ne devez pas appeler `DefineMethod` avec un jeu de doublon de valeurs dans le `td`, `wzName`, et `pvSig` paramètres. (Ces trois paramètres définissent de façon unique la méthode.). Toutefois, vous pouvez utiliser un triple en double si, pour l’une des définitions de méthode, vous définissez la `mdPrivateScope` bit dans le `dwMethodFlags` paramètre. (Le `mdPrivateScope` bits signifie que le compilateur n’émet pas d’une référence à cette définition de méthode.)  
  
## <a name="method-implementation-information"></a>Informations d’implémentation (méthode)  
 Plus d’informations sur l’implémentation de méthode ne sont souvent pas connus au moment où que la méthode est déclarée. Par conséquent, vous n’avez pas besoin de passer des valeurs dans le `ulCodeRVA` et `dwImplFlags` paramètres lors de l’appel `DefineMethod`. Les valeurs peuvent être fournies ultérieurement via [IMetaDataEmit::SetMethodImplFlags](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmethodimplflags-method.md) ou [IMetaDataEmit::SetRVA](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setrva-method.md), le cas échéant.  
  
 Dans certaines situations, telles que l’appel de plate-forme (PInvoke) ou des scénarios COM interop, le corps de méthode n’est pas fourni, et `ulCodeRVA` doit être égale à zéro. Dans ce cas, la méthode ne doit pas être identifiée comme abstract, étant donné que le runtime utilise pour localiser l’implémentation.  
  
## <a name="defining-a-method-for-pinvoke"></a>Définition d’une méthode pour PInvoke  
 Pour chaque fonction non managée à appeler via PInvoke, vous devez définir une méthode managée qui représente la fonction non managée cible. Pour définir la méthode managée, utilisez `DefineMethod` avec certains des paramètres définis pour certaines valeurs, en fonction de la façon dont PInvoke est utilisée :  
  
-   PInvoke true : implique l’appel d’une méthode non managée externe qui réside dans une DLL non managée.  
  
-   PInvoke local : implique l’appel d’une méthode non managée native qui est incorporée dans le module managé actuel.  
  
 Les paramètres figurent dans le tableau suivant.  
  
|Paramètre|Valeurs pour PInvoke true|Valeurs pour PInvoke local|  
|---------------|-----------------------------|------------------------------|  
|`dwMethodFlags`||Définissez `mdStatic`; effacer `mdSynchronized` et `mdAbstract`.|  
|`pvSigBlob`|Une signature de méthode du common language runtime (CLR) valide avec des paramètres valides des types managés.|Une signature de méthode CLR valide avec des paramètres valides des types managés.|  
|`ulCodeRVA`||0|  
|`dwImplFlags`|Définissez `miCil` et `miManaged`.|Définissez `miNative` et `miUnmanaged`.|  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor.h  
  
 **Bibliothèque :** utilisé en tant que ressource dans MSCorEE.dll  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [IMetaDataEmit (Interface)](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [IMetaDataEmit2 (Interface)](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
