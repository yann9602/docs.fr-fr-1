---
title: '&lt;reliableSession&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 129b4a59-37f0-4030-b664-03795d257d29
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f8484fe902b356f7fae4e526bdaa5610bf7d7ac6
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="ltreliablesessiongt"></a><span data-ttu-id="b7a00-102">&lt;reliableSession&gt;</span><span class="sxs-lookup"><span data-stu-id="b7a00-102">&lt;reliableSession&gt;</span></span>
<span data-ttu-id="b7a00-103">Définit le paramètre pour la messagerie WS-Reliable.</span><span class="sxs-lookup"><span data-stu-id="b7a00-103">Defines setting for WS-Reliable Messaging.</span></span> <span data-ttu-id="b7a00-104">Lorsque cet élément est ajouté à une liaison personnalisée, le canal résultant peut prendre en charge des assurances de remise EOD (Exactly-Once-Delivery).</span><span class="sxs-lookup"><span data-stu-id="b7a00-104">When this element is added to a custom binding, the resulting channel can support exactly-once delivery assurances.</span></span>  
  
 <span data-ttu-id="b7a00-105">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="b7a00-105">\<system.serviceModel></span></span>  
<span data-ttu-id="b7a00-106">\<liaisons ></span><span class="sxs-lookup"><span data-stu-id="b7a00-106">\<bindings></span></span>  
<span data-ttu-id="b7a00-107">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="b7a00-107">\<customBinding></span></span>  
<span data-ttu-id="b7a00-108">\<liaison ></span><span class="sxs-lookup"><span data-stu-id="b7a00-108">\<binding></span></span>  
<span data-ttu-id="b7a00-109">\<reliableSession ></span><span class="sxs-lookup"><span data-stu-id="b7a00-109">\<reliableSession></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7a00-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b7a00-110">Syntax</span></span>  
  
