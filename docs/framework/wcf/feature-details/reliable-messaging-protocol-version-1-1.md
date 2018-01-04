---
title: "Protocole de messagerie fiable version 1,1"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0da47b82-f8eb-42da-8bfe-e56ce7ba6f59
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 67df8b539109d7e4dafcbc42ad7679643767021a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="reliable-messaging-protocol-version-11"></a><span data-ttu-id="62055-102">Protocole de messagerie fiable version 1,1</span><span class="sxs-lookup"><span data-stu-id="62055-102">Reliable Messaging Protocol version 1.1</span></span>
<span data-ttu-id="62055-103">Cette rubrique traite des détails de l'implémentation [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] pour le protocole WS-ReliableMessaging de février 2007 (version 1.1) nécessaire pour l'interopérabilité à l'aide du transport HTTP.</span><span class="sxs-lookup"><span data-stu-id="62055-103">This topic covers [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] implementation details for the WS-ReliableMessaging February 2007 (version 1.1) protocol necessary for interoperation using the HTTP transport.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="62055-104"> suit la spécification WS-ReliableMessaging avec les contraintes et les éclaircissements présentés dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="62055-104"> follows the WS-ReliableMessaging specification with the constraints and clarifications explained in this topic.</span></span> <span data-ttu-id="62055-105">Notez que le protocole de la version 1.1 de WS-ReliableMessaging est implémenté en commençant par le [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="62055-105">Note that the WS-ReliableMessaging version 1.1 protocol is implemented starting with the [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)].</span></span>  
  
 <span data-ttu-id="62055-106">Le protocole WS-ReliableMessaging de février 2007 est implémenté dans [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] par <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="62055-106">The WS-ReliableMessaging February 2007 protocol is implemented in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] by the <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>.</span></span>  
  
 <span data-ttu-id="62055-107">Pour plus de simplicité, la rubrique utilise les rôles suivants :</span><span class="sxs-lookup"><span data-stu-id="62055-107">For convenience, the topic uses the following roles:</span></span>  
  
-   <span data-ttu-id="62055-108">Initiateur : client qui initialise la création de séquence de message WS-Reliable .</span><span class="sxs-lookup"><span data-stu-id="62055-108">Initiator: The client that initiates WS-Reliable Message sequence creation.</span></span>  
  
-   <span data-ttu-id="62055-109">Répondeur : service qui reçoit les demandes de l'initiateur.</span><span class="sxs-lookup"><span data-stu-id="62055-109">Responder: The service that receives the initiator's requests.</span></span>  
  
 <span data-ttu-id="62055-110">Ce document utilise les préfixes et les espaces de noms répertoriés dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="62055-110">This document uses the prefixes and namespaces in the following table.</span></span>  
  
|<span data-ttu-id="62055-111">Préfixe</span><span class="sxs-lookup"><span data-stu-id="62055-111">Prefix</span></span>|<span data-ttu-id="62055-112">Espace de noms</span><span class="sxs-lookup"><span data-stu-id="62055-112">Namespace</span></span>|  
|-|-|  
|<span data-ttu-id="62055-113">wsrm</span><span class="sxs-lookup"><span data-stu-id="62055-113">wsrm</span></span>|<span data-ttu-id="62055-114">http://docs.oasis-open.org/ws-rx/wsrm/200702</span><span class="sxs-lookup"><span data-stu-id="62055-114">http://docs.oasis-open.org/ws-rx/wsrm/200702</span></span>|  
|<span data-ttu-id="62055-115">netrm</span><span class="sxs-lookup"><span data-stu-id="62055-115">netrm</span></span>|<span data-ttu-id="62055-116">http://schemas.microsoft.com/ws/2006/05/rm</span><span class="sxs-lookup"><span data-stu-id="62055-116">http://schemas.microsoft.com/ws/2006/05/rm</span></span>|  
|<span data-ttu-id="62055-117">s</span><span class="sxs-lookup"><span data-stu-id="62055-117">s</span></span>|<span data-ttu-id="62055-118">http://www.w3.org/2003/05/soap-envelope</span><span class="sxs-lookup"><span data-stu-id="62055-118">http://www.w3.org/2003/05/soap-envelope</span></span>|  
|<span data-ttu-id="62055-119">wsa</span><span class="sxs-lookup"><span data-stu-id="62055-119">wsa</span></span>|<span data-ttu-id="62055-120">http://schemas.xmlsoap.org/ws/2005/08/addressing</span><span class="sxs-lookup"><span data-stu-id="62055-120">http://schemas.xmlsoap.org/ws/2005/08/addressing</span></span>|  
|<span data-ttu-id="62055-121">wsse</span><span class="sxs-lookup"><span data-stu-id="62055-121">wsse</span></span>|<span data-ttu-id="62055-122">http://docs.oasis-open.org/wss/2004/01/oasis-200401-wssecurity-secext-1.0.xsd</span><span class="sxs-lookup"><span data-stu-id="62055-122">http://docs.oasis-open.org/wss/2004/01/oasis-200401-wssecurity-secext-1.0.xsd</span></span>|  
|<span data-ttu-id="62055-123">wsrmp</span><span class="sxs-lookup"><span data-stu-id="62055-123">wsrmp</span></span>|<span data-ttu-id="62055-124">http://docs.oasis-open.org/ws-rx/wsrmp/200702</span><span class="sxs-lookup"><span data-stu-id="62055-124">http://docs.oasis-open.org/ws-rx/wsrmp/200702</span></span>|  
|<span data-ttu-id="62055-125">netrmp</span><span class="sxs-lookup"><span data-stu-id="62055-125">netrmp</span></span>|<span data-ttu-id="62055-126">http://schemas.microsoft.com/ws-rx/wsrmp/200702</span><span class="sxs-lookup"><span data-stu-id="62055-126">http://schemas.microsoft.com/ws-rx/wsrmp/200702</span></span>|  
|<span data-ttu-id="62055-127">wsp</span><span class="sxs-lookup"><span data-stu-id="62055-127">wsp</span></span>|<span data-ttu-id="62055-128">(WS-Policy 1.2 ou WS-Policy 1.5)</span><span class="sxs-lookup"><span data-stu-id="62055-128">(Either WS-Policy 1.2 or WS-Policy 1.5)</span></span>|  
  
## <a name="messaging"></a><span data-ttu-id="62055-129">Messagerie</span><span class="sxs-lookup"><span data-stu-id="62055-129">Messaging</span></span>  
  
### <a name="sequence-creation"></a><span data-ttu-id="62055-130">Création de la séquence</span><span class="sxs-lookup"><span data-stu-id="62055-130">Sequence Creation</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="62055-131"> implémente des messages `CreateSequence` et `CreateSequenceResponse` pour établir une séquence de messagerie fiable.</span><span class="sxs-lookup"><span data-stu-id="62055-131"> implements `CreateSequence` and `CreateSequenceResponse` messages to establish a reliable messaging sequence.</span></span> <span data-ttu-id="62055-132">Les contraintes suivantes s'appliquent :</span><span class="sxs-lookup"><span data-stu-id="62055-132">The following constraints apply:</span></span>  
  
-   <span data-ttu-id="62055-133">B1101 : l'initiateur [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] utilise la même référence de point de terminaison que les `CreateSequence`, `ReplyTo` et `AcksTo` du message `Offer/Endpoint`.</span><span class="sxs-lookup"><span data-stu-id="62055-133">B1101: The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator uses the same endpoint reference as the `CreateSequence` message’s `ReplyTo`, `AcksTo` and `Offer/Endpoint`.</span></span>  
  
-   <span data-ttu-id="62055-134">R1102 : les références de point de terminaison `AcksTo`, `ReplyTo` et `Offer/Endpoint` dans le message `CreateSequence` doivent avoir des valeurs d'adresse avec des représentations sous forme de chaîne identiques qui correspondent à l'octet.</span><span class="sxs-lookup"><span data-stu-id="62055-134">R1102: The `AcksTo`, `ReplyTo` and `Offer/Endpoint` endpoint references in the `CreateSequence` message must have address values with identical string representations such that they match the octet-wise.</span></span>  
  
    -   <span data-ttu-id="62055-135">Le répondeur [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] vérifie que la partie URI des références de point de terminaison `AcksTo`, `ReplyTo` et `Endpoint` sont identiques avant de créer une séquence.</span><span class="sxs-lookup"><span data-stu-id="62055-135">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder verifies that the URI portion of the `AcksTo`, `ReplyTo` and `Endpoint` endpoint references are identical before creating a sequence.</span></span>  
  
-   <span data-ttu-id="62055-136">R1103 : les références de point de terminaison `AcksTo`, `ReplyTo` et `Offer/Endpoint` dans le message `CreateSequence` doivent avoir le même jeu de paramètres de référence.</span><span class="sxs-lookup"><span data-stu-id="62055-136">R1103: The `AcksTo`, `ReplyTo` and `Offer/Endpoint` endpoint references in the `CreateSequence` message should have the same set of reference parameters.</span></span>  
  
    -   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="62055-137"> n'applique pas, mais suppose que les paramètres de référence des références de point de terminaison `AcksTo`, `ReplyTo` et `Offer/Endpoint` sur `CreateSequence` sont identiques et utilise des paramètres de référence à partir de la référence de point de terminaison `ReplyTo` pour les messages d'accusé de réception et de séquence de conversion.</span><span class="sxs-lookup"><span data-stu-id="62055-137"> does not enforce, but assumes that reference parameters of the `AcksTo`, `ReplyTo` and `Offer/Endpoint` endpoint references on `CreateSequence` are identical and uses reference parameters from the `ReplyTo` endpoint reference for acknowledgements and converse sequence messages.</span></span>  
  
-   <span data-ttu-id="62055-138">B1104 : l'initiateur [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ne génère pas l'élément `Expires` ou `Offer/Expires` facultatif dans le message `CreateSequence`.</span><span class="sxs-lookup"><span data-stu-id="62055-138">B1104: The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator does not generate the optional `Expires` or `Offer/Expires` element in the `CreateSequence` message.</span></span>  
  
-   <span data-ttu-id="62055-139">B1105 : lors de l'accès au message `CreateSequence`, le répondeur [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] utilise la valeur `Expires` dans l'élément `CreateSequence` comme valeur `Expires` dans l'élément `CreateSequenceResponse`.</span><span class="sxs-lookup"><span data-stu-id="62055-139">B1105: When accessing the `CreateSequence` message, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder uses the `Expires` value in the `CreateSequence` element as the `Expires` value in the `CreateSequenceResponse` element.</span></span> <span data-ttu-id="62055-140">Sinon, le répondeur [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] lit et ignore les valeurs `Expires` et `Offer/Expires`.</span><span class="sxs-lookup"><span data-stu-id="62055-140">Otherwise, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder reads and ignores the `Expires` and `Offer/Expires` values.</span></span>  
  
