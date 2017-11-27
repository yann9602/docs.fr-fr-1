---
title: "&lt;TypeParameter&gt;, élément (.NET Native)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d37bb1b7-1ddc-4c6d-8ecf-583f804a2479
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 94c7b2fe5cf586c0f8a58d1698cdf3870b5b5c96
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="lttypeparametergt-element-net-native"></a><span data-ttu-id="e51e3-102">&lt;TypeParameter&gt;, élément (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="e51e3-102">&lt;TypeParameter&gt; Element (.NET Native)</span></span>
<span data-ttu-id="e51e3-103">Applique la stratégie au type représenté par un argument Type passé à une méthode.</span><span class="sxs-lookup"><span data-stu-id="e51e3-103">Applies policy to the type represented by a Type argument passed to a method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e51e3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e51e3-104">Syntax</span></span>  
  
```xml  
<Parameter Name="parameter_name"  
           Activate="policy_type"  
           Browse="policy_type"  
           Dynamic="policy_type"  
           Serialize="policy_type"  
           DataContractSerializer="policy_type"  
           DataContractJsonSerializer="policy_type"  
           XmlSerializer="policy_type"  
           MarshalObject="policy_type"  
           MarshalDelegate="policy_type"  
           MarshalStructure="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e51e3-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="e51e3-105">Attributes and Elements</span></span>  
 <span data-ttu-id="e51e3-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="e51e3-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e51e3-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="e51e3-107">Attributes</span></span>  
  
|<span data-ttu-id="e51e3-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="e51e3-108">Attribute</span></span>|<span data-ttu-id="e51e3-109">Type d'attribut</span><span class="sxs-lookup"><span data-stu-id="e51e3-109">Attribute type</span></span>|<span data-ttu-id="e51e3-110">Description</span><span class="sxs-lookup"><span data-stu-id="e51e3-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="e51e3-111">Général</span><span class="sxs-lookup"><span data-stu-id="e51e3-111">General</span></span>|<span data-ttu-id="e51e3-112">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="e51e3-112">Required attribute.</span></span> <span data-ttu-id="e51e3-113">Nom du paramètre de type <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="e51e3-113">The name of the parameter of type <xref:System.Type>.</span></span> <span data-ttu-id="e51e3-114">Par exemple, pour la signature de méthode `Type.GetInterfaceMap(Type interfaceType)`, la valeur de l'attribut `Name` est « interfaceType ».</span><span class="sxs-lookup"><span data-stu-id="e51e3-114">For example, for the method signature `Type.GetInterfaceMap(Type interfaceType)`, the value of the `Name` attribute is "interfaceType".</span></span>|  
|`Activate`|<span data-ttu-id="e51e3-115">Réflexion</span><span class="sxs-lookup"><span data-stu-id="e51e3-115">Reflection</span></span>|<span data-ttu-id="e51e3-116">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="e51e3-116">Optional attribute.</span></span> <span data-ttu-id="e51e3-117">Contrôle l'accès aux constructeurs pour permettre l'activation d'instances au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="e51e3-117">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="e51e3-118">Réflexion</span><span class="sxs-lookup"><span data-stu-id="e51e3-118">Reflection</span></span>|<span data-ttu-id="e51e3-119">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="e51e3-119">Optional attribute.</span></span> <span data-ttu-id="e51e3-120">Contrôle la demande d'informations sur les éléments de programme, mais ne permet pas l'accès au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="e51e3-120">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="e51e3-121">Réflexion</span><span class="sxs-lookup"><span data-stu-id="e51e3-121">Reflection</span></span>|<span data-ttu-id="e51e3-122">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="e51e3-122">Optional attribute.</span></span> <span data-ttu-id="e51e3-123">Contrôle l'accès à l'exécution à tous les membres de types, y compris les constructeurs, les méthodes, les champs, les propriétés et les événements, pour permettre la programmation dynamique.</span><span class="sxs-lookup"><span data-stu-id="e51e3-123">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="e51e3-124">Sérialisation</span><span class="sxs-lookup"><span data-stu-id="e51e3-124">Serialization</span></span>|<span data-ttu-id="e51e3-125">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="e51e3-125">Optional attribute.</span></span> <span data-ttu-id="e51e3-126">Contrôle l'accès au moment de l'exécution aux constructeurs, champs et propriétés, pour permettre la sérialisation et la désérialisation des instances de types par des bibliothèques comme le sérialiseur JSON Newtonsoft.</span><span class="sxs-lookup"><span data-stu-id="e51e3-126">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="e51e3-127">Sérialisation</span><span class="sxs-lookup"><span data-stu-id="e51e3-127">Serialization</span></span>|<span data-ttu-id="e51e3-128">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="e51e3-128">Optional attribute.</span></span> <span data-ttu-id="e51e3-129">Contrôle la stratégie pour la sérialisation qui utilise la classe <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e51e3-129">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="e51e3-130">Sérialisation</span><span class="sxs-lookup"><span data-stu-id="e51e3-130">Serialization</span></span>|<span data-ttu-id="e51e3-131">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="e51e3-131">Optional attribute.</span></span> <span data-ttu-id="e51e3-132">Contrôle la stratégie pour la sérialisation JSON qui utilise la classe <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e51e3-132">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="e51e3-133">Sérialisation</span><span class="sxs-lookup"><span data-stu-id="e51e3-133">Serialization</span></span>|<span data-ttu-id="e51e3-134">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="e51e3-134">Optional attribute.</span></span> <span data-ttu-id="e51e3-135">Contrôle la stratégie pour la sérialisation XML qui utilise la classe <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e51e3-135">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="e51e3-136">Interop</span><span class="sxs-lookup"><span data-stu-id="e51e3-136">Interop</span></span>|<span data-ttu-id="e51e3-137">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="e51e3-137">Optional attribute.</span></span> <span data-ttu-id="e51e3-138">Contrôle la stratégie pour le marshaling des types de références vers Windows Runtime et COM.</span><span class="sxs-lookup"><span data-stu-id="e51e3-138">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="e51e3-139">Interop</span><span class="sxs-lookup"><span data-stu-id="e51e3-139">Interop</span></span>|<span data-ttu-id="e51e3-140">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="e51e3-140">Optional attribute.</span></span> <span data-ttu-id="e51e3-141">Contrôle la stratégie pour le marshaling des types de délégués comme pointeurs de fonction vers du code natif.</span><span class="sxs-lookup"><span data-stu-id="e51e3-141">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="e51e3-142">Interop</span><span class="sxs-lookup"><span data-stu-id="e51e3-142">Interop</span></span>|<span data-ttu-id="e51e3-143">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="e51e3-143">Optional attribute.</span></span> <span data-ttu-id="e51e3-144">Contrôle la stratégie pour le marshaling des types de valeurs vers du code natif.</span><span class="sxs-lookup"><span data-stu-id="e51e3-144">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="e51e3-145">Name (attribut)</span><span class="sxs-lookup"><span data-stu-id="e51e3-145">Name attribute</span></span>  
  
|<span data-ttu-id="e51e3-146">Valeur</span><span class="sxs-lookup"><span data-stu-id="e51e3-146">Value</span></span>|<span data-ttu-id="e51e3-147">Description</span><span class="sxs-lookup"><span data-stu-id="e51e3-147">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e51e3-148">*nom_paramètre*</span><span class="sxs-lookup"><span data-stu-id="e51e3-148">*parameter_name*</span></span>|<span data-ttu-id="e51e3-149">Nom du paramètre de type <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="e51e3-149">The name of the parameter of type <xref:System.Type>.</span></span> <span data-ttu-id="e51e3-150">Par exemple, pour la signature de méthode `Type.GetInterfaceMap(Type interfaceType)`, la valeur de l'attribut `Name` est « interfaceType ».</span><span class="sxs-lookup"><span data-stu-id="e51e3-150">For example, for the method signature `Type.GetInterfaceMap(Type interfaceType)`, the value of the `Name` attribute is "interfaceType".</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="e51e3-151">Tous les autres attributs</span><span class="sxs-lookup"><span data-stu-id="e51e3-151">All other attributes</span></span>  
  
|<span data-ttu-id="e51e3-152">Valeur</span><span class="sxs-lookup"><span data-stu-id="e51e3-152">Value</span></span>|<span data-ttu-id="e51e3-153">Description</span><span class="sxs-lookup"><span data-stu-id="e51e3-153">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e51e3-154">*paramètre_stratégie*</span><span class="sxs-lookup"><span data-stu-id="e51e3-154">*policy_setting*</span></span>|<span data-ttu-id="e51e3-155">Paramètre à appliquer à ce type de stratégie.</span><span class="sxs-lookup"><span data-stu-id="e51e3-155">The setting to apply to this policy type.</span></span> <span data-ttu-id="e51e3-156">Les valeurs possibles sont `All`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal` et `Required All`.</span><span class="sxs-lookup"><span data-stu-id="e51e3-156">Possible values are `All`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="e51e3-157">Pour plus d’informations, consultez [Paramètres de stratégie de directive runtime](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="e51e3-157">For more information, see [Runtime Directive Policy Settings](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e51e3-158">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="e51e3-158">Child Elements</span></span>  
 <span data-ttu-id="e51e3-159">Aucun.</span><span class="sxs-lookup"><span data-stu-id="e51e3-159">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e51e3-160">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="e51e3-160">Parent Elements</span></span>  
  
|<span data-ttu-id="e51e3-161">Élément</span><span class="sxs-lookup"><span data-stu-id="e51e3-161">Element</span></span>|<span data-ttu-id="e51e3-162">Description</span><span class="sxs-lookup"><span data-stu-id="e51e3-162">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e51e3-163">\<Method></span><span class="sxs-lookup"><span data-stu-id="e51e3-163">\<Method></span></span>](../../../docs/framework/net-native/method-element-net-native.md)|<span data-ttu-id="e51e3-164">Applique une stratégie de réflexion runtime à un constructeur ou à une méthode.</span><span class="sxs-lookup"><span data-stu-id="e51e3-164">Applies runtime reflection policy to a constructor or method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e51e3-165">Remarques</span><span class="sxs-lookup"><span data-stu-id="e51e3-165">Remarks</span></span>  
 <span data-ttu-id="e51e3-166">L’élément `<TypeParameter>` est similaire à l’élément [\<Parameter>](../../../docs/framework/net-native/parameter-element-net-native.md), à ceci près qu’il peut uniquement être appliqué à des paramètres de type <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="e51e3-166">The `<TypeParameter>` element is similar to the [\<Parameter>](../../../docs/framework/net-native/parameter-element-net-native.md) element, except that it can be applied only to parameters of type <xref:System.Type>.</span></span> <span data-ttu-id="e51e3-167">Il applique la stratégie à tout type représenté au moment de l'exécution par l'argument de type spécifié par l'attribut `Name`.</span><span class="sxs-lookup"><span data-stu-id="e51e3-167">It applies policy to whatever type is represented at run time by the type argument specified by the `Name` attribute.</span></span>  
  
 <span data-ttu-id="e51e3-168">Par exemple, le sérialiseur JSON NewtonSoft inclut une méthode `JsonConvert.DeserializeObject(String value, Type type)` statique.</span><span class="sxs-lookup"><span data-stu-id="e51e3-168">For example, the NewtonSoft JSON serializer includes a static `JsonConvert.DeserializeObject(String value, Type type)` method.</span></span> <span data-ttu-id="e51e3-169">Les directives de réflexion suivantes :</span><span class="sxs-lookup"><span data-stu-id="e51e3-169">The following reflection directives:</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Type Name="Newtonsoft.Json.JsonConvert" >  
      <Method Name="DeserializeObject">  
         <GenericParameter Name="type" Serialize="Required All" />  
      </Method>  
   </Type>  
</Directives>  
```  
  
 <span data-ttu-id="e51e3-170">spécifient que les métadonnées pour le type de runtime représenté par l’argument `type` doivent être accessibles pour la sérialisation.</span><span class="sxs-lookup"><span data-stu-id="e51e3-170">specify that metadata for the runtime type represented by the `type` argument should be made available for serialization.</span></span> <span data-ttu-id="e51e3-171">Si ces directives runtime s'appliquent à un projet qui inclut le code source suivant :</span><span class="sxs-lookup"><span data-stu-id="e51e3-171">If these runtime directives apply to a project that includes the following source code:</span></span>  
  
```csharp  
Type t = typeof(StockQuote);  
Object obj = JsonConvert.DeserializeObject(data, t);  
```  
  
 <span data-ttu-id="e51e3-172">les directives de réflexion rendent les métadonnées pour le type `StockQuote` disponibles pour le sérialiseur JSON NewtonSoft au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="e51e3-172">the reflection directives make metadata for the `StockQuote` type available for the NewtonSoft JSON serializer at run time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e51e3-173">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e51e3-173">See Also</span></span>  
 [<span data-ttu-id="e51e3-174">\<Method>, élément</span><span class="sxs-lookup"><span data-stu-id="e51e3-174">\<Method> Element</span></span>](../../../docs/framework/net-native/method-element-net-native.md)  
 [<span data-ttu-id="e51e3-175">Guide de référence du fichier de configuration des directives runtime (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="e51e3-175">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [<span data-ttu-id="e51e3-176">Paramètres de stratégie de directive runtime</span><span class="sxs-lookup"><span data-stu-id="e51e3-176">Runtime Directive Policy Settings</span></span>](../../../docs/framework/net-native/runtime-directive-policy-settings.md)  
 [<span data-ttu-id="e51e3-177">Éléments de directive runtime</span><span class="sxs-lookup"><span data-stu-id="e51e3-177">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)
