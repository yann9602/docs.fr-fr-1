---
title: "&lt;filtre&gt; élément &lt;ajouter&gt; pour &lt;écouteurs&gt; pour &lt;source&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#filter
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/add/filter
helpviewer_keywords:
- initializeData attribute
- <filter> element for <add> for <listeners> for <source>
- filter element for <add> for <listeners> for <source>
ms.assetid: 15808b80-4579-4c25-b385-178cfdf154ba
caps.latest.revision: "7"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: ff5acf8edcda68979c04f5e62237464ee6f040a0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltfiltergt-element-for-ltaddgt-for-ltlistenersgt-for-ltsourcegt"></a><span data-ttu-id="4e89a-102">&lt;filtre&gt; élément &lt;ajouter&gt; pour &lt;écouteurs&gt; pour &lt;source&gt;</span><span class="sxs-lookup"><span data-stu-id="4e89a-102">&lt;filter&gt; Element for &lt;add&gt; for &lt;listeners&gt; for &lt;source&gt;</span></span>
<span data-ttu-id="4e89a-103">Ajoute un filtre à un écouteur dans la collection `Listeners` pour une source de trace.</span><span class="sxs-lookup"><span data-stu-id="4e89a-103">Adds a filter to a listener in the `Listeners` collection for a trace source.</span></span>  
  
 <span data-ttu-id="4e89a-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="4e89a-104">\<configuration></span></span>  
<span data-ttu-id="4e89a-105">\<System.Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="4e89a-105">\<system.diagnostics></span></span>  
<span data-ttu-id="4e89a-106">\<sources ></span><span class="sxs-lookup"><span data-stu-id="4e89a-106">\<sources></span></span>  
<span data-ttu-id="4e89a-107">\<source ></span><span class="sxs-lookup"><span data-stu-id="4e89a-107">\<source></span></span>  
<span data-ttu-id="4e89a-108">\<écouteurs ></span><span class="sxs-lookup"><span data-stu-id="4e89a-108">\<listeners></span></span>  
<span data-ttu-id="4e89a-109">\<add></span><span class="sxs-lookup"><span data-stu-id="4e89a-109">\<add></span></span>  
<span data-ttu-id="4e89a-110">\<Filtre ></span><span class="sxs-lookup"><span data-stu-id="4e89a-110">\<filter></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e89a-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4e89a-111">Syntax</span></span>  
  
