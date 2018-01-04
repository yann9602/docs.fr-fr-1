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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 377a67edb37ada5c9e1b022d50a4718b5740afd8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-configure-a-basic-windows-communication-foundation-client"></a><span data-ttu-id="58039-102">Comment : configurer un client Windows Communication Foundation de base</span><span class="sxs-lookup"><span data-stu-id="58039-102">How to: Configure a Basic Windows Communication Foundation Client</span></span>
<span data-ttu-id="58039-103">Il s'agit de la cinquième des six tâches requises pour créer une application de base [!INCLUDE[indigo1](../../../includes/indigo1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="58039-103">This is the fifth of six tasks required to create a basic [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] application.</span></span> <span data-ttu-id="58039-104">Pour une vue d’ensemble des six tâches, consultez la [Getting Started Tutorial](../../../docs/framework/wcf/getting-started-tutorial.md) rubrique.</span><span class="sxs-lookup"><span data-stu-id="58039-104">For an overview of all six of the tasks, see the [Getting Started Tutorial](../../../docs/framework/wcf/getting-started-tutorial.md) topic.</span></span>  
  
 <span data-ttu-id="58039-105">Cette rubrique de disuccess le fichier de configuration de client qui a été généré à l’aide de la fonctionnalité Ajouter une référence de Service de [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] ou [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="58039-105">This topic disuccess the client configuration file that was generated using the Add Service Reference functionality of [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] or the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="58039-106">La configuration du client consiste à spécifier le point de terminaison que le client utilise pour accéder au service.</span><span class="sxs-lookup"><span data-stu-id="58039-106">Configuring the client consists of specifying the endpoint that the client uses to access the service.</span></span> <span data-ttu-id="58039-107">Un point de terminaison a une adresse, une liaison et un contrat et chacun de ces éléments doit être spécifié dans le processus de configuration du client.</span><span class="sxs-lookup"><span data-stu-id="58039-107">An endpoint has an address, a binding and a contract, and each of these must be specified in the process of configuring the client.</span></span>  
  
### <a name="to-configure-a-windows-communication-foundation-client"></a><span data-ttu-id="58039-108">Pour configurer un client Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="58039-108">To configure a Windows Communication Foundation client</span></span>  
  
1.  <span data-ttu-id="58039-109">Ouvrez le fichier de configuration généré (App.config) du projet GettingStartedClient.</span><span class="sxs-lookup"><span data-stu-id="58039-109">Open the generated configuration file (App.config) from the GettingStartedClient project.</span></span> <span data-ttu-id="58039-110">L'exemple suivant est une vue du fichier de configuration généré.</span><span class="sxs-lookup"><span data-stu-id="58039-110">The following example is a view of the generated configuration file.</span></span> <span data-ttu-id="58039-111">Sous le [ \<system.serviceModel >](../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) section, recherchez la [ \<point de terminaison >](http://msdn.microsoft.com/en-us/13aa23b7-2f08-4add-8dbf-a99f8127c017) élément.</span><span class="sxs-lookup"><span data-stu-id="58039-111">Under the [\<system.serviceModel>](../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) section, find the [\<endpoint>](http://msdn.microsoft.com/en-us/13aa23b7-2f08-4add-8dbf-a99f8127c017) element.</span></span>  
  
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
  
     <span data-ttu-id="58039-112">Cet exemple configure le point de terminaison que le client utilise pour accéder au service localisé à l'adresse suivante : http://localhost:8000/ServiceModelSamples/Service/CalculatorService.</span><span class="sxs-lookup"><span data-stu-id="58039-112">This example configures the endpoint that the client uses to access the service that is located at the following address: http://localhost:8000/ServiceModelSamples/Service/CalculatorService</span></span>  
  
     <span data-ttu-id="58039-113">L'élément de point de terminaison spécifie que le contrat de service `ServiceReference1.ICalculator` est utilisé pour la communication entre le client et le service WCF.</span><span class="sxs-lookup"><span data-stu-id="58039-113">The endpoint element specifies that the `ServiceReference1.ICalculator` service contract is used for communication between the WCF client and service.</span></span> <span data-ttu-id="58039-114">Le canal WCF est configuré avec fournie par le système <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`>.</span><span class="sxs-lookup"><span data-stu-id="58039-114">The WCF channel is configured with the system-provided <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`>.</span></span> <span data-ttu-id="58039-115">Ce contrat a été généré à l'aide de la fonctionnalité Ajouter une référence de service dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="58039-115">This contract was generated by using Add Service Reference in Visual Studio.</span></span> <span data-ttu-id="58039-116">Il s'agit essentiellement d'une copie du contrat défini dans le projet GettingStartedLib.</span><span class="sxs-lookup"><span data-stu-id="58039-116">It is essentially a copy of the contract that was defined in the GettingStartedLib project.</span></span> <span data-ttu-id="58039-117">Le <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> liaison spécifie le protocole HTTP comme transport, la sécurité interopérable et autres détails de configuration.</span><span class="sxs-lookup"><span data-stu-id="58039-117">The <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> binding specifies HTTP as the transport, interoperable security, and other configuration details.</span></span>  
  
2.  [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="58039-118">comment utiliser le client généré avec cette configuration, consultez [Comment : utiliser un Client](../../../docs/framework/wcf/how-to-use-a-wcf-client.md).</span><span class="sxs-lookup"><span data-stu-id="58039-118"> how to use the generated client with this configuration, see [How to: Use a Client](../../../docs/framework/wcf/how-to-use-a-wcf-client.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58039-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="58039-119">See Also</span></span>  
 [<span data-ttu-id="58039-120">Utilisation de liaisons pour configurer des services et des clients</span><span class="sxs-lookup"><span data-stu-id="58039-120">Using Bindings to Configure Services and Clients</span></span>](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [<span data-ttu-id="58039-121">Outil ServiceModel Metadata Utility (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="58039-121">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)  
 [<span data-ttu-id="58039-122">Guide pratique pour créer un client</span><span class="sxs-lookup"><span data-stu-id="58039-122">How to: Create a Client</span></span>](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)  
 [<span data-ttu-id="58039-123">Prise en main</span><span class="sxs-lookup"><span data-stu-id="58039-123">Getting Started</span></span>](../../../docs/framework/wcf/samples/getting-started-sample.md)  
 [<span data-ttu-id="58039-124">Auto-hébergement</span><span class="sxs-lookup"><span data-stu-id="58039-124">Self-Host</span></span>](../../../docs/framework/wcf/samples/self-host.md)