-   <span data-ttu-id="62055-141">B1106 : lors de l'accès au message `CreateSequenceResponse`, l'initiateur [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] lit la valeur `Expires` facultative mais ne l'utilise pas.</span><span class="sxs-lookup"><span data-stu-id="62055-141">B1106: When accessing the `CreateSequenceResponse` message, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator reads the optional `Expires` value but does not use it.</span></span>  
  
-   <span data-ttu-id="62055-142">B1107 : l'initiateur et le répondeur [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] génèrent toujours l'élément `IncompleteSequenceBehavior` facultatif dans les éléments `CreateSequence/Offer` et `CreateSequenceResponse`.</span><span class="sxs-lookup"><span data-stu-id="62055-142">B1107: The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator and Responder always generate the optional `IncompleteSequenceBehavior` element in the `CreateSequence/Offer` and `CreateSequenceResponse` elements.</span></span>  
  
-   <span data-ttu-id="62055-143">B1108 : [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] utilise uniquement les valeurs `DiscardFollowingFirstGap` et `NoDiscard` dans l'élément `IncompleteSequenceBehavior`.</span><span class="sxs-lookup"><span data-stu-id="62055-143">B1108: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uses only the `DiscardFollowingFirstGap` and `NoDiscard` values in the `IncompleteSequenceBehavior` element.</span></span>  
  
    -   <span data-ttu-id="62055-144">WS-ReliableMessaging utilise le mécanisme `Offer` pour établir deux séquences corrélées réciproques qui forment une session.</span><span class="sxs-lookup"><span data-stu-id="62055-144">WS-ReliableMessaging utilizes the `Offer` mechanism to establish the two converse correlated sequences that form a session.</span></span>  
  
