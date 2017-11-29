---
title: "Exemple de compensation personnalisée"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 385920da-9284-44bf-9fe9-0d87c7478ec5
caps.latest.revision: "13"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c3a9745c0cdd3a2d7050aed083d2eee5dfd4aaaf
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="custom-compensation-sample"></a><span data-ttu-id="a8edc-102">Exemple de compensation personnalisée</span><span class="sxs-lookup"><span data-stu-id="a8edc-102">Custom Compensation Sample</span></span>
<span data-ttu-id="a8edc-103">Cet exemple montre comment utiliser <xref:System.Activities.Statements.CompensableActivity> et son gestionnaire de compensation pour définir une logique de compensation personnalisée.</span><span class="sxs-lookup"><span data-stu-id="a8edc-103">This sample shows how to use <xref:System.Activities.Statements.CompensableActivity> and its compensation handler to define custom compensation logic.</span></span> <span data-ttu-id="a8edc-104">Le scénario modélisé de cet exemple est une agence de location de camions.</span><span class="sxs-lookup"><span data-stu-id="a8edc-104">The scenario modeled in this sample is a Truck Rental Agency.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="a8edc-105">Détails de l'exemple</span><span class="sxs-lookup"><span data-stu-id="a8edc-105">Sample Details</span></span>  
 <span data-ttu-id="a8edc-106">Les étapes simulées sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="a8edc-106">The steps simulated are:</span></span>  
  
1.  <span data-ttu-id="a8edc-107">L'utilisateur demande des devis de location de camion pour une date donnée.</span><span class="sxs-lookup"><span data-stu-id="a8edc-107">The user requests truck rental quotes for a given date.</span></span>  
  
2.  <span data-ttu-id="a8edc-108">Trois sociétés de camions sont contactées et les trois devis sont fournis.</span><span class="sxs-lookup"><span data-stu-id="a8edc-108">Three truck companies are contacted and the three quotes are provided.</span></span>  
  
3.  <span data-ttu-id="a8edc-109">L'utilisateur sélectionne un devis pour un camion et effectue la commande par carte de crédit.</span><span class="sxs-lookup"><span data-stu-id="a8edc-109">The user selects one truck quote and proceeds to order by credit card.</span></span>  
  
4.  <span data-ttu-id="a8edc-110">L'application annule les deux autres devis de camion.</span><span class="sxs-lookup"><span data-stu-id="a8edc-110">The application cancels the other two truck quotes.</span></span>  
  
5.  <span data-ttu-id="a8edc-111">L'application facture des frais de service qui ne sont pas remboursables pour les comptes non Premium en cas d'annulation 10 jours ou moins avant la date de réservation.</span><span class="sxs-lookup"><span data-stu-id="a8edc-111">The application charges a service fee that is non-refundable for non-premium accounts if cancelation happens 10 days or less prior to the reservation date.</span></span>  
  
6.  <span data-ttu-id="a8edc-112">L'application facture le prix de location du camion.</span><span class="sxs-lookup"><span data-stu-id="a8edc-112">The application charges the truck rental fee.</span></span>  
  
7.  <span data-ttu-id="a8edc-113">L'application attend jusqu'à la date de réservation ou jusqu'à ce que le client ait décidé d'annuler la réservation, selon ce qui se produit en premier.</span><span class="sxs-lookup"><span data-stu-id="a8edc-113">The application waits until the reservation date or until the customer decided to cancel the reservation, whichever comes first.</span></span>  
  
8.  <span data-ttu-id="a8edc-114">Si le client annule la réservation, la logique de compensation personnalisée <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> s'exécute d'après la logique suivante :</span><span class="sxs-lookup"><span data-stu-id="a8edc-114">If the customer cancels the reservation, the <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> custom compensation logic runs according to the following logic:</span></span>  
  
    1.  <span data-ttu-id="a8edc-115">Si le client dispose d'un compte non Premium et qu'il reste moins que 10 jours avant la date de réservation, les frais de service restent facturés ; sinon, l'application rembourse les frais de service.</span><span class="sxs-lookup"><span data-stu-id="a8edc-115">If the customer has a non-premium account and it is less than 10 days prior to the reservation date, then the service fee is still charged; otherwise, the application refunds the service fee.</span></span>  
  
    2.  <span data-ttu-id="a8edc-116">Le reste des activités compensables (commande de camion + frais de commande du camion) sont exécutées d'après la logique de compensation par défaut, laquelle consiste à compenser dans l'ordre inverse de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="a8edc-116">The rest of the compensable activities (truck order + truck order fee) are run according to the default compensation logic, which is to compensate in reverse order of execution.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="a8edc-117">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="a8edc-117">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="a8edc-118">À l'aide de [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], ouvrez la solution CustomCompensation.sln.</span><span class="sxs-lookup"><span data-stu-id="a8edc-118">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the CustomCompensation.sln solution.</span></span> <span data-ttu-id="a8edc-119">Elle se trouve dans le répertoire \WF\Basic\Compensation\CustomCompensation.</span><span class="sxs-lookup"><span data-stu-id="a8edc-119">It is located in the \WF\Basic\Compensation\CustomCompensation directory.</span></span>  
  
2.  <span data-ttu-id="a8edc-120">Appuyez sur Ctrl+Maj+B pour générer la solution.</span><span class="sxs-lookup"><span data-stu-id="a8edc-120">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
3.  <span data-ttu-id="a8edc-121">Appuyez sur CTRL+F5 pour exécuter l'application.</span><span class="sxs-lookup"><span data-stu-id="a8edc-121">Press CTRL + F5 to run the application.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a8edc-122">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="a8edc-122">The samples may already be installed on your machine.</span></span> <span data-ttu-id="a8edc-123">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="a8edc-123">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="a8edc-124">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="a8edc-124">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a8edc-125">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="a8edc-125">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Compensation\CustomCompensation`  
  
## <a name="see-also"></a><span data-ttu-id="a8edc-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a8edc-126">See Also</span></span>
