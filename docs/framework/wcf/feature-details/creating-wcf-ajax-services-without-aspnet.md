---
title: "Création de services AJAX WCF sans ASP.NET"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ba4a7d1b-e277-4978-9f62-37684e6dc934
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 70926e1deb9b4911a7d89d49280b9a0e6068cc42
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="creating-wcf-ajax-services-without-aspnet"></a><span data-ttu-id="7c039-102">Création de services AJAX WCF sans ASP.NET</span><span class="sxs-lookup"><span data-stu-id="7c039-102">Creating WCF AJAX Services without ASP.NET</span></span>
<span data-ttu-id="7c039-103">Il est possible d'accéder aux services AJAX [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] à partir d'une page Web activée pour JavaScript, sans recourir à ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="7c039-103">[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] AJAX services can be accessed from any JavaScript-enabled Web page, without requiring ASP.NET AJAX.</span></span> <span data-ttu-id="7c039-104">Cette rubrique décrit comment créer un service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] de ce type.</span><span class="sxs-lookup"><span data-stu-id="7c039-104">This topic describes how to create such a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span></span>  
  
 <span data-ttu-id="7c039-105">Pour obtenir des instructions sur l’utilisation de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] avec ASP.NET AJAX, consultez [création de Services WCF pour ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md).</span><span class="sxs-lookup"><span data-stu-id="7c039-105">For instructions on using [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] with ASP.NET AJAX, see [Creating WCF Services for ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md).</span></span>  
  
 <span data-ttu-id="7c039-106">La création d'un service AJAX [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] se décompose en trois parties :</span><span class="sxs-lookup"><span data-stu-id="7c039-106">There are three parts to a creating a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] AJAX service:</span></span>  
  
-   <span data-ttu-id="7c039-107">Création d'un point de terminaison AJAX accessible à partir du navigateur</span><span class="sxs-lookup"><span data-stu-id="7c039-107">Creating an AJAX endpoint that can be accessed from the browser.</span></span>  
  
-   <span data-ttu-id="7c039-108">Création d'un contrat de service compatible AJAX</span><span class="sxs-lookup"><span data-stu-id="7c039-108">Creating an AJAX-compatible service contract.</span></span>  
  
-   <span data-ttu-id="7c039-109">Accès aux services AJAX WCF</span><span class="sxs-lookup"><span data-stu-id="7c039-109">Accessing WCF AJAX services.</span></span>  
  
## <a name="creating-an-ajax-endpoint"></a><span data-ttu-id="7c039-110">Création d'un point de terminaison AJAX</span><span class="sxs-lookup"><span data-stu-id="7c039-110">Creating an AJAX Endpoint</span></span>  
 <span data-ttu-id="7c039-111">La méthode la plus simple pour activer la prise en charge d'AJAX dans un service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] consiste à utiliser le <xref:System.ServiceModel.Activation.WebServiceHostFactory> dans le fichier .svc associé au service, comme l'illustre l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="7c039-111">The most basic way to enable AJAX support in a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service is to use the <xref:System.ServiceModel.Activation.WebServiceHostFactory> in the .svc file associated with the service, as in the following example.</span></span>  
  
```  
<%ServiceHost   
    language=c#  
    Debug="true"  
    Service="Microsoft.Ajax.Samples.CityService"  
    Factory=System.ServiceModel.Activation.WebServiceHostFactory  
%>  
```  
  
 <span data-ttu-id="7c039-112">Vous avez également la possibilité d'utiliser une configuration pour ajouter un point de terminaison AJAX.</span><span class="sxs-lookup"><span data-stu-id="7c039-112">Alternatively, you can also use configuration to add an AJAX endpoint.</span></span> <span data-ttu-id="7c039-113">Utilisez le <xref:System.ServiceModel.WebHttpBinding> sur le point de terminaison de service et configurez ce point de terminaison avec le <xref:System.ServiceModel.Description.WebHttpBehavior>, comme l'illustre l'extrait de code suivant.</span><span class="sxs-lookup"><span data-stu-id="7c039-113">Use the <xref:System.ServiceModel.WebHttpBinding> on the service endpoint and configure that endpoint with the <xref:System.ServiceModel.Description.WebHttpBehavior> as shown in the following code snippet.</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="AjaxBehavior">  
          <webHttp/>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
    <services>  
      <service name="Microsoft.Ajax.Samples.CityService">  
        <endpoint   
          address="ajaxEndpoint"  
          behaviorConfiguration="AjaxBehavior"  
          binding="webHttpBinding"  
          contract="Microsoft.Ajax.Samples.ICityService" />  
      </service>  
    </services>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="7c039-114">Pour obtenir un exemple, consultez la [AJAX Service with JSON et XML](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md).</span><span class="sxs-lookup"><span data-stu-id="7c039-114">For a working example, see the [AJAX Service with JSON and XML](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md).</span></span>  
  
