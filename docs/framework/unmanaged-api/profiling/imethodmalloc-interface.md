---
title: IMethodMalloc, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMethodMalloc
api_location: mscorwks.dll
api_type: COM
f1_keywords: IMethodMalloc
helpviewer_keywords: IMethodMalloc interface [.NET Framework profiling]
ms.assetid: 8c8ab5dc-557c-473a-82f2-6e403eca7dac
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: d246f329f80a76d2c93190fd663c7362418385f7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="imethodmalloc-interface"></a>IMethodMalloc, interface
Fournit une méthode pour allouer de la mémoire pour un nouveau corps de fonction MSIL (intermediate language).  
  
> [!NOTE]
>  Le `IMethodMalloc` interface est un allocateur de mémoire simple. Elle permet à allouer de la mémoire, mais ne pas pour le libérer.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[Alloc (méthode)](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-alloc-method.md)|Tente d’allouer une quantité de mémoire spécifiée pour un nouveau corps de fonction MSIL.|  
  
## <a name="remarks"></a>Remarques  
 Chaque allocateur est spécifique au module et garantit que le corps de fonction sera à un offset positif à partir de la base du module. Mémoire au-dessus de la base d’un module peut être précieuse, donc l’allocateur doit être utilisé pour allouer de la mémoire uniquement pour un corps de fonction.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de profilage](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
