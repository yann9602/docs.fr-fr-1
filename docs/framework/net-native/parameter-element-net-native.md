---
title: "&lt;Parameter&gt;, élément (.NET Native)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 22aaa1f3-596f-4733-93db-f4bcabcb5240
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 820c36abda104bbf748e5b3a7838f3c7715048e2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltparametergt-element-net-native"></a><span data-ttu-id="cbc13-102">&lt;Parameter&gt;, élément (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="cbc13-102">&lt;Parameter&gt; Element (.NET Native)</span></span>
<span data-ttu-id="cbc13-103">Applique la stratégie de réflexion au type de l’argument passé à une méthode.</span><span class="sxs-lookup"><span data-stu-id="cbc13-103">Applies reflection policy to the type of the argument passed to a method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cbc13-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cbc13-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cbc13-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="cbc13-105">Attributes and Elements</span></span>  
 <span data-ttu-id="cbc13-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="cbc13-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cbc13-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="cbc13-107">Attributes</span></span>  
  
|<span data-ttu-id="cbc13-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="cbc13-108">Attribute</span></span>|<span data-ttu-id="cbc13-109">Type d'attribut</span><span class="sxs-lookup"><span data-stu-id="cbc13-109">Attribute type</span></span>|<span data-ttu-id="cbc13-110">Description</span><span class="sxs-lookup"><span data-stu-id="cbc13-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="cbc13-111">Général</span><span class="sxs-lookup"><span data-stu-id="cbc13-111">General</span></span>|<span data-ttu-id="cbc13-112">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="cbc13-112">Required attribute.</span></span> <span data-ttu-id="cbc13-113">Nom du paramètre.</span><span class="sxs-lookup"><span data-stu-id="cbc13-113">The parameter name.</span></span> <span data-ttu-id="cbc13-114">Par exemple, pour la signature de méthode `String.CompareTo(Object value)`, la valeur de l'attribut `Name` est « value ».</span><span class="sxs-lookup"><span data-stu-id="cbc13-114">For example, for the method signature `String.CompareTo(Object value)`, the value of the `Name` attribute is "value".</span></span>|  
|`Activate`|<span data-ttu-id="cbc13-115">Réflexion</span><span class="sxs-lookup"><span data-stu-id="cbc13-115">Reflection</span></span>|<span data-ttu-id="cbc13-116">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="cbc13-116">Optional attribute.</span></span> <span data-ttu-id="cbc13-117">Contrôle l'accès aux constructeurs pour permettre l'activation d'instances au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="cbc13-117">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="cbc13-118">Réflexion</span><span class="sxs-lookup"><span data-stu-id="cbc13-118">Reflection</span></span>|<span data-ttu-id="cbc13-119">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="cbc13-119">Optional attribute.</span></span> <span data-ttu-id="cbc13-120">Contrôle la demande d'informations sur les éléments de programme, mais ne permet pas l'accès au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="cbc13-120">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="cbc13-121">Réflexion</span><span class="sxs-lookup"><span data-stu-id="cbc13-121">Reflection</span></span>|<span data-ttu-id="cbc13-122">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="cbc13-122">Optional attribute.</span></span> <span data-ttu-id="cbc13-123">Contrôle l'accès à l'exécution à tous les membres de types, y compris les constructeurs, les méthodes, les champs, les propriétés et les événements, pour permettre la programmation dynamique.</span><span class="sxs-lookup"><span data-stu-id="cbc13-123">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="cbc13-124">Sérialisation</span><span class="sxs-lookup"><span data-stu-id="cbc13-124">Serialization</span></span>|<span data-ttu-id="cbc13-125">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="cbc13-125">Optional attribute.</span></span> <span data-ttu-id="cbc13-126">Contrôle l'accès au moment de l'exécution aux constructeurs, champs et propriétés, pour permettre la sérialisation et la désérialisation des instances de types par des bibliothèques comme le sérialiseur JSON Newtonsoft.</span><span class="sxs-lookup"><span data-stu-id="cbc13-126">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="cbc13-127">Sérialisation</span><span class="sxs-lookup"><span data-stu-id="cbc13-127">Serialization</span></span>|<span data-ttu-id="cbc13-128">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="cbc13-128">Optional attribute.</span></span> <span data-ttu-id="cbc13-129">Contrôle la stratégie pour la sérialisation qui utilise la classe <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="cbc13-129">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="cbc13-130">Sérialisation</span><span class="sxs-lookup"><span data-stu-id="cbc13-130">Serialization</span></span>|<span data-ttu-id="cbc13-131">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="cbc13-131">Optional attribute.</span></span> <span data-ttu-id="cbc13-132">Contrôle la stratégie pour la sérialisation JSON qui utilise la classe <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="cbc13-132">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="cbc13-133">Sérialisation</span><span class="sxs-lookup"><span data-stu-id="cbc13-133">Serialization</span></span>|<span data-ttu-id="cbc13-134">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="cbc13-134">Optional attribute.</span></span> <span data-ttu-id="cbc13-135">Contrôle la stratégie pour la sérialisation XML qui utilise la classe <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="cbc13-135">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="cbc13-136">Interop</span><span class="sxs-lookup"><span data-stu-id="cbc13-136">Interop</span></span>|<span data-ttu-id="cbc13-137">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="cbc13-137">Optional attribute.</span></span> <span data-ttu-id="cbc13-138">Contrôle la stratégie de marshaling des types référence vers WinRT et COM.</span><span class="sxs-lookup"><span data-stu-id="cbc13-138">Controls policy for marshaling reference types to WinRT and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="cbc13-139">Interop</span><span class="sxs-lookup"><span data-stu-id="cbc13-139">Interop</span></span>|<span data-ttu-id="cbc13-140">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="cbc13-140">Optional attribute.</span></span> <span data-ttu-id="cbc13-141">Contrôle la stratégie pour le marshaling des types de délégués comme pointeurs de fonction vers du code natif.</span><span class="sxs-lookup"><span data-stu-id="cbc13-141">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="cbc13-142">Interop</span><span class="sxs-lookup"><span data-stu-id="cbc13-142">Interop</span></span>|<span data-ttu-id="cbc13-143">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="cbc13-143">Optional attribute.</span></span> <span data-ttu-id="cbc13-144">Contrôle la stratégie pour le marshaling des types de valeurs vers du code natif.</span><span class="sxs-lookup"><span data-stu-id="cbc13-144">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="cbc13-145">Name (attribut)</span><span class="sxs-lookup"><span data-stu-id="cbc13-145">Name attribute</span></span>  
  
