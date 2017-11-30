---
title: Utilisation de la classe WorkflowInvoker
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0a966164-3990-4e78-8aa2-c6797ebbee94
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 8bb6c4049b56702c8fad226c20884ff581ec6203
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="using-the-workflowinvoker-class"></a><span data-ttu-id="6a4e6-102">Utilisation de la classe WorkflowInvoker</span><span class="sxs-lookup"><span data-stu-id="6a4e6-102">Using the WorkflowInvoker Class</span></span>
<span data-ttu-id="6a4e6-103">Cet exemple montre comment utiliser la classe <xref:System.Activities.WorkflowInvoker> pour appeler une activité comme s'il s'agissait d'une méthode.</span><span class="sxs-lookup"><span data-stu-id="6a4e6-103">This sample demonstrates how to use the <xref:System.Activities.WorkflowInvoker> class to invoke an activity as if it were a method.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="6a4e6-104">Détails de l'exemple</span><span class="sxs-lookup"><span data-stu-id="6a4e6-104">Sample Details</span></span>  
 <span data-ttu-id="6a4e6-105">Utiliser la classe <xref:System.Activities.WorkflowInvoker> est la façon la plus simple d'exécuter une activité.</span><span class="sxs-lookup"><span data-stu-id="6a4e6-105">Using the <xref:System.Activities.WorkflowInvoker> class is the simplest way to execute an activity.</span></span> <span data-ttu-id="6a4e6-106">Elle est conçue pour exécuter une activité directement comme s'il s'agissait d'un appel de méthode.</span><span class="sxs-lookup"><span data-stu-id="6a4e6-106">It is designed for directly running an activity as if it were a method call.</span></span> <span data-ttu-id="6a4e6-107">C'est une API légère, hautement performante et simple d'utilisation, destinée à être utilisée dans des scénarios où l'exécution d'une activité ne requiert pas l'infrastructure de contrôle fournie par d'autres variations d'hébergement.</span><span class="sxs-lookup"><span data-stu-id="6a4e6-107">It is a lightweight, high-performing, easy to use API for use in scenarios where an activity’s execution does not require the control infrastructure provided by other hosting variations.</span></span>  
  
 <span data-ttu-id="6a4e6-108">L’exemple utilise une activité personnalisée qui dérive de <xref:System.Activities.CodeActivity%601>< Int32\> nommé `Add` qui ajoute deux <xref:System.Activities.InArgument%601>, `X` et `Y`et retourne un `Result` <xref:System.Activities.OutArgument%601>.</span><span class="sxs-lookup"><span data-stu-id="6a4e6-108">The sample uses a custom activity that derives from <xref:System.Activities.CodeActivity%601><Int32\> named `Add` that adds two <xref:System.Activities.InArgument%601>, `X` and `Y`, and returns a `Result`<xref:System.Activities.OutArgument%601>.</span></span> <span data-ttu-id="6a4e6-109">(<xref:System.Activities.CodeActivity%601>\<T > dérive <xref:System.Activities.Activity%601>< T\>, qui a un <xref:System.Activities.OutArgument%601> \<T > nommé `Result`.) A `Dictionary` \<chaîne, objet > est utilisé pour passer des arguments dans une activité appelée via <xref:System.Activities.WorkflowInvoker>.</span><span class="sxs-lookup"><span data-stu-id="6a4e6-109">(<xref:System.Activities.CodeActivity%601>\<T> derives from <xref:System.Activities.Activity%601><T\>, which has an <xref:System.Activities.OutArgument%601>\<T> named `Result`.) A `Dictionary`\<string, object> is used to pass arguments into an activity being invoked through <xref:System.Activities.WorkflowInvoker>.</span></span> <span data-ttu-id="6a4e6-110">La clé du dictionnaire correspond au nom d’un argument sur l’activité appelée.</span><span class="sxs-lookup"><span data-stu-id="6a4e6-110">The key of the dictionary corresponds to the name of an argument on the invoked activity.</span></span> <span data-ttu-id="6a4e6-111">La valeur associée à une clé particulière est liée à l'argument identifié par la clé.</span><span class="sxs-lookup"><span data-stu-id="6a4e6-111">The value associated with a particular key is bound to the argument identified by the key.</span></span>  
  
 <span data-ttu-id="6a4e6-112">L'exemple appelle <xref:System.Activities.WorkflowInvoker.Invoke%2A> et passe un dictionnaire qui contient des valeurs pour `X` et `Y`.</span><span class="sxs-lookup"><span data-stu-id="6a4e6-112">The sample calls <xref:System.Activities.WorkflowInvoker.Invoke%2A> and passes a dictionary that contains values for `X` and `Y`.</span></span> <span data-ttu-id="6a4e6-113">La classe <xref:System.Activities.WorkflowInvoker> lie ces valeurs aux arguments de l'activité `Add`, exécute l'activité, puis retourne le résultat.</span><span class="sxs-lookup"><span data-stu-id="6a4e6-113">The <xref:System.Activities.WorkflowInvoker> class binds these values to the `Add` activity’s arguments, executes the activity, and returns the result.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="6a4e6-114">Pour utiliser cet exemple</span><span class="sxs-lookup"><span data-stu-id="6a4e6-114">To use this sample</span></span>  
  
1.  <span data-ttu-id="6a4e6-115">À l'aide de [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], ouvrez le fichier solution Invoker.sln.</span><span class="sxs-lookup"><span data-stu-id="6a4e6-115">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the Invoker.sln solution file.</span></span>  
  
2.  <span data-ttu-id="6a4e6-116">Pour générer la solution, appuyez sur Ctrl+Maj+B.</span><span class="sxs-lookup"><span data-stu-id="6a4e6-116">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="6a4e6-117">Pour exécuter la solution, appuyez sur F5.</span><span class="sxs-lookup"><span data-stu-id="6a4e6-117">To run the solution, press F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="6a4e6-118">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="6a4e6-118">The samples may already be installed on your machine.</span></span> <span data-ttu-id="6a4e6-119">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="6a4e6-119">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="6a4e6-120">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="6a4e6-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="6a4e6-121">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="6a4e6-121">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\WorkflowInvoker`