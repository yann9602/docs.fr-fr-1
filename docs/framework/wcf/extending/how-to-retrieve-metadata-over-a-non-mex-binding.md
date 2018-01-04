---
title: "Procédure : récupérer des métadonnées sur une liaison non-MEX"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2292e124-81b2-4317-b881-ce9c1ec66ecb
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6879694c0c6490de5f591f9aed82075c539fbc1f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-retrieve-metadata-over-a-non-mex-binding"></a><span data-ttu-id="2c99a-102">Procédure : récupérer des métadonnées sur une liaison non-MEX</span><span class="sxs-lookup"><span data-stu-id="2c99a-102">How to: Retrieve Metadata Over a non-MEX Binding</span></span>
<span data-ttu-id="2c99a-103">Cette rubrique décrit comment récupérer les métadonnées d’un point de terminaison MEX sur une liaison non-MEX.</span><span class="sxs-lookup"><span data-stu-id="2c99a-103">This topic describes how to retrieve metadata from a MEX endpoint over a non-MEX binding.</span></span> <span data-ttu-id="2c99a-104">Le code dans cet exemple est basé sur le [personnalisé sécuriser les métadonnées de point de terminaison](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md) exemple.</span><span class="sxs-lookup"><span data-stu-id="2c99a-104">The code in this sample is based on the [Custom Secure Metadata Endpoint](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md) sample.</span></span>  
  
### <a name="to-retrieve-metadata-over-a-non-mex-binding"></a><span data-ttu-id="2c99a-105">Pour récupérer des métadonnées sur une liaison non-MEX</span><span class="sxs-lookup"><span data-stu-id="2c99a-105">To retrieve metadata over a non-MEX binding</span></span>  
  
1.  <span data-ttu-id="2c99a-106">Déterminez la liaison utilisée par le point de terminaison MEX.</span><span class="sxs-lookup"><span data-stu-id="2c99a-106">Determine the binding used by the MEX endpoint.</span></span> <span data-ttu-id="2c99a-107">Concernant les services [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)], vous pouvez déterminer la liaison MEX en accédant au fichier de configuration du service.</span><span class="sxs-lookup"><span data-stu-id="2c99a-107">For [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] services, you can determine the MEX binding by accessing the service's configuration file.</span></span> <span data-ttu-id="2c99a-108">Dans ce cas, la liaison MEX est définie dans la configuration de service suivante :</span><span class="sxs-lookup"><span data-stu-id="2c99a-108">In this case, the MEX binding is defined in the following service configuration.</span></span>  
  
    ```xml  
    <services>  
        <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
                behaviorConfiguration="CalculatorServiceBehavior">  
         <!-- Use the base address provided by the host. -->  
         <endpoint address=""  
           binding="wsHttpBinding"  
           bindingConfiguration="Binding2"  
           contract="Microsoft.ServiceModel.Samples.ICalculator" />  
         <endpoint address="mex"  
           binding="wsHttpBinding"  
           bindingConfiguration="Binding1"  
           contract="IMetadataExchange" />  
         </service>  
     </services>  
     <bindings>  
       <wsHttpBinding>  
         <binding name="Binding1">  
           <security mode="Message">  
             <message clientCredentialType="Certificate" />  
           </security>  
         </binding>  
         <binding name="Binding2">  
           <reliableSession inactivityTimeout="00:01:00" enabled="true" />  
           <security mode="Message">  
             <message clientCredentialType="Certificate" />  
           </security>  
         </binding>  
       </wsHttpBinding>  
     </bindings>  
    ```  
  
2.  <span data-ttu-id="2c99a-109">Dans le fichier de configuration client, configurez la même liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="2c99a-109">In the client configuration file, configure the same custom binding.</span></span> <span data-ttu-id="2c99a-110">Dans ce cas, le client définit également un comportement `clientCredentials` pour fournir un certificat permettant d'authentifier auprès du service lors de la demande des métadonnées provenant du point de terminaison MEX.</span><span class="sxs-lookup"><span data-stu-id="2c99a-110">Here the client also defines a `clientCredentials` behavior to provide a certificate to use to authenticate to the service when requesting metadata from the MEX endpoint.</span></span> <span data-ttu-id="2c99a-111">Lorsque vous utilisez Svcutil.exe pour demander les métadonnées sur une liaison personnalisée, vous devez ajouter la configuration du point de terminaison MEX au fichier de configuration de Svcutil.exe (Svcutil.exe.config), et le nom de la configuration du point de terminaison doit correspondre au schéma d’URI de l’adresse du point de terminaison MEX, comme indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="2c99a-111">When using Svcutil.exe to request metadata over a custom binding, you should add the MEX endpoint configuration to the configuration file for Svcutil.exe (Svcutil.exe.config), and the name of the endpoint configuration should match the URI scheme of the address of the MEX endpoint, as shown in the following code.</span></span>  
  
    ```xml  
    <system.serviceModel>  
      <client>  
        <endpoint name="http"  
                  binding="wsHttpBinding"  
                  bindingConfiguration="Binding1"  
                  behaviorConfiguration="ClientCertificateBehavior"  
                  contract="IMetadataExchange" />  
      </client>  
      <bindings>  
        <wsHttpBinding>  
          <binding name="Binding1">  
            <security mode="Message">  
              <message clientCredentialType="Certificate"/>  
            </security>  
          </binding>  
        </wsHttpBinding>  
      </bindings>  
      <behaviors>  
        <endpointBehaviors>  
          <behavior name="ClientCertificateBehavior">  
            <clientCredentials>  
              <clientCertificate findValue="client.com" storeLocation="CurrentUser" storeName="My" x509FindType="FindBySubjectName" />  
              <serviceCertificate>  
                <authentication certificateValidationMode="PeerOrChainTrust" />  
              </serviceCertificate>  
            </clientCredentials>  
          </behavior>  
        </endpointBehaviors>  
      </behaviors>    
    </system.serviceModel>  
    ```  
  
