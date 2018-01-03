---
title: '&lt;routing&gt; of &lt;serviceBehavior&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d8f9c844-4629-4a45-9599-856dc8f01794
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: eb43a658e26237037ac2a93658d97893005d07cd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltroutinggt-of-ltservicebehaviorgt"></a><span data-ttu-id="b2952-102">&lt;routing&gt; of &lt;serviceBehavior&gt;</span><span class="sxs-lookup"><span data-stu-id="b2952-102">&lt;routing&gt; of &lt;serviceBehavior&gt;</span></span>
<span data-ttu-id="b2952-103">Fournit un accès au service de routage au moment de l'exécution afin d'autoriser une modification dynamique de la configuration de routage.</span><span class="sxs-lookup"><span data-stu-id="b2952-103">Provides run-time access to the routing service to allow dynamic modification of the routing configuration.</span></span>  
  
 <span data-ttu-id="b2952-104">\<système. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="b2952-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="b2952-105">\<comportements ></span><span class="sxs-lookup"><span data-stu-id="b2952-105">\<behaviors></span></span>  
<span data-ttu-id="b2952-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="b2952-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="b2952-107">\<comportement ></span><span class="sxs-lookup"><span data-stu-id="b2952-107">\<behavior></span></span>  
<span data-ttu-id="b2952-108">\<routage ></span><span class="sxs-lookup"><span data-stu-id="b2952-108">\<routing></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2952-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b2952-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <routing filterTable="String" 
               routeOnHeadersOnly="Boolean" 
               SoapProcessingEnabled="Boolean" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b2952-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="b2952-110">Attributes and Elements</span></span>  
 <span data-ttu-id="b2952-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="b2952-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b2952-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="b2952-112">Attributes</span></span>  
  
|<span data-ttu-id="b2952-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="b2952-113">Attribute</span></span>|<span data-ttu-id="b2952-114">Description</span><span class="sxs-lookup"><span data-stu-id="b2952-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b2952-115">filterTable</span><span class="sxs-lookup"><span data-stu-id="b2952-115">filterTable</span></span>|<span data-ttu-id="b2952-116">Chaîne qui spécifie le nom de la table de routage contenant les filtres destinés à être évalués par le service de routage.</span><span class="sxs-lookup"><span data-stu-id="b2952-116">A string that specifies the name of the routing table that contains filters to be evaluated by the routing service.</span></span> <span data-ttu-id="b2952-117">Cette valeur doit correspondre à la `name` attribut d’un [ \<filterTable >](../../../../../docs/framework/configure-apps/file-schema/wcf/filtertable.md) élément dans le [ \<filterTables >](../../../../../docs/framework/configure-apps/file-schema/wcf/filtertables.md) section.</span><span class="sxs-lookup"><span data-stu-id="b2952-117">This value must match the `name` attribute of a [\<filterTable>](../../../../../docs/framework/configure-apps/file-schema/wcf/filtertable.md) element in the [\<filterTables>](../../../../../docs/framework/configure-apps/file-schema/wcf/filtertables.md) section.</span></span>|  
|<span data-ttu-id="b2952-118">routeOnHeaderOnly</span><span class="sxs-lookup"><span data-stu-id="b2952-118">routeOnHeaderOnly</span></span>|<span data-ttu-id="b2952-119">Valeur booléenne qui spécifie si le filtre doit examiner à la fois le corps du message et l'en-tête, ou l'en-tête uniquement.</span><span class="sxs-lookup"><span data-stu-id="b2952-119">A Boolean value that specifies whether the filter will examine both the message body and the header, or the header only.</span></span> <span data-ttu-id="b2952-120">La valeur par défaut est `true`.</span><span class="sxs-lookup"><span data-stu-id="b2952-120">The default is `true`.</span></span>|  
|<span data-ttu-id="b2952-121">soapProcessingEnabled</span><span class="sxs-lookup"><span data-stu-id="b2952-121">soapProcessingEnabled</span></span>|<span data-ttu-id="b2952-122">Valeur booléenne qui spécifie si le traitement SOAP doit avoir lieu.</span><span class="sxs-lookup"><span data-stu-id="b2952-122">A Boolean value that specifies whether SOAP processing should occur.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b2952-123">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="b2952-123">Child Elements</span></span>  
 <span data-ttu-id="b2952-124">Aucun.</span><span class="sxs-lookup"><span data-stu-id="b2952-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b2952-125">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="b2952-125">Parent Elements</span></span>  
  
|<span data-ttu-id="b2952-126">Élément</span><span class="sxs-lookup"><span data-stu-id="b2952-126">Element</span></span>|<span data-ttu-id="b2952-127">Description</span><span class="sxs-lookup"><span data-stu-id="b2952-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b2952-128">\<comportement ></span><span class="sxs-lookup"><span data-stu-id="b2952-128">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="b2952-129">Spécifie un élément de comportement.</span><span class="sxs-lookup"><span data-stu-id="b2952-129">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b2952-130">Notes</span><span class="sxs-lookup"><span data-stu-id="b2952-130">Remarks</span></span>  
 <span data-ttu-id="b2952-131">Lorsqu'il est ajouté à la configuration de comportement du service, cet élément de configuration active le routage pour le service.</span><span class="sxs-lookup"><span data-stu-id="b2952-131">When added to the service’s behavior configuration, this configuration element enables routing for the service.</span></span> <span data-ttu-id="b2952-132">Vous pouvez spécifier la table de routage réelle que le service doit utiliser dans cet élément.</span><span class="sxs-lookup"><span data-stu-id="b2952-132">You can specify the actual routing table to be used by the service in this element.</span></span>  
  
 <span data-ttu-id="b2952-133">Cette section de configuration vous permet de modifier immédiatement vos paramètres de routage lorsque votre modèle de déploiement change.</span><span class="sxs-lookup"><span data-stu-id="b2952-133">Using this configuration section, you can change your routing settings on the fly when your deployment pattern changes.</span></span> <span data-ttu-id="b2952-134">Au moment de l’exécution, vous pouvez inscrire votre propre extension de routage avec de nouveaux paramètres de routage. Le service de routage commence alors à utiliser les informations de configuration mises à jour pour les nouveaux messages et sessions, en laissant les messages/sessions en cours utiliser les règles qui étaient en place lorsqu’ils ont démarré.</span><span class="sxs-lookup"><span data-stu-id="b2952-134">At runtime, you can register your own routing extension with new routing settings and the routing service will begin using the updated configuration information for new messages and sessions, while leaving in-flight messages/sessions using whatever rules were in place when they started.</span></span>  <span data-ttu-id="b2952-135">Vous avez ainsi la possibilité de reconfigurer le service de routage au moment de l'exécution, sans interruption de session ni recyclage.</span><span class="sxs-lookup"><span data-stu-id="b2952-135">This gives you the ability to do session-safe, recycle-less reconfiguration of the Routing Service during runtime.</span></span>  
  
