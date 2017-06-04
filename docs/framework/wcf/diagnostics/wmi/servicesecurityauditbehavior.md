---
title: "ServiceSecurityAuditBehavior | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2c5809e7-5364-44ce-bc71-848be4672e2a
caps.latest.revision: 8
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 8
---
# ServiceSecurityAuditBehavior
ServiceSecurityAuditBehavior  
  
## Syntaxe  
  
```  
class ServiceSecurityAuditBehavior : Behavior  
{  
  string AuditLogLocation;  
  string MessageAuthenticationAuditLevel;  
  string ServiceAuthorizationAuditLevel;  
  boolean SuppressAuditFailure;  
};  
```  
  
## Méthodes  
 La classe ServiceSecurityAuditBehavior ne définit pas de méthode.  
  
## Propriétés  
 La classe ServiceSecurityAuditBehavior a les propriétés suivantes :  
  
### AuditLogLocation  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Emplacement du journal d'audit.  
  
### MessageAuthenticationAuditLevel  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Type de niveau d'authentification de message utilisé pour enregistrer des événements d'audit.  
  
### ServiceAuthorizationAuditLevel  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Types d'événement d'autorisation enregistrés dans le journal d'audit.  
  
### SuppressAuditFailure  
 Type de données : booléen  
  
 Type d'accès : lecture seule  
  
 Valeur booléenne qui spécifie le comportement permettant de supprimer les erreurs d'écriture dans le journal d'audit.  
  
## Spécifications  
  
|MOF|Déclaré dans Servicemodel.mof.|  
|---------|------------------------------------|  
|Espace de noms|Défini dans root\\ServiceModel|  
  
## Voir aussi  
 <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>