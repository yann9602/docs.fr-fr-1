---
title: "ICorDebugModule2::ApplyChanges, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugModule2.ApplyChanges
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugModule2::ApplyChanges
helpviewer_keywords:
- ApplyChanges method [.NET Framework debugging]
- ICorDebugModule2::ApplyChanges method [.NET Framework debugging]
ms.assetid: 96fa3406-6a6f-41a1-88c6-d9bc5d1a16d1
topic_type: apiref
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 51c14bd6937d4b588227f7cf748c9a8052fb449c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugmodule2applychanges-method"></a>ICorDebugModule2::ApplyChanges, méthode
Applique les modifications dans les métadonnées et les modifications dans le code MSIL (intermediate language) de Microsoft pour le processus en cours d’exécution.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT ApplyChanges (  
    [in] ULONG                       cbMetadata,  
    [in, size_is(cbMetadata)] BYTE   pbMetadata[],  
    [in] ULONG                       cbIL,  
    [in, size_is(cbIL)] BYTE         pbIL[]  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `cbMetadata`  
 [in] Taille, en octets, des métadonnées delta.  
  
 `pbMetadata`  
 [in] Mémoire tampon qui contient les métadonnées delta. L’adresse de la mémoire tampon est retournée à partir de la [IMetaDataEmit2::SaveDeltaToMemory](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatomemory-method.md) (méthode).  
  
 Les adresses virtuelles relatives (RVA) dans les métadonnées doivent être par rapport au début du code MSIL.  
  
 `cbIL`  
 [in] Taille, en octets, du code MSIL delta.  
  
 `pbIL`  
 [in] Mémoire tampon qui contient le code MSIL mis à jour.  
  
## <a name="remarks"></a>Remarques  
 Le `pbMetadata` paramètre est dans un format de métadonnées delta spécial (comme sortie par [IMetaDataEmit2::SaveDeltaToMemory](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatomemory-method.md)). `pbMetadata`utilise les métadonnées précédentes comme base et décrit les différentes modifications à appliquer à cette base.  
  
 En revanche, le `pbIL[`] paramètre contient le nouveau code MSIL pour la méthode de mise à jour et est destiné à remplacer complètement le code MSIL précédent de cette méthode  
  
 Lorsque le delta MSIL et les métadonnées ont été créés dans la mémoire du débogueur, le débogueur appelle `ApplyChanges` pour envoyer les modifications dans le common language runtime (CLR). Le runtime met à jour ses tables de métadonnées, place le nouveau MSIL dans le processus et configure la compilation du nouveau MSIL un juste-à-temps (JIT). Lorsque les modifications ont été appliquées, le débogueur doit appeler [IMetaDataEmit2::ResetENCLog](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-resetenclog-method.md) pour préparer la session d’édition suivante. Le débogueur peut ensuite continuer le processus.  
  
 Chaque fois que le débogueur appelle `ApplyChanges` sur un module qui a des métadonnées delta, il doit également appeler [IMetaDataEmit::ApplyEditAndContinue](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-applyeditandcontinue-method.md) avec les mêmes métadonnées delta sur toutes ses copies des métadonnées de ce module, à l’exception de la copie utilisé pour émettre les modifications. Si une copie des métadonnées devient une certaine manière-synchronisé avec les métadonnées, le débogueur peut toujours supprimer cette copie et obtenir une nouvelle copie.  
  
 Si le `ApplyChanges` méthode échoue, le débogage session est dans un état non valide et doit être redémarrée.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
