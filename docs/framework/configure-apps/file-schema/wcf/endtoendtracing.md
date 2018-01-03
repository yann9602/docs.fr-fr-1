---
title: '&lt;endToEndTracing&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5034f5de-bb60-4157-9ad4-58aaade094e0
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a43801f4c45d7ac518c3b24cadc58ffbec40adb4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltendtoendtracinggt"></a><span data-ttu-id="55249-102">&lt;endToEndTracing&gt;</span><span class="sxs-lookup"><span data-stu-id="55249-102">&lt;endToEndTracing&gt;</span></span>
<span data-ttu-id="55249-103">Élément de configuration qui vous permet d'activer et désactiver différents aspects du suivi de bout en bout pendant l'exécution d'une application de service.</span><span class="sxs-lookup"><span data-stu-id="55249-103">A configuration element that allows you to enable and disable different aspects of end-to-end tracing during the running of a service application.</span></span>  
  
 <span data-ttu-id="55249-104">\<système. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="55249-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="55249-105">\<diagnostic ></span><span class="sxs-lookup"><span data-stu-id="55249-105">\<diagnostic></span></span>  
<span data-ttu-id="55249-106">\<endToEndTracing ></span><span class="sxs-lookup"><span data-stu-id="55249-106">\<endToEndTracing></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55249-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="55249-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
   <diagnostics>  
       <endToEndTracing activityTracing="Boolean"  
          messageFlowTracing="Boolean"  
          propagateActivity="Boolean" />  
   </diagnostics>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="55249-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="55249-108">Attributes and Elements</span></span>  
 <span data-ttu-id="55249-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="55249-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="55249-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="55249-110">Attributes</span></span>  
  
|<span data-ttu-id="55249-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="55249-111">Attribute</span></span>|<span data-ttu-id="55249-112">Description</span><span class="sxs-lookup"><span data-stu-id="55249-112">Description</span></span>|  
|---------------|-----------------|  
|`activityTracing`|<span data-ttu-id="55249-113">Valeur booléenne qui spécifie si le suivi d'activité est activé.</span><span class="sxs-lookup"><span data-stu-id="55249-113">A Boolean value that specifies whether activity tracing is enabled.</span></span>|  
|`messageFlowTracing`|<span data-ttu-id="55249-114">Valeur booléenne qui spécifie si le suivi de flux de messages est activé.</span><span class="sxs-lookup"><span data-stu-id="55249-114">A Boolean value that specifies whether message flow tracing in enabled.</span></span>|  
|`propagateActivity`|<span data-ttu-id="55249-115">Valeur booléenne qui spécifie si l'attribut de propagation a la valeur True.</span><span class="sxs-lookup"><span data-stu-id="55249-115">A Boolean value that specifies whether the propagate attribute is set to true.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="55249-116">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="55249-116">Child Elements</span></span>  
 <span data-ttu-id="55249-117">Aucun.</span><span class="sxs-lookup"><span data-stu-id="55249-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="55249-118">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="55249-118">Parent Elements</span></span>  
  
|<span data-ttu-id="55249-119">Élément</span><span class="sxs-lookup"><span data-stu-id="55249-119">Element</span></span>|<span data-ttu-id="55249-120">Description</span><span class="sxs-lookup"><span data-stu-id="55249-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="55249-121">\<Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="55249-121">\<diagnostics></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md)|<span data-ttu-id="55249-122">Définit des paramètres WCF pour l'inspection et le contrôle au moment de l'exécution pour l'administrateur.</span><span class="sxs-lookup"><span data-stu-id="55249-122">Defines WCF settings for runtime inspection and control for the administrator.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="55249-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="55249-123">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.DiagnosticSection>  
 <xref:System.ServiceModel.Diagnostics>  
 <xref:System.ServiceModel.Configuration.DiagnosticSection.EndToEndTracing%2A>  
 <xref:System.ServiceModel.Configuration.EndToEndTracingElement>  
 [<span data-ttu-id="55249-124">Suivi de bout en bout</span><span class="sxs-lookup"><span data-stu-id="55249-124">End-to-End Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing.md)