|<span data-ttu-id="cbc13-146">Valeur</span><span class="sxs-lookup"><span data-stu-id="cbc13-146">Value</span></span>|<span data-ttu-id="cbc13-147">Description</span><span class="sxs-lookup"><span data-stu-id="cbc13-147">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="cbc13-148">*nom_paramètre*</span><span class="sxs-lookup"><span data-stu-id="cbc13-148">*parameter_name*</span></span>|<span data-ttu-id="cbc13-149">Nom du paramètre de méthode auquel la stratégie est appliquée.</span><span class="sxs-lookup"><span data-stu-id="cbc13-149">The name of the method parameter to which policy is applied.</span></span> <span data-ttu-id="cbc13-150">Par exemple, pour la signature de méthode `String.CompareTo(Object value)`, la valeur de l'attribut `Name` est « value ».</span><span class="sxs-lookup"><span data-stu-id="cbc13-150">For example, for the method signature `String.CompareTo(Object value)`, the value of the `Name` attribute is "value".</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="cbc13-151">Tous les autres attributs</span><span class="sxs-lookup"><span data-stu-id="cbc13-151">All other attributes</span></span>  
  
|<span data-ttu-id="cbc13-152">Valeur</span><span class="sxs-lookup"><span data-stu-id="cbc13-152">Value</span></span>|<span data-ttu-id="cbc13-153">Description</span><span class="sxs-lookup"><span data-stu-id="cbc13-153">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="cbc13-154">*paramètre_stratégie*</span><span class="sxs-lookup"><span data-stu-id="cbc13-154">*policy_setting*</span></span>|<span data-ttu-id="cbc13-155">Paramètre à appliquer à ce type de stratégie.</span><span class="sxs-lookup"><span data-stu-id="cbc13-155">The setting to apply to this policy type.</span></span> <span data-ttu-id="cbc13-156">Les valeurs possibles sont `All`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal` et `Required All`.</span><span class="sxs-lookup"><span data-stu-id="cbc13-156">Possible values are `All`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="cbc13-157">Pour plus d’informations, consultez [Paramètres de stratégie de directive runtime](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="cbc13-157">For more information, see [Runtime Directive Policy Settings](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cbc13-158">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="cbc13-158">Child Elements</span></span>  
 <span data-ttu-id="cbc13-159">Aucun.</span><span class="sxs-lookup"><span data-stu-id="cbc13-159">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cbc13-160">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="cbc13-160">Parent Elements</span></span>  
  
|<span data-ttu-id="cbc13-161">Élément</span><span class="sxs-lookup"><span data-stu-id="cbc13-161">Element</span></span>|<span data-ttu-id="cbc13-162">Description</span><span class="sxs-lookup"><span data-stu-id="cbc13-162">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cbc13-163">\<Method></span><span class="sxs-lookup"><span data-stu-id="cbc13-163">\<Method></span></span>](../../../docs/framework/net-native/method-element-net-native.md)|<span data-ttu-id="cbc13-164">Applique une stratégie de réflexion runtime à un constructeur ou à une méthode.</span><span class="sxs-lookup"><span data-stu-id="cbc13-164">Applies runtime reflection policy to a constructor or method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cbc13-165">Notes</span><span class="sxs-lookup"><span data-stu-id="cbc13-165">Remarks</span></span>  
 <span data-ttu-id="cbc13-166">L’élément `<Parameter>` est un enfant de l’élément [\<Method>](../../../docs/framework/net-native/method-element-net-native.md) et est utilisé pour appliquer la stratégie à un paramètre de méthode particulier.</span><span class="sxs-lookup"><span data-stu-id="cbc13-166">The `<Parameter>` element is a child of the [\<Method>](../../../docs/framework/net-native/method-element-net-native.md) element and is used to apply policy to a particular method parameter.</span></span> <span data-ttu-id="cbc13-167">Le paramètre de méthode spécifique est défini par le nom plutôt que par le type.</span><span class="sxs-lookup"><span data-stu-id="cbc13-167">The specific method parameter is specified by name rather than by type.</span></span> <span data-ttu-id="cbc13-168">Au moins un attribut qui représente un type de stratégie, tel que `Activate` ou `Dynamic`, doit être présent.</span><span class="sxs-lookup"><span data-stu-id="cbc13-168">At least one attribute that represents a policy type, such as `Activate` or `Dynamic`, must be present.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cbc13-169">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cbc13-169">See Also</span></span>  
 [<span data-ttu-id="cbc13-170">\<Method>, élément</span><span class="sxs-lookup"><span data-stu-id="cbc13-170">\<Method> Element</span></span>](../../../docs/framework/net-native/method-element-net-native.md)  
 [<span data-ttu-id="cbc13-171">Guide de référence du fichier de configuration des directives runtime (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="cbc13-171">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [<span data-ttu-id="cbc13-172">Paramètres de stratégie de directive runtime</span><span class="sxs-lookup"><span data-stu-id="cbc13-172">Runtime Directive Policy Settings</span></span>](../../../docs/framework/net-native/runtime-directive-policy-settings.md)  
 [<span data-ttu-id="cbc13-173">Éléments de directive runtime</span><span class="sxs-lookup"><span data-stu-id="cbc13-173">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)