```xml  
<filter   
  type="traceFilterClassName"   
  initializeData="data" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4e89a-112">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="4e89a-112">Attributes and Elements</span></span>  
 <span data-ttu-id="4e89a-113">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="4e89a-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4e89a-114">Attributs</span><span class="sxs-lookup"><span data-stu-id="4e89a-114">Attributes</span></span>  
  
|<span data-ttu-id="4e89a-115">Attribut</span><span class="sxs-lookup"><span data-stu-id="4e89a-115">Attribute</span></span>|<span data-ttu-id="4e89a-116">Description</span><span class="sxs-lookup"><span data-stu-id="4e89a-116">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="4e89a-117">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="4e89a-117">Required attribute.</span></span><br /><br /> <span data-ttu-id="4e89a-118">Spécifie le type du filtre, qui doit hériter de la <xref:System.Diagnostics.TraceFilter> classe.</span><span class="sxs-lookup"><span data-stu-id="4e89a-118">Specifies the type of the filter, which should inherit from the <xref:System.Diagnostics.TraceFilter> class.</span></span> <span data-ttu-id="4e89a-119">Vous pouvez utiliser le nom qualifié d’espace de noms du type, ce qui correspond au type <xref:System.Type.FullName%2A> propriété, ou vous pouvez utiliser le nom de type qualifié complet, y compris les informations de l’assembly, qui correspondant à la <xref:System.Type.AssemblyQualifiedName%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="4e89a-119">You can use the namespace-qualified name of the type, which corresponds to the type's <xref:System.Type.FullName%2A> property, or you can use the fully qualified type name including the assembly information, which corresponds to the <xref:System.Type.AssemblyQualifiedName%2A> property.</span></span> <span data-ttu-id="4e89a-120">Pour plus d’informations sur les noms de types qualifiés complets, consultez [en spécifiant des noms de types qualifiés complets](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="4e89a-120">For information about fully qualified type names, see [Specifying Fully Qualified Type Names](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="4e89a-121">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="4e89a-121">Optional attribute.</span></span><br /><br /> <span data-ttu-id="4e89a-122">La chaîne passée au constructeur pour la classe de filtre spécifiée.</span><span class="sxs-lookup"><span data-stu-id="4e89a-122">The string passed to the constructor for the specified filter class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4e89a-123">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="4e89a-123">Child Elements</span></span>  
 <span data-ttu-id="4e89a-124">Aucun.</span><span class="sxs-lookup"><span data-stu-id="4e89a-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4e89a-125">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="4e89a-125">Parent Elements</span></span>  
  
|<span data-ttu-id="4e89a-126">Élément</span><span class="sxs-lookup"><span data-stu-id="4e89a-126">Element</span></span>|<span data-ttu-id="4e89a-127">Description</span><span class="sxs-lookup"><span data-stu-id="4e89a-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="4e89a-128">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4e89a-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="4e89a-129">Spécifie les écouteurs de trace qui collectent, stockent et acheminent les messages, ainsi que le niveau auquel un commutateur de trace est défini.</span><span class="sxs-lookup"><span data-stu-id="4e89a-129">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="4e89a-130">Contient les sources de trace qui lancent des messages de traçage.</span><span class="sxs-lookup"><span data-stu-id="4e89a-130">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="4e89a-131">Spécifie une source de trace qui lance des messages de traçage.</span><span class="sxs-lookup"><span data-stu-id="4e89a-131">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="4e89a-132">Contient des écouteurs qui collectent, stocker et acheminer les messages.</span><span class="sxs-lookup"><span data-stu-id="4e89a-132">Contains listeners that collect, store, and route messages.</span></span> <span data-ttu-id="4e89a-133">Les écouteurs dirigent la sortie de traçage vers une cible appropriée.</span><span class="sxs-lookup"><span data-stu-id="4e89a-133">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`add`|<span data-ttu-id="4e89a-134">Ajoute un écouteur à la collection `Listeners` pour une source de trace.</span><span class="sxs-lookup"><span data-stu-id="4e89a-134">Adds a listener to the `Listeners` collection for a trace source.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4e89a-135">Notes</span><span class="sxs-lookup"><span data-stu-id="4e89a-135">Remarks</span></span>  
 <span data-ttu-id="4e89a-136">Le `<filter>` élément doit être contenu dans un `<add>` élément pour un écouteur de trace source qui spécifie le type de l’écouteur, pas seulement le nom d’un écouteur défini dans un [ \<sharedListeners >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md).</span><span class="sxs-lookup"><span data-stu-id="4e89a-136">The `<filter>` element must be contained in an `<add>` element for a trace source listener that specifies the type of the listener, not just the name of a listener defined in a [\<sharedListeners>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md).</span></span> <span data-ttu-id="4e89a-137">Si l’écouteur est défini dans un [ \<sharedListeners >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md), le filtre de cet écouteur doit être défini dans cet élément.</span><span class="sxs-lookup"><span data-stu-id="4e89a-137">If the listener is defined in a [\<sharedListeners>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md), the filter for that listener must be defined in that element.</span></span>  
  
 <span data-ttu-id="4e89a-138">Cet élément peut être utilisé dans le fichier de configuration de l’ordinateur (Machine.config) et le fichier de configuration d’application.</span><span class="sxs-lookup"><span data-stu-id="4e89a-138">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4e89a-139">Exemple</span><span class="sxs-lookup"><span data-stu-id="4e89a-139">Example</span></span>  
 <span data-ttu-id="4e89a-140">L’exemple suivant montre comment utiliser le `<filter>` élément pour ajouter un filtre à l’écouteur `console` dans les `Listeners` collection pour la source de trace `myTraceSource`, en spécifiant le niveau d’événement en tant que filtre `Error`.</span><span class="sxs-lookup"><span data-stu-id="4e89a-140">The following example shows how to use the `<filter>` element to add a filter to the listener `console` in the `Listeners` collection for the trace source `myTraceSource`, specifying the filter event level as `Error`.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="myTraceSource" switchName="SourceSwitch"   
        switchType="System.Diagnostics.SourceSwitch"  >  
        <listeners>  
          <add name="console"   
            type="System.Diagnostics.ConsoleTraceListener" >  
            <filter type="System.Diagnostics.EventTypeFilter"   
              initializeData="Error" />  
          </add>  
          <remove name="Default" />  
        </listeners>  
      </source>  
    </sources>  
    <switches>  
      <add name="SourceSwitch" value="Warning" />  
    </switches>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4e89a-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4e89a-141">See Also</span></span>  
 <xref:System.Diagnostics.TraceSource>  
 <xref:System.Diagnostics.TraceListener>  
 <xref:System.Diagnostics.TraceListener.Filter%2A?displayProperty=nameWithType>  
 <xref:System.Diagnostics.TraceFilter>  
 [<span data-ttu-id="4e89a-142">Schéma des paramètres de trace et de débogage</span><span class="sxs-lookup"><span data-stu-id="4e89a-142">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
