---
title: "Vue d&#39;ensemble&#160;de WCF Data Services | Microsoft Docs"
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
  - "Services de données WCF"
  - "Services de données WCF, à propos de"
ms.assetid: 7924cf94-c9a6-4015-afc9-f5d22b1743bb
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# Vue d&#39;ensemble&#160;de WCF Data Services
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] permet de créer et de consommer des services de données pour le Web ou un Intranet à l'aide du protocole [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)].  [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] vous permet d'exposer vos données sous forme de ressources adressables par des URI.  Cela vous permet d'accéder aux données et de les modifier à l'aide de la sémantique REST \(representational state transfer\), spécifiquement, les verbes HTTP standard GET, PUT, POST et DELETE. Cette rubrique inclut une vue d'ensemble des modèles et des pratiques définis par [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] ainsi que des fonctionnalités fournies par [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] pour tirer parti de [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] dans les applications basées sur .NET Framework.  
  
## Adresser des données comme ressources  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] expose les données comme ressources adressables par des URI. Les chemins d'accès aux ressources sont construits selon les conventions de relation d'entité de l'Entity Data Model.  Dans ce modèle, les entités représentent des unités opérationnelles de données dans un domaine d'application, par exemple les clients, les commandes, les éléments et les produits.  Pour plus d'informations, consultez [Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model.md).  
  
 Dans [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)], vous adressez des ressources d'entité comme un jeu d'entités qui contient des instances de types d'entité.  Par exemple, l'URI `http://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/Orders` retourne toutes les commandes du service de données `Northwind` qui sont associées au client ayant une valeur `CustomerID` équivalente à `ALFKI.`  
  
 Les expressions de requête vous permettent d'effectuer des opérations de requête traditionnelles sur des ressources, telles que filtrer, trier et paginer.  Par exemple, l'URI `http://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/Orders?$filter=Freight gt 50` filtre les ressources de façon à retourner uniquement les commandes dont le coût de fret est supérieur à 50 $.  Pour plus d'informations, consultez [Accès aux ressources de service des données](../../../../docs/framework/data/wcf/accessing-data-service-resources-wcf-data-services.md).  
  
## Accès aux données interopérables  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] tire parti des protocoles Internet standard pour rendre les services de données interactifs avec les applications qui n'utilisent pas .NET Framework.  Comme vous pouvez faire appel à des URI standard pour adresser des données, votre application peut accéder à des données et les modifier en utilisant la sémantique REST, en particulier les verbes HTTP standard GET, PUT, POST et DELETE.  De cette manière, vous pouvez accéder à ces services depuis tout client qui peut analyser et accéder aux données transmises sur des protocoles HTTP standard.  
  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] définit un jeu d'extensions au protocole AtomPub. Il prend en charge les requêtes et les réponses HTTP sous plusieurs formats de données pour prendre en charge des plateformes et des applications clientes diverses.  Un flux [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] peut représenter des données dans Atom, JSON \(JavaScript Object Notation\), et sous forme de XML ordinaire.  Bien qu'Atom soit le format par défaut, le format du flux est spécifié dans l'en\-tête de la requête HTTP.  Pour plus d'informations, consultez [OData : format Atom](http://go.microsoft.com/fwlink/?LinkID=185794) et [OData : format JSON](http://go.microsoft.com/fwlink/?LinkID=185795).  
  
 Lors de la publication de données sous forme de flux [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)], [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] s'appuie sur d'autres outils Internet existants pour ce type d'opération, comme la mise en cache et l'authentification.  Pour cela, [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] s'intègre avec des applications et des services d'hébergement existants, tels qu'ASP.NET, Windows Communication Foundation \(WCF\) et les Services Internet \(IIS\).  
  
