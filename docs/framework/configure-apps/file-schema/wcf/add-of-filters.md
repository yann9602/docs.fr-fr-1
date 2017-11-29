---
title: '&lt;add&gt; de &lt;filters&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e3bf437c-dd99-49f3-9792-9a8721e6eaad
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7143216b6b195c59077b004f8aaa1b17a249fbc3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltaddgt-of-ltfiltersgt"></a><span data-ttu-id="268ef-102">&lt;add&gt; de &lt;filters&gt;</span><span class="sxs-lookup"><span data-stu-id="268ef-102">&lt;add&gt; of &lt;filters&gt;</span></span>
<span data-ttu-id="268ef-103">Filtre XPath qui spécifie le type de message à enregistrer.</span><span class="sxs-lookup"><span data-stu-id="268ef-103">A XPath filter that specifies the kind of message to be logged.</span></span>  
  
 <span data-ttu-id="268ef-104">\<système. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="268ef-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="268ef-105">\<diagnostic ></span><span class="sxs-lookup"><span data-stu-id="268ef-105">\<diagnostic></span></span>  
<span data-ttu-id="268ef-106">\<enregistrement des messages ></span><span class="sxs-lookup"><span data-stu-id="268ef-106">\<messageLogging></span></span>  
<span data-ttu-id="268ef-107">\<filtres ></span><span class="sxs-lookup"><span data-stu-id="268ef-107">\<filters></span></span>  
<span data-ttu-id="268ef-108">\<add></span><span class="sxs-lookup"><span data-stu-id="268ef-108">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="268ef-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="268ef-109">Syntax</span></span>  
  
