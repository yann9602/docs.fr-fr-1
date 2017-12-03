---
title: Journalisation des messages
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6bce0682-75ef-4d65-a659-b328fba4a8b5
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a771cbc22febf966fec2cf608a9b59204fc6e51a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="message-logging"></a><span data-ttu-id="24415-102">Journalisation des messages</span><span class="sxs-lookup"><span data-stu-id="24415-102">Message Logging</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="24415-103"> intègre une fonctionnalité permettant d'enregistrer les messages entrants et sortants afin de pouvoir les utiliser hors ligne.</span><span class="sxs-lookup"><span data-stu-id="24415-103"> provides the capability to log incoming and outgoing messages for offline consumption.</span></span> <span data-ttu-id="24415-104">L'enregistrement des messages dans des journaux vous permet de voir à quoi ils ressemblent et à quoi ressemble le corps de ces messages.</span><span class="sxs-lookup"><span data-stu-id="24415-104">Message logging enables you to see what the message and message body looks like.</span></span> <span data-ttu-id="24415-105">Ce type d'enregistrement est particulièrement utile car il vous permet de savoir quels arguments ont été passés et de connaître la manière dont le point de terminaison destinataire a perçu les arguments exprimés en langage XML.</span><span class="sxs-lookup"><span data-stu-id="24415-105">This type of logging is particularly helpful in letting you know what arguments were passed in and how the receiving endpoint saw the arguments expressed as XML.</span></span> <span data-ttu-id="24415-106">En outre, l'enregistrement des messages tels qu'ils ont été reçus vous permet d'identifier les messages erronés et de voir la manière dont les messages sont arrivés.</span><span class="sxs-lookup"><span data-stu-id="24415-106">In addition, logging the message as it was received allows you to diagnose malformed messages as well as to see how the message arrived.</span></span> <span data-ttu-id="24415-107">Dans ces journaux, vous pouvez également examiner les jetons de sécurité utilisés, les parties chiffrées et signées ainsi que les parties laissées telles quelles.</span><span class="sxs-lookup"><span data-stu-id="24415-107">You can also examine the security tokens used, parts encrypted and signed, and parts left intact.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="24415-108">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="24415-108">In This Section</span></span>  
 [<span data-ttu-id="24415-109">Vue d’ensemble du flux de message</span><span class="sxs-lookup"><span data-stu-id="24415-109">Message Flow Overview</span></span>](../../../../docs/framework/wcf/diagnostics/message-flow-overview.md)  
  
 <span data-ttu-id="24415-110">Cette rubrique décrit la façon dont les messages du journal d'événements correspondent aux événements du client et du service.</span><span class="sxs-lookup"><span data-stu-id="24415-110">This topic describes how event log messages correspond to client and service events.</span></span>  
  
 [<span data-ttu-id="24415-111">Configuration de la journalisation de Message</span><span class="sxs-lookup"><span data-stu-id="24415-111">Configuring Message Logging</span></span>](../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md)  
  
 <span data-ttu-id="24415-112">Cette rubrique contient des instructions permettant de configurer l'enregistrement des messages en fonction de différentes situations.</span><span class="sxs-lookup"><span data-stu-id="24415-112">This topic describes how you can configure message logging for different scenarios.</span></span>  
  
 [<span data-ttu-id="24415-113">Affichage des journaux de messages</span><span class="sxs-lookup"><span data-stu-id="24415-113">Viewing Message Logs</span></span>](../../../../docs/framework/wcf/diagnostics/viewing-message-logs.md)  
  
 <span data-ttu-id="24415-114">Cette rubrique contient des instructions permettant d'afficher les journaux des messages.</span><span class="sxs-lookup"><span data-stu-id="24415-114">This topic describes how you can view message logs.</span></span>  
  
 [<span data-ttu-id="24415-115">Problèmes de sécurité pour la journalisation des messages</span><span class="sxs-lookup"><span data-stu-id="24415-115">Security Concerns for Message Logging</span></span>](../../../../docs/framework/wcf/diagnostics/security-concerns-for-message-logging.md)  
  
 <span data-ttu-id="24415-116">Cette rubrique contient des instructions permettant de protéger des données sensibles afin d'éviter qu'elles ne soient visibles dans les journaux des messages et de protéger les événements générés par l'enregistrement des messages.</span><span class="sxs-lookup"><span data-stu-id="24415-116">This topic describes how you can protect sensitive data from being exposed in message logs, as well as events generated by message logging.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24415-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="24415-117">See Also</span></span>  
 [<span data-ttu-id="24415-118">Administration et diagnostics</span><span class="sxs-lookup"><span data-stu-id="24415-118">Administration and Diagnostics</span></span>](../../../../docs/framework/wcf/diagnostics/index.md)
