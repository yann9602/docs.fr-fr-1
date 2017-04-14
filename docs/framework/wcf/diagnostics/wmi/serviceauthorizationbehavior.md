---
title: "ServiceAuthorizationBehavior | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 77dad8e8-fea4-4d1c-b366-2f01a2a87f78
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# ServiceAuthorizationBehavior
ServiceAuthorizationBehavior  
  
## Syntaxe  
  
```  
class ServiceAuthorizationBehavior : Behavior  
{  
  boolean ImpersonateCallerForAllOperations;  
  string PrincipalPermissionMode;  
  string RoleProvider;  
  string ServiceAuthorizationManager;  
};  
```  
  
## Méthodes  
 La classe ServiceAuthorizationBehavior ne définit pas de méthode.  
  
## Propriétés  
 La classe ServiceAuthorizationBehavior a les propriétés suivantes :  
  
### ImpersonateCallerForAllOperations  
 Type de données : booléen  
  
 Type d'accès : lecture seule  
  
 Valeur qui contrôle si le service essaie d'emprunter l'identité à l'aide des informations d'identification fournies par le message entrant.  
  
### PrincipalPermissionMode  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Principal de sécurité utilisée pour effectuer les opérations sur le serveur.  
  
### RoleProvider  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Nom du fournisseur de rôles ASP.NET.  
  
### ServiceAuthorizationManager  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Gestionnaire d'autorisations utilisé pour l'autorisation personnalisée.  
  
## Spécifications  
  
|MOF|Déclaré dans Servicemodel.mof.|  
|---------|------------------------------------|  
|Espace de noms|Défini dans root\\ServiceModel|  
  
## Voir aussi  
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>