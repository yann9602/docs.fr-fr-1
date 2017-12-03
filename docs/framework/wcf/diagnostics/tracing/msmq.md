---
title: MSMQ
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d9fca29f-fa44-4ec4-bb48-b10800694500
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 15be4b6bfb84a0aa843e3d62861a9195e125a04e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="msmq"></a><span data-ttu-id="09f1c-102">MSMQ</span><span class="sxs-lookup"><span data-stu-id="09f1c-102">MSMQ</span></span>
<span data-ttu-id="09f1c-103">Dans une application MSMQ, aucune activité supplémentaire n'est transférée du canal mis en file d'attente vers MSMQ et de MSMQ vers le canal mis en file d'attente.</span><span class="sxs-lookup"><span data-stu-id="09f1c-103">In an MSMQ application, no additional activity is transferred from the queued channel to MSMQ and from MSMQ to the queued channel.</span></span>  
  
 <span data-ttu-id="09f1c-104">De plus, l'ID de message MSMQ et l'ID de message SOAP (ainsi que l'ID d'activité, s'il existe) sont suivis dans le cadre des suivis de canaux mis en file d'attente lors d'une opération d'envoi.</span><span class="sxs-lookup"><span data-stu-id="09f1c-104">In addition, MSMQ Message ID and SOAP message ID (along with Activity ID, if one exists) are traced as part of queued channel traces on a Send operation.</span></span>  
  
 <span data-ttu-id="09f1c-105">L'ID de message MSMQ et l'ID de message SOAP (ainsi que l'ID d'activité, s'il existe) sont suivis dans le cadre des suivis de canaux mis en file d'attente lors d'une opération de réception.</span><span class="sxs-lookup"><span data-stu-id="09f1c-105">MSMQ Message ID and SOAP message ID (along with activity ID, if one exists) are traced as part of queued channel traces on a Receive operation.</span></span>  
  
 <span data-ttu-id="09f1c-106">Les transferts requis au cours de l'opération de réception sont exécutés de la même façon que tout autre transport (réception d'octets->traitement du message->opération).</span><span class="sxs-lookup"><span data-stu-id="09f1c-106">The required transfers on the Receive operation are executed similarly to any other transport (receive bytes->Process message-> operation).</span></span>
