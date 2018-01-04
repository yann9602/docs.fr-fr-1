---
title: Protocoles de transaction version 1.0
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 034679af-0002-402e-98a8-ef73dcd71bb6
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e616f989416fcee77caa9b9a5d87cfa6812eab32
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="transaction-protocols-version-10"></a><span data-ttu-id="ccb90-102">Protocoles de transaction version 1.0</span><span class="sxs-lookup"><span data-stu-id="ccb90-102">Transaction Protocols version 1.0</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="ccb90-103"> version 1 implémente la version 1.0 des protocoles WS-Atomic Transaction et WS-Coordination.</span><span class="sxs-lookup"><span data-stu-id="ccb90-103"> version 1 implements version 1.0 of the WS-Atomic Transaction and WS-Coordination protocols.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="ccb90-104">la version 1.1, consultez [protocoles de Transaction](../../../../docs/framework/wcf/feature-details/transaction-protocols.md).</span><span class="sxs-lookup"><span data-stu-id="ccb90-104"> version 1.1, see [Transaction Protocols](../../../../docs/framework/wcf/feature-details/transaction-protocols.md).</span></span>  
  
|<span data-ttu-id="ccb90-105">Spécification/Document</span><span class="sxs-lookup"><span data-stu-id="ccb90-105">Specification/Document</span></span>|<span data-ttu-id="ccb90-106">Link</span><span class="sxs-lookup"><span data-stu-id="ccb90-106">Link</span></span>|  
|-----------------------------|----------|  
|<span data-ttu-id="ccb90-107">WS-Coordination</span><span class="sxs-lookup"><span data-stu-id="ccb90-107">WS-Coordination</span></span>|<span data-ttu-id="ccb90-108">http://msdn.microsoft.com/ws/2005/08/ws-coordination/</span><span class="sxs-lookup"><span data-stu-id="ccb90-108">http://msdn.microsoft.com/ws/2005/08/ws-coordination/</span></span>|  
|<span data-ttu-id="ccb90-109">WS-AtomicTransaction</span><span class="sxs-lookup"><span data-stu-id="ccb90-109">WS-AtomicTransaction</span></span>|<span data-ttu-id="ccb90-110">http://msdn.microsoft.com/ws/2005/08/ws-atomictransaction/</span><span class="sxs-lookup"><span data-stu-id="ccb90-110">http://msdn.microsoft.com/ws/2005/08/ws-atomictransaction/</span></span>|  
  
 <span data-ttu-id="ccb90-111">L'interopérabilité sur ces spécifications de protocole est requise à deux niveaux : entre les applications et entre les gestionnaires de transactions (consultez la figure suivante).</span><span class="sxs-lookup"><span data-stu-id="ccb90-111">Interoperability on these protocol specifications is required at two levels: between applications and between transaction managers (see the following figure).</span></span> <span data-ttu-id="ccb90-112">Les spécifications décrivent de manière très détaillée les formats de message et l'échange de messages pour les deux niveaux d'interopérabilité.</span><span class="sxs-lookup"><span data-stu-id="ccb90-112">Specifications describe in great detail the message formats and message exchange for both interoperability levels.</span></span> <span data-ttu-id="ccb90-113">Une certain niveau de sécurité, de fiabilité et des encodages pour l'échange interapplication s'appliquent de la même manière que pour l'échange entre applications normal.</span><span class="sxs-lookup"><span data-stu-id="ccb90-113">Certain security, reliability, and encodings for application-to-application exchange apply as they do for regular application exchange.</span></span> <span data-ttu-id="ccb90-114">Toutefois, l'interopérabilité réussie entre les gestionnaires de transactions requiert un contrat sur la liaison spécifique, car il n'est généralement pas configuré par l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="ccb90-114">However, successful interoperability between transaction managers requires agreement on the particular binding, because it is usually not configured by the user.</span></span>  
  
 <span data-ttu-id="ccb90-115">Cette rubrique décrit une composition de la spécification WS-AT (WS-Atomic Transaction) avec sécurité et décrit la liaison sécurisée utilisée pour la communication entre les gestionnaires de transactions.</span><span class="sxs-lookup"><span data-stu-id="ccb90-115">This topic describes a composition of the WS-Atomic Transaction (WS-AT) specification with security and describes the secure binding used for communication between transaction managers.</span></span> <span data-ttu-id="ccb90-116">L'approche décrite dans ce document a été testée avec succès avec d'autres implémentations de WS-AT et WS-Coordination, dont IBM, IONA, Sun Microsystems, etc.</span><span class="sxs-lookup"><span data-stu-id="ccb90-116">The approach described in this document has been successfully tested with other implementations of WS-AT and WS-Coordination including IBM, IONA, Sun Microsystems, and others.</span></span>  
  
 <span data-ttu-id="ccb90-117">La figure suivante représente l’interopérabilité entre deux gestionnaires de transactions (Gestionnaire de transactions 1 et Gestionnaire de transactions 2) et deux applications (Application 1 et Application 2).</span><span class="sxs-lookup"><span data-stu-id="ccb90-117">The following figure depicts the interoperability between two transaction managers, Transaction Manager 1 and Transaction Manager 2, and two applications, Application 1 and Application 2.</span></span>  
  
 <span data-ttu-id="ccb90-118">![Protocoles de transaction](../../../../docs/framework/wcf/feature-details/media/transactionmanagers.gif "TransactionManagers")</span><span class="sxs-lookup"><span data-stu-id="ccb90-118">![Transaction Protocols](../../../../docs/framework/wcf/feature-details/media/transactionmanagers.gif "TransactionManagers")</span></span>  
  
 <span data-ttu-id="ccb90-119">Examinons un scénario WS-Coordination/WS-Atomic Transaction classique avec un Initiateur (I) et un Participant (P).</span><span class="sxs-lookup"><span data-stu-id="ccb90-119">Consider a typical WS-Coordination/WS-Atomic Transaction scenario with one Initiator (I) and one Participant (P).</span></span> <span data-ttu-id="ccb90-120">L’Initiateur et le Participant ont des Gestionnaires de transactions (ITM et PTM, respectivement).</span><span class="sxs-lookup"><span data-stu-id="ccb90-120">Both Initiator and Participant have Transaction Managers, (ITM and PTM, respectively).</span></span> <span data-ttu-id="ccb90-121">La validation en deux phases est désignée sous le terme « 2PC » dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="ccb90-121">Two-phase commit is referred to as 2PC in this topic.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ccb90-122">1. CreateCoordinationContext</span><span class="sxs-lookup"><span data-stu-id="ccb90-122">1. CreateCoordinationContext</span></span>|<span data-ttu-id="ccb90-123">12. Réponse de message d'application</span><span class="sxs-lookup"><span data-stu-id="ccb90-123">12. Application Message Response</span></span>|  
