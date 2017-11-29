---
title: Default Service Behavior
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- service behaviors, defaults
- Default Service Behavior Sample [Windows Communication Foundation]
ms.assetid: 442d4f71-c64e-4c62-816a-a66c38e7d3ec
caps.latest.revision: "28"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d584bbe3092524397639e5db8da6632deea8a752
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="default-service-behavior"></a><span data-ttu-id="a18e0-102">Default Service Behavior</span><span class="sxs-lookup"><span data-stu-id="a18e0-102">Default Service Behavior</span></span>
<span data-ttu-id="a18e0-103">Cet exemple montre comment les paramètres de comportement du service peuvent être configurés.</span><span class="sxs-lookup"><span data-stu-id="a18e0-103">This sample demonstrates how service behavior settings can be configured.</span></span> <span data-ttu-id="a18e0-104">L’exemple est basé sur le [mise en route](../../../../docs/framework/wcf/samples/getting-started-sample.md), qui implémente le `ICalculator` contrat de service.</span><span class="sxs-lookup"><span data-stu-id="a18e0-104">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), which implements the `ICalculator` service contract.</span></span> <span data-ttu-id="a18e0-105">Cet exemple définit explicitement des comportements de service et des comportements d'opération à l'aide des attributs <xref:System.ServiceModel.ServiceBehaviorAttribute> et <xref:System.ServiceModel.OperationBehaviorAttribute>.</span><span class="sxs-lookup"><span data-stu-id="a18e0-105">This sample explicitly defines service behaviors and operation behaviors using the <xref:System.ServiceModel.ServiceBehaviorAttribute> and <xref:System.ServiceModel.OperationBehaviorAttribute> attributes.</span></span> <span data-ttu-id="a18e0-106">Vous pouvez configurer les comportements dans les fichiers de configuration ou impérativement dans le code (comme le montre cet exemple).</span><span class="sxs-lookup"><span data-stu-id="a18e0-106">You can configure behaviors in configuration files or imperatively in code (as this sample demonstrates).</span></span>  
  
 <span data-ttu-id="a18e0-107">Dans cet exemple, le client est une application console (.exe) et le service est hébergé par les services IIS (Internet Information Services).</span><span class="sxs-lookup"><span data-stu-id="a18e0-107">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a18e0-108">La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="a18e0-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="a18e0-109">La classe de service spécifie des comportements avec l'<xref:System.ServiceModel.ServiceBehaviorAttribute> et l'<xref:System.ServiceModel.OperationBehaviorAttribute> comme le montre l'exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="a18e0-109">The service class specifies behaviors with the <xref:System.ServiceModel.ServiceBehaviorAttribute> and the <xref:System.ServiceModel.OperationBehaviorAttribute> as shown in the following code sample.</span></span> <span data-ttu-id="a18e0-110">Toutes les valeurs spécifiées sont les valeurs par défaut.</span><span class="sxs-lookup"><span data-stu-id="a18e0-110">All values specified are the defaults.</span></span>  
  
```  
[ServiceBehavior(  
    AutomaticSessionShutdown=true,  
    ConcurrencyMode=ConcurrencyMode.Single,  
    InstanceContextMode=InstanceContextMode.PerSession,  
    IncludeExceptionDetailInFaults=false,  
    UseSynchronizationContext=true,  
    ValidateMustUnderstand=true)]  
public class CalculatorService : ICalculator  
{  
    [OperationBehavior(  
        TransactionAutoComplete=true,  
        TransactionScopeRequired=false,  
        Impersonation=ImpersonationOption.NotAllowed)]  
    public double Add(double n1, double n2)  
    {  
        System.Threading.Thread.Sleep(1600);  
        return n1 + n2;  
    }  
    ...  
}  
```  
  
 <span data-ttu-id="a18e0-111">Les comportements de service sont spécifiés avec l'attribut <xref:System.ServiceModel.ServiceBehaviorAttribute>.</span><span class="sxs-lookup"><span data-stu-id="a18e0-111">Service behaviors are specified with the <xref:System.ServiceModel.ServiceBehaviorAttribute> attribute.</span></span> <span data-ttu-id="a18e0-112">Le tableau suivant décrit quelques-uns de ces comportements.</span><span class="sxs-lookup"><span data-stu-id="a18e0-112">The following table describes some of these behaviors.</span></span>  
  
