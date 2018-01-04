---
title: Protocoles de messagerie
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5b20bca7-87b3-4c8f-811b-f215b5987104
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 600a1bd57015c6a64a51bf99f3ded35a375e62fe
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="messaging-protocols"></a><span data-ttu-id="56dfb-102">Protocoles de messagerie</span><span class="sxs-lookup"><span data-stu-id="56dfb-102">Messaging Protocols</span></span>
<span data-ttu-id="56dfb-103">La pile de canaux [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] utilise l'encodage et les canaux de transport pour transformer la représentation du message interne en son format de transmission et l'envoyer en utilisant un transport particulier.</span><span class="sxs-lookup"><span data-stu-id="56dfb-103">The [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] channel stack employs encoding and transport channels to transform internal message representation into its wire format and send it by using a particular transport.</span></span> <span data-ttu-id="56dfb-104">Le transport le plus couramment utilisé pour l'interopérabilité des services Web est le HTTP, et les encodages les plus couramment utilisés par les services Web sont SOAP 1.1 basé sur XML, SOAP 1.2 et MTOM (Message Transmission Optimization Mechanism).</span><span class="sxs-lookup"><span data-stu-id="56dfb-104">The most common transport used for Web services interoperability is HTTP, and the most common encodings used by Web services are XML-based SOAP 1.1, SOAP 1.2, and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="56dfb-105">Cette rubrique décrit les détails de l'implémentation [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] pour les protocoles suivants utilisés par <xref:System.ServiceModel.Channels.HttpTransportBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="56dfb-105">This topic covers [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] implementation details for the following protocols employed by <xref:System.ServiceModel.Channels.HttpTransportBindingElement>.</span></span>  
  
|<span data-ttu-id="56dfb-106">Spécification/document</span><span class="sxs-lookup"><span data-stu-id="56dfb-106">Specification/document</span></span>|<span data-ttu-id="56dfb-107">Link</span><span class="sxs-lookup"><span data-stu-id="56dfb-107">Link</span></span>|  
|-----------------------------|----------|  
|<span data-ttu-id="56dfb-108">HTTP 1.1</span><span class="sxs-lookup"><span data-stu-id="56dfb-108">HTTP 1.1</span></span>|<span data-ttu-id="56dfb-109">http://www.ietf.org/rfc/rfc2616.txt</span><span class="sxs-lookup"><span data-stu-id="56dfb-109">http://www.ietf.org/rfc/rfc2616.txt</span></span>|  
|<span data-ttu-id="56dfb-110">Liaison HTTP SOAP 1.1</span><span class="sxs-lookup"><span data-stu-id="56dfb-110">SOAP 1.1 HTTP Binding</span></span>|<span data-ttu-id="56dfb-111">http://www.w3.org/TR/2000/NOTE-SOAP-20000508/, Section 7</span><span class="sxs-lookup"><span data-stu-id="56dfb-111">http://www.w3.org/TR/2000/NOTE-SOAP-20000508/, Section 7</span></span>|  
|<span data-ttu-id="56dfb-112">Liaison HTTP SOAP 1,2</span><span class="sxs-lookup"><span data-stu-id="56dfb-112">SOAP 1.2 HTTP Binding</span></span>|<span data-ttu-id="56dfb-113">http://www.w3.org/TR/soap12-part2/, Section 7</span><span class="sxs-lookup"><span data-stu-id="56dfb-113">http://www.w3.org/TR/soap12-part2/, Section 7</span></span>|  
  
 <span data-ttu-id="56dfb-114">Cette rubrique décrit les détails de l'implémentation [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] pour les protocoles suivants utilisés par <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> et <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="56dfb-114">This topic covers [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] implementation details for the following protocols  that <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> and <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> employ.</span></span>  
  
|<span data-ttu-id="56dfb-115">Spécification/Document</span><span class="sxs-lookup"><span data-stu-id="56dfb-115">Specification/Document</span></span>|<span data-ttu-id="56dfb-116">Link</span><span class="sxs-lookup"><span data-stu-id="56dfb-116">Link</span></span>|  
|-----------------------------|----------|  
|<span data-ttu-id="56dfb-117">XML</span><span class="sxs-lookup"><span data-stu-id="56dfb-117">XML</span></span>|<span data-ttu-id="56dfb-118">http://www.w3.org/TR/REC-xml</span><span class="sxs-lookup"><span data-stu-id="56dfb-118">http://www.w3.org/TR/REC-xml</span></span>|  
|<span data-ttu-id="56dfb-119">SOAP 1,1</span><span class="sxs-lookup"><span data-stu-id="56dfb-119">SOAP 1.1</span></span>|<span data-ttu-id="56dfb-120">http://www.w3.org/TR/2000/NOTE-SOAP-20000508/</span><span class="sxs-lookup"><span data-stu-id="56dfb-120">http://www.w3.org/TR/2000/NOTE-SOAP-20000508/</span></span>|  
|<span data-ttu-id="56dfb-121">SOAP 1.2 Core</span><span class="sxs-lookup"><span data-stu-id="56dfb-121">SOAP 1.2 Core</span></span>|<span data-ttu-id="56dfb-122">http://www.w3.org/TR/soap12-part1/</span><span class="sxs-lookup"><span data-stu-id="56dfb-122">http://www.w3.org/TR/soap12-part1/</span></span>|  
|<span data-ttu-id="56dfb-123">WS-Addressing 2004/08</span><span class="sxs-lookup"><span data-stu-id="56dfb-123">WS-Addressing 2004/08</span></span>|<span data-ttu-id="56dfb-124">http://www.w3.org/Submission/2004/SUBM-ws-addressing-20040810/</span><span class="sxs-lookup"><span data-stu-id="56dfb-124">http://www.w3.org/Submission/2004/SUBM-ws-addressing-20040810/</span></span>|  
|<span data-ttu-id="56dfb-125">W3C Web Services Addressing 1.0 – Éléments principaux</span><span class="sxs-lookup"><span data-stu-id="56dfb-125">W3C Web Services Addressing 1.0 - Core</span></span>|<span data-ttu-id="56dfb-126">http://www.w3.org/TR/2006/REC-ws-addr-core-20060509</span><span class="sxs-lookup"><span data-stu-id="56dfb-126">http://www.w3.org/TR/2006/REC-ws-addr-core-20060509</span></span>|  
|<span data-ttu-id="56dfb-127">W3C Web Services Addressing 1.0 – Liaison SOAP</span><span class="sxs-lookup"><span data-stu-id="56dfb-127">W3C Web Services Addressing 1.0 - SOAP Binding</span></span>|<span data-ttu-id="56dfb-128">http://www.w3.org/TR/2006/REC-ws-addr-soap-20060509</span><span class="sxs-lookup"><span data-stu-id="56dfb-128">http://www.w3.org/TR/2006/REC-ws-addr-soap-20060509</span></span>|  
|<span data-ttu-id="56dfb-129">W3C Web Services Addressing 1.0 – Liaison WSDL</span><span class="sxs-lookup"><span data-stu-id="56dfb-129">W3C Web Services Addressing 1.0 - WSDL Binding</span></span>|<span data-ttu-id="56dfb-130">http://www.w3.org/TR/2006/CR-ws-addr-wsdl-20060529/</span><span class="sxs-lookup"><span data-stu-id="56dfb-130">http://www.w3.org/TR/2006/CR-ws-addr-wsdl-20060529/</span></span>|  
<span data-ttu-id="56dfb-131">W3C Web Services Addressing 1.0 - Métadonnées</span><span class="sxs-lookup"><span data-stu-id="56dfb-131">W3C Web Services Addressing 1.0 - Metadata</span></span>|<span data-ttu-id="56dfb-132">http://www.w3.org/TR/ws-addr-metadata/</span><span class="sxs-lookup"><span data-stu-id="56dfb-132">http://www.w3.org/TR/ws-addr-metadata/</span></span>|  
|<span data-ttu-id="56dfb-133">Liaison WSDL SOAP 1.1</span><span class="sxs-lookup"><span data-stu-id="56dfb-133">WSDL SOAP1.1 Binding</span></span>|<span data-ttu-id="56dfb-134">http://www.w3.org/TR/wsdl/</span><span class="sxs-lookup"><span data-stu-id="56dfb-134">http://www.w3.org/TR/wsdl/</span></span>|  
|<span data-ttu-id="56dfb-135">Liaison WSDL SOAP 1.2</span><span class="sxs-lookup"><span data-stu-id="56dfb-135">WSDL SOAP1.2 Binding</span></span>|<span data-ttu-id="56dfb-136">http://www.w3.org/Submission/wsdl11soap12/</span><span class="sxs-lookup"><span data-stu-id="56dfb-136">http://www.w3.org/Submission/wsdl11soap12/</span></span>|  
  
 <span data-ttu-id="56dfb-137">Cette rubrique décrit les détails de l'implémentation [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] pour les protocoles suivants utilisés par <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="56dfb-137">This topic covers [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] implementation details for the following protocols that <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> employs.</span></span>  
  
|<span data-ttu-id="56dfb-138">Spécification/document</span><span class="sxs-lookup"><span data-stu-id="56dfb-138">Specification/document</span></span>|<span data-ttu-id="56dfb-139">Link</span><span class="sxs-lookup"><span data-stu-id="56dfb-139">Link</span></span>|  
|-----------------------------|----------|  
|<span data-ttu-id="56dfb-140">XOP</span><span class="sxs-lookup"><span data-stu-id="56dfb-140">XOP</span></span>|<span data-ttu-id="56dfb-141">http://www.w3.org/TR/xop10/</span><span class="sxs-lookup"><span data-stu-id="56dfb-141">http://www.w3.org/TR/xop10/</span></span>|  
|<span data-ttu-id="56dfb-142">Liaison MTOM + SOAP 1.2</span><span class="sxs-lookup"><span data-stu-id="56dfb-142">MTOM + SOAP 1.2 Binding</span></span>|<span data-ttu-id="56dfb-143">http://www.w3.org/TR/soap12-mtom/</span><span class="sxs-lookup"><span data-stu-id="56dfb-143">http://www.w3.org/TR/soap12-mtom/</span></span>|  
|<span data-ttu-id="56dfb-144">Liaison MTOM SOAP 1.1</span><span class="sxs-lookup"><span data-stu-id="56dfb-144">MTOM SOAP 1.1 Binding</span></span>|<span data-ttu-id="56dfb-145">http://www.w3.org/Submission/soap11mtom10/</span><span class="sxs-lookup"><span data-stu-id="56dfb-145">http://www.w3.org/Submission/soap11mtom10/</span></span>|  
|<span data-ttu-id="56dfb-146">Assertion de MTOM WS-Policy</span><span class="sxs-lookup"><span data-stu-id="56dfb-146">MTOM WS-Policy Assertion</span></span>|<span data-ttu-id="56dfb-147">http://www.w3.org/Submission/2006/SUBM-WS-MTOMPolicy-20061101/.</span><span class="sxs-lookup"><span data-stu-id="56dfb-147">http://www.w3.org/Submission/2006/SUBM-WS-MTOMPolicy-20061101/.</span></span>|  
  
 <span data-ttu-id="56dfb-148">Les espaces de noms XML suivants et les préfixes associés sont utilisés dans l'ensemble de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="56dfb-148">The following XML namespaces and associated prefixes are used throughout this topic.</span></span>  
  
|<span data-ttu-id="56dfb-149">Préfixe</span><span class="sxs-lookup"><span data-stu-id="56dfb-149">Prefix</span></span>|<span data-ttu-id="56dfb-150">URI (Uniform Resource Identifier) de l'espace de noms</span><span class="sxs-lookup"><span data-stu-id="56dfb-150">Namespace Uniform Resource Identifier (URI)</span></span>|  
|------------|---------------------------------------------------|  
|<span data-ttu-id="56dfb-151">s11</span><span class="sxs-lookup"><span data-stu-id="56dfb-151">s11</span></span>|<span data-ttu-id="56dfb-152">http://schemas.xmlsoap.org/soap/envelope</span><span class="sxs-lookup"><span data-stu-id="56dfb-152">http://schemas.xmlsoap.org/soap/envelope</span></span>|  
|<span data-ttu-id="56dfb-153">s12</span><span class="sxs-lookup"><span data-stu-id="56dfb-153">s12</span></span>|<span data-ttu-id="56dfb-154">http://www.w3.org/2003/05/soap-envelope</span><span class="sxs-lookup"><span data-stu-id="56dfb-154">http://www.w3.org/2003/05/soap-envelope</span></span>|  
|<span data-ttu-id="56dfb-155">wsa</span><span class="sxs-lookup"><span data-stu-id="56dfb-155">wsa</span></span>|<span data-ttu-id="56dfb-156">http://www.w3.org/2004/08/Addressing</span><span class="sxs-lookup"><span data-stu-id="56dfb-156">http://www.w3.org/2004/08/addressing</span></span>|  
|<span data-ttu-id="56dfb-157">wsam</span><span class="sxs-lookup"><span data-stu-id="56dfb-157">wsam</span></span>|<span data-ttu-id="56dfb-158">http://www.w3.org/2007/05/addressing/metadata</span><span class="sxs-lookup"><span data-stu-id="56dfb-158">http://www.w3.org/2007/05/addressing/metadata</span></span>|  
|<span data-ttu-id="56dfb-159">wsap</span><span class="sxs-lookup"><span data-stu-id="56dfb-159">wsap</span></span>|<span data-ttu-id="56dfb-160">http://schemas.xmlsoap.org/ws/2004/09/policy/addressing</span><span class="sxs-lookup"><span data-stu-id="56dfb-160">http://schemas.xmlsoap.org/ws/2004/09/policy/addressing</span></span>|  
|<span data-ttu-id="56dfb-161">wsa10</span><span class="sxs-lookup"><span data-stu-id="56dfb-161">wsa10</span></span>|<span data-ttu-id="56dfb-162">http://www.w3.org/2005/08/addressing (page pouvant être en anglais)</span><span class="sxs-lookup"><span data-stu-id="56dfb-162">http://www.w3.org/2005/08/addressing</span></span>|  
|<span data-ttu-id="56dfb-163">wsaw10</span><span class="sxs-lookup"><span data-stu-id="56dfb-163">wsaw10</span></span>|<span data-ttu-id="56dfb-164">http://www.w3.org/2006/05/addressing/wsdl</span><span class="sxs-lookup"><span data-stu-id="56dfb-164">http://www.w3.org/2006/05/addressing/wsdl</span></span>|  
|<span data-ttu-id="56dfb-165">xop</span><span class="sxs-lookup"><span data-stu-id="56dfb-165">xop</span></span>|<span data-ttu-id="56dfb-166">http://www.w3.org/2004/08/xop/include</span><span class="sxs-lookup"><span data-stu-id="56dfb-166">http://www.w3.org/2004/08/xop/include</span></span>|  
|<span data-ttu-id="56dfb-167">xmime</span><span class="sxs-lookup"><span data-stu-id="56dfb-167">xmime</span></span>|<span data-ttu-id="56dfb-168">http://www.w3.org/2004/06/xmlmime</span><span class="sxs-lookup"><span data-stu-id="56dfb-168">http://www.w3.org/2004/06/xmlmime</span></span><br /><br /> <span data-ttu-id="56dfb-169">http://www.w3.org/2005/05/xmlmime</span><span class="sxs-lookup"><span data-stu-id="56dfb-169">http://www.w3.org/2005/05/xmlmime</span></span>|  
<span data-ttu-id="56dfb-170">point de distribution</span><span class="sxs-lookup"><span data-stu-id="56dfb-170">dp</span></span>|<span data-ttu-id="56dfb-171">http://schemas.microsoft.com/net/2006/06/duplex</span><span class="sxs-lookup"><span data-stu-id="56dfb-171">http://schemas.microsoft.com/net/2006/06/duplex</span></span>|  
  