|<span data-ttu-id="ccb90-124">2. CreateCoordinationContextResponse</span><span class="sxs-lookup"><span data-stu-id="ccb90-124">2. CreateCoordinationContextResponse</span></span>|<span data-ttu-id="ccb90-125">13. Commit (achèvement)</span><span class="sxs-lookup"><span data-stu-id="ccb90-125">13. Commit (Completion)</span></span>|  
|<span data-ttu-id="ccb90-126">3. Register (achèvement)</span><span class="sxs-lookup"><span data-stu-id="ccb90-126">3. Register (Completion)</span></span>|<span data-ttu-id="ccb90-127">14. Prepare (2PC)</span><span class="sxs-lookup"><span data-stu-id="ccb90-127">14. Prepare (2PC)</span></span>|  
|<span data-ttu-id="ccb90-128">4. RegisterResponse</span><span class="sxs-lookup"><span data-stu-id="ccb90-128">4. RegisterResponse</span></span>|<span data-ttu-id="ccb90-129">15. Prepare (2PC)</span><span class="sxs-lookup"><span data-stu-id="ccb90-129">15. Prepare (2PC)</span></span>|  
|<span data-ttu-id="ccb90-130">5. Message d'application</span><span class="sxs-lookup"><span data-stu-id="ccb90-130">5. Application Message</span></span>|<span data-ttu-id="ccb90-131">16. Prepared (2PC)</span><span class="sxs-lookup"><span data-stu-id="ccb90-131">16. Prepared (2PC)</span></span>|  
|<span data-ttu-id="ccb90-132">6. CreateCoordinationContext avec Context</span><span class="sxs-lookup"><span data-stu-id="ccb90-132">6. CreateCoordinationContext with Context</span></span>|<span data-ttu-id="ccb90-133">17. Prepared (2PC)</span><span class="sxs-lookup"><span data-stu-id="ccb90-133">17. Prepared (2PC)</span></span>|  
|<span data-ttu-id="ccb90-134">7. Register (durable)</span><span class="sxs-lookup"><span data-stu-id="ccb90-134">7. Register (Durable)</span></span>|<span data-ttu-id="ccb90-135">18. Committed (achèvement)</span><span class="sxs-lookup"><span data-stu-id="ccb90-135">18. Committed (Completion)</span></span>|  
|<span data-ttu-id="ccb90-136">8. RegisterResponse</span><span class="sxs-lookup"><span data-stu-id="ccb90-136">8. RegisterResponse</span></span>|<span data-ttu-id="ccb90-137">19. Commit (2PC)</span><span class="sxs-lookup"><span data-stu-id="ccb90-137">19. Commit (2PC)</span></span>|  
|<span data-ttu-id="ccb90-138">9. CreateCoordinationContextResponse</span><span class="sxs-lookup"><span data-stu-id="ccb90-138">9. CreateCoordinationContextResponse</span></span>|<span data-ttu-id="ccb90-139">20. Commit (2PC)</span><span class="sxs-lookup"><span data-stu-id="ccb90-139">20. Commit (2PC)</span></span>|  
|<span data-ttu-id="ccb90-140">10. Register (durable)</span><span class="sxs-lookup"><span data-stu-id="ccb90-140">10. Register (Durable)</span></span>|<span data-ttu-id="ccb90-141">21. Committed (2PC)</span><span class="sxs-lookup"><span data-stu-id="ccb90-141">21. Committed (2PC)</span></span>|  
|<span data-ttu-id="ccb90-142">11. RegisterResponse</span><span class="sxs-lookup"><span data-stu-id="ccb90-142">11. RegisterResponse</span></span>|<span data-ttu-id="ccb90-143">22. Committed (2PC)</span><span class="sxs-lookup"><span data-stu-id="ccb90-143">22. Committed (2PC)</span></span>|  
  
 <span data-ttu-id="ccb90-144">Ce document décrit une composition de la spécification WS-AtomicTransaction avec sécurité et décrit la liaison sécurisée utilisée pour la communication entre les gestionnaires de transactions.</span><span class="sxs-lookup"><span data-stu-id="ccb90-144">This document describes a composition of the WS-AtomicTransaction specification with security and describes the secure binding used for communication between transaction managers.</span></span> <span data-ttu-id="ccb90-145">L'approche décrite dans ce document a été testée avec succès avec d'autres implémentations de WS-AT et WS-Coordination.</span><span class="sxs-lookup"><span data-stu-id="ccb90-145">The approach described in this document has been successfully tested with other implementations of WS-AT and WS-Coordination.</span></span>  
  
 <span data-ttu-id="ccb90-146">La figure et le tableau présentent quatre classes de messages du point de vue de sécurité :</span><span class="sxs-lookup"><span data-stu-id="ccb90-146">The figure and table illustrate four classes of messages from the viewpoint of security:</span></span>  
  
-   <span data-ttu-id="ccb90-147">Messages d'activation (CreateCoordinationContext et CreateCoordinationContextResponse).</span><span class="sxs-lookup"><span data-stu-id="ccb90-147">Activation messages (CreateCoordinationContext and CreateCoordinationContextResponse).</span></span>  
  
-   <span data-ttu-id="ccb90-148">Messages d'inscription (Register et RegisterResponse)</span><span class="sxs-lookup"><span data-stu-id="ccb90-148">Registration messages (Register and RegisterResponse)</span></span>  
  
