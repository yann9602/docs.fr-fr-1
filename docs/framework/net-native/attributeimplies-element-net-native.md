---
title: "&lt;AttributeImplies&gt;, élément (.NET Native)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 82db7193-a860-418b-84fc-fff2fdf2e025
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ec2bc90283aa39b8258ad14777cda7180c043c69
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltattributeimpliesgt-element-net-native"></a><span data-ttu-id="038f3-102">&lt;AttributeImplies&gt;, élément (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="038f3-102">&lt;AttributeImplies&gt; Element (.NET Native)</span></span>
<span data-ttu-id="038f3-103">Définit la stratégie pour les éléments de code auxquels l'attribut conteneur est appliqué.</span><span class="sxs-lookup"><span data-stu-id="038f3-103">Defines policy for code elements the containing attribute is applied to.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="038f3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="038f3-104">Syntax</span></span>  
  
```xml  
<AttributeImplies Activate="policy_type"  
                  Browse="policy_type"  
                  Dynamic="policy_type"  
                  Serialize="policy_type"   
                  DataContractSerializer="policy_setting"  
                  DataContractJsonSerializer="policy_setting"  
                  XmlSerializer="policy_setting"  
                  MarshalObject="policy_setting"  
                  MarshalDelegate="policy_setting"  
                  MarshalStructure="policy_setting" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="038f3-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="038f3-105">Attributes and Elements</span></span>  
 <span data-ttu-id="038f3-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="038f3-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="038f3-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="038f3-107">Attributes</span></span>  
  
|<span data-ttu-id="038f3-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="038f3-108">Attribute</span></span>|<span data-ttu-id="038f3-109">Type d'attribut</span><span class="sxs-lookup"><span data-stu-id="038f3-109">Attribute type</span></span>|<span data-ttu-id="038f3-110">Description</span><span class="sxs-lookup"><span data-stu-id="038f3-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Activate`|<span data-ttu-id="038f3-111">Réflexion</span><span class="sxs-lookup"><span data-stu-id="038f3-111">Reflection</span></span>|<span data-ttu-id="038f3-112">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="038f3-112">Optional attribute.</span></span> <span data-ttu-id="038f3-113">Contrôle l'accès aux constructeurs pour permettre l'activation d'instances au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="038f3-113">Controls runtime access to constructors to enable activation of instances.</span></span>|  
|`Browse`|<span data-ttu-id="038f3-114">Réflexion</span><span class="sxs-lookup"><span data-stu-id="038f3-114">Reflection</span></span>|<span data-ttu-id="038f3-115">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="038f3-115">Optional attribute.</span></span> <span data-ttu-id="038f3-116">Contrôle la demande d'informations sur les éléments de programme, mais ne permet pas l'accès au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="038f3-116">Controls querying for information about program elements, but does not enable any runtime access.</span></span>|  
|`Dynamic`|<span data-ttu-id="038f3-117">Réflexion</span><span class="sxs-lookup"><span data-stu-id="038f3-117">Reflection</span></span>|<span data-ttu-id="038f3-118">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="038f3-118">Optional attribute.</span></span> <span data-ttu-id="038f3-119">Contrôle l'accès à l'exécution à tous les membres de types, y compris les constructeurs, les méthodes, les champs, les propriétés et les événements, pour permettre la programmation dynamique.</span><span class="sxs-lookup"><span data-stu-id="038f3-119">Controls runtime access to all type members, including constructors, methods, fields, properties, and events, to enable dynamic programming.</span></span>|  
|`Serialize`|<span data-ttu-id="038f3-120">Sérialisation</span><span class="sxs-lookup"><span data-stu-id="038f3-120">Serialization</span></span>|<span data-ttu-id="038f3-121">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="038f3-121">Optional attribute.</span></span> <span data-ttu-id="038f3-122">Contrôle l'accès au moment de l'exécution aux constructeurs, champs et propriétés, pour permettre la sérialisation et la désérialisation des instances de types par des bibliothèques comme le sérialiseur JSON Newtonsoft.</span><span class="sxs-lookup"><span data-stu-id="038f3-122">Controls runtime access to constructors, fields, and properties, to enable type instances to be serialized and deserialized by libraries such as the Newtonsoft JSON serializer.</span></span>|  
|`DataContractSerializer`|<span data-ttu-id="038f3-123">Sérialisation</span><span class="sxs-lookup"><span data-stu-id="038f3-123">Serialization</span></span>|<span data-ttu-id="038f3-124">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="038f3-124">Optional attribute.</span></span> <span data-ttu-id="038f3-125">Contrôle la stratégie pour la sérialisation qui utilise la classe <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="038f3-125">Controls policy for serialization that uses the <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> class.</span></span>|  
|`DataContractJsonSerializer`|<span data-ttu-id="038f3-126">Sérialisation</span><span class="sxs-lookup"><span data-stu-id="038f3-126">Serialization</span></span>|<span data-ttu-id="038f3-127">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="038f3-127">Optional attribute.</span></span> <span data-ttu-id="038f3-128">Contrôle la stratégie pour la sérialisation JSON qui utilise la classe <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="038f3-128">Controls policy for JSON serialization that uses the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> class.</span></span>|  
|`XmlSerializer`|<span data-ttu-id="038f3-129">Sérialisation</span><span class="sxs-lookup"><span data-stu-id="038f3-129">Serialization</span></span>|<span data-ttu-id="038f3-130">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="038f3-130">Optional attribute.</span></span> <span data-ttu-id="038f3-131">Contrôle la stratégie pour la sérialisation XML qui utilise la classe <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="038f3-131">Controls policy for XML serialization that uses the <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> class.</span></span>|  
|`MarshalObject`|<span data-ttu-id="038f3-132">Interop</span><span class="sxs-lookup"><span data-stu-id="038f3-132">Interop</span></span>|<span data-ttu-id="038f3-133">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="038f3-133">Optional attribute.</span></span> <span data-ttu-id="038f3-134">Contrôle la stratégie pour le marshaling des types de références vers Windows Runtime et COM.</span><span class="sxs-lookup"><span data-stu-id="038f3-134">Controls policy for marshaling reference types to Windows Runtime and COM.</span></span>|  
|`MarshalDelegate`|<span data-ttu-id="038f3-135">Interop</span><span class="sxs-lookup"><span data-stu-id="038f3-135">Interop</span></span>|<span data-ttu-id="038f3-136">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="038f3-136">Optional attribute.</span></span> <span data-ttu-id="038f3-137">Contrôle la stratégie pour le marshaling des types de délégués comme pointeurs de fonction vers du code natif.</span><span class="sxs-lookup"><span data-stu-id="038f3-137">Controls policy for marshaling delegate types as function pointers to native code.</span></span>|  
|`MarshalStructure`|<span data-ttu-id="038f3-138">Interop</span><span class="sxs-lookup"><span data-stu-id="038f3-138">Interop</span></span>|<span data-ttu-id="038f3-139">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="038f3-139">Optional attribute.</span></span> <span data-ttu-id="038f3-140">Contrôle la stratégie pour le marshaling des types de valeurs vers du code natif.</span><span class="sxs-lookup"><span data-stu-id="038f3-140">Controls policy for marshaling value types to native code.</span></span>|  
  