```xml  
<filters>  
   <add filter="String"/>  
</filters>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="268ef-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="268ef-110">Attributes and Elements</span></span>  
 <span data-ttu-id="268ef-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="268ef-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="268ef-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="268ef-112">Attributes</span></span>  
  
|<span data-ttu-id="268ef-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="268ef-113">Attribute</span></span>|<span data-ttu-id="268ef-114">Description</span><span class="sxs-lookup"><span data-stu-id="268ef-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="268ef-115">filtre</span><span class="sxs-lookup"><span data-stu-id="268ef-115">filter</span></span>|<span data-ttu-id="268ef-116">Chaîne qui spécifie une requête sur un document XML défini par une expression XPath 1.0.</span><span class="sxs-lookup"><span data-stu-id="268ef-116">A string that specifies a query on an XML document defined by an XPath 1.0 expression.</span></span> <span data-ttu-id="268ef-117">Pour plus d'informations, consultez <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>.</span><span class="sxs-lookup"><span data-stu-id="268ef-117">For more information, see <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="268ef-118">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="268ef-118">Child Elements</span></span>  
 <span data-ttu-id="268ef-119">Aucun.</span><span class="sxs-lookup"><span data-stu-id="268ef-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="268ef-120">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="268ef-120">Parent Elements</span></span>  
  
|<span data-ttu-id="268ef-121">Élément</span><span class="sxs-lookup"><span data-stu-id="268ef-121">Element</span></span>|<span data-ttu-id="268ef-122">Description</span><span class="sxs-lookup"><span data-stu-id="268ef-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="268ef-123">\<filtres ></span><span class="sxs-lookup"><span data-stu-id="268ef-123">\<filters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters.md)|<span data-ttu-id="268ef-124">Contient une collection de filtres XPath utilisés pour contrôler le type de message enregistré.</span><span class="sxs-lookup"><span data-stu-id="268ef-124">Contains a collection of XPath filters used to control what kind of message is logged.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="268ef-125">Remarques</span><span class="sxs-lookup"><span data-stu-id="268ef-125">Remarks</span></span>  
 <span data-ttu-id="268ef-126">Les filtres sont appliqués uniquement à la couche de transport, spécifiée par `logMessagesAtTransportLevel` (valeur `true`).</span><span class="sxs-lookup"><span data-stu-id="268ef-126">Filters are applied only at the transport layer, specified by `logMessagesAtTransportLevel` is `true`.</span></span> <span data-ttu-id="268ef-127">Le niveau de service et l'enregistrement du message incorrect ne sont pas affectés par les filtres.</span><span class="sxs-lookup"><span data-stu-id="268ef-127">Service level and malformed message logging are not affected by filters.</span></span>  
  
 <span data-ttu-id="268ef-128">Pour ajouter un filtre à la collection, utilisez le mot clé `add`.</span><span class="sxs-lookup"><span data-stu-id="268ef-128">To add a filter to the collection, use the `add` keyword.</span></span> <span data-ttu-id="268ef-129">Lorsqu'un ou plusieurs filtres sont définis, seuls les messages qui correspondent au moins à l'un des filtres sont enregistrés.</span><span class="sxs-lookup"><span data-stu-id="268ef-129">When one or more filters are defined, only messages that match at least one of the filters are logged.</span></span> <span data-ttu-id="268ef-130">Si aucun filtre n'est défini, tous les messages passent.</span><span class="sxs-lookup"><span data-stu-id="268ef-130">If no filter is defined, all messages pass through.</span></span>  
  
 <span data-ttu-id="268ef-131">Les filtres prennent en charge la syntaxe XPath complète et s'appliquent dans l'ordre dans lequel ils apparaissent dans le fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="268ef-131">Filters support the full XPath syntax, and are applied in the order they appear in the configuration file.</span></span> <span data-ttu-id="268ef-132">Un filtre syntaxiquement incorrect provoque la levée d'une exception de configuration.</span><span class="sxs-lookup"><span data-stu-id="268ef-132">A syntactically incorrect filter results in a configuration exception.</span></span>  
  
 <span data-ttu-id="268ef-133">L'exemple de code suivant illustre comment configurer un filtre afin que seuls les messages contenant une section d'en-tête SOAP soient enregistrés.</span><span class="sxs-lookup"><span data-stu-id="268ef-133">The following is an example of how to configure a filter that records only messages that have a SOAP Header section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="268ef-134">Exemple</span><span class="sxs-lookup"><span data-stu-id="268ef-134">Example</span></span>  
 <span data-ttu-id="268ef-135">L'exemple de code suivant illustre comment configurer un filtre afin que seuls les messages contenant une section d'en-tête SOAP soient enregistrés.</span><span class="sxs-lookup"><span data-stu-id="268ef-135">The following is an example of how to configure a filter that records only messages that have a SOAP Header section.</span></span>  
  
```xml  
<messageLogging logEntireMessage="true"  
     logMalformedMessages="true" logMessagesAtServiceLevel="true"  
     logMessagesAtTransportLevel="true" maxMessagesToLog="420">  
     <filters>  
        <add xmlns:soap="http://www.w3.org/2003/05/soap-envelope">  
                        /soap:Envelope/soap:Headers  
        </add>  
     </filters>  
</messageLogging>  
```  
  
## <a name="see-also"></a><span data-ttu-id="268ef-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="268ef-136">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.DiagnosticSection>  
 <xref:System.ServiceModel.Diagnostics>  
 <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>  
 <xref:System.ServiceModel.Configuration.MessageLoggingElement>  
 <xref:System.ServiceModel.Configuration.MessageLoggingElement.Filters%2A>  
 <xref:System.ServiceModel.Configuration.XPathMessageFilterElement>  
 <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>  
 [<span data-ttu-id="268ef-137">Configuration de la journalisation de Message</span><span class="sxs-lookup"><span data-stu-id="268ef-137">Configuring Message Logging</span></span>](../../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md)  
 [<span data-ttu-id="268ef-138">Configuration de la journalisation de Message</span><span class="sxs-lookup"><span data-stu-id="268ef-138">Configuring Message Logging</span></span>](../../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md)  
 [<span data-ttu-id="268ef-139">\<enregistrement des messages ></span><span class="sxs-lookup"><span data-stu-id="268ef-139">\<messageLogging></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/messagelogging.md)
