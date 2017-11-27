---
title: "IMetaDataDispenserEx::SetOption, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataDispenserEx.SetOption
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataDispenserEx::SetOption
helpviewer_keywords:
- IMetaDataDispenserEx::SetOption method [.NET Framework metadata]
- SetOption method [.NET Framework metadata]
ms.assetid: 9f1c7ccd-7fb2-41d8-aa00-24b823376527
topic_type: apiref
caps.latest.revision: "20"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a58ac4379522c13125f98df058cd67bceb7cdbd1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadatadispenserexsetoption-method"></a>IMetaDataDispenserEx::SetOption, méthode
Définit l’option spécifiée à une valeur donnée pour la portée de métadonnées actuelle. L’option contrôle la gestion des appels à la portée de métadonnées actuelle.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SetOption (  
    [in] REFGUID optionId,   
    [in] const VARIANT *pValue  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `optionId`  
 [in] Pointeur vers un GUID qui spécifie l’option à définir.  
  
 `pValue`  
 [in] La valeur à utiliser pour définir l’option. Le type de cette valeur doit être une variante de type de l’option spécifiée.  
  
## <a name="remarks"></a>Remarques  
 Le tableau suivant répertorie les GUID disponibles qui le `optionId` paramètre peut pointer vers et les valeurs valides correspondantes pour le `pValue` paramètre.  
  
|GUID|Description|`pValue`Paramètre|  
|----------|-----------------|------------------------|  
|MetaDataCheckDuplicatesFor|Contrôle quels éléments sont activés pour les doublons. Chaque fois que vous appelez une [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) méthode qui crée un nouvel élément, vous pouvez demander à la méthode pour vérifier si l’élément existe déjà dans la portée actuelle. Par exemple, vous pouvez vérifier l’existence de `mdMethodDef` éléments ; dans ce cas, lorsque vous appelez [IMetaDataEmit::DefineMethod](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethod-method.md), il vérifie que la méthode n’existe pas déjà dans la portée actuelle. Cette vérification utilise la clé qui identifie de façon unique une méthode donnée : parent de type, nom et signature.|Doit être un variant de type UI4 et doit contenir une combinaison des valeurs de la [CorCheckDuplicatesFor](../../../../docs/framework/unmanaged-api/metadata/corcheckduplicatesfor-enumeration.md) énumération.|  
|MetaDataRefToDefCheck|Contrôle quels éléments référencés est convertis en définitions. Par défaut, le moteur de métadonnées permettra d’optimiser le code en convertissant un élément référencé à sa définition si l’élément référencé est réellement définie dans la portée actuelle.|Doit être un variant de type UI4 et doit contenir une combinaison des valeurs de la [CorRefToDefCheck](../../../../docs/framework/unmanaged-api/metadata/correftodefcheck-enumeration.md) énumération.|  
|MetaDataNotificationForTokenMovement|Contrôles quel jeton remappe qui se produisent pendant une fusion des métadonnées génèrent des rappels. Utilisez le [IMetaDataEmit::SetHandler](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md) méthode pour établir vos [IMapToken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md) interface.|Doit être un variant de type UI4 et doit contenir une combinaison des valeurs de la [CorNotificationForTokenMovement](../../../../docs/framework/unmanaged-api/metadata/cornotificationfortokenmovement-enumeration.md) énumération.|  
|MetaDataSetENC|Contrôle le comportement de modifier et continuer (ENC). Un seul mode de comportement peut être défini à la fois.|Doit être un variant de type UI4 et doit contenir une valeur de la [CorSetENC](../../../../docs/framework/unmanaged-api/metadata/corsetenc-enumeration.md) énumération. La valeur n’est pas un masque de bits.|  
|MetaDataErrorIfEmitOutOfOrder|Contrôles quelles erreurs émis--ordonnés génèrent des rappels. Émission de métadonnées en désordre n’est pas irrécupérable ; Toutefois, si vous émettez les métadonnées dans un ordre préconisé par le moteur de métadonnées, les métadonnées sont le plus compacte et par conséquent peuvent être recherchées plus efficacement. Utilisez le `IMetaDataEmit::SetHandler` méthode pour établir vos [IMetaDataError](../../../../docs/framework/unmanaged-api/metadata/imetadataerror-interface.md) interface.|Doit être un variant de type UI4 et doit contenir une combinaison des valeurs de la [CorErrorIfEmitOutOfOrder](../../../../docs/framework/unmanaged-api/metadata/corerrorifemitoutoforder-enumeration.md) énumération.|  
|MetaDataImportOption|Contrôle quels types d’éléments qui ont été supprimés pendant un ENC sont récupérés par un énumérateur.|Doit être un variant de type UI4 et doit contenir une combinaison des valeurs de la [CorImportOptions, énumération](../../../../docs/framework/unmanaged-api/metadata/corimportoptions-enumeration.md) énumération.|  
|MetaDataThreadSafetyOptions|Contrôle si le moteur de métadonnées obtient des verrous, ce qui garantit la sécurité des threads du lecteur/enregistreur. Par défaut, le moteur suppose que l’accès est monothread par l’appelant, donc aucun verrou n’est obtenues. Les clients sont responsables de la maintenance de synchronisation des threads appropriée lors de l’utilisation de l’API de métadonnées.|Doit être un variant de type UI4 et doit contenir une valeur de la [CorThreadSafetyOptions](../../../../docs/framework/unmanaged-api/metadata/corthreadsafetyoptions-enumeration.md) énumération. La valeur n’est pas un masque de bits.|  
|MetaDataGenerateTCEAdapters|Contrôle si l’importateur de bibliothèque de types doit générer les adaptateurs d’événements fortement couplés (TCE) pour les conteneurs de point de connexion COM.|Doit être un variant de type BOOL. Si `pValue` a la valeur `true`, l’importateur de bibliothèque de types génère les adaptateurs TCE.|  
|MetaDataTypeLibImportNamespace|Spécifie un espace de noms par défaut pour la bibliothèque de types qui est en cours d’importation.|Doit être une valeur null ou un variant de type BSTR. Si `pValue` est une valeur null, l’espace de noms actuel a la valeur null ; sinon, l’espace de noms actuel a la valeur la chaîne qui est contenue dans le type du variant BSTR.|  
|MetaDataLinkerOptions|Contrôle si l’éditeur de liens doit générer un assembly ou un fichier de module .NET Framework.|Doit être un variant de type UI4 et doit contenir une combinaison des valeurs de la [CorLinkerOptions](../../../../docs/framework/unmanaged-api/metadata/corlinkeroptions-enumeration.md) énumération.|  
|MetaDataRuntimeVersion|Spécifie la version du common language runtime par rapport à laquelle cette image a été créée. La version est stockée sous forme de chaîne, telles que « v1.0.3705 ».|Doit être une valeur null, une valeur VT_EMPTY ou un variant de type BSTR. Si `pValue` est null, la version du runtime est définie avec la valeur null. Si `pValue` est VT_EMPTY, la version est définie sur une valeur par défaut, qui est tracée à partir de la version de Mscorwks.dll dans laquelle le code de métadonnées est en cours d’exécution. Dans le cas contraire, la version du runtime est définie à la chaîne qui est contenue dans le type du variant BSTR.|  
|MetaDataMergerOptions|Spécifie les options de fusion des métadonnées.|Doit être un variant de type UI4 et doit contenir une combinaison des valeurs de la `MergeFlags` énumération, qui est décrite dans le fichier CorHdr.h.|  
|MetaDataPreserveLocalRefs|Désactive l’optimisation des références locales dans des définitions.|Doit contenir une combinaison des valeurs de la [CorLocalRefPreservation](../../../../docs/framework/unmanaged-api/metadata/corlocalrefpreservation-enumeration.md) énumération.|  
  
## <a name="requirements"></a>Spécifications  
 **Plateforme :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor.h  
  
 **Bibliothèque :** utilisé en tant que ressource dans MsCorEE.dll  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [IMetaDataDispenserEx (Interface)](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)  
 [IMetaDataDispenser (Interface)](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
