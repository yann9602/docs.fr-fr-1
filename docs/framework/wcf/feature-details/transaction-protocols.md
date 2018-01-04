---
title: Protocoles de transaction
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2820b0ec-2f32-430c-b299-1f0e95e1f2dc
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 13784a3a5062705abba1b3bbb33a04e66bd22072
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="transaction-protocols"></a><span data-ttu-id="0aabe-102">Protocoles de transaction</span><span class="sxs-lookup"><span data-stu-id="0aabe-102">Transaction Protocols</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="0aabe-103"> implémente les protocoles WS-Atomic Transaction et WS-Coordination.</span><span class="sxs-lookup"><span data-stu-id="0aabe-103"> implements WS-Atomic Transaction and WS-Coordination protocols.</span></span>  
  
|<span data-ttu-id="0aabe-104">Spécification/Document</span><span class="sxs-lookup"><span data-stu-id="0aabe-104">Specification/Document</span></span>|<span data-ttu-id="0aabe-105">Version</span><span class="sxs-lookup"><span data-stu-id="0aabe-105">Version</span></span>|<span data-ttu-id="0aabe-106">Lien</span><span class="sxs-lookup"><span data-stu-id="0aabe-106">Link</span></span>|  
|-----------------------------|-------------|----------|  
|<span data-ttu-id="0aabe-107">WS-Coordination</span><span class="sxs-lookup"><span data-stu-id="0aabe-107">WS-Coordination</span></span>|<span data-ttu-id="0aabe-108">1.0</span><span class="sxs-lookup"><span data-stu-id="0aabe-108">1.0</span></span><br /><br /> <span data-ttu-id="0aabe-109">1.1</span><span class="sxs-lookup"><span data-stu-id="0aabe-109">1.1</span></span>|[<span data-ttu-id="0aabe-110">http://go.Microsoft.com/fwlink/?LinkId=96104</span><span class="sxs-lookup"><span data-stu-id="0aabe-110">http://go.microsoft.com/fwlink/?LinkId=96104</span></span>](http://go.microsoft.com/fwlink/?LinkId=96104)<br /><br /> [<span data-ttu-id="0aabe-111">http://go.Microsoft.com/fwlink/?LinkId=96079</span><span class="sxs-lookup"><span data-stu-id="0aabe-111">http://go.microsoft.com/fwlink/?LinkId=96079</span></span>](http://go.microsoft.com/fwlink/?LinkId=96079)|  
|<span data-ttu-id="0aabe-112">WS-AtomicTransaction</span><span class="sxs-lookup"><span data-stu-id="0aabe-112">WS-AtomicTransaction</span></span>|<span data-ttu-id="0aabe-113">1.0</span><span class="sxs-lookup"><span data-stu-id="0aabe-113">1.0</span></span><br /><br /> <span data-ttu-id="0aabe-114">1.1</span><span class="sxs-lookup"><span data-stu-id="0aabe-114">1.1</span></span>|[<span data-ttu-id="0aabe-115">http://go.Microsoft.com/fwlink/?LinkId=96080</span><span class="sxs-lookup"><span data-stu-id="0aabe-115">http://go.microsoft.com/fwlink/?LinkId=96080</span></span>](http://go.microsoft.com/fwlink/?LinkId=96080)<br /><br /> <span data-ttu-id="0aabe-116">http://go.microsoft.com/fwlink/?LinkId=96081 (page pouvant être en anglais)</span><span class="sxs-lookup"><span data-stu-id="0aabe-116">http://go.microsoft.com/fwlink/?LinkId=96081</span></span>|  
  
 <span data-ttu-id="0aabe-117">L’interopérabilité sur ces spécifications de protocole est requise à deux niveaux : entre les applications et entre les gestionnaires de transactions (consultez la figure suivante).</span><span class="sxs-lookup"><span data-stu-id="0aabe-117">Interoperability on these protocol specifications is required at two levels: between applications and between transaction managers (see the following figure).</span></span> <span data-ttu-id="0aabe-118">Les spécifications décrivent de manière très détaillée les formats de message et l'échange de messages pour les deux niveaux d'interopérabilité.</span><span class="sxs-lookup"><span data-stu-id="0aabe-118">Specifications describe in great detail the message formats and message exchange for both interoperability levels.</span></span> <span data-ttu-id="0aabe-119">Une certain niveau de sécurité, de fiabilité et des encodages pour l'échange interapplication s'appliquent de la même manière que pour l'échange entre applications normal.</span><span class="sxs-lookup"><span data-stu-id="0aabe-119">Certain security, reliability, and encodings for application-to-application exchange apply as they do for regular application exchange.</span></span> <span data-ttu-id="0aabe-120">Toutefois, l'interopérabilité réussie entre les gestionnaires de transactions requiert un contrat sur la liaison spécifique, car il n'est généralement pas configuré par l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="0aabe-120">However, successful interoperability between transaction managers requires agreement on the particular binding, because it is usually not configured by the user.</span></span>  
  
 <span data-ttu-id="0aabe-121">Cette rubrique décrit une composition de la spécification WS-AT (WS-Atomic Transaction) avec sécurité et décrit la liaison sécurisée utilisée pour la communication entre les gestionnaires de transactions.</span><span class="sxs-lookup"><span data-stu-id="0aabe-121">This topic describes a composition of the WS-Atomic Transaction (WS-AT) specification with security and describes the secure binding used for communication between transaction managers.</span></span> <span data-ttu-id="0aabe-122">L'approche décrite dans ce document a été testée avec succès avec d'autres implémentations de WS-AT et WS-Coordination, dont IBM, IONA, Sun Microsystems, etc.</span><span class="sxs-lookup"><span data-stu-id="0aabe-122">The approach described in this document has been successfully tested with other implementations of WS-AT and WS-Coordination including IBM, IONA, Sun Microsystems, and others.</span></span>  
  
 <span data-ttu-id="0aabe-123">La figure suivante représente l’interopérabilité entre deux gestionnaires de transactions (Gestionnaire de transactions 1 et Gestionnaire de transactions 2) et deux applications (Application 1 et Application 2).</span><span class="sxs-lookup"><span data-stu-id="0aabe-123">The following figure depicts the interoperability between two transaction managers, Transaction Manager 1 and Transaction Manager 2, and two applications, Application 1 and Application 2.</span></span>  
  
 <span data-ttu-id="0aabe-124">![Protocoles de transaction](../../../../docs/framework/wcf/feature-details/media/transactionmanagers.gif "TransactionManagers")</span><span class="sxs-lookup"><span data-stu-id="0aabe-124">![Transaction Protocols](../../../../docs/framework/wcf/feature-details/media/transactionmanagers.gif "TransactionManagers")</span></span>  
  
 <span data-ttu-id="0aabe-125">Examinons un scénario WS-Coordination/WS-Atomic Transaction classique avec un Initiateur (I) et un Participant (P).</span><span class="sxs-lookup"><span data-stu-id="0aabe-125">Consider a typical WS-Coordination/WS-Atomic Transaction scenario with one Initiator (I) and one Participant (P).</span></span> <span data-ttu-id="0aabe-126">L’Initiateur et le Participant ont des Gestionnaires de transactions (ITM et PTM, respectivement).</span><span class="sxs-lookup"><span data-stu-id="0aabe-126">Both Initiator and Participant have Transaction Managers, (ITM and PTM, respectively).</span></span> <span data-ttu-id="0aabe-127">La validation en deux phases est désignée sous le terme « 2PC » dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="0aabe-127">Two-phase commit is referred to as 2PC in this topic.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0aabe-128">1. CreateCoordinationContext</span><span class="sxs-lookup"><span data-stu-id="0aabe-128">1. CreateCoordinationContext</span></span>|<span data-ttu-id="0aabe-129">12. Réponse de message d'application</span><span class="sxs-lookup"><span data-stu-id="0aabe-129">12. Application Message Response</span></span>|  
|<span data-ttu-id="0aabe-130">2. CreateCoordinationContextResponse</span><span class="sxs-lookup"><span data-stu-id="0aabe-130">2. CreateCoordinationContextResponse</span></span>|<span data-ttu-id="0aabe-131">13. Commit (achèvement)</span><span class="sxs-lookup"><span data-stu-id="0aabe-131">13. Commit (Completion)</span></span>|  
|<span data-ttu-id="0aabe-132">3. Register (achèvement)</span><span class="sxs-lookup"><span data-stu-id="0aabe-132">3. Register (Completion)</span></span>|<span data-ttu-id="0aabe-133">14. Prepare (2PC)</span><span class="sxs-lookup"><span data-stu-id="0aabe-133">14. Prepare (2PC)</span></span>|  
|<span data-ttu-id="0aabe-134">4. RegisterResponse</span><span class="sxs-lookup"><span data-stu-id="0aabe-134">4. RegisterResponse</span></span>|<span data-ttu-id="0aabe-135">15. Prepare (2PC)</span><span class="sxs-lookup"><span data-stu-id="0aabe-135">15. Prepare (2PC)</span></span>|  
|<span data-ttu-id="0aabe-136">5. Message d'application</span><span class="sxs-lookup"><span data-stu-id="0aabe-136">5. Application Message</span></span>|<span data-ttu-id="0aabe-137">16. Prepared (2PC)</span><span class="sxs-lookup"><span data-stu-id="0aabe-137">16. Prepared (2PC)</span></span>|  
|<span data-ttu-id="0aabe-138">6. CreateCoordinationContext avec Context</span><span class="sxs-lookup"><span data-stu-id="0aabe-138">6. CreateCoordinationContext with Context</span></span>|<span data-ttu-id="0aabe-139">17. Prepared (2PC)</span><span class="sxs-lookup"><span data-stu-id="0aabe-139">17. Prepared (2PC)</span></span>|  
|<span data-ttu-id="0aabe-140">7. Register (durable)</span><span class="sxs-lookup"><span data-stu-id="0aabe-140">7. Register (Durable)</span></span>|<span data-ttu-id="0aabe-141">18. Committed (achèvement)</span><span class="sxs-lookup"><span data-stu-id="0aabe-141">18. Committed (Completion)</span></span>|  
|<span data-ttu-id="0aabe-142">8. RegisterResponse</span><span class="sxs-lookup"><span data-stu-id="0aabe-142">8. RegisterResponse</span></span>|<span data-ttu-id="0aabe-143">19. Commit (2PC)</span><span class="sxs-lookup"><span data-stu-id="0aabe-143">19. Commit (2PC)</span></span>|  
|<span data-ttu-id="0aabe-144">9. CreateCoordinationContextResponse</span><span class="sxs-lookup"><span data-stu-id="0aabe-144">9. CreateCoordinationContextResponse</span></span>|<span data-ttu-id="0aabe-145">20. Commit (2PC)</span><span class="sxs-lookup"><span data-stu-id="0aabe-145">20. Commit (2PC)</span></span>|  
|<span data-ttu-id="0aabe-146">10. Register (durable)</span><span class="sxs-lookup"><span data-stu-id="0aabe-146">10. Register (Durable)</span></span>|<span data-ttu-id="0aabe-147">21. Committed (2PC)</span><span class="sxs-lookup"><span data-stu-id="0aabe-147">21. Committed (2PC)</span></span>|  
|<span data-ttu-id="0aabe-148">11. RegisterResponse</span><span class="sxs-lookup"><span data-stu-id="0aabe-148">11. RegisterResponse</span></span>|<span data-ttu-id="0aabe-149">22. Committed (2PC)</span><span class="sxs-lookup"><span data-stu-id="0aabe-149">22. Committed (2PC)</span></span>|  
  
 <span data-ttu-id="0aabe-150">Ce document décrit une composition de la spécification WS-AtomicTransaction avec sécurité et décrit la liaison sécurisée utilisée pour la communication entre les gestionnaires de transactions.</span><span class="sxs-lookup"><span data-stu-id="0aabe-150">This document describes a composition of the WS-AtomicTransaction specification with security and describes the secure binding used for communication between transaction managers.</span></span> <span data-ttu-id="0aabe-151">L'approche décrite dans ce document a été testée avec succès avec d'autres implémentations de WS-AT et WS-Coordination.</span><span class="sxs-lookup"><span data-stu-id="0aabe-151">The approach described in this document has been successfully tested with other implementations of WS-AT and WS-Coordination.</span></span>  
  
 <span data-ttu-id="0aabe-152">La figure et le tableau présentent quatre classes de messages du point de vue de sécurité :</span><span class="sxs-lookup"><span data-stu-id="0aabe-152">The figure and table illustrate four classes of messages from the viewpoint of security:</span></span>  
  
-   <span data-ttu-id="0aabe-153">Messages d'activation (CreateCoordinationContext et CreateCoordinationContextResponse).</span><span class="sxs-lookup"><span data-stu-id="0aabe-153">Activation messages (CreateCoordinationContext and CreateCoordinationContextResponse).</span></span>  
  
-   <span data-ttu-id="0aabe-154">Messages d'inscription (Register et RegisterResponse)</span><span class="sxs-lookup"><span data-stu-id="0aabe-154">Registration messages (Register and RegisterResponse)</span></span>  
  
-   <span data-ttu-id="0aabe-155">Messages de protocole (Prepare, Rollback, Commit, Aborted, etc).</span><span class="sxs-lookup"><span data-stu-id="0aabe-155">Protocol messages (Prepare, Rollback, Commit, Aborted, and so on).</span></span>  
  
-   <span data-ttu-id="0aabe-156">Messages d'application</span><span class="sxs-lookup"><span data-stu-id="0aabe-156">Application messages.</span></span>  
  
 <span data-ttu-id="0aabe-157">Les trois premières classes de message sont considérées comme des messages de gestionnaire de transactions et leur configuration de liaison est décrite dans la section « Échange de messages d'application » développée ultérieurement dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="0aabe-157">The first three message classes are considered Transaction Manager messages and their binding configuration is described in the "Application Message Exchange" later in this topic.</span></span> <span data-ttu-id="0aabe-158">La quatrième classe de message concerne les messages interapplication et est décrite dans la section « Exemples de message » développée ultérieurement dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="0aabe-158">The fourth class of message is application to application messages and is described in the "Message Examples" section later in this topic.</span></span> <span data-ttu-id="0aabe-159">Cette section décrit les liaisons de protocole utilisées pour chacune de ces classes par [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0aabe-159">This section describes the protocol bindings used for each of these classes by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
 <span data-ttu-id="0aabe-160">Les espaces de noms XML suivants et préfixes associés sont utilisés dans l'ensemble de ce document.</span><span class="sxs-lookup"><span data-stu-id="0aabe-160">The following XML Namespaces and associated prefixes are used throughout this document.</span></span>  
  
|<span data-ttu-id="0aabe-161">Préfixe</span><span class="sxs-lookup"><span data-stu-id="0aabe-161">Prefix</span></span>|<span data-ttu-id="0aabe-162">Version</span><span class="sxs-lookup"><span data-stu-id="0aabe-162">Version</span></span>|<span data-ttu-id="0aabe-163">URI d'espace de noms</span><span class="sxs-lookup"><span data-stu-id="0aabe-163">Namespace URI</span></span>|  
|------------|-------------|-------------------|  
|<span data-ttu-id="0aabe-164">s11</span><span class="sxs-lookup"><span data-stu-id="0aabe-164">s11</span></span>||[<span data-ttu-id="0aabe-165">http://go.Microsoft.com/fwlink/?LinkId=96014</span><span class="sxs-lookup"><span data-stu-id="0aabe-165">http://go.microsoft.com/fwlink/?LinkId=96014</span></span>](http://go.microsoft.com/fwlink/?LinkId=96014)|  
|<span data-ttu-id="0aabe-166">wsa</span><span class="sxs-lookup"><span data-stu-id="0aabe-166">wsa</span></span>|<span data-ttu-id="0aabe-167">Pre-1.0</span><span class="sxs-lookup"><span data-stu-id="0aabe-167">Pre-1.0</span></span><br /><br /> <span data-ttu-id="0aabe-168">1.0</span><span class="sxs-lookup"><span data-stu-id="0aabe-168">1.0</span></span>|<span data-ttu-id="0aabe-169">http://www.w3.org/2004/08/Addressing</span><span class="sxs-lookup"><span data-stu-id="0aabe-169">http://www.w3.org/2004/08/addressing</span></span><br /><br /> [<span data-ttu-id="0aabe-170">http://go.Microsoft.com/fwlink/?LinkId=96022</span><span class="sxs-lookup"><span data-stu-id="0aabe-170">http://go.microsoft.com/fwlink/?LinkId=96022</span></span>](http://go.microsoft.com/fwlink/?LinkId=96022)|  
|<span data-ttu-id="0aabe-171">wscoor</span><span class="sxs-lookup"><span data-stu-id="0aabe-171">wscoor</span></span>|<span data-ttu-id="0aabe-172">1.0</span><span class="sxs-lookup"><span data-stu-id="0aabe-172">1.0</span></span><br /><br /> <span data-ttu-id="0aabe-173">1.1</span><span class="sxs-lookup"><span data-stu-id="0aabe-173">1.1</span></span>|[<span data-ttu-id="0aabe-174">http://go.Microsoft.com/fwlink/?LinkId=96078</span><span class="sxs-lookup"><span data-stu-id="0aabe-174">http://go.microsoft.com/fwlink/?LinkId=96078</span></span>](http://go.microsoft.com/fwlink/?LinkId=96078)<br /><br /> [<span data-ttu-id="0aabe-175">http://go.Microsoft.com/fwlink/?LinkId=96079</span><span class="sxs-lookup"><span data-stu-id="0aabe-175">http://go.microsoft.com/fwlink/?LinkId=96079</span></span>](http://go.microsoft.com/fwlink/?LinkId=96079)|  
|<span data-ttu-id="0aabe-176">wsat</span><span class="sxs-lookup"><span data-stu-id="0aabe-176">wsat</span></span>|<span data-ttu-id="0aabe-177">1.0</span><span class="sxs-lookup"><span data-stu-id="0aabe-177">1.0</span></span><br /><br /> <span data-ttu-id="0aabe-178">1.1</span><span class="sxs-lookup"><span data-stu-id="0aabe-178">1.1</span></span>|[<span data-ttu-id="0aabe-179">http://go.Microsoft.com/fwlink/?LinkId=96080</span><span class="sxs-lookup"><span data-stu-id="0aabe-179">http://go.microsoft.com/fwlink/?LinkId=96080</span></span>](http://go.microsoft.com/fwlink/?LinkId=96080)<br /><br /> [<span data-ttu-id="0aabe-180">http://go.Microsoft.com/fwlink/?LinkId=96081</span><span class="sxs-lookup"><span data-stu-id="0aabe-180">http://go.microsoft.com/fwlink/?LinkId=96081</span></span>](http://go.microsoft.com/fwlink/?LinkId=96081)|  
|<span data-ttu-id="0aabe-181">t</span><span class="sxs-lookup"><span data-stu-id="0aabe-181">t</span></span>|<span data-ttu-id="0aabe-182">Pre-1.3</span><span class="sxs-lookup"><span data-stu-id="0aabe-182">Pre-1.3</span></span><br /><br /> <span data-ttu-id="0aabe-183">1.3</span><span class="sxs-lookup"><span data-stu-id="0aabe-183">1.3</span></span>|[<span data-ttu-id="0aabe-184">http://go.Microsoft.com/fwlink/?LinkId=96082</span><span class="sxs-lookup"><span data-stu-id="0aabe-184">http://go.microsoft.com/fwlink/?LinkId=96082</span></span>](http://go.microsoft.com/fwlink/?LinkId=96082)<br /><br /> [<span data-ttu-id="0aabe-185">http://go.Microsoft.com/fwlink/?LinkId=96100</span><span class="sxs-lookup"><span data-stu-id="0aabe-185">http://go.microsoft.com/fwlink/?LinkId=96100</span></span>](http://go.microsoft.com/fwlink/?LinkId=96100)|  
|<span data-ttu-id="0aabe-186">o</span><span class="sxs-lookup"><span data-stu-id="0aabe-186">o</span></span>||[<span data-ttu-id="0aabe-187">http://go.Microsoft.com/fwlink/?LinkId=96101</span><span class="sxs-lookup"><span data-stu-id="0aabe-187">http://go.microsoft.com/fwlink/?LinkId=96101</span></span>](http://go.microsoft.com/fwlink/?LinkId=96101)|  
|<span data-ttu-id="0aabe-188">xsd</span><span class="sxs-lookup"><span data-stu-id="0aabe-188">xsd</span></span>||[<span data-ttu-id="0aabe-189">http://go.Microsoft.com/fwlink/?LinkId=96102</span><span class="sxs-lookup"><span data-stu-id="0aabe-189">http://go.microsoft.com/fwlink/?LinkId=96102</span></span>](http://go.microsoft.com/fwlink/?LinkId=96102)|  
  
## <a name="transaction-manager-bindings"></a><span data-ttu-id="0aabe-190">Liaisons de gestionnaire de transactions</span><span class="sxs-lookup"><span data-stu-id="0aabe-190">Transaction Manager Bindings</span></span>  
 <span data-ttu-id="0aabe-191">R1001 : Les gestionnaires de transactions participant à une transaction WS-AT 1.0 doivent utiliser SOAP 1.1 et WS-Addressing 2004/08 pour WS-Atomic Transaction et les échanges de messages WS-Coordination.</span><span class="sxs-lookup"><span data-stu-id="0aabe-191">R1001: Transaction Managers participating in a WS-AT 1.0 transaction must use SOAP 1.1 and WS-Addressing 2004/08 for WS-Atomic Transaction and WS-Coordination message exchanges.</span></span>  
  
 <span data-ttu-id="0aabe-192">R1002 : les gestionnaires de transactions qui participent à une transaction WS-AT 1.1 doivent utiliser SOAP 1.1 et WS-Addressing 2005/08 pour les échanges WS-Atomic Transaction et WS-Coordination.</span><span class="sxs-lookup"><span data-stu-id="0aabe-192">R1002: Transaction Managers participating in a WS-AT 1.1 transaction must use SOAP 1.1 and WS-Addressing 2005/08 for WS-Atomic Transaction and WS-Coordination message exchanges.</span></span>  
  
 <span data-ttu-id="0aabe-193">Les messages d’application ne sont pas contraints à ces liaisons et sont décrits ultérieurement.</span><span class="sxs-lookup"><span data-stu-id="0aabe-193">Application messages are not constrained to these bindings and are described later.</span></span>  
  
### <a name="transaction-manager-https-binding"></a><span data-ttu-id="0aabe-194">Liaison HTTPS de gestionnaire de transactions</span><span class="sxs-lookup"><span data-stu-id="0aabe-194">Transaction Manager HTTPS Binding</span></span>  
 <span data-ttu-id="0aabe-195">La liaison HTTPS de gestionnaire de transactions s'appuie uniquement sur le transport de sécurité pour assurer la sécurité et établir la confiance entre chaque paire expéditeur-récepteur dans l'arborescence de transactions.</span><span class="sxs-lookup"><span data-stu-id="0aabe-195">The transaction manager HTTPS binding relies solely on transport security to achieve security and establish trust between each sender-receiver pair in the transaction tree.</span></span>  
  
#### <a name="https-transport-configuration"></a><span data-ttu-id="0aabe-196">Configuration du transport HTTPS</span><span class="sxs-lookup"><span data-stu-id="0aabe-196">HTTPS Transport Configuration</span></span>  
 <span data-ttu-id="0aabe-197">Les certificats X.509 permettent d'établir l'identité de gestionnaire de transactions.</span><span class="sxs-lookup"><span data-stu-id="0aabe-197">X.509 certificates are used to establish Transaction Manager Identity.</span></span> <span data-ttu-id="0aabe-198">L'authentification client/serveur est requise, et l'autorisation client/serveur est considérée comme un détail d'implémentation :</span><span class="sxs-lookup"><span data-stu-id="0aabe-198">Client/server authentication is required, and client/server authorization is left as an implementation detail:</span></span>  
  
-   <span data-ttu-id="0aabe-199">R1111 : les certificats X.509 présentés sur le câble doivent avoir un nom de sujet qui correspond au nom de domaine complet de l'ordinateur d'origine.</span><span class="sxs-lookup"><span data-stu-id="0aabe-199">R1111: X.509 certificates presented over the wire must have a subject name that matches the fully qualified domain name (FQDN) of the originating machine.</span></span>  
  
-   <span data-ttu-id="0aabe-200">B1112 : le DNS doit être fonctionnel entre chaque paire expéditeur-récepteur du système pour que les vérifications du nom de sujet X.509 réussissent.</span><span class="sxs-lookup"><span data-stu-id="0aabe-200">B1112: DNS must be functional between each sender-receiver pair in the system for X.509 subject name checks to succeed.</span></span>  
  
#### <a name="activation-and-registration-binding-configuration"></a><span data-ttu-id="0aabe-201">Configuration de liaison d'activation et d'inscription</span><span class="sxs-lookup"><span data-stu-id="0aabe-201">Activation and Registration Binding Configuration</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="0aabe-202"> requiert une liaison duplex demande/réponse avec corrélation sur HTTPS.</span><span class="sxs-lookup"><span data-stu-id="0aabe-202"> requires request/reply duplex binding with correlation over HTTPS.</span></span> <span data-ttu-id="0aabe-203">(Pour plus d'informations sur la corrélation et les descriptions des modèles d'échange de messages demande/réponse, consultez WS-Atomic Transaction, section 8.)</span><span class="sxs-lookup"><span data-stu-id="0aabe-203">(For more information about correlation and descriptions of the request/reply message exchange patterns, see WS-Atomic Transaction, Section 8.)</span></span>  
  
#### <a name="2pc-protocol-binding-configuration"></a><span data-ttu-id="0aabe-204">Configuration de liaison de protocole 2PC</span><span class="sxs-lookup"><span data-stu-id="0aabe-204">2PC Protocol Binding Configuration</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="0aabe-205"> prend en charge des messages monodirectionnels (datagramme) sur HTTPS.</span><span class="sxs-lookup"><span data-stu-id="0aabe-205"> supports one-way (datagram) messages over HTTPS.</span></span> <span data-ttu-id="0aabe-206">La corrélation au sein des messages est considérée comme un détail d'implémentation.</span><span class="sxs-lookup"><span data-stu-id="0aabe-206">Correlation among the messages is left as an implementation detail.</span></span>  
  
 <span data-ttu-id="0aabe-207">B1131 : Les implémentations doivent prendre en charge `wsa:ReferenceParameters` comme décrit dans WS-Addressing pour la corrélation de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]de messages 2PC.</span><span class="sxs-lookup"><span data-stu-id="0aabe-207">B1131: Implementations must support `wsa:ReferenceParameters` as described in WS-Addressing to achieve correlation of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]’s 2PC messages.</span></span>  
  
### <a name="transaction-manager-mixed-security-binding"></a><span data-ttu-id="0aabe-208">Liaison de sécurité mixte de gestionnaire de transactions</span><span class="sxs-lookup"><span data-stu-id="0aabe-208">Transaction Manager Mixed Security Binding</span></span>  
 <span data-ttu-id="0aabe-209">Cette autre liaison (mode mixte) utilise le transport de sécurité combiné avec le modèle WS-Coordination Issued Token à des fins d'établissement d'identité.</span><span class="sxs-lookup"><span data-stu-id="0aabe-209">This is an alternate (mixed mode) binding that uses transport security combined with the WS-Coordination Issued Token model for identity establishment purposes.</span></span> <span data-ttu-id="0aabe-210">L’activation et l’inscription sont les seuls éléments qui diffèrent entre les deux liaisons.</span><span class="sxs-lookup"><span data-stu-id="0aabe-210">Activation and Registration are the only elements that differ between the two bindings.</span></span>  
  
#### <a name="https-transport-configuration"></a><span data-ttu-id="0aabe-211">Configuration du transport HTTPS</span><span class="sxs-lookup"><span data-stu-id="0aabe-211">HTTPS Transport Configuration</span></span>  
 <span data-ttu-id="0aabe-212">Les certificats X.509 permettent d’établir l’identité de gestionnaire de transactions.</span><span class="sxs-lookup"><span data-stu-id="0aabe-212">X.509 certificates are used to establish Transaction Manager Identity.</span></span> <span data-ttu-id="0aabe-213">L'authentification client/serveur est requise, et l'autorisation client/serveur est considérée comme un détail d'implémentation.</span><span class="sxs-lookup"><span data-stu-id="0aabe-213">Client/Server authentication is required, and client/server authorization is left as an implementation detail.</span></span>  
  
#### <a name="activation-message-binding-configuration"></a><span data-ttu-id="0aabe-214">Configuration de liaison de message d’activation</span><span class="sxs-lookup"><span data-stu-id="0aabe-214">Activation Message Binding Configuration</span></span>  
 <span data-ttu-id="0aabe-215">En général, les messages d’activation ne participent pas à l’interopérabilité car ils se produisent habituellement entre une application et son gestionnaire de transactions local.</span><span class="sxs-lookup"><span data-stu-id="0aabe-215">Activation Messages usually do not participate in interoperability because they typically occur between an application and its local Transaction Manager.</span></span>  
  
 <span data-ttu-id="0aabe-216">B1221 : [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] utilise la liaison HTTPS duplex (décrit dans [protocoles de messagerie](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)) pour les messages d’Activation.</span><span class="sxs-lookup"><span data-stu-id="0aabe-216">B1221: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uses duplex HTTPS binding (described in [Messaging Protocols](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)) for Activation messages.</span></span> <span data-ttu-id="0aabe-217">Les messages de demande et de réponse sont corrélés à l'aide de WS-Addressing 2004/08 pour WS-AT 1.0 et WS-Addressing 2005/08 pour WS-AT 1.1.</span><span class="sxs-lookup"><span data-stu-id="0aabe-217">Request and Reply messages are correlated using WS-Addressing 2004/08 for WS-AT 1.0 and WS-Addressing 2005/08 for WS-AT 1.1.</span></span>  
  
 <span data-ttu-id="0aabe-218">La spécification WS-Atomic Transaction, section 8, fournit des informations supplémentaires sur la corrélation et les modèles d'échange de messages.</span><span class="sxs-lookup"><span data-stu-id="0aabe-218">WS-Atomic Transaction specification, Section 8, describes further details about correlation and the message exchange patterns.</span></span>  
  
-   <span data-ttu-id="0aabe-219">R1222 : après réception de `CreateCoordinationContext`, le coordinateur doit émettre `SecurityContextToken` avec le `STx` secret associé.</span><span class="sxs-lookup"><span data-stu-id="0aabe-219">R1222: Upon receiving a `CreateCoordinationContext`, the Coordinator must issue a `SecurityContextToken` with associated secret `STx`.</span></span> <span data-ttu-id="0aabe-220">Ce jeton est retourné à l'intérieur d'un en-tête `t:IssuedTokens` selon la spécification WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="0aabe-220">This token is returned inside a `t:IssuedTokens` header following WS-Trust specification.</span></span>  
  
-   <span data-ttu-id="0aabe-221">R1223 : si l'activation se produit dans un contexte de coordination existant, l'en-tête `t:IssuedTokens` avec `SecurityContextToken` associé au contexte existant doit transmettre sur le message `CreateCoordinationContext`.</span><span class="sxs-lookup"><span data-stu-id="0aabe-221">R1223: If Activation occurs within an existing Coordination Context, the `t:IssuedTokens` header with the `SecurityContextToken` associated with existing Context must flow on the `CreateCoordinationContext` message.</span></span>  
  
 <span data-ttu-id="0aabe-222">Un nouveau `t:IssuedTokens` en-tête doit être généré pour l’attachement à sortant `wscoor:CreateCoordinationContextResponse` message.</span><span class="sxs-lookup"><span data-stu-id="0aabe-222">A new `t:IssuedTokens` header should be generated for attaching to the outgoing `wscoor:CreateCoordinationContextResponse` message.</span></span>  
  
#### <a name="registration-message-binding-configuration"></a><span data-ttu-id="0aabe-223">Configuration de liaison de message d’inscription</span><span class="sxs-lookup"><span data-stu-id="0aabe-223">Registration Message Binding Configuration</span></span>  
 <span data-ttu-id="0aabe-224">B1231 : [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] utilise la liaison HTTPS duplex (décrit dans [protocoles de messagerie](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)).</span><span class="sxs-lookup"><span data-stu-id="0aabe-224">B1231: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uses duplex HTTPS binding (described in [Messaging Protocols](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)).</span></span> <span data-ttu-id="0aabe-225">Les messages de demande et de réponse sont corrélés à l'aide de WS-Addressing 2004/08 pour WS-AT 1.0 et WS-Addressing 2005/08 pour WS-AT 1.1.</span><span class="sxs-lookup"><span data-stu-id="0aabe-225">Request and Reply messages are correlated using WS-Addressing 2004/08 for WS-AT 1.0 and WS-Addressing 2005/08 for WS-AT 1.1.</span></span>  
  
 <span data-ttu-id="0aabe-226">WS-AtomicTransaction, section 8, fournit des informations supplémentaires sur la corrélation et des descriptions des modèles d’échange de messages.</span><span class="sxs-lookup"><span data-stu-id="0aabe-226">WS-AtomicTransaction, Section 8, describes further details about correlation and descriptions of the message exchange patterns.</span></span>  
  
 <span data-ttu-id="0aabe-227">R1232 : Sortant `wscoor:Register` messages doivent utiliser le `IssuedTokenOverTransport` mode d’authentification décrits dans [protocoles de sécurité](../../../../docs/framework/wcf/feature-details/security-protocols.md).</span><span class="sxs-lookup"><span data-stu-id="0aabe-227">R1232: Outgoing `wscoor:Register` messages must use the `IssuedTokenOverTransport` authentication mode described in [Security Protocols](../../../../docs/framework/wcf/feature-details/security-protocols.md).</span></span>  
  
 <span data-ttu-id="0aabe-228">Le `wsse:Timestamp` élément doit être signé à l’aide de la `SecurityContextToken``STx` émis.</span><span class="sxs-lookup"><span data-stu-id="0aabe-228">The `wsse:Timestamp` element must be signed using the `SecurityContextToken``STx` issued.</span></span> <span data-ttu-id="0aabe-229">Cette signature est une preuve de possession du jeton associée à une transaction spécifique et est utilisée pour authentifier un participant qui s’inscrit à la transaction.</span><span class="sxs-lookup"><span data-stu-id="0aabe-229">This signature is a proof of possession of the token associated with particular transaction and is used to authenticate a participant enlisting in the transaction.</span></span> <span data-ttu-id="0aabe-230">Le message RegistrationResponse est renvoyé sur HTTPS.</span><span class="sxs-lookup"><span data-stu-id="0aabe-230">The RegistrationResponse message is sent back over HTTPS.</span></span>  
  
#### <a name="2pc-protocol-binding-configuration"></a><span data-ttu-id="0aabe-231">Configuration de liaison de protocole 2PC</span><span class="sxs-lookup"><span data-stu-id="0aabe-231">2PC Protocol Binding Configuration</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="0aabe-232"> prend en charge des messages monodirectionnels (datagramme) sur HTTPS.</span><span class="sxs-lookup"><span data-stu-id="0aabe-232"> supports one-way (datagram) messages over HTTPS.</span></span> <span data-ttu-id="0aabe-233">La corrélation au sein des messages est considérée comme un détail d'implémentation.</span><span class="sxs-lookup"><span data-stu-id="0aabe-233">Correlation among the messages is left as an implementation detail.</span></span>  
  
 <span data-ttu-id="0aabe-234">B1241 : les implémentations doivent prendre en charge `wsa:ReferenceParameters`, tel que décrit dans WS-Addressing pour assurer la corrélation des messages 2PC de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0aabe-234">B1241: Implementations must support `wsa:ReferenceParameters` as described in WS-Addressing to achieve correlation of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]’s 2PC messages.</span></span>  
  
## <a name="application-message-exchange"></a><span data-ttu-id="0aabe-235">Échange de messages d'application</span><span class="sxs-lookup"><span data-stu-id="0aabe-235">Application Message Exchange</span></span>  
 <span data-ttu-id="0aabe-236">Les applications sont libres d'utiliser n'importe quelle liaison spécifique pour les messages interapplication, tant que la liaison satisfait aux conditions de sécurité suivantes :</span><span class="sxs-lookup"><span data-stu-id="0aabe-236">Applications are free to use any particular binding for application-to-application messages, as long as the binding meets the following security requirements:</span></span>  
  
-   <span data-ttu-id="0aabe-237">R2001 : les messages interapplication doivent transmettre l'en-tête `t:IssuedTokens` avec `CoordinationContext` dans l'en-tête du message.</span><span class="sxs-lookup"><span data-stu-id="0aabe-237">R2001: Application-to-application messages must flow the `t:IssuedTokens` header along with the `CoordinationContext` in the header of the message.</span></span>  
  
-   <span data-ttu-id="0aabe-238">R2002 : l'intégrité et la confidentialité de `t:IssuedToken` doivent être assurées.</span><span class="sxs-lookup"><span data-stu-id="0aabe-238">R2002: Integrity and confidentiality of `t:IssuedToken` must be provided.</span></span>  
  
 <span data-ttu-id="0aabe-239">L'en-tête `CoordinationContext` contient `wscoor:Identifier`.</span><span class="sxs-lookup"><span data-stu-id="0aabe-239">The `CoordinationContext` header contains `wscoor:Identifier`.</span></span> <span data-ttu-id="0aabe-240">Alors que la définition de `xsd:AnyURI` permet d'utiliser des URI absolus et relatifs, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] prend uniquement en charge `wscoor:Identifiers`, qui sont des URI absolus.</span><span class="sxs-lookup"><span data-stu-id="0aabe-240">While the definition of `xsd:AnyURI` allows the use of both absolute and relative URIs, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] supports only `wscoor:Identifiers`, which are absolute URIs.</span></span>  
  
 <span data-ttu-id="0aabe-241">B2003 : si `wscoor:Identifier` de `wscoor:CoordinationContext` est un URI relatif, les erreurs seront retournées par les services [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] transactionnels.</span><span class="sxs-lookup"><span data-stu-id="0aabe-241">B2003: If the `wscoor:Identifier` of the `wscoor:CoordinationContext` is a relative URI, faults will be returned from transactional [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services.</span></span>  
  
## <a name="message-examples"></a><span data-ttu-id="0aabe-242">Exemples de message</span><span class="sxs-lookup"><span data-stu-id="0aabe-242">Message Examples</span></span>  
  
### <a name="createcoordinationcontext-requestresponse-messages"></a><span data-ttu-id="0aabe-243">Messages de demande/réponse CreateCoordinationContext</span><span class="sxs-lookup"><span data-stu-id="0aabe-243">CreateCoordinationContext Request/Response Messages</span></span>  
 <span data-ttu-id="0aabe-244">Les messages suivants suivent un modèle de demande/réponse.</span><span class="sxs-lookup"><span data-stu-id="0aabe-244">The following messages follow a request/response pattern.</span></span>  
  
#### <a name="createcoordinationcontext-with-wscoor-10"></a><span data-ttu-id="0aabe-245">CreateCoordinationContext avec WSCoor 1.0</span><span class="sxs-lookup"><span data-stu-id="0aabe-245">CreateCoordinationContext with WSCoor 1.0</span></span>  
  
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
  
#### <a name="createcoordinationcontext-with-wscoor-11"></a><span data-ttu-id="0aabe-246">CreateCoordinationContext avec WSCoor 1.1</span><span class="sxs-lookup"><span data-stu-id="0aabe-246">CreateCoordinationContext with WSCoor 1.1</span></span>  
  
```xml  
<s:Envelope>   
<s:Header>  
<a:Action>http://docs.oasis-open.org/ws-tx/wscoor/2006/06/CreateCoordinationContext</Action>  
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
  
#### <a name="createcoordinationcontextresponse-with-trust-pre-13-and-wscoor-10"></a><span data-ttu-id="0aabe-247">CreateCoordinationContextResponse avec Trust Pre-1.3 et WSCoor 1.0</span><span class="sxs-lookup"><span data-stu-id="0aabe-247">CreateCoordinationContextResponse with Trust Pre-1.3 and WSCoor 1.0</span></span>  
  
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
  
#### <a name="createcoordinationcontextresponse-with-trust-13-and-wscoor-11"></a><span data-ttu-id="0aabe-248">CreateCoordinationContextResponse avec Trust 1.3 et WSCoor 1.1</span><span class="sxs-lookup"><span data-stu-id="0aabe-248">CreateCoordinationContextResponse with Trust 1.3 and WSCoor 1.1</span></span>  
  
```xml  
<s:Envelope>  
<!-- Data below is shown in the clear for illustration purposes only. -->   
<s:Header>   
<a:Action>http://docs.oasis-open.org/ws-tx/wscoor/2006/06/CreateCoordinationContextResponse </a:Action>  
<a:RelatesTo>urn:uuid:069f5104-fd88-4264-9f99-60032a82854e</a:RelatesTo>  
<a:To s:mustUnderstand="1">https://... </a:To>   
<t:IssuedTokens>   
<wst:RequestSecurityTokenResponse   
xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"   
xmlns:wssu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-     wssecurity-utility-1.0.xsd"   
xmlns:wst=http://docs.oasis-open.org/ws-sx/ws-trust/200512  
xmlns:wsc=http://schemas.xmlsoap.org/ws/2005/02/sc  
xmlns:wsp="http://schemas.xmlsoap.org/ws/2004/09/policy">  
<wst:TokenType>http://schemas.xmlsoap.org/ws/2005/02/sc/sct</wst:TokenType>  
<wst:RequestedSecurityToken>   
<wsc:SecurityContextToken>   
<wssu:Identifier> http://fabrikam123.com/SCTi  
</wssu:Identifier>   
</wsc:SecurityContextToken>   
</wst:RequestedSecurityToken>   
<wsp:AppliesTo> http://fabrikam123.com/CCi </wsp:AppliesTo>  
<wst:RequestedAttachedReference>   
<wsse:SecurityTokenReference >   
<wsse:Reference  
  ValueType=http://schemas.xmlsoap.org/ws/2005/02/sc/sct  
  URI="http://fabrikam123.com/SCTi"/>  
</wsse:SecurityTokenReference>   
</wst:RequestedAttachedReference>   
<wst:RequestedUnattachedReference>   
<wsse:SecurityTokenReference>   
<wsse:Reference  
 ValueType=http://schemas.xmlsoap.org/ws/2005/02/sc/sct  
 URI="http://fabrikam123.com/SCTi"/>  
</wsse:SecurityTokenReference>   
</wst:RequestedUnattachedReference>   
<wst:RequestedProofToken>   
<wst:BinarySecret  
  Type="http://docs.oasis-open.org/ws-sx/ws-trust/200512/SymmetricKey">  
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
<wscoor:Identifier> http://fabrikam123.com/CCi  
</wscoor:Identifier>   
<wscoor:Expires>...</wscoor:Expires>  
<wscoor:CoordinationType>...</wscoor:CoordinationType>  
<wscoor:RegistrationService>   
<a:Address>https://...</a:Address>  
<a:ReferenceParameters> ...  
</a:ReferenceParameters>  
</wscoor:RegistrationService>   
</wscoor:CoordinationContext>   
</wscoor:CreateCoordinationContextResponse>   
</s:Body>   
</s:Envelope>  
```  
  
### <a name="registration-messages"></a><span data-ttu-id="0aabe-249">Messages d'inscription</span><span class="sxs-lookup"><span data-stu-id="0aabe-249">Registration Messages</span></span>  
 <span data-ttu-id="0aabe-250">Les messages suivants sont des messages d'inscription.</span><span class="sxs-lookup"><span data-stu-id="0aabe-250">The following messages are registration messages.</span></span>  
  
#### <a name="register-with-wscoor-10"></a><span data-ttu-id="0aabe-251">Register avec WSCoor 1.0</span><span class="sxs-lookup"><span data-stu-id="0aabe-251">Register with WSCoor 1.0</span></span>  
  
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
  
#### <a name="register-with-wscoor-11"></a><span data-ttu-id="0aabe-252">Register avec WSCoor 1.1</span><span class="sxs-lookup"><span data-stu-id="0aabe-252">Register with WSCoor 1.1</span></span>  
  
```xml  
<s:Envelope>  
<s:Header>   
<a:Action>http://docs.oasis-open.org/ws-tx/wscoor/2006/06/Register</a:Action>   
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
<wssu:Identifier> http://fabrikam123.com/SCTi  
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
<ds:DigestMethod  
Algorithm="http://www.w3.org/2000/09/xmldsig#sha1"/>   
<ds:DigestValue> alRzyhjLgoUOYoh8cx4n75eTcUk=  
</ds:DigestValue>   
</ds:Reference>   
</ds:SignedInfo>  
<ds:SignatureValue>YZYjnVvSOVasAQqQxaaviTSWtqI=  
</ds:SignatureValue>  
<ds:KeyInfo>   
<wsse:SecurityTokenReference xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">  
  <wsse:Reference URI="http://fabrikam123.com/SCTi"/>  
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
  
#### <a name="register-response-with-wscoor-10"></a><span data-ttu-id="0aabe-253">Register Response avec WSCoor 1.0</span><span class="sxs-lookup"><span data-stu-id="0aabe-253">Register Response with WSCoor 1.0</span></span>  
  
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
  
#### <a name="register-response-with-wscoor-11"></a><span data-ttu-id="0aabe-254">Register Response avec WSCoor 1.1</span><span class="sxs-lookup"><span data-stu-id="0aabe-254">Register Response with WSCoor 1.1</span></span>  
  
```xml  
<s:Envelope>  
<s:Header>   
<a:Action> http://docs.oasis-open.org/ws-tx/wscoor/2006/06/RegisterResponse  
</a:Action>   
<a:MessageID>urn:uuid:ed418b86-a75e-4aea-9d4e-a5d0cb5c088d</a:MessageID>  
<a:RelatesTo> urn:uuid:ed418b86-a75e-4aea-9d4e-a5d0cb5c088e </a:RelatesTo>  
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
<a:ReferenceParameters> ... </a:ReferenceParameters>  
</wscoor:CoordinatorProtocolService>   
</wscoor:RegisterResponse>   
</s:Body>   
</s:Envelope>  
```  
  
### <a name="two-phase-commit-protocol-messages"></a><span data-ttu-id="0aabe-255">Messages de protocole de validation à deux phases</span><span class="sxs-lookup"><span data-stu-id="0aabe-255">Two Phase Commit Protocol Messages</span></span>  
 <span data-ttu-id="0aabe-256">Le message suivant concerne le protocole de validation en deux phases (2PC).</span><span class="sxs-lookup"><span data-stu-id="0aabe-256">The following message relates to the two-phase commit (2PC) protocol.</span></span>  
  
#### <a name="commit-with-wsat-10"></a><span data-ttu-id="0aabe-257">COMMIT avec WSAT 1.0</span><span class="sxs-lookup"><span data-stu-id="0aabe-257">Commit with WSAT 1.0</span></span>  
  
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
  
#### <a name="commit-with-wsat-11"></a><span data-ttu-id="0aabe-258">Commit avec WSAT 1.1</span><span class="sxs-lookup"><span data-stu-id="0aabe-258">Commit with WSAT 1.1</span></span>  
  
```xml  
<s:Envelope>  
<s:Header>   
<a:Action>http://docs.oasis-open.org/ws-tx/wsat/2006/06</a:Action>  
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
  
### <a name="application-messages"></a><span data-ttu-id="0aabe-259">Messages d'application</span><span class="sxs-lookup"><span data-stu-id="0aabe-259">Application Messages</span></span>  
 <span data-ttu-id="0aabe-260">Les messages suivants sont des messages d'application.</span><span class="sxs-lookup"><span data-stu-id="0aabe-260">The following messages are application messages.</span></span>  
  
#### <a name="application-message-request"></a><span data-ttu-id="0aabe-261">Message d'application - demande</span><span class="sxs-lookup"><span data-stu-id="0aabe-261">Application message-Request</span></span>  
  
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