-   <span data-ttu-id="62055-145">B1109 : si `CreateSequence` contient un élément `Offer`, le répondeur [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] unidirectionnel rejette la séquence présentée en répondant avec un `CreateSequenceResponse` sans un élément `Accept`.</span><span class="sxs-lookup"><span data-stu-id="62055-145">B1109: If `CreateSequence` contains an `Offer` element, the one way [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder rejects the offered sequence by responding with a `CreateSequenceResponse` without an `Accept` element.</span></span>  
  
-   <span data-ttu-id="62055-146">B1110 : si un répondeur de messagerie fiable rejette la séquence présentée, l'initiateur [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] fait échouer la séquence récemment établie.</span><span class="sxs-lookup"><span data-stu-id="62055-146">B1110: If a Reliable Messaging Responder rejects the offered sequence, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator faults the newly established sequence.</span></span>  
  
-   <span data-ttu-id="62055-147">B1111 : si `CreateSequence` ne contient pas d'élément `Offer`, le répondeur [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] bidirectionnel rejette la séquence présentée en répondant par une erreur `CreateSequenceRefused`.</span><span class="sxs-lookup"><span data-stu-id="62055-147">B1111: If `CreateSequence` does not contain an `Offer` element, the two-way [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder rejects the offered sequence by responding with a `CreateSequenceRefused` fault.</span></span>  
  
-   <span data-ttu-id="62055-148">R1112 : lorsque deux séquences réciproques sont établies à l'aide du mécanisme `Offer`, la propriété `[address]` de la référence du point de terminaison `CreateSequenceResponse/Accept/AcksTo` doit correspondre à l'URI de destination du message `CreateSequence` octet par octet.</span><span class="sxs-lookup"><span data-stu-id="62055-148">R1112: When two converse sequences are established using the `Offer` mechanism, the `[address]` property of the `CreateSequenceResponse/Accept/AcksTo` endpoint reference must match the destination URI of the `CreateSequence` message byte for byte.</span></span>  
  
-   <span data-ttu-id="62055-149">R1113 : lorsque deux séquences réciproques sont établies à l'aide du mécanisme `Offer`, tous les messages sur les deux séquences circulant de l'initiateur au répondeur doivent être envoyés à la même référence de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="62055-149">R1113: When two converse sequences are established using the `Offer` mechanism, all messages on both sequences flowing from the Initiator to the Responder must be sent to the same endpoint reference.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="62055-150"> utilise WS-ReliableMessaging pour établir des sessions fiables entre l'initiateur et le répondeur.</span><span class="sxs-lookup"><span data-stu-id="62055-150"> uses WS-ReliableMessaging to establish reliable sessions between the Initiator and the Responder.</span></span> <span data-ttu-id="62055-151">L'implémentation WS-ReliableMessaging [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] fournit une session fiable pour les modèles de messagerie en mode duplex intégral, demande-réponse et unidirectionnels.</span><span class="sxs-lookup"><span data-stu-id="62055-151">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WS-ReliableMessaging implementation provides a reliable session for one-way, request-reply and full duplex messaging patterns.</span></span> <span data-ttu-id="62055-152">Le mécanisme WS-ReliableMessaging `Offer` sur `CreateSequence` et `CreateSequenceResponse` vous permet d'établir deux séquences réciproques corrélées et fournit un protocole de session qui convient à tous les points de terminaison de message.</span><span class="sxs-lookup"><span data-stu-id="62055-152">The WS-ReliableMessaging `Offer` mechanism on `CreateSequence` and `CreateSequenceResponse` lets you establish two correlated converse sequences and provides a session protocol that is suitable for all message endpoints.</span></span> <span data-ttu-id="62055-153">Comme [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] fournit une garantie de sécurité pour ce type de session qui inclut la protection de bout en bout de l'intégrité de session, il est pratique de s'assurer que les messages prévus pour le même correspondant arrivent à la même destination.</span><span class="sxs-lookup"><span data-stu-id="62055-153">Because [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] provides a security guarantee for such a session including end-to-end protection for session integrity, it is practical to ensure that messages intended for the same party arrive at the same destination.</span></span> <span data-ttu-id="62055-154">Cela autorise également la « superposition » des accusés de réception de séquence sur les messages d'application.</span><span class="sxs-lookup"><span data-stu-id="62055-154">This also allows "piggy-backing" of sequence acknowledgements on application messages.</span></span> <span data-ttu-id="62055-155">Par conséquent, les contraintes R1102, R1112 et R1113 s’appliquent à [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="62055-155">Therefore, constraints R1102, R1112, and R1113 apply to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
 <span data-ttu-id="62055-156">Exemple de message `CreateSequence`.</span><span class="sxs-lookup"><span data-stu-id="62055-156">An example of a `CreateSequence` message.</span></span>  
  
```xml  
<s:Envelope>  
  <s:Header>  
    <wsa:Action s:mustUnderstand="1">http://docs.oasis-open.org/ws-rx/wsrm/200702/CreateSequence</wsa:Action>  
    <wsa:MessageID>urn:uuid:949cca61-8813-42ff-ab33-18d9e3fa82fa</wsa:MessageID>  
    <wsa:ReplyTo>  
        <wsa:Address>http://Business456.com/clientA</wsa:Address>   
    </wsa:ReplyTo>  
    <wsa:To s:mustUnderstand="1">http://BusinessABC.com/serviceA</wsa:To>  
  </s:Header>  
  <s:Body>  
    <wsrm:CreateSequence>  
      <wsrm:AcksTo>  
        <wsa:Address>http://Business456.com/clientA</wsa:Address>  
      </wsrm:AcksTo>  
      <wsrm:Offer>  
        <wsrm:Identifier>urn:uuid:066b4730-fc82-458a-a5c1-210be4fb4e4e</wsrm:Identifier>  
        <wsrm:Endpoint>  
          <wsa:Address>http://Business456.com/clientA</wsa:Address>  
        </wsrm:Endpoint>  
        <wsrm:IncompleteSequenceBehavior>DiscardFollowingFirstGap</wsrm:IncompleteSequenceBehavior>  
      </wsrm:Offer>  
    </wsrm:CreateSequence>  
  </s:Body>  
</s:Envelope>  
```  
  
 <span data-ttu-id="62055-157">Exemple de message `CreateSequenceResponse`.</span><span class="sxs-lookup"><span data-stu-id="62055-157">An example of a `CreateSequenceResponse` message.</span></span>  
  
```xml  
<s:Envelope>  
  <s:Header>  
    <wsa:Action s:mustUnderstand="1">http://docs.oasis-open.org/ws-rx/wsrm/200702/CreateSequenceResponse</wsa:Action>  
    <wsa:RelatesTo>urn:uuid:949cca61-8813-42ff-ab33-18d9e3fa82fa</wsa:RelatesTo>  
    <wsa:To s:mustUnderstand="1">http://Business456.com/clientA</wsa:To>  
  </s:Header>  
  <s:Body>  
    <wsrm:CreateSequenceResponse>  
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
      <wsrm:IncompleteSequenceBehavior>DiscardFollowingFirstGap</wsrm:IncompleteSequenceBehavior>  
      <wsrm:Accept>  
        <wsrm:AcksTo>  
          <wsa:Address>http://BusinessABC.com/serviceA</wsa:Address>  
        </wsrm:AcksTo>  
      </wsrm:Accept>  
    </wsrm:CreateSequenceResponse>  
  </s:Body>  
</s:Envelope>  
```  
  
### <a name="closing-a-sequence"></a><span data-ttu-id="62055-158">Fermeture d'une séquence</span><span class="sxs-lookup"><span data-stu-id="62055-158">Closing a Sequence</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="62055-159"> utilise les messages `CloseSequence` et `CloseSequenceResponse` pour un arrêt initié par la source de la messagerie fiable.</span><span class="sxs-lookup"><span data-stu-id="62055-159"> uses the `CloseSequence` and `CloseSequenceResponse` messages for a Reliable Messaging source-initiated shutdown.</span></span> <span data-ttu-id="62055-160">La destination de messagerie fiable [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] n'initie pas l'arrêt, et la source de messagerie fiable [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ne prend pas en charge un arrêt initié par la destination de la messagerie fiable.</span><span class="sxs-lookup"><span data-stu-id="62055-160">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Reliable Messaging destination does not initiate shutdown and the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Reliable Messaging source does not support a Reliable Messaging destination-initiated shutdown.</span></span> <span data-ttu-id="62055-161">Les contraintes suivantes s'appliquent :</span><span class="sxs-lookup"><span data-stu-id="62055-161">The following constraints apply:</span></span>  
  
-   <span data-ttu-id="62055-162">B1201 : la source de messagerie fiable [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] envoie toujours un message `CloseSequence` pour arrêter la séquence.</span><span class="sxs-lookup"><span data-stu-id="62055-162">B1201: The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Reliable Messaging source always sends a `CloseSequence` message to shut down the sequence.</span></span>  
  
-   <span data-ttu-id="62055-163">B1202 : la source de la messagerie fiable attend l'accusé de réception de l'ensemble complet des messages de séquence avant d'envoyer le message `CloseSequence`.</span><span class="sxs-lookup"><span data-stu-id="62055-163">B1202: The Reliable Messaging source waits for acknowledgement of the full range of sequence messages before sending the `CloseSequence` message.</span></span>  
  
-   <span data-ttu-id="62055-164">B1203 : la source de messagerie fiable inclut toujours l'élément `LastMsgNumber` facultatif sauf si la séquence ne contient pas de messages.</span><span class="sxs-lookup"><span data-stu-id="62055-164">B1203: The Reliable Messaging source always includes the optional `LastMsgNumber` element unless the sequence does not contain messages.</span></span>  
  
-   <span data-ttu-id="62055-165">R1204 : la destination de messagerie fiable ne doit pas initier l'arrêt en envoyant un message `CloseSequence`.</span><span class="sxs-lookup"><span data-stu-id="62055-165">R1204: The Reliable Messaging destination must not initiate shutdown by sending a `CloseSequence` message.</span></span>  
  
-   <span data-ttu-id="62055-166">B1205 : à la réception d'un message `CloseSequence`, la source de messagerie fiable [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] considère que la séquence est incomplète et envoie une erreur.</span><span class="sxs-lookup"><span data-stu-id="62055-166">B1205: Upon receiving a `CloseSequence` message, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Reliable Messaging source considers the sequence incomplete and sends a fault.</span></span>  
  
 <span data-ttu-id="62055-167">Exemple de message `CloseSequence`.</span><span class="sxs-lookup"><span data-stu-id="62055-167">An example of a `CloseSequence` message.</span></span>  
  
```xml  
<s:Envelope>  
  <s:Header>  
    <wsa:Action s:mustUnderstand="1">http://docs.oasis-open.org/ws-rx/wsrm/200702/CloseSequence</wsa:Action>  
    <wsa:MessageID>urn:uuid:6ce1d4c3-e1c1-474f-a8c9-4210e37f7877</wsa:MessageID>  
    <wsa:ReplyTo>  
      <wsa:Address>http://Business456.com/clientA</wsa:Address>  
    </wsa:ReplyTo>  
    <wsa:To s:mustUnderstand="1">http://BusinessABC.com/serviceA</wsa:To>  
  </s:Header>  
  <s:Body>  
    <wsrm:CloseSequence>  
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
      <wsrm:LastMsgNumber>30</wsrm:LastMsgNumber>  
    </wsrm:CloseSequence>  
  </s:Body>  
</s:Envelope>  
Example CloseSequenceResponse message:  
<s:Envelope>  
  <s:Header>  
    <wsrm:SequenceAcknowledgement>  
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
      <wsrm:AcknowledgementRange Lower="1" Upper="30"></wsrm:AcknowledgementRange>  
      <wsrm:Final></wsrm:Final>  
      <netrm:BufferRemaining>8</netrm:BufferRemaining>  
    </wsrm:SequenceAcknowledgement>  
    <wsa:Action s:mustUnderstand="1">http://docs.oasis-open.org/ws-rx/wsrm/200702/CloseSequenceResponse</wsa:Action>  
    <wsa:RelatesTo>urn:uuid:6ce1d4c3-e1c1-474f-a8c9-4210e37f7877</wsa:RelatesTo>  
    <wsa:To s:mustUnderstand="1">http://Business456.com/clientA</wsa:To>  
  </s:Header>  
  <s:Body>  
    <wsrm:CloseSequenceResponse>  
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
    </wsrm:CloseSequenceResponse>  
  </s:Body>  
</s:Envelope>  
```  
  
### <a name="sequence-termination"></a><span data-ttu-id="62055-168">Séquence d'arrêt</span><span class="sxs-lookup"><span data-stu-id="62055-168">Sequence Termination</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="62055-169"> utilise essentiellement la négociation de sécurité `TerminateSequence/TerminateSequenceResponse` après avoir complété la négociation de sécurité `CloseSequence/CloseSequenceResponse`.</span><span class="sxs-lookup"><span data-stu-id="62055-169"> primarily uses the `TerminateSequence/TerminateSequenceResponse` handshake after completing the `CloseSequence/CloseSequenceResponse` handshake.</span></span> <span data-ttu-id="62055-170">La destination de messagerie fiable [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] n'initie pas l'arrêt, et la source de messagerie fiable ne prend pas en charge un arrêt initié par la destination de la messagerie fiable.</span><span class="sxs-lookup"><span data-stu-id="62055-170">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Reliable Messaging destination does not initiate termination and the Reliable Messaging source does not support a Reliable Messaging destination-initiated termination.</span></span> <span data-ttu-id="62055-171">Les contraintes suivantes s'appliquent :</span><span class="sxs-lookup"><span data-stu-id="62055-171">The following constraints apply:</span></span>  
  
-   <span data-ttu-id="62055-172">B1301 : l'initiateur [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] envoie seulement le message `TerminateSequence` après l'achèvement correct de la négociation de sécurité `CloseSequence/CloseSequenceResponse`.</span><span class="sxs-lookup"><span data-stu-id="62055-172">B1301: The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator only sends the `TerminateSequence` message after the successful completion of the `CloseSequence/CloseSequenceResponse` handshake.</span></span>  
  
-   <span data-ttu-id="62055-173">R1302 : [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] valide que l'élément `LastMsgNumber` est cohérent avec tous les messages `CloseSequence` et `TerminateSequence` pour une séquence donnée.</span><span class="sxs-lookup"><span data-stu-id="62055-173">R1302: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] validates that the `LastMsgNumber` element is consistent across all `CloseSequence` and `TerminateSequence` messages for a given sequence.</span></span> <span data-ttu-id="62055-174">Cela signifie que `LastMsgNumber` est soit absent sur tous les messages `CloseSequence` et `TerminateSequence`, soit présent et identique sur tous les messages `CloseSequence` et `TerminateSequence`.</span><span class="sxs-lookup"><span data-stu-id="62055-174">This means that `LastMsgNumber` is either not present on all `CloseSequence` and `TerminateSequence` messages, or it is present and identical on all `CloseSequence` and `TerminateSequence` messages.</span></span>  
  
-   <span data-ttu-id="62055-175">B1303 : à la réception d'un message `TerminateSequence` après la négociation de sécurité `CloseSequence/CloseSequenceResponse`, la destination de messagerie fiable répond avec un message `TerminateSequenceResponse`.</span><span class="sxs-lookup"><span data-stu-id="62055-175">B1303: When receiving a `TerminateSequence` message after the `CloseSequence/CloseSequenceResponse` handshake, the Reliable Messaging destination responds with a `TerminateSequenceResponse` message.</span></span> <span data-ttu-id="62055-176">Étant donné que la source de messagerie fiable a l'accusé de réception final avant d'envoyer le message `TerminateSequence`, la destination de messagerie fiable sait sans doute que la séquence se termine, et libère immédiatement les ressources.</span><span class="sxs-lookup"><span data-stu-id="62055-176">Because the Reliable Messaging source has the final acknowledgement before sending the `TerminateSequence` message, the Reliable Messaging destination knows without doubt that the sequence ends, and reclaims resources immediately.</span></span>  
  
-   <span data-ttu-id="62055-177">B13043  : à la réception d'un message `TerminateSequence` avant la négociation de sécurité `CloseSequence/CloseSequenceResponse`, la destination de messagerie fiable [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] répond avec un message `TerminateSequenceResponse`.</span><span class="sxs-lookup"><span data-stu-id="62055-177">B1304: When receiving a `TerminateSequence` message prior to the `CloseSequence/CloseSequenceResponse` handshake, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Reliable Messaging destination responds with a `TerminateSequenceResponse` message.</span></span> <span data-ttu-id="62055-178">Si la destination de messagerie fiable détermine que la séquence ne contient aucune incohérence, elle attend l'heure spécifiée par la destination d'une application avant de libérer des ressources afin de permettre au client de recevoir l'accusé de réception final.</span><span class="sxs-lookup"><span data-stu-id="62055-178">If the Reliable Messaging destination determines that there are no inconsistencies in the sequence, the Reliable Messaging destination waits for an application destination-specified time before reclaiming resources, to allow the client the chance to receive the final acknowledgement.</span></span> <span data-ttu-id="62055-179">Sinon, la destination de messagerie fiable libère immédiatement des ressources et indique à la destination d'application que la séquence se termine en déclenchant l'événement `Faulted`.</span><span class="sxs-lookup"><span data-stu-id="62055-179">Otherwise, the Reliable Messaging destination reclaims resources immediately and indicates to the application destination that the sequence ends with doubt by raising the `Faulted` event.</span></span>  
  
 <span data-ttu-id="62055-180">Exemple de message `TerminateSequence`.</span><span class="sxs-lookup"><span data-stu-id="62055-180">An example of a `TerminateSequence` message.</span></span>  
  
```xml  
<s:Envelope>  
  <s:Header>  
    <wsa:Action s:mustUnderstand="1">http://docs.oasis-open.org/ws-rx/wsrm/200702/TerminateSequence</wsa:Action>  
    <wsa:MessageID>urn:uuid:3597a398-4f3c-40f4-9335-8f1515572fdf</wsa:MessageID>  
    <wsa:ReplyTo>  
      <wsa:Address>http://Business456.com/clientA</wsa:Address>  
    </wsa:ReplyTo>  
    <wsa:To s:mustUnderstand="1">http://BusinessABC.com/serviceA</wsa:To>  
  </s:Header>  
  <s:Body>  
    <wsrm:TerminateSequence>  
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
      <wsrm:LastMsgNumber>30</wsrm:LastMsgNumber>  
      </wsrm:TerminateSequence>  
  </s:Body>  
</s:Envelope>  
Example TerminateSequenceResponse message:  
<s:Envelope>  
  <s:Header>  
    <wsrm:SequenceAcknowledgement>  
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
      <wsrm:AcknowledgementRange Lower="1" Upper="30"></wsrm:AcknowledgementRange>  
      <wsrm:Final></wsrm:Final>  
      <netrm:BufferRemaining>8</netrm:BufferRemaining>  
    </wsrm:SequenceAcknowledgement>  
    <wsa:Action s:mustUnderstand="1">http://docs.oasis-open.org/ws-rx/wsrm/200702/TerminateSequenceResponse</wsa:Action>  
    <wsa:RelatesTo>urn:uuid:3597a398-4f3c-40f4-9335-8f1515572fdf</wsa:RelatesTo>  
    <wsa:To s:mustUnderstand="1">://Business456.com/clientA</wsa:To>  
  </s:Header>  
  <s:Body>  
    <wsrm:TerminateSequenceResponse>  
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
    </wsrm:TerminateSequenceResponse>  
  </s:Body>  
</s:Envelope>  
```  
  
### <a name="sequences"></a><span data-ttu-id="62055-181">Séquences</span><span class="sxs-lookup"><span data-stu-id="62055-181">Sequences</span></span>  
 <span data-ttu-id="62055-182">Voici une liste des contraintes qui s'appliquent aux séquences :</span><span class="sxs-lookup"><span data-stu-id="62055-182">The following is a list of constraints that apply to sequences:</span></span>  
  
-   <span data-ttu-id="62055-183">B1401 :[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] génère et accède à des numéros de séquence ne dépassant pas `xs:long`de valeur inclusive maximale, 9223372036854775807.</span><span class="sxs-lookup"><span data-stu-id="62055-183">B1401:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generates and accesses sequence numbers no higher than `xs:long`’s maximum inclusive value, 9223372036854775807.</span></span>  
  
 <span data-ttu-id="62055-184">Exemple d'en-tête `Sequence`.</span><span class="sxs-lookup"><span data-stu-id="62055-184">An example of a `Sequence` header.</span></span>  
  
```xml  
<wsrm:Sequence s:mustUnderstand="1">  
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
  <wsrm:MessageNumber>1</wsrm:MessageNumber>  
</wsrm:Sequence>  
```  
  
### <a name="request-acknowledgement"></a><span data-ttu-id="62055-185">Demander un accusé de réception</span><span class="sxs-lookup"><span data-stu-id="62055-185">Request Acknowledgement</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="62055-186"> utilise l'en-tête `AckRequested` comme un mécanisme persistant.</span><span class="sxs-lookup"><span data-stu-id="62055-186"> uses the `AckRequested` header as a keep-alive mechanism.</span></span>  
  
 <span data-ttu-id="62055-187">Exemple d'en-tête `AckRequested`.</span><span class="sxs-lookup"><span data-stu-id="62055-187">An example of an `AckRequested` header.</span></span>  
  
```xml  
<wsrm:AckRequested>  
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
</wsrm:AckRequested>  
```  
  
### <a name="sequenceacknowledgement"></a><span data-ttu-id="62055-188">SequenceAcknowledgement</span><span class="sxs-lookup"><span data-stu-id="62055-188">SequenceAcknowledgement</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="62055-189"> utilise un mécanisme de « superposition » pour les accusés de réception de séquence fournis dans la messagerie WS-Reliable.</span><span class="sxs-lookup"><span data-stu-id="62055-189"> uses a "piggy-back" mechanism for sequence acknowledgements provided in WS-Reliable Messaging.</span></span> <span data-ttu-id="62055-190">Les contraintes suivantes s'appliquent :</span><span class="sxs-lookup"><span data-stu-id="62055-190">The following constraints apply:</span></span>  
  
-   <span data-ttu-id="62055-191">R1601 : Lorsque deux séquences réciproques sont établies à l’aide de la `Offer` mécanisme, la `SequenceAcknowledgement` en-tête peut être inclus dans n’importe quel message d’application transmis au destinataire prévu.</span><span class="sxs-lookup"><span data-stu-id="62055-191">R1601: When two converse sequences are established using the `Offer` mechanism, the `SequenceAcknowledgement` header may be included in any application message transmitted to the intended recipient.</span></span> <span data-ttu-id="62055-192">Le point de terminaison distant doit être en mesure d'accéder à un en-tête `SequenceAcknowledgement` superposé.</span><span class="sxs-lookup"><span data-stu-id="62055-192">The remote endpoint must be able to access a piggybacked `SequenceAcknowledgement` header.</span></span>  
  
-   <span data-ttu-id="62055-193">B1602 : [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ne génère pas les en-têtes `SequenceAcknowledgement` qui contiennent des éléments `Nack`.</span><span class="sxs-lookup"><span data-stu-id="62055-193">B1602: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] does not generate `SequenceAcknowledgement` headers that contain `Nack` elements.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="62055-194"> valide que chaque élément `Nack` contient un numéro de séquence, mais sinon ignore l'élément et la valeur `Nack`.</span><span class="sxs-lookup"><span data-stu-id="62055-194"> validates that each `Nack` element contains a sequence number, but otherwise ignores the `Nack` element and value.</span></span>  
  
 <span data-ttu-id="62055-195">Exemple d'en-tête `SequenceAcknowledgement`.</span><span class="sxs-lookup"><span data-stu-id="62055-195">An example of a `SequenceAcknowledgement` header.</span></span>  
  
```xml  
<wsrm:SequenceAcknowledgement>  
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
  <wsrm:AcknowledgementRange Lower="1" Upper="1"></wsrm:AcknowledgementRange>  
</wsrm:SequenceAcknowledgement>  
```  
  
### <a name="ws-reliablemessaging-faults"></a><span data-ttu-id="62055-196">Erreurs de la messagerie WS-Reliable</span><span class="sxs-lookup"><span data-stu-id="62055-196">WS-ReliableMessaging Faults</span></span>  
 <span data-ttu-id="62055-197">Les éléments suivants sont une liste des contraintes qui s'appliquent à l'implémentation [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] des erreurs WS-ReliableMessaging.</span><span class="sxs-lookup"><span data-stu-id="62055-197">The following is a list of constraints that apply to the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] implementation of WS-ReliableMessaging faults.</span></span> <span data-ttu-id="62055-198">Les contraintes suivantes s'appliquent :</span><span class="sxs-lookup"><span data-stu-id="62055-198">The following constraints apply:</span></span>  
  
-   <span data-ttu-id="62055-199">B1701 : [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ne génère pas `MessageNumberRollover` erreurs.</span><span class="sxs-lookup"><span data-stu-id="62055-199">B1701: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] does not generate `MessageNumberRollover` faults.</span></span>  
  
-   <span data-ttu-id="62055-200">B1702 : sur SOAP 1.2, lorsque le point de terminaison de service atteint sa limite de connexion et ne peut pas traiter de nouvelles connexions, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] génère un sous-code d'erreur `CreateSequenceRefused` imbriqué, `netrm:ConnectionLimitReached`, comme indiqué dans l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="62055-200">B1702: Over SOAP 1.2, when the service endpoint reaches its connection limit and cannot process new connections, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generates a nested `CreateSequenceRefused` fault subcode, `netrm:ConnectionLimitReached`, as shown in the following example.</span></span>  
  
