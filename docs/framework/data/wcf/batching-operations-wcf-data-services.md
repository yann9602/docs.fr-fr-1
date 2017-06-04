---
title: "Op&#233;rations de traitement par lot (WCF Data Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-oob"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Services de données WCF, bibliothèque cliente"
ms.assetid: 962a49d1-cc11-4b96-bc7d-071dd6607d6c
caps.latest.revision: 3
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# Op&#233;rations de traitement par lot (WCF Data Services)
Le protocole [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] prend en charge le traitement par lots des demandes faites à un service [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)].  Pour plus d'informations, consultez [OData : traitement par lots](http://go.microsoft.com/fwlink/?LinkId=186075). Dans [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], chaque opération qui utilise l'élément <xref:System.Data.Services.Client.DataServiceContext>, comme l'exécution d'une requête ou l'enregistrement de modifications, entraîne l'envoi d'une demande distincte au service de données.  Pour maintenir une étendue logique pour les jeux d'opérations, vous pouvez définir explicitement des lots opérationnels.  Cela garantit que toutes les opérations dans le lot sont envoyées au service de données dans une requête HTTP unique, et cela permet au serveur de traiter les opérations de manière atomique et de réduire le nombre de boucles vers le service de données.  
  
## Opérations de traitement par lot des requêtes  
 Pour exécuter plusieurs requêtes dans un lot unique, vous devez créer chaque requête dans le lot comme une instance distincte de la classe <xref:System.Data.Services.Client.DataServiceRequest%601>.  Lorsque vous créez une requête d'interrogation de cette manière, la requête elle\-même est définie comme un URI, et elle suit les règles pour l'adressage de ressources.  Pour plus d'informations, consultez [Accès aux ressources de service des données](../../../../docs/framework/data/wcf/accessing-data-service-resources-wcf-data-services.md).  Les requêtes d'interrogation par lot sont envoyées au service de données lorsque la méthode <xref:System.Data.Services.Client.DataServiceContext.ExecuteBatch%2A> est appelée qui contient les objets de requête d'interrogation.  Cette méthode retourne un objet <xref:System.Data.Services.Client.DataServiceResponse> qui est une collection d'objets <xref:System.Data.Services.Client.QueryOperationResponse%601> qui représentent des réponses aux requêtes individuelles dans le lot, chacune contenant une collection d'objets retournés par la requête ou des informations d'erreur.  Lorsqu'une opération de requête unique dans le lot échoue, les informations d'erreur sont retournées dans l'objet <xref:System.Data.Services.Client.QueryOperationResponse%601> pour l'opération qui a échoué et les opérations restantes sont exécutées.  Pour plus d'informations, consultez [Procédure : exécuter des requêtes dans un lot](../../../../docs/framework/data/wcf/how-to-execute-queries-in-a-batch-wcf-data-services.md).  
  
 Les requêtes par lot peuvent également être exécutées de façon asynchrone.  Pour plus d'informations, consultez [Opérations asynchrones](../../../../docs/framework/data/wcf/asynchronous-operations-wcf-data-services.md).  
  
## Traitement par lot de l'opération SaveChanges  
 Lorsque vous appelez la méthode <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A>, toutes les modifications suivies par le contexte sont traduites en opérations REST envoyées au service [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] sous forme de requêtes HTTP.  Par défaut, ces modifications ne sont pas envoyées dans un message de demande unique.  Pour que toutes les modifications soient envoyées dans une demande unique, vous devez appeler la méthode <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%28System.Data.Services.Client.SaveChangesOptions%29> et inclure une valeur <xref:System.Data.Services.Client.SaveChangesOptions> dans l'énumération <xref:System.Data.Services.Client.SaveChangesOptions> que vous fournissez à la méthode.  
  
 Vous pouvez également enregistrer de façon asynchrone les modifications par lot.  Pour plus d'informations, consultez [Opérations asynchrones](../../../../docs/framework/data/wcf/asynchronous-operations-wcf-data-services.md).  
  
## Voir aussi  
 [Bibliothèque cliente de WCF Data Services](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)