## <a name="soap-11-and-soap-12"></a><span data-ttu-id="56dfb-172">SOAP 1.1 et SOAP 1.2</span><span class="sxs-lookup"><span data-stu-id="56dfb-172">SOAP 1.1 and SOAP 1.2</span></span>  
  
### <a name="envelope-and-processing-model"></a><span data-ttu-id="56dfb-173">Enveloppe et modèle de traitement</span><span class="sxs-lookup"><span data-stu-id="56dfb-173">Envelope and Processing Model</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="56dfb-174"> implémente le traitement d'enveloppe SOAP 1.1 en suivant les profils Basic Profile 1.1 (BP11) et Basic Profile 1.0 (SSBP10).</span><span class="sxs-lookup"><span data-stu-id="56dfb-174"> implements SOAP 1.1 envelope processing following Basic Profile 1.1 (BP11) and Basic Profile 1.0 (SSBP10).</span></span> <span data-ttu-id="56dfb-175">Le traitement d'enveloppe SOAP 1.2 est implémenté selon SOAP12-Part1.</span><span class="sxs-lookup"><span data-stu-id="56dfb-175">SOAP 1.2 Envelope processing is implemented following SOAP12-Part1.</span></span>  
  
 <span data-ttu-id="56dfb-176">Cette section explique des certains choix d'implémentation pris par [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] quant à BP11 et SOAP12-Part1.</span><span class="sxs-lookup"><span data-stu-id="56dfb-176">This section explains certain implementation choices taken by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] with regard to BP11 and SOAP12-Part1.</span></span>  
  
#### <a name="mandatory-header-processing"></a><span data-ttu-id="56dfb-177">Traitement obligatoire des en-têtes</span><span class="sxs-lookup"><span data-stu-id="56dfb-177">Mandatory Header Processing</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="56dfb-178"> suit les règles de traitement des en-têtes marqués `mustUnderstand` décrites dans les spécifications SOAP 1.1 et SOAP 1.2, avec les variations suivantes.</span><span class="sxs-lookup"><span data-stu-id="56dfb-178"> follows rules for processing headers marked `mustUnderstand` described in the SOAP 1.1 and SOAP 1.2 specifications, with the following variations.</span></span>  
  
 <span data-ttu-id="56dfb-179">Un message qui entre dans la pile de canaux [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] est traité par les canaux individuels configurés par des éléments de liaison associés, par exemple l'encodage de message texte, la sécurité, la messagerie fiable et les transactions.</span><span class="sxs-lookup"><span data-stu-id="56dfb-179">A message that enters the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] channel stack is processed by individual channels configured by associated binding elements, for example, Text Message Encoding, Security, Reliable Messaging, and Transactions.</span></span> <span data-ttu-id="56dfb-180">Chaque canal reconnaît les en-têtes de l'espace de noms associé et les marque comme compris.</span><span class="sxs-lookup"><span data-stu-id="56dfb-180">Each channel recognizes headers from the associated namespace and marks them as understood.</span></span> <span data-ttu-id="56dfb-181">Une fois qu'un message entre le répartiteur, le module de formatage de l'opération lit les en-têtes attendus par le contrat de message/opération correspondant et les marque comme compris.</span><span class="sxs-lookup"><span data-stu-id="56dfb-181">Once a message enters the dispatcher, the operation formatter reads headers expected by the corresponding message/operation contract and marks them understood.</span></span> <span data-ttu-id="56dfb-182">Ensuite, le répartiteur vérifie si des en-têtes restants ne sont pas compris mais marqués comme `mustUnderstand` et lève une exception.</span><span class="sxs-lookup"><span data-stu-id="56dfb-182">Then the dispatcher verifies whether any remaining headers are not understood but marked as `mustUnderstand` and throws an exception.</span></span> <span data-ttu-id="56dfb-183">Les messages qui contiennent des en-têtes `mustUnderstand` ciblant le destinataire ne sont pas traités par le code de l'application destinataire.</span><span class="sxs-lookup"><span data-stu-id="56dfb-183">Messages that contain `mustUnderstand` headers that are targeted at the recipient are not processed by recipient application code.</span></span>  
  
 <span data-ttu-id="56dfb-184">Un tel traitement par couches permet de séparer les couches d'infrastructure et les couches d'application du nœud SOAP :</span><span class="sxs-lookup"><span data-stu-id="56dfb-184">Such layered processing allows for separation between infrastructure layers and application layers of the SOAP node:</span></span>  
  
-   <span data-ttu-id="56dfb-185">B1111: les en-têtes non compris sont détectés après que le message a été traité par la pile de canaux de l'infrastructure [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], mais avant qu'il ne soit traité par l'application.</span><span class="sxs-lookup"><span data-stu-id="56dfb-185">B1111: Headers that are not understood are detected after the message is processed by the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] infrastructure channel stack, but before it is processed by application</span></span>  
  
     <span data-ttu-id="56dfb-186">La valeur d'en-tête `mustUnderstand` diffère entre SOAP 1.1 et SOAP 1.2.</span><span class="sxs-lookup"><span data-stu-id="56dfb-186">The `mustUnderstand` header value differs between SOAP 1.1 and SOAP 1.2.</span></span> <span data-ttu-id="56dfb-187">Basic Profile 1.1 exige que la valeur `mustUnderstand` soit définie sur 0 ou 1 pour les messages SOAP 1.1.</span><span class="sxs-lookup"><span data-stu-id="56dfb-187">Basic Profile 1.1 requires that the `mustUnderstand` value be 0 or 1 for SOAP 1.1 messages.</span></span> <span data-ttu-id="56dfb-188">SOAP 1.2 accepte les valeurs 0, 1, `false` et `true`, mais recommande d'émettre une représentation canonique de valeurs `xs:boolean` (`false`, `true`).</span><span class="sxs-lookup"><span data-stu-id="56dfb-188">SOAP 1.2 allows 0, 1, `false`, and `true` as values, but recommends emitting a canonical representation of `xs:boolean` values (`false`, `true`).</span></span>  
  
-   <span data-ttu-id="56dfb-189">B1112 : [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] émet les valeurs `mustUnderstand` de 0 et 1 pour les versions SOAP 1.1 et SOAP 1.2 de l'enveloppe SOAP.</span><span class="sxs-lookup"><span data-stu-id="56dfb-189">B1112: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] emits `mustUnderstand` values 0 and 1 for both SOAP 1.1 and SOAP 1.2 versions of the SOAP envelope.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="56dfb-190"> accepte l'espace de valeur entier de `xs:boolean` pour l'en-tête `mustUnderstand` (0, 1, `false`, `true`)</span><span class="sxs-lookup"><span data-stu-id="56dfb-190"> accepts the entire value space of `xs:boolean` for the `mustUnderstand` header (0, 1, `false`, `true`)</span></span>  
  
#### <a name="soap-faults"></a><span data-ttu-id="56dfb-191">Erreurs SOAP</span><span class="sxs-lookup"><span data-stu-id="56dfb-191">SOAP Faults</span></span>  
 <span data-ttu-id="56dfb-192">Voici une liste d'erreurs d'implémentation de SOAP spécifiques à [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="56dfb-192">The following is a list of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]-specific SOAP fault implementations.</span></span>  
  
-   <span data-ttu-id="56dfb-193">B2121 : [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] retourne les Codes d’erreur SOAP 1.1 suivantes : `s11:mustUnderstand`, `s11:Client`, et `s11:Server`.</span><span class="sxs-lookup"><span data-stu-id="56dfb-193">B2121: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] returns the following SOAP 1.1 Fault Codes: `s11:mustUnderstand`, `s11:Client`, and `s11:Server`.</span></span>  
  
-   <span data-ttu-id="56dfb-194">B2122 : [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] retourne les codes d'erreur SOAP 1.2 suivants : `s12:MustUnderstand`, `s12:Sender` et `s12:Receiver`.</span><span class="sxs-lookup"><span data-stu-id="56dfb-194">B2122: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] returns the following SOAP 1.2 Fault Codes: `s12:MustUnderstand`, `s12:Sender`, and `s12:Receiver`.</span></span>  
  
### <a name="http-binding"></a><span data-ttu-id="56dfb-195">Liaison HTTP</span><span class="sxs-lookup"><span data-stu-id="56dfb-195">HTTP Binding</span></span>  
  
#### <a name="soap-11-http-binding"></a><span data-ttu-id="56dfb-196">Liaison HTTP SOAP 1.1</span><span class="sxs-lookup"><span data-stu-id="56dfb-196">SOAP 1.1 HTTP Binding</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="56dfb-197"> implémente la liaison HTTP SOAP1.1 en suivant la spécification Basic Profile 1.1 section 3.4 avec les éclaircissements suivants :</span><span class="sxs-lookup"><span data-stu-id="56dfb-197"> implements SOAP1.1 HTTP binding following the Basic Profile 1.1 specification section 3.4 with the following clarifications:</span></span>  
  
-   <span data-ttu-id="56dfb-198">B2211 : le service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] n'implémente pas la redirection des demandes HTTP POST.</span><span class="sxs-lookup"><span data-stu-id="56dfb-198">B2211: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service does not implement redirection of HTTP POST requests.</span></span>  
  
-   <span data-ttu-id="56dfb-199">B2212 : les clients [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] prennent en charge les cookies HTTP conformément à 3.4.8.</span><span class="sxs-lookup"><span data-stu-id="56dfb-199">B2212: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] clients support HTTP Cookies in accordance with 3.4.8.</span></span>  
  
#### <a name="soap-12-http-binding"></a><span data-ttu-id="56dfb-200">Liaison HTTP SOAP 1,2</span><span class="sxs-lookup"><span data-stu-id="56dfb-200">SOAP 1.2 HTTP Binding</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="56dfb-201"> implémente la liaison HTTP SOAP 1.2 telle que décrite dans la spécification SOAP 1.2-part 2 (SOAP12Part2) avec les éclaircissements suivants.</span><span class="sxs-lookup"><span data-stu-id="56dfb-201"> implements SOAP 1.2 HTTP binding as described in the SOAP 1.2-part 2 (SOAP12Part2) specification with the following clarifications.</span></span>  
  
 <span data-ttu-id="56dfb-202">SOAP 1.2 a introduit un paramètre d'action facultatif pour le type de média `application/soap+xml`.</span><span class="sxs-lookup"><span data-stu-id="56dfb-202">SOAP 1.2 introduced an optional action parameter for the `application/soap+xml` media type.</span></span> <span data-ttu-id="56dfb-203">Ce paramètre est utile pour optimiser la distribution du message sans que le corps du message SOAP soit analysé lorsque la spécification WS-Addressing n'est pas utilisée.</span><span class="sxs-lookup"><span data-stu-id="56dfb-203">This parameter is useful to optimize message dispatch without requiring that the body of the SOAP message be parsed when WS-Addressing is not used.</span></span>  
  
-   <span data-ttu-id="56dfb-204">R2221 : le paramètre d'action `application/soap+xml`, lorsqu'il est présent dans une demande SOAP 1.2, doit correspondre à l'attribut `soapAction` sur l'élément `wsoap12:operation` dans la liaison WSDL correspondante.</span><span class="sxs-lookup"><span data-stu-id="56dfb-204">R2221: The `application/soap+xml` action parameter, when present on a SOAP 1.2 request, must match the `soapAction` attribute on the `wsoap12:operation` element inside the corresponding WSDL binding.</span></span>  
  
-   <span data-ttu-id="56dfb-205">R2222 : le paramètre d'action `application/soap+xml`, lorsqu'il est présent dans un message SOAP 1.2, doit correspondre à `wsa:Action` lorsque la spécification WS-Addressing 2004/08 ou WS-Addressing 1.0 est utilisée.</span><span class="sxs-lookup"><span data-stu-id="56dfb-205">R2222: The `application/soap+xml` action parameter, when present on a SOAP 1.2 message, must match `wsa:Action` when WS-Addressing 2004/08 or WS-Addressing 1.0 are used.</span></span>  
  
 <span data-ttu-id="56dfb-206">Lorsque la spécification WS-Addressing est désactivée et qu'une demande entrante ne contient pas de paramètre d'action, l'`Action` du message est considérée comme non spécifiée.</span><span class="sxs-lookup"><span data-stu-id="56dfb-206">When WS-Addressing is disabled and an incoming request does not contain an action parameter, message `Action` is considered not specified.</span></span>  
  
## <a name="ws-addressing"></a><span data-ttu-id="56dfb-207">WS-Addressing</span><span class="sxs-lookup"><span data-stu-id="56dfb-207">WS-Addressing</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="56dfb-208"> implémente 3 versions de WS-Addressing :</span><span class="sxs-lookup"><span data-stu-id="56dfb-208"> implements 3 versions of WS-Addressing:</span></span>  
  
-   <span data-ttu-id="56dfb-209">WS-Addressing 2004/08</span><span class="sxs-lookup"><span data-stu-id="56dfb-209">WS-Addressing 2004/08</span></span>  
  
-   <span data-ttu-id="56dfb-210">W3C Web Services Addressing 1.0 Core (ADDR10-CORE) et liaison SOAP (ADDR10-SOAP)</span><span class="sxs-lookup"><span data-stu-id="56dfb-210">W3C Web Services Addressing 1.0 Core  (ADDR10-CORE) and SOAP Binding (ADDR10-SOAP)</span></span>  
  
-   <span data-ttu-id="56dfb-211">WS-Addressing 1.0 - Métadonnées</span><span class="sxs-lookup"><span data-stu-id="56dfb-211">WS-Addressing 1.0 - Metadata</span></span>  
  
### <a name="endpoint-references"></a><span data-ttu-id="56dfb-212">Références de point de terminaison</span><span class="sxs-lookup"><span data-stu-id="56dfb-212">Endpoint References</span></span>  
 <span data-ttu-id="56dfb-213">Toutes les versions de WS-Addressing que [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] implémente utilisent des références de point de terminaison pour décrire des points de terminaison.</span><span class="sxs-lookup"><span data-stu-id="56dfb-213">All versions of WS-Addressing that [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] implements use endpoint references to describe endpoints.</span></span>  
  