```xml  
<s:Envelope>  
  <s:Header>  
    <wsa:Action>http://docs.oasis-open.org/ws-rx/wsrm/200702/fault</wsa:Action>  
  </s:Header>  
  <s:Body>  
    <s:Fault>  
      <s:Code>  
        <s:Value>s:Receiver</s:Value>  
        <s:Subcode>  
          <s:Value>wsrm:CreateSequenceRefused</s:Value>  
          <s:Subcode>  
            <s:Value>netrm:ConnectionLimitReached</s:Value>  
          </s:Subcode>  
        </s:Subcode>  
      </s:Code>  
      <s:Reason>  
        <s:Text xml:lang="en">Server 'http://BusinessABC.com/serviceA' is too busy to process this request. Try again later.</s:Text>  
      </s:Reason>  
    </s:Fault>  
  </s:Body>  
</s:Envelope>  
```  
  
### <a name="ws-addressing-faults"></a><span data-ttu-id="62055-201">Erreurs WS-Addressing</span><span class="sxs-lookup"><span data-stu-id="62055-201">WS-Addressing Faults</span></span>  
 <span data-ttu-id="62055-202">Étant donné que WS-ReliableMessaging utilise WS-Addressing, l'implémentation WS-ReliableMessaging [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] peut générer et transmettre des erreurs WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="62055-202">Because WS-ReliableMessaging uses WS-Addressing, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WS-ReliableMessaging implementation may generate and transmit WS-Addressing faults.</span></span> <span data-ttu-id="62055-203">Cette section traite des erreurs WS-Addressing que [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] génère explicitement et transmet au niveau de la couche WS-ReliableMessaging :</span><span class="sxs-lookup"><span data-stu-id="62055-203">This section covers the WS-Addressing faults that [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] explicitly generates and transmits at the WS-ReliableMessaging layer:</span></span>  
  
-   <span data-ttu-id="62055-204">B1801 :[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] génère et transmet le `Message Addressing Header Required` d’erreur lorsque l’une des valeurs suivantes est vraie :</span><span class="sxs-lookup"><span data-stu-id="62055-204">B1801:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generates and transmits the `Message Addressing Header Required` fault when one of the following is true:</span></span>  
  
    -   <span data-ttu-id="62055-205">Il manque un en-tête `CreateSequence` à un message `CloseSequence`, `TerminateSequence` ou `MessageId`.</span><span class="sxs-lookup"><span data-stu-id="62055-205">A `CreateSequence`, `CloseSequence` or `TerminateSequence` message is missing a `MessageId` header.</span></span>  
  
    -   <span data-ttu-id="62055-206">Il manque un en-tête `CreateSequence` à un message `CloseSequence`, `TerminateSequence` ou `ReplyTo`.</span><span class="sxs-lookup"><span data-stu-id="62055-206">A `CreateSequence`, `CloseSequence` or `TerminateSequence` message is missing a `ReplyTo` header.</span></span>  
  
    -   <span data-ttu-id="62055-207">Il manque un en-tête `CreateSequenceResponse` à un message `CloseSequenceResponse`, `TerminateSequenceResponse` ou `RelatesTo`.</span><span class="sxs-lookup"><span data-stu-id="62055-207">A `CreateSequenceResponse`, `CloseSequenceResponse`, or `TerminateSequenceResponse` message is missing a `RelatesTo` header.</span></span>  
  
-   <span data-ttu-id="62055-208">B1802 :[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] génère et transmet le `Endpoint Unavailable` indiquent il n’y a aucun point de terminaison qui écoute la panne peut traiter la séquence en fonction de l’examen des en-têtes d’adressage dans le `CreateSequence` message.</span><span class="sxs-lookup"><span data-stu-id="62055-208">B1802:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generates and transmits the `Endpoint Unavailable` fault to indicate there is no endpoint listening that can process the sequence based on examination of the addressing headers in the `CreateSequence` message.</span></span>  
  
## <a name="protocol-composition"></a><span data-ttu-id="62055-209">Composition du protocole</span><span class="sxs-lookup"><span data-stu-id="62055-209">Protocol Composition</span></span>  
  
### <a name="composition-with-ws-addressing"></a><span data-ttu-id="62055-210">Composition avec WS-Addressing</span><span class="sxs-lookup"><span data-stu-id="62055-210">Composition with WS-Addressing</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="62055-211"> prend en charge deux versions de WS-Addressing : WS-Addressing 2004/08 [WS-ADDR] et W3C WS-Addressing 1.0 Recommendations [WS-ADDR-CORE] et [WS-ADDR-SOAP]</span><span class="sxs-lookup"><span data-stu-id="62055-211"> supports two versions of WS-Addressing: WS-Addressing 2004/08 [WS-ADDR] and W3C WS-Addressing 1.0 Recommendations [WS-ADDR-CORE] and [WS-ADDR-SOAP].</span></span>  
  
 <span data-ttu-id="62055-212">Si la spécification WS-ReliableMessaging mentionne WS-Addressing 2004/08 uniquement, elle ne limite pas la version WS-Addressing à utiliser.</span><span class="sxs-lookup"><span data-stu-id="62055-212">While the WS-ReliableMessaging specification mentions only WS-Addressing 2004/08, it does not restrict the WS-Addressing version to be used.</span></span> <span data-ttu-id="62055-213">Voici une liste des contraintes qui s'appliquent à [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] :</span><span class="sxs-lookup"><span data-stu-id="62055-213">The following is a list of constraints that apply to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:</span></span>  
  