## <a name="creating-an-ajax-compatible-service-contract"></a><span data-ttu-id="7c039-115">Création d'un contrat de service compatible AJAX</span><span class="sxs-lookup"><span data-stu-id="7c039-115">Creating an AJAX-Compatible Service Contract</span></span>  
 <span data-ttu-id="7c039-116">Par défaut, les contrats de service exposés sur un point de terminaison AJAX retournent les données au format XML.</span><span class="sxs-lookup"><span data-stu-id="7c039-116">By default, service contracts exposed over an AJAX endpoint return data in the XML format.</span></span> <span data-ttu-id="7c039-117">Qui plus est, les opérations de service sont, par défaut, accessibles par le biais des requêtes HTTP POST adressées aux URL qui incluent l'adresse du point de terminaison suivie du nom de l'opération, comme l'illustre l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="7c039-117">Also, by default service operations are accessible through HTTP POST requests to URLs that include the endpoint address followed by the operation name, as shown in the following example.</span></span>  
  
```  
[OperationContract]  
string[] GetCities(string firstLetters);  
```  
  
 <span data-ttu-id="7c039-118">Cette opération est accessible à l’aide d’une requête HTTP POST à `http://serviceaddress/endpointaddress/GetCities` et retourne un message XML.</span><span class="sxs-lookup"><span data-stu-id="7c039-118">This operation is accessible using an HTTP POST to `http://serviceaddress/endpointaddress/GetCities` and return an XML message.</span></span>  
  
 <span data-ttu-id="7c039-119">Vous pouvez utiliser le modèle de programmation Web complet pour personnaliser ces aspects de base.</span><span class="sxs-lookup"><span data-stu-id="7c039-119">You can use the full Web Programming Model to customize these basic aspects.</span></span> <span data-ttu-id="7c039-120">Par exemple, vous pouvez utiliser les attributs <xref:System.ServiceModel.Web.WebGetAttribute> ou <xref:System.ServiceModel.Web.WebInvokeAttribute> pour contrôler le verbe HTTP auquel l'opération répond, ou vous pouvez utiliser la propriété `UriTemplate` de ces attributs respectifs pour spécifier des URI personnalisés.</span><span class="sxs-lookup"><span data-stu-id="7c039-120">For example, you can use the <xref:System.ServiceModel.Web.WebGetAttribute> or <xref:System.ServiceModel.Web.WebInvokeAttribute> attributes to control the HTTP verb to which the operation responds or use the `UriTemplate` property of these respective attributes to specify custom URIs.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="7c039-121">le [modèle de programmation WCF Web HTTP](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md) rubrique.</span><span class="sxs-lookup"><span data-stu-id="7c039-121"> the [WCF Web HTTP Programming Model](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md) topic.</span></span>  
  
 <span data-ttu-id="7c039-122">Le format de données JSON est souvent utilisé dans les services AJAX.</span><span class="sxs-lookup"><span data-stu-id="7c039-122">The JSON data format is often used in AJAX services.</span></span> <span data-ttu-id="7c039-123">Pour créer une opération qui retourne des données JSON au lieu de données XML, affectez <xref:System.ServiceModel.Web.WebGetAttribute.ResponseFormat%2A> à la propriété <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A> (ou la propriété <xref:System.ServiceModel.Web.WebMessageFormat.Json>).</span><span class="sxs-lookup"><span data-stu-id="7c039-123">To create an operation that returns JSON instead of XML, set the <xref:System.ServiceModel.Web.WebGetAttribute.ResponseFormat%2A> (or the <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A>) property to <xref:System.ServiceModel.Web.WebMessageFormat.Json>.</span></span> <span data-ttu-id="7c039-124">Le [de la sérialisation JSON autonome](../../../../docs/framework/wcf/feature-details/stand-alone-json-serialization.md) rubrique indique comment intégrés .NET les données et les types de contrat les types sont mappés au format JSON.</span><span class="sxs-lookup"><span data-stu-id="7c039-124">The [Stand-Alone JSON Serialization](../../../../docs/framework/wcf/feature-details/stand-alone-json-serialization.md) topic shows how built-in .NET types and data contract types map to JSON.</span></span>  
  
 <span data-ttu-id="7c039-125">En principe, les demandes et les réponses JSON sont composées d'un seul élément.</span><span class="sxs-lookup"><span data-stu-id="7c039-125">Normally, JSON requests and responses consist of just one item.</span></span> <span data-ttu-id="7c039-126">Pour l'opération `GetCities` précédente, la demande ressemble à l'instruction suivante.</span><span class="sxs-lookup"><span data-stu-id="7c039-126">For the preceding `GetCities` operation, the request resembles the following statement.</span></span>  
  