|<span data-ttu-id="a18e0-113">Comportement de service</span><span class="sxs-lookup"><span data-stu-id="a18e0-113">Service behavior</span></span>|<span data-ttu-id="a18e0-114">Description</span><span class="sxs-lookup"><span data-stu-id="a18e0-114">Description</span></span>|  
|----------------------|-----------------|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.AutomaticSessionShutdown%2A>|<span data-ttu-id="a18e0-115">Ferme automatiquement une session à la demande du client.</span><span class="sxs-lookup"><span data-stu-id="a18e0-115">Automatically shuts down a session at the client's request.</span></span>|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A>|<span data-ttu-id="a18e0-116">Spécifie le mode d'accès concurrentiel pour chaque instance de service.</span><span class="sxs-lookup"><span data-stu-id="a18e0-116">Specifies the concurrency mode for each service instance.</span></span>|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A>|<span data-ttu-id="a18e0-117">Spécifie le mode de contexte d'instance.</span><span class="sxs-lookup"><span data-stu-id="a18e0-117">Specifies the instance context mode.</span></span>|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.UseSynchronizationContext%2A>|<span data-ttu-id="a18e0-118">Détermine s’il faut utiliser le contexte de synchronisation fourni, s’il est défini.</span><span class="sxs-lookup"><span data-stu-id="a18e0-118">Determines whether to use the provided synchronization context, if one is set.</span></span> <span data-ttu-id="a18e0-119">Utilisez-le pour contrôler s'il faut utiliser un `WindowsFormsSynchronizationContext` dans les applications Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="a18e0-119">Use this when you want to control whether to use a `WindowsFormsSynchronizationContext` in Windows Forms applications.</span></span>|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A>|<span data-ttu-id="a18e0-120">Détermine si les exceptions d'exécution non prise en charge générales doivent être converties en `Fault<string>` et envoyées comme un message d'erreur.</span><span class="sxs-lookup"><span data-stu-id="a18e0-120">Determines whether general unhandled execution exceptions are to be converted into a `Fault<string>` and sent as a fault message.</span></span>|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A>|<span data-ttu-id="a18e0-121">Spécifie le niveau d’isolation des transactions.</span><span class="sxs-lookup"><span data-stu-id="a18e0-121">Specifies the isolation level for transactions.</span></span>|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.ValidateMustUnderstand%2A>|<span data-ttu-id="a18e0-122">Détermine si les en-têtes de message inattendus provoquent une condition d'erreur.</span><span class="sxs-lookup"><span data-stu-id="a18e0-122">Determines whether unexpected message headers cause an error condition.</span></span>|  
  
 <span data-ttu-id="a18e0-123">Les comportements d'opération sont spécifiés à l'aide de l'attribut <xref:System.ServiceModel.OperationBehaviorAttribute>.</span><span class="sxs-lookup"><span data-stu-id="a18e0-123">Operation behaviors are specified by using the <xref:System.ServiceModel.OperationBehaviorAttribute> attribute.</span></span> <span data-ttu-id="a18e0-124">Le tableau suivant décrit quelques-uns de ces comportements.</span><span class="sxs-lookup"><span data-stu-id="a18e0-124">The following table describes some of these behaviors.</span></span>  
  
|<span data-ttu-id="a18e0-125">Comportement d'opération</span><span class="sxs-lookup"><span data-stu-id="a18e0-125">Operation Behavior</span></span>|<span data-ttu-id="a18e0-126">Description</span><span class="sxs-lookup"><span data-stu-id="a18e0-126">Description</span></span>|  
|------------------------|-----------------|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A>|<span data-ttu-id="a18e0-127">Détermine si l’achèvement de l’opération de service valide la transaction en cours.</span><span class="sxs-lookup"><span data-stu-id="a18e0-127">Determines whether service operation completion commits the current transaction.</span></span>|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A>|<span data-ttu-id="a18e0-128">Détermine si l’opération de service s’inscrit dans une transaction transmise par le client.</span><span class="sxs-lookup"><span data-stu-id="a18e0-128">Determines whether the service operation enlists in a client-flowed transaction.</span></span>|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A>|<span data-ttu-id="a18e0-129">Détermine si l'opération de service emprunte l'identité de l'appelant.</span><span class="sxs-lookup"><span data-stu-id="a18e0-129">Determines whether the service operation impersonates the caller's identity.</span></span>|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.ReleaseInstanceMode%2A>|<span data-ttu-id="a18e0-130">Détermine si les instances de service sont recyclées au début ou à la fin de l'appel de l'opération de service.</span><span class="sxs-lookup"><span data-stu-id="a18e0-130">Determines whether service instances are recycled at the start or end of the service operation call.</span></span>|  
  
 <span data-ttu-id="a18e0-131">Lorsque vous exécutez l'exemple, les demandes et réponses d'opération s'affichent dans la fenêtre de console du client.</span><span class="sxs-lookup"><span data-stu-id="a18e0-131">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="a18e0-132">Le délai entre les appels est le résultat des appels passés à `System.Threading.Thread.Sleep()` dans les opérations de service.</span><span class="sxs-lookup"><span data-stu-id="a18e0-132">The delay between the calls is the result of the calls to `System.Threading.Thread.Sleep()` made in the service operations.</span></span> <span data-ttu-id="a18e0-133">Le reste des exemples de comportements explique ces comportements de manière plus détaillée.</span><span class="sxs-lookup"><span data-stu-id="a18e0-133">The rest of the behavior samples explain these behaviors in more detail.</span></span> <span data-ttu-id="a18e0-134">Appuyez sur Entrée dans la fenêtre du client pour l'arrêter.</span><span class="sxs-lookup"><span data-stu-id="a18e0-134">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="a18e0-135">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="a18e0-135">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="a18e0-136">Assurez-vous d’avoir effectué la [procédure d’installation d’à usage unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a18e0-136">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="a18e0-137">Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a18e0-137">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="a18e0-138">Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [en cours d’exécution les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a18e0-138">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a18e0-139">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="a18e0-139">The samples may already be installed on your machine.</span></span> <span data-ttu-id="a18e0-140">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="a18e0-140">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="a18e0-141">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="a18e0-141">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a18e0-142">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="a18e0-142">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Default`  
  
## <a name="see-also"></a><span data-ttu-id="a18e0-143">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a18e0-143">See Also</span></span>