-   <span data-ttu-id="62055-214">R2101 : WS-Addressing 2004/08 et WS-Addressing 1.0 peuvent être utilisés ensemble avec la messagerie WS-Reliable.</span><span class="sxs-lookup"><span data-stu-id="62055-214">R2101: Both WS-Addressing 2004/08 and WS-Addressing 1.0 can be used with WS-Reliable Messaging.</span></span>  
  
-   <span data-ttu-id="62055-215">R2102 : une version unique de WS-Addressing doit être utilisée dans l'ensemble d'une séquence WS-ReliableMessaging ou une paire de séquences réciproques corrélées à l'aide du mécanisme `Offer`.</span><span class="sxs-lookup"><span data-stu-id="62055-215">R2102: A single version of WS-Addressing must be used throughout a given WS-ReliableMessaging sequence or a pair of converse sequences correlated by using the `Offer` mechanism.</span></span>  
  
### <a name="composition-with-soap"></a><span data-ttu-id="62055-216">Composition avec SOAP</span><span class="sxs-lookup"><span data-stu-id="62055-216">Composition with SOAP</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="62055-217"> prend en charge l'utilisation de SOAP 1.1 et SOAP 1.2 avec la messagerie WS-Reliable.</span><span class="sxs-lookup"><span data-stu-id="62055-217"> supports the use of both SOAP 1.1 and SOAP 1.2 with WS-Reliable Messaging.</span></span>  
  
### <a name="composition-with-ws-security-and-ws-secureconversation"></a><span data-ttu-id="62055-218">Composition avec WS-Security et WS-SecureConversation</span><span class="sxs-lookup"><span data-stu-id="62055-218">Composition with WS-Security and WS-SecureConversation</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="62055-219"> fournit une protection pour les séquences WS-ReliableMessaging en utilisant le transport sécurisé (HTTPS), la composition avec WS-Security, et la composition avec WS-Secture Conversation.</span><span class="sxs-lookup"><span data-stu-id="62055-219"> provides protection for WS-ReliableMessaging sequences by using secure Transport (HTTPS), composition with WS-Security, and composition with WS-Secure Conversation.</span></span> <span data-ttu-id="62055-220">Le protocole WS-ReliableMessaging 1.1, WS-Security 1.1 et le protocole WS-Secure Conversation 1.3 doivent être utilisés ensemble.</span><span class="sxs-lookup"><span data-stu-id="62055-220">The WS-ReliableMessaging 1.1 protocol, WS-Security 1.1 and WS-Secure Conversation 1.3 protocol should be used together.</span></span> <span data-ttu-id="62055-221">Voici une liste des contraintes qui s'appliquent à [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] :</span><span class="sxs-lookup"><span data-stu-id="62055-221">The following is a list of constraints that apply to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:</span></span>  
  
-   <span data-ttu-id="62055-222">R2301 : pour protéger l'intégrité d'une séquence WS-ReliableMessaging en plus de l'intégrité et de la confidentialité des messages individuels, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] requiert l'utilisation de WS-Secure Conversation.</span><span class="sxs-lookup"><span data-stu-id="62055-222">R2301: To protect the integrity of a WS-ReliableMessaging sequence in addition to the integrity and confidentiality of individual messages, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] requires that WS-Secure Conversation must be used.</span></span>  
  
-   <span data-ttu-id="62055-223">R2302:AWS-session de Secure Conversation doit être établie avant d’établir des séquences de WS-ReliableMessaging.</span><span class="sxs-lookup"><span data-stu-id="62055-223">R2302:AWS-Secure Conversation session must be established prior to establishing WS-ReliableMessaging sequence(s).</span></span>  
  
-   <span data-ttu-id="62055-224">R2303 : si la durée de vie de la séquence WS-ReliableMessaging dépasse celle de la session WS-Secure Conversation, le `SecurityContextToken` établi à l'aide de WS-Secure Conversation doit être renouvelé par le biais de la liaison de renouvellement WS-Secure Conversation correspondante.</span><span class="sxs-lookup"><span data-stu-id="62055-224">R2303: If the WS-ReliableMessaging sequence lifetime exceeds the WS-Secure Conversation session’s lifetime, the `SecurityContextToken` established by using WS-Secure Conversation must be renewed by using the corresponding WS-Secure Conversation Renewal binding.</span></span>  
  
-   <span data-ttu-id="62055-225">B2304:WS-ReliableMessaging séquence ou une paire de séquences réciproques corrélées sont toujours liées à une seule session WS-SecureConversation.</span><span class="sxs-lookup"><span data-stu-id="62055-225">B2304:WS-ReliableMessaging sequence or a pair of correlated converse sequences are always bound to a single WS-SecureConversation session.</span></span>  
  
-   <span data-ttu-id="62055-226">R2305 : lorsqu'il est composé avec WS-Secure Conversation, le répondeur [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] requiert que le message `CreateSequence` contienne l'élément `wsse:SecurityTokenReference` et l'en-tête `wsrm:UsesSequenceSTR`.</span><span class="sxs-lookup"><span data-stu-id="62055-226">R2305: When composed with WS-Secure Conversation, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] responder requires that the `CreateSequence` message contain the `wsse:SecurityTokenReference` element and the `wsrm:UsesSequenceSTR` header.</span></span>  
  
 <span data-ttu-id="62055-227">Exemple d'en-tête `UsesSequenceSTR`.</span><span class="sxs-lookup"><span data-stu-id="62055-227">An example of a `UsesSequenceSTR` header.</span></span>  
  
```xml  
<wsrm:UsesSequenceSTR></wsrm:UsesSequenceSTR>  
```  
  
### <a name="composition-with-ssltls-sessions"></a><span data-ttu-id="62055-228">Composition avec les sessions SSL/TLS</span><span class="sxs-lookup"><span data-stu-id="62055-228">Composition with SSL/TLS sessions</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="62055-229"> ne prend pas en charge la composition avec les sessions SSL/TLS :</span><span class="sxs-lookup"><span data-stu-id="62055-229"> does not support composition with SSL/TLS sessions:</span></span>  
  
-   <span data-ttu-id="62055-230">B2401 : [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ne génère pas l'en-tête `wsrm:UsesSequenceSSL`.</span><span class="sxs-lookup"><span data-stu-id="62055-230">B2401: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] does not generate the `wsrm:UsesSequenceSSL` header.</span></span>  
  
-   <span data-ttu-id="62055-231">R2402 : un initiateur de messagerie fiable ne doit pas envoyer de message `CreateSequence` avec un en-tête `wsrm:UsesSequenceSSL` à un répondeur [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="62055-231">R2402: A Reliable Messaging Initiator must not send a `CreateSequence` message with a `wsrm:UsesSequenceSSL` header to a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder.</span></span>  
  
### <a name="composition-with-ws-policy"></a><span data-ttu-id="62055-232">Composition avec WS-Policy</span><span class="sxs-lookup"><span data-stu-id="62055-232">Composition with WS-Policy</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="62055-233"> prend en charge deux versions de WS-Policy : WS-Policy 1.2 et WS-Policy 1.5.</span><span class="sxs-lookup"><span data-stu-id="62055-233"> supports two versions of WS-Policy: WS-Policy 1.2 and WS-Policy 1.5.</span></span>  
  
## <a name="ws-reliablemessaging-ws-policy-assertion"></a><span data-ttu-id="62055-234">Assertion WS-Policy de la messagerie WS-ReliableMessaging</span><span class="sxs-lookup"><span data-stu-id="62055-234">WS-ReliableMessaging WS-Policy Assertion</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="62055-235"> utilise l'assertion WS-Policy de la messagerie WS-ReliableMessaging `wsrm:RMAssertion` pour décrire des fonctions de points de terminaison.</span><span class="sxs-lookup"><span data-stu-id="62055-235"> uses WS-ReliableMessaging WS-Policy Assertion `wsrm:RMAssertion` to describe endpoints capabilities.</span></span> <span data-ttu-id="62055-236">Voici une liste des contraintes qui s'appliquent à [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] :</span><span class="sxs-lookup"><span data-stu-id="62055-236">The following is a list of constraints that apply to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:</span></span>  
  
-   <span data-ttu-id="62055-237">B3001 : [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] attache l'assertion WS-Policy `wsrmn:RMAssertion` aux éléments `wsdl:binding`.</span><span class="sxs-lookup"><span data-stu-id="62055-237">B3001: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] attaches `wsrmn:RMAssertion` WS-Policy Assertion to `wsdl:binding` elements.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="62055-238"> prend en charge des pièces jointes aux éléments `wsdl:binding` et `wsdl:port`.</span><span class="sxs-lookup"><span data-stu-id="62055-238"> supports both attachments to `wsdl:binding` and `wsdl:port` elements.</span></span>  
  
-   <span data-ttu-id="62055-239">B3002 : [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ne génère jamais la balise `wsp:Optional`.</span><span class="sxs-lookup"><span data-stu-id="62055-239">B3002: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] never generates the `wsp:Optional` tag.</span></span>  
  
-   <span data-ttu-id="62055-240">B3003 : lors de l'accès à l'assertion WS-Policy `wsrmp:RMAssertion`, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ignore la balise `wsp:Optional` et traite la stratégie WS-RM comme obligatoire.</span><span class="sxs-lookup"><span data-stu-id="62055-240">B3003: When accessing the `wsrmp:RMAssertion` WS-Policy Assertion, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ignores the `wsp:Optional` tag and treats the WS-RM policy as mandatory.</span></span>  
  
-   <span data-ttu-id="62055-241">R3004 : étant donné que [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ne compose pas avec les sessions SSL/TLS, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] n'accepte pas la stratégie qui spécifie `wsrmp:SequenceTransportSecurity`.</span><span class="sxs-lookup"><span data-stu-id="62055-241">R3004: Because [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] does not compose with SSL/TLS sessions, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] does not accept policy that specifies `wsrmp:SequenceTransportSecurity`.</span></span>  
  
-   <span data-ttu-id="62055-242">B3005 : [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] génère toujours l'élément `wsrmp:DeliveryAssurance`.</span><span class="sxs-lookup"><span data-stu-id="62055-242">B3005: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] always generates the `wsrmp:DeliveryAssurance` element.</span></span>  
  
-   <span data-ttu-id="62055-243">B3006 : [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] spécifie toujours l'assurance de remise `wsrmp:ExactlyOnce`.</span><span class="sxs-lookup"><span data-stu-id="62055-243">B3006: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] always specifies the `wsrmp:ExactlyOnce` delivery assurance.</span></span>  
  
-   <span data-ttu-id="62055-244">B3007 : [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] génère et lit les propriétés suivantes de l’assertion WS-ReliableMessaging et assure leur contrôle sur le [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] `ReliableSessionBindingElement`:</span><span class="sxs-lookup"><span data-stu-id="62055-244">B3007: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generates and reads the following properties of the WS-ReliableMessaging assertion and provides control over them on the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]`ReliableSessionBindingElement`:</span></span>  
  
    -   `netrmp:InactivityTimeout`  
  
    -   `netrmp:AcknowledgementInterval`  
  
     <span data-ttu-id="62055-245">Exemple de `RMAssertion`.</span><span class="sxs-lookup"><span data-stu-id="62055-245">An example of a `RMAssertion`.</span></span>  
  
    ```xml  
    <wsrmp:RMAssertion>  
      <wsp:Policy>  
        <wsrmp:SequenceSTR/>  
        <wsrmp:DeliveryAssurance>  
          <wsp:Policy>  
            <wsrmp:ExactlyOnce/>  
            <wsrmp:InOrder/>  
          </wsp:Policy>  
        </wsrmp:DeliveryAssurance>  
      </wsp:Policy>  
      <netrmp:InactivityTimeout Milliseconds="600000"/>  
      <netrmp:AcknowledgementInterval Milliseconds="200"/>  
    </wsrmp:RMAssertion>  
    ```  
  
## <a name="flow-control-ws-reliablemessaging-extension"></a><span data-ttu-id="62055-246">Extension de messagerie WS-Reliable pour le contrôle de flux</span><span class="sxs-lookup"><span data-stu-id="62055-246">Flow Control WS-ReliableMessaging Extension</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="62055-247"> utilise l'extensibilité WS-ReliableMessaging pour fournir davantage de contrôle plus pointu facultatif sur le flux de messages de séquence.</span><span class="sxs-lookup"><span data-stu-id="62055-247"> uses WS-ReliableMessaging extensibility to provide optional additional tighter control over sequence message flow.</span></span>  
  
 <span data-ttu-id="62055-248">Contrôle de flux est activé en définissant le `ReliableSessionBindingElement`de `FlowControlEnabled``boolean` propriété `true`.</span><span class="sxs-lookup"><span data-stu-id="62055-248">Flow control is enabled by setting the `ReliableSessionBindingElement`’s `FlowControlEnabled``boolean` property to `true`.</span></span> <span data-ttu-id="62055-249">Voici une liste des contraintes qui s'appliquent à [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] :</span><span class="sxs-lookup"><span data-stu-id="62055-249">The following is a list of constraints that apply to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:</span></span>  
  
-   <span data-ttu-id="62055-250">B4001 : lorsque le contrôle de flux de messagerie fiable est activé, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] génère un élément `netrm:BufferRemaining` dans l'élément d'extensibilité de l'en-tête `SequenceAcknowledgement`, comme indiqué dans l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="62055-250">B4001: When Reliable Messaging Flow Control is enabled, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generates a `netrm:BufferRemaining` element in the element extensibility of the `SequenceAcknowledgement` header, as shown in the following example.</span></span>  
  
    ```xml  
    <wsrm:SequenceAcknowledgement>  
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
      <wsrm:AcknowledgementRange Upper="1" Lower="1"/>             
      <netrm:BufferRemaining>8</netrm:BufferRemaining>  
    </wsrm:SequenceAcknowledgement>  
    ```  
  