## Indépendance du stockage  
 Bien que les ressources soient adressées selon un modèle de relation d'entité, [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] expose les flux [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] indépendamment de la source de données. Après l'acceptation par [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] d'une demande HTTP pour une ressource identifiée par un URI, la demande est désérialisée et une représentation de cette demande est passée à un fournisseur [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)].  Ce fournisseur traduit la requête dans un format spécifique à la source de données et exécute la requête sur la source de données sous\-jacente. [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] effectue l'indépendance de stockage en séparant le modèle conceptuel qui adresse des ressources prescrites par [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] du schéma spécifique de la source de données sous\-jacente.  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] s'intègre à ADO.NET Entity Framework pour vous permettre de créer des services de données qui exposent des données relationnelles.  Vous pouvez utiliser les outils Entity Data Model pour créer un modèle de données qui contient des ressources adressables en tant qu'entités et définir en même temps le mappage entre ce modèle et les tables dans la base de données sous\-jacente.  Pour plus d'informations, consultez [Fournisseur Entity Framework](../../../../docs/framework/data/wcf/entity-framework-provider-wcf-data-services.md).  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] vous permet également de créer des services de données qui exposent les structures de données qui retournent une implémentation de l'interface <xref:System.Linq.IQueryable%601>.  De cette manière, vous pouvez créer des services de données qui exposent des données à partir de types .NET Framework.  Les opérations de création, de mise à jour et de suppression sont prises en charge lorsque vous implémentez également l'interface <xref:System.Data.Services.IUpdatable>.  Pour plus d'informations, consultez [Fournisseur de réflexion](../../../../docs/framework/data/wcf/reflection-provider-wcf-data-services.md).  
  
 Pour voir comment [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] s'intègre avec ces fournisseurs de données, consultez le diagramme architectural plus loin dans cette rubrique.  
  
## Logique métier personnalisée  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] facilite l'ajout d'une logique métier personnalisée à un service de données via des opérations de service et des intercepteurs.  Les opérations de service sont des méthodes définies sur le serveur qui sont adressables par des URI sous la même forme que des ressources de données.  Les opérations de service peuvent également utiliser la syntaxe d'expression de requête pour filtrer, classer et paginer des données retournées par une opération. Par exemple, l'URI `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'&$orderby=OrderDate&$top=10&$skip=10` représente un appel à une opération de service nommée `GetOrdersByCity` sur le service de données Northwind qui retourne des commandes de clients de Londres et des résultats paginés triés par `OrderDate`.  Pour plus d'informations, consultez [Opérations de service](../../../../docs/framework/data/wcf/service-operations-wcf-data-services.md).  
  
 Les intercepteurs permettent à la logique d'application personnalisée d'être intégrée dans le traitement des messages de réponse ou de demande par un service de données.  Les intercepteurs sont appelés lorsqu'une action de requête, d'insertion, de mise à jour ou de suppression a lieu dans le jeu d'entités spécifié.  Un intercepteur peut alors modifier les données, appliquer la stratégie d'autorisation ou même mettre fin à l'opération.  Les méthodes d'intercepteur doivent être enregistrées explicitement pour un jeu d'entités donné exposé par un service de données.  Pour plus d'informations, consultez [Intercepteurs](../../../../docs/framework/data/wcf/interceptors-wcf-data-services.md).  
  
## Bibliothèque clientes  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] définit un jeu de modèles uniformes pour l'interaction avec les services de données.  Ainsi, il est possible de créer des composants réutilisables selon ces services, comme des bibliothèques côté client qui simplifient la consommation de ces services de données.  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] inclut des bibliothèques clientes pour les applications clientes .NET Framework et Silverlight.  Ces bibliothèques clientes vous permettent d'interagir avec les services de données en utilisant des objets .NET Framework.  Elles prennent également en charge des requêtes basées sur des objets et des requêtes LINQ, le chargement des objets connexes, le suivi des modifications et la résolution d'identité. Pour plus d'informations, consultez [Bibliothèque cliente de WCF Data Services](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md).  
  
 En plus des bibliothèques clientes [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] incluses avec .NET Framework et Silverlight, il existe d'autres bibliothèques clientes qui vous permettent de consommer un flux [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] dans des applications clientes, telles que des applications PHP, AJAX et Java.  Pour plus d'informations, consultez [Kit de développement logiciel \(SDK\) OData](http://go.microsoft.com/fwlink/?LinkID=185796).  
  
## Vue d'ensemble de l'architecture  
 Le diagramme suivant illustre l'architecture [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] pour l'exposition des flux [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] et leur utilisation dans les bibliothèques clientes [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] :  
  
 ![Diagramme d'architecture des services de données WCF](../../../../docs/framework/data/wcf/media/astoriaservicearch.gif "AstoriaServiceArch")  
  
## Voir aussi  
 [WCF Data Services 4.5](../../../../docs/framework/data/wcf/index.md)   
 [Mise en route](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)   
 [Définition de WCF Data Services](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)   
 [Accessing a Data Service \(WCF Data Services\)](http://msdn.microsoft.com/fr-fr/1e54a2b9-2ec6-4002-b8f8-c1d8df37c350)   
 [Bibliothèque cliente de WCF Data Services](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)   
 [REST \(Representational State Transfer\)](http://go.microsoft.com/fwlink/?LinkId=113919)