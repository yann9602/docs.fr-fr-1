---
title: "Comment : activer le service de partage de ports Net.TCP"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- port sharing [WCF]
- activation services [WCF]
ms.assetid: c9175af4-c27c-4765-bf45-b8f7528a7282
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b9f1c57f067fa7c8bece3acaf0d51303b31d13bf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-enable-the-nettcp-port-sharing-service"></a><span data-ttu-id="27efe-102">Comment : activer le service de partage de ports Net.TCP</span><span class="sxs-lookup"><span data-stu-id="27efe-102">How to: Enable the Net.TCP Port Sharing Service</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="27efe-103"> utilise un service Windows appelé Service de partage de ports Net.TCP pour faciliter le partage des ports TCP à travers des processus multiples.</span><span class="sxs-lookup"><span data-stu-id="27efe-103"> uses a Windows service called the Net.TCP Port Sharing Service to facilitate the sharing of TCP ports across multiple processes.</span></span> <span data-ttu-id="27efe-104">Ce service est installé dans [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], mais n'est pas activé par défaut par mesure de sécurité et doit être activé manuellement avant la première utilisation.</span><span class="sxs-lookup"><span data-stu-id="27efe-104">This service is installed as part of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], but the service is not enabled by default as a security precaution and so must be manually enabled prior to first use.</span></span> <span data-ttu-id="27efe-105">Cette rubrique décrit comment configurer le service de partage de ports Net.TCP à l'aide du composant logiciel enfichable Microsoft Management Console (MMC).</span><span class="sxs-lookup"><span data-stu-id="27efe-105">This topic describes how to configure the Net TCP Port Sharing Service using the Microsoft Management Console (MMC) snap-In.</span></span>  
  
 <span data-ttu-id="27efe-106">Après avoir activé le Service de partage de ports Net.TCP et que vous démarrez manuellement, consultez [Comment : configurer un Service WCF à utiliser le partage de Port](../../../../docs/framework/wcf/feature-details/how-to-configure-a-wcf-service-to-use-port-sharing.md) pour plus d’informations sur la façon de configurer votre service pour utiliser ce service.</span><span class="sxs-lookup"><span data-stu-id="27efe-106">After you enable the Net.TCP Port Sharing Service and start it manually, see [How to: Configure a WCF Service to Use Port Sharing](../../../../docs/framework/wcf/feature-details/how-to-configure-a-wcf-service-to-use-port-sharing.md) for information about how to configure your service to use this service.</span></span>  
  
 <span data-ttu-id="27efe-107">Pour voir un exemple qui utilise le partage de ports net.tcp://, le [Net.TCP Port Sharing, exemple](../../../../docs/framework/wcf/samples/net-tcp-port-sharing-sample.md).</span><span class="sxs-lookup"><span data-stu-id="27efe-107">For a sample that uses net.tcp:// port sharing, see the [Net.TCP Port Sharing Sample](../../../../docs/framework/wcf/samples/net-tcp-port-sharing-sample.md).</span></span>  
  
### <a name="to-enable-the-nettcp-port-sharing-service-using-mmc"></a><span data-ttu-id="27efe-108">Pour activer le service de partage de ports Net.TCP à l'aide de MMC</span><span class="sxs-lookup"><span data-stu-id="27efe-108">To enable the Net.TCP Port Sharing Service using MMC</span></span>  
  
1.  <span data-ttu-id="27efe-109">Dans le menu Démarrer, ouvrez la Console de gestion de Services soit en ouvrant une fenêtre d’invite de commandes et en tapant `services.msc` ou en sélectionnant exécuter et en tapant `services.msc` dans la zone Ouvrir.</span><span class="sxs-lookup"><span data-stu-id="27efe-109">From the Start menu, open the Services Management Console either by opening a Command Prompt window and typing `services.msc` or by opening Run and typing `services.msc` into the Open box.</span></span>  
  
2.  <span data-ttu-id="27efe-110">Dans le **nom** avec le bouton droit de la colonne de la liste des services, le **Service de partage de Port Net.Tcp**, puis sélectionnez **propriétés** à partir du menu.</span><span class="sxs-lookup"><span data-stu-id="27efe-110">In the **Name** column of the list of services, right-click the **Net.Tcp Port Sharing Service**, and select **Properties** from the menu.</span></span>  
  
3.  <span data-ttu-id="27efe-111">Pour permettre le démarrage manuel du service, dans le **propriétés** fenêtre Sélectionner le **général** onglet et dans le **type de démarrage** zone Sélectionnez manuel, puis cliquez sur **Appliquer**.</span><span class="sxs-lookup"><span data-stu-id="27efe-111">To enable the manual start-up of the service, in the **Properties** window select the **General** tab, and in the **Startup type** box select Manual, and then click **Apply**.</span></span>  
  
4.  <span data-ttu-id="27efe-112">Pour démarrer le service, dans la zone d’état de Service, cliquez sur le **Démarrer** bouton.</span><span class="sxs-lookup"><span data-stu-id="27efe-112">To start the service,  in the Service status area, click the **Start** button.</span></span> <span data-ttu-id="27efe-113">L'état du service doit maintenant afficher "Démarré".</span><span class="sxs-lookup"><span data-stu-id="27efe-113">The service status should now display "Started".</span></span>  
  
5.  <span data-ttu-id="27efe-114">Pour revenir à la liste des services, cliquez sur le **OK**, quittez la Console MMC.</span><span class="sxs-lookup"><span data-stu-id="27efe-114">To return to the list of services, click the **OK**, and exit the MMC Console.</span></span>  
  
## <a name="example"></a><span data-ttu-id="27efe-115">Exemple</span><span class="sxs-lookup"><span data-stu-id="27efe-115">Example</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27efe-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="27efe-116">See Also</span></span>  
 [<span data-ttu-id="27efe-117">Partage de ports Net.TCP</span><span class="sxs-lookup"><span data-stu-id="27efe-117">Net.TCP Port Sharing</span></span>](../../../../docs/framework/wcf/feature-details/net-tcp-port-sharing.md)  
 [<span data-ttu-id="27efe-118">Configuration du service de partage de ports Net.TCP</span><span class="sxs-lookup"><span data-stu-id="27efe-118">Configuring the Net.TCP Port Sharing Service</span></span>](../../../../docs/framework/wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md)