-   <span data-ttu-id="62055-251">B4002 : même lorsque le contrôle de flux de messagerie fiable est activé, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ne requiert pas d'élément `netrm:BufferRemaining` dans l'en-tête `SequenceAcknowledgement`.</span><span class="sxs-lookup"><span data-stu-id="62055-251">B4002: Even when Reliable Messaging Flow Control is enabled, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] does not require a `netrm:BufferRemaining` element in the `SequenceAcknowledgement` header.</span></span>  
  
-   <span data-ttu-id="62055-252">B4003 : la destination de messagerie fiable [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] utilise `netrm:BufferRemaining` pour indiquer combien de nouveaux messages elle peut mettre en mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="62055-252">B4003: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Reliable Messaging Destination uses `netrm:BufferRemaining` to indicate how many new messages it can buffer.</span></span>  
  
-   <span data-ttu-id="62055-253">B4004:when fiable de flux de contrôle de messagerie est activé, le [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Source de messagerie fiable utilise la valeur de `netrm:BufferRemaining` pour limiter la transmission des messages.</span><span class="sxs-lookup"><span data-stu-id="62055-253">B4004:When Reliable Messaging Flow Control is enabled, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Reliable Messaging Source uses the value of `netrm:BufferRemaining` to throttle message transmission.</span></span>  
  
-   <span data-ttu-id="62055-254">B4005 : [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] génère des valeurs entières `netrm:BufferRemaining` dans une plage inclusive de 0 à 4096 et lit des valeurs entières dans une plage inclusive de 0 à la valeur `xs:int` 214748364 de `maxInclusive`.</span><span class="sxs-lookup"><span data-stu-id="62055-254">B4005: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generates `netrm:BufferRemaining` integer values between 0 and 4096 inclusive, and reads integer values between 0 and `xs:int`’s `maxInclusive` value 214748364 inclusive.</span></span>  
  
## <a name="message-exchange-patterns"></a><span data-ttu-id="62055-255">Modèles d’échange de messages</span><span class="sxs-lookup"><span data-stu-id="62055-255">Message Exchange Patterns</span></span>  
 <span data-ttu-id="62055-256">Cette section décrit le comportement de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] lorsque WS-ReliableMessaging est utilisé pour différents modèles d'échange de messages.</span><span class="sxs-lookup"><span data-stu-id="62055-256">This section describes [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]'s behavior when WS-ReliableMessaging is used for different Message Exchange Patterns.</span></span> <span data-ttu-id="62055-257">Pour chaque modèle d’échange de messages, les deux scénarios de déploiements suivants sont considérés :</span><span class="sxs-lookup"><span data-stu-id="62055-257">For each Message Exchange Pattern the following two deployments scenarios are considered:</span></span>  
  
-   <span data-ttu-id="62055-258">Initiateur non adressable : l'initiateur est derrière un pare-feu ; le répondeur peut remettre uniquement des messages à celui-ci sur les réponses HTTP.</span><span class="sxs-lookup"><span data-stu-id="62055-258">Non-Addressable Initiator: Initiator is behind a firewall; Responder can deliver messages to the Initiator only on HTTP responses.</span></span>  
  
-   <span data-ttu-id="62055-259">Initiateur adressable : l'initiateur et le répondeur peuvent tous les deux recevoir des requêtes HTTP ; en d'autres termes, deux connexions HTTP réciproques peuvent être établies.</span><span class="sxs-lookup"><span data-stu-id="62055-259">Addressable Initiator: Initiator and Responder both can be sent HTTP requests; in other words, two converse HTTP connections can be established.</span></span>  
  
### <a name="one-way-non-addressable-initiator"></a><span data-ttu-id="62055-260">Initiateur unidirectionnel, non adressable</span><span class="sxs-lookup"><span data-stu-id="62055-260">One-way, Non-addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="62055-261">Liaison</span><span class="sxs-lookup"><span data-stu-id="62055-261">Binding</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="62055-262"> fournit un modèle unidirectionnel d'échange de messages qui utilise une séquence sur un canal HTTP.</span><span class="sxs-lookup"><span data-stu-id="62055-262"> provides a one-way message exchange pattern using one sequence over one HTTP channel.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="62055-263"> utilise des requêtes HTTP de transmettre tous les messages de l'initiateur au répondeur et les réponses HTTP pour transmettre tous les messages de répondeur à l'initiateur.</span><span class="sxs-lookup"><span data-stu-id="62055-263"> uses HTTP requests to transmit all messages from the Initiator to the Responder and HTTP responses to transmit all messages from the Responder to the Initiator.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="62055-264">Échange CreateSequence</span><span class="sxs-lookup"><span data-stu-id="62055-264">CreateSequence Exchange</span></span>  
 <span data-ttu-id="62055-265">L'initiateur [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] transmet un message `CreateSequence` sans élément `Offer` sur une requête HTTP et attend le message `CreateSequenceResponse` sur la réponse HTTP.</span><span class="sxs-lookup"><span data-stu-id="62055-265">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator transmits a `CreateSequence` message with no `Offer` element on an HTTP request and expects the `CreateSequenceResponse` message on the HTTP response.</span></span> <span data-ttu-id="62055-266">Le répondeur [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] crée une séquence et transmet le message `CreateSequenceResponse` sans élément `Accept` sur la réponse HTTP.</span><span class="sxs-lookup"><span data-stu-id="62055-266">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder creates a sequence and transmits the `CreateSequenceResponse` message with no `Accept` element on the HTTP response.</span></span>  
  
#### <a name="sequenceacknowledgement"></a><span data-ttu-id="62055-267">SequenceAcknowledgement</span><span class="sxs-lookup"><span data-stu-id="62055-267">SequenceAcknowledgement</span></span>  
 <span data-ttu-id="62055-268">L'initiateur [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] traite les accusés de réception sur la réponse de tous les messages sauf le message `CreateSequence` et les messages d'erreur.</span><span class="sxs-lookup"><span data-stu-id="62055-268">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator processes acknowledgements on the reply of all messages except the `CreateSequence` message and fault messages.</span></span> <span data-ttu-id="62055-269">Le répondeur [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] transmet toujours un accusé de réception autonome sur la réponse HTTP à tous les messages de séquence et `AckRequested`.</span><span class="sxs-lookup"><span data-stu-id="62055-269">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder always transmits a stand-alone acknowledgement on the HTTP response to all sequence and `AckRequested` messages.</span></span>  
  
#### <a name="closesequence-exchange"></a><span data-ttu-id="62055-270">Échange CloseSequence</span><span class="sxs-lookup"><span data-stu-id="62055-270">CloseSequence Exchange</span></span>  
 <span data-ttu-id="62055-271">L'initiateur [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] transmet un message `CloseSequence` sur une requête HTTP et attend le message `CreateSequenceResponse` sur la réponse HTTP.</span><span class="sxs-lookup"><span data-stu-id="62055-271">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator transmits a `CloseSequence` message on an HTTP request and expects the `CreateSequenceResponse` message on the HTTP response.</span></span> <span data-ttu-id="62055-272">Le répondeur [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] transmet le message `CloseSequenceResponse` sur la réponse HTTP.</span><span class="sxs-lookup"><span data-stu-id="62055-272">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder transmits the `CloseSequenceResponse` message on the HTTP response.</span></span>  
  
