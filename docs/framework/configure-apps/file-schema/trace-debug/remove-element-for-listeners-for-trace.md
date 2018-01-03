---
title: "&lt;supprimer&gt; élément &lt;écouteurs&gt; pour &lt;trace&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/remove
helpviewer_keywords:
- remove element
- <remove> element
ms.assetid: 9a5cd1b5-be1a-485f-8f0c-2890ad3ef3e0
caps.latest.revision: "12"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 7bc4136fb917ee9b63b7cca26ba1834de21f542e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltremovegt-element-for-ltlistenersgt-for-lttracegt"></a><span data-ttu-id="e3ce9-102">&lt;supprimer&gt; élément &lt;écouteurs&gt; pour &lt;trace&gt;</span><span class="sxs-lookup"><span data-stu-id="e3ce9-102">&lt;remove&gt; Element for &lt;listeners&gt; for &lt;trace&gt;</span></span>
<span data-ttu-id="e3ce9-103">Supprime un écouteur de la **écouteurs** collection.</span><span class="sxs-lookup"><span data-stu-id="e3ce9-103">Removes a listener from the **Listeners** collection.</span></span>  
  
 <span data-ttu-id="e3ce9-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="e3ce9-104">\<configuration></span></span>  
<span data-ttu-id="e3ce9-105">\<System.Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="e3ce9-105">\<system.diagnostics></span></span>  
<span data-ttu-id="e3ce9-106">\<trace ></span><span class="sxs-lookup"><span data-stu-id="e3ce9-106">\<trace></span></span>  
<span data-ttu-id="e3ce9-107">\<écouteurs ></span><span class="sxs-lookup"><span data-stu-id="e3ce9-107">\<listeners></span></span>  
<span data-ttu-id="e3ce9-108">\<Supprimer ></span><span class="sxs-lookup"><span data-stu-id="e3ce9-108">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3ce9-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e3ce9-109">Syntax</span></span>  
  
```xml  
<remove name="listener name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e3ce9-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="e3ce9-110">Attributes and Elements</span></span>  
 <span data-ttu-id="e3ce9-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="e3ce9-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e3ce9-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="e3ce9-112">Attributes</span></span>  
  
|<span data-ttu-id="e3ce9-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="e3ce9-113">Attribute</span></span>|<span data-ttu-id="e3ce9-114">Description</span><span class="sxs-lookup"><span data-stu-id="e3ce9-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e3ce9-115">**name**</span><span class="sxs-lookup"><span data-stu-id="e3ce9-115">**name**</span></span>|<span data-ttu-id="e3ce9-116">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="e3ce9-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="e3ce9-117">Le nom de l’écouteur à supprimer de la **écouteurs** collection.</span><span class="sxs-lookup"><span data-stu-id="e3ce9-117">The name of the listener to remove from the **Listeners** collection.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e3ce9-118">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="e3ce9-118">Child Elements</span></span>  
 <span data-ttu-id="e3ce9-119">Aucun.</span><span class="sxs-lookup"><span data-stu-id="e3ce9-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e3ce9-120">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="e3ce9-120">Parent Elements</span></span>  
  
|<span data-ttu-id="e3ce9-121">Élément</span><span class="sxs-lookup"><span data-stu-id="e3ce9-121">Element</span></span>|<span data-ttu-id="e3ce9-122">Description</span><span class="sxs-lookup"><span data-stu-id="e3ce9-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="e3ce9-123">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e3ce9-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`listeners`|<span data-ttu-id="e3ce9-124">Spécifie un écouteur qui collecte, stocke et achemine les messages.</span><span class="sxs-lookup"><span data-stu-id="e3ce9-124">Specifies a listener that collects, stores, and routes messages.</span></span> <span data-ttu-id="e3ce9-125">Les écouteurs dirigent la sortie de traçage vers une cible appropriée.</span><span class="sxs-lookup"><span data-stu-id="e3ce9-125">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="e3ce9-126">Spécifie les écouteurs de trace qui collectent, stockent et acheminent les messages, ainsi que le niveau auquel un commutateur de trace est défini.</span><span class="sxs-lookup"><span data-stu-id="e3ce9-126">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`trace`|<span data-ttu-id="e3ce9-127">Configure le service de suivi ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="e3ce9-127">Configures the ASP.NET trace service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e3ce9-128">Notes</span><span class="sxs-lookup"><span data-stu-id="e3ce9-128">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e3ce9-129">Suppression de la <xref:System.Diagnostics.DefaultTraceListener> à partir de la `Listeners` collection modifie le comportement de la <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>, et <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> méthodes.</span><span class="sxs-lookup"><span data-stu-id="e3ce9-129">Removing the <xref:System.Diagnostics.DefaultTraceListener> from the `Listeners` collection alters the behavior of the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>, and <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="e3ce9-130">Appeler un `Assert` ou `Fail` méthode normalement provoque l’affichage d’un message, mais la boîte de message ne s’affiche pas si le <xref:System.Diagnostics.DefaultTraceListener> ne figure pas dans le `Listeners` collection.</span><span class="sxs-lookup"><span data-stu-id="e3ce9-130">Calling an `Assert` or `Fail` method normally results in the display of a message box, however the message box is not displayed if the <xref:System.Diagnostics.DefaultTraceListener> is not in the `Listeners` collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e3ce9-131">Exemple</span><span class="sxs-lookup"><span data-stu-id="e3ce9-131">Example</span></span>  
 <span data-ttu-id="e3ce9-132">L’exemple suivant montre comment supprimer l’écouteur de trace par défaut de la trace **écouteurs** collection.</span><span class="sxs-lookup"><span data-stu-id="e3ce9-132">The following example shows how to remove the default trace listener from the trace **Listeners** collection.</span></span>  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <trace autoflush="true" indentsize="0">  
         <listeners>  
            <remove name="Default" />  
         </listeners>  
      </trace>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e3ce9-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e3ce9-133">See Also</span></span>  
 <xref:System.Diagnostics.TraceListener>  
 <xref:System.Diagnostics.DefaultTraceListener>  
 <xref:System.Diagnostics.TextWriterTraceListener>  
 <xref:System.Diagnostics.EventLogTraceListener>  
 [<span data-ttu-id="e3ce9-134">Schéma des paramètres de trace et de débogage</span><span class="sxs-lookup"><span data-stu-id="e3ce9-134">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
