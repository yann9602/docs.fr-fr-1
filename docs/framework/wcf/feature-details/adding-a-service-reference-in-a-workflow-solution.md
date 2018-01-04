---
title: "Ajout d'une référence de service dans une solution de workflow"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 83574cf3-9803-49bc-837f-432936dc9c76
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ee974ee5a9f4564b0e44256bc4773f9898d89fc6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="adding-a-service-reference-in-a-workflow-solution"></a><span data-ttu-id="976ed-102">Ajout d'une référence de service dans une solution de workflow</span><span class="sxs-lookup"><span data-stu-id="976ed-102">Adding a Service Reference in a Workflow Solution</span></span>
<span data-ttu-id="976ed-103">L'ajout d'une référence de service dans une application de workflow fonctionne de façon légèrement différente que dans une application WCF normale.</span><span class="sxs-lookup"><span data-stu-id="976ed-103">Adding a service reference in a workflow application works a little differently than a regular WCF application.</span></span> <span data-ttu-id="976ed-104">Lorsque vous sélectionnez Ajouter une référence de service et lorsque vous spécifiez l'URL du service, les métadonnées sont téléchargées et les activités personnalisées sont générées pour vous permettre d'appeler le service WCF ou le service de workflow WCF auquel vous avez ajouté une référence.</span><span class="sxs-lookup"><span data-stu-id="976ed-104">When you select Add Service Reference and specify the URL to the service the metadata is downloaded and custom activities are generated that allow you to call the WCF service or WCF workflow service you added a reference to.</span></span> <span data-ttu-id="976ed-105">Après l'ajout d'une référence de service, régénérez la solution pour que les activités générées soient construites.</span><span class="sxs-lookup"><span data-stu-id="976ed-105">After adding a service reference, rebuild the solution so the generated activities are built.</span></span> <span data-ttu-id="976ed-106">Celles-ci vont ensuite apparaître dans la boîte à outils du concepteur de workflow.</span><span class="sxs-lookup"><span data-stu-id="976ed-106">They will then appear in the workflow designer toolbox.</span></span> <span data-ttu-id="976ed-107">Notez toutefois que cela ne fonctionne que si vous ajoutez une référence de service dans une solution de workflow.</span><span class="sxs-lookup"><span data-stu-id="976ed-107">Note however, that this will only work if you are adding a service reference within a workflow solution.</span></span> <span data-ttu-id="976ed-108">Le cast web suivant montre comment ajouter une référence de service dans d’autres types de projets : [appeler un Service WCF à partir d’un flux de travail dans un projet Web](http://go.microsoft.com/fwlink/?LinkId=207725).</span><span class="sxs-lookup"><span data-stu-id="976ed-108">The following web cast shows how to add a service reference in other types of projects: [Calling a WCF Service from a Workflow in a Web Project](http://go.microsoft.com/fwlink/?LinkId=207725).</span></span>  
  
 <span data-ttu-id="976ed-109">L'ajout de deux ou plus références de service aux services qui contiennent le même nom d'opération entraîne un problème.</span><span class="sxs-lookup"><span data-stu-id="976ed-109">Adding two or more service references to services that contain the same operation name will cause a problem.</span></span> <span data-ttu-id="976ed-110">Les activités générées vont appeler uniquement la première opération de service.</span><span class="sxs-lookup"><span data-stu-id="976ed-110">The generated activities will call only the first service operation.</span></span> <span data-ttu-id="976ed-111">Pour contourner ce problème, il faut renommer les opérations de service avec des noms différents ou modifier le nom de la configuration de point de terminaison dans chaque activité générée.</span><span class="sxs-lookup"><span data-stu-id="976ed-111">To work around this issue rename the service operations so they are different or change the endpoint configuration name within each generated activity.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="976ed-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="976ed-112">See Also</span></span>  
 [<span data-ttu-id="976ed-113">Services de workflow</span><span class="sxs-lookup"><span data-stu-id="976ed-113">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [<span data-ttu-id="976ed-114">Guide pratique pour créer un service de workflow qui appelle un autre service de workflow</span><span class="sxs-lookup"><span data-stu-id="976ed-114">How to: Create a Workflow Service That Calls Another Workflow Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-that-calls-another-workflow-service.md)  
 [<span data-ttu-id="976ed-115">Appeler un Service WCF à partir d’un flux de travail dans un projet Web</span><span class="sxs-lookup"><span data-stu-id="976ed-115">Calling a WCF Service from a Workflow in a Web Project</span></span>](http://go.microsoft.com/fwlink/?LinkId=207725)
