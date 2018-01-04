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
# <a name="serializing-in-json-with-message-level-programming"></a><span data-ttu-id="f0005-102">Sérialisation dans JSON avec programmation de niveau message</span><span class="sxs-lookup"><span data-stu-id="f0005-102">Serializing in Json with Message Level Programming</span></span>
<span data-ttu-id="f0005-103">WCF prend en charge la sérialisation des données au format JSON.</span><span class="sxs-lookup"><span data-stu-id="f0005-103">WCF supports serializing data in JSON format.</span></span> <span data-ttu-id="f0005-104">Cette rubrique explique comment indiquer à WCF de sérialiser vos types à l'aide de <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span><span class="sxs-lookup"><span data-stu-id="f0005-104">This topic describes how to tell WCF to serialize your types using the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span>  
  
## <a name="typed-message-programming"></a><span data-ttu-id="f0005-105">Programmation de message typé</span><span class="sxs-lookup"><span data-stu-id="f0005-105">Typed Message Programming</span></span>  
 <span data-ttu-id="f0005-106"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> est utilisé lorsque <xref:System.ServiceModel.Web.WebGetAttribute> ou <xref:System.ServiceModel.Web.WebInvokeAttribute> est appliqué à une opération de service.</span><span class="sxs-lookup"><span data-stu-id="f0005-106">The <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> is used when the <xref:System.ServiceModel.Web.WebGetAttribute> or the <xref:System.ServiceModel.Web.WebInvokeAttribute> is applied to a service operation.</span></span> <span data-ttu-id="f0005-107">Les deux attributs vous permettent de spécifier `RequestFormat` et `ResponseFormat`.</span><span class="sxs-lookup"><span data-stu-id="f0005-107">Both of these attributes allow you to specify the `RequestFormat` and `ResponseFormat`.</span></span> <span data-ttu-id="f0005-108">Pour utiliser JSON pour les demandes et les réponses définissez-les à `WebMessageFormat.Json`.</span><span class="sxs-lookup"><span data-stu-id="f0005-108">To use JSON for requests and responses set both of these to `WebMessageFormat.Json`.</span></span>  <span data-ttu-id="f0005-109">Pour utiliser JSON, vous devez utiliser le <xref:System.ServiceModel.WebHttpBinding> qui configure automatiquement le <xref:System.ServiceModel.Description.WebHttpBehavior>.</span><span class="sxs-lookup"><span data-stu-id="f0005-109">In order to use JSON you must use the <xref:System.ServiceModel.WebHttpBinding> which automatically configures the <xref:System.ServiceModel.Description.WebHttpBehavior>.</span></span> <span data-ttu-id="f0005-110">Pour plus d’informations sur la sérialisation WCF, consultez : [sérialisation et désérialisation](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md), [sérialisation dans Windows Communication Foundation](http://msdn.microsoft.com/magazine/cc163569.aspx).</span><span class="sxs-lookup"><span data-stu-id="f0005-110">For more information about WCF serialization, see: [Serialization and Deserialization](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md), [Serialization in Windows Communication Foundation](http://msdn.microsoft.com/magazine/cc163569.aspx).</span></span> <span data-ttu-id="f0005-111">Pour plus d’informations sur JSON et WCF, consultez [Introduction aux Services RESTfull avec WCF](http://msdn.microsoft.com/magazine/dd315413.aspx), [compatible JSON de création de Services WCF dans .NET 3.5](http://www.pluralsight-training.net/community/blogs/fritz/archive/2008/01/31/50121.aspx), et [vue d’ensemble de REST dans WCF](http://msdn.microsoft.com/netframework/dd547388).</span><span class="sxs-lookup"><span data-stu-id="f0005-111">For more information about JSON and WCF see [An Introduction to RESTfull Services with WCF](http://msdn.microsoft.com/magazine/dd315413.aspx), [Creating JSON-enabled WCF Services in .NET 3.5](http://www.pluralsight-training.net/community/blogs/fritz/archive/2008/01/31/50121.aspx), and [Overview of REST in WCF](http://msdn.microsoft.com/netframework/dd547388).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f0005-112">L'utilisation de JSON requiert l'utilisation de <xref:System.ServiceModel.WebHttpBinding> et <xref:System.ServiceModel.Description.WebHttpBehavior> qui ne prennent pas en charge la communication SOAP.</span><span class="sxs-lookup"><span data-stu-id="f0005-112">Using JSON requires use of <xref:System.ServiceModel.WebHttpBinding> and <xref:System.ServiceModel.Description.WebHttpBehavior> which do not support SOAP communication.</span></span> <span data-ttu-id="f0005-113">Les services qui communiquent avec le <xref:System.ServiceModel.WebHttpBinding> ne prennent pas en charge exposition des métadonnées de service afin de vous ne serez pas en mesure d’utiliser la fonctionnalité d’ajouter une référence de Service de Visual Studio ou l’outil de ligne de commande svcutil pour générer un proxy côté client.</span><span class="sxs-lookup"><span data-stu-id="f0005-113">Services that communicate with the <xref:System.ServiceModel.WebHttpBinding> do not support exposing service metadata so you will not be able to use Visual Studio’s Add Service Reference functionality or the svcutil command-line tool to generate a client-side proxy.</span></span> <span data-ttu-id="f0005-114">Pour plus d’informations, comment vous pouvez appeler par programmation les services qui utilisent <xref:System.ServiceModel.WebHttpBinding>, consultez [comment consommer des Services REST avec WCF](http://blogs.msdn.com/b/pedram/archive/2008/04/21/how-to-consume-rest-services-with-wcf.aspx).</span><span class="sxs-lookup"><span data-stu-id="f0005-114">For more information how you can programmatically call services that use <xref:System.ServiceModel.WebHttpBinding>, see [How to Consume REST Services with WCF](http://blogs.msdn.com/b/pedram/archive/2008/04/21/how-to-consume-rest-services-with-wcf.aspx).</span></span>  
  
## <a name="untyped-message-programming"></a><span data-ttu-id="f0005-115">Programmation de message non typé</span><span class="sxs-lookup"><span data-stu-id="f0005-115">Untyped Message Programming</span></span>  
 <span data-ttu-id="f0005-116">Lorsque utilisez directement des objets du message non typé, vous devez définir explicitement les propriétés sur le message non typé pour le sérialiser comme JSON.</span><span class="sxs-lookup"><span data-stu-id="f0005-116">When working directly with untyped Message objects, you must explicitly set the properties on the untyped message to serialize it as JSON.</span></span> <span data-ttu-id="f0005-117">L'extrait de code suivant montre comment procéder.</span><span class="sxs-lookup"><span data-stu-id="f0005-117">The following code snippet shows how to do this.</span></span>  
  
```  
 Message response = Message.CreateMessage(  
                  MessageVersion.None,    // No SOAP message version  
                             "*",                     // SOAP action, ignored since this is JSON  
                             "Response string: JSON format specified", // Message body  
                             new DataContractJsonSerializer(typeof(string))); // Specify DataContractJsonSerializer  
      response.Properties.Add( WebBodyFormatMessageProperty.Name,   
                    new WebBodyFormatMessageProperty(WebContentFormat.Json)); // Use JSON format  
```  
  
## <a name="see-also"></a><span data-ttu-id="f0005-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f0005-118">See Also</span></span>  
 [<span data-ttu-id="f0005-119">Intégration d’AJAX et prise en charge de JSON</span><span class="sxs-lookup"><span data-stu-id="f0005-119">AJAX Integration and JSON Support</span></span>](../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md)  
 [<span data-ttu-id="f0005-120">Sérialisation JSON autonome</span><span class="sxs-lookup"><span data-stu-id="f0005-120">Stand-Alone JSON Serialization</span></span>](../../../../docs/framework/wcf/feature-details/stand-alone-json-serialization.md)  
 [<span data-ttu-id="f0005-121">Sérialisation JSON</span><span class="sxs-lookup"><span data-stu-id="f0005-121">JSON Serialization</span></span>](../../../../docs/framework/wcf/samples/json-serialization.md)
