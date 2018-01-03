---
title: '&lt;soapProcessing&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e8707027-e6b8-4539-893d-3cd7c13fbc18
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1aeb100e1b8e160d30566cd43d67cbf49c6b5c4e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltsoapprocessinggt"></a><span data-ttu-id="fc70f-102">&lt;soapProcessing&gt;</span><span class="sxs-lookup"><span data-stu-id="fc70f-102">&lt;soapProcessing&gt;</span></span>

<span data-ttu-id="fc70f-103">Définit le comportement de point de terminaison client utilisé pour marshaler des messages entre les versions de message et les types de liaison différents.</span><span class="sxs-lookup"><span data-stu-id="fc70f-103">Defines the client endpoint behavior used to marshal messages between different binding types and message versions.</span></span>

<span data-ttu-id="fc70f-104">**\<système. ServiceModel >** </span><span class="sxs-lookup"><span data-stu-id="fc70f-104">**\<system.ServiceModel>** </span></span>  
<span data-ttu-id="fc70f-105">&nbsp;&nbsp;**\<comportements >** </span><span class="sxs-lookup"><span data-stu-id="fc70f-105">&nbsp;&nbsp;**\<behaviors>** </span></span>  
<span data-ttu-id="fc70f-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<endpointBehaviors >** </span><span class="sxs-lookup"><span data-stu-id="fc70f-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<endpointBehaviors>** </span></span>  
<span data-ttu-id="fc70f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<comportement >** </span><span class="sxs-lookup"><span data-stu-id="fc70f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<behavior>** </span></span>  
<span data-ttu-id="fc70f-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<soapProcessing >**</span><span class="sxs-lookup"><span data-stu-id="fc70f-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<soapProcessing>**</span></span>

## <a name="syntax"></a><span data-ttu-id="fc70f-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fc70f-109">Syntax</span></span>

```xml
<soapProcessing processMessages="true|false" />
```

## <a name="attributes-and-elements"></a><span data-ttu-id="fc70f-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="fc70f-110">Attributes and elements</span></span>

<span data-ttu-id="fc70f-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="fc70f-111">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="fc70f-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="fc70f-112">Attributes</span></span>

|                   | <span data-ttu-id="fc70f-113">Description</span><span class="sxs-lookup"><span data-stu-id="fc70f-113">Description</span></span> |
| ----------------- | ----------- |
| `processMessages` | <span data-ttu-id="fc70f-114">Valeur booléenne qui spécifie si les messages doivent être marshalés entre des versions de message SOAP.</span><span class="sxs-lookup"><span data-stu-id="fc70f-114">A Boolean value that specifies whether messages should be marshaled between SOAP message versions.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="fc70f-115">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="fc70f-115">Child elements</span></span>

<span data-ttu-id="fc70f-116">Aucun.</span><span class="sxs-lookup"><span data-stu-id="fc70f-116">None</span></span>

### <a name="parent-elements"></a><span data-ttu-id="fc70f-117">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="fc70f-117">Parent elements</span></span>

|     | <span data-ttu-id="fc70f-118">Description</span><span class="sxs-lookup"><span data-stu-id="fc70f-118">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="fc70f-119">**\<comportement >**</span><span class="sxs-lookup"><span data-stu-id="fc70f-119">**\<behavior>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) | <span data-ttu-id="fc70f-120">Spécifie un comportement de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="fc70f-120">Specifies an endpoint behavior.</span></span> |

## <a name="remarks"></a><span data-ttu-id="fc70f-121">Notes</span><span class="sxs-lookup"><span data-stu-id="fc70f-121">Remarks</span></span>

<span data-ttu-id="fc70f-122">Le traitement SOAP est le processus par lequel les messages sont convertis entre des versions de message.</span><span class="sxs-lookup"><span data-stu-id="fc70f-122">SOAP processing is the process where messages are converted between message versions.</span></span>

<span data-ttu-id="fc70f-123">Le service de routage [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] peut convertir des messages entre différents protocoles.</span><span class="sxs-lookup"><span data-stu-id="fc70f-123">The [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] Routing Service can convert messages from one protocol to another.</span></span> <span data-ttu-id="fc70f-124">Si les versions des messages entrant et sortant sont différentes, un nouveau message est créé dans la version correcte.</span><span class="sxs-lookup"><span data-stu-id="fc70f-124">If the incoming and outgoing Message Versions are different, a new message of the correct version is created.</span></span> <span data-ttu-id="fc70f-125">Le traitement des messages à partir d’un <!--zz <xref:System.ServiceModel.Channel.MessageVersion> --> `MessageVersion` à un autre s’effectue en créant un nouveau [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] message qui contient la partie de corps et en-têtes pertinents entrant [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] message.</span><span class="sxs-lookup"><span data-stu-id="fc70f-125">Processing messages from one <!--zz <xref:System.ServiceModel.Channel.MessageVersion> --> `MessageVersion`  to another is accomplished by constructing a new [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] message that contains the body part and relevant headers from the incoming [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] message.</span></span> <span data-ttu-id="fc70f-126">Les en-têtes spécifiques à l'adressage ou reconnus au niveau du routeur ne sont pas utilisés pendant la création du nouveau message WCF car ils sont de versions différentes (dans le cas d'en-têtes d'adressage) ou ont été traités dans le cadre de la communication entre le client et le routeur.</span><span class="sxs-lookup"><span data-stu-id="fc70f-126">Headers that are specific to addressing, or that are understood at the router level, are not used during construction of the new WCF message because these headers are either of a different version (in the case of addressing headers) or have been processed as part of the communication between the client and the router.</span></span>

