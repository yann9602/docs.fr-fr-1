---
title: "Bibliothèque client services de données WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF Data Services, client library
- DataServiceQuery class, about DataServiceQuery class
- DataServiceContext class, about DataServiceContext class
ms.assetid: 21075e50-8917-413e-a8ea-35a0f6e65aa5
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1e321200ce4b3582d154c5a188584c9e0b12c10d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="wcf-data-services-client-library"></a>Bibliothèque client services de données WCF
Toute application peut interagir avec un service de données basé sur [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] si elle peut envoyer une requête HTTP et traiter le flux [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] retourné par un service de données. Cette interopérabilité vous permet d'accéder aux services basés sur [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] à partir d'une large gamme d'applications Web. [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]inclut des bibliothèques clientes qui fournissent une expérience en programmation plus riche lorsque vous consommez [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] flux à partir de .NET Framework ou les applications Silverlight.  
  
 Les deux classes principales de la bibliothèque cliente sont la classe <xref:System.Data.Services.Client.DataServiceContext> et la classe <xref:System.Data.Services.Client.DataServiceQuery%601>. La classe <xref:System.Data.Services.Client.DataServiceContext> encapsule des opérations prises en charge sur un service de données spécifié. Même si les services [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] sont sans état, ce n'est pas le cas du contexte. Par conséquent, vous pouvez utiliser la <xref:System.Data.Services.Client.DataServiceContext> classe pour gérer l’état sur le client entre des interactions avec le service de données pour prendre en charge des fonctionnalités telles que la gestion des modifications. Cette classe gère également des identités et suit les modifications. La classe <xref:System.Data.Services.Client.DataServiceQuery%601> représente une requête sur un jeu d'entités spécifique.  
  
 Cette section décrit comment utiliser des bibliothèques clientes pour accéder et modifier des données d'une application cliente .NET Framework. Pour plus d’informations sur l’utilisation de la [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] bibliothèque client avec une application basée sur Silverlight, consultez [WCF Data Services (Silverlight)](http://go.microsoft.com/fwlink/?LinkId=186016). Autres bibliothèques clientes sont disponibles qui permettent de consommer un [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] flux dans d’autres types d’applications. Pour plus d’informations, consultez la [OData SDK](http://go.microsoft.com/fwlink/?LinkID=185796).  
  
## <a name="in-this-section"></a>Dans cette section  
 [Génération de la bibliothèque cliente du service de données](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md)  
 Décrit comment générer une bibliothèque cliente et les classes de service de données de client qui sont basées sur [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] flux.  
  
 [Interrogation du service de données](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)  
 Décrit comment interroger un service de données depuis une application .NET Framework à l'aide de bibliothèques clientes.  
  
 [Chargement de contenu différé](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md)  
 Décrit comment charger un contenu supplémentaire non inclus dans la réponse à la requête initiale.  
  
 [Mise à jour du Service de données](../../../../docs/framework/data/wcf/updating-the-data-service-wcf-data-services.md)  
 Décrit comment créer, modifier et supprimer des entités et des relations à l'aide des bibliothèques clientes.  
  
 [Opérations asynchrones](../../../../docs/framework/data/wcf/asynchronous-operations-wcf-data-services.md)  
 Décrit les fonctions fournies par les bibliothèques clientes pour l'utilisation d'un service de données de façon asynchrone.  
  
 [Opérations de traitement par lot](../../../../docs/framework/data/wcf/batching-operations-wcf-data-services.md)  
 Décrit comment envoyer plusieurs demandes au service de données dans un lot unique à l'aide des bibliothèques clientes.  
  
 [Liaison de données aux contrôles](../../../../docs/framework/data/wcf/binding-data-to-controls-wcf-data-services.md)  
 Décrit comment lier des contrôles à un [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] flux retourné par un service de données.  
  
 [Appel des opérations de Service](../../../../docs/framework/data/wcf/calling-service-operations-wcf-data-services.md)  
 Décrit comment utiliser la bibliothèque cliente pour appeler des opérations de service.  
  
 [Gérer le contexte de Service de données](../../../../docs/framework/data/wcf/managing-the-data-service-context-wcf-data-services.md)  
 Décrit les options de gestion du comportement de la bibliothèque cliente.  
  
 [Utilisation des données binaires](../../../../docs/framework/data/wcf/working-with-binary-data-wcf-data-services.md)  
 Décrit comment accéder à des données binaires retournées par le service de données sous forme de flux de données et les modifier.  
  
## <a name="see-also"></a>Voir aussi  
 [Définition de WCF Data Services](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)  
 [Prise en main](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)
