---
title: "Utilisation d&#39;un service de donn&#233;es dans une application cliente (WCF Data Services) | Microsoft Docs"
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
  - "Services de données WCF, mise en route"
ms.assetid: 90872d0c-e989-4490-b3e9-54afb10d33d4
caps.latest.revision: 3
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# Utilisation d&#39;un service de donn&#233;es dans une application cliente (WCF Data Services)
Vous pouvez accéder à un service qui expose un flux [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] en fournissant un URI à un navigateur Web.  L'URI fournit l'adresse d'une ressource, et les messages de demande sont envoyés à ces adresses pour accéder ou modifier les données sous\-jacentes que représente la ressource.  Le navigateur émet une commande HTTP GET et retourne la ressource demandée sous forme d'un flux [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)].  Pour plus d'informations, consultez [Accès au service à partir d'un navigateur Web](../../../../docs/framework/data/wcf/accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md).  
  
 Même si un navigateur Web peut être utile pour tester si un service [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] retourne les données attendues, les services [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] de production qui vous permettent également de créer, mettre à jour et supprimer les données sont en général accessibles via le code d'application ou les langages de script d'une page Web.  Cette rubrique présente la façon d'accéder aux flux [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] depuis une application cliente.  
  
## Accès et modification des données à l'aide de la sémantique REST  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] contribue à garantir l'interopérabilité entre les services qui exposent des flux et les applications [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] qui consomment des flux [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]. Les applications accèdent aux données et les modifient dans un service [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] en envoyant des messages de requête d'une action spécifique HTTP et avec un URI qui traite une ressource d'entité sur laquelle l'action doit être exécutée.  Lorsque les données d'entité doivent être fournies, elles le sont comme une charge utile spécifiquement encodée dans le corps du message.  
  
### Actions HTTP  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] prend en charge les actions HTTP suivantes pour effectuer des opérations de création, lecture, mise à jour et suppression sur les données d'entité représentées par la ressource adressée :  
  
-   **HTTP GET** \- Action par défaut lorsqu'un navigateur accède à une ressource.  Aucune charge utile n'est fournie dans le message de demande, et une méthode de réponse avec une charge utile qui contient les données demandées est retournée.  
  
-   **HTTP POST** \- Insère de nouvelles données d'entité dans la ressource fournie.  Les données à insérer sont fournies dans la charge utile du message de demande.  La charge utile du message de réponse contient les données de l'entité créée récemment.  Cela inclut les valeurs de clés créées automatiquement.  L'en\-tête contient également l'URI qui adresse la nouvelle ressource d'entité.  
  
-   **HTTP DELETE** \- Supprime les données d'entité que représente la ressource spécifiée.  Une charge utile n'est pas présente dans les messages de demande ou de réponse.  
  
-   **HTTP PUT** \- Remplace les données d'entité existantes à la ressource demandée par les nouvelles données fournies dans la charge utile du message de demande.  
  
-   **HTTP MERGE** \- En raison du manque d'efficacité lors de l'exécution d'une suppression suivie par une insertion dans la source de données dans le seul but de modifier des données d'entité, [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] présente une nouvelle action HTTP MERGE.  La charge utile du message de demande contient les propriétés qui doivent être changées sur la ressource d'entité adressée.  Comme HTTP MERGE n'est pas défini dans la spécification HTTP, elle peut nécessiter un traitement supplémentaire pour acheminer une demande HTTP MERGE via des serveurs non\-[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)].  
  
 Pour plus d'informations, consultez [OData : opérations](http://go.microsoft.com/fwlink/?LinkId=185792).  
  
### Formats de charge utile  
 Pour une demande HTTP PUT, HTTP POST ou HTTP MERGE, la charge utile d'un message de demande contient les données d'entité que vous envoyez au service de données.  Le contenu de la charge utile dépend du format de données du message.  Les réponses HTTP à toutes les actions sauf DELETE contiennent également une charge utile.  [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] prend en charge les formats de charge utile suivants pour l'accès et la modification de données avec le service :  
  
-   **Atom** \- Encodage de message XML défini par [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] comme une extension du protocole Atom Publishing Protocol \(AtomPub\) pour permettre l'échange de données sur le protocole HTTP pour les flux Web, podcasts, wikis et fonctionnalité Internet au format XML.  Pour plus d'informations, consultez [OData : format Atom](http://go.microsoft.com/fwlink/?LinkId=185794).  
  
-   **JSON** \- JSON \(JavaScript Object Notation\) est un format d'échange de données léger basé sur un sous\-ensemble du langage de programmation JavaScript.  Pour plus d'informations, consultez [OData : format JSON](http://go.microsoft.com/fwlink/?LinkId=185795).  
  
 Le format du message de la charge utile est demandé dans l'en\-tête du message de requête HTTP.  Pour plus d'informations, consultez [OData : opérations](http://go.microsoft.com/fwlink/?LinkID=185792).  
  
## Accès et modification des données à l'aide des bibliothèques clientes  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] inclut des bibliothèques clientes qui vous permettent de consommer plus facilement un flux [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] depuis les applications clientes .NET Framework et Silverlight.  Ces bibliothèques simplifient l'envoi et la réception des messages HTTP.  Elles traduisent également la charge utile de message dans les objets CLR qui représentent des données d'entité.  Les bibliothèques clientes comprennent les deux classes principales <xref:System.Data.Services.Client.DataServiceContext> et <xref:System.Data.Services.Client.DataServiceQuery%601>.  Ces classes vous permettent d'interroger un service de données, puis d'utiliser les données d'entité retournées sous forme d'objets CLR.  Pour plus d’informations, consultez [Bibliothèque cliente de WCF Data Services](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md) et [WCF Data Services \(Silverlight\)](http://msdn.microsoft.com/fr-fr/c0cd9f4b-1372-48e4-9935-c8421239da30).  
  
 Vous pouvez utiliser la boîte de dialogue **Ajouter une référence de service** dans Visual Studio pour ajouter une référence à un service de données.  Cet outil demande les métadonnées de service à un service de données référencé et génère le <xref:System.Data.Services.Client.DataServiceContext> qui représente un service de données, ainsi que les classes de service de données client qui représentent des entités.  Pour plus d'informations, consultez [Génération de la bibliothèque cliente du service de données](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md).  
  
 Il existe des bibliothèques de programmation que vous pouvez utiliser pour consommer des flux [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] dans d'autres types d'application cliente.  Pour plus d'informations, consultez [Kit de développement logiciel \(SDK\) OData](http://go.microsoft.com/fwlink/?LinkId=185796).  
  
## Voir aussi  
 [Accès aux ressources de service des données](../../../../docs/framework/data/wcf/accessing-data-service-resources-wcf-data-services.md)   
 [Démarrage rapide](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)