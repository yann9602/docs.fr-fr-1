---
title: "Comment : ajouter un point de terminaison AJAX ASP.NET sans utiliser de configuration"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b05c1742-8d0a-4673-9d71-725b18a3008e
caps.latest.revision: "14"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e71e8f8f9b4c6f2a407febc8ba8ac045ecc0e239
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-add-an-aspnet-ajax-endpoint-without-using-configuration"></a><span data-ttu-id="0a59a-102">Comment : ajouter un point de terminaison AJAX ASP.NET sans utiliser de configuration</span><span class="sxs-lookup"><span data-stu-id="0a59a-102">How to: Add an ASP.NET AJAX Endpoint Without Using Configuration</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="0a59a-103"> vous permet de créer un service qui expose un point de terminaison activé ASP.NET AJAX pouvant être appelé à partir de JavaScript sur un site Web client.</span><span class="sxs-lookup"><span data-stu-id="0a59a-103"> allows you to create a service that exposes an ASP.NET AJAX-enabled endpoint that can be called from JavaScript on a client Web site.</span></span> <span data-ttu-id="0a59a-104">Pour créer ce point de terminaison, vous pouvez utiliser un fichier de configuration, comme pour tous les autres points de terminaison WCF, ou utiliser une méthode qui ne requiert aucun élément de configuration.</span><span class="sxs-lookup"><span data-stu-id="0a59a-104">To create such an endpoint, you can either use a configuration file, as with all other WCF endpoints, or use a method that does not require any configuration elements.</span></span> <span data-ttu-id="0a59a-105">Cette rubrique décrit la deuxième approche.</span><span class="sxs-lookup"><span data-stu-id="0a59a-105">This topic demonstrates the second approach.</span></span>  
  
 <span data-ttu-id="0a59a-106">Pour créer des services avec les points de terminaison ASP.NET AJAX sans configuration, les services doivent être hébergés par les services IIS (Internet Information Services).</span><span class="sxs-lookup"><span data-stu-id="0a59a-106">To create services with ASP.NET AJAX endpoints without configuration, the services must be hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="0a59a-107">Pour activer un point de terminaison ASP.NET AJAX à l’aide de cette approche, vous devez spécifier le <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> comme paramètre fabrique dans la [ @ServiceHost ](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive dans le fichier .svc.</span><span class="sxs-lookup"><span data-stu-id="0a59a-107">To activate an ASP.NET AJAX endpoint using this approach, specify the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> as the Factory parameter in the [@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive in the .svc file.</span></span> <span data-ttu-id="0a59a-108">Cette fabrication personnalisée est le composant qui configure automatiquement un point de terminaison ASP.NET AJAX afin qu’il puisse être appelé à partir de JavaScript sur un site web client.</span><span class="sxs-lookup"><span data-stu-id="0a59a-108">This custom factory is the component that automatically configures an ASP.NET AJAX endpoint so that it can be called from JavaScript on a client Web site.</span></span>  
  
 <span data-ttu-id="0a59a-109">Pour obtenir un exemple, consultez la [AJAX Service sans Configuration](../../../../docs/framework/wcf/samples/ajax-service-without-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="0a59a-109">For a working example, see the [AJAX Service Without Configuration](../../../../docs/framework/wcf/samples/ajax-service-without-configuration.md).</span></span>  
  
 <span data-ttu-id="0a59a-110">Pour obtenir une description de la configuration d’un point de terminaison ASP.NET AJAX à l’aide des éléments de configuration, consultez [Comment : utiliser la Configuration pour ajouter un point de terminaison ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md).</span><span class="sxs-lookup"><span data-stu-id="0a59a-110">For an outline of how to configure an ASP.NET AJAX endpoint using configuration elements, see [How to: Use Configuration to Add an ASP.NET AJAX Endpoint](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md).</span></span>  
  
### <a name="to-create-a-basic-wcf-service"></a><span data-ttu-id="0a59a-111">Pour créer un service WCF de base</span><span class="sxs-lookup"><span data-stu-id="0a59a-111">To create a basic WCF service</span></span>  
  
1.  <span data-ttu-id="0a59a-112">Définissez un contrat de service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] de base en utilisant une interface marquée avec l'attribut <xref:System.ServiceModel.ServiceContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="0a59a-112">Define a basic [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service contract with an interface marked with the <xref:System.ServiceModel.ServiceContractAttribute> attribute.</span></span> <span data-ttu-id="0a59a-113">Marquez chaque opération avec <xref:System.ServiceModel.OperationContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="0a59a-113">Mark each operation with the <xref:System.ServiceModel.OperationContractAttribute>.</span></span> <span data-ttu-id="0a59a-114">Assurez-vous de définir la propriété <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A>.</span><span class="sxs-lookup"><span data-stu-id="0a59a-114">Be sure to set the <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> property.</span></span>  
  
    ```csharp  
    [ServiceContract(Namespace = "MyService")]]  
    public interface ICalculator  
    {  
        [OperationContract]  
        // This operation returns the sum of d1 and d2.  
        double Add(double n1, double n2);  
  
        //Other operations omitted…  
  
    }  
    ```  
  
2.  <span data-ttu-id="0a59a-115">Implémentez le contrat de service `ICalculator` avec un `CalculatorService`.</span><span class="sxs-lookup"><span data-stu-id="0a59a-115">Implement the `ICalculator` service contract with a `CalculatorService`.</span></span>  
  
    ```csharp  
    public class CalculatorService : ICalculator  
    {  
        public double Add(double n1, double n2)  
        {  
            return n1 + n2;  
        }  
  
    //Other operations omitted…  
    ```  
  
3.  <span data-ttu-id="0a59a-116">Définissez un espace de noms pour les implémentations `ICalculator` et `CalculatorService` en les encapsulant dans un bloc Namespace.</span><span class="sxs-lookup"><span data-stu-id="0a59a-116">Define a namespace for the `ICalculator` and `CalculatorService` implementations by wrapping them in a namespace block.</span></span>  
  
    ```csharp  
    Namespace Microsoft.Ajax.Samples  
    {  
        //Include the code for ICalculator and Caculator here.  
    }  
    ```  
  
### <a name="to-host-the-service-in-internet-information-services-without-configuration"></a><span data-ttu-id="0a59a-117">Pour héberger le service dans les services IIS sans configuration</span><span class="sxs-lookup"><span data-stu-id="0a59a-117">To host the service in Internet Information Services without configuration</span></span>  
  
1.  <span data-ttu-id="0a59a-118">Créez un nouveau fichier pour le service avec une extension .svc dans l’application.</span><span class="sxs-lookup"><span data-stu-id="0a59a-118">Create a new file named service with a .svc extension in the application.</span></span> <span data-ttu-id="0a59a-119">Modifier ce fichier en ajoutant les [ @ServiceHost ](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) informations directives pour le service.</span><span class="sxs-lookup"><span data-stu-id="0a59a-119">Edit this file by adding the appropriate [@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive information for the service.</span></span> <span data-ttu-id="0a59a-120">Spécifier que le <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> doit être utilisé dans le [ @ServiceHost ](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) la directive pour configurer automatiquement un point de terminaison ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="0a59a-120">Specify that the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> is to be used in the [@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive to automatically configure an ASP.NET AJAX endpoint.</span></span>  
  
    ```  
    <%@ServiceHost   
        language=c#   
        Debug="true"   
        Service="Microsoft.Ajax.Samples.CalculatorService"  
        Factory=System.ServiceModel.Activation.WebScriptServiceHostFactory  
    %>  
    ```  
  
2.  <span data-ttu-id="0a59a-121">Générez le service et appelez-le à partir du client.</span><span class="sxs-lookup"><span data-stu-id="0a59a-121">Build the service and call it from the client.</span></span> <span data-ttu-id="0a59a-122">Les services IIS (Internet Information Services) activent le service lorsqu'il est appelé.</span><span class="sxs-lookup"><span data-stu-id="0a59a-122">Internet Information Services (IIS) activates the service when called.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="0a59a-123">hébergement dans IIS, consultez [Comment : héberger un Service WCF dans IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).</span><span class="sxs-lookup"><span data-stu-id="0a59a-123"> hosting in IIS, see [How to: Host a WCF Service in IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).</span></span>  
  
### <a name="to-call-the-service"></a><span data-ttu-id="0a59a-124">Pour appeler le service</span><span class="sxs-lookup"><span data-stu-id="0a59a-124">To call the service</span></span>  
  
1.  <span data-ttu-id="0a59a-125">Le point de terminaison est configuré avec une adresse vide renvoyant au fichier .svc, afin que le service est maintenant disponible et peut être appelé en envoyant des demandes à service.svc /\<opération >, par exemple, service.svc/Add pour le `Add` opération.</span><span class="sxs-lookup"><span data-stu-id="0a59a-125">The endpoint is configured at an empty address relative to the .svc file, so the service is now available and can be invoked by sending requests to service.svc/\<operation> - for example, service.svc/Add for the `Add` operation.</span></span> <span data-ttu-id="0a59a-126">Vous pouvez l’utiliser en entrant l’URL du service dans la collection Scripts du contrôle Script Manager ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="0a59a-126">You can use it by entering the service URL into the Scripts collection of the ASP.NET AJAX Script Manager control.</span></span> <span data-ttu-id="0a59a-127">Pour obtenir un exemple, consultez la [AJAX Service sans Configuration](../../../../docs/framework/wcf/samples/ajax-service-without-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="0a59a-127">For an example, see the [AJAX Service Without Configuration](../../../../docs/framework/wcf/samples/ajax-service-without-configuration.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0a59a-128">Exemple</span><span class="sxs-lookup"><span data-stu-id="0a59a-128">Example</span></span>  
  
 <span data-ttu-id="0a59a-129">Le point de terminaison configuré automatiquement est créé au niveau d'une adresse vide qui est fonction de l'URL de base.</span><span class="sxs-lookup"><span data-stu-id="0a59a-129">The automatically-configured endpoint is created at an empty address relative to the base URL.</span></span> <span data-ttu-id="0a59a-130">Un fichier de configuration peut également être ajouté et utilisé avec cette approche.</span><span class="sxs-lookup"><span data-stu-id="0a59a-130">A configuration file can also be added and used with this approach.</span></span> <span data-ttu-id="0a59a-131">Si le fichier de configuration contient des définitions de point de terminaison, ces points de terminaison sont ajoutés au point de terminaison configuré automatiquement.</span><span class="sxs-lookup"><span data-stu-id="0a59a-131">If the configuration file contains endpoint definitions, these endpoints are added to the automatically-configured endpoint.</span></span>  
  
 <span data-ttu-id="0a59a-132">Par exemple, service.svc utilise <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> et le répertoire du service contient un fichier Web.config qui définit un point de terminaison pour le même service en utilisant <xref:System.ServiceModel.BasicHttpBinding> au niveau de l'adresse relative « soap ».</span><span class="sxs-lookup"><span data-stu-id="0a59a-132">For example, service.svc uses the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> and the service directory contains a Web.config file that defines an endpoint for the same service using the <xref:System.ServiceModel.BasicHttpBinding> at the "soap" relative address.</span></span> <span data-ttu-id="0a59a-133">Dans ce cas, le service contient deux points de terminaison : un au niveau de service.svc (qui répond aux demandes ASP.NET AJAX) et un autre au niveau de service.svc/soap (qui répond aux demandes SOAP).</span><span class="sxs-lookup"><span data-stu-id="0a59a-133">In this case, the service contains two endpoints: one at service.svc (which responds to ASP.NET AJAX requests) and another at service.svc/soap (which responds to SOAP requests).</span></span>  
  
 <span data-ttu-id="0a59a-134">Si le fichier de configuration définit un point de terminaison au niveau d'une adresse relative vide et <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> est utilisé, une exception est levée et le service ne peut pas démarrer.</span><span class="sxs-lookup"><span data-stu-id="0a59a-134">If the configuration file defines an endpoint at an empty relative address and the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> is used, an exception is thrown and the service fails to start.</span></span>  
  
 <span data-ttu-id="0a59a-135">Vous ne pouvez pas utiliser de configuration pour modifier des paramètres sur le point de terminaison configuré automatiquement.</span><span class="sxs-lookup"><span data-stu-id="0a59a-135">You cannot use configuration to modify settings on the automatically-configured endpoint.</span></span> <span data-ttu-id="0a59a-136">Si un paramètre (tel qu'un quota de lecteur) doit être modifié, vous ne devez pas utiliser l'approche sans configuration en supprimant <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> dans le fichier .svc et en créant une entrée de configuration pour le point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="0a59a-136">If any setting (such as a reader quota) must be modified, you must not use the configuration-free approach by removing the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> from the .svc file and creating a configuration entry for the endpoint.</span></span>  
  
 <span data-ttu-id="0a59a-137">Si votre service requiert le mode de compatibilité ASP.NET, par exemple, s'il utilise la classe <xref:System.Web.HttpContext> ou les mécanismes d'autorisation ASP.NET, un fichier de configuration est néanmoins requis pour activer ce mode.</span><span class="sxs-lookup"><span data-stu-id="0a59a-137">If your service requires ASP.NET Compatibility Mode - for example, if it uses the <xref:System.Web.HttpContext> class or ASP.NET authorization mechanisms - a configuration file is still required to turn on this mode.</span></span> <span data-ttu-id="0a59a-138">L’élément de configuration requise est la [ \<serviceHostingEnvironment >](../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md) élément, qui doit être ajouté comme suit.</span><span class="sxs-lookup"><span data-stu-id="0a59a-138">The configuration element required is the [\<serviceHostingEnvironment>](../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md) element, which must be added as follows.</span></span>  
  
 `<system.serviceModel>`  
  
 `<serviceHostingEnvironment aspNetCompatibilityEnabled="true" /> </system.serviceModel>`  
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="0a59a-139">le [Services WCF et ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md) rubrique.</span><span class="sxs-lookup"><span data-stu-id="0a59a-139"> the [WCF Services and ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md) topic.</span></span>  
  
 <span data-ttu-id="0a59a-140">La classe <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> est dérivée de la classe <xref:System.ServiceModel.Activation.ServiceHostFactory>.</span><span class="sxs-lookup"><span data-stu-id="0a59a-140">The <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> class is a derived class of <xref:System.ServiceModel.Activation.ServiceHostFactory>.</span></span> <span data-ttu-id="0a59a-141">Pour obtenir une explication détaillée de la méthode de fabrique hôte service, consultez le [extension de ServiceHostFactory à l’aide d’hébergement](../../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md) rubrique.</span><span class="sxs-lookup"><span data-stu-id="0a59a-141">For a detailed explanation of the service host factory mechanism, see the [Extending Hosting Using ServiceHostFactory](../../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md) topic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a59a-142">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0a59a-142">See Also</span></span>  
 [<span data-ttu-id="0a59a-143">Création de Services WCF pour ASP.NET AJAX</span><span class="sxs-lookup"><span data-stu-id="0a59a-143">Creating WCF Services for ASP.NET AJAX</span></span>](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)  
 [<span data-ttu-id="0a59a-144">Comment : migrer les Services Web ASP.NET compatible AJAX vers WCF</span><span class="sxs-lookup"><span data-stu-id="0a59a-144">How to: Migrate AJAX-Enabled ASP.NET Web Services to WCF</span></span>](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
