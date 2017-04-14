---
title: "S&#233;rialisation dans JSON avec programmation de niveau message | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5f940ba2-57ee-4c49-a779-957c5e7e71fa
caps.latest.revision: 3
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# S&#233;rialisation dans JSON avec programmation de niveau message
WCF prend en charge la sérialisation des données au format JSON.Cette rubrique explique comment indiquer à WCF de sérialiser vos types à l'aide de <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.  
  
## Programmation de message typé  
 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> est utilisé lorsque <xref:System.ServiceModel.Web.WebGetAttribute> ou <xref:System.ServiceModel.Web.WebInvokeAttribute> est appliqué à une opération de service.Les deux attributs vous permettent de spécifier `RequestFormat` et `ResponseFormat`.Pour utiliser JSON pour les demandes et les réponses définissez\-les à `WebMessageFormat.Json`.Pour utiliser JSON, vous devez utiliser le <xref:System.ServiceModel.WebHttpBinding> qui configure automatiquement le <xref:System.ServiceModel.Description.WebHttpBehavior>.Pour plus d'informations sur la sérialisation WCF, consultez [Sérialisation et désérialisation](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md)[Sérialisation dans Windows Communication Foundation](http://msdn.microsoft.com/magazine/cc163569.aspx).Pour plus d'informations sur JSON et WCF, consultez [Introduction aux services RESTfull avec WCF](http://msdn.microsoft.com/magazine/dd315413.aspx), [Création de services WCF compatibles JSON dans .NET 3.5](http://www.pluralsight-training.net/community/blogs/fritz/archive/2008/01/31/50121.aspx) et [Vue d'ensemble de REST dans WCF](http://msdn.microsoft.com/netframework/dd547388).  
  
> [!IMPORTANT]
>  L'utilisation de JSON requiert l'utilisation de <xref:System.ServiceModel.WebHttpBinding> et <xref:System.ServiceModel.Description.WebHttpBehavior> qui ne prennent pas en charge la communication SOAP.Les services qui communiquent avec <xref:System.ServiceModel.WebHttpBinding> ne prennent pas en charge l'exposition des métadonnées de service, par conséquent vous ne pouvez pas utiliser la fonctionnalité Ajouter une référence de service de Visual Studio ou l'outil en ligne de commande svcutil pour générer un proxy côté client.Pour plus d'informations sur l'appel de services par programme qui utilisent <xref:System.ServiceModel.WebHttpBinding>, consultez [Procédure : consommer les services REST avec WCF](http://blogs.msdn.com/b/pedram/archive/2008/04/21/how-to-consume-rest-services-with-wcf.aspx).  
  
## Programmation de message non typé  
 Lorsque utilisez directement des objets du message non typé, vous devez définir explicitement les propriétés sur le message non typé pour le sérialiser comme JSON.L'extrait de code suivant montre comment procéder.  
  
```  
 Message response = Message.CreateMessage(  
                  MessageVersion.None,    // No SOAP message version  
                             "*",                     // SOAP action, ignored since this is JSON  
                             "Response string: JSON format specified", // Message body  
                             new DataContractJsonSerializer(typeof(string))); // Specify DataContractJsonSerializer  
      response.Properties.Add( WebBodyFormatMessageProperty.Name,   
                    new WebBodyFormatMessageProperty(WebContentFormat.Json)); // Use JSON format  
  
```  
  
## Voir aussi  
 [Intégration d'AJAX et prise en charge de JSON](../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md)   
 [Sérialisation JSON autonome](../../../../docs/framework/wcf/feature-details/stand-alone-json-serialization.md)   
 [JSON Serialization](../../../../docs/framework/wcf/samples/json-serialization.md)