-   <span data-ttu-id="ccb90-149">Messages de protocole (Prepare, Rollback, Commit, Aborted, etc).</span><span class="sxs-lookup"><span data-stu-id="ccb90-149">Protocol messages (Prepare, Rollback, Commit, Aborted, and so on).</span></span>  
  
-   <span data-ttu-id="ccb90-150">Messages d'application</span><span class="sxs-lookup"><span data-stu-id="ccb90-150">Application messages.</span></span>  
  
 <span data-ttu-id="ccb90-151">Les trois premières classes de message sont considérées comme des messages de gestionnaire de transactions et leur configuration de liaison est décrite dans la section « Échange de messages d'application » développée ultérieurement dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="ccb90-151">The first three message classes are considered Transaction Manager messages and their binding configuration is described in the "Application Message Exchange" later in this topic.</span></span> <span data-ttu-id="ccb90-152">La quatrième classe de message concerne les messages interapplication et est décrite dans la section « Exemples de message » développée ultérieurement dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="ccb90-152">The fourth class of message is application to application messages and is described in the "Message Examples" section later in this topic.</span></span> <span data-ttu-id="ccb90-153">Cette section décrit les liaisons de protocole utilisées pour chacune de ces classes par [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ccb90-153">This section describes the protocol bindings used for each of these classes by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
 <span data-ttu-id="ccb90-154">Les espaces de noms XML suivants et préfixes associés sont utilisés dans l'ensemble de ce document.</span><span class="sxs-lookup"><span data-stu-id="ccb90-154">The following XML Namespaces and associated prefixes are used throughout this document.</span></span>  
  
|<span data-ttu-id="ccb90-155">Préfixe</span><span class="sxs-lookup"><span data-stu-id="ccb90-155">Prefix</span></span>|<span data-ttu-id="ccb90-156">URI d'espace de noms</span><span class="sxs-lookup"><span data-stu-id="ccb90-156">Namespace URI</span></span>|  
|------------|-------------------|  
|<span data-ttu-id="ccb90-157">s11</span><span class="sxs-lookup"><span data-stu-id="ccb90-157">s11</span></span>|<span data-ttu-id="ccb90-158">http://schemas.xmlsoap.org/soap/envelope</span><span class="sxs-lookup"><span data-stu-id="ccb90-158">http://schemas.xmlsoap.org/soap/envelope</span></span>|  
|<span data-ttu-id="ccb90-159">wsa</span><span class="sxs-lookup"><span data-stu-id="ccb90-159">wsa</span></span>|<span data-ttu-id="ccb90-160">http://www.w3.org/2004/08/Addressing</span><span class="sxs-lookup"><span data-stu-id="ccb90-160">http://www.w3.org/2004/08/addressing</span></span>|  
|<span data-ttu-id="ccb90-161">wscoor</span><span class="sxs-lookup"><span data-stu-id="ccb90-161">wscoor</span></span>|<span data-ttu-id="ccb90-162">http://schemas.xmlsoap.org/ws/2004/10/wscoor</span><span class="sxs-lookup"><span data-stu-id="ccb90-162">http://schemas.xmlsoap.org/ws/2004/10/wscoor</span></span>|  
|<span data-ttu-id="ccb90-163">wsat</span><span class="sxs-lookup"><span data-stu-id="ccb90-163">wsat</span></span>|<span data-ttu-id="ccb90-164">http://schemas.xmlsoap.org/ws/2004/10/wsat</span><span class="sxs-lookup"><span data-stu-id="ccb90-164">http://schemas.xmlsoap.org/ws/2004/10/wsat</span></span>|  
|<span data-ttu-id="ccb90-165">t</span><span class="sxs-lookup"><span data-stu-id="ccb90-165">t</span></span>|<span data-ttu-id="ccb90-166">http://schemas.xmlsoap.org/ws/2005/02/trust</span><span class="sxs-lookup"><span data-stu-id="ccb90-166">http://schemas.xmlsoap.org/ws/2005/02/trust</span></span>|  
|<span data-ttu-id="ccb90-167">o</span><span class="sxs-lookup"><span data-stu-id="ccb90-167">o</span></span>|<span data-ttu-id="ccb90-168">http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd</span><span class="sxs-lookup"><span data-stu-id="ccb90-168">http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd</span></span>|  
|<span data-ttu-id="ccb90-169">xsd</span><span class="sxs-lookup"><span data-stu-id="ccb90-169">xsd</span></span>|<span data-ttu-id="ccb90-170">http://www.w3.org/2001/XMLSchema</span><span class="sxs-lookup"><span data-stu-id="ccb90-170">http://www.w3.org/2001/XMLSchema</span></span>|  
  
## <a name="transaction-manager-bindings"></a><span data-ttu-id="ccb90-171">Liaisons de gestionnaire de transactions</span><span class="sxs-lookup"><span data-stu-id="ccb90-171">Transaction Manager Bindings</span></span>  
 <span data-ttu-id="ccb90-172">R1001 : les gestionnaires de transactions doivent utiliser SOAP 1.1 et WS-Addressing 2004/08 pour les échanges de message WS-Atomic Transaction et WS-Coordination.</span><span class="sxs-lookup"><span data-stu-id="ccb90-172">R1001: Transaction Managers must use SOAP 1.1 and WS-Addressing 2004/08 for WS-Atomic Transaction and WS-Coordination message exchanges.</span></span>  
  
 <span data-ttu-id="ccb90-173">Les messages d'application ne sont pas contraints à ces liaisons et sont décrits ultérieurement.</span><span class="sxs-lookup"><span data-stu-id="ccb90-173">Application messages are not constrained to these bindings and are described later.</span></span>  
  
### <a name="transaction-manager-https-binding"></a><span data-ttu-id="ccb90-174">Liaison HTTPS de gestionnaire de transactions</span><span class="sxs-lookup"><span data-stu-id="ccb90-174">Transaction Manager HTTPS Binding</span></span>  
 <span data-ttu-id="ccb90-175">La liaison HTTPS de gestionnaire de transactions s'appuie uniquement sur le transport de sécurité pour assurer la sécurité et établir la confiance entre chaque paire expéditeur-récepteur dans l'arborescence de transactions.</span><span class="sxs-lookup"><span data-stu-id="ccb90-175">The transaction manager HTTPS binding relies solely on transport security to achieve security and establish trust between each sender-receiver pair in the transaction tree.</span></span>  
  
