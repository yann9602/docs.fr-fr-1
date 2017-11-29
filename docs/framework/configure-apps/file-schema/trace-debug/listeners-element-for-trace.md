---
title: "&lt;écouteurs&gt; , élément pour &lt;trace&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners
helpviewer_keywords:
- <listeners> element
- listeners element
ms.assetid: 1394c2c3-6304-46db-87c1-8e8b16f5ad5b
caps.latest.revision: "17"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 97d6673fddb20e99454bf97c87254049b82f0000
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltlistenersgt-element-for-lttracegt"></a><span data-ttu-id="b72d4-102">&lt;écouteurs&gt; , élément pour &lt;trace&gt;</span><span class="sxs-lookup"><span data-stu-id="b72d4-102">&lt;listeners&gt; Element for &lt;trace&gt;</span></span>
<span data-ttu-id="b72d4-103">Spécifie un écouteur qui collecte, stocke et achemine les messages.</span><span class="sxs-lookup"><span data-stu-id="b72d4-103">Specifies a listener that collects, stores, and routes messages.</span></span> <span data-ttu-id="b72d4-104">Les écouteurs dirigent la sortie de traçage vers une cible appropriée.</span><span class="sxs-lookup"><span data-stu-id="b72d4-104">Listeners direct the tracing output to an appropriate target.</span></span>  
  
 <span data-ttu-id="b72d4-105">\<configuration > élément</span><span class="sxs-lookup"><span data-stu-id="b72d4-105">\<configuration> Element</span></span>  
<span data-ttu-id="b72d4-106">\<System.Diagnostics > élément</span><span class="sxs-lookup"><span data-stu-id="b72d4-106">\<system.diagnostics> Element</span></span>  
<span data-ttu-id="b72d4-107">\<trace > élément</span><span class="sxs-lookup"><span data-stu-id="b72d4-107">\<trace> Element</span></span>  
<span data-ttu-id="b72d4-108">\<écouteurs >, élément pour \<trace ></span><span class="sxs-lookup"><span data-stu-id="b72d4-108">\<listeners> Element for \<trace></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b72d4-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b72d4-109">Syntax</span></span>  
  
