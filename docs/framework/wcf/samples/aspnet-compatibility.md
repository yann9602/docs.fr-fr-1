---
title: ASP.NET Compatibility
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c8b51f1e-c096-4c42-ad99-0519887bbbc5
caps.latest.revision: "25"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 751fe96caa2be63e925b3107fa2c198b523bef72
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="aspnet-compatibility"></a><span data-ttu-id="a5c0a-102">ASP.NET Compatibility</span><span class="sxs-lookup"><span data-stu-id="a5c0a-102">ASP.NET Compatibility</span></span>
<span data-ttu-id="a5c0a-103">Cet exemple illustre comment activer le mode de compatibilité [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] dans [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a5c0a-103">This sample demonstrates how to enable [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Compatibility mode in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span></span> <span data-ttu-id="a5c0a-104">Les services qui s'exécutent dans le mode de compatibilité [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] participent pleinement au pipeline de l'application [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] et peuvent utiliser des fonctionnalités [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] telles que l'autorisation de fichier/d'URL, l'état de session et la classe <xref:System.Web.HttpContext>.</span><span class="sxs-lookup"><span data-stu-id="a5c0a-104">Services running in [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Compatibility mode participate fully in the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] application pipeline and can make use of [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] features such as file/URL authorization, session state, and the <xref:System.Web.HttpContext> class.</span></span> <span data-ttu-id="a5c0a-105">La classe <xref:System.Web.HttpContext> permet l'accès aux cookies, aux sessions ainsi qu'à d'autres fonctionnalités [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a5c0a-105">The <xref:System.Web.HttpContext> class allows access to cookies, sessions, and other [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] features.</span></span> <span data-ttu-id="a5c0a-106">Dans ce mode, les liaisons doivent utiliser le transport HTTP et le service lui-même doit être hébergé dans les services IIS.</span><span class="sxs-lookup"><span data-stu-id="a5c0a-106">This mode requires that the bindings use the HTTP transport and the service itself must be hosted in IIS.</span></span>  
  
 <span data-ttu-id="a5c0a-107">Dans cet exemple, le client est une application console (fichier exécutable) et le service est hébergé dans les services IIS </span><span class="sxs-lookup"><span data-stu-id="a5c0a-107">In this sample, the client is a console application (an executable) and the service is hosted in Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a5c0a-108">La procédure d'installation ainsi que les instructions de génération correspondant à cet exemple figurent en fin de rubrique.</span><span class="sxs-lookup"><span data-stu-id="a5c0a-108">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a5c0a-109">Cet exemple requiert pour fonctionner un pool d'applications [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a5c0a-109">This sample requires a [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] application pool in order to run.</span></span> <span data-ttu-id="a5c0a-110">Pour créer un pool d'applications ou modifier le pool d'applications par défaut, procédez comme suit.</span><span class="sxs-lookup"><span data-stu-id="a5c0a-110">To create a new application pool, or to modify the default application pool, follow these steps.</span></span>  
>   
>  1.  <span data-ttu-id="a5c0a-111">Ouvrez le **Panneau de configuration**.</span><span class="sxs-lookup"><span data-stu-id="a5c0a-111">Open **Control Panel**.</span></span>  <span data-ttu-id="a5c0a-112">Ouvrez le **outils d’administration** applet sous le **système et sécurité** titre.</span><span class="sxs-lookup"><span data-stu-id="a5c0a-112">Open the **Administrative Tools** applet under the **System and Security** heading.</span></span> <span data-ttu-id="a5c0a-113">Ouvrez le **Gestionnaire des Services Internet (IIS)** applet.</span><span class="sxs-lookup"><span data-stu-id="a5c0a-113">Open the **Internet Information Services (IIS) Manager** applet.</span></span>  
> 2.  <span data-ttu-id="a5c0a-114">Développez l’arborescence dans le **connexions** volet.</span><span class="sxs-lookup"><span data-stu-id="a5c0a-114">Expand the treeview in the **Connections** pane.</span></span> <span data-ttu-id="a5c0a-115">Sélectionnez le **Pools d’applications** nœud.</span><span class="sxs-lookup"><span data-stu-id="a5c0a-115">Select the **Application Pools** node.</span></span>  
> 3.  <span data-ttu-id="a5c0a-116">Pour définir le pool d’applications par défaut à utiliser [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] (ce qui peut entraîner des problèmes d’incompatibilité avec les sites existants), avec le bouton droit le **DefaultAppPool** élément de liste et sélectionnez **les paramètres de base...** .</span><span class="sxs-lookup"><span data-stu-id="a5c0a-116">To set the default application pool to use [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] (which may cause incompatibility problems with existing sites), right-click the **DefaultAppPool** list item and select **Basic Settings…**.</span></span> <span data-ttu-id="a5c0a-117">Définir le **.Net Framework Version** déroulant **.Net Framework v4.0.30128** (ou version ultérieure).</span><span class="sxs-lookup"><span data-stu-id="a5c0a-117">Set the **.Net Framework Version** pull-down to **.Net Framework v4.0.30128** (or later).</span></span>  
> 4.  <span data-ttu-id="a5c0a-118">Pour créer un nouveau pool d’applications qui utilise [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] (pour préserver la compatibilité avec d’autres applications), avec le bouton droit le **Pools d’applications** nœud et sélectionnez **ajouter un Pool d’applications...** .</span><span class="sxs-lookup"><span data-stu-id="a5c0a-118">To create a new application pool that uses [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] (to preserve compatibility for other applications), right-click the **Application Pools** node and select **Add Application Pool…**.</span></span> <span data-ttu-id="a5c0a-119">Nommez le nouveau pool d’applications et le **.Net Framework Version** déroulant **.Net Framework v4.0.30128** (ou version ultérieure).</span><span class="sxs-lookup"><span data-stu-id="a5c0a-119">Name the new application pool, and set the **.Net Framework Version** pull-down to **.Net Framework v4.0.30128** (or later).</span></span> <span data-ttu-id="a5c0a-120">Une fois que le programme d’installation en cours d’exécution d’étapes ci-dessous, cliquez sur le **ServiceModelSamples** application et sélectionnez **gérer l’Application**, **paramètres avancés...** .</span><span class="sxs-lookup"><span data-stu-id="a5c0a-120">After running the setup steps below, right-click the **ServiceModelSamples** application and select **Manage Application**, **Advanced Settings…**.</span></span> <span data-ttu-id="a5c0a-121">Définir le **Pool d’applications** pour le pool d’applications.</span><span class="sxs-lookup"><span data-stu-id="a5c0a-121">Set the **Application Pool** to the new application pool.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a5c0a-122">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="a5c0a-122">The samples may already be installed on your computer.</span></span> <span data-ttu-id="a5c0a-123">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="a5c0a-123">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="a5c0a-124">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="a5c0a-124">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a5c0a-125">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="a5c0a-125">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WebHost\ASPNetCompatibility`  
  
 <span data-ttu-id="a5c0a-126">Cet exemple est basé sur le [mise en route](../../../../docs/framework/wcf/samples/getting-started-sample.md), qui implémente un service de calculatrice.</span><span class="sxs-lookup"><span data-stu-id="a5c0a-126">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), which implements a calculator service.</span></span> <span data-ttu-id="a5c0a-127">Les contrats `ICalculator` et `ICalculatorSession` ont été modifiés pour permettre à un ensemble d'opérations d'être effectuées tout en conservant un résultat d'exécution.</span><span class="sxs-lookup"><span data-stu-id="a5c0a-127">The `ICalculator` contract has been modified as the `ICalculatorSession` contract to allow a set of operations to be performed, while keeping a running result.</span></span>  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface ICalculatorSession  
{  
    [OperationContract]  
    void Clear();  
    [OperationContract]  
    void AddTo(double n);  
    [OperationContract]  
    void SubtractFrom(double n);  
    [OperationContract]  
    void MultiplyBy(double n);  
    [OperationContract]  
    void DivideBy(double n);  
    [OperationContract]  
    double Result();  
}  
```  
  
 <span data-ttu-id="a5c0a-128">Le service conserve l'état de chaque client (à l'aide de la fonctionnalité correspondante) tandis que plusieurs opérations de service sont appelées pour effectuer un calcul.</span><span class="sxs-lookup"><span data-stu-id="a5c0a-128">The service maintains state, using the feature, for each client as multiple service operations are called to perform a calculation.</span></span> <span data-ttu-id="a5c0a-129">Le client peut récupérer le résultat actuel en appelant `Result` et remettre le résultat à zéro en appelant `Clear`.</span><span class="sxs-lookup"><span data-stu-id="a5c0a-129">The client can retrieve the current result by calling `Result` and can clear the result to zero by calling `Clear`.</span></span>  
  
 <span data-ttu-id="a5c0a-130">Le service utilise la session [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] pour stocker le résultat de chaque session de client.</span><span class="sxs-lookup"><span data-stu-id="a5c0a-130">The service uses the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] session to store the result for each client session.</span></span> <span data-ttu-id="a5c0a-131">Cela lui permet de conserver le résultat d'exécution de chaque client tandis qu'il reçoit plusieurs appels.</span><span class="sxs-lookup"><span data-stu-id="a5c0a-131">This allows the service to maintain the running result for each client across multiple calls to the service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a5c0a-132">L'état de session [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] et les sessions [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sont deux fonctionnalités très différentes l'une de l'autre.</span><span class="sxs-lookup"><span data-stu-id="a5c0a-132">[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] session state and [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sessions are very different things.</span></span>  <span data-ttu-id="a5c0a-133">Consultez le [Session](../../../../docs/framework/wcf/samples/session.md) pour plus d’informations sur [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sessions.</span><span class="sxs-lookup"><span data-stu-id="a5c0a-133">See the [Session](../../../../docs/framework/wcf/samples/session.md) for details on [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sessions.</span></span>  
  
 <span data-ttu-id="a5c0a-134">Le service dépend étroitement de l'état de session [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] et nécessite que le mode de compatibilité [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] fonctionne correctement.</span><span class="sxs-lookup"><span data-stu-id="a5c0a-134">The service has an intimate dependency on [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] session state and requires [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] compatibility mode to function correctly.</span></span> <span data-ttu-id="a5c0a-135">Ces spécifications sont définies de manière déclarative en appliquant l'attribut `AspNetCompatibilityRequirements`.</span><span class="sxs-lookup"><span data-stu-id="a5c0a-135">These requirements are expressed declaratively by applying the `AspNetCompatibilityRequirements` attribute.</span></span>  
  
