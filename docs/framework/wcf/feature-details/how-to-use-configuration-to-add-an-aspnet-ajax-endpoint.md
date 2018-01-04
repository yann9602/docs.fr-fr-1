---
title: "Comment : utiliser la configuration pour ajouter un point de terminaison AJAX ASP.NET"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7cd0099e-dc3a-47e4-a38c-6e10f997f6ea
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e1b46239366c38b54a38e3ce62b59c81eeb3316c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-configuration-to-add-an-aspnet-ajax-endpoint"></a><span data-ttu-id="f7453-102">Comment : utiliser la configuration pour ajouter un point de terminaison AJAX ASP.NET</span><span class="sxs-lookup"><span data-stu-id="f7453-102">How to: Use Configuration to Add an ASP.NET AJAX Endpoint</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="f7453-103"> vous permet de créer un service qui rend disponible un point de terminaison compatible ASP.NET AJAX pouvant être appelé à partir de JavaScript sur un site Web client.</span><span class="sxs-lookup"><span data-stu-id="f7453-103"> allows you to create a service that makes an ASP.NET AJAX-enabled endpoint available that can be called from JavaScript on a client Web site.</span></span> <span data-ttu-id="f7453-104">Pour créer ce point de terminaison, vous pouvez utiliser un fichier de configuration, comme pour tous les autres points de terminaison [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)], ou utiliser une méthode qui ne requiert aucun élément de configuration.</span><span class="sxs-lookup"><span data-stu-id="f7453-104">To create such an endpoint, you can either use a configuration file, as with all other [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] endpoints, or use a method that does not require any configuration elements.</span></span> <span data-ttu-id="f7453-105">Cette rubrique décrit l'approche utilisant le fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="f7453-105">This topic demonstrates the configuration approach.</span></span>  
  
 <span data-ttu-id="f7453-106">La partie de la procédure qui permet le service point de terminaison compatible ASP.NET AJAX consiste à configurer le point de terminaison à utiliser le <xref:System.ServiceModel.WebHttpBinding> et ajouter la [ \<enableWebScript >](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) comportement de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="f7453-106">The part of the procedure that enables the service endpoint to become ASP.NET AJAX-enabled consists of configuring the endpoint to use the <xref:System.ServiceModel.WebHttpBinding> and to add the [\<enableWebScript>](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) endpoint behavior.</span></span> <span data-ttu-id="f7453-107">Après avoir configuré le point de terminaison, les étapes pour implémenter et héberger le service sont semblables à celles utilisée pour tout service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f7453-107">After configuring the endpoint, the steps to implement and host the service are similar to those used by any [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span></span> <span data-ttu-id="f7453-108">Pour obtenir un exemple, consultez la [AJAX Service utilisant HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).</span><span class="sxs-lookup"><span data-stu-id="f7453-108">For a working example, see the [AJAX Service Using HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).</span></span>  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="f7453-109">comment configurer un point de terminaison ASP.NET AJAX sans utiliser de configuration, consultez [Comment : ajouter un point de terminaison du AJAX ASP.NET sans Configuration à l’aide de](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="f7453-109"> how to configure an ASP.NET AJAX endpoint without using configuration, see [How to: Add an ASP.NET AJAX Endpoint Without Using Configuration](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).</span></span>  
  
### <a name="to-create-a-basic-wcf-service"></a><span data-ttu-id="f7453-110">Pour créer un service WCF de base</span><span class="sxs-lookup"><span data-stu-id="f7453-110">To create a basic WCF service</span></span>  
  
1.  <span data-ttu-id="f7453-111">Définissez un contrat de service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] de base en utilisant une interface marquée avec l'attribut <xref:System.ServiceModel.ServiceContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="f7453-111">Define a basic [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service contract with an interface marked with the <xref:System.ServiceModel.ServiceContractAttribute> attribute.</span></span> <span data-ttu-id="f7453-112">Marquez chaque opération avec <xref:System.ServiceModel.OperationContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="f7453-112">Mark each operation with the <xref:System.ServiceModel.OperationContractAttribute>.</span></span> <span data-ttu-id="f7453-113">Assurez-vous de définir la propriété <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A>.</span><span class="sxs-lookup"><span data-stu-id="f7453-113">Be sure to set the <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> property.</span></span>  
  
    ```  
    [ServiceContract(Namespace = "MyService")]  
    public interface ICalculator  
    {  
        [OperationContract]  
         // This operation returns the sum of d1 and d2.  
        double Add(double n1, double n2);  
  
        //Other operations omitted…  
  
    }  
    ```  
  
2.  <span data-ttu-id="f7453-114">Implémentez le contrat de service `ICalculator` avec un `CalculatorService`.</span><span class="sxs-lookup"><span data-stu-id="f7453-114">Implement the `ICalculator` service contract with a `CalculatorService`.</span></span>  
  
    ```  
    public class CalculatorService : ICalculator  
    {  
        public double Add(double n1, double n2)  
        {  
            return n1 + n2;  
        }  
  
    //Other operations omitted…  
    ```  
  
3.  <span data-ttu-id="f7453-115">Définissez un espace de noms pour les implémentations `ICalculator` et `CalculatorService` en les encapsulant dans un bloc Namespace.</span><span class="sxs-lookup"><span data-stu-id="f7453-115">Define a namespace for the `ICalculator` and `CalculatorService` implementations by wrapping them in a namespace block.</span></span>  
  
    ```  
    Namespace Microsoft.Ajax.Samples  
    {  
        //Include the code for ICalculator and Caculator here.  
    }  
    ```  
  