```  
"na"  
```  
  
 <span data-ttu-id="7c039-127">La réponse à cette demande ressemble à l'instruction suivante.</span><span class="sxs-lookup"><span data-stu-id="7c039-127">The response to that request resembles the following statement.</span></span>  
  
```  
["Nairobi", "Naples", "Nashville"]  
```  
  
 <span data-ttu-id="7c039-128">Si l'opération utilise un paramètre supplémentaire, le style de demande doit être encapsulé pour encapsuler les deux paramètres dans un seul objet JSON.</span><span class="sxs-lookup"><span data-stu-id="7c039-128">If the operation takes an extra parameter, the request style must be wrapped to wrap both parameters in a single JSON object.</span></span> <span data-ttu-id="7c039-129">L'exemple suivant illustre un message JSON de ce style.</span><span class="sxs-lookup"><span data-stu-id="7c039-129">An example of this style JSON message is in the following example.</span></span>  
  
```json  
{"firstLetters": "na", "maxNumber": 2}  
```  
  
 <span data-ttu-id="7c039-130">Le contrat suivant accepte ce message.</span><span class="sxs-lookup"><span data-stu-id="7c039-130">The following contract accepts this message.</span></span>  
  
```  
[WebInvoke(BodyStyle=WebMessageBodyStyle.WrappedRequest, ResponseFormat=WebMessageFormat.Json)]  
[OperationContract]  
string[] GetCities(string firstLetters, int maxNumber);  
```  
  
## <a name="accessing-ajax-services"></a><span data-ttu-id="7c039-131">Accès aux services AJAX</span><span class="sxs-lookup"><span data-stu-id="7c039-131">Accessing AJAX Services</span></span>  
 <span data-ttu-id="7c039-132">Les points de terminaison AJAX [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] acceptent systématiquement les demandes XML et JSON.</span><span class="sxs-lookup"><span data-stu-id="7c039-132">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] AJAX endpoints always accept both JSON and XML requests.</span></span>  
  
 <span data-ttu-id="7c039-133">Les requêtes HTTP POST avec un type de contenu de « application/json » sont traités en tant que JSON, et ceux dont le type de contenu qui indique XML (par exemple, « texte/xml ») sont traités en tant que XML.</span><span class="sxs-lookup"><span data-stu-id="7c039-133">HTTP POST requests with a content-type of "application/json" are treated as JSON, and those with content-type that indicate XML (for example, "text/xml") are treated as XML.</span></span>  
  
 <span data-ttu-id="7c039-134">Les requêtes HTTP GET contiennent tous les paramètres de requête dans l'URL proprement dite.</span><span class="sxs-lookup"><span data-stu-id="7c039-134">HTTP GET requests contain all the request parameters in the URL itself.</span></span>  
  
 <span data-ttu-id="7c039-135">Il revient à l'utilisateur de choisir comment créer la requête HTTP au point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="7c039-135">It is up to the user to decide how to create the HTTP request to the endpoint.</span></span> <span data-ttu-id="7c039-136">De plus, l'utilisateur dispose d'un contrôle total sur la construction du JSON qui forme le corps de la demande.</span><span class="sxs-lookup"><span data-stu-id="7c039-136">Also, the user has full control over constructing the JSON that forms the body of the request.</span></span> <span data-ttu-id="7c039-137">Pour obtenir un exemple de création d’une demande à partir de JavaScript, consultez le [AJAX Service with JSON et XML](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md).</span><span class="sxs-lookup"><span data-stu-id="7c039-137">For an example of creating a request from JavaScript, see the [AJAX Service with JSON and XML](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md).</span></span>
