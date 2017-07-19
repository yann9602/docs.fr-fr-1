---
title: "Biblioth&#232;que cliente de WCF Data Services | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-oob"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "HTML"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "DataServiceContext, classe, à propos de la classe DataServiceContext"
  - "DataServiceQuery, classe, à propos de la classe DataServiceQuery"
  - "Services de données WCF, bibliothèque cliente"
ms.assetid: 21075e50-8917-413e-a8ea-35a0f6e65aa5
caps.latest.revision: 4
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# Biblioth&#232;que cliente de WCF Data Services
Une application peut interagir avec un service de données basé sur [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] si elle peut envoyer une requête HTTP et transformer le flux d'[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] retourné par un service de données. Cette interopérabilité vous permet d'accéder aux services basés sur [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] à partir d'une large gamme d'applications Web.  [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] inclut également des bibliothèques clientes qui fournissent une expérience en programmation plus riche lorsque vous consommez des flux [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] à partir des applications .NET Framework ou Silverlight.  
  
 Les deux classes principales de la bibliothèque cliente sont la classe <xref:System.Data.Services.Client.DataServiceContext> et la classe <xref:System.Data.Services.Client.DataServiceQuery%601>.  La classe <xref:System.Data.Services.Client.DataServiceContext> encapsule des opérations prises en charge sur un service de données spécifié.  Même si les services [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] sont sans état, ce n'est pas le cas du contexte.  Par conséquent, vous pouvez utiliser la classe <xref:System.Data.Services.Client.DataServiceContext> pour conserver l'état sur le client entre des interactions avec le service de données afin de prendre en charge des fonctionnalités telles que la gestion des changements.  Cette classe gère également des identités et suit les modifications.  La classe <xref:System.Data.Services.Client.DataServiceQuery%601> représente une requête sur un jeu d'entités spécifique.  
  
 Cette section décrit comment utiliser des bibliothèques clientes pour accéder et modifier des données d'une application cliente .NET Framework.  Pour plus d'informations sur la façon d'utiliser la bibliothèque cliente [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] avec une application Silverlight, consultez [Services de données WCF \(Silverlight\)](http://go.microsoft.com/fwlink/?LinkId=186016).  D'autres bibliothèques clientes sont disponibles et vous permettent de consommer un flux [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] dans d'autres types d'applications.  Pour plus d'informations, consultez [Kit de développement logiciel \(SDK\) OData](http://go.microsoft.com/fwlink/?LinkID=185796).  
  
## Dans cette section  
 [Génération de la bibliothèque cliente du service de données](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md)  
 Décrit comment générer une bibliothèque cliente et des classes de service de données client basées sur un flux [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)].  
  
 [Interrogation du service de données](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)  
 Décrit comment interroger un service de données depuis une application .NET Framework à l'aide de bibliothèques clientes.  
  
 [Chargement de contenu différé](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md)  
 Décrit comment charger un contenu supplémentaire non inclus dans la réponse à la requête initiale.  
  
 [Mise à jour du service de données](../../../../docs/framework/data/wcf/updating-the-data-service-wcf-data-services.md)  
 Décrit comment créer, modifier et supprimer des entités et des relations à l'aide des bibliothèques clientes.  
  
 [Opérations asynchrones](../../../../docs/framework/data/wcf/asynchronous-operations-wcf-data-services.md)  
 Décrit les fonctions fournies par les bibliothèques clientes pour l'utilisation d'un service de données de façon asynchrone.  
  
 [Opérations de traitement par lot](../../../../docs/framework/data/wcf/batching-operations-wcf-data-services.md)  
 Décrit comment envoyer plusieurs demandes au service de données dans un lot unique à l'aide des bibliothèques clientes.  
  
 [Liaison de données aux contrôles](../../../../docs/framework/data/wcf/binding-data-to-controls-wcf-data-services.md)  
 Décrit comment lier des contrôles à un flux [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] retourné par un service de données.  
  
 [Appel des opérations de service](../../../../docs/framework/data/wcf/calling-service-operations-wcf-data-services.md)  
 Décrit comment utiliser la bibliothèque cliente pour appeler des opérations de service.  
  
 [Gérer le contexte du service de données](../../../../docs/framework/data/wcf/managing-the-data-service-context-wcf-data-services.md)  
 Décrit les options de gestion du comportement de la bibliothèque cliente.  
  
 [Utilisation de données binaires](../../../../docs/framework/data/wcf/working-with-binary-data-wcf-data-services.md)  
 Décrit comment accéder à des données binaires retournées par le service de données sous forme de flux de données et les modifier.  
  
## Voir aussi  
 [Définition de WCF Data Services](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)   
 [Mise en route](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)