```xml  
<listeners>   
  <add>...</add>  
  <clear/>  
  <remove ... />  
</listeners>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b72d4-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="b72d4-110">Attributes and Elements</span></span>  
 <span data-ttu-id="b72d4-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="b72d4-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b72d4-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="b72d4-112">Attributes</span></span>  
 <span data-ttu-id="b72d4-113">Aucun</span><span class="sxs-lookup"><span data-stu-id="b72d4-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b72d4-114">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="b72d4-114">Child Elements</span></span>  
  
|<span data-ttu-id="b72d4-115">Élément</span><span class="sxs-lookup"><span data-stu-id="b72d4-115">Element</span></span>|<span data-ttu-id="b72d4-116">Description</span><span class="sxs-lookup"><span data-stu-id="b72d4-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b72d4-117">\<add></span><span class="sxs-lookup"><span data-stu-id="b72d4-117">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/add-element-for-listeners-for-trace.md)|<span data-ttu-id="b72d4-118">Ajoute un écouteur à la collection `Listeners`.</span><span class="sxs-lookup"><span data-stu-id="b72d4-118">Adds a listener to the `Listeners` collection.</span></span>|  
|[<span data-ttu-id="b72d4-119">\<clear></span><span class="sxs-lookup"><span data-stu-id="b72d4-119">\<clear></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/clear-element-for-listeners-for-trace.md)|<span data-ttu-id="b72d4-120">Efface la collection `Listeners` de la trace.</span><span class="sxs-lookup"><span data-stu-id="b72d4-120">Clears the `Listeners` collection for trace.</span></span>|  
|[<span data-ttu-id="b72d4-121">\<remove></span><span class="sxs-lookup"><span data-stu-id="b72d4-121">\<remove></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/remove-element-for-listeners-for-trace.md)|<span data-ttu-id="b72d4-122">Supprime un écouteur de la `Listeners` collection.</span><span class="sxs-lookup"><span data-stu-id="b72d4-122">Removes a listener from the `Listeners` collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b72d4-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="b72d4-123">Parent Elements</span></span>  
  
|<span data-ttu-id="b72d4-124">Élément</span><span class="sxs-lookup"><span data-stu-id="b72d4-124">Element</span></span>|<span data-ttu-id="b72d4-125">Description</span><span class="sxs-lookup"><span data-stu-id="b72d4-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="b72d4-126">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b72d4-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="b72d4-127">Spécifie l'élément racine de la section de configuration ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="b72d4-127">Specifies the root element for the ASP.NET configuration section.</span></span>|  
|`trace`|<span data-ttu-id="b72d4-128">Contient les écouteurs qui collectent, stockent et acheminent les messages de traçage.</span><span class="sxs-lookup"><span data-stu-id="b72d4-128">Contains listeners that collect, store, and route tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b72d4-129">Remarques</span><span class="sxs-lookup"><span data-stu-id="b72d4-129">Remarks</span></span>  
 <span data-ttu-id="b72d4-130">Le <xref:System.Diagnostics.Debug> et <xref:System.Diagnostics.Trace> classes partagent le même **écouteurs** collection.</span><span class="sxs-lookup"><span data-stu-id="b72d4-130">The <xref:System.Diagnostics.Debug> and <xref:System.Diagnostics.Trace> classes share the same **Listeners** collection.</span></span> <span data-ttu-id="b72d4-131">Si vous ajoutez un objet écouteur à la collection dans un de ces classes, l’autre classe utilise le même écouteur.</span><span class="sxs-lookup"><span data-stu-id="b72d4-131">If you add a listener object to the collection in one of these classes, the other class uses the same listener.</span></span> <span data-ttu-id="b72d4-132">Les classes d’écouteur livrées avec le .NET Framework dérivent la <xref:System.Diagnostics.TraceListener> classe.</span><span class="sxs-lookup"><span data-stu-id="b72d4-132">The listener classes shipped with the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="b72d4-133">Fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="b72d4-133">Configuration File</span></span>  
 <span data-ttu-id="b72d4-134">Cet élément peut être utilisé dans le fichier de configuration de l’ordinateur (Machine.config) et le fichier de configuration d’application.</span><span class="sxs-lookup"><span data-stu-id="b72d4-134">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b72d4-135">Exemple</span><span class="sxs-lookup"><span data-stu-id="b72d4-135">Example</span></span>  
 <span data-ttu-id="b72d4-136">L’exemple suivant montre comment utiliser le  **\<écouteurs >** élément pour ajouter les écouteurs `MyListener` et `MyEventListener` à la **écouteurs** collection.</span><span class="sxs-lookup"><span data-stu-id="b72d4-136">The following example shows how to use the **\<listeners>** element to add the listeners `MyListener` and `MyEventListener` to the **Listeners** collection.</span></span> <span data-ttu-id="b72d4-137">`MyListener`Crée un fichier appelé `MyListener.log` et écrit la sortie dans le fichier.</span><span class="sxs-lookup"><span data-stu-id="b72d4-137">`MyListener` creates a file called `MyListener.log` and writes the output to the file.</span></span> <span data-ttu-id="b72d4-138">`MyEventListener`Crée une entrée dans le journal des événements.</span><span class="sxs-lookup"><span data-stu-id="b72d4-138">`MyEventListener` creates an entry in the event log.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <trace autoflush="true" indentsize="0">  
      <listeners>  
        <add name="myListener"   
          type="System.Diagnostics.TextWriterTraceListener,   
            system, version=1.0.3300.0, Culture=neutral,   
            PublicKeyToken=b77a5c561934e089"   
          initializeData="c:\myListener.log" />  
        <add name="MyEventListener"  
          type="System.Diagnostics.EventLogTraceListener,   
            system, version=1.0.3300.0, Culture=neutral,   
            PublicKeyToken=b77a5c561934e089"  
          initializeData="MyConfigEventLog"/>  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b72d4-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b72d4-139">See Also</span></span>  
 <xref:System.Diagnostics.TraceListener>  
 [<span data-ttu-id="b72d4-140">Schéma des paramètres de trace et de débogage</span><span class="sxs-lookup"><span data-stu-id="b72d4-140">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
