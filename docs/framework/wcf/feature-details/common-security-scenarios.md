---
title: "Sc&#233;narios de s&#233;curit&#233; courants | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "sécurité (WCF), scénarios"
ms.assetid: 201923b5-5162-4a8a-8d4c-e7bd242748d5
caps.latest.revision: 18
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 18
---
# Sc&#233;narios de s&#233;curit&#233; courants
Les rubriques de cette section présentent un certain nombre de configurations de sécurité de service et client possibles.Les configurations varient selon un certain nombre de facteurs.Par exemple, si un service ou un client est sur un intranet, ou si la sécurité est fournie par Windows ou un transport \(tel que HTTPS\).  
  
## Dans cette section  
 [Service et client Internet non sécurisés](../../../../docs/framework/wcf/feature-details/internet-unsecured-client-and-service.md)  
 Exemple de client\/service public non sécurisé.  
  
 [Service et client intranet non sécurisés](../../../../docs/framework/wcf/feature-details/intranet-unsecured-client-and-service.md)  
 Service [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] de base développé pour fournir des informations sur un réseau privé sécurisé à une application [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
 [Sécurité de transport avec l'authentification de base](../../../../docs/framework/wcf/feature-details/transport-security-with-basic-authentication.md)  
 L'application autorise les clients à se connecter à l'aide de l'authentification personnalisée.  
  
 [Sécurité de transport avec l'authentification Windows](../../../../docs/framework/wcf/feature-details/transport-security-with-windows-authentication.md)  
 Présente un client\/service sécurisé par la sécurité Windows.  
  
 [Sécurité des transports avec un client anonyme](../../../../docs/framework/wcf/feature-details/transport-security-with-an-anonymous-client.md)  
 Ce scénario utilise la sécurité de transport \(tel que HTTPS\) pour assurer la confidentialité et l'intégrité.  
  
 [Sécurité de transport avec l'authentification par certificat](../../../../docs/framework/wcf/feature-details/transport-security-with-certificate-authentication.md)  
 Présente un client\/service sécurisé par un certificat.  
  
 [Sécurité de message avec un client anonyme](../../../../docs/framework/wcf/feature-details/message-security-with-an-anonymous-client.md)  
 Présente un client\/service sécurisé par la sécurité de message [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
 [Sécurité de message avec un client de type Nom d'utilisateur](../../../../docs/framework/wcf/feature-details/message-security-with-a-user-name-client.md)  
 Le client est une application Windows Forms qui autorise les clients à se connecter à l'aide d'un mot de passe et d'un nom d'utilisateur de domaine.  
  
 [Sécurité de message avec un client de certificat](../../../../docs/framework/wcf/feature-details/message-security-with-a-certificate-client.md)  
 Les serveurs ont des certificats, et chaque client a un certificat.Un contexte de sécurité est établi via la négociation TLS \(Transport Layer Security\).  
  
 [Sécurité de message avec un client Windows](../../../../docs/framework/wcf/feature-details/message-security-with-a-windows-client.md)  
 Variante du client de certificat.Les serveurs ont des certificats, et chaque client a un certificat.Un contexte de sécurité est établi via la négociation TLS.  
  
 [Sécurité de message avec un client Windows sans négociation d'informations d'identification](../../../../docs/framework/wcf/feature-details/message-security-with-a-windows-client-without-credential-negotiation.md)  
 Présente un client\/service sécurisé par un domaine Kerberos.  
  
 [Sécurité de message avec certificats mutuels](../../../../docs/framework/wcf/feature-details/message-security-with-mutual-certificates.md)  
 Les serveurs ont des certificats, et chaque client a un certificat.Le certificat de serveur est distribué avec l'application et est disponible hors bande.  
  
 [Sécurité de message avec jetons émis](../../../../docs/framework/wcf/feature-details/message-security-with-issued-tokens.md)  
 Sécurité fédérée qui permet d'établir la confiance entre des domaines indépendants.  
  
 [Sous\-système approuvé](../../../../docs/framework/wcf/feature-details/trusted-subsystem.md)  
 Un client accède à un ou plusieurs services Web distribués sur un réseau.Les services Web accèdent aux ressources supplémentaires \(telles que les bases de données ou autres services Web\) qui doivent être sécurisées.  
  
## Référence  
 <xref:System.ServiceModel>  
  
## Rubriques connexes  
 [Autorisation](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
  
 [Vue d'ensemble de la sécurité](../../../../docs/framework/wcf/feature-details/security-overview.md)  
  
 [Sécurité](../../../../docs/framework/wcf/feature-details/security.md)  
  
 [Liaisons et sécurité](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)  
  
 [Sécurisation des services et des clients](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
  
 [Authentification](../../../../docs/framework/wcf/feature-details/authentication-in-wcf.md)  
  
 [Autorisation](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
  
 [Fédération et jetons émis](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
  
 [Audit](../../../../docs/framework/wcf/feature-details/auditing-security-events.md)  
  
## Voir aussi  
 [Aide sur la sécurité et meilleures pratiques](../../../../docs/framework/wcf/feature-details/security-guidance-and-best-practices.md)   
 [Modèle de sécurité pour Windows Server AppFabric](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)