#### <a name="terminatesequence-exchange"></a><span data-ttu-id="62055-273">Échange TerminateSequence</span><span class="sxs-lookup"><span data-stu-id="62055-273">TerminateSequence Exchange</span></span>  
 <span data-ttu-id="62055-274">L'initiateur [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] transmet un message `TerminateSequence` sur une requête HTTP et attend le message `TerminateSequenceResponse` sur la réponse HTTP.</span><span class="sxs-lookup"><span data-stu-id="62055-274">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator transmits a `TerminateSequence` message on an HTTP request and expects the `TerminateSequenceResponse` message on the HTTP response.</span></span> <span data-ttu-id="62055-275">Le répondeur [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] transmet le message `TerminateSequenceResponse` sur la réponse HTTP.</span><span class="sxs-lookup"><span data-stu-id="62055-275">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder transmits the `TerminateSequenceResponse` message on the HTTP response.</span></span>  
  
### <a name="one-way-addressable-initiator"></a><span data-ttu-id="62055-276">Initiateur unidirectionnel, adressable</span><span class="sxs-lookup"><span data-stu-id="62055-276">One Way, Addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="62055-277">Liaison</span><span class="sxs-lookup"><span data-stu-id="62055-277">Binding</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="62055-278"> fournit un modèle unidirectionnel d'échange de messages qui utilise une séquences sur un canal HTTP entrant et un canal sortant.</span><span class="sxs-lookup"><span data-stu-id="62055-278"> provides a one-way message exchange pattern using one sequence over one inbound and one outbound HTTP channel.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="62055-279"> utilise les requêtes HTTP pour transmettre les messages.</span><span class="sxs-lookup"><span data-stu-id="62055-279"> uses the HTTP requests to transmit all messages.</span></span> <span data-ttu-id="62055-280">Toutes les réponses HTTP ont un corps vide et le code d'état HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="62055-280">All HTTP responses have an empty body and HTTP 202 status code.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="62055-281">Échange CreateSequence</span><span class="sxs-lookup"><span data-stu-id="62055-281">CreateSequence Exchange</span></span>  
 <span data-ttu-id="62055-282">L'initiateur [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] transmet un message `CreateSequence` sans élément `Offer` sur une requête HTTP.</span><span class="sxs-lookup"><span data-stu-id="62055-282">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator transmits a `CreateSequence` message with no `Offer` element on an HTTP request.</span></span> <span data-ttu-id="62055-283">Le répondeur [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] crée une séquence et transmet le message `CreateSequenceResponse` sans élément `Accept` sur une requête HTTP.</span><span class="sxs-lookup"><span data-stu-id="62055-283">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder creates a sequence and transmits the `CreateSequenceResponse` message with no `Accept` element on an HTTP request.</span></span>  
  
### <a name="duplex-addressable-initiator"></a><span data-ttu-id="62055-284">Initiateur duplex, adressable</span><span class="sxs-lookup"><span data-stu-id="62055-284">Duplex, Addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="62055-285">Liaison</span><span class="sxs-lookup"><span data-stu-id="62055-285">Binding</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="62055-286"> fournit un modèle d'échange de messages asynchrone complet, bidirectionnel qui utilise deux séquences sur un canal HTTP entrant et sortant.</span><span class="sxs-lookup"><span data-stu-id="62055-286"> provides a fully-asynchronous, two-way message exchange pattern using two sequences over one inbound and one outbound HTTP channel.</span></span> <span data-ttu-id="62055-287">Ce modèle d'échange de messages peut être combiné avec le modèle d'échange de messages initiateur `Request/Reply`, `Addressable` d'une manière limitée.</span><span class="sxs-lookup"><span data-stu-id="62055-287">This message exchange pattern can be mixed with the `Request/Reply`, `Addressable` Initiator message exchange pattern in a limited way.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="62055-288"> utilise les requêtes HTTP pour transmettre les messages.</span><span class="sxs-lookup"><span data-stu-id="62055-288"> uses HTTP requests to transmit all messages.</span></span> <span data-ttu-id="62055-289">Toutes les réponses HTTP ont un corps vide et le code d'état HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="62055-289">All HTTP responses have an empty body and HTTP 202 status code.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="62055-290">Échange CreateSequence</span><span class="sxs-lookup"><span data-stu-id="62055-290">CreateSequence Exchange</span></span>  
 <span data-ttu-id="62055-291">L'initiateur [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] transmet un message `CreateSequence` avec un élément `Offer` sur une requête HTTP.</span><span class="sxs-lookup"><span data-stu-id="62055-291">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator transmits a `CreateSequence` message with an `Offer` element on an HTTP request.</span></span> <span data-ttu-id="62055-292">Le répondeur [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] vérifie que `CreateSequence` possède un élément `Offer`, puis crée une séquence et transmet le message `CreateSequenceResponse` avec un élément `Accept`.</span><span class="sxs-lookup"><span data-stu-id="62055-292">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder ensures that the `CreateSequence` has an `Offer` element, then creates a sequence and transmits the `CreateSequenceResponse` message with an `Accept` element.</span></span>  
  
#### <a name="sequence-lifetime"></a><span data-ttu-id="62055-293">Durée de vie de séquence</span><span class="sxs-lookup"><span data-stu-id="62055-293">Sequence Lifetime</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="62055-294"> traite les deux séquences comme une session duplex complète.</span><span class="sxs-lookup"><span data-stu-id="62055-294"> treats the two sequences as one fully-duplex session.</span></span>  
  
 <span data-ttu-id="62055-295">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] s'attend à ce que le point de terminaison distant trouve une erreur dans les deux séquences pour générer une erreur qui fait échouer une séquence.</span><span class="sxs-lookup"><span data-stu-id="62055-295">Upon generating a fault that faults one sequence, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] expects the remote endpoint to fault both sequences.</span></span> <span data-ttu-id="62055-296">À la lecture d'une erreur qui fait échouer une séquence, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] fait échouer les deux séquences.</span><span class="sxs-lookup"><span data-stu-id="62055-296">Upon reading a fault that faults one sequence, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] faults both sequences.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="62055-297"> peut fermer sa séquence sortante et continuer à traiter des messages sur sa séquence entrante.</span><span class="sxs-lookup"><span data-stu-id="62055-297"> can close its outbound sequence and continue to process messages on its inbound sequence.</span></span> <span data-ttu-id="62055-298">Inversement, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] peut traiter la fermeture de la séquence entrante et continuer à envoyer des messages sur sa séquence sortante.</span><span class="sxs-lookup"><span data-stu-id="62055-298">Conversely, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] can process the close of the inbound sequence and continue to send messages on its outbound sequence.</span></span>  
  
### <a name="request-reply-and-one-way-non-addressable-initiator"></a><span data-ttu-id="62055-299">Initiateur demande-réponse, unidirectionnel et non adressable</span><span class="sxs-lookup"><span data-stu-id="62055-299">Request-Reply and One-Way, Non-Addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="62055-300">Liaison</span><span class="sxs-lookup"><span data-stu-id="62055-300">Binding</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="62055-301"> fournit un modèle unidirectionnel d'échange de messages et de réponse-demande qui utilise deux séquences sur un canal HTTP.</span><span class="sxs-lookup"><span data-stu-id="62055-301"> provides a one-way and request-reply message exchange pattern using two sequences over one HTTP channel.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="62055-302"> utilise des requêtes HTTP de transmettre tous les messages de l'initiateur au répondeur et les réponses HTTP pour transmettre tous les messages de répondeur à l'initiateur.</span><span class="sxs-lookup"><span data-stu-id="62055-302"> uses HTTP requests to transmit all messages from the Initiator to the Responder and HTTP responses to transmit all messages from the Responder to the Initiator.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="62055-303">Échange CreateSequence</span><span class="sxs-lookup"><span data-stu-id="62055-303">CreateSequence Exchange</span></span>  
 <span data-ttu-id="62055-304">L'initiateur [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] transmet un message `CreateSequence` avec un élément `Offer` sur une requête HTTP et attend le message `CreateSequenceResponse` sur la réponse HTTP.</span><span class="sxs-lookup"><span data-stu-id="62055-304">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator transmits a `CreateSequence` message with an `Offer` element on an HTTP request and expects the `CreateSequenceResponse` message on the HTTP response.</span></span> <span data-ttu-id="62055-305">Le répondeur [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] crée une séquence et transmet le message `CreateSequenceResponse` avec un élément `Accept` sur la réponse HTTP.</span><span class="sxs-lookup"><span data-stu-id="62055-305">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder creates a sequence and transmits the `CreateSequenceResponse` message with an `Accept` element on the HTTP response.</span></span>  
  
#### <a name="one-way-message"></a><span data-ttu-id="62055-306">Message unidirectionnel</span><span class="sxs-lookup"><span data-stu-id="62055-306">One-way Message</span></span>  
 <span data-ttu-id="62055-307">Pour réussir un échange de messages unidirectionnel, l'initiateur [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] transmet un message de séquence de demande sur la requête HTTP et reçoit un message `SequenceAcknowledgement` autonome sur la réponse HTTP.</span><span class="sxs-lookup"><span data-stu-id="62055-307">To complete a one-way message exchange successfully, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator transmits a request sequence message on the HTTP request and receives a standalone `SequenceAcknowledgement` message on the HTTP response.</span></span> <span data-ttu-id="62055-308">`SequenceAcknowledgement` doit accepter le message transmis.</span><span class="sxs-lookup"><span data-stu-id="62055-308">The `SequenceAcknowledgement` must acknowledge the message transmitted.</span></span>  
  
 <span data-ttu-id="62055-309">Le répondeur [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] peut répondre à la demande avec un accusé de réception, une erreur ou une réponse avec un corps vide et le code d'état HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="62055-309">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder may reply to the request with an acknowledgement, a fault, or a response with an empty body and HTTP 202 status code.</span></span>  
  
