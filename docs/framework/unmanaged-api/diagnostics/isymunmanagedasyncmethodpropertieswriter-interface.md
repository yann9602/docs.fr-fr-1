---
title: ISymUnmanagedAsyncMethodPropertiesWriter, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: caa71820-8058-4b6a-93a2-25ee757d92d3
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 99d61fdb9f7e3eb2bc10de7584061d8922bf9285
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedasyncmethodpropertieswriter-interface"></a>ISymUnmanagedAsyncMethodPropertiesWriter, interface
Permet de définir les informations de méthode async facultatif pour chaque symbole de méthode. Toujours utiliser avec une méthode ouverte ; Autrement dit, entre les appels à la [OpenMethod, méthode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md) et le [CloseMethod, méthode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```idl  
[object,uuid(FC073774-1739-4232-BD56-A027294BEC15),pointer_default(unique)]interface ISymUnmanagedAsyncMethodPropertiesWriter : IUnknown  
```  
  
## <a name="methods"></a>Méthodes  
 Cette interface contient les méthodes suivantes :  
  
|Méthode|Description|  
|------------|-----------------|  
|[DefineAsyncStepInfo, méthode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md)|Définissez un groupe d’async await des opérations dans la méthode actuelle.<br /><br /> Chaque décalage yield correspond à l’instruction de retour d’une expression await, identifiant un rendement potentiel. Chaque `breakpointMethod` / `breakpointOffset` paire identifie où l’opération asynchrone reprendra ; il peut être dans une autre méthode.|  
|[DefineCatchHandlerILOffset, méthode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md)|Définit le langage intermédiaire de décalage pour le gestionnaire catch de généré par le compilateur qui encapsule une méthode async.<br /><br /> Offset IL de la capture générée permet de gérer des catch comme s’il s’agissait de code non-utilisateur, même si elle peut se produire dans une méthode de code de l’utilisateur par le débogueur. En particulier, il est utilisé en réponse à une **CatchHandlerFound** événement d’exception.|  
|[DefineKickoffMethod, méthode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md)|Définit la méthode de démarrage qui lance l’opération asynchrone.|  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces du magasin de symboles de diagnostics](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
