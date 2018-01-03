---
title: "&lt;Désactivez&gt; élément &lt;écouteurs&gt; pour &lt;trace&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/clear
helpviewer_keywords:
- clear element for <listeners> for <trace>
- <clear> element for <listeners> for <trace>
ms.assetid: b44732a8-271f-4a06-ba9e-fe3298d6f192
caps.latest.revision: "11"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: b2739cc5eaa6a1e43c06849e1b00f7ac8bd531e7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltcleargt-element-for-ltlistenersgt-for-lttracegt"></a><span data-ttu-id="8ac7c-102">&lt;Désactivez&gt; élément &lt;écouteurs&gt; pour &lt;trace&gt;</span><span class="sxs-lookup"><span data-stu-id="8ac7c-102">&lt;clear&gt; Element for &lt;listeners&gt; for &lt;trace&gt;</span></span>
<span data-ttu-id="8ac7c-103">Efface la collection `Listeners` de la trace.</span><span class="sxs-lookup"><span data-stu-id="8ac7c-103">Clears the `Listeners` collection for trace.</span></span>  
  
 <span data-ttu-id="8ac7c-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="8ac7c-104">\<configuration></span></span>  
<span data-ttu-id="8ac7c-105">\<System.Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="8ac7c-105">\<system.diagnostics></span></span>  
<span data-ttu-id="8ac7c-106">\<trace ></span><span class="sxs-lookup"><span data-stu-id="8ac7c-106">\<trace></span></span>  
<span data-ttu-id="8ac7c-107">\<écouteurs ></span><span class="sxs-lookup"><span data-stu-id="8ac7c-107">\<listeners></span></span>  
<span data-ttu-id="8ac7c-108">\<Désactivez ></span><span class="sxs-lookup"><span data-stu-id="8ac7c-108">\<clear></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ac7c-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8ac7c-109">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8ac7c-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="8ac7c-110">Attributes and Elements</span></span>  
 <span data-ttu-id="8ac7c-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="8ac7c-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8ac7c-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="8ac7c-112">Attributes</span></span>  
 <span data-ttu-id="8ac7c-113">Aucun.</span><span class="sxs-lookup"><span data-stu-id="8ac7c-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="8ac7c-114">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="8ac7c-114">Child Elements</span></span>  
 <span data-ttu-id="8ac7c-115">Aucun.</span><span class="sxs-lookup"><span data-stu-id="8ac7c-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8ac7c-116">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="8ac7c-116">Parent Elements</span></span>  
  
