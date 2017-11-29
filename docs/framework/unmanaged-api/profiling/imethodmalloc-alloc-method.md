---
title: "IMethodMalloc::Alloc, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMethodMalloc.Alloc
api_location: mscorwks.dll
api_type: COM
f1_keywords: IMethodMalloc::Alloc
helpviewer_keywords:
- IMethodMalloc::Alloc method [.NET Framework profiling]
- Alloc method, IMethodMalloc interface [.NET Framework profiling]
ms.assetid: 8653bd4c-2290-43d2-a3e1-cbbd50033f4f
topic_type: apiref
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: ae0fa84c08cb8e366db36b6727a3058f24789801
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="imethodmallocalloc-method"></a>IMethodMalloc::Alloc, méthode
Tente d’allouer une quantité de mémoire spécifiée pour un nouveau corps de fonction MSIL (intermediate language).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
PVOID Alloc (  
    [in] ULONG   cb  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `cb`  
 [in] Le nombre d’octets à allouer pour le corps de méthode.  
  
## <a name="remarks"></a>Remarques  
 La mémoire allouée commencera à une adresse supérieure à l’adresse de base du module qui est associé à cet allocateur. En d’autres termes, chaque allocateur est créé pour un module particulier et tentera d’allouer la mémoire à un offset positif à partir de son adresse de base. Si `Alloc` ne parvient pas à allouer le nombre requis d’octets à une adresse supérieure à l’adresse de base du module, il retourne E_OUTOFMEMORY, quelle que soit la quantité réelle de l’espace mémoire disponible.  
  
 Le `Alloc` méthode doit être utilisée conjointement avec la [ICorProfilerInfo::SetILFunctionBody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md) (méthode).  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** WindSee [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [IMethodMalloc (Interface)](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-interface.md)
