---
title: "&lt;filtre&gt; élément &lt;ajouter&gt; pour &lt;écouteurs&gt; pour &lt;trace&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/add/filter
helpviewer_keywords:
- initializeData attribute
- filter element for <add> for <listeners> for <trace>
- <filter> element for <add> for <listeners> for <trace>
ms.assetid: eb9c18f5-dfa8-47c5-b91b-e4b93e76e1cc
caps.latest.revision: "9"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 3d1cf912e5a07e7514a6b032ff511923ae93c5f1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltfiltergt-element-for-ltaddgt-for-ltlistenersgt-for-lttracegt"></a><span data-ttu-id="e6c6b-102">&lt;filtre&gt; élément &lt;ajouter&gt; pour &lt;écouteurs&gt; pour &lt;trace&gt;</span><span class="sxs-lookup"><span data-stu-id="e6c6b-102">&lt;filter&gt; Element for &lt;add&gt; for &lt;listeners&gt; for &lt;trace&gt;</span></span>
<span data-ttu-id="e6c6b-103">Ajoute un filtre à un écouteur de la `Listeners` collection pour une trace.</span><span class="sxs-lookup"><span data-stu-id="e6c6b-103">Adds a filter to a listener in the `Listeners` collection for a trace.</span></span>  
  
 <span data-ttu-id="e6c6b-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="e6c6b-104">\<configuration></span></span>  
<span data-ttu-id="e6c6b-105">\<System.Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="e6c6b-105">\<system.diagnostics></span></span>  
<span data-ttu-id="e6c6b-106">\<trace ></span><span class="sxs-lookup"><span data-stu-id="e6c6b-106">\<trace></span></span>  
<span data-ttu-id="e6c6b-107">\<écouteurs ></span><span class="sxs-lookup"><span data-stu-id="e6c6b-107">\<listeners></span></span>  
<span data-ttu-id="e6c6b-108">\<add></span><span class="sxs-lookup"><span data-stu-id="e6c6b-108">\<add></span></span>  
<span data-ttu-id="e6c6b-109">\<Filtre ></span><span class="sxs-lookup"><span data-stu-id="e6c6b-109">\<filter></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6c6b-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e6c6b-110">Syntax</span></span>  
  