#### <a name="two-way-messages"></a><span data-ttu-id="62055-310">Messages bidirectionnels</span><span class="sxs-lookup"><span data-stu-id="62055-310">Two Way Messages</span></span>  
 <span data-ttu-id="62055-311">Pour compléter un protocole d'échange de messages bidirectionnel, l'initiateur [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] transmet un message de séquence de demande sur la requête HTTP et reçoit un message de séquence de réponse sur la réponse HTTP.</span><span class="sxs-lookup"><span data-stu-id="62055-311">To complete a two way message exchange protocol successfully, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator transmits a request sequence message on the HTTP request and receives a reply sequence message on the HTTP response.</span></span> <span data-ttu-id="62055-312">La réponse doit contenir un `SequenceAcknowledgement` qui accuse réception du message de séquence de demande transmis.</span><span class="sxs-lookup"><span data-stu-id="62055-312">The response must carry a `SequenceAcknowledgement` acknowledging the request sequence message transmitted.</span></span>  
  
 <span data-ttu-id="62055-313">Le répondeur [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] peut répondre à la demande avec une réponse d'application, une erreur ou une réponse avec un corps vide et le code d'état HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="62055-313">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder may reply to the request with an application reply, a fault or a response with an empty body and HTTP 202 status code.</span></span>  
  
 <span data-ttu-id="62055-314">En raison de la présence de messages unidirectionnels et du délai d'attente des réponses d'application, le numéro de séquence du message de séquence de demande et le numéro de séquence du message de réponse n'ont aucune corrélation.</span><span class="sxs-lookup"><span data-stu-id="62055-314">Because of the presence of one-way messages and the timing of application replies, the request sequence message’s sequence number and the response message’s sequence number have no correlation.</span></span>  
  
#### <a name="retrying-replies"></a><span data-ttu-id="62055-315">Nouvelles tentatives de réponses</span><span class="sxs-lookup"><span data-stu-id="62055-315">Retrying Replies</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="62055-316"> repose sur la corrélation demande-réponse HTTP pour la corrélation de protocole d'échange de messages bidirectionnel.</span><span class="sxs-lookup"><span data-stu-id="62055-316"> relies on HTTP request-reply correlation for two-way message exchange protocol correlation.</span></span> <span data-ttu-id="62055-317">De ce fait, l'initiateur [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ne cesse pas de réessayer un message de séquence de demande lorsque le message de séquence de demande est accepté mais plutôt lorsque la réponse HTTP contient un `SequenceAcknowledgement`, une réponse d'application ou une erreur.</span><span class="sxs-lookup"><span data-stu-id="62055-317">Because of this, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator does not stop retrying a request sequence message when the request sequence message is acknowledged but rather when the HTTP response carries a `SequenceAcknowledgement`, application reply, or fault.</span></span> <span data-ttu-id="62055-318">Le répondeur [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] réessaie des réponses sur la réponse HTTP de la demande à laquelle la réponse est corrélée.</span><span class="sxs-lookup"><span data-stu-id="62055-318">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder retries replies on the HTTP response of the request to which the reply is correlated.</span></span>  
  
#### <a name="closesequence-exchange"></a><span data-ttu-id="62055-319">Échange CloseSequence</span><span class="sxs-lookup"><span data-stu-id="62055-319">CloseSequence Exchange</span></span>  
 <span data-ttu-id="62055-320">Après réception de tous les accusés de réception et des messages de séquence de réponse pour touts les messages de séquence de demande unidirectionnels, l'initiateur [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] transmet un message `CloseSequence` pour la séquence de demande sur une requête HTTP et attend `CloseSequenceResponse` sur la réponse HTTP.</span><span class="sxs-lookup"><span data-stu-id="62055-320">After receiving all reply sequence messages and acknowledgements for all one way request sequence messages, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator transmits a `CloseSequence` message for the request sequence on an HTTP request and expects the `CloseSequenceResponse` on the HTTP response.</span></span>  
  
 <span data-ttu-id="62055-321">La fermeture de la séquence de demande ferme implicitement la séquence de réponse.</span><span class="sxs-lookup"><span data-stu-id="62055-321">Closing the request sequence implicitly closes the reply sequence.</span></span> <span data-ttu-id="62055-322">Cela signifie que l'initiateur [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] inclut le `SequenceAcknowledgement` final de la séquence de réponse sur le message `CloseSequence` et la séquence de réponse n'a pas d'échange `CloseSequence`.</span><span class="sxs-lookup"><span data-stu-id="62055-322">This means the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator includes the reply sequence’s Final `SequenceAcknowledgement` on the `CloseSequence` message and the reply sequence does not have a `CloseSequence` exchange.</span></span>  
  
 <span data-ttu-id="62055-323">Le répondeur [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] s'assure que toutes les réponses sont acceptées et transmet le message `CloseSequenceResponse` sur la réponse HTTP.</span><span class="sxs-lookup"><span data-stu-id="62055-323">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder ensures all replies are acknowledged and transmits the `CloseSequenceResponse` message on the HTTP response.</span></span>  
  
#### <a name="terminatesequence-exchange"></a><span data-ttu-id="62055-324">Échange TerminateSequence</span><span class="sxs-lookup"><span data-stu-id="62055-324">TerminateSequence Exchange</span></span>  
 <span data-ttu-id="62055-325">Après réception du message `CloseSequenceResponse`, l'initiateur [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] transmet un message `TerminateSequence` pour la séquence de demande sur une requête HTTP et attend le `TerminateSequenceResponse` sur la réponse HTTP.</span><span class="sxs-lookup"><span data-stu-id="62055-325">After receiving the `CloseSequenceResponse` message, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator transmits a `TerminateSequence` message for the request sequence on an HTTP request and expects the `TerminateSequenceResponse` on the HTTP response.</span></span>  
  
 <span data-ttu-id="62055-326">Comme l'échange `CloseSequence`, terminer la séquence de demande termine implicitement la séquence de réponse.</span><span class="sxs-lookup"><span data-stu-id="62055-326">Like the `CloseSequence` exchange, terminating the request sequence implicitly terminates the reply sequence.</span></span> <span data-ttu-id="62055-327">Cela signifie que l'initiateur [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] inclut le `SequenceAcknowledgement` final de la séquence de réponse sur le message `TerminateSequence` et la séquence de réponse n'a pas d'échange `TerminateSequence`.</span><span class="sxs-lookup"><span data-stu-id="62055-327">This means the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator includes the reply sequence’s final `SequenceAcknowledgement` on the `TerminateSequence` message and the reply sequence does not have a `TerminateSequence` exchange.</span></span>  
  
 <span data-ttu-id="62055-328">Le répondeur [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] transmet le message `TerminateSequenceResponse` sur la réponse HTTP.</span><span class="sxs-lookup"><span data-stu-id="62055-328">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder transmits the `TerminateSequenceResponse` message on the HTTP response.</span></span>  
  
### <a name="requestreply-addressable-initiator"></a><span data-ttu-id="62055-329">Initiateur demande/réponse, adressable</span><span class="sxs-lookup"><span data-stu-id="62055-329">Request/Reply, Addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="62055-330">Liaison</span><span class="sxs-lookup"><span data-stu-id="62055-330">Binding</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="62055-331"> fournit un modèle d'échange de messages de réponse-demande qui utilise deux séquences sur un canal HTTP entrant et un canal sortant.</span><span class="sxs-lookup"><span data-stu-id="62055-331"> provides a request-reply message exchange pattern using two sequences over one inbound and one outbound HTTP channel.</span></span> <span data-ttu-id="62055-332">Ce modèle d'échange de messages peut être combiné avec le modèle d'échange de messages initiateur `Duplex, Addressable` d'une manière limitée.</span><span class="sxs-lookup"><span data-stu-id="62055-332">This message exchange pattern can be mixed with the `Duplex, Addressable` Initiator message exchange pattern in a limited way.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="62055-333"> utilise les requêtes HTTP pour transmettre les messages.</span><span class="sxs-lookup"><span data-stu-id="62055-333"> uses the HTTP requests to transmit all messages.</span></span> <span data-ttu-id="62055-334">Toutes les réponses HTTP ont un corps vide et le code d'état HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="62055-334">All HTTP responses have an empty body and HTTP 202 status code.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="62055-335">Échange CreateSequence</span><span class="sxs-lookup"><span data-stu-id="62055-335">CreateSequence Exchange</span></span>  
 <span data-ttu-id="62055-336">L'initiateur [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] transmet un message `CreateSequence` avec un élément `Offer` sur une requête HTTP.</span><span class="sxs-lookup"><span data-stu-id="62055-336">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator transmits a `CreateSequence` message with an `Offer` element on an HTTP request.</span></span> <span data-ttu-id="62055-337">Le répondeur [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] s'assure que `CreateSequence` possède un élément `Offer`, puis crée une séquence et transmet le message `CreateSequenceResponse` avec un élément `Accept`.</span><span class="sxs-lookup"><span data-stu-id="62055-337">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder ensures that the `CreateSequence` has an `Offer` element then creates a sequence and transmits the `CreateSequenceResponse` message with an `Accept` element.</span></span>  
  
#### <a name="requestreply-correlation"></a><span data-ttu-id="62055-338">Corrélation demande/réponse</span><span class="sxs-lookup"><span data-stu-id="62055-338">Request/Reply Correlation</span></span>  
 <span data-ttu-id="62055-339">Les points suivants s'appliquent à toutes les demandes et réponses corrélées :</span><span class="sxs-lookup"><span data-stu-id="62055-339">The following applies to all correlated requests and replies:</span></span>  
  
-   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="62055-340"> s'assure que tous les messages de demande d'application contiennent une référence de point de terminaison `ReplyTo` et un `MessageId`.</span><span class="sxs-lookup"><span data-stu-id="62055-340"> ensures all application request messages bear a `ReplyTo` endpoint reference and a `MessageId`.</span></span>  
  
-   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="62055-341"> applique la référence de point de terminaison locale comme le `ReplyTo` de chaque message de demande d'application.</span><span class="sxs-lookup"><span data-stu-id="62055-341"> applies the local endpoint reference as each application request message’s `ReplyTo`.</span></span> <span data-ttu-id="62055-342">La référence de point de terminaison locale est `CreateSequence` du message `ReplyTo` pour l'initiateur et `CreateSequence` du message `To` pour le répondeur.</span><span class="sxs-lookup"><span data-stu-id="62055-342">The local endpoint reference is the `CreateSequence` message’s `ReplyTo` for the Initiator and the `CreateSequence` message’s `To` for the Responder.</span></span>  
  
-   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="62055-343"> s'assure que les messages de demande entrants contiennent un `MessageId` et un `ReplyTo`.</span><span class="sxs-lookup"><span data-stu-id="62055-343"> ensures that incoming request messages bear a `MessageId` and a `ReplyTo`.</span></span>  
  
-   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="62055-344"> s'assure que l'URI de tous les messages de demande d'application de la référence de point de terminaison `ReplyTo` correspond à la référence de point de terminaison locale définie précédemment.</span><span class="sxs-lookup"><span data-stu-id="62055-344"> ensures the `ReplyTo` endpoint reference’s URI of all application request messages match the local endpoint reference as defined earlier.</span></span>  
  
-   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="62055-345"> s'assure que toutes les réponses contiennent les en-têtes `RelatesTo` et `To` corrects en conformité avec les règles de corrélation demande/réponse `wsa`.</span><span class="sxs-lookup"><span data-stu-id="62055-345"> ensures that all replies bear the correct `RelatesTo` and `To` headers following `wsa` request/reply correlation rules.</span></span>
