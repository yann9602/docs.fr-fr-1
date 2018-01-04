---
title: UriTemplate Table, exemple
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5dd1d38f-1989-4c64-820d-821f5a02216a
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f8d8b05bcb897cfb7371b1d5353b6fd0e7949b08
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="uritemplate-table-sample"></a><span data-ttu-id="3b9a0-102">UriTemplate Table, exemple</span><span class="sxs-lookup"><span data-stu-id="3b9a0-102">UriTemplate Table Sample</span></span>
<span data-ttu-id="3b9a0-103">La classe <xref:System.UriTemplateTable> fournit une structure de table associative de type dictionnaire permettant d'utiliser un ensemble d'instances d'`UriTemplate`.</span><span class="sxs-lookup"><span data-stu-id="3b9a0-103">The <xref:System.UriTemplateTable> class provides a dictionary-like associative table structure for working with a set of `UriTemplate` instances.</span></span> <span data-ttu-id="3b9a0-104">Les URI (Uniform Resource Identifier) spécifiques peuvent être mis en correspondance avec tous les modèles de la table de manière efficace, et les données associées au modèle mis en correspondance peuvent être récupérées.</span><span class="sxs-lookup"><span data-stu-id="3b9a0-104">Specific Uniform Resource Identifiers (URIs) can be matched efficiently against all templates in the table, and data associated with the matched template can be retrieved.</span></span>  
  
 <span data-ttu-id="3b9a0-105">Cet exemple présente les concepts clés suivants relatifs à la classe `UriTemplateTable` :</span><span class="sxs-lookup"><span data-stu-id="3b9a0-105">This sample demonstrates the following key concepts related to the `UriTemplateTable` class:</span></span>  
  
-   <span data-ttu-id="3b9a0-106">Syntaxe d'instanciation de `UriTemplateTable`.</span><span class="sxs-lookup"><span data-stu-id="3b9a0-106">Syntax for instantiating a `UriTemplateTable`.</span></span>  
  
-   <span data-ttu-id="3b9a0-107">Remplissage de `UriTemplateTable` avec un jeu de paires clé/valeur.</span><span class="sxs-lookup"><span data-stu-id="3b9a0-107">Populating a `UriTemplateTable` with a set of key/value pairs.</span></span>  
  
-   <span data-ttu-id="3b9a0-108">Mise en correspondance d'un URI candidat avec la table à l'aide de <xref:System.UriTemplateTable.MatchSingle%2A>.</span><span class="sxs-lookup"><span data-stu-id="3b9a0-108">Matching a candidate URI against the table using <xref:System.UriTemplateTable.MatchSingle%2A>.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="3b9a0-109">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="3b9a0-109">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="3b9a0-110">Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3b9a0-110">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2.  <span data-ttu-id="3b9a0-111">Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [en cours d’exécution les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3b9a0-111">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="3b9a0-112">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="3b9a0-112">The samples may already be installed on your computer.</span></span> <span data-ttu-id="3b9a0-113">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="3b9a0-113">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="3b9a0-114">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="3b9a0-114">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="3b9a0-115">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="3b9a0-115">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\UriTemplateTable`  
  
## <a name="see-also"></a><span data-ttu-id="3b9a0-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3b9a0-116">See Also</span></span>  
 [<span data-ttu-id="3b9a0-117">Répartiteur de table UriTemplate</span><span class="sxs-lookup"><span data-stu-id="3b9a0-117">UriTemplate Table Dispatcher</span></span>](../../../../docs/framework/wcf/samples/uritemplate-table-dispatcher-sample.md)  
 [<span data-ttu-id="3b9a0-118">UriTemplate</span><span class="sxs-lookup"><span data-stu-id="3b9a0-118">UriTemplate</span></span>](../../../../docs/framework/wcf/samples/uritemplate-sample.md)
