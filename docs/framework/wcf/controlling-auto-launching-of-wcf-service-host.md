---
title: "Contrôle de l'auto-lancement de l'hôte de service WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: WcfOptions
ms.assetid: 6abe5d34-519b-4cef-8f02-3c0a7f125585
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: dc89ed3ae41471af49fc92f31834f0ae268309dd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="controlling-auto-launching-of-wcf-service-host"></a><span data-ttu-id="59766-102">Contrôle de l'auto-lancement de l'hôte de service WCF</span><span class="sxs-lookup"><span data-stu-id="59766-102">Controlling Auto-launching of WCF Service Host</span></span>
<span data-ttu-id="59766-103">Vous pouvez contrôler la fonction d'auto-lancement de l'hôte du service [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] (WcfSvcHost.exe) pour un projet de bibliothèque du service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] lorsque vous déboguez un autre projet dans la même solution [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] contenant plusieurs projets.</span><span class="sxs-lookup"><span data-stu-id="59766-103">You can control the auto-launching capability of [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] Service Host (WcfSvcHost.exe) for a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Service Library project, when you debug another project in the same [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] solution containing multiple projects.</span></span>  
  
 <span data-ttu-id="59766-104">Pour ce faire, cliquez sur le [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] projet de Service dans **l’Explorateur de solutions**, choisissez **propriétés**, puis cliquez sur **Options WCF** onglet. Le **démarrer WCF Service hôte lors du débogage d’un autre projet dans la même solution** case à cocher est activée par défaut.</span><span class="sxs-lookup"><span data-stu-id="59766-104">To do so, right-click the [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Service Project in **Solution Explorer**, choose **Properties**, and click **WCF Options** tab. The **Start WCF Service Host when debugging another project in the same solution** check box is enabled by default.</span></span> <span data-ttu-id="59766-105">Vous pouvez la désactiver afin que l'hôte du service [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] de ce projet spécifique ne démarre pas lorsqu'un autre projet est débogué dans la même solution.</span><span class="sxs-lookup"><span data-stu-id="59766-105">You can clear the box so that [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Service Host for this specific project is not launched when another project is debugged in the same solution.</span></span>  
  
 <span data-ttu-id="59766-106">Ce comportement n'affecte pas le débogage F5 ni les fonctionnalités d'ajout d'une référence de service pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="59766-106">This behavior does not affect the F5 debugging, or Add Service Reference functionalities for this project.</span></span>  
  
 <span data-ttu-id="59766-107">Cette option est disponible dans le cadre des projets suivants :</span><span class="sxs-lookup"><span data-stu-id="59766-107">This option is available to the following projects:</span></span>  
  
-   [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]<span data-ttu-id="59766-108"> Projet de la bibliothèque du service</span><span class="sxs-lookup"><span data-stu-id="59766-108"> Service Library Project.</span></span>  
  
-   <span data-ttu-id="59766-109">Projet de la bibliothèque du service du workflow séquentiel</span><span class="sxs-lookup"><span data-stu-id="59766-109">Sequential Workflow Service Library Project.</span></span>  
  
-   <span data-ttu-id="59766-110">Projet de la bibliothèque du service de workflow d'ordinateur d'état</span><span class="sxs-lookup"><span data-stu-id="59766-110">State Machine Workflow Service Library Project.</span></span>  
  
-   <span data-ttu-id="59766-111">Projet de la bibliothèque du service de syndication</span><span class="sxs-lookup"><span data-stu-id="59766-111">Syndication Service Library Project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59766-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="59766-112">See Also</span></span>  
 [<span data-ttu-id="59766-113">WCF Service Host (WcfSvcHost.exe)</span><span class="sxs-lookup"><span data-stu-id="59766-113">WCF Service Host (WcfSvcHost.exe)</span></span>](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)
