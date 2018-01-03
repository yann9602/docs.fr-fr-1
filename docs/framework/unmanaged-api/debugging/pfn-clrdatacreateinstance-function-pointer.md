---
title: PFN_CLRDataCreateInstance (pointeur fonction)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: PFN_CLRDataCreateInstance
api_location: mscordbi.dll
api_type: COM
f1_keywords: PFN_CLRDataCreateInstance
helpviewer_keywords: PFN_CLRDataCreateInstance function pointer [.NET Framework debugging]
ms.assetid: 5c66ac57-d751-4de5-af9f-26ceb949af8b
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 98a966434332549d9ceb7f29de81e19fa1b2108f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="pfnclrdatacreateinstance-function-pointer"></a>PFN_CLRDataCreateInstance (pointeur fonction)
Pointe vers une fonction qui crée un objet d’interface pour l’élément cible spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef HRESULT (STDAPICALLTYPE* PFN_CLRDataCreateInstance) (  
    [in]  REFIID           iid,  
    [in]  ICLRDataTarget  *target,  
    [out] void           **iface  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `iid`  
 [in] Identificateur de l’interface pour être instancié.  
  
 `target`  
 [in] Un pointeur vers un implémenté par l’utilisateur [ICLRDataTarget](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md) objet qui représente l’élément cible pour lequel créer l’objet d’interface.  
  
 `iface`  
 [out] Pointeur vers l’adresse de l’objet d’interface retourné.  
  
## <a name="remarks"></a>Notes  
 Le `ICLRDataTarget` objet est implémenté par le writer de l’application de débogage. L’implémentation varie selon le type de l’élément cible qui est représenté. L’élément cible peut être un processus, vidage de la mémoire, ordinateur distant et ainsi de suite.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** ClrData.idl  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions statiques globales de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