#### <a name="https-transport-configuration"></a><span data-ttu-id="ccb90-176">Configuration du transport HTTPS</span><span class="sxs-lookup"><span data-stu-id="ccb90-176">HTTPS Transport Configuration</span></span>  
 <span data-ttu-id="ccb90-177">Les certificats X.509 permettent d'établir l'identité de gestionnaire de transactions.</span><span class="sxs-lookup"><span data-stu-id="ccb90-177">X.509 certificates are used to establish Transaction Manager Identity.</span></span> <span data-ttu-id="ccb90-178">L'authentification client/serveur est requise, et l'autorisation client/serveur est considérée comme un détail d'implémentation :</span><span class="sxs-lookup"><span data-stu-id="ccb90-178">Client/server authentication is required, and client/server authorization is left as an implementation detail:</span></span>  
  
-   <span data-ttu-id="ccb90-179">R1111 : les certificats X.509 présentés sur le câble doivent avoir un nom de sujet qui correspond au nom de domaine complet de l'ordinateur d'origine.</span><span class="sxs-lookup"><span data-stu-id="ccb90-179">R1111: X.509 certificates presented over the wire must have a subject name that matches the fully qualified domain name (FQDN) of the originating machine.</span></span>  
  
-   <span data-ttu-id="ccb90-180">B1112 : le DNS doit être fonctionnel entre chaque paire expéditeur-récepteur du système pour que les vérifications du nom de sujet X.509 réussissent.</span><span class="sxs-lookup"><span data-stu-id="ccb90-180">B1112: DNS must be functional between each sender-receiver pair in the system for X.509 subject name checks to succeed.</span></span>  
  
#### <a name="activation-and-registration-binding-configuration"></a><span data-ttu-id="ccb90-181">Configuration de liaison d'activation et d'inscription</span><span class="sxs-lookup"><span data-stu-id="ccb90-181">Activation and Registration Binding Configuration</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="ccb90-182"> requiert une liaison duplex demande/réponse avec corrélation sur HTTPS.</span><span class="sxs-lookup"><span data-stu-id="ccb90-182"> requires request/reply duplex binding with correlation over HTTPS.</span></span> <span data-ttu-id="ccb90-183">(Pour plus d'informations sur la corrélation et les descriptions des modèles d'échange de messages demande/réponse, consultez WS-Atomic Transaction, section 8.)</span><span class="sxs-lookup"><span data-stu-id="ccb90-183">(For more information about correlation and descriptions of the request/reply message exchange patterns, see WS-Atomic Transaction, Section 8.)</span></span>  
  
#### <a name="2pc-protocol-binding-configuration"></a><span data-ttu-id="ccb90-184">Configuration de liaison de protocole 2PC</span><span class="sxs-lookup"><span data-stu-id="ccb90-184">2PC Protocol Binding Configuration</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="ccb90-185"> prend en charge des messages monodirectionnels (datagramme) sur HTTPS.</span><span class="sxs-lookup"><span data-stu-id="ccb90-185"> supports one-way (datagram) messages over HTTPS.</span></span> <span data-ttu-id="ccb90-186">La corrélation au sein des messages est considérée comme un détail d'implémentation.</span><span class="sxs-lookup"><span data-stu-id="ccb90-186">Correlation among the messages is left as an implementation detail.</span></span>  
  
 <span data-ttu-id="ccb90-187">B2131 : Les implémentations doivent prendre en charge `wsa:ReferenceParameters` comme décrit dans WS-Addressing pour la corrélation de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]de messages 2PC.</span><span class="sxs-lookup"><span data-stu-id="ccb90-187">B2131: Implementations must support `wsa:ReferenceParameters` as described in WS-Addressing to achieve correlation of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]’s 2PC messages.</span></span>  
  
### <a name="transaction-manager-mixed-security-binding"></a><span data-ttu-id="ccb90-188">Liaison de sécurité mixte de gestionnaire de transactions</span><span class="sxs-lookup"><span data-stu-id="ccb90-188">Transaction Manager Mixed Security Binding</span></span>  
 <span data-ttu-id="ccb90-189">Il s’agit d’un autre (mode mixte) qui utilise la sécurité transport combinée avec le modèle WS-Coordination Issued Token à des fins identité établissement de liaison.</span><span class="sxs-lookup"><span data-stu-id="ccb90-189">This is an alternate (mixed mode) binding that uses transport security combined with the  WS-Coordination Issued Token model for identity establishment purposes.</span></span>  <span data-ttu-id="ccb90-190">L’activation et l’inscription sont les seuls éléments qui diffèrent entre les deux liaisons.</span><span class="sxs-lookup"><span data-stu-id="ccb90-190">Activation and Registration are the only elements that differ between the two bindings.</span></span>  
  
#### <a name="https-transport-configuration"></a><span data-ttu-id="ccb90-191">Configuration du transport HTTPS</span><span class="sxs-lookup"><span data-stu-id="ccb90-191">HTTPS Transport Configuration</span></span>  
 <span data-ttu-id="ccb90-192">Les certificats X.509 permettent d’établir l’identité de gestionnaire de transactions.</span><span class="sxs-lookup"><span data-stu-id="ccb90-192">X.509 certificates are used to establish Transaction Manager Identity.</span></span> <span data-ttu-id="ccb90-193">L'authentification client/serveur est requise, et l'autorisation client/serveur est considérée comme un détail d'implémentation.</span><span class="sxs-lookup"><span data-stu-id="ccb90-193">Client/Server authentication is required, and client/server authorization is left as an implementation detail.</span></span>  
  
