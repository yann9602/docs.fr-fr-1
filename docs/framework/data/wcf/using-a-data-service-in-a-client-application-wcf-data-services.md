---
title: "Utilisation d'un service de données dans une application cliente (services de données WCF)"
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
- WCF Data Services, getting started
ms.assetid: 90872d0c-e989-4490-b3e9-54afb10d33d4
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c802342f352652e24e53b70c730ddb4c5b8973a0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="using-a-data-service-in-a-client-application-wcf-data-services"></a>Utilisation d'un service de données dans une application cliente (services de données WCF)
Vous pouvez accéder à un service qui expose un [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] flux en fournissant un URI par un navigateur Web. L'URI fournit l'adresse d'une ressource, et les messages de demande sont envoyés à ces adresses pour accéder ou modifier les données sous-jacentes que représente la ressource. Le navigateur émet une commande HTTP GET et retourne la ressource demandée sous forme d'un flux [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]. Pour plus d’informations, consultez [l’accès au Service à partir d’un navigateur Web](../../../../docs/framework/data/wcf/accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md).  
  
 Même si un navigateur Web peut être utile pour tester si un service [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] retourne les données attendues, les services [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] de production qui vous permettent également de créer, mettre à jour et supprimer les données sont en général accessibles via le code d'application ou les langages de script d'une page Web. Cette rubrique fournit une vue d’ensemble de l’accès à [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] de flux à partir d’une application cliente.  
  
## <a name="accessing-and-changing-data-using-rest-semantics"></a>Accès et modification des données à l'aide de la sémantique REST  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]aide à garantie l’interopérabilité entre les services qui exposent [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] flux et les applications qui consomment [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] flux. Applications accéder et modifier des données dans un [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]-en fonction de service en envoyant des messages de demande d’une action HTTP spécifique et avec un URI qui adresse une ressource d’entité par rapport à laquelle l’action doit être effectuée. Lorsque les données d'entité doivent être fournies, elles le sont comme une charge utile spécifiquement encodée dans le corps du message.  
  
### <a name="http-actions"></a>Actions HTTP  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] prend en charge les actions HTTP suivantes pour effectuer des opérations de création, lecture, mise à jour et suppression sur les données d'entité représentées par la ressource adressée :  
  
-   **HTTP GET** -il s’agit d’action par défaut lors de l’accès à une ressource à partir d’un navigateur. Aucune charge utile n'est fournie dans le message de demande, et une méthode de réponse avec une charge utile qui contient les données demandées est retournée.  
  
-   **HTTP POST** -insère de nouvelles données d’entité dans la ressource fournie. Les données à insérer sont fournies dans la charge utile du message de demande. La charge utile du message de réponse contient les données de l'entité créée récemment. Cela inclut les valeurs de clés créées automatiquement. L'en-tête contient également l'URI qui adresse la nouvelle ressource d'entité.  
  
-   **HTTP DELETE** -supprime les données d’entité qui représente la ressource spécifiée. Une charge utile n'est pas présente dans les messages de demande ou de réponse.  
  
-   **HTTP PUT** - remplace les données d’entité à la ressource demandée avec de nouvelles données qui sont fournies dans la charge utile du message de demande existantes.  
  
-   **HTTP MERGE** - en raison du manque d’efficacité lors de l’exécution d’une suppression suivie d’une insertion dans la source de données, de modifier les données d’entité, [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] présente une nouvelle action HTTP MERGE. La charge utile du message de demande contient les propriétés qui doivent être changées sur la ressource d'entité adressée. Comme HTTP MERGE n'est pas défini dans la spécification HTTP, elle peut nécessiter un traitement supplémentaire pour acheminer une demande HTTP MERGE via des serveurs non-[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)].  
  
 Pour plus d’informations, consultez [OData : opérations](http://go.microsoft.com/fwlink/?LinkId=185792).  
  
### <a name="payload-formats"></a>Formats de charge utile  
 Pour une demande HTTP PUT, HTTP POST ou HTTP MERGE, la charge utile d'un message de demande contient les données d'entité que vous envoyez au service de données. Le contenu de la charge utile dépend du format de données du message. Les réponses HTTP à toutes les actions sauf DELETE contiennent également une charge utile. [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]prend en charge les formats de charge utile suivants pour accéder et modifier des données avec le service :  
  
-   **Atom** -encodage de message XML qui est défini par [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] en tant qu’extension aux Atom Publishing Protocol (AtomPub) pour permettre l’échange de données sur HTTP pour les flux Web, podcasts, wikis et fonctionnalité Internet XML. Pour plus d’informations, consultez [OData : Format Atom](http://go.microsoft.com/fwlink/?LinkId=185794).  
  
-   **JSON** -JavaScript Objet Notation (JSON) est un format d’échange de données léger basé sur un sous-ensemble du langage de programmation JavaScript. Pour plus d’informations, consultez [OData : Format JSON](http://go.microsoft.com/fwlink/?LinkId=185795).  
  
 Le format du message de la charge utile est demandé dans l'en-tête du message de requête HTTP. Pour plus d’informations, consultez [OData : opérations](http://go.microsoft.com/fwlink/?LinkID=185792).  
  
## <a name="accessing-and-changing-data-using-client-libraries"></a>Accès et modification des données à l'aide des bibliothèques clientes  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]inclut des bibliothèques clientes qui vous permettent de consommer plus facilement un [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] flux à partir de .NET Framework et les applications clientes basées sur Silverlight. Ces bibliothèques simplifient l'envoi et la réception des messages HTTP. Elles traduisent également la charge utile de message dans les objets CLR qui représentent des données d'entité. Les bibliothèques clientes comprennent les deux classes principales <xref:System.Data.Services.Client.DataServiceContext> et <xref:System.Data.Services.Client.DataServiceQuery%601>. Ces classes vous permettent d'interroger un service de données, puis d'utiliser les données d'entité retournées sous forme d'objets CLR. Pour plus d’informations, consultez [bibliothèque cliente de WCF Data Services](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md) et [WCF Data Services (Silverlight)](http://msdn.microsoft.com/en-us/c0cd9f4b-1372-48e4-9935-c8421239da30).  
  
 Vous pouvez utiliser la **ajouter une référence de Service** boîte de dialogue dans Visual Studio pour ajouter une référence à un service de données. Cet outil demande les métadonnées de service à un service de données référencé et génère le <xref:System.Data.Services.Client.DataServiceContext> qui représente un service de données, ainsi que les classes de service de données client qui représentent des entités. Pour plus d’informations, consultez [génération de la bibliothèque de Client de Service de données](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md).  
  
 Il existe des bibliothèques de programmation que vous pouvez utiliser pour consommer un [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] flux dans d’autres types d’applications clientes. Pour plus d’informations, consultez la [OData SDK](http://go.microsoft.com/fwlink/?LinkId=185796).  
  
## <a name="see-also"></a>Voir aussi  
 [Accès aux ressources d’un service de données](../../../../docs/framework/data/wcf/accessing-data-service-resources-wcf-data-services.md)  
 [Démarrage rapide](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)
