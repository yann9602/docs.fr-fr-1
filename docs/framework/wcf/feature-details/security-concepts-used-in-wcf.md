---
title: "Concepts de sécurité utilisés dans WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3b9dfcf5-4bf1-4f35-9070-723171c823a1
caps.latest.revision: "15"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 142de63c3d61ae2ff7f89b1d602f2a48c739f53a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="security-concepts-used-in-wcf"></a>Concepts de sécurité utilisés dans WCF
La sécurité [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] est basée sur des concepts déjà utilisés et déployés dans diverses infrastructures de sécurité.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] prend en charge quelques-unes de ces infrastructures, telles que SSL (Secure Sockets Layer) sur HTTP (HTTPS). Toutefois, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ne prend pas uniquement en charge les infrastructures de sécurité existantes, mais implémente également des standards de sécurité interopérables plus récents (tels que WS-Security) sur des messages encodés selon le protocole SOAP. Toutefois, qu'il s'agisse de mécanismes existants ou de nouveaux standards interopérables, les concepts de sécurité sous-jacents sont dans ces deux cas les mêmes. Par conséquent, comprendre les concepts qui sous-tendent les infrastructures existantes et les standards plus récents est un atout essentiel à l'implémentation du meilleur modèle de sécurité pour une application.  
  
## <a name="introduction-to-security-for-wcf-web-services"></a>Introduction à la sécurité pour WCF Web Services  
 Le groupe Microsoft Patterns and Practices a écrit un livre blanc détaillée sur le Guide de sécurité WCF qui est disponible pour téléchargement ici : [Guide de sécurité de WCF](http://go.microsoft.com/fwlink/?LinkId=210210). Ce livre blanc décrit les concepts de sécurité fondamentaux liés aux services Web, aux principes de sécurité WCF clés ainsi qu'aux scénarios d'application Intranet et Internet.  
  
## <a name="industry-wide-security-specifications"></a>Spécifications de sécurité de l'industrie  
  
### <a name="public-key-infrastructure"></a>Infrastructure à clé publique  
 L’infrastructure à clé publique (PKI) est un système de certificats numériques, d’autorités de certification et autres autorités d’immatriculation qui vérifient et authentifient chaque partie impliquée dans une transaction électronique via l’utilisation du chiffrement à clé publique. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Services de certificats de Windows Server 2008 R2](http://go.microsoft.com/fwlink/?LinkId=210211).  
  
### <a name="kerberos-protocol"></a>Protocole Kerberos  
 Le *protocole Kerberos* est une spécification pour la création d’un mécanisme de sécurité qui authentifie les utilisateurs sur un domaine Windows. Il permet d'établir un contexte sécurisé avec d'autres entités au sein d'un domaine. Windows 2000 et les plateformes ultérieures utilisent le protocole Kerberos par défaut. La maîtrise des mécanismes du système est utile lors de la création d'un service qui interagira avec les clients intranet. En outre, étant donné que la *liaison Kerberos de la sécurité de Services Web* est largement publiée, vous pouvez utiliser le protocole Kerberos pour communiquer avec les clients Internet (autrement dit, le protocole Kerberos est interopérable). [!INCLUDE[crabout](../../../../includes/crabout-md.md)]le protocole Kerberos est implémenté dans Windows, voir [Microsoft Kerberos](http://go.microsoft.com/fwlink/?LinkId=210212).  
  
### <a name="x509-certificates"></a>Certificats X.509  
 Les certificats X.509 constituent un formulaire d'informations d'identification principal utilisé dans les applications de sécurité. Pour plus d’informations sur X.509 certificats Voir [des certificats de clé publique X.509](http://go.microsoft.com/fwlink/?LinkId=210213). Les certificats X.509 sont stockés dans un magasin de certificats. Un ordinateur qui exécute Windows a plusieurs types de magasins de certificats, chacun ayant un but différent. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]les magasins différents, consultez [des magasins de certificats](http://go.microsoft.com/fwlink/?LinkID=87787).  
  
## <a name="web-services-security-specifications"></a>Spécifications Web Services Security  
 Les liaisons définies par le système prennent en charge plusieurs spécifications de sécurité communément utilisées pour les services Web. Ils prennent en charge pour une liste complète des liaisons fournies par le système et les spécifications des services web voir : [Web Services protocoles pris en charge par les liaisons d’interopérabilité fournies](../../../../docs/framework/wcf/feature-details/web-services-protocols-supported-by-system-provided-interoperability-bindings.md)  
  
## <a name="access-control-mechanisms"></a>Mécanismes de contrôle d'accès  
 WCF offre plusieurs méthodes pour contrôler l'accès à un service ou à une opération. Parmi celles-ci :  
  
1.  <xref:System.Security.Permissions.PrincipalPermissionAttribute>  
  
2.  Fournisseur d'appartenances ASP.NET  
  
3.  Fournisseur de rôle ASP.NET  
  
4.  Gestionnaire d'autorisations  
  
5.  Modèle d'identité  
  
 Pour plus d’informations sur ces rubriques, consultez [mécanismes de contrôle d’accès](../../../../docs/framework/wcf/feature-details/access-control-mechanisms.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de la sécurité](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [Modèle de sécurité pour Windows Server AppFabric](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