#### <a name="activation-message-binding-configuration"></a><span data-ttu-id="ccb90-194">Configuration de liaison de message d’activation</span><span class="sxs-lookup"><span data-stu-id="ccb90-194">Activation Message Binding Configuration</span></span>  
 <span data-ttu-id="ccb90-195">En général, les messages d’activation ne participent pas à l’interopérabilité car ils se produisent habituellement entre une application et son gestionnaire de transactions local.</span><span class="sxs-lookup"><span data-stu-id="ccb90-195">Activation Messages usually do not participate in interoperability because they typically occur between an application and its local Transaction Manager.</span></span>  
  
 <span data-ttu-id="ccb90-196">B1221 : [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] utilise la liaison HTTPS duplex (décrit dans [protocoles de messagerie](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)) pour les messages d’Activation.</span><span class="sxs-lookup"><span data-stu-id="ccb90-196">B1221: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uses duplex HTTPS binding (described in [Messaging Protocols](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)) for Activation messages.</span></span> <span data-ttu-id="ccb90-197">Les messages de demande et de réponse sont corrélés à l'aide de WS-Addressing 2004/08.</span><span class="sxs-lookup"><span data-stu-id="ccb90-197">Request and Reply messages are correlated using WS-Addressing 2004/08.</span></span>  
  
 <span data-ttu-id="ccb90-198">La spécification WS-Atomic Transaction, section 8, fournit des informations supplémentaires sur la corrélation et les modèles d’échange de messages.</span><span class="sxs-lookup"><span data-stu-id="ccb90-198">WS-Atomic Transaction specification, Section 8, describes further details about correlation and the message exchange patterns.</span></span>  
  
-   <span data-ttu-id="ccb90-199">R1222 : après réception de `CreateCoordinationContext`, le coordinateur doit émettre `SecurityContextToken` avec le `STx` secret associé.</span><span class="sxs-lookup"><span data-stu-id="ccb90-199">R1222: Upon receiving a `CreateCoordinationContext`, the Coordinator must issue a `SecurityContextToken` with associated secret `STx`.</span></span> <span data-ttu-id="ccb90-200">Ce jeton est retourné à l'intérieur d'un en-tête `t:IssuedTokens` selon la spécification WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="ccb90-200">This token is returned inside a `t:IssuedTokens` header following WS-Trust specification.</span></span>  
  
-   <span data-ttu-id="ccb90-201">R1223 : si l'activation se produit dans un contexte de coordination existant, l'en-tête `t:IssuedTokens` avec `SecurityContextToken` associé au contexte existant doit transmettre sur le message `CreateCoordinationContext`.</span><span class="sxs-lookup"><span data-stu-id="ccb90-201">R1223: If Activation occurs within an existing Coordination Context, the `t:IssuedTokens` header with the `SecurityContextToken` associated with existing Context must flow on the `CreateCoordinationContext` message.</span></span>  
  
 <span data-ttu-id="ccb90-202">Un nouveau `t:IssuedTokens` en-tête doit être généré pour l’attachement à sortant `wscoor:CreateCoordinationContextResponse` message.</span><span class="sxs-lookup"><span data-stu-id="ccb90-202">A new `t:IssuedTokens` header should be generated for attaching to the outgoing `wscoor:CreateCoordinationContextResponse` message.</span></span>  
  
#### <a name="registration-message-binding-configuration"></a><span data-ttu-id="ccb90-203">Configuration de liaison de message d’inscription</span><span class="sxs-lookup"><span data-stu-id="ccb90-203">Registration Message Binding Configuration</span></span>  
 <span data-ttu-id="ccb90-204">B1231 : [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] utilise la liaison HTTPS duplex (décrit dans [protocoles de messagerie](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)).</span><span class="sxs-lookup"><span data-stu-id="ccb90-204">B1231: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uses duplex HTTPS binding (described in [Messaging Protocols](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)).</span></span> <span data-ttu-id="ccb90-205">Les messages de demande et de réponse sont corrélés à l'aide de WS-Addressing 2004/08.</span><span class="sxs-lookup"><span data-stu-id="ccb90-205">Request and Reply messages are correlated using WS-Addressing 2004/08.</span></span>  
  
 <span data-ttu-id="ccb90-206">WS-AtomicTransaction, section 8, fournit des informations supplémentaires sur la corrélation et des descriptions des modèles d’échange de messages.</span><span class="sxs-lookup"><span data-stu-id="ccb90-206">WS-AtomicTransaction, Section 8, describes further details about correlation and descriptions of the message exchange patterns.</span></span>  
  
 <span data-ttu-id="ccb90-207">R1232 : Sortant `wscoor:Register` messages doivent utiliser le `IssuedTokenOverTransport` mode d’authentification décrits dans [protocoles de sécurité](../../../../docs/framework/wcf/feature-details/security-protocols.md).</span><span class="sxs-lookup"><span data-stu-id="ccb90-207">R1232: Outgoing `wscoor:Register` messages must use the `IssuedTokenOverTransport` authentication mode described in [Security Protocols](../../../../docs/framework/wcf/feature-details/security-protocols.md).</span></span>  
  
 <span data-ttu-id="ccb90-208">Le `wsse:Timestamp` élément doit être signé à l’aide de la `SecurityContextToken``STx` émis.</span><span class="sxs-lookup"><span data-stu-id="ccb90-208">The `wsse:Timestamp` element must be signed using the `SecurityContextToken``STx` issued.</span></span> <span data-ttu-id="ccb90-209">Cette signature est une preuve de possession du jeton associée à une transaction spécifique et est utilisée pour authentifier un participant qui s’inscrit à la transaction.</span><span class="sxs-lookup"><span data-stu-id="ccb90-209">This signature is a proof of possession of the token associated with particular transaction and is used to authenticate a participant enlisting in the transaction.</span></span> <span data-ttu-id="ccb90-210">Le message RegistrationResponse est renvoyé sur HTTPS.</span><span class="sxs-lookup"><span data-stu-id="ccb90-210">The RegistrationResponse message is sent back over HTTPS.</span></span>  
  
