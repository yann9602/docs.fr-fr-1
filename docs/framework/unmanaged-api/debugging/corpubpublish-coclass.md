---
title: CorpubPublish (coclasse)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorpubPublish Coclass
api_location: mscoree.dll
api_type: COM
f1_keywords: CorpubPublish
helpviewer_keywords: CorpubPublish coclass [.NET Framework debugging]
ms.assetid: 191015da-f54a-4bac-a28a-1de7ab3c3428
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f3dec1175715bdbddc3c975924e91e238fa6d5f3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="corpubpublish-coclass"></a>CorpubPublish (coclasse)
Fournit les interfaces pour la publication d'informations sur les domaines d'application et les processus.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
coclass CorpubPublish {  
    [default] interface ICorPublish;  
    interface           ICorPublishProcess;  
    interface           ICorPublishAppDomain;  
    interface           ICorPublishProcessEnum;  
    interface           ICorPublishAppDomainEnum;  
};  
```  
  
## <a name="interfaces"></a>Interfaces  
  
|Interface|Description|  
|---------------|-----------------|  
|[ICorPublish, interface](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md)|Fournit des méthodes pour la publication des informations sur les processus et les domaines d’application dans ces processus.|  
|[ICorPublishAppDomain, interface](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md)|Représente et fournit des informations sur un domaine d’application dans un processus.|  
|[ICorPublishAppDomainEnum, interface](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md)|Fournit des méthodes qui parcourent une collection de domaines d’application qui existent actuellement dans un processus.|  
|[ICorPublishProcess, interface](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)|Représente un processus qui s’exécute sur un ordinateur.|  
|[ICorPublishProcessEnum, interface](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md)|Fournit des méthodes qui parcourent une collection de processus qui s’exécutent sur un ordinateur.|  
  
## <a name="remarks"></a>Notes  
 Un scénario classique de publication implique un développeur qui souhaite déboguer du code managé qui s’exécute sur un ordinateur dans un domaine d’application. L’environnement d’hébergement peut exécuter plusieurs domaines d’application dans un processus. Le développeur souhaite utiliser une interface utilisateur graphique ou autres moyens pour répertorier tous les processus qui sont exécutent sur l’ordinateur et choisir un processus spécifique. La liste doit inclure tous les domaines d’application dans les processus qui sont en cours d’exécution du code managé. Le développeur peut ensuite identifier le domaine d’application spécifique et joindre un débogueur à ce domaine.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorPub.idl  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Débogage](../../../../docs/framework/unmanaged-api/debugging/index.md)