<span data-ttu-id="fc70f-127">Le placement d'un en-tête dans le message sortant dépend de son balisage comme étant compris au moment où il traverse la couche du canal entrant.</span><span class="sxs-lookup"><span data-stu-id="fc70f-127">Whether a header is placed in the outbound message is determined by whether or not it was marked as understood as it passed through the incoming channel layer.</span></span> <span data-ttu-id="fc70f-128">Les en-têtes non reconnus (tels que les en-têtes personnalisés) ne sont pas supprimés et traversent donc le service de routage en étant copiés dans le message sortant.</span><span class="sxs-lookup"><span data-stu-id="fc70f-128">Headers that are not understood (such as custom headers) are not removed and so pass through the routing service by being copied to the outbound message.</span></span> <span data-ttu-id="fc70f-129">Le corps du message est copié dans le message sortant.</span><span class="sxs-lookup"><span data-stu-id="fc70f-129">The body of the message is copied to the outbound message.</span></span> <span data-ttu-id="fc70f-130">Le message est ensuite envoyé via le canal de sortie ; les en-têtes et autres données d'enveloppe spécifiques à ce protocole de communication/transport sont alors créés et ajoutés.</span><span class="sxs-lookup"><span data-stu-id="fc70f-130">The message is then sent out the outbound channel, at which point all of the headers and other envelope data specific to that communication protocol/transport will be created and added.</span></span>

<span data-ttu-id="fc70f-131">Ces étapes de traitement s'exécutent lorsque le comportement de traitement SOAP est spécifié.</span><span class="sxs-lookup"><span data-stu-id="fc70f-131">Such processing steps take place when the SOAP processing behavior is specified.</span></span> <span data-ttu-id="fc70f-132">Cela [ \<soapProcessingExtension >](../../../../../docs/framework/configure-apps/file-schema/wcf/soapprocessing.md) comportement est un comportement de point de terminaison qui est appliqué à tous les points de terminaison de client (sortant) au démarrage du Service de routage.</span><span class="sxs-lookup"><span data-stu-id="fc70f-132">This [\<soapProcessingExtension>](../../../../../docs/framework/configure-apps/file-schema/wcf/soapprocessing.md) behavior is an endpoint behavior that is applied to all client (outgoing) endpoints when the Routing Service starts up.</span></span> <span data-ttu-id="fc70f-133">par défaut, le [ \<routage >](../../../../../docs/framework/configure-apps/file-schema/wcf/routing-of-servicebehavior.md) comportement crée et attache un nouveau [ \<soapProcessingExtension >](../../../../../docs/framework/configure-apps/file-schema/wcf/soapprocessing.md) comportement avec `processMessages` la valeur `true` pour chaque point de terminaison client.</span><span class="sxs-lookup"><span data-stu-id="fc70f-133">default, the [\<routing>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing-of-servicebehavior.md) behavior creates and attaches a new [\<soapProcessingExtension>](../../../../../docs/framework/configure-apps/file-schema/wcf/soapprocessing.md) behavior with `processMessages` set to `true` for each client endpoint.</span></span> <span data-ttu-id="fc70f-134">Si vous utilisez un protocole non reconnu par le service de routage ou souhaitez remplacer le comportement de traitement par défaut, vous pouvez désactiver le traitement SOAP pour l'intégralité du service de routage ou pour des points de terminaison particuliers.</span><span class="sxs-lookup"><span data-stu-id="fc70f-134">If you have a protocol that the Routing Service does not understand, or wish to override the default processing behavior, you can disable SOAP processing either for the entire Routing Service or just for particular endpoints.</span></span>  <span data-ttu-id="fc70f-135">Pour désactiver le traitement pour le service de routage entier sur tous les points de terminaison SOAP, définissez la `soapProcessing` attribut de la [ \<routage >](../../../../../docs/framework/configure-apps/file-schema/wcf/routing-of-servicebehavior.md) comportement `false`.</span><span class="sxs-lookup"><span data-stu-id="fc70f-135">To disable SOAP processing for the entire routing service on all endpoints, set the `soapProcessing` attribute of the [\<routing>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing-of-servicebehavior.md) behavior to `false`.</span></span> <span data-ttu-id="fc70f-136">Pour désactiver le traitement SOAP pour un point de terminaison particulier, utilisez ce comportement et affectez à son attribut `processMessages` la valeur `false`, puis attachez ce comportement au point de terminaison au niveau duquel vous ne voulez pas exécuter le code de traitement par défaut.</span><span class="sxs-lookup"><span data-stu-id="fc70f-136">To turn off SOAP processing for a particular endpoint, use this behavior and set its `processMessages` attribute to `false`, then attach this behavior to the endpoint you do not want the default processing code to run at.</span></span>  <span data-ttu-id="fc70f-137">Lorsque le [ \<routage >](../../../../../docs/framework/configure-apps/file-schema/wcf/routing-of-servicebehavior.md) comportement configure le Service de routage, elle sera ignorée en réappliquant le comportement de point de terminaison, car il en existe déjà.</span><span class="sxs-lookup"><span data-stu-id="fc70f-137">When the [\<routing>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing-of-servicebehavior.md) behavior sets up the Routing Service, it will skip reapplying the endpoint behavior since one already exists.</span></span>