#### <a name="endpoint-references-and-ws-addressing-versions"></a><span data-ttu-id="56dfb-214">Références de point de terminaison et versions de WS-Addressing</span><span class="sxs-lookup"><span data-stu-id="56dfb-214">Endpoint References and WS-Addressing Versions</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="56dfb-215"> implémente plusieurs protocoles d'infrastructure qui utilisent WS-Addressing et en particulier l'élément `EndpointReference` et la classe `W3C.WsAddressing.EndpointReferenceType` (par exemple, le WS-ReliableMessaging, WS-SecureConversation et WS-Trust).</span><span class="sxs-lookup"><span data-stu-id="56dfb-215"> implements a number of the infrastructure protocols that use WS-Addressing and in particular the `EndpointReference` element and `W3C.WsAddressing.EndpointReferenceType` class (for example, WS-ReliableMessaging, WS-SecureConversation, and WS-Trust).</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="56dfb-216"> prend en charge l'utilisation des deux versions de WS-Addressing avec d'autres protocoles d'infrastructure.</span><span class="sxs-lookup"><span data-stu-id="56dfb-216"> supports the use of either version of WS-Addressing with other infrastructure protocols.</span></span> <span data-ttu-id="56dfb-217">Les points de terminaison [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] prennent en charge une version de WS-Addressing par point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="56dfb-217">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] endpoints support one version of WS-Addressing per endpoint.</span></span>  
  
 <span data-ttu-id="56dfb-218">Pour R3111, l'espace de noms pour l'élément `EndpointReference` ou le type utilisé dans les messages échangés avec un point de terminaison [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] doit correspondre à la version de WS-Addressing implémentée par ce point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="56dfb-218">For R3111, the namespace for the `EndpointReference` element or type used in messages exchanged with a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] endpoint must match the version of WS-Addressing implemented by this endpoint.</span></span>  
  
 <span data-ttu-id="56dfb-219">Par exemple, si un point de terminaison [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] implémente WS-ReliableMessaging, l'en-tête `AcksTo` retourné par un tel point de terminaison à l'intérieur de `CreateSequenceResponse` utilise la version de WS-Addressing que l'élément `EncodingBinding` spécifie pour ce point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="56dfb-219">For example, if a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] endpoint implements WS-ReliableMessaging, the `AcksTo` header returned by such an endpoint inside `CreateSequenceResponse` uses the WS-Addressing version that the `EncodingBinding` element specifies for this endpoint.</span></span>  
  
#### <a name="endpoint-references-and-metadata"></a><span data-ttu-id="56dfb-220">Références de point de terminaison et métadonnées</span><span class="sxs-lookup"><span data-stu-id="56dfb-220">Endpoint References and Metadata</span></span>  
 <span data-ttu-id="56dfb-221">Plusieurs scénarios nécessitent de communiquer des métadonnées ou une référence aux métadonnées pour un point de terminaison donné.</span><span class="sxs-lookup"><span data-stu-id="56dfb-221">A number of scenarios require communicating metadata or a reference to metadata for a given endpoint.</span></span>  
  
 <span data-ttu-id="56dfb-222">B3121 : [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] utilise les mécanismes décrits dans la spécification WS-MetadataExchange (MEX) section 6 pour inclure les métadonnées dans les références de point de terminaison par valeur ou par référence.</span><span class="sxs-lookup"><span data-stu-id="56dfb-222">B3121: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] employs mechanisms described in the WS-MetadataExchange (MEX) specification Section 6 to include metadata for endpoint references by value or by reference.</span></span>  
  
 <span data-ttu-id="56dfb-223">Considérez un scénario dans lequel un service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] requiert l'authentification à l'aide d'un jeton SAML (Security Assertions Markup Language) publié par l'émetteur de jetons à l'adresse http://sts.fabrikam123.com. Le point de terminaison [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] décrit cette spécification d'authentification en utilisant l'assertion `sp:IssuedToken` avec une assertion `sp:Issuer` imbriquée qui pointe sur l'émetteur de jetons.</span><span class="sxs-lookup"><span data-stu-id="56dfb-223">Consider a scenario where a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service requires authentication using a Security Assertions Markup Language (SAML) token issued by the token issuer at http://sts.fabrikam123.com. The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] endpoint describes this authentication requirement by using `sp:IssuedToken` assertion with a nested `sp:Issuer` assertion pointing to the token issuer.</span></span> <span data-ttu-id="56dfb-224">Les applications clientes qui accèdent à l'assertion `sp:Issuer` doivent savoir comment communiquer avec l'émetteur du jetons du point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="56dfb-224">Client applications that access the `sp:Issuer` assertion need to know how to communicate with the token issuer endpoint.</span></span> <span data-ttu-id="56dfb-225">Le client a besoin de connaître les métadonnées relatives à l'émetteur de jetons.</span><span class="sxs-lookup"><span data-stu-id="56dfb-225">The client needs to know metadata about the token issuer.</span></span> <span data-ttu-id="56dfb-226">À l'aide des extensions de métadonnées de la référence de point de terminaison définies dans MEX, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] fournit une référence aux métadonnées de l'émetteur de jetons.</span><span class="sxs-lookup"><span data-stu-id="56dfb-226">Using the endpoint reference metadata extensions defined in MEX, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] provides a reference to the token issuer metadata.</span></span>  
  
```xml  
<sp:IssuedToken>  
  <sp:Issuer>  
    <wsa10:Address>  
      http://sts.fabrikam123.com  
    </wsa10:Address>  
    <wsa10:Metadata>  
      <mex:Metadata>  
        <mex:MetadataSection>  
          <mex:MetadataReference>  
            <wsa10:Address>  
              http://sts.fabrikam123.com/mex  
            </wsa10:Address>  
          </mex:MetadataReference>  
        </mex:MetadataSection>  
      </mex:Metadata>  
    </wsa10:Metadata>  
  </sp:Issuer>  
</sp:IssuedToken>  
```  
  
### <a name="message-addressing-headers"></a><span data-ttu-id="56dfb-227">En-têtes d'adressage des messages</span><span class="sxs-lookup"><span data-stu-id="56dfb-227">Message Addressing Headers</span></span>  
  
#### <a name="message-headers"></a><span data-ttu-id="56dfb-228">En-têtes de message</span><span class="sxs-lookup"><span data-stu-id="56dfb-228">Message Headers</span></span>  
 <span data-ttu-id="56dfb-229">Pour les deux versions de WS-Addressing, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] utilise les en-têtes de message suivants comme le prescrivent les spécifications `wsa:To`, `wsa:ReplyTo`, `wsa:Action`, `wsa:MessageID`, et `wsa:RelatesTo`.</span><span class="sxs-lookup"><span data-stu-id="56dfb-229">For both WS-Addressing versions, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uses the following message headers as prescribed by the specifications `wsa:To`, `wsa:ReplyTo`, `wsa:Action`, `wsa:MessageID`,and `wsa:RelatesTo`.</span></span>  
  
 <span data-ttu-id="56dfb-230">B3211 : pour toutes les versions de WS-Addressing, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] respecte mais ne produit pas directement les en-têtes de message WS-Addressing `wsa:FaultTo` et `wsa:From`.</span><span class="sxs-lookup"><span data-stu-id="56dfb-230">B3211: For all WS-Addressing versions, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] honors, but does not produce out of the box, WS-Addressing message headers `wsa:FaultTo` and `wsa:From`.</span></span>  
  
 <span data-ttu-id="56dfb-231">Les applications qui interagissent avec les applications [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] peuvent ajouter que ces en-têtes de message et [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] les traitera en conséquence.</span><span class="sxs-lookup"><span data-stu-id="56dfb-231">Applications that interact with [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications can add these message headers and [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] will process them accordingly.</span></span>  
  
#### <a name="reference-parameters-and-properties"></a><span data-ttu-id="56dfb-232">Paramètres et propriétés de référence</span><span class="sxs-lookup"><span data-stu-id="56dfb-232">Reference Parameters and Properties</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="56dfb-233"> implémente le traitement des paramètres de référence de point de terminaison et des propriétés de référence</span><span class="sxs-lookup"><span data-stu-id="56dfb-233"> implements processing of endpoint reference parameters and reference p</span></span>  
  
 <span data-ttu-id="56dfb-234">conformément aux spécifications respectives.</span><span class="sxs-lookup"><span data-stu-id="56dfb-234">roperties in accordance with respective specifications.</span></span>  
  
 <span data-ttu-id="56dfb-235">B3221: lorsqu'ils sont configurés pour utiliser WS-Addressing 2004/08, les points de terminaison [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ne font pas la différence entre le traitement des propriétés de référence et des paramètres de référence.</span><span class="sxs-lookup"><span data-stu-id="56dfb-235">B3221: When configured to use WS-Addressing 2004/08, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] endpoints do not differentiate between processing Reference Properties and Reference Parameters.</span></span>  
  
### <a name="message-exchange-patterns"></a><span data-ttu-id="56dfb-236">Modèles d’échange de messages</span><span class="sxs-lookup"><span data-stu-id="56dfb-236">Message Exchange Patterns</span></span>  
 <span data-ttu-id="56dfb-237">La séquence de messages impliquée dans l’appel d’opération de service Web est appelée le *modèle d’échange de message*.</span><span class="sxs-lookup"><span data-stu-id="56dfb-237">The sequence of messages involved in the Web service operation invocation is referred to as the *message exchange pattern*.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="56dfb-238"> prend en charge les modèles d'échange de messages duplex, demande-réponse et unidirectionnels.</span><span class="sxs-lookup"><span data-stu-id="56dfb-238"> supports one-way, request-reply, and duplex message exchange patterns.</span></span> <span data-ttu-id="56dfb-239">Cette section clarifie les exigences WS-Addressing de traitement des messages en fonction du modèle d’échange de messages utilisé.</span><span class="sxs-lookup"><span data-stu-id="56dfb-239">This section clarifies WS-Addressing requirements on message processing depending on the message exchange pattern being used.</span></span>  
  
 <span data-ttu-id="56dfb-240">Dans cette section, le demandeur envoie le premier message et le répondeur reçoit le premier message.</span><span class="sxs-lookup"><span data-stu-id="56dfb-240">Throughout this section, the requester sends the first message and the responder receives the first message.</span></span>  
  
#### <a name="one-way-message"></a><span data-ttu-id="56dfb-241">Message unidirectionnel</span><span class="sxs-lookup"><span data-stu-id="56dfb-241">One-Way Message</span></span>  
 <span data-ttu-id="56dfb-242">Lorsqu'un point de terminaison [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] est configuré pour prendre en charge les messages avec une `Action` donnée qui suivent d'un modèle unidirectionnel, le point de terminaison [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] observe les comportements et les spécifications qui suivent.</span><span class="sxs-lookup"><span data-stu-id="56dfb-242">When a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] endpoint is configured to support messages with a given `Action` to follow a one-way pattern, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] endpoint follows the following behaviors and requirements.</span></span> <span data-ttu-id="56dfb-243">Sauf spécification contraire, les comportements et les règles s'appliquent aux deux versions de WS-Addressing prises en charge par [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] :</span><span class="sxs-lookup"><span data-stu-id="56dfb-243">Unless otherwise specified, behaviors and rules apply for both versions of WS-Addressing supported in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:</span></span>  
  
-   <span data-ttu-id="56dfb-244">R3311 : le demandeur doit inclure `wsa:To`, `wsa:Action` et les en-têtes pour tous les paramètres de référence spécifiés par la référence de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="56dfb-244">R3311: The requester must include `wsa:To`, `wsa:Action`, and headers for all reference parameters specified by the endpoint reference.</span></span> <span data-ttu-id="56dfb-245">Lorsque WS-Addressing 2004/08 est utilisée et que des [propriétés de référence] sont spécifiées par la référence de point de terminaison, les en-têtes correspondants doivent également être ajoutés au message.</span><span class="sxs-lookup"><span data-stu-id="56dfb-245">When WS-Addressing 2004/08 is used and [reference properties] are specified by the endpoint reference, the corresponding headers must be added to the message too.</span></span>  
  
-   <span data-ttu-id="56dfb-246">B3312: le demandeur peut inclure les en-têtes `MessageID`, `ReplyTo` et `FaultTo`.</span><span class="sxs-lookup"><span data-stu-id="56dfb-246">B3312: The requester may include `MessageID`, `ReplyTo`, and `FaultTo` headers.</span></span> <span data-ttu-id="56dfb-247">L'infrastructure du récepteur les ignorera, et ils seront passés à l'application.</span><span class="sxs-lookup"><span data-stu-id="56dfb-247">The receiver infrastructure will ignore them, and they will be passed to the application.</span></span>  
  
-   <span data-ttu-id="56dfb-248">R3313: lorsque le HTTP est utilisé et qu'aucun message n'est envoyé sur la section de réponse HTTP, le répondeur doit envoyer une réponse HTTP avec un corps vide et un code d'état HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="56dfb-248">R3313: When HTTP is used and no message is being sent on the HTTP response leg, the responder must send an HTTP response with an empty body and an HTTP 202 status code.</span></span>  
  
     <span data-ttu-id="56dfb-249">Lorsque le transport HTTP est utilisé et que le contrat d'opération déclare un message unidirectionnel, la réponse HTTP peut encore être utilisée pour envoyer les messages d'infrastructure. Par exemple, la messagerie fiable peut envoyer un message `SequenceAcknowledgement` sur une réponse HTTP.</span><span class="sxs-lookup"><span data-stu-id="56dfb-249">When the HTTP transport is in use and the operation contract declares a message one-way, the HTTP response can still be used for sending infrastructure messages—for example, reliable messaging can send a `SequenceAcknowledgement` message on an HTTP response.</span></span>  
  
-   <span data-ttu-id="56dfb-250">B3314 : le répondeur [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] n'envoie pas de message d'erreur en réponse à un message unidirectionnel.</span><span class="sxs-lookup"><span data-stu-id="56dfb-250">B3314: The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] responder does not send a fault message in response to a one-way message.</span></span>  
  
#### <a name="request-reply"></a><span data-ttu-id="56dfb-251">Demande-réponse</span><span class="sxs-lookup"><span data-stu-id="56dfb-251">Request-Reply</span></span>  
 <span data-ttu-id="56dfb-252">Lorsqu'un point de terminaison [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] est configuré de manière à ce qu'un message avec une `Action` donnée suive le modèle demande-réponse, le point de terminaison [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] suit les comportements et les spécifications ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="56dfb-252">When a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] endpoint is configured for a message with a given `Action` to follow the request-reply pattern, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] endpoint follows the behaviors and requirements below.</span></span> <span data-ttu-id="56dfb-253">Sauf spécification contraire, les comportements et les règles s'appliquent aux deux versions de WS-Addressing prises en charge par [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] :</span><span class="sxs-lookup"><span data-stu-id="56dfb-253">Unless specified otherwise, behaviors and rules apply for both versions of WS-Addressing supported in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:</span></span>  
  
-   <span data-ttu-id="56dfb-254">R3321 : Le demandeur doit inclure dans la demande `wsa:To`, `wsa:Action`, `wsa:MessageID`et les en-têtes pour tous les paramètres de référence ou référence propriétés (ou les deux) spécifiés par la référence de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="56dfb-254">R3321: The requester must include in the request `wsa:To`, `wsa:Action`, `wsa:MessageID`, and headers for all reference parameters or reference properties (or both) specified by the endpoint reference.</span></span>  
  
-   <span data-ttu-id="56dfb-255">R3322 : lorsque WS-Addressing 2004/08 est utilisée, `ReplyTo` doit également être inclus dans la demande.</span><span class="sxs-lookup"><span data-stu-id="56dfb-255">R3322: When WS-Addressing 2004/08 is used, `ReplyTo` must also be included in the request.</span></span>  
  
-   <span data-ttu-id="56dfb-256">R3323 : lorsque WS-Addressing 1.0 est utilisée et que `ReplyTo` n'est pas présent dans la demande, une référence de point de terminaison par défaut avec la propriété [adresse] égale à « http://www.w3.org/2005/08/addressing/anonymous » est utilisée.</span><span class="sxs-lookup"><span data-stu-id="56dfb-256">R3323: When WS-Addressing 1.0 is used and `ReplyTo` is not present in the request, a default endpoint reference with the [address] property equal to "http://www.w3.org/2005/08/addressing/anonymous" is used.</span></span>  
  
