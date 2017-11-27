---
title: "Scénarios synchrones utilisant HTTP, TCP ou Canal nommé"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a4d62402-43a4-48a4-9ced-220633ebc4ce
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c697069aad590013ff360eb6ee4cba39468b89d5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="asynchronous-scenarios-using-http-tcp-or-named-pipe"></a><span data-ttu-id="6b419-102">Scénarios synchrones utilisant HTTP, TCP ou Canal nommé</span><span class="sxs-lookup"><span data-stu-id="6b419-102">Asynchronous Scenarios using HTTP, TCP, or Named-Pipe</span></span>
<span data-ttu-id="6b419-103">Cette rubrique décrit les activités et transferts pour différents scénarios de demande/réponse asynchrones, avec des demandes multithread utilisant une connexion HTTP, TCP ou de canal nommé.</span><span class="sxs-lookup"><span data-stu-id="6b419-103">This topic describes the activities and transfers for different asynchronous request/reply scenarios, with multithreaded requests using HTTP, TCP, or named pipe.</span></span>  
  
## <a name="asynchronous-requestreply-without-errors"></a><span data-ttu-id="6b419-104">Demande/réponse asynchrone sans erreurs</span><span class="sxs-lookup"><span data-stu-id="6b419-104">Asynchronous Request/Reply without Errors</span></span>  
 <span data-ttu-id="6b419-105">Cette section décrit les activités et transferts pour un scénario de demande/réponse asynchrone, avec des clients multithread.</span><span class="sxs-lookup"><span data-stu-id="6b419-105">This section describes the activities and transfers for an asynchronous request/reply scenario, with multithreaded clients.</span></span>  
  
 <span data-ttu-id="6b419-106">L'activité de l'appelant se termine lorsque `beginCall` est retourné et `endCall` est retourné.</span><span class="sxs-lookup"><span data-stu-id="6b419-106">The caller activity terminates when `beginCall` returns, and `endCall` returns.</span></span> <span data-ttu-id="6b419-107">Si un rappel est appelé, celui-ci est retourné.</span><span class="sxs-lookup"><span data-stu-id="6b419-107">If a callback is called, the callback returns.</span></span>  
  
 <span data-ttu-id="6b419-108">L'activité appelée se termine lorsque `beginCall` est retourné, `endCall` est retourné, ou lorsque le rappel est retourné s'il a été appelé à partir de cette activité.</span><span class="sxs-lookup"><span data-stu-id="6b419-108">The called activity terminates when `beginCall` returns, `endCall` returns, or when the callback returns if it was called from that activity.</span></span>  
  
### <a name="asynchronous-client-without-callback"></a><span data-ttu-id="6b419-109">Client asynchrone sans rappel</span><span class="sxs-lookup"><span data-stu-id="6b419-109">Asynchronous Client without Callback</span></span>  
  
#### <a name="propagation-is-enabled-on-both-sides-using-http"></a><span data-ttu-id="6b419-110">La propagation est activée de chaque côté, avec HTTP</span><span class="sxs-lookup"><span data-stu-id="6b419-110">Propagation is Enabled on Both Sides, using HTTP</span></span>  
 <span data-ttu-id="6b419-111">![Scénarios asynchrones](../../../../../docs/framework/wcf/diagnostics/tracing/media/asyn1.gif "Asyn1")</span><span class="sxs-lookup"><span data-stu-id="6b419-111">![Asynchronous scenarios](../../../../../docs/framework/wcf/diagnostics/tracing/media/asyn1.gif "Asyn1")</span></span>  
  
 <span data-ttu-id="6b419-112">Figure 1.</span><span class="sxs-lookup"><span data-stu-id="6b419-112">Figure 1.</span></span> <span data-ttu-id="6b419-113">Client asynchrone, sans rappel, `propagateActivity` = `true` des deux côtés, HTTP</span><span class="sxs-lookup"><span data-stu-id="6b419-113">Asynchronous client, no callback, `propagateActivity`=`true` on both sides, HTTP</span></span>  
  
 <span data-ttu-id="6b419-114">Si `propagateActivity` = `true`, ProcessMessage indique l’activité ProcessAction pour transférer vers laquelle.</span><span class="sxs-lookup"><span data-stu-id="6b419-114">If `propagateActivity`=`true`, ProcessMessage indicates which ProcessAction activity to transfer to.</span></span>  
  
 <span data-ttu-id="6b419-115">Pour les scénarios HTTP, l'activité ReceiveBytes est appelée sur le premier message à envoyer et existe pendant la durée de vie de la demande.</span><span class="sxs-lookup"><span data-stu-id="6b419-115">For HTTP-based scenarios, ReceiveBytes is invoked on the first message to send, and exists for the lifetime of the request.</span></span>  
  
