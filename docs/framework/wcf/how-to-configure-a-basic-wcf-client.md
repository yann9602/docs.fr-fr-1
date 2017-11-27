---
title: "Comment : configurer un client Windows Communication Foundation de base"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: WCF clients [WCF], configuring
ms.assetid: d067b86d-afb0-47bf-94f6-45180a3d8d78
caps.latest.revision: "47"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1f4d6b5386e82a2052182ba3f4a929de13b27c22
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-configure-a-basic-windows-communication-foundation-client"></a><span data-ttu-id="c27cb-102">Comment : configurer un client Windows Communication Foundation de base</span><span class="sxs-lookup"><span data-stu-id="c27cb-102">How to: Configure a Basic Windows Communication Foundation Client</span></span>
<span data-ttu-id="c27cb-103">Il s'agit de la cinquième des six tâches requises pour créer une application de base [!INCLUDE[indigo1](../../../includes/indigo1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c27cb-103">This is the fifth of six tasks required to create a basic [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] application.</span></span> <span data-ttu-id="c27cb-104">Pour une vue d’ensemble des six tâches, consultez la [Getting Started Tutorial](../../../docs/framework/wcf/getting-started-tutorial.md) rubrique.</span><span class="sxs-lookup"><span data-stu-id="c27cb-104">For an overview of all six of the tasks, see the [Getting Started Tutorial](../../../docs/framework/wcf/getting-started-tutorial.md) topic.</span></span>  
  
 <span data-ttu-id="c27cb-105">Cette rubrique de disuccess le fichier de configuration de client qui a été généré à l’aide de la fonctionnalité Ajouter une référence de Service de [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] ou [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="c27cb-105">This topic disuccess the client configuration file that was generated using the Add Service Reference functionality of [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] or the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="c27cb-106">La configuration du client consiste à spécifier le point de terminaison que le client utilise pour accéder au service.</span><span class="sxs-lookup"><span data-stu-id="c27cb-106">Configuring the client consists of specifying the endpoint that the client uses to access the service.</span></span> <span data-ttu-id="c27cb-107">Un point de terminaison a une adresse, une liaison et un contrat et chacun de ces éléments doit être spécifié dans le processus de configuration du client.</span><span class="sxs-lookup"><span data-stu-id="c27cb-107">An endpoint has an address, a binding and a contract, and each of these must be specified in the process of configuring the client.</span></span>  
  
### <a name="to-configure-a-windows-communication-foundation-client"></a><span data-ttu-id="c27cb-108">Pour configurer un client Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="c27cb-108">To configure a Windows Communication Foundation client</span></span>  
  
1.  <span data-ttu-id="c27cb-109">Ouvrez le fichier de configuration généré (App.config) du projet GettingStartedClient.</span><span class="sxs-lookup"><span data-stu-id="c27cb-109">Open the generated configuration file (App.config) from the GettingStartedClient project.</span></span> <span data-ttu-id="c27cb-110">L'exemple suivant est une vue du fichier de configuration généré.</span><span class="sxs-lookup"><span data-stu-id="c27cb-110">The following example is a view of the generated configuration file.</span></span> <span data-ttu-id="c27cb-111">Sous le [ \<system.serviceModel >](../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) section, recherchez la [ \<point de terminaison >](http://msdn.microsoft.com/en-us/13aa23b7-2f08-4add-8dbf-a99f8127c017) élément.</span><span class="sxs-lookup"><span data-stu-id="c27cb-111">Under the [\<system.serviceModel>](../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) section, find the [\<endpoint>](http://msdn.microsoft.com/en-us/13aa23b7-2f08-4add-8dbf-a99f8127c017) element.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
        <startup>   
          <!-- specifies the version of WCF to use-->  
            <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.5,Profile=Client" />  
        </startup>  
        <system.serviceModel>  
            <bindings>  
                <!-- Uses wsHttpBinding-->  
                <wsHttpBinding>  
                    <binding name="WSHttpBinding_ICalculator" />  
                </wsHttpBinding>  
            </bindings>  
            <client>  
                <!-- specifies the endpoint to use when calling the service -->  
                <endpoint address="http://localhost:8000/ServiceModelSamples/Service/CalculatorService"  
                    binding="wsHttpBinding" bindingConfiguration="WSHttpBinding_ICalculator"  
                    contract="ServiceReference1.ICalculator" name="WSHttpBinding_ICalculator">  
                    <identity>  
                        <userPrincipalName value="migree@redmond.corp.microsoft.com" />  
                    </identity>  
                </endpoint>  
            </client>  
        </system.serviceModel>  
    </configuration>   
    ```  
  
     <span data-ttu-id="c27cb-112">Cet exemple configure le point de terminaison que le client utilise pour accéder au service localisé à l'adresse suivante : http://localhost:8000/ServiceModelSamples/Service/CalculatorService.</span><span class="sxs-lookup"><span data-stu-id="c27cb-112">This example configures the endpoint that the client uses to access the service that is located at the following address: http://localhost:8000/ServiceModelSamples/Service/CalculatorService</span></span>  
  
     <span data-ttu-id="c27cb-113">L'élément de point de terminaison spécifie que le contrat de service `ServiceReference1.ICalculator` est utilisé pour la communication entre le client et le service WCF.</span><span class="sxs-lookup"><span data-stu-id="c27cb-113">The endpoint element specifies that the `ServiceReference1.ICalculator` service contract is used for communication between the WCF client and service.</span></span> <span data-ttu-id="c27cb-114">Le canal WCF est configuré avec fournie par le système <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`>.</span><span class="sxs-lookup"><span data-stu-id="c27cb-114">The WCF channel is configured with the system-provided <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`>.</span></span> <span data-ttu-id="c27cb-115">Ce contrat a été généré à l'aide de la fonctionnalité Ajouter une référence de service dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c27cb-115">This contract was generated by using Add Service Reference in Visual Studio.</span></span> <span data-ttu-id="c27cb-116">Il s'agit essentiellement d'une copie du contrat défini dans le projet GettingStartedLib.</span><span class="sxs-lookup"><span data-stu-id="c27cb-116">It is essentially a copy of the contract that was defined in the GettingStartedLib project.</span></span> <span data-ttu-id="c27cb-117">Le <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> liaison spécifie le protocole HTTP comme transport, la sécurité interopérable et autres détails de configuration.</span><span class="sxs-lookup"><span data-stu-id="c27cb-117">The <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> binding specifies HTTP as the transport, interoperable security, and other configuration details.</span></span>  
  
2.  [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="c27cb-118">comment utiliser le client généré avec cette configuration, consultez [Comment : utiliser un Client](../../../docs/framework/wcf/how-to-use-a-wcf-client.md).</span><span class="sxs-lookup"><span data-stu-id="c27cb-118"> how to use the generated client with this configuration, see [How to: Use a Client](../../../docs/framework/wcf/how-to-use-a-wcf-client.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c27cb-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c27cb-119">See Also</span></span>  
 [<span data-ttu-id="c27cb-120">Utilisation de liaisons pour configurer des services et des clients</span><span class="sxs-lookup"><span data-stu-id="c27cb-120">Using Bindings to Configure Services and Clients</span></span>](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [<span data-ttu-id="c27cb-121">Outil ServiceModel Metadata Utility (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="c27cb-121">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)  
 [<span data-ttu-id="c27cb-122">Guide pratique pour créer un client</span><span class="sxs-lookup"><span data-stu-id="c27cb-122">How to: Create a Client</span></span>](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)  
 [<span data-ttu-id="c27cb-123">Prise en main</span><span class="sxs-lookup"><span data-stu-id="c27cb-123">Getting Started</span></span>](../../../docs/framework/wcf/samples/getting-started-sample.md)  
 [<span data-ttu-id="c27cb-124">L’auto-hébergement</span><span class="sxs-lookup"><span data-stu-id="c27cb-124">Self-Host</span></span>](../../../docs/framework/wcf/samples/self-host.md)
