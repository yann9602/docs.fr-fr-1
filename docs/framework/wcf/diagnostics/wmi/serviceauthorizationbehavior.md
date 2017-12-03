---
title: ServiceAuthorizationBehavior
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 77dad8e8-fea4-4d1c-b366-2f01a2a87f78
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: fd22cd7e7783a67e7ad10371533eee680bd3af16
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="serviceauthorizationbehavior"></a>ServiceAuthorizationBehavior
ServiceAuthorizationBehavior  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class ServiceAuthorizationBehavior : Behavior  
{  
  boolean ImpersonateCallerForAllOperations;  
  string PrincipalPermissionMode;  
  string RoleProvider;  
  string ServiceAuthorizationManager;  
};  
```  
  
## <a name="methods"></a>Méthodes  
 La classe ServiceAuthorizationBehavior ne définit pas de méthode.  
  
## <a name="properties"></a>Propriétés  
 La classe ServiceAuthorizationBehavior a les propriétés suivantes :  
  
### <a name="impersonatecallerforalloperations"></a>ImpersonateCallerForAllOperations  
 Type de données : booléen  
  
 Type d'accès : lecture seule  
  
 Valeur qui contrôle si le service essaie d'emprunter l'identité à l'aide des informations d'identification fournies par le message entrant.  
  
### <a name="principalpermissionmode"></a>PrincipalPermissionMode  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Principal de sécurité utilisée pour effectuer les opérations sur le serveur.  
  
### <a name="roleprovider"></a>RoleProvider  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Nom du fournisseur de rôles ASP.NET.  
  
### <a name="serviceauthorizationmanager"></a>ServiceAuthorizationManager  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Gestionnaire d'autorisations utilisé pour l'autorisation personnalisée.  
  
## <a name="requirements"></a>Spécifications  
  
|MOF|Déclaré dans Servicemodel.mof.|  
|---------|-----------------------------------|  
|Espace de noms|Défini dans root\ServiceModel|  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
