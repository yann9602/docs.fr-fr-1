---
title: Mise en forme des messages dans les services de workflow
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6d15d44b-20f8-4cb7-bd4f-598c32781ebc
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ddbe0c4e1b4af422925c42044136396e4036469e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="formatting-messages-in-workflow-services"></a><span data-ttu-id="2f11d-102">Mise en forme des messages dans les services de workflow</span><span class="sxs-lookup"><span data-stu-id="2f11d-102">Formatting messages in Workflow Services</span></span>
<span data-ttu-id="2f11d-103">Cet exemple montre comment différents types utilisateur peuvent être utilisés dans des activités de messagerie (services WF).</span><span class="sxs-lookup"><span data-stu-id="2f11d-103">This sample shows how different user types can be used in messaging activities (WF services).</span></span> <span data-ttu-id="2f11d-104">L'exemple de service est un service d'approbation des dépenses simple qui expose trois opérations.</span><span class="sxs-lookup"><span data-stu-id="2f11d-104">The sample service is a simple expense approval service and exposes three operations.</span></span> <span data-ttu-id="2f11d-105">`ApproveExpense` prend un type de contrat de données et montre comment utiliser des types connus.</span><span class="sxs-lookup"><span data-stu-id="2f11d-105">`ApproveExpense` takes a data contract type and shows how to use known types.</span></span> <span data-ttu-id="2f11d-106">L'opération retourne `true` ou `false` selon le montant de la dépense.</span><span class="sxs-lookup"><span data-stu-id="2f11d-106">The operation returns `true` or `false` based on the expense amount.</span></span> <span data-ttu-id="2f11d-107">`ApprovePO`prend un type XmlSerializer et retourne `true` ou `false` selon le montant de frais.`ApprovedVendor`</span><span class="sxs-lookup"><span data-stu-id="2f11d-107">`ApprovePO` takes an XmlSerializer type and returns `true` or `false` based on the expense amount.`ApprovedVendor`</span></span> <span data-ttu-id="2f11d-108">prend un type de contrat de message et retourne `true` ou `false` si le fournisseur figure dans la liste des fournisseurs approuvés ou si la demande provient du service financier (le service financier peut utiliser n’importe quel fournisseur).</span><span class="sxs-lookup"><span data-stu-id="2f11d-108">takes a message contract type and returns `true` or `false` if the vendor is in the list of approved vendors or if the request came from the finance department (the finance department can use any vendor).</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="2f11d-109">Pour utiliser cet exemple</span><span class="sxs-lookup"><span data-stu-id="2f11d-109">To use this sample</span></span>  
  
1.  <span data-ttu-id="2f11d-110">Chargez la solution du projet dans [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] et générez le projet.</span><span class="sxs-lookup"><span data-stu-id="2f11d-110">Load the project solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] and build the project.</span></span>  
  
2.  <span data-ttu-id="2f11d-111">En premier lieu, exécutez le service, généré dans [répertoire de base de la solution]\FormatterService\bin\debug\.</span><span class="sxs-lookup"><span data-stu-id="2f11d-111">First run the service, generated in [solution base directory]\FormatterService\bin\debug\\</span></span>  
  
3.  <span data-ttu-id="2f11d-112">En second lieu, exécutez l'application cliente, générée dans [répertoire de base de la solution]\FormatterClient\bin\debug.</span><span class="sxs-lookup"><span data-stu-id="2f11d-112">Second, run the Client application generated in [solution base directory]\FormatterClient\bin\debug.</span></span>  
  
4.  <span data-ttu-id="2f11d-113">Le client appelle trois opérations sur le service et imprime les résultats.</span><span class="sxs-lookup"><span data-stu-id="2f11d-113">The client calls three operations on the service and prints the results.</span></span> <span data-ttu-id="2f11d-114">Une fois cette opération terminée, appuyez sur ENTRÉE pour quitter le client, puis le service.</span><span class="sxs-lookup"><span data-stu-id="2f11d-114">When complete, press ENTER to exit the client and then the service.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="2f11d-115">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="2f11d-115">The samples may already be installed on your machine.</span></span> <span data-ttu-id="2f11d-116">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="2f11d-116">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="2f11d-117">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="2f11d-117">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="2f11d-118">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="2f11d-118">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\Formatter`  
  
## <a name="see-also"></a><span data-ttu-id="2f11d-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2f11d-119">See Also</span></span>