-   <span data-ttu-id="56dfb-257">R3324 : Le demandeur doit inclure `wsa:To`, `wsa:Action`, et `wsa:RelatesTo` en-têtes du message de réponse, ainsi que les en-têtes pour tous les paramètres de référence ou référence propriétés (ou les deux) spécifiés par la `ReplyTo` référence de point de terminaison dans le demande.</span><span class="sxs-lookup"><span data-stu-id="56dfb-257">R3324: The requester must include `wsa:To`, `wsa:Action`, and `wsa:RelatesTo` headers in the reply message, as well as headers for all reference parameters or reference properties (or both) specified by the `ReplyTo` endpoint reference in the request.</span></span>  
  
### <a name="web-services-addressing-faults"></a><span data-ttu-id="56dfb-258">Erreurs d'adressage des services Web</span><span class="sxs-lookup"><span data-stu-id="56dfb-258">Web Services Addressing Faults</span></span>  
 <span data-ttu-id="56dfb-259">R3411 : [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] produit les erreurs suivantes définies par WS-Addressing 2004/08.</span><span class="sxs-lookup"><span data-stu-id="56dfb-259">R3411: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] produces the following faults defined by WS-Addressing 2004/08.</span></span>  
  
|<span data-ttu-id="56dfb-260">Code</span><span class="sxs-lookup"><span data-stu-id="56dfb-260">Code</span></span>|<span data-ttu-id="56dfb-261">Cause</span><span class="sxs-lookup"><span data-stu-id="56dfb-261">Cause</span></span>|  
|----------|-----------|  
|<span data-ttu-id="56dfb-262">wsa:DestinationUnreachable</span><span class="sxs-lookup"><span data-stu-id="56dfb-262">wsa:DestinationUnreachable</span></span>|<span data-ttu-id="56dfb-263">Le message est arrivé avec un `ReplyTo` différent de l'adresse de réponse établie pour ce canal ; il n'y a aucun point de terminaison qui écoute l'adresse spécifiée dans l'en-tête To.</span><span class="sxs-lookup"><span data-stu-id="56dfb-263">The message arrived with a `ReplyTo` that is different from the reply address established for this channel; there is no endpoint listening at the address specified in the To header.</span></span>|  
|<span data-ttu-id="56dfb-264">wsa:ActionNotSupported</span><span class="sxs-lookup"><span data-stu-id="56dfb-264">wsa:ActionNotSupported</span></span>|<span data-ttu-id="56dfb-265">les canaux de l'infrastructure ou le répartiteur associé au point de terminaison ne reconnaissent pas l'action spécifiée dans l'en-tête `Action`.</span><span class="sxs-lookup"><span data-stu-id="56dfb-265">the infrastructure channels or dispatcher associated with the endpoint do not recognize the action specified in the `Action` header.</span></span>|  
  
 <span data-ttu-id="56dfb-266">R3412 : [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] produit les erreurs suivantes définies par WS-Addressing 1.0.</span><span class="sxs-lookup"><span data-stu-id="56dfb-266">R3412: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] produces the following faults defined by WS-Addressing 1.0.</span></span>  
  
|<span data-ttu-id="56dfb-267">Code</span><span class="sxs-lookup"><span data-stu-id="56dfb-267">Code</span></span>|<span data-ttu-id="56dfb-268">Cause</span><span class="sxs-lookup"><span data-stu-id="56dfb-268">Cause</span></span>|  
|----------|-----------|  
|<span data-ttu-id="56dfb-269">wsa10:InvalidAddressingHeader</span><span class="sxs-lookup"><span data-stu-id="56dfb-269">wsa10:InvalidAddressingHeader</span></span>|<span data-ttu-id="56dfb-270">Dupliquer `wsa:To`, `wsa:ReplyTo`, `wsa:From` ou `wsa:MessageID`.</span><span class="sxs-lookup"><span data-stu-id="56dfb-270">Duplicate `wsa:To`, `wsa:ReplyTo`, `wsa:From` or `wsa:MessageID`.</span></span> <span data-ttu-id="56dfb-271">Dupliquer `wsa:RelatesTo` avec le même `RelationshipType`.</span><span class="sxs-lookup"><span data-stu-id="56dfb-271">Duplicate `wsa:RelatesTo` with the same `RelationshipType`.</span></span>|  
|<span data-ttu-id="56dfb-272">wsa10:MessageAddressingHeaderRequired</span><span class="sxs-lookup"><span data-stu-id="56dfb-272">wsa10:MessageAddressingHeaderRequired</span></span>|<span data-ttu-id="56dfb-273">L'en-tête d'adressage requis est absent.</span><span class="sxs-lookup"><span data-stu-id="56dfb-273">The required Addressing header is missing.</span></span>|  
|<span data-ttu-id="56dfb-274">wsa10:DestinationUnreachable</span><span class="sxs-lookup"><span data-stu-id="56dfb-274">wsa10:DestinationUnreachable</span></span>|<span data-ttu-id="56dfb-275">Le message est arrivé avec un `ReplyTo` différent de l'adresse de réponse établie pour ce canal.</span><span class="sxs-lookup"><span data-stu-id="56dfb-275">The message arrived with a `ReplyTo` that is different from the reply address established for this channel.</span></span> <span data-ttu-id="56dfb-276">Il n'y a aucun point de terminaison qui écoute l'adresse spécifiée dans l'en-tête To.</span><span class="sxs-lookup"><span data-stu-id="56dfb-276">There is no endpoint listening at the address specified in the To header.</span></span>|  
|<span data-ttu-id="56dfb-277">wsa10:ActionNotSupported</span><span class="sxs-lookup"><span data-stu-id="56dfb-277">wsa10:ActionNotSupported</span></span>|<span data-ttu-id="56dfb-278">Une action spécifiée dans l'en-tête `Action` n'est pas reconnue par les canaux de l'infrastructure ou le répartiteur associé au point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="56dfb-278">An action specified in the `Action` header is not recognized by the infrastructure channels or dispatcher associated with the endpoint.</span></span>|  
|<span data-ttu-id="56dfb-279">wsa10:EndpointUnavailable</span><span class="sxs-lookup"><span data-stu-id="56dfb-279">wsa10:EndpointUnavailable</span></span>|<span data-ttu-id="56dfb-280">Le canal RM renvoie cette erreur pour indiquer que le point de terminaison ne traitera pas la séquence suite à l'examen des en-têtes d'adressage du message `CreateSequence`.</span><span class="sxs-lookup"><span data-stu-id="56dfb-280">The RM channel sends this fault back, indicating the endpoint will not process the sequence based upon examination of the `CreateSequence` message’s addressing headers.</span></span>|  
  
 <span data-ttu-id="56dfb-281">Le code des tables précédentes correspond à `FaultCode` dans SOAP 1.1 et `SubCode` (avec Code=Expéditeur) dans SOAP 1.2.</span><span class="sxs-lookup"><span data-stu-id="56dfb-281">Code in the preceding tables maps to `FaultCode` in SOAP 1.1 and `SubCode` (with Code=Sender) in SOAP 1.2.</span></span>  
  
### <a name="wsdl-11-binding-and-ws-policy-assertions"></a><span data-ttu-id="56dfb-282">Liaison WSDL 1.1 et assertions de WS-Policy</span><span class="sxs-lookup"><span data-stu-id="56dfb-282">WSDL 1.1 Binding and WS-Policy Assertions</span></span>  
  
#### <a name="indicating-use-of-ws-addressing"></a><span data-ttu-id="56dfb-283">Utilisation recommandée de WS-Addressing</span><span class="sxs-lookup"><span data-stu-id="56dfb-283">Indicating Use of WS-Addressing</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="56dfb-284"> utilise des assertions de stratégie pour indiquer la prise en charge d'un point de terminaison pour une version particulière de WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="56dfb-284"> uses policy assertions to indicate endpoint support for a particular WS-Addressing version.</span></span>  
  
 <span data-ttu-id="56dfb-285">L'assertion de stratégie suivante possède l'objet de stratégie de point de terminaison [WS-PA] et indique que les messages envoyés et reçus depuis le point de terminaison doivent utiliser WS-Addressing 2004/08.</span><span class="sxs-lookup"><span data-stu-id="56dfb-285">The following policy assertion has Endpoint Policy Subject [WS-PA] and indicates messages sent and received from the endpoint must use WS-Addressing 2004/08.</span></span>  
  
```xml  
<wsap:UsingAddressing />  
```  
  
 <span data-ttu-id="56dfb-286">Cette assertion de stratégie complète la spécification WS-Addressing 2004/08.</span><span class="sxs-lookup"><span data-stu-id="56dfb-286">This policy assertion augments the WS-Addressing 2004/08 specification.</span></span>  
  
 <span data-ttu-id="56dfb-287">L'assertion de stratégie indique que les messages envoyés/reçus doivent utiliser WS-Addressing 1.0.</span><span class="sxs-lookup"><span data-stu-id="56dfb-287">The following policy assertion this indicates that messages sent/received must use WS-Addressing 1.0.</span></span>  
  
```xml
<wsam:Addressing/>   
```  
  
 <span data-ttu-id="56dfb-288">L'assertion de stratégie suivante possède un objet de stratégie de point de terminaison [WS-PA] et indique que les messages envoyés et reçus depuis le point de terminaison doivent utiliser WS-Addressing 2004/08.</span><span class="sxs-lookup"><span data-stu-id="56dfb-288">The following policy assertion has an Endpoint Policy Subject [WS-PA] and indicates that messages sent and received from the endpoint must use WS-Addressing 2004/08.</span></span>  
  
```xml  
<wsaw10:UsingAddressing />  
```  
  
 <span data-ttu-id="56dfb-289">L'élément `wsaw10:UsingAddressing` est emprunté à [WS-Adressage-WSDL] et est utilisé dans le contexte de WS-Policy conformément à la section 3.1.2 de cette spécification.</span><span class="sxs-lookup"><span data-stu-id="56dfb-289">The `wsaw10:UsingAddressing` element is borrowed from [WS-Addressing-WSDL] and is used in the context of WS-Policy in compliance with that specification, section 3.1.2.</span></span>  
  
 <span data-ttu-id="56dfb-290">L’utilisation de l’adressage n’altère pas la sémantique des liaisons HTTP WSDL 1.1, SOAP 1.1 et SOAP 1.2.</span><span class="sxs-lookup"><span data-stu-id="56dfb-290">Use of Addressing does not alter the semantics of WSDL 1.1, SOAP 1.1, and SOAP 1.2 HTTP Bindings.</span></span> <span data-ttu-id="56dfb-291">Par exemple, si une réponse est attendue à une demande envoyée à un point de terminaison qui utilise l’adressage et la liaison HTTP WSDL SOAP 1.x, elle doit être envoyée en utilisant la réponse HTTP.</span><span class="sxs-lookup"><span data-stu-id="56dfb-291">For example, if a reply is expected to a request that is sent to an endpoint that uses Addressing and WSDL SOAP 1.x HTTP binding, the reply must be sent by using the HTTP response.</span></span>  
  
 <span data-ttu-id="56dfb-292">Pour les réponses envoyées via HTTP, l'assertion WS-AM est :</span><span class="sxs-lookup"><span data-stu-id="56dfb-292">For replies sent over the http response, the WS-AM assertion is:</span></span>  
  
```xml  
<wsam:AnonymousResponses/>  
```  
  
 <span data-ttu-id="56dfb-293">L'assertion de stratégie complète peut ressembler à ceci :</span><span class="sxs-lookup"><span data-stu-id="56dfb-293">The complete policy assertion might look like this:</span></span>  
  
```xml  
<wsam:Addressing>  
    <wsp:Policy>  
        <wsam:AnonymousResponses />   
    </wsp:Policy>  
</wsam:Addressing>  
```  
  
 <span data-ttu-id="56dfb-294">Toutefois, certains modèles d’échange de messages profitent du fait que deux connexions HTTP réciproques indépendantes soient établies entre le demandeur et le répondeur, par exemple dans le cas de messages unidirectionnels non sollicités envoyés par le répondeur.</span><span class="sxs-lookup"><span data-stu-id="56dfb-294">However, there are message exchange patterns that benefit from having two independent converse HTTP connections established between the requester and the responder, for example, unsolicited one-way messages sent by the responder.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="56dfb-295"> propose un utilitaire grâce auquel deux canaux de transport sous-jacents peuvent former un canal duplex composite, où un canal est utilisé pour les messages d'entrée et l'autre est utilisé pour les messages de sortie.</span><span class="sxs-lookup"><span data-stu-id="56dfb-295"> offers a feature by which two underlying transport channels can form a Composite Duplex channel, where one channel is used for input messages and the other is used for output messages.</span></span> <span data-ttu-id="56dfb-296">Dans le cas du transport HTTP, le canal duplex composite fournit deux connexions HTTP réciproques.</span><span class="sxs-lookup"><span data-stu-id="56dfb-296">In the case of the HTTP Transport, Composite Duplex provides two converse HTTP connections.</span></span> <span data-ttu-id="56dfb-297">Le demandeur utilise une connexion pour envoyer des messages au répondeur, et le répondeur utilise l'autre pour renvoyer des messages au demandeur.</span><span class="sxs-lookup"><span data-stu-id="56dfb-297">The requester uses one connection to send messages to the responder, and the responder uses the other to send messages back to the requester.</span></span>  
  
 <span data-ttu-id="56dfb-298">Pour les réponses envoyées via des demandes HTTP distinctes, l'assertion WS-AM est :</span><span class="sxs-lookup"><span data-stu-id="56dfb-298">For replies sent over separate http requests, the ws-am assertion is</span></span>  
  
```xml  
<wsam:NonAnonymousResponses/>  
```  
  
 <span data-ttu-id="56dfb-299">L'assertion de stratégie complète peut ressembler à ceci :</span><span class="sxs-lookup"><span data-stu-id="56dfb-299">The complete policy assertion might look like this:</span></span>  
  
```xml  
<wsam:Addressing>  
    <wsp:Policy>  
      <wsam:NonAnonymousResponses />   
   </wsp:Policy>  
  </wsam:Addressing>  
```  
  
 <span data-ttu-id="56dfb-300">Pour utiliser l’assertion suivante, qui possède un objet de stratégie de point de terminaison [WS-PA] sur les points de terminaison qui utilisent des liaisons HTTP WSDL 1.1 SOAP 1.x, il est nécessaire d’utiliser deux connexions HTTP réciproques séparées pour transmettre des messages du demandeur au répondeur et du répondeur au demandeur, respectivement.</span><span class="sxs-lookup"><span data-stu-id="56dfb-300">Use of the following assertion that has Endpoint Policy Subject [WS-PA] on endpoints that use WSDL 1.1 SOAP 1.x HTTP bindings requires two separate converse HTTP connections to be used for messages flowing from requester to responder and responder to requester, respectively.</span></span>  
  
```xml  
<cdp:CompositeDuplex/>  
```  
  
 <span data-ttu-id="56dfb-301">L'instruction précédente mène aux spécifications suivantes pour l'en-tête `wsa:ReplyTo` des messages de demande :</span><span class="sxs-lookup"><span data-stu-id="56dfb-301">The previous statement leads to the following requirements on the `wsa:ReplyTo` header for request messages:</span></span>  
  
