---
title: "ServiceCredentials | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9c780793-4785-46f7-add9-ac1ebeadb614
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# ServiceCredentials
ServiceCredentials  
  
## Syntaxe  
  
```  
class ServiceCredentials : Behavior  
{  
  string ClientCertificate;  
  string IssuedTokenAuthentication;  
  string Peer;  
  string SecureConversationAuthentication;  
  string ServiceCertificate;  
  string UserNameAuthentication;  
  string WindowsAuthentication;  
};  
```  
  
## Méthodes  
 La classe ServiceCredentials ne définit aucune méthode.  
  
## Propriétés  
 La classe ServiceCredentials a les propriétés suivantes :  
  
### ClientCertificate  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Paramètres d'authentification et d'approvisionnement des certificats clients pour ce service.  
  
### IssuedTokenAuthentication  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Paramètres actuels d'authentification de jeton émis pour ce service.  
  
### Peer  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Authentification des informations d'identification actuelles et fourniture des paramètres à utiliser par les points de terminaison de transport d'homologue.  
  
### SecureConversationAuthentication  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Spécifie les paramètres actuels de conversation sécurisée.  
  
### ServiceCertificate  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Certificat associé à ce service.  
  
### UserNameAuthentication  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Paramètres de nom d'utilisateur\/mot de passe pour ce service.  
  
### WindowsAuthentication  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Paramètres d'authentification Windows pour ce service.  
  
## Spécifications  
  
|MOF|Déclaré dans Servicemodel.mof.|  
|---------|------------------------------------|  
|Espace de noms|Défini dans root\\ServiceModel|  
  
## Voir aussi  
 <xref:System.ServiceModel.Description.ServiceCredentials>