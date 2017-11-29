---
title: '&lt;filtres&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 37a87222-ec78-4728-8105-9ca1bd961f0c
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 21f2115f83772312e1b9f42a66c53ba8ee2834f9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="ltfiltersgt"></a><span data-ttu-id="f4074-102">&lt;filtres&gt;</span><span class="sxs-lookup"><span data-stu-id="f4074-102">&lt;filters&gt;</span></span>

<span data-ttu-id="f4074-103">L'élément `filters` détient une collection de filtres XPath utilisés pour contrôler le type de message enregistré.</span><span class="sxs-lookup"><span data-stu-id="f4074-103">The `filters` element holds a collection of XPath filters used to control what kind of message is logged.</span></span>

<span data-ttu-id="f4074-104">Les filtres sont appliqués uniquement à la couche de transport, spécifiée par `logMessagesAtTransportLevel` (valeur `true`).</span><span class="sxs-lookup"><span data-stu-id="f4074-104">Filters are applied only at the transport layer, specified by `logMessagesAtTransportLevel` is `true`.</span></span> <span data-ttu-id="f4074-105">Le niveau de service et l'enregistrement du message incorrect ne sont pas affectés par les filtres.</span><span class="sxs-lookup"><span data-stu-id="f4074-105">Service level and malformed message logging are not affected by filters.</span></span>

<span data-ttu-id="f4074-106">Pour ajouter un filtre à la collection, utilisez le mot clé `add`.</span><span class="sxs-lookup"><span data-stu-id="f4074-106">To add a filter to the collection, use the `add` keyword.</span></span> <span data-ttu-id="f4074-107">Lorsqu'un ou plusieurs filtres sont définis, seuls les messages qui correspondent au moins à l'un des filtres sont enregistrés.</span><span class="sxs-lookup"><span data-stu-id="f4074-107">When one or more filters are defined, only messages that match at least one of the filters are logged.</span></span> <span data-ttu-id="f4074-108">Si aucun filtre n'est défini, tous les messages passent.</span><span class="sxs-lookup"><span data-stu-id="f4074-108">If no filter is defined, all messages pass through.</span></span>

<span data-ttu-id="f4074-109">Les filtres prennent en charge la syntaxe XPath complète et s'appliquent dans l'ordre dans lequel ils apparaissent dans le fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="f4074-109">Filters support the full XPath syntax, and are applied in the order they appear in the configuration file.</span></span> <span data-ttu-id="f4074-110">Un filtre syntaxiquement incorrect provoque la levée d'une exception de configuration.</span><span class="sxs-lookup"><span data-stu-id="f4074-110">A syntactically incorrect filter results in a configuration exception.</span></span>

<span data-ttu-id="f4074-111">L'exemple de code suivant illustre comment configurer un filtre afin que seuls les messages contenant une section d'en-tête SOAP soient enregistrés.</span><span class="sxs-lookup"><span data-stu-id="f4074-111">The following is an example of how to configure a filter that records only messages that have a SOAP Header section.</span></span>

```xml
<messageLogging logEntireMessage="true"
                logMalformedMessages="true"
                logMessagesAtServiceLevel="true"
                logMessagesAtTransportLevel="true"
                maxMessagesToLog="420">  
  <filters>  
    <add xmlns:soap="http://www.w3.org/2003/05/soap-envelope">  
      /soap:Envelope/soap:Headers  
    </add>  
  </filters>  
</messageLogging>
```

## <a name="see-also"></a><span data-ttu-id="f4074-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f4074-112">See also</span></span>

 <span data-ttu-id="f4074-113"><xref:System.ServiceModel.Configuration.DiagnosticSection><xref:System.ServiceModel.Diagnostics> <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A> <xref:System.ServiceModel.Configuration.MessageLoggingElement> <xref:System.ServiceModel.Configuration.MessageLoggingElement.Filters%2A> <xref:System.ServiceModel.Configuration.XPathMessageFilterElementCollection> <xref:System.ServiceModel.Configuration.XPathMessageFilterElement> <xref:System.ServiceModel.Dispatcher.XPathMessageFilter> [Configuration de la journalisation du Message](../../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md) [ \<enregistrement des messages >](../../../../../docs/framework/configure-apps/file-schema/wcf/messagelogging.md)</span><span class="sxs-lookup"><span data-stu-id="f4074-113"><xref:System.ServiceModel.Configuration.DiagnosticSection> <xref:System.ServiceModel.Diagnostics> <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A> <xref:System.ServiceModel.Configuration.MessageLoggingElement> <xref:System.ServiceModel.Configuration.MessageLoggingElement.Filters%2A> <xref:System.ServiceModel.Configuration.XPathMessageFilterElementCollection> <xref:System.ServiceModel.Configuration.XPathMessageFilterElement> <xref:System.ServiceModel.Dispatcher.XPathMessageFilter> [Configuring Message Logging](../../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md) [\<messageLogging>](../../../../../docs/framework/configure-apps/file-schema/wcf/messagelogging.md)</span></span>