-   <span data-ttu-id="56dfb-302">R3514 : les messages de demande envoyés à un point de terminaison doivent avoir un en-tête `ReplyTo` avec la propriété `[address]` non égale à « http://www.w3.org/2005/08/addressing/anonymous » si le point de terminaison utilise une liaison HTTP WSDL 1.1 SOAP 1.x et utilise une alternative de stratégie avec une assertion `wsap10:UsingAddressing` ou `wsap:UsingAddressing` associée à une assertion `cdp:CompositeDuplex` jointe.</span><span class="sxs-lookup"><span data-stu-id="56dfb-302">R3514: Request messages sent to an endpoint must have a `ReplyTo` header with the `[address]` property not equal to "http://www.w3.org/2005/08/addressing/anonymous" if the endpoint uses a WSDL 1.1 SOAP 1.x HTTP binding and has a policy alternative with a `wsap10:UsingAddressing` or `wsap:UsingAddressing` assertion coupled with `cdp:CompositeDuplex` attached.</span></span>  
  
-   <span data-ttu-id="56dfb-303">R3515 : les messages de demande envoyés à un point de terminaison doivent avoir un en-tête `ReplyTo` avec la propriété `[address]` égale à « http://www.w3.org/2005/08/addressing/anonymous », ou n'avoir aucun en-tête `ReplyTo`, si le point de terminaison utilise une liaison HTTP WSDL 1.1 SOAP 1.x et utilise une alternative de stratégie avec une assertion `wsap10:UsingAddressing` et aucune assertion `cdp:CompositeDuplex` jointe.</span><span class="sxs-lookup"><span data-stu-id="56dfb-303">R3515: Request messages sent to an endpoint must have a `ReplyTo` header with the `[address]` property equal to "http://www.w3.org/2005/08/addressing/anonymous", or not have a `ReplyTo` header at all, if the endpoint uses a WSDL 1.1 SOAP 1.x HTTP binding and has a policy alternative with `wsap10:UsingAddressing` assertion and no `cdp:CompositeDuplex` assertion attached.</span></span>  
  
-   <span data-ttu-id="56dfb-304">R3516 : les messages de demande envoyés à un point de terminaison doivent avoir un en-tête `ReplyTo` avec une propriété `[address]` égale à « http://www.w3.org/2005/08/addressing/anonymous » si le point de terminaison utilise une liaison HTTP WSDL 1.1 SOAP 1.x et utilise une alternative de stratégie avec une assertion `wsap:UsingAddressing` et aucune assertion `cdp:CompositeDuplex` jointe.</span><span class="sxs-lookup"><span data-stu-id="56dfb-304">R3516: Request messages sent to an endpoint must have a `ReplyTo` header with an `[address]` property equal to "http://www.w3.org/2005/08/addressing/anonymous" if the endpoint uses a WSDL 1.1 SOAP 1.x HTTP binding and has a policy alternative with `wsap:UsingAddressing` assertion and no `cdp:CompositeDuplex` assertion attached.</span></span>  
  
 <span data-ttu-id="56dfb-305">La spécification WSDL de WS-Addressing tente de décrire des liaisons de protocole semblables en présentant un élément `<wsaw:Anonymous/>` avec trois valeurs textuelles (obligatoire, facultatif et a interdit) pour indiquer des besoins sur l'en-tête `wsa:ReplyTo` (section 3.2).</span><span class="sxs-lookup"><span data-stu-id="56dfb-305">The WS-addressing WSDL specification attempts to describe similar protocol bindings by introducing an element `<wsaw:Anonymous/>` with three textual values (required, optional, and prohibited) to indicate requirements on the `wsa:ReplyTo` header (section 3.2).</span></span> <span data-ttu-id="56dfb-306">Malheureusement, une telle définition d'élément n'est pas particulièrement utilisable comme une assertion dans le contexte de WS-Policy, car il requiert que les extensions spécifiques au domaine prennent en charge l'intersection d'alternatives à l'aide d'un élément de ce type comme une assertion.</span><span class="sxs-lookup"><span data-stu-id="56dfb-306">Unfortunately, such element definition is not particularly usable as an assertion in the context of WS-Policy, because it requires domain-specific extensions to support the intersection of alternatives using such an element as an assertion.</span></span> <span data-ttu-id="56dfb-307">Une telle définition d'élément indique également la valeur de l'en-tête `ReplyTo` par opposition au comportement du point de terminaison sur la transmission, ce qui le rend spécifique au transport HTTP.</span><span class="sxs-lookup"><span data-stu-id="56dfb-307">Such element definition also indicates the value of the `ReplyTo` header as opposed to the endpoint behavior on the wire, which makes it specific to HTTP transport.</span></span>  
  
#### <a name="action-definition"></a><span data-ttu-id="56dfb-308">Définition d'action</span><span class="sxs-lookup"><span data-stu-id="56dfb-308">Action Definition</span></span>  
 <span data-ttu-id="56dfb-309">WS-Addressing 2004/08 définit un attribut `wsa:Action` pour les éléments `wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]`.</span><span class="sxs-lookup"><span data-stu-id="56dfb-309">WS-Addressing 2004/08 defines a `wsa:Action` attribute for the `wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]` elements.</span></span> <span data-ttu-id="56dfb-310">La liaison WS-Addressing 1.0 WSDL (WS-ADDR10-WSDL) définit un attribut semblable, `wsaw10:Action`.</span><span class="sxs-lookup"><span data-stu-id="56dfb-310">WS-Addressing 1.0 WSDL Binding (WS-ADDR10-WSDL) defines a similar attribute, `wsaw10:Action`.</span></span>  
  
 <span data-ttu-id="56dfb-311">La seule différence entre les deux réside dans la sémantique du modèle d’action par défaut décrite à la section 3.3.2 de WS-ADDR et à la section 4.4.4 de WS-ADDR10-WSDL, respectivement.</span><span class="sxs-lookup"><span data-stu-id="56dfb-311">The only difference between the two is the default Action pattern semantics described in section 3.3.2 of WS-ADDR and section 4.4.4 of WS-ADDR10-WSDL, respectively.</span></span>  
  
 <span data-ttu-id="56dfb-312">Il est raisonnable d'avoir deux points de terminaison qui partagent le même `portType` (ou contrat, dans la terminologie [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]) mais utilisant des versions différentes de WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="56dfb-312">It is a reasonable to have two endpoints that share the same `portType` (or contract, in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] terminology) but using different versions of WS-Addressing.</span></span> <span data-ttu-id="56dfb-313">Mais étant donné que cette action est définie par le `portType` et ne doit pas pour les points de terminaison qui implémentent le `portType`, il devient impossible de prendre en charge les deux modèles d'action par défaut.</span><span class="sxs-lookup"><span data-stu-id="56dfb-313">But given that Action is defined by the `portType` and should not change across the endpoints that implement the `portType`, it becomes impossible to support both default action patterns.</span></span>  
  
 <span data-ttu-id="56dfb-314">Pour résoudre ce conflit, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] prend en charge une version unique de l'attribut `Action`.</span><span class="sxs-lookup"><span data-stu-id="56dfb-314">To resolve this controversy, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] supports a single version of the `Action` attribute.</span></span>  
  
 <span data-ttu-id="56dfb-315">B3521 : [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] utilise l'attribut `wsaw10:Action` sur les éléments `wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]` comme défini dans WS-ADDR10-WSDL pour déterminer l'URI `Action` pour les messages correspondants quelle que soit la version de WS-Addressing utilisée par le point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="56dfb-315">B3521: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uses the `wsaw10:Action` attribute on `wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]` elements as defined in WS-ADDR10-WSDL to determine the `Action` URI for the corresponding messages irrespective of the WS-Addressing version used by the endpoint.</span></span>  
  
#### <a name="use-endpoint-reference-inside-wsdl-port"></a><span data-ttu-id="56dfb-316">Utilisation des références de point de terminaison à l'intérieur d'un port WSDL</span><span class="sxs-lookup"><span data-stu-id="56dfb-316">Use Endpoint Reference Inside WSDL Port</span></span>  
 <span data-ttu-id="56dfb-317">La section 4.1 de WS-ADDR10-WSDL étend l'élément `wsdl:port` de manière à inclure l'élément enfant `<wsa10:EndpointReference…/>` et décrire le point de terminaison en des termes propres à WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="56dfb-317">WS-ADDR10-WSDL section 4.1 extends the `wsdl:port` element to include the `<wsa10:EndpointReference…/>` child element to describe the endpoint in WS-Addressing terms.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="56dfb-318"> étend cette fonctionnalité à WS-Addressing 2004/08, en permettant à `<wsa:EndpointReference…/>` d'apparaître en tant qu'élément enfant de `wsdl:port`.</span><span class="sxs-lookup"><span data-stu-id="56dfb-318"> expands this utility on WS-Addressing 2004/08, allowing `<wsa:EndpointReference…/>` to appear as a child element of `wsdl:port`.</span></span>  
  
-   <span data-ttu-id="56dfb-319">R3531 : si un point de terminaison possède une alternative de stratégie attachée avec une assertion de la stratégie `<wsaw10:UsingAddressing/>`, l'élément `wsdl:port` correspondant peut contenir un élément enfant `<wsa10:EndpointReference …/>`.</span><span class="sxs-lookup"><span data-stu-id="56dfb-319">R3531: If an endpoint has an attached policy alternative with a `<wsaw10:UsingAddressing/>` policy assertion, the corresponding `wsdl:port` element can contain a child element `<wsa10:EndpointReference …/>`.</span></span>  
  
-   <span data-ttu-id="56dfb-320">R3532 : Si un `wsdl:port` contient un élément enfant `<wsa10:EndpointReference …/>`, le `wsa10:EndpointReference/wsa10:Address` valeur de l’élément enfant doit correspondre à la valeur de la `@address` attribut du frère `wsdl:port` / `wsdl:location` élément.</span><span class="sxs-lookup"><span data-stu-id="56dfb-320">R3532: If a `wsdl:port` contains a child element `<wsa10:EndpointReference …/>`, the `wsa10:EndpointReference/wsa10:Address` child element value must match the value of the `@address` attribute of the sibling `wsdl:port`/`wsdl:location` element.</span></span>  
  
-   <span data-ttu-id="56dfb-321">R3533 : si un point de terminaison possède une alternative de stratégie attachée avec une assertion de la stratégie `<wsap:UsingAddressing/>`, l'élément `wsdl:port` correspondant peut contenir un élément enfant `<wsa:EndpointReference …/>`.</span><span class="sxs-lookup"><span data-stu-id="56dfb-321">R3533: If an endpoint has an attached policy alternative with `<wsap:UsingAddressing/>` policy assertion, the corresponding `wsdl:port` element can contain a child element `<wsa:EndpointReference …/>`.</span></span>  
  
-   <span data-ttu-id="56dfb-322">R3534 : Si un `wsdl:port` contient un élément enfant `<wsa:EndpointReference …/>`, le `wsa:EndpointReference/wsa:Address` valeur de l’élément enfant doit correspondre à la valeur de la `@address` attribut du frère `wsdl:port` / `wsdl:location` élément.</span><span class="sxs-lookup"><span data-stu-id="56dfb-322">R3534: If a `wsdl:port` contains a child element `<wsa:EndpointReference …/>`, the `wsa:EndpointReference/wsa:Address` child element value must match the value of the `@address` attribute of the sibling `wsdl:port`/`wsdl:location` element.</span></span>  
  
### <a name="composition-with-ws-security"></a><span data-ttu-id="56dfb-323">Composition avec WS-Security</span><span class="sxs-lookup"><span data-stu-id="56dfb-323">Composition with WS-Security</span></span>  
 <span data-ttu-id="56dfb-324">D'après les sections relatives à la sécurité de WS-ADDR et WS-ADDR10, il est recommandé que tous les en-têtes d'adressage de messages soient signés avec le corps du message afin de les lier.</span><span class="sxs-lookup"><span data-stu-id="56dfb-324">According to security consideration sections in WS-ADDR and WS-ADDR10, all addressing message headers are recommended to be signed together with the message body to bind them together.</span></span>  
  
 <span data-ttu-id="56dfb-325">Lorsque WS-Security est utilisée pour la protection de l'intégrité des messages, les en-têtes de message WS-Addressing ainsi que les en-têtes résultant des paramètres ou des propriétés de référence (ou les deux) doivent être signés avec le corps du message.</span><span class="sxs-lookup"><span data-stu-id="56dfb-325">When WS-Security is used for message integrity protection, WS-Addressing message headers as well as headers resulted from reference parameters or properties (or both) must be signed together with the body of the message.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="56dfb-326">Exemples</span><span class="sxs-lookup"><span data-stu-id="56dfb-326">Examples</span></span>  
  
#### <a name="one-way-message"></a><span data-ttu-id="56dfb-327">Message unidirectionnel</span><span class="sxs-lookup"><span data-stu-id="56dfb-327">One-Way Message</span></span>  
 <span data-ttu-id="56dfb-328">Dans ce scénario, l'expéditeur envoie un message unidirectionnel au récepteur.</span><span class="sxs-lookup"><span data-stu-id="56dfb-328">In this scenario, the sender sends a one-way message to the receiver.</span></span> <span data-ttu-id="56dfb-329">SOAP 1.2, HTTP 1.1 et W3C WS-Addressing 1.0 sont utilisés.</span><span class="sxs-lookup"><span data-stu-id="56dfb-329">SOAP 1.2, HTTP 1.1, and W3C WS-Addressing 1.0 are used.</span></span>  
  
 <span data-ttu-id="56dfb-330">Structure du message de demande : les en-têtes de message incluent les éléments `wsa10:To` et `wsa10:Action`.</span><span class="sxs-lookup"><span data-stu-id="56dfb-330">The Request Message Structure: The message headers include `wsa10:To` and `wsa10:Action` elements.</span></span> <span data-ttu-id="56dfb-331">Le corps du message inclut un élément `<app:Ping>` spécifique de l'espace de noms de l'application.</span><span class="sxs-lookup"><span data-stu-id="56dfb-331">The message body includes a specific `<app:Ping>` element from the application namespace.</span></span>  
  
 <span data-ttu-id="56dfb-332">En-têtes HTTP : La destination dans POST correspond à l’URI dans le `wsa10:To` élément.</span><span class="sxs-lookup"><span data-stu-id="56dfb-332">HTTP Headers: The destination in POST matches the URI in the `wsa10:To` element.</span></span>  
  
 <span data-ttu-id="56dfb-333">L'en-tête Content-Type a la valeur `application/soap+xml` comme l'exige SOAP 1.2.</span><span class="sxs-lookup"><span data-stu-id="56dfb-333">The Content-Type header has the value of `application/soap+xml` as required by SOAP 1.2.</span></span> <span data-ttu-id="56dfb-334">Les paramètres `charset` et `action` sont inclus.</span><span class="sxs-lookup"><span data-stu-id="56dfb-334">Parameters `charset` and `action` are included.</span></span> <span data-ttu-id="56dfb-335">Le paramètre `action` de l'en-tête Content-Type correspond à la valeur de l'en-tête de message `wsa10:Action`.</span><span class="sxs-lookup"><span data-stu-id="56dfb-335">The `action` parameter of the Content-Type header matches the value of the `wsa10:Action` message header.</span></span>  
  
