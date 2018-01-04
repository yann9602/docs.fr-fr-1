---
title: WS Reliable Session
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Reliable session
ms.assetid: 86e914f2-060b-432b-bd17-333695317745
caps.latest.revision: "30"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c07130715b0416e7a8603b46a1c39c2f22dd7d2e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ws-reliable-session"></a><span data-ttu-id="fae2d-102">WS Reliable Session</span><span class="sxs-lookup"><span data-stu-id="fae2d-102">WS Reliable Session</span></span>
<span data-ttu-id="fae2d-103">Cet exemple montre l'utilisation des sessions fiables.</span><span class="sxs-lookup"><span data-stu-id="fae2d-103">This sample demonstrates the use of reliable sessions.</span></span> <span data-ttu-id="fae2d-104">Les sessions fiables fournissent la prise en charge de la messagerie et des sessions fiables.</span><span class="sxs-lookup"><span data-stu-id="fae2d-104">Reliable sessions provide support for reliable messaging and sessions.</span></span> <span data-ttu-id="fae2d-105">La messagerie fiable réessaie d'établir la communication en cas d'échec et permet de spécifier des assurances de remise telles que l'ordre d'arrivée des messages.</span><span class="sxs-lookup"><span data-stu-id="fae2d-105">Reliable messaging retries communication on failure and allows delivery assurances to be specified, such as in-order arrival of messages.</span></span> <span data-ttu-id="fae2d-106">Les sessions conservent l'état pour les clients entre les appels.</span><span class="sxs-lookup"><span data-stu-id="fae2d-106">Sessions maintain state for clients between calls.</span></span> <span data-ttu-id="fae2d-107">Cet exemple implémente des sessions permettant de conserver l'état du client et spécifie des assurances de remise par ordre d'arrivée.</span><span class="sxs-lookup"><span data-stu-id="fae2d-107">The sample implements sessions for maintaining client state and specifies in-order delivery assurances.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="fae2d-108">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="fae2d-108">The samples may already be installed on your machine.</span></span> <span data-ttu-id="fae2d-109">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="fae2d-109">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="fae2d-110">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="fae2d-110">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="fae2d-111">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="fae2d-111">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\wsReliableSession`  
  
 <span data-ttu-id="fae2d-112">Cet exemple est basé sur le [mise en route](../../../../docs/framework/wcf/samples/getting-started-sample.md) qui implémente un service de calculatrice.</span><span class="sxs-lookup"><span data-stu-id="fae2d-112">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="fae2d-113">Les fonctionnalités de sessions fiables sont activées et configurées dans les fichiers de configuration d’application respectifs du client et du service.</span><span class="sxs-lookup"><span data-stu-id="fae2d-113">The reliable session features are enabled and configured in the application configuration files for the client and service.</span></span>  
  
 <span data-ttu-id="fae2d-114">Dans cet exemple, le service est hébergé dans les services IIS (Internet Information Services) et le client est une application console (.exe).</span><span class="sxs-lookup"><span data-stu-id="fae2d-114">In this sample, the service is hosted in Internet Information Services (IIS) and the client is a console application (.exe).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fae2d-115">La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="fae2d-115">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="fae2d-116">L'exemple utilise le fichier `wsHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="fae2d-116">The sample uses the `wsHttpBinding`.</span></span> <span data-ttu-id="fae2d-117">La liaison est spécifiée dans les fichiers de configuration pour le client et le service.</span><span class="sxs-lookup"><span data-stu-id="fae2d-117">The binding is specified in the configuration files for both the client and service.</span></span> <span data-ttu-id="fae2d-118">Le type de liaison est spécifié dans l'attribut `binding` de l'élément de point de terminaison, tel qu'indiqué dans l'exemple de configuration suivant.</span><span class="sxs-lookup"><span data-stu-id="fae2d-118">The binding type is specified in the endpoint element’s `binding` attribute as shown in the following sample configuration.</span></span>  
  
```xml  
<endpoint address=""  
          binding="wsHttpBinding"  
          bindingConfiguration="Binding1"   
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 <span data-ttu-id="fae2d-119">Le point de terminaison contient un attribut `bindingConfiguration` qui référence une configuration de liaison appelée « Binding1 ».</span><span class="sxs-lookup"><span data-stu-id="fae2d-119">The endpoint contains a `bindingConfiguration` attribute that references a binding configuration named "Binding1."</span></span> <span data-ttu-id="fae2d-120">La configuration de liaison active les sessions fiables en définissant le `enabled` attribut de la [ \<reliableSession >](../../../../docs/framework/configure-apps/file-schema/wcf/reliablesession.md) à `true`.</span><span class="sxs-lookup"><span data-stu-id="fae2d-120">The binding configuration enables reliable sessions by setting the `enabled` attribute of the [\<reliableSession>](../../../../docs/framework/configure-apps/file-schema/wcf/reliablesession.md) to `true`.</span></span> <span data-ttu-id="fae2d-121">Les assurances de remise pour les sessions ordonnées sont contrôlées en affectant `true` ou `false` à l'attribut ordonné.</span><span class="sxs-lookup"><span data-stu-id="fae2d-121">Delivery assurances for ordered sessions are controlled by setting the ordered attribute to `true` or `false`.</span></span> <span data-ttu-id="fae2d-122">La valeur par défaut est `true`.</span><span class="sxs-lookup"><span data-stu-id="fae2d-122">The default is `true`.</span></span>  
  
```xml  
<bindings>  
    <wsHttpBinding>  
        <binding name="Binding1">  
            <reliableSession enabled="true" />  
        </binding>  
    </wsHttpBinding>  
</bindings>  
```  
  
 <span data-ttu-id="fae2d-123">La classe d'implémentation de service implémente l'instanciation <xref:System.ServiceModel.InstanceContextMode.PerSession> afin de conserver une instance de classe distincte pour chaque client, tel qu'indiqué dans l'exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="fae2d-123">The service implementation class implements <xref:System.ServiceModel.InstanceContextMode.PerSession> instancing to maintain a separate class instance for each client, as shown in the following sample code.</span></span>  
  
```  
[ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)] public class CalculatorService : ICalculator  
{  
    ...  
}  
```  
  
 <span data-ttu-id="fae2d-124">Lorsque vous exécutez l'exemple, les demandes et réponses d'opération s'affichent dans la fenêtre de console du client.</span><span class="sxs-lookup"><span data-stu-id="fae2d-124">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="fae2d-125">Appuyez sur Entrée dans la fenêtre du client pour l'arrêter.</span><span class="sxs-lookup"><span data-stu-id="fae2d-125">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="fae2d-126">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="fae2d-126">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="fae2d-127">Installez [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 à l'aide de la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="fae2d-127">Install [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 using the following command.</span></span>  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  <span data-ttu-id="fae2d-128">Assurez-vous d’avoir effectué la [procédure d’installation d’à usage unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="fae2d-128">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3.  <span data-ttu-id="fae2d-129">Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="fae2d-129">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="fae2d-130">Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [en cours d’exécution les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="fae2d-130">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fae2d-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fae2d-131">See Also</span></span>
