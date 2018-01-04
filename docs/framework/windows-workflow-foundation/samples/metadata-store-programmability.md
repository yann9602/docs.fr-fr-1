---
title: "Programmabilité du magasin des métadonnées"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5b613661-f3f9-4e07-8e88-28c9ea2fd8f8
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2b8bfce17169a1095d2d2817467fcc8f3366ead3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="metadata-store-programmability"></a><span data-ttu-id="d0603-102">Programmabilité du magasin des métadonnées</span><span class="sxs-lookup"><span data-stu-id="d0603-102">Metadata Store Programmability</span></span>
<span data-ttu-id="d0603-103">Le magasin des métadonnées est une fonctionnalité du [!INCLUDE[wfd1](../../../../includes/wfd1-md.md)] qui permet d'associer des métadonnées arbitraires, sous la forme d'attributs CLR, à des types au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="d0603-103">The metadata store is a [!INCLUDE[wfd1](../../../../includes/wfd1-md.md)] feature that allows for the association of arbitrary metadata, in the form of CLR attributes, to types at runtime.</span></span> <span data-ttu-id="d0603-104">Cela permet un couplage faible entre les composants runtime et leurs équivalents au moment du design, ainsi que la modification des composants au moment du design sans affecter le runtime.</span><span class="sxs-lookup"><span data-stu-id="d0603-104">This allows for a loose coupling between the run-time components and their design-time counterparts, as well as the ability to change the design-time components without affecting the runtime.</span></span> <span data-ttu-id="d0603-105">L'exemple montre comment d'écrire des programmes par rapport au magasin des métadonnées en appliquant des attributs à un type au moment de l'exécution, la source sur laquelle nous n'avons aucun contrôle.</span><span class="sxs-lookup"><span data-stu-id="d0603-105">The sample shows how to program against the metadata store by applying attributes to a run-time type, the source for which we have no control over.</span></span> <span data-ttu-id="d0603-106">La terminologie généralement utilisée est qu'une application d'hébergement enregistre les métadonnées pour un ensemble de types.</span><span class="sxs-lookup"><span data-stu-id="d0603-106">The terminology typically used is that a hosting application registers the metadata for a set of types.</span></span>  
  
 <span data-ttu-id="d0603-107">Dans la sortie, vous pouvez remarquer un attribut supplémentaire inattendu, <!--zz <xref:System.Runtime.InteropServices.GUIDAttribute> --> `System.Runtime.InteropServices.GUIDAttribute`.</span><span class="sxs-lookup"><span data-stu-id="d0603-107">Within the output, you may notice an additional, unexpected attribute, <!--zz <xref:System.Runtime.InteropServices.GUIDAttribute> --> `System.Runtime.InteropServices.GUIDAttribute`.</span></span> <span data-ttu-id="d0603-108">Il est ajouté lorsque l'API des métadonnées est utilisée, et n'a aucun impact sur l'exécution de l'exemple.</span><span class="sxs-lookup"><span data-stu-id="d0603-108">This is added when using the Metadata API and has no impact on the running of the sample.</span></span>  
  
 <span data-ttu-id="d0603-109">Cet exemple illustre les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="d0603-109">This sample demonstrates:</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="d0603-110">Démonstrations</span><span class="sxs-lookup"><span data-stu-id="d0603-110">Demonstrates</span></span>  
  
-   <span data-ttu-id="d0603-111">Injection d'attributs à l'aide de l'API du magasin des métadonnées.</span><span class="sxs-lookup"><span data-stu-id="d0603-111">Attribute injection using the metadata store API.</span></span>  
  
-   <span data-ttu-id="d0603-112">Utilisation d'un mécanisme de rappel pour différer l'inscription des métadonnées.</span><span class="sxs-lookup"><span data-stu-id="d0603-112">Using a callback mechanism to defer metadata registration.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="d0603-113">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="d0603-113">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="d0603-114">À l'aide de [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], ouvrez le fichier solution ProgrammingMetadataStore.sln.</span><span class="sxs-lookup"><span data-stu-id="d0603-114">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the ProgrammingMetadataStore.sln solution file.</span></span>  
  
2.  <span data-ttu-id="d0603-115">Pour générer la solution, appuyez sur Ctrl+Maj+B.</span><span class="sxs-lookup"><span data-stu-id="d0603-115">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="d0603-116">Pour exécuter la solution, appuyez sur F5.</span><span class="sxs-lookup"><span data-stu-id="d0603-116">To run the solution, press F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d0603-117">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="d0603-117">The samples may already be installed on your machine.</span></span> <span data-ttu-id="d0603-118">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="d0603-118">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="d0603-119">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="d0603-119">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d0603-120">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="d0603-120">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\MetadataStore`