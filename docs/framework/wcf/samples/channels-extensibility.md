---
title: "Extensibilité des canaux"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4cc3b20b-778a-4ae8-b58c-a3822fb13065
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bcda7f9edc741e8f0c9c56214119255ca2777d77
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="channels-extensibility"></a><span data-ttu-id="4fdb3-102">Extensibilité des canaux</span><span class="sxs-lookup"><span data-stu-id="4fdb3-102">Channels Extensibility</span></span>
<span data-ttu-id="4fdb3-103">Cette section contient des exemples qui illustrent des canaux personnalisés.</span><span class="sxs-lookup"><span data-stu-id="4fdb3-103">This section contains samples that demonstrate custom channels.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4fdb3-104">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="4fdb3-104">In This Section</span></span>  
 [<span data-ttu-id="4fdb3-105">Canal local</span><span class="sxs-lookup"><span data-stu-id="4fdb3-105">Local Channel</span></span>](../../../../docs/framework/wcf/samples/local-channel.md)  
 <span data-ttu-id="4fdb3-106">Illustre le canal local, un canal du transport [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] utilisé pour la communication dans un même domaine d'application.</span><span class="sxs-lookup"><span data-stu-id="4fdb3-106">Demonstrates the local channel, a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] transport channel that is used for communication within the same application domain.</span></span>  
  
 [<span data-ttu-id="4fdb3-107">Profil de sécurité fiable</span><span class="sxs-lookup"><span data-stu-id="4fdb3-107">Reliable Secure Profile</span></span>](../../../../docs/framework/wcf/samples/reliable-secure-profile.md)  
 <span data-ttu-id="4fdb3-108">Montre comment agencer [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] et Reliable Secure Profile (RSP).</span><span class="sxs-lookup"><span data-stu-id="4fdb3-108">Demonstrates how to compose [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] and Reliable Secure Profile (RSP).</span></span>  
  
 [<span data-ttu-id="4fdb3-109">Répartiteur de canal personnalisé</span><span class="sxs-lookup"><span data-stu-id="4fdb3-109">Custom Channel Dispatcher</span></span>](../../../../docs/framework/wcf/samples/custom-channel-dispatcher.md)  
 <span data-ttu-id="4fdb3-110">Montre comment générer la pile de canaux de façon personnalisée en implémentant <xref:System.ServiceModel.ServiceHostBase> directement et comment créer un répartiteur de canal personnalisé dans un environnement avec hôte Web.</span><span class="sxs-lookup"><span data-stu-id="4fdb3-110">Demonstrates how to build the channel stack in a custom way by implementing <xref:System.ServiceModel.ServiceHostBase> directly and how to create a custom channel dispatcher in Web host environment.</span></span>  
  
 [<span data-ttu-id="4fdb3-111">Canal de segmentation</span><span class="sxs-lookup"><span data-stu-id="4fdb3-111">Chunking Channel</span></span>](../../../../docs/framework/wcf/samples/chunking-channel.md)  
 <span data-ttu-id="4fdb3-112">Montre comment limiter la mémoire utilisée pour mettre en mémoire tampon des messages volumineux envoyés à l'aide de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4fdb3-112">Demonstrates how to limit the amount of memory used to buffer large messages sent using [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
 [<span data-ttu-id="4fdb3-113">Canal d’accusé de réception HTTP</span><span class="sxs-lookup"><span data-stu-id="4fdb3-113">HTTP Acknowledgement Channel</span></span>](../../../../docs/framework/wcf/samples/http-acknowledgement-channel.md)  
 <span data-ttu-id="4fdb3-114">Illustre un canal superposé qui modifie le modèle de messagerie unidirectionnel.</span><span class="sxs-lookup"><span data-stu-id="4fdb3-114">Demonstrates a layered channel which changes the one-way messaging pattern.</span></span>  
  
 [<span data-ttu-id="4fdb3-115">HttpCookieSession</span><span class="sxs-lookup"><span data-stu-id="4fdb3-115">HttpCookieSession</span></span>](../../../../docs/framework/wcf/samples/httpcookiesession.md)  
 <span data-ttu-id="4fdb3-116">Montre comment générer un canal de protocole personnalisé pour utiliser des cookies HTTP pour la gestion des sessions.</span><span class="sxs-lookup"><span data-stu-id="4fdb3-116">Demonstrates how to build a custom protocol channel to use HTTP cookies for session management.</span></span>  
  
 [<span data-ttu-id="4fdb3-117">Intercepteur de Message personnalisé</span><span class="sxs-lookup"><span data-stu-id="4fdb3-117">Custom Message Interceptor</span></span>](../../../../docs/framework/wcf/samples/custom-message-interceptor.md)  
 <span data-ttu-id="4fdb3-118">Montre comment implémenter un élément de liaison personnalisé qui crée des fabriques et des écouteurs de canaux pour intercepter tous les messages entrants et sortants à un point spécifique de la pile d’exécution.</span><span class="sxs-lookup"><span data-stu-id="4fdb3-118">Demonstrates how to implement a custom binding element that creates channel factories and channel listeners to intercept all incoming and outgoing messages at a particular point in the run-time stack.</span></span>
