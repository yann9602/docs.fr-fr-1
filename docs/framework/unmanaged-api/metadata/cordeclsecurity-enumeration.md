---
title: "CorDeclSecurity, énumération"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDeclSecurity
api_location: mscoree.dll
api_type: COM
f1_keywords: CorDeclSecurity
helpviewer_keywords: CorDeclSecurity enumeration [.NET Framework metadata]
ms.assetid: 864f1267-d267-4696-8df7-1f83f8444d6f
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 30fd7ca2cf7962c6cadb43d4d8e3031b59292463
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="cordeclsecurity-enumeration"></a>CorDeclSecurity, énumération
Spécifie les actions de sécurité qui peuvent être effectuées à l’aide de la sécurité déclarative.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef enum CorDeclSecurity {  
  
    dclActionMask               =   0x001f,  
    dclActionNil                =   0x0000,  
    dclRequest                  =   0x0001,  
    dclDemand                   =   0x0002,  
    dclAssert                   =   0x0003,  
    dclDeny                     =   0x0004,  
    dclPermitOnly               =   0x0005,  
    dclLinktimeCheck            =   0x0006,  
    dclInheritanceCheck         =   0x0007,  
    dclRequestMinimum           =   0x0008,  
    dclRequestOptional          =   0x0009,  
    dclRequestRefuse            =   0x000a,  
    dclPrejitGrant              =   0x000b,  
    dclPrejitDenied             =   0x000c,  
    dclNonCasDemand             =   0x000d,  
    dclNonCasLinkDemand         =   0x000e,  
    dclNonCasInheritance        =   0x000f,  
    dclLinkDemandChoice         =   0x0010,  
    dclInheritanceDemandChoice  =   0x0011,  
    dclDemandChoice             =   0x0012,  
    dclMaximumValue             =   0x0012  
  
} CorDeclSecurity;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`dclActionMask`|Réservé.|  
|`dclActionNil`|Réservé.|  
|`dclRequest`|Réservé.|  
|`dclDemand`|Tous les appelants figurant plus haut dans la pile des appels doivent disposer de l’autorisation spécifiée par l’objet d’autorisation actuel.|  
|`dclAssert`|Le code appelant peut accéder à la ressource identifiée par l’objet d’autorisation actuel, même si les appelants plus hauts dans la pile n’ont pas reçus l’autorisation d’accéder à la ressource|  
|`dclDeny`|La possibilité d’accéder à la ressource spécifiée par l’objet d’autorisation en cours est refusée aux appelants, même si elles ont reçu l’autorisation d’y accéder.|  
|`dclPermitOnly`|Seules les ressources spécifiées par l’objet d’autorisation sont accessibles, même si le code a reçu l’autorisation d’accéder à d’autres ressources.|  
|`dclLinktimeCheck`|L’appelant immédiat est nécessaire pour ont reçu l’autorisation spécifiée pour une période donnée.|  
|`dclInheritanceCheck`|La classe dérivée hérite d’une autre classe ou la substitution d’une méthode est nécessaire de disposer de l’autorisation spécifiée.|  
|`dclRequestMinimum`|L’appelant peut demander des autorisations minimales requises pour l’exécution de code. Cette action ne peut être utilisée que dans la portée de l’assembly.|  
|`dclRequestOptional`|L’appelant peut demander des autorisations supplémentaires qui sont facultatives (non requis pour exécuter). Cette requête refuse implicitement toutes les autres autorisations qui ne sont pas spécifiquement demandées. Cette action ne peut être utilisée que dans la portée de l’assembly.|  
|`dclRequestRefuse`|Peut demander l’appelant des autorisations qui peuvent être utilisées abusivement ne soient pas accordée. Cette action ne peut être utilisée que dans la portée de l’assembly.|  
|`dclPrejitGrant`|Réservé.|  
|`dclPrejitDenied`|Réservé.|  
|`dclNonCasDemand`|Réservé.|  
|`dclNonCasLinkDemand`|L’appelant immédiat doit avoir reçu l’autorisation spécifiée.|  
|`dclNonCasInheritance`|Réservé.|  
|`dclLinkDemandChoice`|Réservé.|  
|`dclInheritanceDemandChoice`|Réservé.|  
|`dclDemandChoice`|Réservé.|  
|`dclMaximumValue`|Réservé.|  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorHdr.h  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations de métadonnées](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
