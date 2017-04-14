---
title: "Concepts de s&#233;curit&#233; utilis&#233;s dans WCF | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3b9dfcf5-4bf1-4f35-9070-723171c823a1
caps.latest.revision: 15
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 15
---
# Concepts de s&#233;curit&#233; utilis&#233;s dans WCF
La sécurité [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] est basée sur des concepts déjà utilisés et déployés dans diverses infrastructures de sécurité.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] prend en charge quelques\-unes de ces infrastructures, telles que SSL \(Secure Sockets Layer\) sur HTTP \(HTTPS\).Toutefois, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ne prend pas uniquement en charge les infrastructures de sécurité existantes, mais implémente également des standards de sécurité interopérables plus récents \(tels que WS\-Security\) sur des messages encodés selon le protocole SOAP.Toutefois, qu'il s'agisse de mécanismes existants ou de nouveaux standards interopérables, les concepts de sécurité sous\-jacents sont dans ces deux cas les mêmes.Par conséquent, comprendre les concepts qui sous\-tendent les infrastructures existantes et les standards plus récents est un atout essentiel à l'implémentation du meilleur modèle de sécurité pour une application.  
  
## Introduction à la sécurité pour WCF Web Services  
 Le groupe Microsoft Patterns and Practices a rédigé un livre blanc approfondi sur les consignes de sécurité WCF, disponible au téléchargement ici : [Guide de la sécurité WCF](http://go.microsoft.com/fwlink/?LinkId=210210).Ce livre blanc décrit les concepts de sécurité fondamentaux liés aux services Web, aux principes de sécurité WCF clés ainsi qu'aux scénarios d'application Intranet et Internet.  
  
## Spécifications de sécurité de l'industrie  
  
### Infrastructure à clé publique  
 L'infrastructure à clé publique \(PKI\) est un système de certificats numériques, d'autorités de certification et autres autorités d'immatriculation qui vérifient et authentifient chaque partie impliquée dans une transaction électronique via l'utilisation du chiffrement à clé publique.[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Services de certificats Windows Server 2008 R2](http://go.microsoft.com/fwlink/?LinkId=210211).  
  
### Protocole Kerberos  
 Le *protocole Kerberos* est une spécification permettant de créer un mécanisme de sécurité qui authentifie les utilisateurs d'un domaine Windows.Il permet d'établir un contexte sécurisé avec d'autres entités au sein d'un domaine.Windows 2000 et les plateformes ultérieures utilisent le protocole Kerberos par défaut.La maîtrise des mécanismes du système est utile lors de la création d'un service qui interagira avec les clients intranet.En outre, étant donné que *la liaison Kerberos de sécurité de services Web* est largement publiée, vous pouvez utiliser le protocole Kerberos pour communiquer avec les clients Internet \(autrement dit, le protocole Kerberos est interopérable\).[!INCLUDE[crabout](../../../../includes/crabout-md.md)] l'implémentation du protocole Kerberos sous Windows, consultez [Microsoft Kerberos](http://go.microsoft.com/fwlink/?LinkId=210212).  
  
### Certificats X.509  
 Les certificats X.509 constituent un formulaire d'informations d'identification principal utilisé dans les applications de sécurité.Pour plus d'informations sur les certificats X.509, consultez [Certificats de clé publique X.509](http://go.microsoft.com/fwlink/?LinkId=210213).Les certificats X.509 sont stockés dans un magasin de certificats.Un ordinateur qui exécute Windows a plusieurs types de magasins de certificats, chacun ayant un but différent.[!INCLUDE[crabout](../../../../includes/crabout-md.md)] les différents magasins, consultez [Magasins de certificats](http://go.microsoft.com/fwlink/?LinkID=87787).  
  
## Spécifications Web Services Security  
 Les liaisons définies par le système prennent en charge plusieurs spécifications de sécurité communément utilisées pour les services Web.Pour obtenir la liste complète des liaisons fournies par le système et les spécifications de services Web qu'elles prennent en charge, consultez : [Protocoles de services Web pris en charge par des liaisons d'interopérabilité fournies par le système](../../../../docs/framework/wcf/feature-details/web-services-protocols-supported-by-system-provided-interoperability-bindings.md).  
  
## Mécanismes de contrôle d'accès  
 WCF offre plusieurs méthodes pour contrôler l'accès à un service ou à une opération.Parmi celles\-ci :  
  
1.  <xref:System.Security.Permissions.PrinciplePermissionAttribute>  
  
2.  Fournisseur d'appartenances ASP.NET  
  
3.  Fournisseur de rôle ASP.NET  
  
4.  Gestionnaire d'autorisations  
  
5.  Modèle d'identité  
  
 Pour plus d'informations à ce sujet, consultez [Mécanismes de contrôle d'accès](../../../../docs/framework/wcf/feature-details/access-control-mechanisms.md).  
  
## Voir aussi  
 [Vue d'ensemble de la sécurité](../../../../docs/framework/wcf/feature-details/security-overview.md)   
 [Modèle de sécurité pour Windows Server AppFabric](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)