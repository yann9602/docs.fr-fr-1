---
title: "Quand ne pas déployer des conteneurs Windows"
description: "Architecture de Microservices .NET pour les Applications .NET en conteneur | Quand ne pas déployer des conteneurs Windows"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.openlocfilehash: 538cb518cd169f42b3e8b7324ca108a1d366137a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="when-not-to-deploy-to-windows-containers"></a><span data-ttu-id="ec20c-103">Quand ne pas déployer des conteneurs Windows</span><span class="sxs-lookup"><span data-stu-id="ec20c-103">When not to deploy to Windows Containers</span></span>

<span data-ttu-id="ec20c-104">Certaines technologies de Windows ne sont pas pris en charge par les conteneurs Windows.</span><span class="sxs-lookup"><span data-stu-id="ec20c-104">Some Windows technologies are not supported by Windows Containers.</span></span> <span data-ttu-id="ec20c-105">Dans ce cas, vous devrez migrer vers les machines virtuelles aux normes, généralement avec Windows et de IIS.</span><span class="sxs-lookup"><span data-stu-id="ec20c-105">In those cases, you still need to migrate to standards VMs, usually with just Windows and IIS.</span></span>

<span data-ttu-id="ec20c-106">Cas non pris en charge dans les conteneurs Windows, à compter de mid 2017 :</span><span class="sxs-lookup"><span data-stu-id="ec20c-106">Cases not supported in Windows Containers, as of mid-2017:</span></span>

-   <span data-ttu-id="ec20c-107">Microsoft Message Queuing (MSMQ) actuellement n’est pas pris en charge dans les conteneurs Windows.</span><span class="sxs-lookup"><span data-stu-id="ec20c-107">Microsoft Message Queuing (MSMQ) currently is not supported in Windows Containers.</span></span>

    -   [<span data-ttu-id="ec20c-108">Forum sur la demande UserVoice</span><span class="sxs-lookup"><span data-stu-id="ec20c-108">UserVoice request forum</span></span>](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/15719031-create-base-container-image-with-msmq-server)

    -   [<span data-ttu-id="ec20c-109">Forum de discussion</span><span class="sxs-lookup"><span data-stu-id="ec20c-109">Discussion forum</span></span>](https://social.msdn.microsoft.com/Forums/bce99a7d-aa60-44fa-a348-450855650810/msmqserver-is-it-supported?forum=windowscontainers)

-   <span data-ttu-id="ec20c-110">Microsoft Distributed Transaction Coordinator (MSDTC) en n'est pas pris en charge dans les conteneurs Windows</span><span class="sxs-lookup"><span data-stu-id="ec20c-110">Microsoft Distributed Transaction Coordinator (MSDTC) currently is not supported in Windows Containers</span></span>

    -   [<span data-ttu-id="ec20c-111">Problème GitHub</span><span class="sxs-lookup"><span data-stu-id="ec20c-111">GitHub issue</span></span>](https://github.com/MicrosoftDocs/Virtualization-Documentation/issues/494)

-   <span data-ttu-id="ec20c-112">Microsoft Office ne prend actuellement pas en charge les conteneurs</span><span class="sxs-lookup"><span data-stu-id="ec20c-112">Microsoft Office currently does not support containers</span></span>

    -   [<span data-ttu-id="ec20c-113">Forum sur la demande UserVoice</span><span class="sxs-lookup"><span data-stu-id="ec20c-113">UserVoice request forum</span></span>](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/19686220-provide-office-support-for-containers)

<span data-ttu-id="ec20c-114">Pour les requêtes à partir de la Communauté et d’autres scénarios non pris en charge, consultez le forum UserVoice pour les conteneurs Windows : <https://windowsserver.uservoice.com/forums/304624-containers>.</span><span class="sxs-lookup"><span data-stu-id="ec20c-114">For additional not-supported scenarios and requests from the community, see the UserVoice forum for Windows Containers: <https://windowsserver.uservoice.com/forums/304624-containers>.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="ec20c-115">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="ec20c-115">Additional resources</span></span>

-   <span data-ttu-id="ec20c-116">**Machines virtuelles et les conteneurs dans Azure**</span><span class="sxs-lookup"><span data-stu-id="ec20c-116">**Virtual machines and containers in Azure**</span></span>

    [<span data-ttu-id="ec20c-117">https://docs.Microsoft.com/Azure/Virtual-machines/Windows/Containers</span><span class="sxs-lookup"><span data-stu-id="ec20c-117">https://docs.microsoft.com/azure/virtual-machines/windows/containers</span></span>](https://docs.microsoft.com/azure/virtual-machines/windows/containers)

>[!div class="step-by-step"]
<span data-ttu-id="ec20c-118">[Précédent](deploy-existing-net-apps-as-windows-containers.md)
[Suivant](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)</span><span class="sxs-lookup"><span data-stu-id="ec20c-118">[Previous](deploy-existing-net-apps-as-windows-containers.md)
[Next](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)</span></span>