## <a name="all-attributes"></a><span data-ttu-id="038f3-141">Tous les attributs</span><span class="sxs-lookup"><span data-stu-id="038f3-141">All attributes</span></span>  
  
|<span data-ttu-id="038f3-142">Valeur</span><span class="sxs-lookup"><span data-stu-id="038f3-142">Value</span></span>|<span data-ttu-id="038f3-143">Description</span><span class="sxs-lookup"><span data-stu-id="038f3-143">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="038f3-144">*paramètre_stratégie*</span><span class="sxs-lookup"><span data-stu-id="038f3-144">*policy_setting*</span></span>|<span data-ttu-id="038f3-145">Paramètre à appliquer à ce type de stratégie.</span><span class="sxs-lookup"><span data-stu-id="038f3-145">The setting to apply to this policy type.</span></span> <span data-ttu-id="038f3-146">Les valeurs possibles sont `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal` et `Required All`.</span><span class="sxs-lookup"><span data-stu-id="038f3-146">Possible values are `All`, `Auto`, `Excluded`, `Public`, `PublicAndInternal`, `Required Public`, `Required PublicAndInternal`, and `Required All`.</span></span> <span data-ttu-id="038f3-147">Pour plus d’informations, consultez [Paramètres de stratégie de directive runtime](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="038f3-147">For more information, see [Runtime Directive Policy Settings](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="038f3-148">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="038f3-148">Child Elements</span></span>  
 <span data-ttu-id="038f3-149">Aucun.</span><span class="sxs-lookup"><span data-stu-id="038f3-149">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="038f3-150">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="038f3-150">Parent Elements</span></span>  
  
|<span data-ttu-id="038f3-151">Élément</span><span class="sxs-lookup"><span data-stu-id="038f3-151">Element</span></span>|<span data-ttu-id="038f3-152">Description</span><span class="sxs-lookup"><span data-stu-id="038f3-152">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="038f3-153">\<Type></span><span class="sxs-lookup"><span data-stu-id="038f3-153">\<Type></span></span>](../../../docs/framework/net-native/type-element-net-native.md)|<span data-ttu-id="038f3-154">Applique la stratégie de réflexion à un type et à tous ses membres.</span><span class="sxs-lookup"><span data-stu-id="038f3-154">Applies reflection policy to a type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="038f3-155">Remarques</span><span class="sxs-lookup"><span data-stu-id="038f3-155">Remarks</span></span>  
 <span data-ttu-id="038f3-156">L'élément `<AttributeImplies>` est utilisé si son type conteneur est un attribut (autrement dit, une classe dérivée de <xref:System.Attribute?displayProperty=nameWithType>).</span><span class="sxs-lookup"><span data-stu-id="038f3-156">The `<AttributeImplies>` element is used if its containing type is an attribute (that is, a class derived from <xref:System.Attribute?displayProperty=nameWithType>).</span></span> <span data-ttu-id="038f3-157">Si l'attribut est appliqué à un élément de programme particulier, la stratégie définie par l'élément `<AttributeImplies>` s'applique à cet élément de programme.</span><span class="sxs-lookup"><span data-stu-id="038f3-157">If the attribute is applied to a particular program element, the policy defined by the `<AttributeImplies>` element applies to that program element.</span></span>  
  
 <span data-ttu-id="038f3-158">Les attributs de réflexion, de sérialisation et d'interopérabilité sont tous facultatifs, même si un au moins doit être présent.</span><span class="sxs-lookup"><span data-stu-id="038f3-158">The reflection, serialization, and interop attributes are all optional, although at least one should be present.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="038f3-159">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="038f3-159">See Also</span></span>  
 [<span data-ttu-id="038f3-160">\<Type > élément</span><span class="sxs-lookup"><span data-stu-id="038f3-160">\<Type> Element</span></span>](../../../docs/framework/net-native/type-element-net-native.md)  
 [<span data-ttu-id="038f3-161">Guide de référence du fichier de configuration des directives runtime (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="038f3-161">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [<span data-ttu-id="038f3-162">Éléments de directive runtime</span><span class="sxs-lookup"><span data-stu-id="038f3-162">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)  
 [<span data-ttu-id="038f3-163">Paramètres de stratégie de directive runtime</span><span class="sxs-lookup"><span data-stu-id="038f3-163">Runtime Directive Policy Settings</span></span>](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