#### <a name="propagation-is-disabled-on-either-sides-using-http"></a><span data-ttu-id="6b419-116">La propagation est désactivée d'un côté ou de l'autre, avec HTTP</span><span class="sxs-lookup"><span data-stu-id="6b419-116">Propagation is Disabled on Either Sides, using HTTP</span></span>  
 <span data-ttu-id="6b419-117">Si `propagateActivity` = `false` de chaque côté, ProcessMessage n’indique pas l’activité ProcessAction pour transférer vers laquelle.</span><span class="sxs-lookup"><span data-stu-id="6b419-117">If `propagateActivity`=`false` on either side, ProcessMessage does not indicate which ProcessAction activity to transfer to.</span></span> <span data-ttu-id="6b419-118">Par conséquent, une nouvelle activité ProcessAction temporaire avec un nouvel ID est appelée.</span><span class="sxs-lookup"><span data-stu-id="6b419-118">Therefore, a new temporary ProcessAction activity with a new ID is invoked.</span></span> <span data-ttu-id="6b419-119">Lorsque la réponse asynchrone est mise en correspondance avec la demande dans le code ServiceModel, l'ID d'activité peut être récupéré du contexte local.</span><span class="sxs-lookup"><span data-stu-id="6b419-119">When the asynchronous response is matched to the request in ServiceModel code, the Activity ID can be retrieved from the local context.</span></span> <span data-ttu-id="6b419-120">Cet ID permet d'effectuer un transfert vers l'activité ProcessAction réelle.</span><span class="sxs-lookup"><span data-stu-id="6b419-120">The actual ProcessAction activity can be transferred to with that ID.</span></span>  
  
 <span data-ttu-id="6b419-121">![Scénarios asynchrones utilisant HTTP &#47; TCP &#47; Canal nommé](../../../../../docs/framework/wcf/diagnostics/tracing/media/async2.gif "Async2")</span><span class="sxs-lookup"><span data-stu-id="6b419-121">![Asynchronous scenarios using HTTP&#47;TCP&#47;Named Pipe](../../../../../docs/framework/wcf/diagnostics/tracing/media/async2.gif "Async2")</span></span>  
  
 <span data-ttu-id="6b419-122">Figure 2.</span><span class="sxs-lookup"><span data-stu-id="6b419-122">Figure 2.</span></span> <span data-ttu-id="6b419-123">Client asynchrone, sans rappel, `propagateActivity` = `false` de chaque côté, HTTP</span><span class="sxs-lookup"><span data-stu-id="6b419-123">Asynchronous client, no callback, `propagateActivity`=`false` on either side, HTTP</span></span>  
  
 <span data-ttu-id="6b419-124">Pour les scénarios HTTP, l'activité ReceiveBytes est appelée sur le premier message à envoyer et existe pendant la durée de vie de la demande.</span><span class="sxs-lookup"><span data-stu-id="6b419-124">For HTTP-based scenarios, ReceiveBytes is invoked on the first message to send, and exists for the lifetime of the request.</span></span>  
  
 <span data-ttu-id="6b419-125">Une activité traiter l’Action est créée sur un client asynchrone lorsque `propagateActivity` = `false` à l’appelant ou appelé, et lorsque le message de réponse n’inclut pas un en-tête d’Action.</span><span class="sxs-lookup"><span data-stu-id="6b419-125">A Process Action activity is created on an asynchronous client when `propagateActivity`=`false` at the caller or callee, and when the response message does not include an Action header.</span></span>  
  
#### <a name="propagation-is-enabled-on-both-sides-using-tcp-or-named-pipe"></a><span data-ttu-id="6b419-126">La propagation est activée de chaque côté, avec TCP ou Canal nommé</span><span class="sxs-lookup"><span data-stu-id="6b419-126">Propagation is Enabled on Both Sides, using TCP or Named Pipe</span></span>  
 <span data-ttu-id="6b419-127">![Scénarios asynchrones utilisant HTTP &#47; TCP &#47; Canal nommé](../../../../../docs/framework/wcf/diagnostics/tracing/media/async3.gif "Async3")</span><span class="sxs-lookup"><span data-stu-id="6b419-127">![Asynchronous scenarios using HTTP&#47;TCP&#47;Named Pipe](../../../../../docs/framework/wcf/diagnostics/tracing/media/async3.gif "Async3")</span></span>  
  
 <span data-ttu-id="6b419-128">Figure 3 :</span><span class="sxs-lookup"><span data-stu-id="6b419-128">Figure 3.</span></span> <span data-ttu-id="6b419-129">Client asynchrone, sans rappel, `propagateActivity` = `true` des deux côtés, canal nommé/TCP</span><span class="sxs-lookup"><span data-stu-id="6b419-129">Asynchronous client, no callback, `propagateActivity`=`true` on both sides, Named-Pipe/TCP</span></span>  
  
 <span data-ttu-id="6b419-130">Pour un scénario Canal nommé ou TCP, l'activité ReceiveBytes est appelée lorsque le client est ouvert, et existe pendant la durée de vie de la connexion.</span><span class="sxs-lookup"><span data-stu-id="6b419-130">For a Named-Pipe or TCP-based scenario, ReceiveBytes is invoked when the client is opened, and exists for the lifetime of the connection.</span></span>  
  
 <span data-ttu-id="6b419-131">Identique à la Figure 1, si `propagateActivity` = `true`, ProcessMessage indique l’activité ProcessAction pour transférer vers laquelle.</span><span class="sxs-lookup"><span data-stu-id="6b419-131">Similar to Figure 1, if `propagateActivity`=`true`, ProcessMessage indicates which ProcessAction activity to transfer to.</span></span>  
  
#### <a name="propagation-is-disabled-on-either-sides-using-tcp-or-named-pipe"></a><span data-ttu-id="6b419-132">La propagation est désactivée d'un côté ou de l'autre, avec TCP ou Canal nommé</span><span class="sxs-lookup"><span data-stu-id="6b419-132">Propagation is Disabled on Either Sides, using TCP or Named Pipe</span></span>  
 <span data-ttu-id="6b419-133">Pour un scénario Canal nommé ou TCP, l'activité ReceiveBytes est appelée lorsque le client est ouvert, et existe pendant la durée de vie de la connexion.</span><span class="sxs-lookup"><span data-stu-id="6b419-133">For a Named-Pipe or TCP-based scenario, ReceiveBytes is invoked when the client is opened, and exists for the lifetime of the connection.</span></span>  
  
 <span data-ttu-id="6b419-134">Similaire à la figure 2, si `propagateActivity` = `false` de chaque côté, ProcessMessage n’indique pas l’activité ProcessAction pour transférer vers laquelle.</span><span class="sxs-lookup"><span data-stu-id="6b419-134">Similar to Fig.2, If `propagateActivity`=`false` on either side, ProcessMessage does not indicate which ProcessAction activity to transfer to.</span></span> <span data-ttu-id="6b419-135">Par conséquent, une nouvelle activité ProcessAction temporaire avec un nouvel ID est appelée.</span><span class="sxs-lookup"><span data-stu-id="6b419-135">Therefore, a new temporary ProcessAction activity with a new ID is invoked.</span></span> <span data-ttu-id="6b419-136">Lorsque la réponse asynchrone est mise en correspondance avec la demande dans le code ServiceModel, l'ID d'activité peut être récupéré du contexte local.</span><span class="sxs-lookup"><span data-stu-id="6b419-136">When the asynchronous response is matched to the request in ServiceModel code, the Activity ID can be retrieved from the local context.</span></span> <span data-ttu-id="6b419-137">Cet ID permet d'effectuer un transfert vers l'activité ProcessAction réelle.</span><span class="sxs-lookup"><span data-stu-id="6b419-137">The actual ProcessAction activity can be transferred to with that ID.</span></span>  
  
 <span data-ttu-id="6b419-138">![Scénarios asynchrones utilisant HTTP &#47; TCP &#47; Canaux nommés](../../../../../docs/framework/wcf/diagnostics/tracing/media/async4.gif "Async4")</span><span class="sxs-lookup"><span data-stu-id="6b419-138">![Asynchronous scenarios using HTTP&#47;TCP&#47; Named Pipes](../../../../../docs/framework/wcf/diagnostics/tracing/media/async4.gif "Async4")</span></span>  
  
 <span data-ttu-id="6b419-139">La figure 4.</span><span class="sxs-lookup"><span data-stu-id="6b419-139">Figure 4.</span></span> <span data-ttu-id="6b419-140">Client asynchrone, sans rappel, `propagateActivity` = `false` de chaque côté, canal nommé/TCP</span><span class="sxs-lookup"><span data-stu-id="6b419-140">Asynchronous client, no callback, `propagateActivity`=`false` on either side, Named-Pipe/TCP</span></span>  
  
### <a name="asynchronous-client-with-callback"></a><span data-ttu-id="6b419-141">Client asynchrone avec rappel</span><span class="sxs-lookup"><span data-stu-id="6b419-141">Asynchronous client with Callback</span></span>  
 <span data-ttu-id="6b419-142">Ce scénario ajoute les activités G et A', pour le rappel et `endCall`, et leurs transferts entrants/sortants.</span><span class="sxs-lookup"><span data-stu-id="6b419-142">This scenario adds activities G and A’, for the callback and `endCall`, and their transfers in/out.</span></span>  
  
 <span data-ttu-id="6b419-143">Cette section montre seulement l’utilisation de HTTP `propragateActivity` = `true`.</span><span class="sxs-lookup"><span data-stu-id="6b419-143">This section only demonstrates using HTTP with `propragateActivity`=`true`.</span></span> <span data-ttu-id="6b419-144">Toutefois, les activités et transferts supplémentaires s’appliquent également aux autres cas (c'est-à-dire, `propagateActivity` = `false`, à l’aide de TCP ou canal nommé).</span><span class="sxs-lookup"><span data-stu-id="6b419-144">However, the additional activities and transfers also apply to the other cases (that is, `propagateActivity`=`false`, using TCP or Named-Pipe).</span></span>  
  
 <span data-ttu-id="6b419-145">Le rappel crée une activité (G) lorsque le client appelle le code utilisateur pour notifier que les résultats sont prêts.</span><span class="sxs-lookup"><span data-stu-id="6b419-145">The callback creates a new activity (G) when the client calls user code to notify that results are ready.</span></span> <span data-ttu-id="6b419-146">Le code utilisateur appelle ensuite `endCall` dans le rappel (comme indiqué à la figure 5) ou hors de celui-ci (figure 6).</span><span class="sxs-lookup"><span data-stu-id="6b419-146">User code then calls `endCall` within the callback (as shown in Figure 5) or outside the callback (Figure 6).</span></span> <span data-ttu-id="6b419-147">Car on ne sait pas quelle activité utilisateur `endCall` est appelée à partir, cette activité est étiquetée `A’`.</span><span class="sxs-lookup"><span data-stu-id="6b419-147">Because it is not known which user activity `endCall` is being called from, this activity is labeled `A’`.</span></span> <span data-ttu-id="6b419-148">L'activité A' peut être identique ou différente de l'activité A.</span><span class="sxs-lookup"><span data-stu-id="6b419-148">It is possible that A’ can be identical to or different from A.</span></span>  
  
 <span data-ttu-id="6b419-149">![Scénarios asynchrones](../../../../../docs/framework/wcf/diagnostics/tracing/media/asynccallback1.gif "AsyncCallback1")</span><span class="sxs-lookup"><span data-stu-id="6b419-149">![Asynchronous scenarios](../../../../../docs/framework/wcf/diagnostics/tracing/media/asynccallback1.gif "AsyncCallback1")</span></span>  
  
 <span data-ttu-id="6b419-150">La figure 5.</span><span class="sxs-lookup"><span data-stu-id="6b419-150">Figure 5.</span></span> <span data-ttu-id="6b419-151">Client asynchrone avec rappel, `endCall` à l'intérieur du rappel</span><span class="sxs-lookup"><span data-stu-id="6b419-151">Asynchronous client with callback, `endCall` in Callback</span></span>  
  
 <span data-ttu-id="6b419-152">![Scénarios asynchrones](../../../../../docs/framework/wcf/diagnostics/tracing/media/asynccallback2.gif "AsyncCallback2")</span><span class="sxs-lookup"><span data-stu-id="6b419-152">![Asynchronous Scenarios](../../../../../docs/framework/wcf/diagnostics/tracing/media/asynccallback2.gif "AsyncCallback2")</span></span>  
  
 <span data-ttu-id="6b419-153">La figure 6.</span><span class="sxs-lookup"><span data-stu-id="6b419-153">Figure 6.</span></span> <span data-ttu-id="6b419-154">Client asynchrone avec rappel, `endCall` hors du rappel</span><span class="sxs-lookup"><span data-stu-id="6b419-154">Asynchronous client with callback, `endCall` outside of Callback</span></span>  
  
### <a name="asynchronous-server-with-callback"></a><span data-ttu-id="6b419-155">Serveur asynchrone avec rappel</span><span class="sxs-lookup"><span data-stu-id="6b419-155">Asynchronous Server with Callback</span></span>  
 <span data-ttu-id="6b419-156">![Scénarios asynchrones utilisant HTTP &#47; TCP &#47; Nommé &#45; Canal](../../../../../docs/framework/wcf/diagnostics/tracing/media/aynchserver.gif "AynchServer")</span><span class="sxs-lookup"><span data-stu-id="6b419-156">![Asynchronous scenarios using HTTP&#47;TCP&#47; Named&#45;Pipe](../../../../../docs/framework/wcf/diagnostics/tracing/media/aynchserver.gif "AynchServer")</span></span>  
  
 <span data-ttu-id="6b419-157">La figure 7.</span><span class="sxs-lookup"><span data-stu-id="6b419-157">Figure 7.</span></span> <span data-ttu-id="6b419-158">Serveur asynchrone avec rappel</span><span class="sxs-lookup"><span data-stu-id="6b419-158">Asynchronous server, with callback</span></span>  
  
 <span data-ttu-id="6b419-159">La pile de canaux rappelle le client à la réception des messages : les traces de ce processus sont émises dans l'activité ProcessRequest elle-même.</span><span class="sxs-lookup"><span data-stu-id="6b419-159">The channel stack calls back the client on Message Receive: traces for this processing are emitted in the ProcessRequest activity itself.</span></span>  
  
## <a name="asynchronous-requestreply-with-errors"></a><span data-ttu-id="6b419-160">Demande/Réponse asynchrone avec erreurs</span><span class="sxs-lookup"><span data-stu-id="6b419-160">Asynchronous Request/Reply with Errors</span></span>  
 <span data-ttu-id="6b419-161">Des messages d'erreur sont reçus au cours de `endCall`.</span><span class="sxs-lookup"><span data-stu-id="6b419-161">Fault message errors are received during `endCall`.</span></span> <span data-ttu-id="6b419-162">Sinon, les activités et transferts sont identiques aux scénarios précédents.</span><span class="sxs-lookup"><span data-stu-id="6b419-162">Otherwise, activities and transfers are similar to previous scenarios.</span></span>  
  
## <a name="asynchronous-one-way-with-or-without-errors"></a><span data-ttu-id="6b419-163">Communication unidirectionnelle asynchrone avec ou sans erreurs</span><span class="sxs-lookup"><span data-stu-id="6b419-163">Asynchronous One-Way with or without Errors</span></span>  
 <span data-ttu-id="6b419-164">Aucune réponse ou erreur n'est renvoyée au client.</span><span class="sxs-lookup"><span data-stu-id="6b419-164">No response or fault is returned to the client.</span></span>
