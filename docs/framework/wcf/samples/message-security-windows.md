---
title: Message Security Windows
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: WS Security
ms.assetid: d2221d1c-c9cb-48d1-b044-a3b4445c7f05
caps.latest.revision: "34"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: c8bb8d0506dd535a312bd8df8954c8143d9543ae
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="message-security-windows"></a><span data-ttu-id="45aac-102">Message Security Windows</span><span class="sxs-lookup"><span data-stu-id="45aac-102">Message Security Windows</span></span>
<span data-ttu-id="45aac-103">Cet exemple illustre comment configurer une liaison <xref:System.ServiceModel.WSHttpBinding> pour permettre l'utilisation de la sécurité de niveau message avec authentification Windows.</span><span class="sxs-lookup"><span data-stu-id="45aac-103">This sample demonstrates how to configure a <xref:System.ServiceModel.WSHttpBinding> binding to use message-level security with Windows authentication.</span></span> <span data-ttu-id="45aac-104">Cet exemple est basé sur le [mise en route](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="45aac-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span> <span data-ttu-id="45aac-105">Dans cet exemple, le service est hébergé dans les services IIS (Internet Information Services) et le client est une application console (.exe).</span><span class="sxs-lookup"><span data-stu-id="45aac-105">In this sample, the service is hosted in Internet Information Services (IIS) and the client is a console application (.exe).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="45aac-106">La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="45aac-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="45aac-107">La sécurité par défaut pour le [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) est la sécurité de message à l’aide de l’authentification Windows.</span><span class="sxs-lookup"><span data-stu-id="45aac-107">The default security for the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) is message security using Windows authentication.</span></span> <span data-ttu-id="45aac-108">Dans cet exemple, les fichiers de configuration définir explicitement la `mode` attribut de la [ \<sécurité >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md) à `Message` et le `clientCredentialType` attribut `Windows`.</span><span class="sxs-lookup"><span data-stu-id="45aac-108">The configuration files in this sample explicitly set the `mode` attribute of the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md) to `Message` and the `clientCredentialType` attribute to `Windows`.</span></span> <span data-ttu-id="45aac-109">Ces valeurs correspondent aux valeurs par défaut de cette liaison. Cependant, elles ont été configurées de manière explicite, ainsi qu’en témoigne l’exemple de configuration suivant, afin d’illustrer leur utilisation.</span><span class="sxs-lookup"><span data-stu-id="45aac-109">These values are the default values for this binding, but they have been explicitly configured, as shown in the following sample configuration to demonstrate their use.</span></span>  
  
```xml  
<bindings>  
    <wsHttpBinding>  
        <binding>  
            <security mode="Message">  
                <message clientCredentialType="Windows"/>  
            </security>  
        </binding>  
    </wsHttpBinding>  
</bindings>  
```  
  
 <span data-ttu-id="45aac-110">La configuration du point de terminaison du client se compose d'une adresse absolue pour le point de terminaison du service, de la liaison et du contrat.</span><span class="sxs-lookup"><span data-stu-id="45aac-110">The client endpoint configuration consists of an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="45aac-111">La liaison du client est configurée avec le `securityMode` et le `authenticationMode` appropriés.</span><span class="sxs-lookup"><span data-stu-id="45aac-111">The client binding is configured with the appropriate `securityMode` and `authenticationMode`.</span></span>  
  
```xml  
<system.serviceModel>  
  <client>  
    <endpoint address=  
            "http://localhost/servicemodelsamples/service.svc"   
            binding="wsHttpBinding"   
            bindingConfiguration="Binding1"   
            contract="Microsoft.ServiceModel.Samples.ICalculator" />  
  </client>  
  
  <bindings>  
    <wsHttpBinding>  
      <!--   
      <!--The default security for the WSHttpBinding is-->  
      <!--Message security using Windows authentication. -->  
      <!--This configuration explicitly defines the security mode -->  
      <!--as Message and the clientCredentialType as Windows  -->  
      <!--for demonstration purposes. -->  
      <binding name="Binding1">  
        <security mode="Message">  
          <message clientCredentialType="Windows"/>  
        </security>  
      </binding>  
    </wsHttpBinding>  
  </bindings>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="45aac-112">Le code source du service a été modifié afin d'illustrer comment le <xref:System.ServiceModel.OperationContext.ServiceSecurityContext%2A> peut être utilisé afin d'accéder à l'identité de l'appelant.</span><span class="sxs-lookup"><span data-stu-id="45aac-112">The service source code has been modified to demonstrate how the <xref:System.ServiceModel.OperationContext.ServiceSecurityContext%2A> can be used to access the identity of the caller.</span></span>  
  
```  
public string GetCallerIdentity()  
{  
    // The Windows identity of the caller can be accessed on the ServiceSecurityContext.WindowsIdentity.  
    return OperationContext.Current.ServiceSecurityContext.WindowsIdentity.Name;  
}  
```  
  
 <span data-ttu-id="45aac-113">Lorsque vous exécutez l'exemple, les demandes et réponses d'opération s'affichent dans la fenêtre de console du client.</span><span class="sxs-lookup"><span data-stu-id="45aac-113">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="45aac-114">La première méthode appelée, `GetCallerIdentity`, retourne le nom de l'identité de l'appelant au client.</span><span class="sxs-lookup"><span data-stu-id="45aac-114">The first method called - `GetCallerIdentity` - returns the name of the caller identity back to the client.</span></span> <span data-ttu-id="45aac-115">Appuyez sur ENTER dans la fenêtre de console pour arrêter le client.</span><span class="sxs-lookup"><span data-stu-id="45aac-115">Press ENTER in the console window to shut down the client.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="45aac-116">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="45aac-116">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="45aac-117">Assurez-vous d’avoir effectué la [procédure d’installation d’à usage unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="45aac-117">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="45aac-118">Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="45aac-118">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="45aac-119">Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [en cours d’exécution les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="45aac-119">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45aac-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="45aac-120">See Also</span></span>
