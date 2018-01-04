---
title: "Sérialisation dans JSON avec programmation de niveau message"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5f940ba2-57ee-4c49-a779-957c5e7e71fa
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bfa8952c54f29d88cb4975c1924b9c3e94c1c226
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="serializing-in-json-with-message-level-programming"></a>Sérialisation dans JSON avec programmation de niveau message
WCF prend en charge la sérialisation des données au format JSON. Cette rubrique explique comment indiquer à WCF de sérialiser vos types à l'aide de <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.  
  
## <a name="typed-message-programming"></a>Programmation de message typé  
 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> est utilisé lorsque <xref:System.ServiceModel.Web.WebGetAttribute> ou <xref:System.ServiceModel.Web.WebInvokeAttribute> est appliqué à une opération de service. Les deux attributs vous permettent de spécifier `RequestFormat` et `ResponseFormat`. Pour utiliser JSON pour les demandes et les réponses définissez-les à `WebMessageFormat.Json`.  Pour utiliser JSON, vous devez utiliser le <xref:System.ServiceModel.WebHttpBinding> qui configure automatiquement le <xref:System.ServiceModel.Description.WebHttpBehavior>. Pour plus d’informations sur la sérialisation WCF, consultez : [sérialisation et désérialisation](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md), [sérialisation dans Windows Communication Foundation](http://msdn.microsoft.com/magazine/cc163569.aspx). Pour plus d’informations sur JSON et WCF, consultez [Introduction aux Services RESTfull avec WCF](http://msdn.microsoft.com/magazine/dd315413.aspx), [compatible JSON de création de Services WCF dans .NET 3.5](http://www.pluralsight-training.net/community/blogs/fritz/archive/2008/01/31/50121.aspx), et [vue d’ensemble de REST dans WCF](http://msdn.microsoft.com/netframework/dd547388).  
  
> [!IMPORTANT]
>  L'utilisation de JSON requiert l'utilisation de <xref:System.ServiceModel.WebHttpBinding> et <xref:System.ServiceModel.Description.WebHttpBehavior> qui ne prennent pas en charge la communication SOAP. Les services qui communiquent avec le <xref:System.ServiceModel.WebHttpBinding> ne prennent pas en charge exposition des métadonnées de service afin de vous ne serez pas en mesure d’utiliser la fonctionnalité d’ajouter une référence de Service de Visual Studio ou l’outil de ligne de commande svcutil pour générer un proxy côté client. Pour plus d’informations, comment vous pouvez appeler par programmation les services qui utilisent <xref:System.ServiceModel.WebHttpBinding>, consultez [comment consommer des Services REST avec WCF](http://blogs.msdn.com/b/pedram/archive/2008/04/21/how-to-consume-rest-services-with-wcf.aspx).  
  
## <a name="untyped-message-programming"></a>Programmation de message non typé  
 Lorsque utilisez directement des objets du message non typé, vous devez définir explicitement les propriétés sur le message non typé pour le sérialiser comme JSON. L'extrait de code suivant montre comment procéder.  
  
```  
 Message response = Message.CreateMessage(  
                  MessageVersion.None,    // No SOAP message version  
                             "*",                     // SOAP action, ignored since this is JSON  
                             "Response string: JSON format specified", // Message body  
                             new DataContractJsonSerializer(typeof(string))); // Specify DataContractJsonSerializer  
      response.Properties.Add( WebBodyFormatMessageProperty.Name,   
                    new WebBodyFormatMessageProperty(WebContentFormat.Json)); // Use JSON format  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Intégration d’AJAX et prise en charge de JSON](../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md)  
 [Sérialisation JSON autonome](../../../../docs/framework/wcf/feature-details/stand-alone-json-serialization.md)  
 [Sérialisation JSON](../../../../docs/framework/wcf/samples/json-serialization.md)
