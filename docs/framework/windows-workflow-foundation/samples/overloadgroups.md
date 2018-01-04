---
title: OverloadGroups
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d1d547d2-f5fb-4de3-a959-ee6139a4f1ad
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 36807ce154ab70e54d211405e0cea5ead56e9b88
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="overloadgroups"></a><span data-ttu-id="6d24b-102">OverloadGroups</span><span class="sxs-lookup"><span data-stu-id="6d24b-102">OverloadGroups</span></span>
<span data-ttu-id="6d24b-103">Cet exemple se compose d'une activité (`CreateLocation`) qui a deux caractéristiques intéressantes :</span><span class="sxs-lookup"><span data-stu-id="6d24b-103">This sample consists of an activity (`CreateLocation`), which has two interesting characteristics:</span></span>  
  
1.  <span data-ttu-id="6d24b-104">Elle comprend quelques arguments obligatoires et quelques arguments facultatifs.</span><span class="sxs-lookup"><span data-stu-id="6d24b-104">It has some required arguments and some optional ones.</span></span>  
  
2.  <span data-ttu-id="6d24b-105">Elle permet à l'utilisateur de fournir un jeu d'arguments sélectionné parmi deux jeux d'arguments différents.</span><span class="sxs-lookup"><span data-stu-id="6d24b-105">It allows the user to choose to provide one of two different sets of arguments.</span></span>  
  
 <span data-ttu-id="6d24b-106">Ces comportements sont obtenus à l'aide des deux fonctionnalités suivantes :</span><span class="sxs-lookup"><span data-stu-id="6d24b-106">These behaviors are accomplished by using these two features:</span></span>  
  
-   <span data-ttu-id="6d24b-107">`[isRequired]` valide qu'une propriété d'une activité spécifique est affectée et, dans le cas contraire, lève une exception.</span><span class="sxs-lookup"><span data-stu-id="6d24b-107">`[isRequired]` validates that a property of a specific activity is assign, and if not, it throws an exception.</span></span>  
  
-   <span data-ttu-id="6d24b-108">`[OverloadGroup]` réunit un jeu d'arguments afin que l'utilisateur de l'activité puisse choisir d'utiliser l'un des deux jeux.</span><span class="sxs-lookup"><span data-stu-id="6d24b-108">`[OverloadGroup]` puts together a set of arguments, so that the user of the activity can choose between using one set or another.</span></span> <span data-ttu-id="6d24b-109">L'utilisateur ne peut pas utiliser d'arguments de différents groupes surchargés dans la même instance.</span><span class="sxs-lookup"><span data-stu-id="6d24b-109">The user cannot use arguments from different Overload Groups in the same instance.</span></span>  
  
 <span data-ttu-id="6d24b-110">Après avoir configuré des workflows différents, appelez <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> qui retourne une collection <xref:System.Activities.Validation.ValidationResults> de <xref:System.Activities.Validation.Constraint>.</span><span class="sxs-lookup"><span data-stu-id="6d24b-110">After setting up different workflows, call <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> which returns a <xref:System.Activities.Validation.ValidationResults> collection of <xref:System.Activities.Validation.Constraint>.</span></span> <span data-ttu-id="6d24b-111">Imprimez les objets <xref:System.Activities.Validation.Constraint> sur la console.</span><span class="sxs-lookup"><span data-stu-id="6d24b-111">Print the <xref:System.Activities.Validation.Constraint> objects to the console.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="6d24b-112">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="6d24b-112">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="6d24b-113">Ouvrez le **OverloadGroups.sln** exemple de solution dans [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6d24b-113">Open the **OverloadGroups.sln** sample solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="6d24b-114">Générez et exécutez la solution.</span><span class="sxs-lookup"><span data-stu-id="6d24b-114">Build and run the solution.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="6d24b-115">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="6d24b-115">The samples may already be installed on your machine.</span></span> <span data-ttu-id="6d24b-116">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="6d24b-116">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="6d24b-117">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="6d24b-117">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="6d24b-118">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="6d24b-118">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Validation\OverloadGroups`
