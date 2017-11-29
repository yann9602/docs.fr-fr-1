---
title: "&lt;source&gt; élément"
ms.date: 09/29/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source
- http://schemas.microsoft.com/.NetConfiguration/v2.0#source
helpviewer_keywords:
- <source> element
- source element
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 129888986a933fe875aade153f6becd8439d4704
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltsourcegt-element"></a><span data-ttu-id="55d93-102">&lt;source&gt; élément</span><span class="sxs-lookup"><span data-stu-id="55d93-102">&lt;source&gt; Element</span></span>
<span data-ttu-id="55d93-103">Spécifie une source de trace qui lance des messages de traçage.</span><span class="sxs-lookup"><span data-stu-id="55d93-103">Specifies a trace source that initiates tracing messages.</span></span>  
  
 <span data-ttu-id="55d93-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="55d93-104">\<configuration></span></span>  
<span data-ttu-id="55d93-105">\<System.Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="55d93-105">\<system.diagnostics></span></span>  
<span data-ttu-id="55d93-106">\<sources ></span><span class="sxs-lookup"><span data-stu-id="55d93-106">\<sources></span></span>  
<span data-ttu-id="55d93-107">\<source ></span><span class="sxs-lookup"><span data-stu-id="55d93-107">\<source></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55d93-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="55d93-108">Syntax</span></span>  
  
```xml  
<source>   
  <listeners>...</listeners>  
</source>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="55d93-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="55d93-109">Attributes and Elements</span></span>  
 <span data-ttu-id="55d93-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="55d93-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="55d93-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="55d93-111">Attributes</span></span>  
  
|<span data-ttu-id="55d93-112">Attribut</span><span class="sxs-lookup"><span data-stu-id="55d93-112">Attribute</span></span>|<span data-ttu-id="55d93-113">Description</span><span class="sxs-lookup"><span data-stu-id="55d93-113">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="55d93-114">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="55d93-114">Optional attribute.</span></span><br /><br /> <span data-ttu-id="55d93-115">Spécifie le nom de la source de trace.</span><span class="sxs-lookup"><span data-stu-id="55d93-115">Specifies the name of the trace source.</span></span>|  
|`switchName`|<span data-ttu-id="55d93-116">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="55d93-116">Optional attribute.</span></span><br /><br /> <span data-ttu-id="55d93-117">Spécifie le nom d’une instance de commutateur de trace dans l’application.</span><span class="sxs-lookup"><span data-stu-id="55d93-117">Specifies the name of a trace switch instance in the application.</span></span> <span data-ttu-id="55d93-118">Si le commutateur n’est pas identifié dans un `<switches>` élément, la valeur spécifie le niveau du commutateur.</span><span class="sxs-lookup"><span data-stu-id="55d93-118">If the switch is not identified in a `<switches>` element, the value specifies the level for the switch.</span></span>|  
|`switchType`|<span data-ttu-id="55d93-119">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="55d93-119">Optional attribute.</span></span><br /><br /> <span data-ttu-id="55d93-120">Spécifie le type du commutateur de trace.</span><span class="sxs-lookup"><span data-stu-id="55d93-120">Specifies the type of the trace switch.</span></span> <span data-ttu-id="55d93-121">Le cas échéant, le type doit être un nom de classe valide et ne peut pas être une chaîne vide.</span><span class="sxs-lookup"><span data-stu-id="55d93-121">If present, the type must be a valid class name and cannot be an empty string.</span></span>|  
|`extraAttribute`|<span data-ttu-id="55d93-122">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="55d93-122">Optional attribute.</span></span><br /><br /> <span data-ttu-id="55d93-123">Spécifie la valeur d’un attribut spécifique à la source de trace identifié par le <xref:System.Diagnostics.TraceSource.GetSupportedAttributes%2A> méthode pour cette source de trace.</span><span class="sxs-lookup"><span data-stu-id="55d93-123">Specifies the value for a trace source-specific attribute identified by the <xref:System.Diagnostics.TraceSource.GetSupportedAttributes%2A> method for that trace source.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="55d93-124">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="55d93-124">Child Elements</span></span>  
  
|<span data-ttu-id="55d93-125">Élément</span><span class="sxs-lookup"><span data-stu-id="55d93-125">Element</span></span>|<span data-ttu-id="55d93-126">Description</span><span class="sxs-lookup"><span data-stu-id="55d93-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="55d93-127">\<listeners></span><span class="sxs-lookup"><span data-stu-id="55d93-127">\<listeners></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/listeners-element-for-source.md)|<span data-ttu-id="55d93-128">Contient des écouteurs qui collectent, stocker et acheminer les messages.</span><span class="sxs-lookup"><span data-stu-id="55d93-128">Contains listeners that collect, store, and route messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="55d93-129">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="55d93-129">Parent Elements</span></span>  
  
|<span data-ttu-id="55d93-130">Élément</span><span class="sxs-lookup"><span data-stu-id="55d93-130">Element</span></span>|<span data-ttu-id="55d93-131">Description</span><span class="sxs-lookup"><span data-stu-id="55d93-131">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="55d93-132">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="55d93-132">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="55d93-133">Spécifie les écouteurs de trace qui collectent, stockent et acheminent les messages, ainsi que le niveau auquel un commutateur de trace est défini.</span><span class="sxs-lookup"><span data-stu-id="55d93-133">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="55d93-134">Contient les sources de trace qui lancent des messages de traçage.</span><span class="sxs-lookup"><span data-stu-id="55d93-134">Contains trace sources that initiate tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="55d93-135">Remarques</span><span class="sxs-lookup"><span data-stu-id="55d93-135">Remarks</span></span>  
 <span data-ttu-id="55d93-136">Cet élément peut être utilisé dans le fichier de configuration de l’ordinateur (Machine.config) et le fichier de configuration d’application.</span><span class="sxs-lookup"><span data-stu-id="55d93-136">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="55d93-137">Exemple</span><span class="sxs-lookup"><span data-stu-id="55d93-137">Example</span></span>  
 <span data-ttu-id="55d93-138">L’exemple suivant montre comment utiliser le `<source>` élément à ajouter la source de suivi `mySource` et pour définir le niveau du commutateur source nommé `sourceSwitch`.</span><span class="sxs-lookup"><span data-stu-id="55d93-138">The following example shows how to use the `<source>` element to add the trace source `mySource` and to set the level for the source switch named `sourceSwitch`.</span></span> <span data-ttu-id="55d93-139">Un écouteur de suivi de console est ajouté qui écrit des informations de traçage dans la console.</span><span class="sxs-lookup"><span data-stu-id="55d93-139">A console trace listener is added that writes trace information to the console.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="mySource" switchName="sourceSwitch" switchType="System.Diagnostics.SourceSwitch"  >  
        <listeners>  
          <add name="console" type="System.Diagnostics.ConsoleTraceListener" >  
            <filter type="System.Diagnostics.EventTypeFilter" initializeData="Error" />  
          </add>  
          <remove name="Default" />  
        </listeners>  
      </source>  
    </sources>  
        <switches>  
           <add name="sourceSwitch" value="Warning" />  
        </switches>    
  </system.diagnostics>   
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="55d93-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="55d93-140">See Also</span></span>  
 [<span data-ttu-id="55d93-141">Schéma des paramètres de trace et de débogage</span><span class="sxs-lookup"><span data-stu-id="55d93-141">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)  
 [<span data-ttu-id="55d93-142">Commutateurs de suivi</span><span class="sxs-lookup"><span data-stu-id="55d93-142">Trace Switches</span></span>](../../../../../docs/framework/debug-trace-profile/trace-switches.md)