```  
POST http://fabrikam123.com/Service HTTP/1.1  
Content-Type: application/soap+xml; charset=utf-8;    
              action="http://fabrikam123.com/Service/OneWay"  
Host: 131.107.72.15  
Content-Length: 1501  
Expect: 100-continue  
Proxy-Connection: Keep-Alive  
<s12:Envelope>  
  <s12:Header>  
    <wsa10:To s12:mustUnderstand="1">  
        http://fabrikam123.com/Service  
    </wsa10:To>  
    <wsa10:Action s12:mustUnderstand="1">  
        http://fabrikam123.com/Service/OneWay   
    </wsa10:Action>  
  </s12:Header>  
  <s12:Body>  
    <Ping xmlns="http://fabrikam123.com/Service/">  
      <Text>Hello World</Text>  
    </Ping>  
  </s12:Body>  
</s12:Envelope>  
```  
  
 <span data-ttu-id="56dfb-336">Le récepteur répond avec une réponse HTTP vide et l'état 202.</span><span class="sxs-lookup"><span data-stu-id="56dfb-336">The receiver responds with an empty HTTP response and status 202.</span></span> <span data-ttu-id="56dfb-337">Exemple de réponse HTTP :</span><span class="sxs-lookup"><span data-stu-id="56dfb-337">An example of the HTTP response:</span></span>  
  
```  
HTTP/1.1 202 Accepted  
Date: Fri, 15 Jul 2005 08:56:07 GMT  
Server: Microsoft-IIS/6.0  
MicrosoftOfficeWebServer: 5.0_Pub  
X-Powered-By: ASP.NET  
X-AspNet-Version: 2.0.50215  
Cache-Control: private  
Content-Length: 0  
```  
  
