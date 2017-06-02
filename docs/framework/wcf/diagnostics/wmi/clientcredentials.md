---
title: "ClientCredentials | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 41dffd6b-8f14-4fed-aefb-2a1bb168efb3
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# ClientCredentials
ClientCredentials  
  
## Syntaxe  
  
```  
class ClientCredentials : Behavior  
{  
  string ClientCertificate;  
  string HttpDigest;  
  string IssuedToken;  
  string Peer;  
  string ServiceCertificate;  
  boolean SupportInteractive;  
  string UserName;  
  string Windows;  
};  
```  
  
## Méthodes  
 La classe ClientCredentials ne définit pas de méthode.  
  
## Propriétés  
 La classe ClientCredentials a les propriétés suivantes :  
  
### ClientCertificate  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Certificat X.509 que le client utilise pour s'authentifier auprès du service.  
  
### HttpDigest  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Informations d'identification Http Digest actuelles.  
  
### IssuedToken  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Adresse de point de terminaison et liaison utilisées pour contacter le service de jetons de sécurité local.  
  
### Peer  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Informations d'identification que le nœud d'homologue utilise pour s'authentifier auprès d'autres nœuds dans la maille.  
  
### ServiceCertificate  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Certificat X.509 du service.  
  
### SupportInteractive  
 Type de données : booléen  
  
 Type d'accès : lecture seule  
  
 Valeur booléenne qui spécifie si les informations d'identification prennent en charge la négociation interactive.  
  
### UserName  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Nom d'utilisateur et mot de passe que le client utilise pour s'authentifier auprès du service.  
  
### Windows  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Informations d'identification que le client utilise pour s'authentifier auprès du service.  
  
## Spécifications  
  
|MOF|Déclaré dans Servicemodel.mof.|  
|---------|------------------------------------|  
|Espace de noms|Défini dans root\\ServiceModel|  
  
## Voir aussi  
 <xref:System.ServiceModel.Description.ClientCredentials>