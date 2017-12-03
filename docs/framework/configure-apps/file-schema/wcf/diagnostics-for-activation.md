---
title: '&lt;diagnostics&gt; pour l''activation'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1486e0eb-fe2a-46c3-b584-c924889477dd
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1610c77125d2820e3adc06b3c37177058c85abdd
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="ltdiagnosticsgt-for-activation"></a><span data-ttu-id="4701e-102">&lt;diagnostics&gt; pour l'activation</span><span class="sxs-lookup"><span data-stu-id="4701e-102">&lt;diagnostics&gt; for Activation</span></span>
<span data-ttu-id="4701e-103">Configure les fonctionnalités de diagnostic de l'écouteur [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4701e-103">Configures [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] listener's diagnostics functionalities.</span></span>  
  
 <span data-ttu-id="4701e-104">\<system.serviceModel.activation ></span><span class="sxs-lookup"><span data-stu-id="4701e-104">\<system.serviceModel.activation></span></span>  
<span data-ttu-id="4701e-105">\<Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="4701e-105">\<diagnostics></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4701e-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4701e-106">Syntax</span></span>  
  
```xml  
<configuration>  
   <system.serviceModel.activation>  
       <diagnostics performanceCountersEnabled="Boolean" />  
   </system.serviceModel.activation>  
</configuration>  
```  
  
## <a name="type"></a><span data-ttu-id="4701e-107">Type</span><span class="sxs-lookup"><span data-stu-id="4701e-107">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4701e-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="4701e-108">Attributes and Elements</span></span>  
 <span data-ttu-id="4701e-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="4701e-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4701e-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="4701e-110">Attributes</span></span>  
  
|<span data-ttu-id="4701e-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="4701e-111">Attribute</span></span>|<span data-ttu-id="4701e-112">Description</span><span class="sxs-lookup"><span data-stu-id="4701e-112">Description</span></span>|  
|---------------|-----------------|  
|`performanceCountersEnabled`|<span data-ttu-id="4701e-113">Valeur booléenne qui indique si les compteurs de performance sont activés à des fins de diagnostic.</span><span class="sxs-lookup"><span data-stu-id="4701e-113">A Boolean value that indicates whether performance counters are enabled for diagnostic purposes.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4701e-114">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="4701e-114">Child Elements</span></span>  
 <span data-ttu-id="4701e-115">Aucun.</span><span class="sxs-lookup"><span data-stu-id="4701e-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4701e-116">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="4701e-116">Parent Elements</span></span>  
  
|<span data-ttu-id="4701e-117">Élément</span><span class="sxs-lookup"><span data-stu-id="4701e-117">Element</span></span>|<span data-ttu-id="4701e-118">Description</span><span class="sxs-lookup"><span data-stu-id="4701e-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4701e-119">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="4701e-119">\<system.serviceModel.activation></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel-activation.md)|<span data-ttu-id="4701e-120">Contient les paramètres de configuration du processus de l'écouteur SMSvcHost.exe.</span><span class="sxs-lookup"><span data-stu-id="4701e-120">Contains configuration settings for the listener process SMSvcHost.exe.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4701e-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4701e-121">See Also</span></span>  
 <xref:System.ServiceModel.Activation.Configuration.DiagnosticSection>