```  
[AspNetCompatibilityRequirements(RequirementsMode =  
                       AspNetCompatibilityRequirementsMode.Required)]  
public class CalculatorService : ICalculatorSession  
{  
    double Result  
    {  // store result in AspNet Session  
       get {  
          if (HttpContext.Current.Session["Result"] != null)  
             return (double)HttpContext.Current.Session["Result"];  
          return 0.0D;  
       }  
       set  
       {  
          HttpContext.Current.Session["Result"] = value;  
       }  
    }  
    public void Clear()  
    {  
        Result = 0.0D;  
    }  
    public void AddTo(double n)  
    {  
        Result += n;  
    }  
    public void SubtractFrom(double n)  
    {  
        Result -= n;  
    }  
    public void MultiplyBy(double n)  
    {  
        Result *= n;  
    }  
    public void DivideBy(double n)  
    {  
        Result /= n;  
    }  
    public double Result()  
    {  
        return Result;  
    }  
}  
```  
  
 <span data-ttu-id="a5c0a-136">Lorsque vous exécutez l'exemple, les demandes et réponses d'opération s'affichent dans la fenêtre de console du client.</span><span class="sxs-lookup"><span data-stu-id="a5c0a-136">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="a5c0a-137">Appuyez sur Entrée dans la fenêtre du client pour l'arrêter.</span><span class="sxs-lookup"><span data-stu-id="a5c0a-137">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
