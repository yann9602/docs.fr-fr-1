---
title: "IMetaDataEmit::MergeEnd, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.MergeEnd
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::MergeEnd
helpviewer_keywords:
- MergeEnd method [.NET Framework metadata]
- IMetaDataEmit::MergeEnd method [.NET Framework metadata]
ms.assetid: 2d64315a-1af1-4c60-aedf-f8a781914aea
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 265fc007b5817e8dffd5846738a7a0003bbddf9d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitmergeend-method"></a>IMetaDataEmit::MergeEnd, méthode
Fusionne dans la portée actuelle toutes les portées de métadonnées spécifiées par un ou plusieurs appels précédents à [IMetaDataEmit::Merge](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-merge-method.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT MergeEnd ();  
```  
  
#### <a name="parameters"></a>Paramètres  
 Cette méthode ne prend aucun paramètre.  
  
## <a name="remarks"></a>Notes  
 Cette routine déclenche la fusion réelle des métadonnées, de toutes les portées spécifiées en faisant précéder les appels à d’importation `IMetaDataEmit::Merge`, dans la portée actuelle de la sortie.  
  
 Les conditions spéciales suivantes s’appliquent à la fusion :  
  
-   Identificateur de version de module (MVID) n’est jamais importé, car il est propre aux métadonnées dans la portée d’importation.  
  
-   Aucune propriété de module existante n’est remplacée.  
  
     Si les propriétés du module ont été déjà définies pour l’étendue actuelle, aucune propriété de module n’est importées. Toutefois, si les propriétés de module n’ont pas été définies dans la portée actuelle, ils sont importés qu’une seule fois, quand ils sont tout d’abord rencontrés. Si ces propriétés de module sont de nouveau rencontrées, ils sont des doublons. Si les valeurs de toutes les propriétés de module (sauf MVID) sont comparées et aucun doublon n’est trouvé, une erreur est générée.  
  
-   Pour les définitions de type (`TypeDef`), sans doublons sont fusionnées dans la portée actuelle. `TypeDef`vérifie les doublons sur chacun des objets *nom d’objet complet* + *GUID* + *numéro de version*. S’il existe une correspondance sur le nom ou le GUID et l’une des deux autres éléments est différent, une erreur est générée. Sinon, si les trois éléments correspondent, `MergeEnd` effectue une vérification rapide pour vérifier que les entrées sont des doublons ; sinon, une erreur est générée. Cette vérification rapide recherche :  
  
    -   Les mêmes déclarations de membre, qui se produisent dans le même ordre. Les membres qui sont signalés en tant que `mdPrivateScope` (consultez la [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) énumération) ne sont pas inclus dans ce contrôle ; ils sont fusionnés spécialement.  
  
    -   La même disposition de classe.  
  
     Cela signifie qu’un `TypeDef` objet doit toujours être complète et cohérente défini dans chaque portée de métadonnées dans laquelle elle est déclarée ; si ses implémentations de membres (pour une classe) sont réparties sur plusieurs unités de compilation, la définition complète est censée pour être dans chaque portée et incrémentielle pour chaque étendue. Par exemple, si les noms de paramètres sont pertinents pour le contrat, ils doivent être émis la même manière dans chaque portée ; Si elles ne sont pas pertinentes, ils ne doivent pas être émis dans les métadonnées.  
  
     L’exception est qu’un `TypeDef` objet peut avoir des membres incrémentiels signalés comme `mdPrivateScope`. Lorsqu’il les rencontre, `MergeEnd` les ajoute de façon incrémentielle à l’étendue actuelle sans tenir compte des doublons. Étant donné que le compilateur comprend la portée privée, le compilateur doit être responsable de l’application de règles.  
  
-   Les adresses virtuelles relatives (RVA) ne sont pas importées ou fusionnées ; le compilateur doit émettre de nouveau ces informations.  
  
-   Attributs personnalisés sont fusionnés uniquement lorsque l’élément auquel ils sont associés est fusionné. Par exemple, les attributs personnalisés associés à une classe sont fusionnées lors de la classe est rencontrée pour la première fois. Si les attributs personnalisés sont associés un `TypeDef` ou `MemberDef` qui est spécifique à l’unité de compilation (par exemple, l’horodatage d’une compilation membre), ils ne sont pas fusionnées et il incombe au compilateur de les supprimer ou mettre à jour ces métadonnées.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor.h  
  
 **Bibliothèque :** utilisé en tant que ressource dans MSCorEE.dll  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [IMetaDataEmit, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [IMetaDataEmit2, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
