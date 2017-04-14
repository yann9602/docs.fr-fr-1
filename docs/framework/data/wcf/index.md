---
title: "WCF Data Services&#160;4.5 | Microsoft Docs"
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
  - "Astoria"
  - "Services de données WCF, prise en main"
ms.assetid: 73d2bec3-7c92-4110-b905-11bb0462357a
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# WCF Data Services&#160;4.5
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] \(antérieurement appelé « ADO.NET Data Services »\) est un composant du .NET Framework qui vous permet de créer des services utilisant le protocole [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] pour exposer et consommer des données sur le web ou l'intranet à l'aide de la sémantique de [REST \(Representational State Transfer\)](http://go.microsoft.com/fwlink/?LinkId=113919). [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] expose les données sous forme de ressources adressables par des URI.  Les données sont accessibles et modifiables à l'aide des verbes HTTP standard GET, PUT, POST et DELETE. [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] utilise les conventions de relation d'entité dans [Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model.md) pour exposer des ressources sous forme de jeux d'entités reliés par des associations.  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] utilise le protocole [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] pour l'adressage et la mise à jour des ressources.  Vous pouvez ainsi accéder à ces services à partir de tout client qui prend en charge [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)].  [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] vous permet de demander et d'écrire des données dans les ressources à l'aide de formats de transfert classiques : Atom, un jeu de normes pour l'échange et la mise à jour de données au format XML, et JSON \(JavaScript Objet Notation\), un format d'échange de données textuel utilisé largement dans l'application AJAX.  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] peut exposer des données qui proviennent de différentes sources, telles que des flux [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)].  Les outils Visual Studio facilitent la création d'un service basé sur [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] à l'aide d'un modèle de données ADO.NET Entity Framework. Vous pouvez également créer des flux [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] basés sur les classes CLR \(Common Language Runtime\) et même des données à liaison tardive ou non typées.  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] inclut également un jeu de bibliothèques clientes, un pour les applications clientes .NET Framework générales et un autre spécifique aux applications Silverlight.  Ces bibliothèques clientes fournissent un modèle de programmation basé sur des objets lorsque vous accédez à un flux [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] depuis des environnements tels que .NET Framework et Silverlight.  
  
## Où est\-ce que je dois démarrer ?  
 Selon ce qui vous intéresse, choisissez de démarrer avec [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] depuis l'une des rubriques suivantes.  
  
 Je veux rentrer dans le vif du sujet...  
 -   [Démarrage rapide](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)  
  
-   [Mise en route](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)  
  
-   [Démarrage rapide de Silverlight](http://go.microsoft.com/fwlink/?LinkID=192782)  
  
-   [Démarrage rapide de Silverlight pour le développement pour Windows Phone](http://go.microsoft.com/fwlink/?LinkID=214535)  
  
 Montrez\-moi des exemples de code...  
 -   [Démarrage rapide](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)  
  
-   [Procédure : exécuter des requêtes de service des données](../../../../docs/framework/data/wcf/how-to-execute-data-service-queries-wcf-data-services.md)  
  
-   [Procédure : lier des données aux éléments Windows Presentation Foundation](../../../../docs/framework/data/wcf/bind-data-to-wpf-elements-wcf-data-services.md)  
  
 Je souhaite en savoir plus sur [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)].  
 -   [Livre blanc : Introduction à OData](http://go.microsoft.com/fwlink/?LinkId=220867)  
  
-   [Site web du protocole Open Data](http://go.microsoft.com/fwlink/?LinkID=184554)  
  
-   [OData : Kit de développement logiciel \(SDK\)](http://go.microsoft.com/fwlink/?LinkID=185248)  
  
-   [OData : questions les plus fréquentes](http://go.microsoft.com/fwlink/?LinkId=185867)  
  
 Je souhaite regarder des vidéos...  
 -   [Guide du débutant pour les services de données WCF](http://go.microsoft.com/fwlink/?LinkId=220864)  
  
-   [Vidéos pour les développeurs de services de données WCF](http://go.microsoft.com/fwlink/?LinkId=220861)  
  
-   [OData : site web des développeurs](http://go.microsoft.com/fwlink/?LinkId=185866)  
  
 Je souhaite consulter des exemples de bout en bout  
 -   [Exemples de la documentation des services de données WCF sur MSDN Samples Gallery](http://go.microsoft.com/fwlink/?LinkID=220865)  
  
-   [Autres exemples de services de données WCF sur MSDN Samples Gallery](http://go.microsoft.com/fwlink/?LinkID=220866)  
  
-   [OData : Kit de développement logiciel \(SDK\)](http://go.microsoft.com/fwlink/?LinkID=185248)  
  
 Qu'en est\-il de l'intégration avec Visual Studio ?  
 -   [Génération de la bibliothèque cliente du service de données](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md)  
  
-   [Création du service de données](../../../../docs/framework/data/wcf/creating-the-data-service.md)  
  
-   [Fournisseur Entity Framework](../../../../docs/framework/data/wcf/entity-framework-provider-wcf-data-services.md)  
  
 Comment puis\-je l'utiliser ?  
 -   [Vue d'ensemble](../../../../docs/framework/data/wcf/wcf-data-services-overview.md)  
  
-   [Livre blanc : Introduction à OData](http://go.microsoft.com/fwlink/?LinkId=220867)  
  
-   [Scénarios d'application](../../../../docs/framework/data/wcf/application-scenarios-wcf-data-services.md)  
  
 Je souhaite utiliser Silverlight...  
 -   [Démarrage rapide de Silverlight](http://go.microsoft.com/fwlink/?LinkID=192782)  
  
-   [Services de données WCF \(Silverlight\)](http://go.microsoft.com/fwlink/?LinkID=143149)  
  
-   [Prise en main de Silverlight](http://go.microsoft.com/fwlink/?LinkId=148366)  
  
 Je souhaite créer une application Windows Phone…  
 -   [Démarrage rapide de Silverlight pour le développement pour Windows Phone](http://go.microsoft.com/fwlink/?LinkID=214535)  
  
-   [Client OData \(Open Data Protocol\) pour Windows Phone](http://go.microsoft.com/fwlink/?LinkID=208749)  
  
 Je souhaite utiliser LINQ...  
 -   [Interrogation du service de données](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)  
  
-   [Considérations sur LINQ](../../../../docs/framework/data/wcf/linq-considerations-wcf-data-services.md)  
  
-   [Procédure : exécuter des requêtes de service des données](../../../../docs/framework/data/wcf/how-to-execute-data-service-queries-wcf-data-services.md)  
  
 J'ai encore besoin d'informations supplémentaires...  
 -   [Blog de l'équipe des services de données WCF](http://go.microsoft.com/fwlink/?LinkID=150511)  
  
-   [Ressources](../../../../docs/framework/data/wcf/wcf-data-services-resources.md)  
  
-   [Centre de développement des services de données WCF](http://go.microsoft.com/fwlink/?LinkId=220868)  
  
-   [Site web du protocole Open Data](http://go.microsoft.com/fwlink/?LinkID=184554)  
  
## Dans cette section  
 [Vue d'ensemble](../../../../docs/framework/data/wcf/wcf-data-services-overview.md)  
 Fournit une vue d'ensemble des caractéristiques et des fonctionnalités disponibles dans [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)].  
  
 [What's New in WCF Data Services](http://msdn.microsoft.com/fr-fr/cf22cad5-b8d9-472b-8d7c-b863b64eaae8)  
 Décrit les nouvelles fonctionnalités de [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] et la prise en charge des nouvelles fonctions de [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)].  
  
 [Mise en route](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)  
 Décrit comment exposer et consommer des flux [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] à l'aide d'[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)].  
  
 [Définition de WCF Data Services](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)  
 Décrit comment créer et configurer un service de données qui expose des flux [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)].  
  
 [Bibliothèque cliente de WCF Data Services](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)  
 Décrit comment utiliser des bibliothèques clientes pour consommer les flux [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] d'une application cliente .NET Framework.  
  
## Voir aussi  
 [REST \(Representational State Transfer\)](http://go.microsoft.com/fwlink/?LinkId=113919)