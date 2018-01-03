---
title: ISymUnmanagedScope, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedScope
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedScope
helpviewer_keywords: ISymUnmanagedScope interface [.NET Framework debugging]
ms.assetid: 3db7a220-cfe9-4810-8ca8-a094bb8e0f5b
topic_type: apiref
caps.latest.revision: "5"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1e4d4c83b754945c126913a9d96db47966959fed
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedscope-interface"></a>ISymUnmanagedScope, interface
Représente une portée lexicale dans une méthode.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetChildren, méthode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getchildren-method.md)|Obtient les enfants de cette étendue.|  
|[GetEndOffset, méthode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getendoffset-method.md)|Obtient l’offset de fin pour cette étendue.|  
|[GetLocalCount, méthode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getlocalcount-method.md)|Obtient le nombre de variables locales définies dans cette portée.|  
|[GetLocals, méthode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getlocals-method.md)|Obtient les variables locales définies dans cette portée.|  
|[GetMethod, méthode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getmethod-method.md)|Obtient la méthode qui contient cette portée.|  
|[GetNamespaces, méthode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getnamespaces-method.md)|Obtient les espaces de noms qui sont utilisés dans cette portée.|  
|[GetParent, méthode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getparent-method.md)|Obtient la portée parent de cette étendue.|  
|[GetStartOffset, méthode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getstartoffset-method.md)|Obtient l’offset de début pour cette étendue.|  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces du magasin de symboles de diagnostics](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [ISymUnmanagedScope2, interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-interface.md)
