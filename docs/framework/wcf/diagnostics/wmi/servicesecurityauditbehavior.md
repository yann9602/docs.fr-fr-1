---
title: ServiceSecurityAuditBehavior
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2c5809e7-5364-44ce-bc71-848be4672e2a
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 1ce712bbdb258c477a2ee56f47281b1a1d09ec54
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="servicesecurityauditbehavior"></a>ServiceSecurityAuditBehavior
ServiceSecurityAuditBehavior  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class ServiceSecurityAuditBehavior : Behavior  
{  
  string AuditLogLocation;  
  string MessageAuthenticationAuditLevel;  
  string ServiceAuthorizationAuditLevel;  
  boolean SuppressAuditFailure;  
};  
```  
  
## <a name="methods"></a>Méthodes  
 La classe ServiceSecurityAuditBehavior ne définit pas de méthode.  
  
## <a name="properties"></a>Propriétés  
 La classe ServiceSecurityAuditBehavior a les propriétés suivantes :  
  
### <a name="auditloglocation"></a>AuditLogLocation  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Emplacement du journal d'audit.  
  
### <a name="messageauthenticationauditlevel"></a>MessageAuthenticationAuditLevel  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Type de niveau d'authentification de message utilisé pour enregistrer des événements d'audit.  
  
### <a name="serviceauthorizationauditlevel"></a>ServiceAuthorizationAuditLevel  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Types d'événement d'autorisation enregistrés dans le journal d'audit.  
  
### <a name="suppressauditfailure"></a>SuppressAuditFailure  
 Type de données : booléen  
  
 Type d'accès : lecture seule  
  
 Valeur booléenne qui spécifie le comportement permettant de supprimer les erreurs d'écriture dans le journal d'audit.  
  
## <a name="requirements"></a>Spécifications  
  
|MOF|Déclaré dans Servicemodel.mof.|  
|---------|-----------------------------------|  
|Espace de noms|Défini dans root\ServiceModel|  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>