#### <a name="2pc-protocol-binding-configuration"></a><span data-ttu-id="ccb90-211">Configuration de liaison de protocole 2PC</span><span class="sxs-lookup"><span data-stu-id="ccb90-211">2PC Protocol Binding Configuration</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="ccb90-212"> prend en charge des messages monodirectionnels (datagramme) sur HTTPS.</span><span class="sxs-lookup"><span data-stu-id="ccb90-212"> supports one-way (datagram) messages over HTTPS.</span></span> <span data-ttu-id="ccb90-213">La corrélation au sein des messages est considérée comme un détail d'implémentation.</span><span class="sxs-lookup"><span data-stu-id="ccb90-213">Correlation among the messages is left as an implementation detail.</span></span>  
  
 <span data-ttu-id="ccb90-214">B2131 : Les implémentations doivent prendre en charge `wsa:ReferenceParameters` comme décrit dans WS-Addressing pour la corrélation de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]de messages 2PC.</span><span class="sxs-lookup"><span data-stu-id="ccb90-214">B2131: Implementations must support `wsa:ReferenceParameters` as described in WS-Addressing to achieve correlation of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]’s 2PC messages.</span></span>  
  
## <a name="application-message-exchange"></a><span data-ttu-id="ccb90-215">Échange de messages d'application</span><span class="sxs-lookup"><span data-stu-id="ccb90-215">Application Message Exchange</span></span>  
 <span data-ttu-id="ccb90-216">Les applications sont libres d'utiliser n'importe quelle liaison spécifique pour les messages interapplication, tant que la liaison satisfait aux conditions de sécurité suivantes :</span><span class="sxs-lookup"><span data-stu-id="ccb90-216">Applications are free to use any particular binding for application-to-application messages, as long as the binding meets the following security requirements:</span></span>  
  
-   <span data-ttu-id="ccb90-217">R2001 : les messages interapplication doivent transmettre l'en-tête `t:IssuedTokens` avec `CoordinationContext` dans l'en-tête du message.</span><span class="sxs-lookup"><span data-stu-id="ccb90-217">R2001: Application-to-application messages must flow the `t:IssuedTokens` header along with the `CoordinationContext` in the header of the message.</span></span>  
  
