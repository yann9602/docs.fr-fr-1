---
title: "ICorProfilerInfo::SetILInstrumentedCodeMap, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.SetILInstrumentedCodeMap
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::SetILInstrumentedCodeMap
helpviewer_keywords:
- ICorProfilerInfo::SetILInstrumentedCodeMap method [.NET Framework profiling]
- SetILInstrumentedCodeMap method [.NET Framework profiling]
ms.assetid: bce1dcf8-b4ec-4e73-a917-f2df1ad49c8a
topic_type: apiref
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 35c87b98a8e0c02ab6f4bca7a4f7a16ff6839c6b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilerinfosetilinstrumentedcodemap-method"></a>ICorProfilerInfo::SetILInstrumentedCodeMap, méthode
Définit une carte de code pour la fonction spécifiée à l’aide des entrées de mappage Microsoft intermediate language (MSIL) spécifiées.  
  
> [!NOTE]
>  Dans le .NET Framework version 2.0, l’appel `SetILInstrumentedCodeMap` sur un `FunctionID` que représente une fonction générique dans un domaine d’application particulier affecte toutes les instances de cette fonction dans le domaine d’application.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SetILInstrumentedCodeMap(  
    [in]  FunctionID functionId,  
    [in]  BOOL       fStartJit,  
    [in]  ULONG      cILMapEntries,  
    [in, size_is(cILMapEntries)] COR_IL_MAP rgILMapEntries[]);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `functionId`  
 [in] L’ID de la fonction pour laquelle définir la carte de code.  
  
 `fStartJit`  
 [in] Valeur booléenne qui indique si l’appel à la `SetILInstrumentedCodeMap` (méthode) est le premier pour un particulier `FunctionID`. Définissez `fStartJit` à `true` dans le premier appel à `SetILInstrumentedCodeMap` pour une donnée `FunctionID`et `false` par la suite.  
  
 `cILMapEntries`  
 [in] Le nombre d’éléments dans le `cILMapEntries` tableau.  
  
 `rgILMapEntries`  
 [in] Tableau de structures COR_IL_MAP, dont chacun spécifie un offset MSIL.  
  
## <a name="remarks"></a>Remarques  
 Un profileur insère souvent des instructions dans le code source d’une méthode pour instrumenter cette méthode (par exemple, pour avertir lorsqu’une ligne source donnée est atteinte). `SetILInstrumentedCodeMap`permet à un profileur de mapper les instructions MSIL d’origine vers leurs nouveaux emplacements. Un profileur peut utiliser le [ICorProfilerInfo::GetILToNativeMapping](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md) méthode pour obtenir l’offset MSIL d’origine pour un offset natif donné.  
  
 Le débogueur suppose que chaque ancien offset fait référence à un offset MSIL dans le code MSIL non modifié d’origine, et que chaque nouvel offset fait référence à l’offset MSIL dans le nouveau code instrumenté. Le mappage doit être trié par ordre croissant. Pour exécuter pas à pas pour fonctionner correctement, suivez ces instructions :  
  
-   Ne réorganisez pas le code MSIL instrumenté.  
  
-   Ne supprimez pas le code MSIL d’origine.  
  
-   Inclure les entrées pour tous les points de séquence dans le fichier du programme (PDB) de la base de données dans le mappage. Le mappage n’interpole pas les entrées manquantes. Par conséquent, étant donné la carte suivante :  
  
     (0 ancien, 0 nouveau)  
  
     (5 anciens, 10 nouveaux)  
  
     (9 ancien, 20 nouveaux)  
  
    -   Un ancien offset de 0, 1, 2, 3 ou 4 sera mappé au nouvel offset 0.  
  
    -   Un ancien offset de 5, 6, 7 ou 8 sera mappé au nouvel offset 10.  
  
    -   Un ancien offset de 9 ou version ultérieure sera mappé au nouvel offset 20.  
  
    -   Un nouvel offset de 0, 1, 2, 3, 4, 5, 6, 7, 8 ou 9 sera mappé à l’ancien offset 0.  
  
    -   Un nouvel offset de 10, 11, 12, 13, 14, 15, 16, 17, 18 ou 19 sera mappé à l’ancien offset 5.  
  
    -   Un nouvel offset de 20 ou supérieur sera mappé à l’ancien offset 9.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [ICorProfilerInfo (Interface)](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
