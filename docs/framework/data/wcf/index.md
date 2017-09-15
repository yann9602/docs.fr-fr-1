---
title: "WCF Data Services 4.5"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- HTML
- VB
- CSharp
- C++
helpviewer_keywords:
- Astoria
- WCF Data Services, getting started
ms.assetid: 73d2bec3-7c92-4110-b905-11bb0462357a
caps.latest.revision: 6
author: Erikre
ms.author: erikre
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 1b491d644112137cb24e847439aa133691e5261d
ms.contentlocale: fr-fr
ms.lasthandoff: 09/05/2017

---
# <a name="wcf-data-services-45"></a>WCF Data Services 4.5
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] (autrefois appelé « ADO.NET Data Services ») est un composant du .NET Framework qui permet de créer des services qui utilisent le protocole [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] pour exposer et consommer des données sur le web ou l’intranet en utilisant la sémantique de [REST (representational state transfer)](http://go.microsoft.com/fwlink/?LinkId=113919). [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] expose des données comme des ressources adressables par des URI. Les données sont accessibles et modifiables à l'aide des verbes HTTP standard GET, PUT, POST et DELETE. [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] utilise les conventions de relation d’entité dans [EDM (Entity Data Model)](../../../../docs/framework/data/adonet/entity-data-model.md) pour exposer des ressources en tant que jeux d’entités liés par des associations.  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] utilise le protocole [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] pour adresser et mettre à jour les ressources. Vous pouvez ainsi accéder à ces services à partir de tout client qui prend en charge [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]. [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] permet de demander et d’écrire des données dans les ressources en utilisant des formats de transfert bien connus : Atom, jeu de normes pour l’échange et la mise à jour de données au format XML, et JSON (JavaScript Objet Notation), format d’échange de données textuel utilisé largement dans l’application AJAX.  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] peut exposer des données issues de différentes sources, telles que des flux [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]. Les outils de Visual Studio simplifient la création de services basés sur [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] à l'aide d'un modèle de données ADO.NET Entity Framework. Vous pouvez aussi créer des flux [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] reposant sur des classes CLR (Common Language Runtime) et même des données à liaison tardive ou non typées.  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] inclut également un jeu de bibliothèques clientes, un pour les applications clientes .NET Framework générales et un autre spécifique aux applications Silverlight. Ces bibliothèques clientes fournissent un modèle de programmation basé sur des objets quand vous accédez à un flux [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] à partir de certains environnements tels que le .NET Framework et Silverlight.  
  
## <a name="where-should-i-start"></a>Où est-ce que je dois démarrer ?  
 Selon ce qui vous intéresse, choisissez de démarrer avec [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] depuis l'une des rubriques suivantes.  
  
 Je veux rentrer dans le vif du sujet...  
 -   [Démarrage rapide](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)  
  
-   [Prise en main](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)  
  
-   [Démarrage rapide avec Silverlight](http://go.microsoft.com/fwlink/?LinkID=192782)  
  
-   [Démarrage rapide avec Silverlight pour le développement de Windows Phone](http://go.microsoft.com/fwlink/?LinkID=214535)  
  
 Montrez-moi des exemples de code...  
 -   [Démarrage rapide](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)  
  
-   [Comment : exécuter les requêtes de services de données](../../../../docs/framework/data/wcf/how-to-execute-data-service-queries-wcf-data-services.md)  
  
-   [Comment : lier les données aux éléments Windows Presentation Foundation](../../../../docs/framework/data/wcf/bind-data-to-wpf-elements-wcf-data-services.md)  
  
 Je souhaite en savoir plus sur [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)].  
 -   [Livre blanc : présentation d’OData](http://go.microsoft.com/fwlink/?LinkId=220867)  
  
-   [Site web Open Data Protocol](http://go.microsoft.com/fwlink/?LinkID=184554)  
  
-   [Kit de développement logiciel (SDK) OData](http://go.microsoft.com/fwlink/?LinkID=185248)  
  
-   [OData : forum aux questions](http://go.microsoft.com/fwlink/?LinkId=185867)  
  
 Je souhaite regarder des vidéos...  
 -   [Guide du débutant sur WCF Data Services](http://go.microsoft.com/fwlink/?LinkId=220864)  
  
-   [Vidéos du développeur WCF Data Services](http://go.microsoft.com/fwlink/?LinkId=220861)  
  
-   [OData : site web développeurs](http://go.microsoft.com/fwlink/?LinkId=185866)  
  
 Je souhaite consulter des exemples de bout en bout  
 -   [Exemples de documentation WCF Data Services dans la galerie d’exemples MSDN](http://go.microsoft.com/fwlink/?LinkID=220865)  
  
-   [Autres exemples WCF Data Services dans la galerie d’exemples MSDN](http://go.microsoft.com/fwlink/?LinkId=220866)  
  
-   [Kit de développement logiciel (SDK) OData](http://go.microsoft.com/fwlink/?LinkID=185248)  
  
 Qu'en est-il de l'intégration avec Visual Studio ?  
 -   [Génération de la bibliothèque cliente du service de données](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md)  
  
-   [Création du service de données](../../../../docs/framework/data/wcf/creating-the-data-service.md)  
  
-   [Fournisseur Entity Framework](../../../../docs/framework/data/wcf/entity-framework-provider-wcf-data-services.md)  
  
 Comment puis-je l'utiliser ?  
 -   [Vue d’ensemble](../../../../docs/framework/data/wcf/wcf-data-services-overview.md)  
  
-   [Livre blanc : présentation d’OData](http://go.microsoft.com/fwlink/?LinkId=220867)  
  
-   [Scénarios d’application](../../../../docs/framework/data/wcf/application-scenarios-wcf-data-services.md)  
  
 Je souhaite utiliser Silverlight...  
 -   [Démarrage rapide avec Silverlight](http://go.microsoft.com/fwlink/?LinkID=192782)  
  
-   [WCF Data Services (Silverlight)](http://go.microsoft.com/fwlink/?LinkID=143149)  
  
-   [Prise en main de Silverlight](http://go.microsoft.com/fwlink/?LinkId=148366)  
  
 Je souhaite créer une application Windows Phone…  
 -   [Démarrage rapide avec Silverlight pour le développement de Windows Phone](http://go.microsoft.com/fwlink/?LinkID=214535)  
  
-   [Client OData (Open Data Protocol) pour Windows Phone](http://go.microsoft.com/fwlink/?LinkID=208749)  
  
 Je souhaite utiliser LINQ...  
 -   [Interrogation du service de données](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)  
  
-   [Considérations sur LINQ](../../../../docs/framework/data/wcf/linq-considerations-wcf-data-services.md)  
  
-   [Comment : exécuter les requêtes de services de données](../../../../docs/framework/data/wcf/how-to-execute-data-service-queries-wcf-data-services.md)  
  
 J'ai encore besoin d'informations supplémentaires...  
 -   [Blog de l’équipe WCF Data Services](http://go.microsoft.com/fwlink/?LinkID=150511)  
  
-   [Ressources](../../../../docs/framework/data/wcf/wcf-data-services-resources.md)  
  
-   [Centre de développement WCF Data Services](http://go.microsoft.com/fwlink/?LinkId=220868)  
  
-   [Site web Open Data Protocol](http://go.microsoft.com/fwlink/?LinkID=184554)  
  
## <a name="in-this-section"></a>Dans cette section  
 [Vue d’ensemble](../../../../docs/framework/data/wcf/wcf-data-services-overview.md)  
 Fournit une vue d'ensemble des caractéristiques et des fonctionnalités disponibles dans [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)].  
  
 [Nouveautés de WCF Data Services](http://msdn.microsoft.com/en-us/cf22cad5-b8d9-472b-8d7c-b863b64eaae8)  
 Décrit les nouvelles fonctionnalités de [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] et la prise en charge des nouvelles fonctions de [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)].  
  
 [Prise en main](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)  
 Décrit comment exposer et consommer des flux [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] à l’aide d’[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)].  
  
 [Définition de WCF Data Services](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)  
 Décrit comment créer et configurer un service de données qui expose des flux [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)].  
  
 [Bibliothèque cliente WCF Data Services](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)  
 Décrit comment utiliser des bibliothèques clientes pour consommer les flux [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] d’une application cliente .NET Framework.  
  
## <a name="see-also"></a>Voir aussi  
 [Representational State Transfer (REST)](http://go.microsoft.com/fwlink/?LinkId=113919)

