---
title: "Isolement réseau pour les applications du Windows Store"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b064497c-d956-46b8-838d-7a0223c7e200
caps.latest.revision: "7"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: ba7e480f50d3a339648229f17152eb28b28ec159
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="network-isolation-for-windows-store-apps"></a><span data-ttu-id="599de-102">Isolement réseau pour les applications du Windows Store</span><span class="sxs-lookup"><span data-stu-id="599de-102">Network Isolation for Windows Store Apps</span></span>
<span data-ttu-id="599de-103">Les classes des espaces de noms <xref:System.Net>, <xref:System.Net.Http> et <xref:System.Net.Http.Headers> peuvent être utilisées pour développer des applications Windows Store et des applications de bureau.</span><span class="sxs-lookup"><span data-stu-id="599de-103">Classes in the <xref:System.Net>,  <xref:System.Net.Http>, and <xref:System.Net.Http.Headers> namespaces can be used to develop Windows Store  apps  or desktop apps.</span></span> <span data-ttu-id="599de-104">Lorsqu’elles sont utilisées dans une application du Windows Store, les classes de ces espaces de noms sont affectées par l’isolement réseau, qui fait partie du modèle de sécurité des applications utilisé par [!INCLUDE[win8](../../../includes/win8-md.md)].</span><span class="sxs-lookup"><span data-stu-id="599de-104">When used in a Windows Store app, classes in these namespaces are affected by network isolation, part of the application security model used by the [!INCLUDE[win8](../../../includes/win8-md.md)].</span></span> <span data-ttu-id="599de-105">Les fonctionnalités réseau appropriées doivent être activées dans le manifeste d’une application du Windows Store pour que le système autorise l’accès réseau.</span><span class="sxs-lookup"><span data-stu-id="599de-105">The appropriate network capabilities must be enabled in the app manifest for a Windows Store app for the system to allow network access.</span></span>  
  
## <a name="checklist-for-network-isolation"></a><span data-ttu-id="599de-106">Liste de vérification pour l’isolement réseau</span><span class="sxs-lookup"><span data-stu-id="599de-106">Checklist for Network Isolation</span></span>  
 <span data-ttu-id="599de-107">Utilisez cette liste de vérification pour vérifier que l’isolement réseau est configuré pour votre application du Windows Store.</span><span class="sxs-lookup"><span data-stu-id="599de-107">Use this checklist to be sure that network isolation is configured for your Windows Store app.</span></span>  
  
1.  <span data-ttu-id="599de-108">Déterminez la direction des requêtes d’accès réseau dont a besoin l’application.</span><span class="sxs-lookup"><span data-stu-id="599de-108">Determine the direction of network access requests needed by the app.</span></span> <span data-ttu-id="599de-109">Il peut s’agir de requêtes sortantes lancées par le client, de requêtes entrantes non sollicitées, ou d’une combinaison de ces deux types de requêtes réseau.</span><span class="sxs-lookup"><span data-stu-id="599de-109">This can be either outbound client-initiated requests or inbound unsolicited requests or it could be a combination of both of these network request types.</span></span>  
  
2.  <span data-ttu-id="599de-110">Déterminez le type de ressources réseau avec lesquelles l’application va communiquer.</span><span class="sxs-lookup"><span data-stu-id="599de-110">Determine the type of network resources that that app will communicate with.</span></span> <span data-ttu-id="599de-111">Une application peut avoir besoin de communiquer avec des ressources approuvées appartenant à un réseau domestique ou d’entreprise.</span><span class="sxs-lookup"><span data-stu-id="599de-111">An app may need to communicate with trusted resources on a Home or Work network.</span></span> <span data-ttu-id="599de-112">Une application peut avoir besoin de communiquer avec des ressources Internet.</span><span class="sxs-lookup"><span data-stu-id="599de-112">An app might need to communicate with resources on the Internet.</span></span> <span data-ttu-id="599de-113">Une application peut avoir besoin d’accéder à ces deux types de ressources réseau.</span><span class="sxs-lookup"><span data-stu-id="599de-113">An app might need access to both types of network resources.</span></span>  
  
3.  <span data-ttu-id="599de-114">Configurez les fonctionnalités d’isolement réseau minimales dans le manifeste d’application.</span><span class="sxs-lookup"><span data-stu-id="599de-114">Configure the minimum-required networking isolation capabilities in the app manifest.</span></span>  
  
4.  <span data-ttu-id="599de-115">Déployez et exécutez votre application pour la tester à l’aide des outils d’isolement réseau fournis pour la résolution des problèmes.</span><span class="sxs-lookup"><span data-stu-id="599de-115">Deploy and run your app to test it using the network isolation tools provided for troubleshooting.</span></span>  
  
 <span data-ttu-id="599de-116">Pour plus d’informations sur la configuration des fonctionnalités réseau et des outils utilisés pour le dépannage de l’isolement réseau, consultez [Comment définir les fonctionnalités réseau (HTML)](http://go.microsoft.com/fwlink/?LinkID=228265) dans la documentation du développeur de [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="599de-116">For more detailed information on how to configure network capabilities and isolation tools used for troubleshooting network isolation, see [How to configure network isolation capabilities](http://go.microsoft.com/fwlink/?LinkID=228265) in the [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] developer documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="599de-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="599de-117">See Also</span></span>  
 [<span data-ttu-id="599de-118">Connexion à un service web</span><span class="sxs-lookup"><span data-stu-id="599de-118">Connecting to a web service</span></span>](http://go.microsoft.com/fwlink/?LinkID=245696)  
 [<span data-ttu-id="599de-119">Instructions et liste de vérification pour l’isolement réseau</span><span class="sxs-lookup"><span data-stu-id="599de-119">Guidelines and checklist for network isolation</span></span>](http://go.microsoft.com/fwlink/?LinkID=228265)  
 [<span data-ttu-id="599de-120">Démarrage rapide : Connexion à l’aide de HttpClient</span><span class="sxs-lookup"><span data-stu-id="599de-120">Quickstart: Connecting using HttpClient</span></span>](http://go.microsoft.com/fwlink/?LinkId=245697)  
 [<span data-ttu-id="599de-121">L’utilisation des gestionnaires de HttpClient</span><span class="sxs-lookup"><span data-stu-id="599de-121">How to use HttpClient handlers</span></span>](http://go.microsoft.com/fwlink/?LinkId=245699)  
 [<span data-ttu-id="599de-122">Comment sécuriser les connexions client HTTP</span><span class="sxs-lookup"><span data-stu-id="599de-122">How to secure HttpClient connections</span></span>](http://go.microsoft.com/fwlink/?LinkId=245698)  
 [<span data-ttu-id="599de-123">Exemple HttpClient</span><span class="sxs-lookup"><span data-stu-id="599de-123">HttpClient Sample</span></span>](http://go.microsoft.com/fwlink/?LinkId=242550)