0, + 100, - 50, * 17.65, / 2 = 441.25  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="a5c0a-138">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="a5c0a-138">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="a5c0a-139">Vérifiez que vous avez effectué la [procédure d’installation d’à usage unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a5c0a-139">Be sure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="a5c0a-140">Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a5c0a-140">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="a5c0a-141">Une fois la solution générée, exécutez Setup.bat pour installer l'application ServiceModelSamples dans [!INCLUDE[iisver](../../../../includes/iisver-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a5c0a-141">After the solution has been built, run Setup.bat to set up the ServiceModelSamples Application in [!INCLUDE[iisver](../../../../includes/iisver-md.md)].</span></span> <span data-ttu-id="a5c0a-142">Le répertoire ServiceModelSamples doit maintenant apparaître en tant qu'application [!INCLUDE[iisver](../../../../includes/iisver-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a5c0a-142">The ServiceModelSamples directory should now appear as an [!INCLUDE[iisver](../../../../includes/iisver-md.md)] Application.</span></span>  
  
4.  <span data-ttu-id="a5c0a-143">Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [en cours d’exécution les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a5c0a-143">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5c0a-144">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a5c0a-144">See Also</span></span>  
 [<span data-ttu-id="a5c0a-145">Hébergement de AppFabric et exemples de persistance</span><span class="sxs-lookup"><span data-stu-id="a5c0a-145">AppFabric Hosting and Persistence Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193961)