### <a name="to-create-an-aspnet-ajax-endpoint-for-the-service"></a><span data-ttu-id="f7453-116">Pour créer un point de terminaison ASP.NET AJAX pour le service</span><span class="sxs-lookup"><span data-stu-id="f7453-116">To create an ASP.NET AJAX endpoint for the service</span></span>  
  
1.  <span data-ttu-id="f7453-117">Créer une configuration de comportement et spécifier le [ \<enableWebScript >](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) comportement des points de terminaison compatible ASP.NET AJAX du service.</span><span class="sxs-lookup"><span data-stu-id="f7453-117">Create a behavior configuration and specify the [\<enableWebScript>](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) behavior for ASP.NET AJAX-enabled endpoints of the service.</span></span>  
  
    ```xml  
    <system.serviceModel>  
        <behaviors>  
            <endpointBehaviors>  
                <behavior name="AspNetAjaxBehavior">  
                    <enableWebScript />  
                </behavior>  
            </endpointBehaviors>  
        </behaviors>  
    </system.serviceModel>  
    ```  
  
2.  <span data-ttu-id="f7453-118">Créez un point de terminaison pour le service qui utilise <xref:System.ServiceModel.WebHttpBinding> et le comportement ASP.NET AJAX défini dans l'étape précédente.</span><span class="sxs-lookup"><span data-stu-id="f7453-118">Create an endpoint for the service that uses the <xref:System.ServiceModel.WebHttpBinding> and the ASP.NET AJAX behavior defined in the previous step.</span></span>  
  
    ```xml  
    <system.serviceModel>  
        <services>  
            <service name="Microsoft.Ajax.Samples.CalculatorService">  
                <endpoint address=""  
                    behaviorConfiguration="AspNetAjaxBehavior"   
                    binding="webHttpBinding"  
                    contract="Microsoft.Ajax.Samples.ICalculator" />  
            </service>  
        </services>  
    </system.serviceModel>   
    ```  
  
### <a name="to-host-the-service-in-iis"></a><span data-ttu-id="f7453-119">Pour héberger le service dans IIS</span><span class="sxs-lookup"><span data-stu-id="f7453-119">To host the service in IIS</span></span>  
  
1.  <span data-ttu-id="f7453-120">Pour héberger le service dans IIS, créez un nouveau fichier nommé "Service" avec une extension .svc dans l’application.</span><span class="sxs-lookup"><span data-stu-id="f7453-120">To host the service in IIS, create a new file named service with a .svc extension in the application.</span></span> <span data-ttu-id="f7453-121">Modifier ce fichier en ajoutant les [ @ServiceHost ](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) informations directives pour le service.</span><span class="sxs-lookup"><span data-stu-id="f7453-121">Edit this file by adding the appropriate [@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive information for the service.</span></span> <span data-ttu-id="f7453-122">Le contenu du fichier Service pour l'exemple `CalculatorService` contient les informations suivantes :</span><span class="sxs-lookup"><span data-stu-id="f7453-122">For example, the content in the service file for the `CalculatorService` sample contains the following information.</span></span>  
  
    ```  
    <%@ServiceHost   
    language=c#   
    Debug="true"   
    Service="Microsoft.Ajax.Samples.CalculatorService"  
    %>  
    ```  
  
2.  [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="f7453-123">hébergement dans IIS, consultez [Comment : héberger un Service WCF dans IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).</span><span class="sxs-lookup"><span data-stu-id="f7453-123"> hosting in IIS, see [How to: Host a WCF Service in IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).</span></span>  
  
### <a name="to-call-the-service"></a><span data-ttu-id="f7453-124">Pour appeler le service</span><span class="sxs-lookup"><span data-stu-id="f7453-124">To call the service</span></span>  
  
1.  <span data-ttu-id="f7453-125">Le point de terminaison est configuré avec une adresse vide renvoyant au fichier .svc, afin que le service est maintenant disponible et peut être appelé en envoyant des demandes à service.svc /\<opération >, par exemple, service.svc/Add pour le `Add` opération.</span><span class="sxs-lookup"><span data-stu-id="f7453-125">The endpoint is configured at an empty address relative to the .svc file, so the service is now available and can be invoked by sending requests to service.svc/\<operation> - for example, service.svc/Add for the `Add` operation.</span></span> <span data-ttu-id="f7453-126">Vous pouvez l’utiliser en entrant le point l’URL du point de terminaison dans la collection Scripts du contrôle Script Manager ASP.NET AJAX .</span><span class="sxs-lookup"><span data-stu-id="f7453-126">You can use it by entering the endpoint URL into the Scripts collection of the ASP.NET AJAX Script Manager control.</span></span> <span data-ttu-id="f7453-127">Pour obtenir un exemple, consultez la [AJAX Service utilisant HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).</span><span class="sxs-lookup"><span data-stu-id="f7453-127">For an example, see the [AJAX Service Using HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7453-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f7453-128">See Also</span></span>  
 [<span data-ttu-id="f7453-129">Création de services WCF pour ASP.NET AJAX</span><span class="sxs-lookup"><span data-stu-id="f7453-129">Creating WCF Services for ASP.NET AJAX</span></span>](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)  
 [<span data-ttu-id="f7453-130">Guide pratique pour migrer des services web ASP.NET compatibles AJAX vers WCF</span><span class="sxs-lookup"><span data-stu-id="f7453-130">How to: Migrate AJAX-Enabled ASP.NET Web Services to WCF</span></span>](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
