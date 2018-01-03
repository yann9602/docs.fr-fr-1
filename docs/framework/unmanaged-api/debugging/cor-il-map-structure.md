---
title: COR_IL_MAP, structure
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_IL_MAP
api_location: mscordbi.dll
api_type: COM
f1_keywords: COR_IL_MAP
helpviewer_keywords: COR_IL_MAP structure [.NET Framework debugging]
ms.assetid: 534ebc17-963d-4b26-8375-8cd940281db3
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2e2772833d75ced2209896ca37cf6cf37fb965f1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="corilmap-structure"></a>COR_IL_MAP, structure
Spécifie des modifications dans le décalage relatif d'une fonction.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef struct _COR_IL_MAP {  
    ULONG32 oldOffset;   
    ULONG32 newOffset;   
    BOOL    fAccurate;  
} COR_IL_MAP;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`oldOffset`|L’ancien Microsoft offset intermediate language (MSIL) par rapport au début de la fonction.|  
|`newOffset`|Nouvel offset MSIL par rapport au début de la fonction.|  
|`fAccurate`|`true`Si le mappage est avéré précis ; dans le cas contraire, `false`.|  
  
## <a name="remarks"></a>Notes  
 Le format de la carte est le suivant : le débogueur suppose que `oldOffset` fait référence à un offset MSIL dans le code MSIL non modifié d’origine. Le `newOffset` paramètre fait référence à l’offset MSIL correspondant dans le nouveau code instrumenté.  
  
 Pour exécuter pas à pas pour fonctionner correctement, les conditions suivantes doivent être remplies :  
  
-   Le mappage doit être trié par ordre croissant.  
  
-   Code MSIL instrumenté ne doit pas être réorganisé.  
  
-   Code MSIL d’origine ne doit pas être supprimé.  
  
-   Le mappage doit inclure des entrées pour mapper tous les points de séquence dans le fichier du programme (PDB) de la base de données.  
  
 Le mappage n’interpole pas les entrées manquantes. L’exemple suivant montre un mappage et ses résultats.  
  
 Carte :  
  
-   ancien offset 0, nouvel offset 0  
  
-   ancien offset 5, nouvel offset 10  
  
-   ancien offset 9, nouvel offset 20  
  
 Résultats :  
  
-   Un ancien offset de 0, 1, 2, 3 ou 4 sera mappé à un nouvel offset de 0.  
  
-   Un ancien offset de 5, 6, 7 ou 8 sera mappé au nouvel offset 10.  
  
-   Un ancien offset de 9 ou version ultérieure sera mappé au nouvel offset 20.  
  
-   Un nouvel offset de 0, 1, 2, 3, 4, 5, 6, 7, 8 ou 9 sera mappé à l’ancien offset 0.  
  
-   Un nouvel offset de 10, 11, 12, 13, 14, 15, 16, 17, 18 ou 19 sera mappé à l’ancien offset 5.  
  
-   Un nouvel offset de 20 ou supérieur sera mappé à l’ancien offset 9.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorProf.idl  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Structures de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [Débogage](../../../../docs/framework/unmanaged-api/debugging/index.md)