|<span data-ttu-id="8ac7c-117">Élément</span><span class="sxs-lookup"><span data-stu-id="8ac7c-117">Element</span></span>|<span data-ttu-id="8ac7c-118">Description</span><span class="sxs-lookup"><span data-stu-id="8ac7c-118">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="8ac7c-119">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8ac7c-119">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="8ac7c-120">Spécifie les écouteurs de trace qui collectent, stockent et acheminent les messages, ainsi que le niveau auquel un commutateur de trace est défini.</span><span class="sxs-lookup"><span data-stu-id="8ac7c-120">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`trace`|<span data-ttu-id="8ac7c-121">Contient les écouteurs qui collectent, stockent et acheminent les messages de traçage.</span><span class="sxs-lookup"><span data-stu-id="8ac7c-121">Contains listeners that collect, store, and route tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="8ac7c-122">Contient des écouteurs qui collectent, stocker et acheminer les messages.</span><span class="sxs-lookup"><span data-stu-id="8ac7c-122">Contains listeners that collect, store, and route messages.</span></span> <span data-ttu-id="8ac7c-123">Les écouteurs dirigent la sortie de traçage vers une cible appropriée.</span><span class="sxs-lookup"><span data-stu-id="8ac7c-123">Listeners direct the tracing output to an appropriate target.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8ac7c-124">Notes</span><span class="sxs-lookup"><span data-stu-id="8ac7c-124">Remarks</span></span>  
 <span data-ttu-id="8ac7c-125">Le `<clear>` élément supprime tous les écouteurs de la `Listeners` collection de la trace.</span><span class="sxs-lookup"><span data-stu-id="8ac7c-125">The `<clear>` element removes all listeners from the `Listeners` collection for trace.</span></span> <span data-ttu-id="8ac7c-126">Vous pouvez utiliser la `<clear>` élément avant d’utiliser le `<add>` pour garantir l’aucun autre écouteur actif dans la collection.</span><span class="sxs-lookup"><span data-stu-id="8ac7c-126">You can use the `<clear>` element before using the `<add>` element to be certain there are no other active listeners in the collection.</span></span>  
  
 <span data-ttu-id="8ac7c-127">Vous pouvez effacer le `Listeners` collection par programme en appelant le <xref:System.Diagnostics.TraceListenerCollection.Clear%2A> méthode sur le <xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=nameWithType> propriété (`System.Diagnostics.Trace.Listeners.Clear()`).</span><span class="sxs-lookup"><span data-stu-id="8ac7c-127">You can clear the `Listeners` collection programmatically by calling the <xref:System.Diagnostics.TraceListenerCollection.Clear%2A> method on the <xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=nameWithType> property (`System.Diagnostics.Trace.Listeners.Clear()`).</span></span>  
  
 <span data-ttu-id="8ac7c-128">Cet élément peut être utilisé dans le fichier de configuration de l’ordinateur (Machine.config) et le fichier de configuration d’application.</span><span class="sxs-lookup"><span data-stu-id="8ac7c-128">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8ac7c-129">Le `<clear>` élément supprime le <xref:System.Diagnostics.DefaultTraceListener> à partir de la `Listeners` collection, la modification du comportement de la <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>, et <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> méthodes.</span><span class="sxs-lookup"><span data-stu-id="8ac7c-129">The `<clear>` element removes the <xref:System.Diagnostics.DefaultTraceListener> from the `Listeners` collection, altering the behavior of the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>, and <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="8ac7c-130">Appeler un `Assert` ou `Fail` normalement la méthode employée dans l’affichage d’un message.</span><span class="sxs-lookup"><span data-stu-id="8ac7c-130">Calling an `Assert` or `Fail` method normally results in the display of a message box.</span></span> <span data-ttu-id="8ac7c-131">Toutefois, la boîte de message s’affiche pas si le <xref:System.Diagnostics.DefaultTraceListener> ne figure pas dans le `Listeners` collection.</span><span class="sxs-lookup"><span data-stu-id="8ac7c-131">However, the message box is not displayed if the <xref:System.Diagnostics.DefaultTraceListener> is not in the `Listeners` collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8ac7c-132">Exemple</span><span class="sxs-lookup"><span data-stu-id="8ac7c-132">Example</span></span>  
 <span data-ttu-id="8ac7c-133">L’exemple suivant montre comment utiliser le `<clear>` élément avant d’utiliser le `<add>` élément pour ajouter l’écouteur `console` à la `Listeners` collection de la trace.</span><span class="sxs-lookup"><span data-stu-id="8ac7c-133">The following example shows how to use the `<clear>` element before using the `<add>` element to add the listener `console` to the `Listeners` collection for trace.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <trace autoflush="false" indentsize="4">  
      <listeners>  
        <clear/>  
        <add name="console"   
          type="System.Diagnostics.ConsoleTraceListener" >  
          <filter type="System.Diagnostics.EventTypeFilter"   
            initializeData="Error" />  
        </add>  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration>   
```  
  
## <a name="see-also"></a><span data-ttu-id="8ac7c-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8ac7c-134">See Also</span></span>  
 <xref:System.Diagnostics.Trace.Listeners%2A>  
 <xref:System.Diagnostics.Trace>  
 <xref:System.Diagnostics.Debug>  
 <xref:System.Diagnostics.TraceSource>  
 [<span data-ttu-id="8ac7c-135">Schéma des paramètres de trace et de débogage</span><span class="sxs-lookup"><span data-stu-id="8ac7c-135">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)  
 [<span data-ttu-id="8ac7c-136">\<remove></span><span class="sxs-lookup"><span data-stu-id="8ac7c-136">\<remove></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/remove-element-for-listeners-for-trace.md)  
 [<span data-ttu-id="8ac7c-137">Écouteurs de suivi</span><span class="sxs-lookup"><span data-stu-id="8ac7c-137">Trace Listeners</span></span>](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