## <a name="soap-message-transmission-optimization-mechanism"></a><span data-ttu-id="56dfb-338">SOAP MTOM (Message Transmission Optimization Mechanism)</span><span class="sxs-lookup"><span data-stu-id="56dfb-338">SOAP Message Transmission Optimization Mechanism</span></span>  
 <span data-ttu-id="56dfb-339">Cette section décrit les détails de l'implémentation [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] pour le protocole MTOM HTTP SOAP.</span><span class="sxs-lookup"><span data-stu-id="56dfb-339">This section describes the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] implementation details for the HTTP SOAP MTOM.</span></span> <span data-ttu-id="56dfb-340">La technologie MTOM est mécanisme d'encodage de message SOAP de la même classe que l'encodage de texte/XML traditionnel ou l'encodage binaire [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="56dfb-340">MTOM technology is SOAP message encoding mechanism of the same class as traditional text/XML encoding or [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Binary encoding.</span></span> <span data-ttu-id="56dfb-341">MTOM inclut ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="56dfb-341">MTOM includes the following:</span></span>  
  
-   <span data-ttu-id="56dfb-342">Un mécanisme d'encodage XML et d'empaquetage décrit par [XOP] qui optimise les éléments d'information XML qui contiennent les données binaires encodées en Base64 dans des parties binaires séparées.</span><span class="sxs-lookup"><span data-stu-id="56dfb-342">An XML encoding and packaging mechanism described by [XOP] that optimizes XML information items containing base64-encoded binary data into separate binary parts.</span></span>  
  
-   <span data-ttu-id="56dfb-343">Encapsulation MIME du package XOP qui sérialise l'ensemble d'informations XML et chaque partie binaire du package XOP dans une partie MIME séparée.</span><span class="sxs-lookup"><span data-stu-id="56dfb-343">A MIME encapsulation of the XOP package that serializes the XML Infoset and each binary part of the XOP package into a separate MIME part.</span></span>  
  
-   <span data-ttu-id="56dfb-344">Encodage XOP MIME appliqué à l'enveloppe SOAP 1.x.</span><span class="sxs-lookup"><span data-stu-id="56dfb-344">A MIME XOP encoding applied to SOAP 1.x Envelope.</span></span>  
  
-   <span data-ttu-id="56dfb-345">Liaison de transport HTTP.</span><span class="sxs-lookup"><span data-stu-id="56dfb-345">An HTTP transport binding.</span></span>  
  
 <span data-ttu-id="56dfb-346">Il est possible d'utiliser MTOM avec des transports non HTTP avec [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="56dfb-346">It is possible to use MTOM with non-HTTP transports with [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span> <span data-ttu-id="56dfb-347">Toutefois, nous nous concentrerons sur le HTTP dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="56dfb-347">However, in this topic we will focus on HTTP.</span></span>  
  
 <span data-ttu-id="56dfb-348">Le format MTOM tire parti d'un grand ensemble de spécifications qui couvrent MTOM lui-même, XOP et MIME.</span><span class="sxs-lookup"><span data-stu-id="56dfb-348">The MTOM format leverages a large set of specifications covering MTOM itself, XOP, and MIME.</span></span> <span data-ttu-id="56dfb-349">La modularité de cet ensemble de spécifications rend quelque peu difficile la reconstruction des spécifications exactes sur le format et le traitement de la sémantique.</span><span class="sxs-lookup"><span data-stu-id="56dfb-349">Modularity of this specification set makes it somewhat difficult to reconstruct exact requirements on the format and processing semantics.</span></span> <span data-ttu-id="56dfb-350">Cette section décrit les spécifications de format et de traitement pour la liaison HTTP MTOM.</span><span class="sxs-lookup"><span data-stu-id="56dfb-350">This section describes the format and processing requirements for MTOM HTTP binding.</span></span>  
  
### <a name="mtom-message-encoding"></a><span data-ttu-id="56dfb-351">Encodage de message MTOM</span><span class="sxs-lookup"><span data-stu-id="56dfb-351">MTOM Message Encoding</span></span>  
  
#### <a name="generating-mtom-messages"></a><span data-ttu-id="56dfb-352">Génération de messages MTOM</span><span class="sxs-lookup"><span data-stu-id="56dfb-352">Generating MTOM messages</span></span>  
 <span data-ttu-id="56dfb-353">Le [XOP] la section 3.1 décrit le processus de l'encodage XML avec des détails d'élément qui contiennent des valeurs Base64 dans un package XOP abstraitement défini.</span><span class="sxs-lookup"><span data-stu-id="56dfb-353">The [XOP] section 3.1 describes the process of encoding XML with element information items that contain base64 values into an abstractly defined XOP package.</span></span>  
  
 <span data-ttu-id="56dfb-354">La séquence d'étapes suivante décrit le processus d'encodage spécifique à MTOM :</span><span class="sxs-lookup"><span data-stu-id="56dfb-354">The following sequence of steps describes the MTOM-specific encoding process:</span></span>  
  
1.  <span data-ttu-id="56dfb-355">Vérifiez que l'enveloppe SOAP à encoder ne contient aucun élément d'information avec un `[namespace name]` de « http://www.w3.org/2004/08/xop/include » et un `[local name]` de `Include`.</span><span class="sxs-lookup"><span data-stu-id="56dfb-355">Ensure that the SOAP Envelope to be encoded contains no element information item with a `[namespace name]` of "http://www.w3.org/2004/08/xop/include" and a `[local name]` of `Include`.</span></span>  
  
2.  <span data-ttu-id="56dfb-356">Créez un package MIME vide.</span><span class="sxs-lookup"><span data-stu-id="56dfb-356">Create an empty MIME package.</span></span>  
  
3.  <span data-ttu-id="56dfb-357">Identifiez dans l'ensemble d'informations XML d'origine les éléments à optimiser.</span><span class="sxs-lookup"><span data-stu-id="56dfb-357">Identify within the Original XML Infoset the element information items to be optimized.</span></span> <span data-ttu-id="56dfb-358">Pour les éléments à optimiser, les caractères qui créent le `[children]` de l'élément d'information doivent avoir la forme canonique de `xs:base64Binary` (voir XSD-2, 3.2.16 base64Binary) et ne doivent contenir aucun espace blanc avant, dans ou après le contenu non espace blanc.</span><span class="sxs-lookup"><span data-stu-id="56dfb-358">For the items to be optimized, the characters that make up the `[children]` of the element information item must be in the canonical form of `xs:base64Binary` (see XSD-2, 3.2.16 base64Binary) and must not contain any whitespace characters preceding, inline with, or following the non-whitespace content.</span></span>  
  
4.  <span data-ttu-id="56dfb-359">Créez une enveloppe SOAP XOP qui est une copie de l'enveloppe SOAP d'origine, mais en remplaçant les enfants de chaque élément d'information identifiés à l'étape précédente par un élément d'information `xop:Include` construit comme suit :</span><span class="sxs-lookup"><span data-stu-id="56dfb-359">Create an XOP SOAP Envelope that is a copy of the Original SOAP Envelope, but with the children of each element information item identified in the previous step replaced by an `xop:Include` element information item constructed as follows:</span></span>  
  
    1.  <span data-ttu-id="56dfb-360">Transformez les caractères remplacés en données binaires en les traitant comme des données encodées en Base64.</span><span class="sxs-lookup"><span data-stu-id="56dfb-360">Transform the replaced characters into binary data by processing them as base64-encoded data.</span></span>  
  
    2.  <span data-ttu-id="56dfb-361">Générez une valeur d'en-tête Content-ID unique qui satisfait aux spécifications R3133 et R3134.</span><span class="sxs-lookup"><span data-stu-id="56dfb-361">Generate a unique Content-ID header value that satisfies requirements R3133 and R3134.</span></span>  
  
    3.  <span data-ttu-id="56dfb-362">Générez un en-tête MIME Content-Transfer-Encoding avec la valeur binaire.</span><span class="sxs-lookup"><span data-stu-id="56dfb-362">Generate a Content-Transfer-Encoding MIME header with the value binary.</span></span>  
  
    4.  <span data-ttu-id="56dfb-363">Si l'élément d'information qui est optimisé (le [parent] de l'élément d'information `xop:Include` inséré) a un élément d'information d'attribut `xmime:contentType`, générez un en-tête MIME Content-type avec la valeur de l'attribut `xmime:contentType`.</span><span class="sxs-lookup"><span data-stu-id="56dfb-363">If the element information item being optimized (the [parent] of the newly inserted `xop:Include` element information item) has an `xmime:contentType` attribute information item, generate a Content-Type MIME header with the value of the `xmime:contentType` attribute.</span></span>  
  
    5.  <span data-ttu-id="56dfb-364">Générez une nouvelle partie MIME binaire avec le contenu formé par les données binaires décodées des caractères remplacés traités en Base64, l'en-tête Content-ID de l'étape 4b, l'en-tête Content-Transfer-Encoding de l'étape 4c, l'en-tête Content-Type si généré à l'étape 4d.</span><span class="sxs-lookup"><span data-stu-id="56dfb-364">Generate a new binary MIME part with content formed by binary data decoded from the replaced characters processed as base64, Content-ID header from 4b, Content- Transfer-Encoding header from 4c, Content-Type header if generated in step 4d.</span></span>  
  
    6.  <span data-ttu-id="56dfb-365">Ajoutez un attribut `href` à l'élément `xop:Include` avec la valeur cid : l'uri dérivé de la valeur d'en-tête Content-ID générée à l'étape 4b.</span><span class="sxs-lookup"><span data-stu-id="56dfb-365">Add an `href` attribute to the `xop:Include` element with the value cid: uri derived from Content-ID header value generated in step 4b.</span></span> <span data-ttu-id="56dfb-366">Supprimer la forme «\<» et « > » caractères, d’échappement URL pour les autres chaînes de caractères et ajoutez le préfixe `cid:`.</span><span class="sxs-lookup"><span data-stu-id="56dfb-366">Remove the enclosing "\<" and ">" characters, URL-escape the remaining string, and add the prefix `cid:`.</span></span> <span data-ttu-id="56dfb-367">Le jeu de caractères minimum suivant est requis pour un échappement par RFC1738 et RFC2396.</span><span class="sxs-lookup"><span data-stu-id="56dfb-367">The following minimum character set is required to be escaped by RFC1738 and RFC2396.</span></span> <span data-ttu-id="56dfb-368">D'autres caractères peuvent faire l'objet d'une séquence d'échappement.</span><span class="sxs-lookup"><span data-stu-id="56dfb-368">Other characters can be escaped.</span></span>  
  
        ```  
        Hexadecimal 00-1F , 7F, 20, "<" | ">" | "#" | "%" | <">  
        "{" | "}" | "|" | "\" | "^" | "[" | "]" | "`" | "~" | "^"  
        ```  
  
5.  <span data-ttu-id="56dfb-369">Créez une partie MIME racine avec l'enveloppe SOAP XOP à partir de l'étape 4.</span><span class="sxs-lookup"><span data-stu-id="56dfb-369">Create a root MIME part with the XOP SOAP Envelope from step 4.</span></span>  
  
6.  <span data-ttu-id="56dfb-370">Écrivez les en-têtes HTTP, y compris l'en-tête HTTP Content-Type.</span><span class="sxs-lookup"><span data-stu-id="56dfb-370">Write the HTTP headers, including the HTTP Content-Type header.</span></span>  
  
7.  <span data-ttu-id="56dfb-371">Écrivez le package MIME.</span><span class="sxs-lookup"><span data-stu-id="56dfb-371">Write the MIME package.</span></span>  
  
#### <a name="processing-mtom-messages"></a><span data-ttu-id="56dfb-372">Traitement des messages MTOM</span><span class="sxs-lookup"><span data-stu-id="56dfb-372">Processing MTOM messages</span></span>  
 <span data-ttu-id="56dfb-373">Le traitement d'un message MTOM est l'inverse exact du processus décrit dans la section précédente « Génération de messages MTOM » :</span><span class="sxs-lookup"><span data-stu-id="56dfb-373">Processing of an MTOM message is the exact reverse of the process described in the preceding "Generating MTOM messages" section:</span></span>  
  
1.  <span data-ttu-id="56dfb-374">Vérifiez que la partie MIME racine possède le `application/xop+xml` Content-type.</span><span class="sxs-lookup"><span data-stu-id="56dfb-374">Ensure the root MIME part has the Content-Type `application/xop+xml`.</span></span>  
  
2.  <span data-ttu-id="56dfb-375">Construisez une enveloppe SOAP en analysant la partie MIME racine du package comme un document XML.</span><span class="sxs-lookup"><span data-stu-id="56dfb-375">Construct a SOAP Envelope by parsing the root MIME part of the package as an XML document.</span></span> <span data-ttu-id="56dfb-376">L'encodage de caractères est déterminé par le paramètre `charset` du Content-type de la partie MIME racine.</span><span class="sxs-lookup"><span data-stu-id="56dfb-376">Character encoding is determined by the `charset` parameter of the Content-Type of the root MIME part.</span></span>  
  
3.  <span data-ttu-id="56dfb-377">Pour chaque élément d'information dans l'enveloppe SOAP construite, qui a comme seul membre de sa propriété [enfant] un élément d'information `xop:Include` :</span><span class="sxs-lookup"><span data-stu-id="56dfb-377">For each element information item in the constructed SOAP Envelope, which has, as the sole member of its [children] property, an `xop:Include` element information item:</span></span>  
  
    1.  <span data-ttu-id="56dfb-378">Supprimez le préfixe `cid:` préfixent et annulez toutes les séquences d'échappement d'URI (RFC 2396) dans la valeur de l'attribut `@href` de l'élément `xop:Include`.</span><span class="sxs-lookup"><span data-stu-id="56dfb-378">Remove the `cid:` prefix and unescape all URI-escape sequences (RFC 2396) in the value of the `@href` attribute of the `xop:Include` element.</span></span> <span data-ttu-id="56dfb-379">Placez la chaîne de résultat «\<», « > ».</span><span class="sxs-lookup"><span data-stu-id="56dfb-379">Enclose the result string in "\<", ">".</span></span>  
  
    2.  <span data-ttu-id="56dfb-380">Localisez la partie MIME avec la valeur d'en-tête Content-ID qui correspond à la chaîne dérivée à l'étape 3a.</span><span class="sxs-lookup"><span data-stu-id="56dfb-380">Locate the MIME part with the Content-ID header value that matches the string derived in step 3a.</span></span>  
  
    3.  <span data-ttu-id="56dfb-381">Remplacez l'élément d'information `xop:Include` qui apparaît dans la propriété `children` de chaque élément par les éléments d'information de caractère qui représentent l'encodage Base64 canonique (voir XSD-2, 3.2.16 base64Binary) du corps d'entité de la partie MIME identifiée à l'étape 3b (remplacez l'élément d'information `xop:Include` par les données reconstruites à partir de la partie du package).</span><span class="sxs-lookup"><span data-stu-id="56dfb-381">Replace the `xop:Include` element information item that appears in the `children` property of each item with the character information items that represent the canonical base64 encoding (see XSD-2, 3.2.16 base64Binary) of the entity body of the MIME part identified in step 3b (effectively replace the `xop:Include` element information item with the data reconstructed from the package part).</span></span>  
  
#### <a name="http-content-type-header"></a><span data-ttu-id="56dfb-382">En-tête HTTP Content-Type</span><span class="sxs-lookup"><span data-stu-id="56dfb-382">HTTP Content-Type Header</span></span>  
 <span data-ttu-id="56dfb-383">Voici une liste d'éclaircissements [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] pour le format de l'en-tête HTTP Content-Type d'un message SOAP 1.x encodé en MTOM dérivé des spécifications déclarées dans la spécification MTOM elle-même et qui sont dérivés de MTOM et RFC 2387.</span><span class="sxs-lookup"><span data-stu-id="56dfb-383">The following is a list of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] clarifications for the format of the HTTP Content-Type header of a SOAP 1.x MTOM-encoded message derived from requirements stated in the MTOM specification itself and are derived from MTOM and RFC 2387.</span></span>  
  
-   <span data-ttu-id="56dfb-384">R4131 : un en-tête HTTP Content-Type doit avoir la valeur de multipart/related (non sensible à la casse) et ses paramètres.</span><span class="sxs-lookup"><span data-stu-id="56dfb-384">R4131: An HTTP Content-Type header must have the value of multipart/related (case-insensitive) and its parameters.</span></span> <span data-ttu-id="56dfb-385">Les noms des paramètres ne respectent pas la casse.</span><span class="sxs-lookup"><span data-stu-id="56dfb-385">Parameter names are case-insensitive.</span></span> <span data-ttu-id="56dfb-386">L'ordre des paramètres n'est pas important.</span><span class="sxs-lookup"><span data-stu-id="56dfb-386">Parameter order is not significant.</span></span>  
  
-   <span data-ttu-id="56dfb-387">La forme Backus-Naur (BNF) complète de l'en-tête Content-Type pour les messages MIME est répertoriée dans RFC 2045, section 5.1.</span><span class="sxs-lookup"><span data-stu-id="56dfb-387">The full Backus-Naur Form (BNF) of the Content-Type header for MIME messages is listed in RFC 2045, section 5.1.</span></span>  
  
-   <span data-ttu-id="56dfb-388">R4132 : un en-tête Content-Type HTTP doit avoir un paramètre de type avec la valeur `application/xop+xml` comprise entre des guillemets doubles.</span><span class="sxs-lookup"><span data-stu-id="56dfb-388">R4132: An HTTP Content-Type header must have a type parameter with the value `application/xop+xml` enclosed in double quotation marks.</span></span>  
  
 <span data-ttu-id="56dfb-389">Alors que la nécessité d’utiliser des guillemets doubles n’est pas explicite dans RFC 2387, le texte observe que du type média multipart/related contiennent des paramètres plus probables pour les caractères réservés comme «@" or "/ » de sorte que vous avez besoin des guillemets doubles.</span><span class="sxs-lookup"><span data-stu-id="56dfb-389">While the requirement to use double quotation marks is not explicit in RFC 2387, the text observes that all of the multipart/related media type parameters most likely contain reserved characters like "@" or "/" and therefore need double quotation marks.</span></span>  
  
-   <span data-ttu-id="56dfb-390">R4133 : un en-tête HTTP Content-Type doit avoir un paramètre de début avec la valeur de l'en-tête Content-ID de la partie MIME qui contient l'enveloppe SOAP 1.x, entourée de guillemets doubles.</span><span class="sxs-lookup"><span data-stu-id="56dfb-390">R4133: An HTTP Content-Type header should have a start parameter with the value of the Content-ID header of the MIME part that contains the SOAP 1.x Envelope, enclosed in double quotation marks.</span></span> <span data-ttu-id="56dfb-391">Si le paramètre de début est omis, la première partie MIME doit contenir l'enveloppe SOAP 1.x.</span><span class="sxs-lookup"><span data-stu-id="56dfb-391">If the start parameter is omitted, the first MIME part must contain the SOAP 1.x Envelope.</span></span>  
  
-   <span data-ttu-id="56dfb-392">R4134 : un en-tête HTTP Content-Type pour un message SOAP 1.1 encodé en MTOM doit inclure le paramètre start-info avec la valeur de texte/xml, entouré par des guillemets doubles.</span><span class="sxs-lookup"><span data-stu-id="56dfb-392">R4134: An HTTP Content-Type header for a SOAP 1.1 MTOM encoded message must include the start-info parameter with the value of text/xml, enclosed in double quotation marks.</span></span>  
  
-   <span data-ttu-id="56dfb-393">R4135 : un en-tête Content-Type HTTP pour un message SOAP 1.2 encodé en MTOM doit inclure le paramètre start-info avec la valeur de `application/soap+xml`, entre des guillemets doubles.</span><span class="sxs-lookup"><span data-stu-id="56dfb-393">R4135: An HTTP Content-Type header for a SOAP 1.2 MTOM-encoded message must include the start-info parameter with the value of `application/soap+xml`, enclosed in double quotation marks.</span></span>  
  
-   <span data-ttu-id="56dfb-394">R4136 : l'en-tête HTTP Content-Type d'un message SOAP 1.x encodé en MTOM doit avoir le paramètre de limite avec la valeur (entourée par des guillemets doubles) qui correspond au BNF de limite MIME défini dans RFC 2046, section 5.1.1</span><span class="sxs-lookup"><span data-stu-id="56dfb-394">R4136: HTTP Content-Type header for a SOAP 1.x MTOM-encoded message must have the boundary parameter with the value (enclosed in double quotation marks) that matches the MIME boundary BNF defined in RFC 2046, section 5.1.1</span></span>  
  
    ```  
    boundary := 0*69<bchars> bcharsnospace   
    bchars := bcharsnospace / " "   
    bcharsnospace :=    DIGIT / ALPHA / "'" / "(" / ")" / "+"   
                        / "_" / "," / "-" / "." / "/" / ":" / "=" / "?"  
    ```  
  
     <span data-ttu-id="56dfb-395">Exemples :</span><span class="sxs-lookup"><span data-stu-id="56dfb-395">Examples:</span></span>  
  
     <span data-ttu-id="56dfb-396">CORRECT</span><span class="sxs-lookup"><span data-stu-id="56dfb-396">CORRECT</span></span>  
  
    ```  
    Content-Type: multipart/related; type="application/xop+xml";start=" <part0@tempuri.org>";boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1";start-info="text/xml"  
    ```  
  
     <span data-ttu-id="56dfb-397">CORRECT</span><span class="sxs-lookup"><span data-stu-id="56dfb-397">CORRECT</span></span>  
  
    ```  
    Content-Type: Multipart/Related; type="application/xop+xml";start-info="text/xml";boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1"  
    ```  
  
     <span data-ttu-id="56dfb-398">INCORRECT</span><span class="sxs-lookup"><span data-stu-id="56dfb-398">INCORRECT</span></span>  
  
    ```  
    Content-Type: Multipart/Related; type=application/xop+xml;start=" <part0@tempuri.org>";start-info="text/xml";boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1"   
    ```  
  
#### <a name="infoset-mime-part"></a><span data-ttu-id="56dfb-399">Partie MIME d'ensemble d'informations</span><span class="sxs-lookup"><span data-stu-id="56dfb-399">Infoset MIME Part</span></span>  
 <span data-ttu-id="56dfb-400">L'enveloppe SOAP 1.x est encapsulée comme une partie racine du package MIME XOP et est souvent appelée la partie `infoset`.</span><span class="sxs-lookup"><span data-stu-id="56dfb-400">The SOAP 1.x Envelope is encapsulated as a root part of the XOP MIME package and is often called the `infoset` part.</span></span>  
  
-   <span data-ttu-id="56dfb-401">R4141 : l'enveloppe SOAP 1.x doit être encapsulée comme une partie racine du package MIME XOP, appelée la partie `infoset` et référencée depuis le Content-Type HTTP.</span><span class="sxs-lookup"><span data-stu-id="56dfb-401">R4141: The SOAP 1.x Envelope must be encapsulated as a root part of the XOP MIME package, called the `infoset` part and referenced from the HTTP Content-Type.</span></span>  
  
-   <span data-ttu-id="56dfb-402">R4142 : la partie SOAP `Infoset` doit inclure les en-têtes MIME suivants : `Content-ID`, `Content-Transfer-Encoding` et `Content-Type`.</span><span class="sxs-lookup"><span data-stu-id="56dfb-402">R4142: The SOAP `Infoset` part must include the following MIME headers: `Content-ID`, `Content-Transfer-Encoding`, and `Content-Type`.</span></span>  
  
 <span data-ttu-id="56dfb-403">Le format de l'en-tête Content-ID est défini par RFC 2045 comme</span><span class="sxs-lookup"><span data-stu-id="56dfb-403">The format of the Content-ID header is defined by RFC 2045 as</span></span>  
  
```  
"Content-ID" ":" msg-id  
```  
  
 <span data-ttu-id="56dfb-404">où `msg-id` est défini dans RFC 2822 (remplace RFC 822, référencé dans RFC 2045) comme :</span><span class="sxs-lookup"><span data-stu-id="56dfb-404">where `msg-id` is defined in RFC 2822 (that supersedes RFC 822, referenced in RFC 2045) as:</span></span>  
  
```  
msg-id    =       [CFWS] "<" id-left "@" id-right ">" [CFWS]  
```  
  
 <span data-ttu-id="56dfb-405">et est effectivement une adresse de messagerie entre «\<» et « > ».</span><span class="sxs-lookup"><span data-stu-id="56dfb-405">and is effectively an e-mail address enclosed within "\<" and  ">".</span></span> <span data-ttu-id="56dfb-406">Les préfixe et suffixe `[CFWS]` ont été ajoutés dans RFC 2822 pour contenir des commentaires et ne doivent pas être utilisés pour préserver l'interopérabilité.</span><span class="sxs-lookup"><span data-stu-id="56dfb-406">The `[CFWS]` prefix and suffix were added in RFC 2822 to carry comments and should not be used to preserve interoperability.</span></span>  
  
 <span data-ttu-id="56dfb-407">R4143 : la valeur de l'en-tête Content-ID pour la partie MIME de l'ensemble d'informations doit suivre la production `msg-id` de RFC 2822 avec les parties `[CFWS]` préfixe et suffixe omises.</span><span class="sxs-lookup"><span data-stu-id="56dfb-407">R4143: The value of the Content-ID header for the Infoset MIME part must follow `msg-id` production from RFC 2822 with the `[CFWS]` prefix and suffix parts omitted.</span></span>  
  
 <span data-ttu-id="56dfb-408">Un plusieurs implémentations MIME ont assoupli des exigences pour la valeur entre »\<» et « > » soit une adresse de messagerie et utilisé `absoluteURI` placé entre »\<», « > » en plus de l’adresse de messagerie.</span><span class="sxs-lookup"><span data-stu-id="56dfb-408">A number of MIME implementations relaxed requirements for the value enclosed within "\<" and ">" to be an e-mail address and used `absoluteURI` enclosed in "\<" , ">" in addition to the e-mail address.</span></span> <span data-ttu-id="56dfb-409">Cette version de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] utilise les valeurs de l'en-tête MIME Content-ID de la forme :</span><span class="sxs-lookup"><span data-stu-id="56dfb-409">This version of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uses values of the Content-ID MIME header of the form:</span></span>  
  
```  
Content-ID: <http://tempuri.org/0>   
```  
  
 <span data-ttu-id="56dfb-410">R4144 : les processeurs MTOM doivent accepter les valeurs d'en-tête Content-ID qui correspondent au `msg-id` assoupli suivant.</span><span class="sxs-lookup"><span data-stu-id="56dfb-410">R4144: MTOM processors should accept Content-ID header values that match the following relaxed `msg-id`.</span></span>  
  
```  
msg-id-relaxed =     [CFWS] "<" (absoluteURI | mail-address) ">" [CFWS]  
mail-address   =     id-left "@" id-right  
```  
  
 <span data-ttu-id="56dfb-411">MIME (RFC 2045) fournit l'en-tête Content-Transfer-Encoding pour communiquer l'encodage du contenu de la partie MIME.</span><span class="sxs-lookup"><span data-stu-id="56dfb-411">MIME (RFC 2045) provides the Content-Transfer-Encoding header to communicate encoding of the content of the MIME part.</span></span> <span data-ttu-id="56dfb-412">La valeur par défaut définie pour Content-Transfer-Encoding est de 7 bits, ce qui ne convient pas à la plupart des messages SOAP ; l'en-tête Content-Transfer-Encoding est donc nécessaire pour une plus grande interopérabilité :</span><span class="sxs-lookup"><span data-stu-id="56dfb-412">The default defined for Content-Transfer-Encoding is 7-bit, which is not suitable for most SOAP messages, so the Content-Transfer-Encoding header is needed for greater interoperability:</span></span>  
  
-   <span data-ttu-id="56dfb-413">R4145 : la partie de l'ensemble d'informations SOAP doit contenir l'en-tête Content-Transfer-Encoding.</span><span class="sxs-lookup"><span data-stu-id="56dfb-413">R4145: The SOAP Infoset part must contain the Content-Transfer-Encoding header.</span></span>  
  
-   <span data-ttu-id="56dfb-414">R4146 : si l'encodage de caractères de l'enveloppe SOAP est UTF-8, la valeur de l'en-tête Content-Transfer-Encoding doit être de 8 bits.</span><span class="sxs-lookup"><span data-stu-id="56dfb-414">R4146: If the SOAP Envelope character encoding is UTF-8, the value of the Content-Transfer-Encoding header must be 8-bit.</span></span>  
  
-   <span data-ttu-id="56dfb-415">R4147 : si l'encodage de caractères de l'enveloppe SOAP est UTF-16, la valeur de l'en-tête Content-Transfer-Encoding doit être binaire.</span><span class="sxs-lookup"><span data-stu-id="56dfb-415">R4147: If the SOAP Envelope character encoding is UTF-16, the value of the Content-Transfer-Encoding header must be binary.</span></span>  
  
-   <span data-ttu-id="56dfb-416">D'après [XOP] section 5,</span><span class="sxs-lookup"><span data-stu-id="56dfb-416">According to [XOP] section 5,</span></span>  
  
-   <span data-ttu-id="56dfb-417">R4148 : SOAP 1.1 Infoset partie doit contenir l’en-tête Content-Type avec le type de média application/xop + xml et les paramètres de type = « texte/xml » et le jeu de caractères</span><span class="sxs-lookup"><span data-stu-id="56dfb-417">R4148: SOAP1.1 Infoset part must contain Content-Type header with media type application/xop+xml and parameters type="text/xml" and charset</span></span>  
  
    ```  
    Content-Type: application/xop+xml;  
                  charset=utf-8;type="text/xml"  
    ```  
  
-   <span data-ttu-id="56dfb-418">R4149 : La partie de l’ensemble d’informations SOAP 1.2 doit contenir l’en-tête Content-Type avec le type de média `application/xop+xml` et paramètres de type = «`application/soap+xml`» et `charset`.</span><span class="sxs-lookup"><span data-stu-id="56dfb-418">R4149: The SOAP 1.2 Infoset part must contain the Content-Type header with media type `application/xop+xml` and parameters type="`application/soap+xml`" and `charset`.</span></span>  
  
    ```  
    Content-Type: application/xop+xml;  
                  charset=utf-8;type="application/soap+xml"  
    ```  
  
     <span data-ttu-id="56dfb-419">Bien que XOP définisse le paramètre `charset` de manière à ce que `application/xop+xml` soit facultatif, il est exigé pour l'interopérabilité comme la spécification BP 1.1 sur le paramètre `charset` pour le type de média `text/xml`.</span><span class="sxs-lookup"><span data-stu-id="56dfb-419">While XOP defines the `charset` parameter for `application/xop+xml` to be optional, it is needed for interoperability similar to the BP 1.1 requirement on the `charset` parameter for the `text/xml` media type.</span></span>  
  
-   <span data-ttu-id="56dfb-420">R41410 : Les paramètres `type` et `charset` doivent être présents dans l'en-tête Content-Type de la partie de l'ensemble d'informations SOAP 1.x.</span><span class="sxs-lookup"><span data-stu-id="56dfb-420">R41410: The `type` and `charset` parameters must be present on the Content-Type header of the SOAP 1.x Infoset part.</span></span>  
  
#### <a name="wcf-endpoint-support-for-mtom"></a><span data-ttu-id="56dfb-421">Prise en charge des points de terminaison WCF pour MTOM</span><span class="sxs-lookup"><span data-stu-id="56dfb-421">WCF Endpoint Support for MTOM</span></span>  
 <span data-ttu-id="56dfb-422">L'objectif de MTOM est d'encoder un message SOAP pour optimiser les données encodées en Base64.</span><span class="sxs-lookup"><span data-stu-id="56dfb-422">The purpose of MTOM is to encode a SOAP message to optimize base64-encoded data.</span></span> <span data-ttu-id="56dfb-423">Les contraintes sont répertoriées dans la liste suivante :</span><span class="sxs-lookup"><span data-stu-id="56dfb-423">The following is a list of constraints:</span></span>  
  
-   <span data-ttu-id="56dfb-424">R4151 : tout élément d'information qui contient des données encodées en Base64 peut être optimisé.</span><span class="sxs-lookup"><span data-stu-id="56dfb-424">R4151: Any element information item that contains base64-encoded data may be optimized.</span></span>  
  
-   <span data-ttu-id="56dfb-425">B4152 : [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] optimise les éléments d'information qui contiennent des données encodées en Base64 et dépassent 1024 octets.</span><span class="sxs-lookup"><span data-stu-id="56dfb-425">B4152: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] optimizes element information items that contain base64-encoded data and exceed 1024 bytes in length.</span></span>  
  
 <span data-ttu-id="56dfb-426">Un point de terminaison [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] configuré pour utiliser MTOM enverra toujours des messages encodés en MTOM.</span><span class="sxs-lookup"><span data-stu-id="56dfb-426">A [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] endpoint configured to use MTOM will always send MTOM-encoded messages.</span></span> <span data-ttu-id="56dfb-427">Même si aucune partie ne répond aux critères requis, le message est tout de même encodé en MTOM (sérialisé comme un package MIME avec une partie MIME unique qui contient l'enveloppe SOAP).</span><span class="sxs-lookup"><span data-stu-id="56dfb-427">Even if no parts meet the required criteria, the message is still MTOM-encoded (serialized as a MIME package with a single MIME part containing the SOAP envelope).</span></span>  
  
### <a name="ws-policy-assertion-for-mtom"></a><span data-ttu-id="56dfb-428">Assertion de WS-Policy pour MTOM</span><span class="sxs-lookup"><span data-stu-id="56dfb-428">WS-Policy Assertion for MTOM</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="56dfb-429"> utilise l'assertion de stratégie suivante pour indiquer l'utilisation MTOM par point de terminaison :</span><span class="sxs-lookup"><span data-stu-id="56dfb-429"> uses the following policy assertion to indicate MTOM usage by endpoint:</span></span>  
  
```xml  
<wsoma:OptimizedMimeSerialization ... />  
```  
  
-   <span data-ttu-id="56dfb-430">R4211 : l'assertion de stratégie précédente a un objet de stratégie de point de terminaison et spécifie que tous les messages envoyés et reçus depuis le point de terminaison doivent être optimisés à l'aide de MTOM.</span><span class="sxs-lookup"><span data-stu-id="56dfb-430">R4211: The preceding policy assertion has an Endpoint Policy Subject and specifies that all messages sent to and received from the endpoint must be optimized using MTOM.</span></span>  
  
-   <span data-ttu-id="56dfb-431">B4212 : en cas de configuration pour utiliser l'optimisation MTOM, un point de terminaison [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ajoute une assertion de stratégie MTOM à la stratégie jointe à la `wsdl:binding` correspondante.</span><span class="sxs-lookup"><span data-stu-id="56dfb-431">B4212: When configured to use MTOM optimization, an [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] endpoint adds an MTOM Policy assertion to the policy attached to the corresponding `wsdl:binding`.</span></span>  
  
### <a name="composition-with-ws-security"></a><span data-ttu-id="56dfb-432">Composition avec WS-Security</span><span class="sxs-lookup"><span data-stu-id="56dfb-432">Composition with WS-Security</span></span>  
 <span data-ttu-id="56dfb-433">MTOM est un mécanisme d'encodage qui est semblable à `text/xml` et [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] XML binaire.</span><span class="sxs-lookup"><span data-stu-id="56dfb-433">MTOM is an encoding mechanism that is similar to `text/xml` and [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Binary XML.</span></span> <span data-ttu-id="56dfb-434">MTOM offre la composition naturelle avec WS-Security et d'autre protocoles WS-* : un message sécurisé à l'aide de WS-Security peut être optimisé à l'aide de MTOM.</span><span class="sxs-lookup"><span data-stu-id="56dfb-434">MTOM offers natural composition with WS-Security and other WS-* protocols: a message secured using WS-Security can be optimized using MTOM.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="56dfb-435">Exemples</span><span class="sxs-lookup"><span data-stu-id="56dfb-435">Examples</span></span>  
  
#### <a name="wcf-soap-11-message-encoded-using-mtom"></a><span data-ttu-id="56dfb-436">Message SOAP 1.1 WCF encodé à l'aide de MTOM</span><span class="sxs-lookup"><span data-stu-id="56dfb-436">WCF SOAP 1.1 Message Encoded Using MTOM</span></span>  
  
```  
POST http://131.107.72.15/Mtom/svc/service.svc/Soap11MtomUTF8 HTTP/1.1  
SOAPAction: "http://xmlsoap.org/echoBinaryAsString"  
Content-Type: multipart/related;type="application/xop+xml";  
              start="<http://tempuri.org/0>";start-info="text/xml";  
       boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1"  
Host: 131.107.72.15  
Content-Length: 1501  
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1  
Content-ID: <http://tempuri.org/0>  
Content-Transfer-Encoding: 8bit  
Content-Type: application/xop+xml;charset=utf-8;type="text/xml"  
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">  
  <s:Body>  
    <EchoBinaryAsString xmlns="http://xmlsoap.org/Ping">  
      <array>  
        <xop:Include   
         href="cid:http%3A%2F%2Ftempuri.org%2F1%2F632618206521093670"   
         xmlns:xop="http://www.w3.org/2004/08/xop/include"/>  
      </array>  
    </EchoBinaryAsString>  
  </s:Body>  
</s:Envelope>  
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1  
Content-ID: <http://tempuri.org/1/632618206521093670>  
Content-Transfer-Encoding: binary  
Content-Type: application/octet-stream  
…Binary Content..  
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1  
```  
  
#### <a name="wcf-secure-soap-12-message-encoded-using-mtom"></a><span data-ttu-id="56dfb-437">Message sécurisé SOAP 1.2 WCF encodé à l'aide de MTOM</span><span class="sxs-lookup"><span data-stu-id="56dfb-437">WCF Secure SOAP 1.2 Message Encoded Using MTOM</span></span>  
 <span data-ttu-id="56dfb-438">Dans cet exemple, un message est encodé à l'aide de MTOM et SOAP 1.2 et protégé à l'aide de WS-Security.</span><span class="sxs-lookup"><span data-stu-id="56dfb-438">In this example, a message is encoded using MTOM and SOAP 1.2 that is protected using WS-Security.</span></span> <span data-ttu-id="56dfb-439">Les parties binaires identifiées pour l'encodage sont les contenus du `BinarySecurityToken`, `CipherValue` des `EncryptedData` correspondant à la signature chiffrée et au corps chiffré.</span><span class="sxs-lookup"><span data-stu-id="56dfb-439">The binary parts identified for encoding are the contents of the `BinarySecurityToken`, `CipherValue` of the `EncryptedData` corresponding to the encrypted signature and encrypted body.</span></span> <span data-ttu-id="56dfb-440">Notez que la `CipherValue` de la `EncryptedKey` n'a pas été identifiée pour l'optimisation par [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], parce que sa longueur est inférieure à 1024 octets.</span><span class="sxs-lookup"><span data-stu-id="56dfb-440">Note that the `CipherValue` of the `EncryptedKey` was not identified for optimization by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], because its length is less then 1024 bytes.</span></span>  
  
```  
POST http://131.107.72.15/Mtom/service.svc/Soap12MtomSecureSignEncrypt HTTP/1.1  
Content-Type: multipart/related; type="application/xop+xml";  
              start="<http://tempuri.org/0>";  
            boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=3";  
              start-info="application/soap+xml";   
              action="http://xmlsoap.org/echoBinaryAsString"  
Host: 131.107.72.15  
Content-Length: 1941  
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=3  
Content-ID: <http://tempuri.org/0>  
Content-Transfer-Encoding: 8bit  
Content-Type: application/xop+xml;charset=utf-8;type="application/soap+xml"  
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/" xmlns:u="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">  
  <s:Header>  
    <o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">  
      <u:Timestamp u:Id="uuid-4d4ee765-5717-4d53-9ac9-99bddc07df6c-5">  
        <u:Created>2005-09-09T06:57:32.488Z</u:Created>  
        <u:Expires>2005-09-09T07:02:32.488Z</u:Expires>  
      </u:Timestamp>  
      <o:BinarySecurityToken u:Id="uuid-4d4ee765-5717-4d53-9ac9-99bddc07df6c-2" ValueType="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-x509-token-profile-1.0#X509v3" EncodingType="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0#Base64Binary">  
        <xop:Include href="cid:http%3A%2F%2Ftempuri.org%2F1%2F632618206525089430" xmlns:xop="http://www.w3.org/2004/08/xop/include"/>  
      </o:BinarySecurityToken>  
      <e:EncryptedKey Id="_1" xmlns:e="http://www.w3.org/2001/04/xmlenc#">  
        <e:EncryptionMethod Algorithm="http://www.w3.org/2001/04/xmlenc#rsa-oaep-mgf1p"/>  
        <KeyInfo xmlns="http://www.w3.org/2000/09/xmldsig#">  
          <o:SecurityTokenReference>  
            <o:KeyIdentifier ValueType="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-x509-token-profile-1.0#X509SubjectKeyIdentifier">Xeg55vRyK3ZhAEhEf+YT0z986L0=</o:KeyIdentifier>  
          </o:SecurityTokenReference>  
        </KeyInfo>  
        <e:CipherData>          <e:CipherValue>oQfpxwT8/SAGyZQzKE2b4yO6dXuQj7pwJ+5CGL3Rf7C06bQ5ttMoQ9GLJcQYkXTzin+WwHEgs5bj5ml9HKTW9QAU5JJ6lksdymmQvWP5ZtGPBVchO4sofEGoCKmBiZL/DYS/cnbzgnc/3a6NYnc10y2fWGaGLiqa00zijAw7o0Y=</e:CipherValue>  
        </e:CipherData>  
      </e:EncryptedKey>  
      <c:DerivedKeyToken u:Id="_2" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc">  
        <o:SecurityTokenReference>  
          <o:Reference URI="#_1"/>  
        </o:SecurityTokenReference>  
        <c:Nonce>OrEPRX7fISIS4sXYWPMv3g==</c:Nonce>  
      </c:DerivedKeyToken>  
      <e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#">  
        <e:DataReference URI="#_3"/>  
        <e:DataReference URI="#_4"/>  
      </e:ReferenceList>  
      <e:EncryptedData Id="_4" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#">  
        <e:EncryptionMethod Algorithm="http://www.w3.org/2001/04/xmlenc#aes256-cbc"/>  
        <KeyInfo xmlns="http://www.w3.org/2000/09/xmldsig#">  
          <o:SecurityTokenReference>  
            <o:Reference URI="#_2"/>  
          </o:SecurityTokenReference>  
        </KeyInfo>  
        <e:CipherData>  
          <e:CipherValue>  
            <xop:Include href="cid:http%3A%2F%2Ftempuri.org%2F2%2F632618206525089430" xmlns:xop="http://www.w3.org/2004/08/xop/include"/>  
          </e:CipherValue>  
        </e:CipherData>  
      </e:EncryptedData>  
    </o:Security>  
  </s:Header>  
  <s:Body u:Id="_0">  
    <e:EncryptedData Id="_3" Type="http://www.w3.org/2001/04/xmlenc#Content" xmlns:e="http://www.w3.org/2001/04/xmlenc#">  
      <e:EncryptionMethod Algorithm="http://www.w3.org/2001/04/xmlenc#aes256-cbc"/>  
      <KeyInfo xmlns="http://www.w3.org/2000/09/xmldsig#">  
        <o:SecurityTokenReference xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">  
          <o:Reference URI="#_2"/>  
        </o:SecurityTokenReference>  
      </KeyInfo>  
      <e:CipherData>  
        <e:CipherValue>  
          <xop:Include href="cid:http%3A%2F%2Ftempuri.org%2F3%2F632618206525089430" xmlns:xop="http://www.w3.org/2004/08/xop/include"/>  
        </e:CipherValue>  
      </e:CipherData>  
    </e:EncryptedData>  
  </s:Body>  
</s:Envelope>  
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=3  
Content-ID: <http://tempuri.org/1/632618206525089430>  
Content-Transfer-Encoding: binary  
Content-Type: application/octet-stream  
...Binary content of BinarySecurityToken - X509 Certificate...  
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=3  
Content-ID: <http://tempuri.org/2/632618206525089430>  
Content-Transfer-Encoding: binary  
Content-Type: application/octet-stream  
...Binary serialization of the encrypted primary signature...  
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=3  
Content-ID: <http://tempuri.org/3/632618206525089430>  
Content-Transfer-Encoding: binary  
Content-Type: application/octet-stream  
...Binary serialization of the encrypted Body...  
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=3--  
```