-   <span data-ttu-id="ccb90-218">R2002 : l'intégrité et la confidentialité de `t:IssuedToken` doivent être assurées.</span><span class="sxs-lookup"><span data-stu-id="ccb90-218">R2002: Integrity and confidentiality of `t:IssuedToken` must be provided.</span></span>  
  
 <span data-ttu-id="ccb90-219">L'en-tête `CoordinationContext` contient `wscoor:Identifier`.</span><span class="sxs-lookup"><span data-stu-id="ccb90-219">The `CoordinationContext` header contains `wscoor:Identifier`.</span></span> <span data-ttu-id="ccb90-220">Alors que la définition de `xsd:AnyURI` permet d'utiliser des URI absolus et relatifs, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] prend uniquement en charge `wscoor:Identifiers`, qui sont des URI absolus.</span><span class="sxs-lookup"><span data-stu-id="ccb90-220">While the definition of `xsd:AnyURI` allows the use of both absolute and relative URIs, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] supports only `wscoor:Identifiers`, which are absolute URIs.</span></span>  
  
 <span data-ttu-id="ccb90-221">Si `wscoor:Identifier` de `wscoor:CoordinationContext` est un URI relatif, les erreurs seront retournées par les services [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] transactionnels.</span><span class="sxs-lookup"><span data-stu-id="ccb90-221">If the `wscoor:Identifier` of the `wscoor:CoordinationContext` is a relative URI, faults will be returned from transactional [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services.</span></span>  
  
## <a name="message-examples"></a><span data-ttu-id="ccb90-222">Exemples de message</span><span class="sxs-lookup"><span data-stu-id="ccb90-222">Message Examples</span></span>  
  
### <a name="createcoordinationcontext-requestresponse-messages"></a><span data-ttu-id="ccb90-223">Messages de demande/réponse CreateCoordinationContext</span><span class="sxs-lookup"><span data-stu-id="ccb90-223">CreateCoordinationContext Request/Response Messages</span></span>  
 <span data-ttu-id="ccb90-224">Les messages suivants suivent un modèle de demande/réponse.</span><span class="sxs-lookup"><span data-stu-id="ccb90-224">The following messages follow a request/response pattern.</span></span>  
  
#### <a name="createcoordinationcontext"></a><span data-ttu-id="ccb90-225">CreateCoordinationContext</span><span class="sxs-lookup"><span data-stu-id="ccb90-225">CreateCoordinationContext</span></span>  
  
```xml  
<s:Envelope>  
  <s:Header>  
    <a:Action>http://.../ws/2004/10/wscoor/CreateCoordinationContext</Action>  
    <a:MessageID>urn:uuid:069f5104-fd88-4264-9f99-60032a82854e</MessageID>  
    <a:ReplyTo>  
      <Address>https://...</a:Address>  
    </a:ReplyTo>  
    <a:To>https://...</a:To>  
    <wsse:Security>  
      <u:Timestamp>  
        <wsu:Created>2005-12-15T23:36:09.921Z</u:Created>  
        <wsu:Expires>2005-12-15T23:41:09.921Z</u:Expires>  
      </u:Timestamp>  
    </wsse:Security>  
  </s:Header>  
  <s:Body xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">  
    <wscoor:CreateCoordinationContext>  
      <wscoor:CoordinationType>...</wscoor:CoordinationType>  
    </wscoor:CreateCoordinationContext>  
  </s:Body>  
</s11:Envelope>  
```  
  
#### <a name="createcoordinationcontextresponse"></a><span data-ttu-id="ccb90-226">CreateCoordinationContextResponse</span><span class="sxs-lookup"><span data-stu-id="ccb90-226">CreateCoordinationContextResponse</span></span>  
  
```xml  
<s:Envelope>  
  <!-- Data below is shown in the clear for  
       illustration purposes only. -->  
  <s:Header>  
    <a:Action>./ws/2004/10/wscoor/CreateCoordinationContextResponse </a:Action>  
    <a:RelatesTo>urn:uuid:069f5104-fd88-4264-9f99-60032a82854e</a:RelatesTo>  
    <a:To s:mustUnderstand="1">https://... </a:To>  
    <t:IssuedTokens>  
 <wst:RequestSecurityTokenResponse     
    xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"  
    xmlns:wssu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd"   
    xmlns:wst="http://schemas.xmlsoap.org/ws/2005/02/trust"  
    xmlns:wsc="http://schemas.xmlsoap.org/ws/2005/02/sc"  
    xmlns:wsp="http://schemas.xmlsoap.org/ws/2004/09/policy">  
    <wst:TokenType>http://schemas.xmlsoap.org/ws/2005/02/sc/sct</wst:TokenType>  
    <wst:RequestedSecurityToken>  
      <wsc:SecurityContextToken>  
        <wssu:Identifier>  
          http://fabrikam123.com/SCTi  
        </wssu:Identifier>  
      </wsc:SecurityContextToken>   
    </wst:RequestedSecurityToken>  
    <wsp:AppliesTo>  
        http://fabrikam123.com/CCi  
    </wsp:AppliesTo>    
    <wst:RequestedAttachedReference>  
      <wsse:SecurityTokenReference >  
        <wsse:Reference   
           ValueType="http://schemas.xmlsoap.org/ws/2005/02/sc/sct"  
           URI="http://fabrikam123.com/SCTi"/>  
      </wsse:SecurityTokenReference>  
    </wst:RequestedAttachedReference>  
    <wst:RequestedUnattachedReference>  
      <wsse:SecurityTokenReference>  
        <wsse:Reference   
          ValueType="http://schemas.xmlsoap.org/ws/2005/02/sc/sct"  
          URI="http://fabrikam123.com/SCTi"/>  
      </wsse:SecurityTokenReference>  
    </wst:RequestedUnattachedReference>  
    <wst:RequestedProofToken>  
      <wst:BinarySecret   
        Type="http://schemas.xmlsoap.org/ws/2005/02/trust/SymmetricKey">  
        <!-- base64 encoded value -->  
      </wst:BinarySecret>  
    </wst:RequestedProofToken>  
    <wst:Lifetime>  
      <wssu:Created>2005-10-24T20:19:26.526Z</wssu:Created>  
      <wssu:Expires>2005-10-25T06:24:26.526Z</wssu:Expires>  
    </wst:Lifetime>  
    <wst:KeySize>256</wst:KeySize>  
</wst:RequestSecurityTokenResponse>  
    </t:IssuedTokens>  
    <o:Security xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">  
      <u:Timestamp u:Id="_0">  
        <u:Created>2005-12-15T23:36:12.015Z</u:Created>  
        <u:Expires>2005-12-15T23:41:12.015Z</u:Expires>  
      </u:Timestamp>  
    </o:Security>  
  </s:Header>  
  <s:Body>  
    <wscoor:CreateCoordinationContextResponse>  
      <wscoor:CoordinationContext>  
        <wscoor:Identifier>  
     http://fabrikam123.com/CCi  
      </wscoor:Identifier>  
        <wscoor:Expires>...</wscoor:Expires>  
        <wscoor:CoordinationType>...</wscoor:CoordinationType>  
        <wscoor:RegistrationService>  
          <a:Address>https://...</a:Address>  
          <a:ReferenceParameters>  
             ...  
          </a:ReferenceParameters>  
        </wscoor:RegistrationService>  
      </wscoor:CoordinationContext>  
    </wscoor:CreateCoordinationContextResponse>  
  </s:Body>  
</s:Envelope>  
```  
  
### <a name="registration-messages"></a><span data-ttu-id="ccb90-227">Messages d'inscription</span><span class="sxs-lookup"><span data-stu-id="ccb90-227">Registration Messages</span></span>  
 <span data-ttu-id="ccb90-228">Les messages suivants sont des messages d'inscription.</span><span class="sxs-lookup"><span data-stu-id="ccb90-228">The following messages are registration messages.</span></span>  
  
#### <a name="register"></a><span data-ttu-id="ccb90-229">Registre</span><span class="sxs-lookup"><span data-stu-id="ccb90-229">Register</span></span>  
  
```xml  
<s:Envelope>  
  <s:Header>  
    <a:Action>http://schemas.xmlsoap.org/ws/2004/10/wscoor/Register</a:Action>  
    <a:MessageID>urn:uuid:ed418b86-a75e-4aea-9d4e-a5d0cb5c088e</a:MessageID>  
    <a:ReplyTo>  
      <a:Address>https://...</a:Address>        
    </a:ReplyTo>  
    <a:To>https://...</a:To>  
    <wsse:Security   
      s:mustUnderstand="1"   
      xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"  
      xmlns:wssu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">  
      <wssu:Timestamp wssu:Id="_0" >  
        <wssu:Created>2005-12-15T23:36:13.827Z</wssu:Created>  
        <wssu:Expires>2005-12-15T23:41:13.827Z</wssu:Expires>  
      </wssu:Timestamp>  
      <wsc:SecurityContextToken>  
      <wssu:Identifier>  
          http://fabrikam123.com/SCTi  
      </wssu:Identifier>  
      </wsc:SecurityContextToken>  
      <!-- supporting signature over the timestamp -->  
      <wsse:Signature xmlns:ds="http://www.w3.org/2000/09/xmldsig#">  
        <ds:SignedInfo>  
          <ds:CanonicalizationMethod Algorithm="http://www.w3.org/2001/10/xml-exc-c14n#"/>  
          <ds:SignatureMethod Algorithm="http://www.w3.org/2000/09/xmldsig#hmac-sha1"/>  
          <ds:Reference URI="#_0">  
            <ds:Transforms>  
              <ds:Transform Algorithm="http://www.w3.org/2001/10/xml-exc-c14n#"/>  
            </ds:Transforms>  
            <ds:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1"/>  
            <ds:DigestValue>  
              alRzyhjLgoUOYoh8cx4n75eTcUk=  
            </ds:DigestValue>  
          </ds:Reference>  
        </ds:SignedInfo>  
        <ds:SignatureValue>YZYjnVvSOVasAQqQxaaviTSWtqI=</ds:SignatureValue>  
        <ds:KeyInfo>  
          <wsse:SecurityTokenReference  
            xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">  
            <wsse:Reference   
              URI="http://fabrikam123.com/SCTi"/>  
          </wsse:SecurityTokenReference>  
        </ds:KeyInfo>  
      </wsse:Signature>  
    </wsse:Security>  
  </s:Header>  
  <s:Body xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">  
    <wscoor:Register>  
      <wscoor:ProtocolIdentifier>...</wscoor:ProtocolIdentifier>  
      <wscoor:ParticipantProtocolService>  
        <a:Address>https://... </a:Address>  
      </wscoor:ParticipantProtocolService>  
    </wscoor:Register>  
  </s:Body>  
</s:Envelope>  
```  
  
#### <a name="register-response"></a><span data-ttu-id="ccb90-230">Register Response</span><span class="sxs-lookup"><span data-stu-id="ccb90-230">Register Response</span></span>  
  
```xml  
<s:Envelope>  
  <s:Header>  
    <a:Action>  
      http://schemas.xmlsoap.org/ws/2004/10/wscoor/RegisterResponse  
    </a:Action>  
    <a:MessageID>urn:uuid:ed418b86-a75e-4aea-9d4e-a5d0cb5c088d</a:MessageID>  
    <a:RelatesTo>  
      urn:uuid:ed418b86-a75e-4aea-9d4e-a5d0cb5c088e        
    </a:RelatesTo>  
    <a:To>https://...</a:To>  
    <wsse:Security   
      s:mustUnderstand="1"   
      xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"  
      xmlns:wssu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">  
      <wssu:Timestamp>  
        <wssu:Created>2005-12-15T23:36:13.827Z</wssu:Created>  
        <wssu:Expires>2005-12-15T23:41:13.827Z</wssu:Expires>  
      </wssu:Timestamp>  
    </wsse:Security>  
  </s:Header>  
  <s:Body xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">  
    <wscoor:RegisterResponse>  
      <wscoor:CoordinatorProtocolService>  
        <a:Address>https://...</a:Address>  
        <a:ReferenceParameters>  
          ...  
        </a:ReferenceParameters>  
      </wscoor:CoordinatorProtocolService>  
    </wscoor:RegisterResponse>  
  </s:Body>  
</s:Envelope>  
```  
  
### <a name="two-phase-commit-protocol-messages"></a><span data-ttu-id="ccb90-231">Messages de protocole de validation à deux phases</span><span class="sxs-lookup"><span data-stu-id="ccb90-231">Two Phase Commit Protocol Messages</span></span>  
 <span data-ttu-id="ccb90-232">Le message suivant concerne le protocole de validation en deux phases (2PC).</span><span class="sxs-lookup"><span data-stu-id="ccb90-232">The following message relates to the two-phase commit (2PC) protocol.</span></span>  
  
#### <a name="commit"></a><span data-ttu-id="ccb90-233">Valider</span><span class="sxs-lookup"><span data-stu-id="ccb90-233">Commit</span></span>  
  
```xml  
<s:Envelope>  
  <s:Header>  
    <a:Action>http://.../ws/2004/10/wsat/Commit</a:Action>  
    <a:To>https://...</a:To>  
    <wsse:Security   
      s:mustUnderstand="1"   
      xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"  
      xmlns:wssu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">  
      <wssu:Timestamp wssu:Id="_0" >  
        <wssu:Created>2005-12-15T23:36:13.827Z</wssu:Created>  
        <wssu:Expires>2005-12-15T23:41:13.827Z</wssu:Expires>  
      </wssu:Timestamp>  
   </wsse:Security>  
  </s:Header>  
  <s:Body xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">  
    <wsat:Commit />  
  </s:Body>  
</s:Envelope>  
```  
  
### <a name="application-messages"></a><span data-ttu-id="ccb90-234">Messages d'application</span><span class="sxs-lookup"><span data-stu-id="ccb90-234">Application Messages</span></span>  
 <span data-ttu-id="ccb90-235">Les messages suivants sont des messages d'application.</span><span class="sxs-lookup"><span data-stu-id="ccb90-235">The following messages are application messages.</span></span>  
  
#### <a name="application-message-request"></a><span data-ttu-id="ccb90-236">Message d'application - demande</span><span class="sxs-lookup"><span data-stu-id="ccb90-236">Application message-Request</span></span>  
  
```xml  
<s:Envelope>  
  <s:Header>  
<!-- Addressing headers, all signed-->  
    <wsse:Security s:mustUnderstand="1">  
      <wssu:Timestamp wssu:Id="timestamp">   
        <wssu:Created>2005-10-25T06:29:18.703Z</wssu:Created>  
        <wssu:Expires>2005-10-25T06:34:18.703Z</wssu:Expires>  
      </wssu:Timestamp>  
      <wsse:BinarySecurityToken   
          wssu:Id="IA_Certificate"   
          ValueType="...#X509v3"   
          EncodingType="...#Base64Binary">  
        <!-- IA certificate -->  
      </wsse:BinarySecurityToken>  
      <e:EncryptedKey Id="encrypted_key">  
            <!-- ephemeral key encrypted for PA certificate -->    
        <e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#">  
          <e:DataReference URI="#encrypted_body"/>  
          <e:DataReference URI="#encrypted_CCi"/>  
          <e:DataReference URI="#encrypted_issuedtokens"/>  
        </e:ReferenceList>  
      </e:EncryptedKey>  
      <Signature xmlns="http://www.w3.org/2000/09/xmldsig#">  
        <!-- signature over Addressing headers, Timestamp, and Body -->  
      </Signature>  
    </wsse:Security>  
    <wsse11:EncryptedHeader >  
     <!-- encrypted wscoor:CoordinationContext header containing CCi -->  
    </wsse11:EncryptedHeader>  
    <wsse11:EncryptedHeader   
      <!-- encrypted wst:IssuedTokens header containing SCTi -->  
      <!-- wst:IssuedTokens header is taken verbatim from message #2 above, omitted for brevity -->  
    </wsse11:EncryptedHeader>  
  </s:Header>  
  <s:Body wssu:Id="body">  
    <!-- encrypted content of the Body element of the application message -->      
    <e:EncryptedData Id="encrypted_body"   
           Type="http://www.w3.org/2001/04/xmlenc#Content"   
           xmlns:e="http://www.w3.org/2001/04/xmlenc#">  
...  
    </e:EncryptedData>  
  </s:Body>  
</s:Envelope>  
```