3.  <span data-ttu-id="2c99a-112">Créez un `MetadataExchangeClient` et appelez `GetMetadata`.</span><span class="sxs-lookup"><span data-stu-id="2c99a-112">Create a `MetadataExchangeClient` and call `GetMetadata`.</span></span> <span data-ttu-id="2c99a-113">Cette opération peut s’effectuer de deux manières différentes : vous pouvez spécifier la liaison personnalisée dans la configuration ou dans le code, comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="2c99a-113">There are two ways to do this: you can specify the custom binding in configuration, or you can specify the custom binding in code, as shown in the following example.</span></span>  
  
    ```  
    // The custom binding is specified in configuration.  
    EndpointAddress mexAddress = new EndpointAddress("http://localhost:8000/ServiceModelSamples/Service/mex");  
  
    MetadataExchangeClient mexClient = new MetadataExchangeClient("http");  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet mexSet = mexClient.GetMetadata(mexAddress);  
  
    // The custom binding is specified in code.  
    // Specify the Metadata Exchange binding and its security mode.  
    WSHttpBinding mexBinding = new WSHttpBinding(SecurityMode.Message);  
    mexBinding.Security.Message.ClientCredentialType = MessageCredentialType.Certificate;  
  
    // Create a MetadataExchangeClient and set the certificate details.  
    MetadataExchangeClient mexClient = new MetadataExchangeClient(mexBinding);  
    mexClient.SoapCredentials.ClientCertificate.SetCertificate(  
        StoreLocation.CurrentUser, StoreName.My,  
        X509FindType.FindBySubjectName, "client.com");  
    mexClient.SoapCredentials.ServiceCertificate.Authentication.  
        CertificateValidationMode =  
        X509CertificateValidationMode.PeerOrChainTrust;  
    mexClient.SoapCredentials.ServiceCertificate.SetDefaultCertificate(  
        StoreLocation.CurrentUser, StoreName.TrustedPeople,  
        X509FindType.FindBySubjectName, "localhost");  
    MetadataExchangeClient mexClient2 = new MetadataExchangeClient(customBinding);  
    mexClient2.ResolveMetadataReferences = true;  
    MetadataSet mexSet2 = mexClient2.GetMetadata(mexAddress);  
    ```  
  
4.  <span data-ttu-id="2c99a-114">Créez un `WsdlImporter`, puis appelez `ImportAllEndpoints`, comme illustré dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="2c99a-114">Create a `WsdlImporter` and call `ImportAllEndpoints`, as shown in the following code.</span></span>  
  
    ```  
    WsdlImporter importer = new WsdlImporter(mexSet);  
    ServiceEndpointCollection endpoints = importer.ImportAllEndpoints();  
    ```  
  
5.  <span data-ttu-id="2c99a-115">À ce stade, vous disposez d’une collection de points de terminaison de service.</span><span class="sxs-lookup"><span data-stu-id="2c99a-115">At this point, you have a collection of service endpoints.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="2c99a-116">l’importation de métadonnées, consultez [Comment : importer les métadonnées dans les points de terminaison de Service](../../../../docs/framework/wcf/feature-details/how-to-import-metadata-into-service-endpoints.md).</span><span class="sxs-lookup"><span data-stu-id="2c99a-116"> importing metadata, see [How to: Import Metadata into Service Endpoints](../../../../docs/framework/wcf/feature-details/how-to-import-metadata-into-service-endpoints.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c99a-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2c99a-117">See Also</span></span>  
 [<span data-ttu-id="2c99a-118">Métadonnées</span><span class="sxs-lookup"><span data-stu-id="2c99a-118">Metadata</span></span>](../../../../docs/framework/wcf/feature-details/metadata.md)
