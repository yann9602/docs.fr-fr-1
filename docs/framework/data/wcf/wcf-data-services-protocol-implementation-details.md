---
title: "D&#233;tails relatifs &#224; l&#39;impl&#233;mentation du protocole WCF Data Services | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-oob"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 712d689b-fada-4cbb-bcdb-d65a3ef83b4c
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# D&#233;tails relatifs &#224; l&#39;impl&#233;mentation du protocole WCF Data Services
## Détails de l'implémentation du protocole OData  
 [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] requiert qu'un service de données qui implémente le protocole fournisse un ensemble minimum spécifique de fonctionnalités.  Ces fonctionnalités sont décrites dans les documents du protocole avec les termes « should » \(devrait\) et « must » \(doit\). Les autres fonctionnalités facultatives sont décrites avec le terme « may » \(peut\). Cette rubrique décrit ces fonctionnalités facultatives qui ne sont pas actuellement implémentées par [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)].  Pour plus d'informations, consultez [Documentation du protocole OData](http://go.microsoft.com/fwlink/?LinkID=184554).  
  
### Prise en charge de l'option de requête $format  
 Le protocole [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] prend en charge les flux JavaScript Notation \(JSON\) et Atom, et [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] fournit l'option de requête système `$format` pour permettre à un client de demander le format du flux de réponse.  Cette option de requête du système \(si prise en charge par le service de données\) doit substituer la valeur de l'en\-tête Accept de la requête.  [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] prend en charge le retour de flux JSON et Atom.  Toutefois, l'implémentation par défaut ne prend pas en charge l'option de requête `$format` et utilise uniquement la valeur de l'en\-tête Accept pour déterminer le format de la réponse.  Il y a des cas où votre service de données doit prendre en charge l'option de requête `$format`, par exemple lorsque les clients ne peuvent pas définir l'en\-tête Accept.  Pour prendre en charge ces scénarios, vous devez étendre votre service de données pour gérer cette option dans l'URI.  Vous pouvez ajouter cette fonctionnalité à votre service de données en téléchargeant l'exemple de projet [JSONP and URL\-controlled format support for ADO.NET Data Services](http://go.microsoft.com/fwlink/?LinkId=208228) à partir du site Web MSDN Code Gallery et en l'ajoutant à votre projet de service de données.  Cet exemple supprime l'option de requête `$format` et remplace l'en\-tête Accept par `application/json`.  Lorsque vous incluez l'exemple de projet et ajoutez `JSONPSupportBehaviorAttribute` à votre classe de service de données, le service peut gérer l'option de requête `$format=json` `$format`.  Une personnalisation plus poussée de cet exemple de projet est requise pour gérer également `$format=atom` ou d'autres formats personnalisés.  
  
## Comportements des services de données WCF  
 Les comportements suivants [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] ne sont pas explicitement définis par le protocole [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] :  
  
### Comportement de tri par défaut  
 Lorsqu'une demande de requête envoyée au service de données inclut une option de requête système `$top` ou `$skip` et n'inclut pas d'option de requête système `$orderby`, le flux retourné est trié par les propriétés de clé, dans l'ordre croissant.  Cela est dû au fait que le dimensionnement est requis pour garantir la pagination correcte des résultats.  Pour cela, le service de données ajoute une expression de classement à la requête.  Ce comportement se produit également lorsque la pagination orientée serveur est vérifiée dans le service de données.  Pour plus d'informations, consultez [Configuration du service de données](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md). Pour contrôler le classement du flux retourné, vous devez inclure `$orderby` dans l'URI de requête.  
  
## Voir aussi  
 [Définition de WCF Data Services](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)   
 [Bibliothèque cliente de WCF Data Services](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)