```xml  
<reliableSession acknowledgementInterval="TimeSpan"  
        flowControlEnabled="Boolean"   
    inactivityTimeout="TimeSpan"  
    maxPendingChannels="Integer"  
    maxRetryCount="Integer"   
        maxTransferWindowSize="Integer"  
    reliableMessagingVersion="Default/WSReliableMessagingFebruary2005/WSReliableMessaging11"  
    ordered="Boolean" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b7a00-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="b7a00-111">Attributes and Elements</span></span>  
 <span data-ttu-id="b7a00-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="b7a00-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b7a00-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="b7a00-113">Attributes</span></span>  
  
|<span data-ttu-id="b7a00-114">Attribut</span><span class="sxs-lookup"><span data-stu-id="b7a00-114">Attribute</span></span>|<span data-ttu-id="b7a00-115">Description</span><span class="sxs-lookup"><span data-stu-id="b7a00-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b7a00-116">acknowledgementInterval</span><span class="sxs-lookup"><span data-stu-id="b7a00-116">acknowledgementInterval</span></span>|<span data-ttu-id="b7a00-117"><xref:System.TimeSpan> qui contient l'intervalle de temps maximum pendant lequel le canal doit attendre avant d'envoyer un accusé de réception pour les messages reçus jusqu'alors.</span><span class="sxs-lookup"><span data-stu-id="b7a00-117">A <xref:System.TimeSpan> that contains the maximum time interval the channel is going to wait to send an acknowledgment for messages received up to that point.</span></span> <span data-ttu-id="b7a00-118">La valeur par défaut est 00:00:0.2.</span><span class="sxs-lookup"><span data-stu-id="b7a00-118">The default is 00:00:0.2.</span></span>|  
|<span data-ttu-id="b7a00-119">flowControlEnabled</span><span class="sxs-lookup"><span data-stu-id="b7a00-119">flowControlEnabled</span></span>|<span data-ttu-id="b7a00-120">Valeur booléenne qui indique si le contrôle de flux avancé (une implémentation du contrôle de flux de la messagerie WS-Reliable spécifique à Microsoft) est activé.</span><span class="sxs-lookup"><span data-stu-id="b7a00-120">A Boolean value that indicates whether advanced flow control, a Microsoft-specific implementation of flow control for WS-Reliable messaging, is activated.</span></span> <span data-ttu-id="b7a00-121">La valeur par défaut est `true`.</span><span class="sxs-lookup"><span data-stu-id="b7a00-121">The default is `true`.</span></span>|  
|<span data-ttu-id="b7a00-122">inactivityTimeout</span><span class="sxs-lookup"><span data-stu-id="b7a00-122">inactivityTimeout</span></span>|<span data-ttu-id="b7a00-123"><xref:System.TimeSpan> qui spécifie la durée maximale pendant laquelle le canal autorisera l'autre partie communicante à ne pas envoyer de messages avant qu'une erreur soit provoquée sur le canal.</span><span class="sxs-lookup"><span data-stu-id="b7a00-123">A <xref:System.TimeSpan> that specifies the maximum duration that the channel is going to allow the other communication party not to send any messages, before faulting the channel.</span></span> <span data-ttu-id="b7a00-124">La valeur par défaut est 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="b7a00-124">The default is 00:10:00.</span></span><br /><br /> <span data-ttu-id="b7a00-125">L'activité sur un canal est définie comme étant la réception de messages d'application ou d'infrastructure.</span><span class="sxs-lookup"><span data-stu-id="b7a00-125">Activity on a channel is defined as receiving an application or infrastructure messages.</span></span> <span data-ttu-id="b7a00-126">Cette propriété contrôle la durée maximale d'activation d'une session inactive.</span><span class="sxs-lookup"><span data-stu-id="b7a00-126">This property controls the maximum amount of time to keep an inactive session alive.</span></span> <span data-ttu-id="b7a00-127">En cas de durée supérieure sans activité, la session est abandonnée par l'infrastructure et une erreur est provoquée sur le canal.</span><span class="sxs-lookup"><span data-stu-id="b7a00-127">If longer time passes with no activity, the session is aborted by the infrastructure and the channel faults.</span></span> <span data-ttu-id="b7a00-128">**Remarque :** n’est pas nécessaire pour l’application envoyer régulièrement des messages afin de maintenir la connexion.</span><span class="sxs-lookup"><span data-stu-id="b7a00-128">**Note:**  It is not necessary for the application to periodically send messages to keep the connection alive.</span></span>|  
|<span data-ttu-id="b7a00-129">maxPendingChannels</span><span class="sxs-lookup"><span data-stu-id="b7a00-129">maxPendingChannels</span></span>|<span data-ttu-id="b7a00-130">Entier qui spécifie le nombre maximal de canaux en attente d'être acceptés sur l'écouteur.</span><span class="sxs-lookup"><span data-stu-id="b7a00-130">An integer that specifies the maximum number of channels that can wait on the listener to be accepted.</span></span> <span data-ttu-id="b7a00-131">Cette valeur doit être comprise entre 1 et 16 384 inclus.</span><span class="sxs-lookup"><span data-stu-id="b7a00-131">This value should be between 1 to 16384 inclusive.</span></span> <span data-ttu-id="b7a00-132">La valeur par défaut est 4.</span><span class="sxs-lookup"><span data-stu-id="b7a00-132">The default is 4.</span></span><br /><br /> <span data-ttu-id="b7a00-133">Les canaux sont en attente lorsqu'ils attendent d'être acceptés.</span><span class="sxs-lookup"><span data-stu-id="b7a00-133">Channels are pending when they are waiting to be accepted.</span></span> <span data-ttu-id="b7a00-134">Une fois que cette limite est atteinte, aucun canal n'est créé.</span><span class="sxs-lookup"><span data-stu-id="b7a00-134">Once that limit is reached, no channels are created.</span></span> <span data-ttu-id="b7a00-135">Au contraire, ils sont mis en mode d'attente jusqu'à ce que ce nombre se réduise (en acceptant des canaux en attente).</span><span class="sxs-lookup"><span data-stu-id="b7a00-135">Rather, they are put in pending mode until this number goes down (by accepting pending channels).</span></span> <span data-ttu-id="b7a00-136">Cette limite dépend des fabriques.</span><span class="sxs-lookup"><span data-stu-id="b7a00-136">This is a per-factory limit.</span></span><br /><br /> <span data-ttu-id="b7a00-137">Lorsque le seuil est atteint et qu'une application distante essaie d'établir une nouvelle session fiable, la demande est refusée et l'opération d'ouverture initiale notifie l'erreur.</span><span class="sxs-lookup"><span data-stu-id="b7a00-137">When the threshold is reached and a remote application tries to establish a new reliable session, the request is denied and the open operation that prompted this faults.</span></span> <span data-ttu-id="b7a00-138">Cette limite ne s'applique pas au nombre de canaux sortants en attente.</span><span class="sxs-lookup"><span data-stu-id="b7a00-138">This limit does not apply to the number of pending outgoing channels.</span></span>|  
|<span data-ttu-id="b7a00-139">maxRetryCount</span><span class="sxs-lookup"><span data-stu-id="b7a00-139">maxRetryCount</span></span>|<span data-ttu-id="b7a00-140">Entier qui spécifie le nombre maximal de tentatives effectuées par un canal fiable pour retransmettre un message pour lequel il n'a pas reçu d'accusé de réception en appelant Send sur son canal sous-jacent.</span><span class="sxs-lookup"><span data-stu-id="b7a00-140">An integer that specifies the maximum number of times a reliable channel attempts to retransmit a message it has not received an acknowledgment for, by calling Send on its underlying channel.</span></span><br /><br /> <span data-ttu-id="b7a00-141">Cette valeur doit être supérieure à zéro.</span><span class="sxs-lookup"><span data-stu-id="b7a00-141">This value should be greater than zero.</span></span> <span data-ttu-id="b7a00-142">La valeur par défaut est 8.</span><span class="sxs-lookup"><span data-stu-id="b7a00-142">The default is 8.</span></span><br /><br /> <span data-ttu-id="b7a00-143">Cette valeur doit être un entier supérieur à zéro.</span><span class="sxs-lookup"><span data-stu-id="b7a00-143">This value should be an integer greater than zero.</span></span> <span data-ttu-id="b7a00-144">Si aucun accusé de réception n'est reçu après la dernière retransmission, le canal notifie l'erreur.</span><span class="sxs-lookup"><span data-stu-id="b7a00-144">If an acknowledgment is not received after the last retransmission, the channel faults.</span></span><br /><br /> <span data-ttu-id="b7a00-145">Un message est considéré comme devant être transféré si sa remise au destinataire a été acceptée par le destinataire.</span><span class="sxs-lookup"><span data-stu-id="b7a00-145">A message is considered to be transferred if its delivery at the recipient has been acknowledged by the recipient.</span></span><br /><br /> <span data-ttu-id="b7a00-146">Si, pour un message ayant été transmis, aucun accusé de réception n'a été reçu après un certain temps, l'infrastructure retransmet automatiquement le message.</span><span class="sxs-lookup"><span data-stu-id="b7a00-146">If an acknowledgment has not been received within a certain amount of time for a message that has been transmitted, the infrastructure automatically retransmits the message.</span></span> <span data-ttu-id="b7a00-147">L'infrastructure essaie de renvoyer le message à autant de reprises que celles spécifiées par cette propriété.</span><span class="sxs-lookup"><span data-stu-id="b7a00-147">The infrastructure tries to resend the message for at most the number of times specified by this property.</span></span> <span data-ttu-id="b7a00-148">Si aucun accusé de réception n'est reçu après la dernière retransmission, le canal notifie l'erreur.</span><span class="sxs-lookup"><span data-stu-id="b7a00-148">If an acknowledgment is not received after the last retransmission, the channel faults.</span></span><br /><br /> <span data-ttu-id="b7a00-149">L'infrastructure utilise un algorithme de réduction de puissance exponentiel pour déterminer quand retransmettre, selon un délai aller-retour moyen calculé.</span><span class="sxs-lookup"><span data-stu-id="b7a00-149">The infrastructure uses an exponential back-off algorithm to determine when to retransmit, based on a computed average round-trip time.</span></span> <span data-ttu-id="b7a00-150">Ce délai démarre initialement 1 seconde avant la retransmission et, le délai doublant à chaque tentative, le délai écoulé entre la première et la dernière tentative de retransmission est d'environ 8,5 minutes.</span><span class="sxs-lookup"><span data-stu-id="b7a00-150">The time initially starts at 1 second before retransmission and doubling the delay with every attempt, which results in approximately 8.5 minutes passing between the first transmission attempt and the last retransmission attempt.</span></span> <span data-ttu-id="b7a00-151">Le délai de la première tentative de retransmission est ajusté au délai aller-retour calculé et le décalage créé par ces tentatives varie en conséquence.</span><span class="sxs-lookup"><span data-stu-id="b7a00-151">The time for the first retransmission attempt is adjusted according to the calculated round-trip time and the resulting stretch of time that those attempts take varies accordingly.</span></span> <span data-ttu-id="b7a00-152">Cela permet au délai de retransmission de s'adapter dynamiquement aux conditions de réseau variables.</span><span class="sxs-lookup"><span data-stu-id="b7a00-152">This allows the retransmission time to dynamically adapt to varying network conditions.</span></span>|  
|<span data-ttu-id="b7a00-153">maxTransferWindowSize</span><span class="sxs-lookup"><span data-stu-id="b7a00-153">maxTransferWindowSize</span></span>|<span data-ttu-id="b7a00-154">Entier qui spécifie la taille maximale de la mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="b7a00-154">An integer that specifies the maximum size of the buffer.</span></span> <span data-ttu-id="b7a00-155">Les valeurs autorisées sont comprises entre 1 et 4 096 (inclus).</span><span class="sxs-lookup"><span data-stu-id="b7a00-155">Valid values are from 1 to 4096 inclusive.</span></span><br /><br /> <span data-ttu-id="b7a00-156">Pour le client, cet attribut définit la taille maximale de la mémoire tampon utilisée par un canal fiable pour contenir les messages n'ayant pas encore été acceptés par le récepteur.</span><span class="sxs-lookup"><span data-stu-id="b7a00-156">On the client, this attribute defines the maximum size of the buffer used by a reliable channel to hold messages not yet acknowledged by the receiver.</span></span> <span data-ttu-id="b7a00-157">L'unité du quota est un message.</span><span class="sxs-lookup"><span data-stu-id="b7a00-157">The unit of the quota is a message.</span></span> <span data-ttu-id="b7a00-158">Si la mémoire tampon est pleine, les opérations SEND suivantes sont bloquées.</span><span class="sxs-lookup"><span data-stu-id="b7a00-158">If the buffer is full, further SEND operations are blocked.</span></span><br /><br /> <span data-ttu-id="b7a00-159">Pour le récepteur, cet attribut définit la taille maximale de la mémoire tampon utilisée par le canal pour stocker les messages entrants n'ayant pas encore été distribués dans l'application.</span><span class="sxs-lookup"><span data-stu-id="b7a00-159">On the receiver, this attribute defines the maximum size of the buffer used by the channel to store incoming messages not yet dispatched to the application.</span></span> <span data-ttu-id="b7a00-160">Si la mémoire tampon est pleine, les messages suivants sont supprimés de manière silencieuse par le récepteur et doivent être retransmis par le client.</span><span class="sxs-lookup"><span data-stu-id="b7a00-160">If the buffer is full, further messages are silently dropped by the receiver and require retransmission by the client.</span></span>|  
|<span data-ttu-id="b7a00-161">ordered</span><span class="sxs-lookup"><span data-stu-id="b7a00-161">ordered</span></span>|<span data-ttu-id="b7a00-162">Valeur booléenne qui spécifie s'il est garanti que les messages arrivent dans l'ordre dans lequel ils ont été envoyés.</span><span class="sxs-lookup"><span data-stu-id="b7a00-162">A Boolean that specifies whether messages are guaranteed to arrive in the order they were sent.</span></span> <span data-ttu-id="b7a00-163">Si ce paramètre est `false`, les messages peuvent arriver dans le désordre.</span><span class="sxs-lookup"><span data-stu-id="b7a00-163">If this setting is `false`, messages can arrive out of order.</span></span> <span data-ttu-id="b7a00-164">La valeur par défaut est `true`.</span><span class="sxs-lookup"><span data-stu-id="b7a00-164">The default is `true`.</span></span>|  
|<span data-ttu-id="b7a00-165">reliableMessagingVersion</span><span class="sxs-lookup"><span data-stu-id="b7a00-165">reliableMessagingVersion</span></span>|<span data-ttu-id="b7a00-166">Valeur autorisée de <xref:System.ServiceModel.ReliableMessagingVersion> qui spécifie la version de messagerie WS-Reliable à utiliser.</span><span class="sxs-lookup"><span data-stu-id="b7a00-166">A valid value from <xref:System.ServiceModel.ReliableMessagingVersion> that specifies the WS-ReliableMessaging version to be used.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b7a00-167">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="b7a00-167">Child Elements</span></span>  
 <span data-ttu-id="b7a00-168">None</span><span class="sxs-lookup"><span data-stu-id="b7a00-168">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b7a00-169">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="b7a00-169">Parent Elements</span></span>  
  
|<span data-ttu-id="b7a00-170">Élément</span><span class="sxs-lookup"><span data-stu-id="b7a00-170">Element</span></span>|<span data-ttu-id="b7a00-171">Description</span><span class="sxs-lookup"><span data-stu-id="b7a00-171">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b7a00-172">\<liaison ></span><span class="sxs-lookup"><span data-stu-id="b7a00-172">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="b7a00-173">Définit toutes les fonctions de liaison d’une liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="b7a00-173">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b7a00-174">Remarques</span><span class="sxs-lookup"><span data-stu-id="b7a00-174">Remarks</span></span>  
 <span data-ttu-id="b7a00-175">Les sessions fiables fournissent des fonctionnalités pour une messagerie et des sessions fiables.</span><span class="sxs-lookup"><span data-stu-id="b7a00-175">Reliable sessions provide features for reliable messaging and sessions.</span></span> <span data-ttu-id="b7a00-176">La messagerie fiable réessaie d'établir la communication en cas d'échec et permet de spécifier des assurances de remise telles que l'ordre d'arrivée des messages.</span><span class="sxs-lookup"><span data-stu-id="b7a00-176">Reliable messaging retries communication on failure and allows delivery assurances such as in-order arrival of messages to be specified.</span></span> <span data-ttu-id="b7a00-177">Les sessions conservent l'état pour les clients entre les appels.</span><span class="sxs-lookup"><span data-stu-id="b7a00-177">Sessions maintain state for clients between calls.</span></span> <span data-ttu-id="b7a00-178">Cet élément assure également en option la remise de messages ordonnés.</span><span class="sxs-lookup"><span data-stu-id="b7a00-178">This element also optionally provides ordered message delivery.</span></span> <span data-ttu-id="b7a00-179">Cette session implémentée peut croiser des intermédiaires SOAP et de transport.</span><span class="sxs-lookup"><span data-stu-id="b7a00-179">This implemented session can cross SOAP and transport intermediaries.</span></span>  
  
 <span data-ttu-id="b7a00-180">Chaque élément de liaison représente une étape de traitement lors de l'envoi ou de la réception des messages.</span><span class="sxs-lookup"><span data-stu-id="b7a00-180">Each binding element represents a processing step when sending or receiving messages.</span></span> <span data-ttu-id="b7a00-181">Au moment de l'exécution, les éléments de liaison créent les fabrications de canal et les écouteurs nécessaires pour générer les piles de canaux sortants et entrants requis pour envoyer et recevoir des messages.</span><span class="sxs-lookup"><span data-stu-id="b7a00-181">At runtime, binding elements create the channel factories and listeners that are necessary to build outgoing and incoming channel stacks required to send and receive messages.</span></span> <span data-ttu-id="b7a00-182">Le `reliableSession` fournit une couche facultative dans la pile capable d'établir une session fiable entre des points de terminaison et de configurer le comportement de cette session.</span><span class="sxs-lookup"><span data-stu-id="b7a00-182">The `reliableSession` provides an optional layer in the stack that can establish a reliable session between endpoints and configure the behavior of this session.</span></span>  
  
 <span data-ttu-id="b7a00-183">Pour plus d’informations, consultez [des Sessions fiables](../../../../../docs/framework/wcf/feature-details/reliable-sessions.md).</span><span class="sxs-lookup"><span data-stu-id="b7a00-183">For more information, see [Reliable Sessions](../../../../../docs/framework/wcf/feature-details/reliable-sessions.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b7a00-184">Exemple</span><span class="sxs-lookup"><span data-stu-id="b7a00-184">Example</span></span>  
 <span data-ttu-id="b7a00-185">L’exemple suivant montre comment configurer une liaison personnalisée avec plusieurs éléments de transport et d’encodage de message, en activant surtout des sessions fiables qui maintiennent l’état du client et spécifient des assurances de remise dans l’ordre.</span><span class="sxs-lookup"><span data-stu-id="b7a00-185">The following example demonstrates how to configure a custom binding with various transport and message encoding elements, especially enabling reliable sessions, which maintains client state and specifies in-order delivery assurances.</span></span> <span data-ttu-id="b7a00-186">Cette fonctionnalité est configurée dans les fichiers de configuration de l'application pour le client et le service.</span><span class="sxs-lookup"><span data-stu-id="b7a00-186">This feature is configured in the application configuration files for the client and service.</span></span> <span data-ttu-id="b7a00-187">L'exemple présente la configuration du service.</span><span class="sxs-lookup"><span data-stu-id="b7a00-187">The example show the service configuration.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service   
          name="Microsoft.ServiceModel.Samples.CalculatorService"  
          behaviorConfiguration="CalculatorServiceBehavior">  
        <!-- This endpoint is exposed at the base address provided by host: http://localhost/servicemodelsamples/service.svc  -->  
        <!-- specify customBinding binding and a binding configuration to use -->  
        <endpoint address=""  
                  binding="customBinding"  
                  bindingConfiguration="Binding1"   
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />  
        <!-- The mex endpoint is exposed at http://localhost/servicemodelsamples/service.svc/mex -->  
        <endpoint address="mex"  
                  binding="mexHttpBinding"  
                  contract="IMetadataExchange" />  
      </service>  
    </services>  
  
    <!-- custom binding configuration - configures HTTP transport, reliable sessions -->  
    <bindings>  
      <customBinding>  
        <binding name="Binding1">  
          <reliableSession />  
          <security authenticationMode="SecureConversation"  
                     requireSecurityContextCancellation="true">  
          </security>  
          <compositeDuplex />  
          <oneWay />  
          <textMessageEncoding messageVersion="Soap12WSAddressing10" writeEncoding="utf-8" />  
          <httpTransport authenticationScheme="Anonymous" bypassProxyOnLocal="false"  
                        hostNameComparisonMode="StrongWildcard"   
                        proxyAuthenticationScheme="Anonymous" realm=""   
                        useDefaultWebProxy="true" />  
        </binding>  
      </customBinding>  
    </bindings>  
  
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="CalculatorServiceBehavior">  
          <serviceMetadata httpGetEnabled="True"/>  
          <serviceDebug includeExceptionDetailInFaults="False" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b7a00-188">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b7a00-188">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ReliableSessionElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>  
 [<span data-ttu-id="b7a00-189">Sessions fiables</span><span class="sxs-lookup"><span data-stu-id="b7a00-189">Reliable Sessions</span></span>](../../../../../docs/framework/wcf/feature-details/reliable-sessions.md)  
 [<span data-ttu-id="b7a00-190">Liaisons</span><span class="sxs-lookup"><span data-stu-id="b7a00-190">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="b7a00-191">Extension de liaisons</span><span class="sxs-lookup"><span data-stu-id="b7a00-191">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="b7a00-192">Liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="b7a00-192">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="b7a00-193">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="b7a00-193">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