```xml  
<filter   
  type="traceFilterClassName"   
  initializeData="data" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e6c6b-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="e6c6b-111">Attributes and Elements</span></span>  
 <span data-ttu-id="e6c6b-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="e6c6b-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e6c6b-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="e6c6b-113">Attributes</span></span>  
  
|<span data-ttu-id="e6c6b-114">Attribut</span><span class="sxs-lookup"><span data-stu-id="e6c6b-114">Attribute</span></span>|<span data-ttu-id="e6c6b-115">Description</span><span class="sxs-lookup"><span data-stu-id="e6c6b-115">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="e6c6b-116">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="e6c6b-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="e6c6b-117">Spécifie le type du filtre, qui doit hériter de la <xref:System.Diagnostics.TraceFilter> classe.</span><span class="sxs-lookup"><span data-stu-id="e6c6b-117">Specifies the type of the filter, which should inherit from the <xref:System.Diagnostics.TraceFilter> class.</span></span> <span data-ttu-id="e6c6b-118">Vous pouvez utiliser le nom qualifié d’espace de noms du type, ce qui correspond au type <xref:System.Type.FullName%2A> propriété, ou vous pouvez utiliser le nom de type qualifié complet, y compris les informations de l’assembly, qui correspondant à la <xref:System.Type.AssemblyQualifiedName%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="e6c6b-118">You can use the namespace-qualified name of the type, which corresponds to the type's <xref:System.Type.FullName%2A> property, or you can use the fully qualified type name including the assembly information, which corresponds to the <xref:System.Type.AssemblyQualifiedName%2A> property.</span></span> <span data-ttu-id="e6c6b-119">Pour plus d’informations sur les noms de types qualifiés complets, consultez [en spécifiant des noms de types qualifiés complets](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="e6c6b-119">For information about fully qualified type names, see [Specifying Fully Qualified Type Names](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="e6c6b-120">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="e6c6b-120">Optional attribute.</span></span><br /><br /> <span data-ttu-id="e6c6b-121">La chaîne passée au constructeur pour la classe de filtre spécifiée.</span><span class="sxs-lookup"><span data-stu-id="e6c6b-121">The string passed to the constructor for the specified filter class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e6c6b-122">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="e6c6b-122">Child Elements</span></span>  
 <span data-ttu-id="e6c6b-123">Aucun.</span><span class="sxs-lookup"><span data-stu-id="e6c6b-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e6c6b-124">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="e6c6b-124">Parent Elements</span></span>  
  
|<span data-ttu-id="e6c6b-125">Élément</span><span class="sxs-lookup"><span data-stu-id="e6c6b-125">Element</span></span>|<span data-ttu-id="e6c6b-126">Description</span><span class="sxs-lookup"><span data-stu-id="e6c6b-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="e6c6b-127">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e6c6b-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="e6c6b-128">Spécifie les écouteurs de trace qui collectent, stockent et acheminent les messages, ainsi que le niveau auquel un commutateur de trace est défini.</span><span class="sxs-lookup"><span data-stu-id="e6c6b-128">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`trace`|<span data-ttu-id="e6c6b-129">Contient les écouteurs qui collectent, stockent et acheminent les messages de traçage.</span><span class="sxs-lookup"><span data-stu-id="e6c6b-129">Contains listeners that collect, store, and route tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="e6c6b-130">Contient des écouteurs qui collectent, stocker et acheminer les messages.</span><span class="sxs-lookup"><span data-stu-id="e6c6b-130">Contains listeners that collect, store, and route messages.</span></span> <span data-ttu-id="e6c6b-131">Les écouteurs dirigent la sortie de traçage vers une cible appropriée.</span><span class="sxs-lookup"><span data-stu-id="e6c6b-131">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`add`|<span data-ttu-id="e6c6b-132">Ajoute un écouteur à la collection `Listeners`.</span><span class="sxs-lookup"><span data-stu-id="e6c6b-132">Adds a listener to the `Listeners` collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e6c6b-133">Remarques</span><span class="sxs-lookup"><span data-stu-id="e6c6b-133">Remarks</span></span>  
 <span data-ttu-id="e6c6b-134">Le `<filter>` élément doit être contenu dans un `<add>` élément pour un écouteur de trace qui spécifie le type de l’écouteur, pas seulement le nom d’un écouteur défini dans un [ \<sharedListeners >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md).</span><span class="sxs-lookup"><span data-stu-id="e6c6b-134">The `<filter>` element must be contained in an `<add>` element for a trace listener that specifies the type of the listener, not just the name of a listener defined in a [\<sharedListeners>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md).</span></span> <span data-ttu-id="e6c6b-135">Si l’écouteur est défini dans un [ \<sharedListeners >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md), le filtre de cet écouteur doit être défini dans cet élément.</span><span class="sxs-lookup"><span data-stu-id="e6c6b-135">If the listener is defined in a [\<sharedListeners>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md), the filter for that listener must be defined in that element.</span></span>  
  
 <span data-ttu-id="e6c6b-136">Cet élément peut être utilisé dans le fichier de configuration de l’ordinateur (Machine.config) et le fichier de configuration d’application.</span><span class="sxs-lookup"><span data-stu-id="e6c6b-136">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e6c6b-137">Exemple</span><span class="sxs-lookup"><span data-stu-id="e6c6b-137">Example</span></span>  
 <span data-ttu-id="e6c6b-138">L’exemple suivant montre comment utiliser le `<filter>` élément pour ajouter un filtre à l’écouteur `console` dans les `Listeners` collection de la trace, en spécifiant le niveau d’événement en tant que filtre `Error`.</span><span class="sxs-lookup"><span data-stu-id="e6c6b-138">The following example shows how to use the `<filter>` element to add a filter to the listener `console` in the `Listeners` collection for trace, specifying the filter event level as `Error`.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <trace autoflush="false" indentsize="4">  
      <listeners>  
        <add name="console"   
          type="System.Diagnostics.ConsoleTraceListener" >  
          <filter type="System.Diagnostics.EventTypeFilter"   
            initializeData="Error" />  
        </add>  
        <remove name="Default" />  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e6c6b-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e6c6b-139">See Also</span></span>  
 <xref:System.Diagnostics.Trace>  
 <xref:System.Diagnostics.TraceListener>  
 <xref:System.Diagnostics.TraceListener.Filter%2A?displayProperty=nameWithType>  
 <xref:System.Diagnostics.TraceFilter>  
 [<span data-ttu-id="e6c6b-140">Schéma des paramètres de trace et de débogage</span><span class="sxs-lookup"><span data-stu-id="e6c6b-140">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
