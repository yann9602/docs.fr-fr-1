---
title: "Utilisation de l&#39;emprunt d&#39;identit&#233; avec la s&#233;curit&#233; de transport | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 426df8cb-6337-4262-b2c0-b96c2edf21a9
caps.latest.revision: 12
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 12
---
# Utilisation de l&#39;emprunt d&#39;identit&#233; avec la s&#233;curit&#233; de transport
L'*emprunt d'identité* est la capacité d'une application serveur à prendre l'identité du client.Les services utilisent couramment l'emprunt d'identité lors de la validation de l'accès aux ressources.L'application serveur s'exécute à l'aide d'un compte de service, mais lorsque le serveur accepte une connexion cliente, il emprunte l'identité du client afin d'exécuter des contrôles d'accès à l'aide des informations d'identification du client.La sécurité de transport est un mécanisme permettant à la fois de passer des informations d'identification et sécuriser les communications à l'aide de ces informations.Cette rubrique décrit l'utilisation de la sécurité de transport dans [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] avec la fonctionnalité d'emprunt d'identité.[!INCLUDE[crabout](../../../../includes/crabout-md.md)] l'emprunt d'identité en utilisant la sécurité du message, consultez [Délégation et emprunt d'identité](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md).  
  
## Les cinq niveaux d'emprunt d'identité  
 La sécurité de transport utilise cinq niveaux d'emprunt d'identité, comme le décrit le tableau suivant.  
  
|Niveau d'emprunt d'identité|Description|  
|---------------------------------|-----------------|  
|Aucun|L'application serveur n'essaie pas d'emprunter l'identité du client.|  
|Anonyme|L'application serveur peut exécuter les contrôles d'accès à partir des informations d'identification du client, mais ne reçoit pas d'informations à propos de l'identité du client.Ce niveau d'emprunt d'identité n'est utile que pour les communications sur ordinateur, telles que les canaux nommés.L'utilisation de `Anonymous` avec une connexion à distance fait passer le niveau d'emprunt d'identité à Identifier.|  
|Identifier|L'application serveur connaît l'identité du client et peut exécuter les contrôles d'accès à partir des informations d'identification du client, mais ne peut pas emprunter l'identité du client.Le niveau Identifier est le niveau d'emprunt d'identité par défaut utilisé avec les informations d'identification SSPI dans [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] à moins que le fournisseur de jetons ne propose un niveau d'emprunt d'identité différent.|  
|Emprunter l'identité|L'application serveur peut accéder aux ressources de l'ordinateur serveur en tant que client en plus d'exécuter des contrôles d'accès.L'application serveur ne peut pas accéder aux ressources des ordinateurs distants à l'aide de l'identité du client parce que le jeton personnifié ne possède pas d'informations d'identification réseau.|  
|Déléguer|En plus d'avoir les mêmes fonctions que le niveau `Impersonate`, le niveau d'emprunt d'identité Déléguer permet également à l'application serveur d'accéder aux ressources des ordinateurs distants à l'aide de l'identité du client et de passer l'identité à d'autres applications.<br /><br /> **Important** Le compte de domaine du serveur doit être marqué comme approuvé pour la délégation pour que le contrôleur de domaine utilise ces fonctions supplémentaires.Ce niveau d'emprunt d'identité ne peut pas être utilisé avec les comptes de domaine du client marqués comme sensibles.|  
  
 Les niveaux utilisés le plus communément avec la sécurité de transport sont `Identify`  et `Impersonate`.Le niveaux `None` et `Anonymous` ne sont pas recommandés pour une utilisation par défaut, car de nombreux transports ne prennent pas en charge l'authentification avec ces niveaux.Le niveau `Delegate` est une fonctionnalité puissante qui doit être utilisée avec prudence.Seules les applications serveur approuvées doivent avoir l'autorisation de déléguer des informations d'identification.  
  
 L'utilisation de l'emprunt d'identité avec les niveaux `Impersonate` ou `Delegate` nécessite que l'application serveur ait le privilège `SeImpersonatePrivilege`.Une application a ce privilège par défaut si elle s'exécute sur un compte du groupe Administrateurs ou sur un compte avec un service SID \(service réseau, service local ou système local\).L'emprunt d'identité ne requiert pas l'authentification mutuelle du client et du serveur.Certains schémas d'authentification qui prennent en charge l'emprunt d'identité, tels que NTLM, ne peuvent pas être utilisés avec l'authentification mutuelle.  
  
## Problèmes spécifiques au transport avec l'emprunt d'identité  
 Le choix d'un transport dans [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] affecte les choix possibles pour l'emprunt d'identité.Cette section décrit les problèmes qui affectent le HTTP standard et les transport de canal nommé dans [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].Les transports personnalisés ont leurs propres restrictions quant à la prise en charge de l'emprunt d'identité.  
  
### Transport de canal nommé  
 Les éléments suivants sont utilisés avec le transport de canal nommé :  
  
-   Le transport de canal nommé est prévu uniquement pour une utilisation sur l'ordinateur local.Le transport de canal nommé dans [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] rejette explicitement les connexions d'ordinateur à ordinateur.  
  
-   Les canaux nommés ne peuvent pas être utilisés avec les niveaux d'emprunt d'identité `Impersonate` ou `Delegate`.Le canal nommé ne peut pas mettre en vigueur la garantie sur ordinateur à ces niveaux d'emprunt d'identité.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)] les canaux nommés, consultez [Choix d'un transport](../../../../docs/framework/wcf/feature-details/choosing-a-transport.md).  
  
### Transport HTTP  
 Les liaisons qui utilisent le transport HTTP \(<xref:System.ServiceModel.WSHttpBinding> et <xref:System.ServiceModel.BasicHttpBinding>\) prennent en charge plusieurs schémas d'authentification, comme l'explique [Fonctionnement de l'authentification HTTP](../../../../docs/framework/wcf/feature-details/understanding-http-authentication.md).Le niveau d'emprunt d'identité pris en charge dépend du schéma d'authentification.Les éléments suivants sont utilisés avec le transport http :  
  
-   Le schéma d'authentification `Anonymous` ignore l'emprunt d'identité.  
  
-   Le schéma d'authentification `Basic`  prend uniquement en charge le niveau `Delegate`.Tous les niveaux d'emprunt d'identité inférieurs sont mis à niveau.  
  
-   Le schéma d'authentification `Digest` prend uniquement en charge les niveaux `Impersonate` et `Delegate`.  
  
-   Le schéma d'authentification `NTLM`, sélectionnable soit directement, soit par négociation, prend uniquement en charge le niveau `Delegate` sur l'ordinateur local.  
  
-   Le schéma d'authentification Kerberos, qui ne peut être sélectionné que par négociation, peut être utilisé avec tout niveau d'emprunt d'identité pris en charge.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)] le transport HTTP, consultez [Choix d'un transport](../../../../docs/framework/wcf/feature-details/choosing-a-transport.md).  
  
## Voir aussi  
 [Délégation et emprunt d'identité](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)   
 [Autorisation](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)   
 [Comment : emprunter l'identité d'un client sur un service](../../../../docs/framework/wcf/how-to-impersonate-a-client-on-a-service.md)   
 [Fonctionnement de l'authentification HTTP](../../../../docs/framework/wcf/feature-details/understanding-http-authentication.md)