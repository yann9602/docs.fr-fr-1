---
title: Contrat d'erreur
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b31b140e-dc3b-408b-b3c7-10b6fe769725
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3ab1213b5821233e28f36089039145d5874dd3a8
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="fault-contract"></a><span data-ttu-id="d6ecf-102">Contrat d'erreur</span><span class="sxs-lookup"><span data-stu-id="d6ecf-102">Fault Contract</span></span>
<span data-ttu-id="d6ecf-103">Cet exemple illustre comment transmettre les informations relatives à une erreur d'un service à un client.</span><span class="sxs-lookup"><span data-stu-id="d6ecf-103">The Fault Contract sample demonstrates how to communicate error information from a service to a client.</span></span> <span data-ttu-id="d6ecf-104">L’exemple est basé sur le [mise en route](../../../../docs/framework/wcf/samples/getting-started-sample.md), avec du code supplémentaire est ajouté au service pour convertir une exception interne d’une erreur.</span><span class="sxs-lookup"><span data-stu-id="d6ecf-104">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), with some additional code added to the service to convert an internal exception to a fault.</span></span> <span data-ttu-id="d6ecf-105">Le client tente d'effectuer une opération de division par zéro pour imposer la génération d'une erreur sur le service.</span><span class="sxs-lookup"><span data-stu-id="d6ecf-105">The client attempts to perform division by zero to force an error condition on the service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d6ecf-106">La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="d6ecf-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="d6ecf-107">Le contrat de calculatrice a été modifié afin d'y inclure un <xref:System.ServiceModel.FaultContractAttribute>, tel qu'illustré dans l'exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="d6ecf-107">The calculator contract has been modified to include a <xref:System.ServiceModel.FaultContractAttribute> as shown in the following sample code.</span></span>  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface ICalculator  
{  
    [OperationContract]  
    int Add(int n1, int n2);  
    [OperationContract]  
    int Subtract(int n1, int n2);  
    [OperationContract]  
    int Multiply(int n1, int n2);  
    [OperationContract]  
    [FaultContract(typeof(MathFault))]  
    int Divide(int n1, int n2);  
}  
```  
  
 <span data-ttu-id="d6ecf-108">L'attribut <xref:System.ServiceModel.FaultContractAttribute> indique que l'opération `Divide` est susceptible de retourner une erreur de type `MathFault`.</span><span class="sxs-lookup"><span data-stu-id="d6ecf-108">The <xref:System.ServiceModel.FaultContractAttribute> attribute indicates that the `Divide` operation may return a fault of type `MathFault`.</span></span> <span data-ttu-id="d6ecf-109">Il peut s'agir de tout type pouvant être sérialisé.</span><span class="sxs-lookup"><span data-stu-id="d6ecf-109">A fault can be of any type that can be serialized.</span></span> <span data-ttu-id="d6ecf-110">Ici, le type `MathFault` correspond à un contrat de données, tel qu'illustré ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="d6ecf-110">In this case, the `MathFault` is a data contract, as follows:</span></span>  
  
```  
[DataContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public class MathFault  
{      
    private string operation;  
    private string problemType;  
  
    [DataMember]  
    public string Operation  
    {  
        get { return operation; }  
        set { operation = value; }  
    }  
  
    [DataMember]          
    public string ProblemType  
    {  
        get { return problemType; }  
        set { problemType = value; }  
    }  
}  
```  
  
 <span data-ttu-id="d6ecf-111">La méthode `Divide` lève une exception <xref:System.ServiceModel.FaultException%601> lorsqu'une opération de division par zéro se produit, tel qu'illustré dans l'exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="d6ecf-111">The `Divide` method throws a <xref:System.ServiceModel.FaultException%601> exception when a divide by zero exception occurs as shown in the following sample code.</span></span> <span data-ttu-id="d6ecf-112">Cette exception provoque l'envoi d'une erreur au client.</span><span class="sxs-lookup"><span data-stu-id="d6ecf-112">This exception results in a fault being sent to the client.</span></span>  
  
```  
public int Divide(int n1, int n2)  
{  
    try  
    {  
        return n1 / n2;  
    }  
    catch (DivideByZeroException)  
    {  
        MathFault mf = new MathFault();  
        mf.operation = "division";  
        mf.problemType = "divide by zero";  
        throw new FaultException<MathFault>(mf);  
    }  
}  
```  
  
 <span data-ttu-id="d6ecf-113">Le code client impose la génération d'une erreur en demandant une division par zéro.</span><span class="sxs-lookup"><span data-stu-id="d6ecf-113">The client code forces an error by requesting a division by zero.</span></span> <span data-ttu-id="d6ecf-114">Lorsque vous exécutez l'exemple, les demandes et réponses d'opération s'affichent dans la fenêtre de console du client.</span><span class="sxs-lookup"><span data-stu-id="d6ecf-114">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="d6ecf-115">Vous pouvez voir que la division par zéro est signalée comme étant une erreur.</span><span class="sxs-lookup"><span data-stu-id="d6ecf-115">You see the division by zero being reported as a fault.</span></span> <span data-ttu-id="d6ecf-116">Appuyez sur Entrée dans la fenêtre du client pour l'arrêter.</span><span class="sxs-lookup"><span data-stu-id="d6ecf-116">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(15,3) = 18  
Subtract(145,76) = 69  
Multiply(9,81) = 729  
FaultException<MathFault>: Math fault while doing division. Problem: divide by zero  
  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="d6ecf-117">Pour ce faire, le client intercepte l'exception `FaultException<MathFault>` appropriée :</span><span class="sxs-lookup"><span data-stu-id="d6ecf-117">The client does this by catching the appropriate `FaultException<MathFault>` exception:</span></span>  
  
```  
catch (FaultException<MathFault> e)  
{  
    Console.WriteLine("FaultException<MathFault>: Math fault while doing " + e.Detail.operation + ". Problem: " + e.Detail.problemType);  
    client.Abort();  
}  
```  
  
 <span data-ttu-id="d6ecf-118">Par défaut, les informations relatives aux exceptions non escomptées ne sont pas envoyées au client afin d'éviter que les informations relatives à l'implémentation du service ne franchissent les frontières de la zone sécurisée de ce dernier.</span><span class="sxs-lookup"><span data-stu-id="d6ecf-118">By default, the details of unexpected exceptions are not sent to the client to prevent details of the service implementation from escaping the secure boundary of the service.</span></span> <span data-ttu-id="d6ecf-119">`FaultContract` permet de décrire des erreurs dans un contrat et de baliser certains types d'exceptions comme requis pour permettre leur transmission au client.</span><span class="sxs-lookup"><span data-stu-id="d6ecf-119">`FaultContract` provides a way to describe faults in a contract and mark certain types of exceptions as appropriate for transmission to the client.</span></span> <span data-ttu-id="d6ecf-120">`FaultException<T>` fournit le mécanisme d'exécution nécessaire à l'envoi des erreurs aux consommateurs.</span><span class="sxs-lookup"><span data-stu-id="d6ecf-120">`FaultException<T>` provides the run-time mechanism for sending faults to consumers.</span></span>  
  
 <span data-ttu-id="d6ecf-121">Toutefois, en cas de débogage, il est utile de consulter les détails internes relatifs aux éventuelles défaillances d'un service.</span><span class="sxs-lookup"><span data-stu-id="d6ecf-121">However, it is useful to see the internal details of a service failure when debugging.</span></span> <span data-ttu-id="d6ecf-122">Pour désactiver le comportement sécurisé précédemment décrit, vous pouvez définir la spécification suivante : inclusion des détails relatifs à toutes les exceptions non prises en charge sur le serveur dans les erreurs envoyées au client.</span><span class="sxs-lookup"><span data-stu-id="d6ecf-122">To turn off the secure behavior previously described, you can indicate that the details of every unhandled exception on the server should be included in the fault that is sent to the client.</span></span> <span data-ttu-id="d6ecf-123">Pour ce faire, il vous suffit d'affecter à <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A> la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="d6ecf-123">This is accomplished by setting <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A> to `true`.</span></span> <span data-ttu-id="d6ecf-124">Ce paramétrage peut être effectué dans le code ou la configuration, tel qu'illustré dans l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="d6ecf-124">You can either set it in code, or in configuration as shown in the following sample.</span></span>  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="CalculatorServiceBehavior">  
      <serviceMetadata httpGetEnabled="True"/>  
      <serviceDebug includeExceptionDetailInFaults="True" />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 <span data-ttu-id="d6ecf-125">En outre, le comportement doit être associé au service en définissant le `behaviorConfiguration` attribut du service dans le fichier de configuration « CalculatorServiceBehavior ».</span><span class="sxs-lookup"><span data-stu-id="d6ecf-125">Further, the behavior must be associated with the service by setting the `behaviorConfiguration` attribute of the service in the configuration file to "CalculatorServiceBehavior".</span></span>  
  
 <span data-ttu-id="d6ecf-126">Pour intercepter de telles erreurs sur le client, il est nécessaire d'intercepter l'exception non générique <xref:System.ServiceModel.FaultException>.</span><span class="sxs-lookup"><span data-stu-id="d6ecf-126">To catch such faults on the client, the non-generic <xref:System.ServiceModel.FaultException> must be caught.</span></span>  
  
 <span data-ttu-id="d6ecf-127">Ce comportement doit être utilisé à des fins de débogage uniquement et ne doit jamais être activé dans la production.</span><span class="sxs-lookup"><span data-stu-id="d6ecf-127">This behavior should only be used for debugging purposes and should never be enabled in production.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="d6ecf-128">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="d6ecf-128">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="d6ecf-129">Assurez-vous d’avoir effectué la [procédure d’installation d’à usage unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d6ecf-129">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="d6ecf-130">Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d6ecf-130">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="d6ecf-131">Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [en cours d’exécution les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d6ecf-131">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d6ecf-132">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="d6ecf-132">The samples may already be installed on your machine.</span></span> <span data-ttu-id="d6ecf-133">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="d6ecf-133">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="d6ecf-134">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="d6ecf-134">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d6ecf-135">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="d6ecf-135">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Faults`  
  
## <a name="see-also"></a><span data-ttu-id="d6ecf-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d6ecf-136">See Also</span></span>
