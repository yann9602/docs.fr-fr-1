---
title: "&lt;MethodInstantiation&gt;, élément (.NET Native)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a3355d78-2a88-4109-8521-830d7cae260a
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c888bf806744c5c62d130ec00b89838c52f67d0a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltmethodinstantiationgt-element-net-native"></a><span data-ttu-id="9df74-102">&lt;MethodInstantiation&gt;, élément (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="9df74-102">&lt;MethodInstantiation&gt; Element (.NET Native)</span></span>
<span data-ttu-id="9df74-103">Applique la stratégie de réflexion runtime à une méthode générique construite.</span><span class="sxs-lookup"><span data-stu-id="9df74-103">Applies runtime reflection policy to a constructed generic method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9df74-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9df74-104">Syntax</span></span>  
  
```xml  
<MethodInstantiation Name="method_name"  
                     Signature="method_signature"  
                     Arguments="method_arguments"  
                     Browse="policy_type"  
                     Dynamic="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9df74-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="9df74-105">Attributes and Elements</span></span>  
 <span data-ttu-id="9df74-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="9df74-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9df74-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="9df74-107">Attributes</span></span>  
  
|<span data-ttu-id="9df74-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="9df74-108">Attribute</span></span>|<span data-ttu-id="9df74-109">Type d'attribut</span><span class="sxs-lookup"><span data-stu-id="9df74-109">Attribute type</span></span>|<span data-ttu-id="9df74-110">Description</span><span class="sxs-lookup"><span data-stu-id="9df74-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="9df74-111">Général</span><span class="sxs-lookup"><span data-stu-id="9df74-111">General</span></span>|<span data-ttu-id="9df74-112">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="9df74-112">Required attribute.</span></span> <span data-ttu-id="9df74-113">Spécifie le nom de la méthode.</span><span class="sxs-lookup"><span data-stu-id="9df74-113">Specifies the method name.</span></span>|  
|`Signature`|<span data-ttu-id="9df74-114">Général</span><span class="sxs-lookup"><span data-stu-id="9df74-114">General</span></span>|<span data-ttu-id="9df74-115">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="9df74-115">Optional attribute.</span></span> <span data-ttu-id="9df74-116">Spécifie les paramètres nommés de la méthode.</span><span class="sxs-lookup"><span data-stu-id="9df74-116">Specifies named parameters of the method.</span></span> <span data-ttu-id="9df74-117">Si plusieurs paramètres nommés sont présents, ils sont séparés par des virgules.</span><span class="sxs-lookup"><span data-stu-id="9df74-117">Multiple named parameters are separated by commas.</span></span> <span data-ttu-id="9df74-118">L'attribut `Signature` est utilisé pour différencier les méthodes surchargées.</span><span class="sxs-lookup"><span data-stu-id="9df74-118">The `Signature` attribute is used to differentiate overloaded methods.</span></span>|  
|`Arguments`|<span data-ttu-id="9df74-119">Général</span><span class="sxs-lookup"><span data-stu-id="9df74-119">General</span></span>|<span data-ttu-id="9df74-120">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="9df74-120">Required attribute.</span></span> <span data-ttu-id="9df74-121">Spécifie les arguments de type générique.</span><span class="sxs-lookup"><span data-stu-id="9df74-121">Specifies the generic type arguments.</span></span> <span data-ttu-id="9df74-122">Si plusieurs arguments sont présents, ils sont séparés par des virgules.</span><span class="sxs-lookup"><span data-stu-id="9df74-122">If multiple arguments are present, they are separated by commas.</span></span>|  
|`Browse`|<span data-ttu-id="9df74-123">Réflexion</span><span class="sxs-lookup"><span data-stu-id="9df74-123">Reflection</span></span>|<span data-ttu-id="9df74-124">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="9df74-124">Optional attribute.</span></span> <span data-ttu-id="9df74-125">Contrôle la demande d'informations sur une méthode ou l'énumération de celle-ci, mais ne permet pas d'effectuer un appel dynamique au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="9df74-125">Controls querying for information about or enumerating a method but does not enable any dynamic invocation at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="9df74-126">Réflexion</span><span class="sxs-lookup"><span data-stu-id="9df74-126">Reflection</span></span>|<span data-ttu-id="9df74-127">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="9df74-127">Optional attribute.</span></span> <span data-ttu-id="9df74-128">Contrôle l'accès à un constructeur ou à une méthode au moment de l'exécution pour activer la programmation dynamique.</span><span class="sxs-lookup"><span data-stu-id="9df74-128">Controls runtime access to a constructor or method to enable dynamic programming.</span></span> <span data-ttu-id="9df74-129">Cette stratégie garantit que le membre peut être appelé dynamiquement au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="9df74-129">This policy ensures that a member can be invoked dynamically at run time.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="9df74-130">Name (attribut)</span><span class="sxs-lookup"><span data-stu-id="9df74-130">Name attribute</span></span>  
  
|<span data-ttu-id="9df74-131">Valeur</span><span class="sxs-lookup"><span data-stu-id="9df74-131">Value</span></span>|<span data-ttu-id="9df74-132">Description</span><span class="sxs-lookup"><span data-stu-id="9df74-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="9df74-133">*nom_méthode*</span><span class="sxs-lookup"><span data-stu-id="9df74-133">*method_name*</span></span>|<span data-ttu-id="9df74-134">Nom de la méthode.</span><span class="sxs-lookup"><span data-stu-id="9df74-134">The method name.</span></span> <span data-ttu-id="9df74-135">Le type de la méthode est défini par le [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) parent ou l’élément [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="9df74-135">The type of the method is defined by the parent [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) or [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) element.</span></span>|  
  
## <a name="signature-attribute"></a><span data-ttu-id="9df74-136">Attribut de signature</span><span class="sxs-lookup"><span data-stu-id="9df74-136">Signature attribute</span></span>  
  
|<span data-ttu-id="9df74-137">Valeur</span><span class="sxs-lookup"><span data-stu-id="9df74-137">Value</span></span>|<span data-ttu-id="9df74-138">Description</span><span class="sxs-lookup"><span data-stu-id="9df74-138">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="9df74-139">*signature_méthode*</span><span class="sxs-lookup"><span data-stu-id="9df74-139">*method_signature*</span></span>|<span data-ttu-id="9df74-140">Spécifie les paramètres nommés de la méthode.</span><span class="sxs-lookup"><span data-stu-id="9df74-140">Specifies the named parameters of the method.</span></span> <span data-ttu-id="9df74-141">Si plusieurs paramètres sont présents, ils sont séparés par des virgules.</span><span class="sxs-lookup"><span data-stu-id="9df74-141">If multiple parameters are present, they are separated by commas.</span></span>|  
  
## <a name="arguments-attribute"></a><span data-ttu-id="9df74-142">Attribut Arguments</span><span class="sxs-lookup"><span data-stu-id="9df74-142">Arguments attribute</span></span>  
  
|<span data-ttu-id="9df74-143">Valeur</span><span class="sxs-lookup"><span data-stu-id="9df74-143">Value</span></span>|<span data-ttu-id="9df74-144">Description</span><span class="sxs-lookup"><span data-stu-id="9df74-144">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="9df74-145">*arguments_méthode*</span><span class="sxs-lookup"><span data-stu-id="9df74-145">*method_arguments*</span></span>|<span data-ttu-id="9df74-146">Spécifie les arguments de type générique.</span><span class="sxs-lookup"><span data-stu-id="9df74-146">Specifies the generic type arguments.</span></span> <span data-ttu-id="9df74-147">Si plusieurs arguments sont présents, ils sont séparés par des virgules.</span><span class="sxs-lookup"><span data-stu-id="9df74-147">If multiple arguments are present, they are separated by commas.</span></span> <span data-ttu-id="9df74-148">Chaque argument doit être composé du nom de type qualifié complet.</span><span class="sxs-lookup"><span data-stu-id="9df74-148">Each argument must consist of the fully qualified type name.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="9df74-149">Tous les autres attributs</span><span class="sxs-lookup"><span data-stu-id="9df74-149">All other attributes</span></span>  
  
|<span data-ttu-id="9df74-150">Valeur</span><span class="sxs-lookup"><span data-stu-id="9df74-150">Value</span></span>|<span data-ttu-id="9df74-151">Description</span><span class="sxs-lookup"><span data-stu-id="9df74-151">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="9df74-152">*paramètre_stratégie*</span><span class="sxs-lookup"><span data-stu-id="9df74-152">*policy_setting*</span></span>|<span data-ttu-id="9df74-153">Paramètre à appliquer à ce type de stratégie pour la méthode.</span><span class="sxs-lookup"><span data-stu-id="9df74-153">The setting to apply to this policy type for the method.</span></span> <span data-ttu-id="9df74-154">Les valeurs possibles sont `Auto`, `Excluded`, `Included` et `Required`.</span><span class="sxs-lookup"><span data-stu-id="9df74-154">Possible values are `Auto`, `Excluded`, `Included`, and `Required`.</span></span> <span data-ttu-id="9df74-155">Pour plus d’informations, consultez [Paramètres de stratégie de directive runtime](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="9df74-155">For more information, see [Runtime Directive Policy Settings](../../../docs/framework/net-native/runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9df74-156">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="9df74-156">Child Elements</span></span>  
 <span data-ttu-id="9df74-157">Aucun.</span><span class="sxs-lookup"><span data-stu-id="9df74-157">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9df74-158">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="9df74-158">Parent Elements</span></span>  
  
|<span data-ttu-id="9df74-159">Élément</span><span class="sxs-lookup"><span data-stu-id="9df74-159">Element</span></span>|<span data-ttu-id="9df74-160">Description</span><span class="sxs-lookup"><span data-stu-id="9df74-160">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9df74-161">\<Type></span><span class="sxs-lookup"><span data-stu-id="9df74-161">\<Type></span></span>](../../../docs/framework/net-native/type-element-net-native.md)|<span data-ttu-id="9df74-162">Applique la stratégie de réflexion à un type et à tous ses membres.</span><span class="sxs-lookup"><span data-stu-id="9df74-162">Applies reflection policy to a type and all its members.</span></span>|  
|[<span data-ttu-id="9df74-163">\<TypeInstantiation></span><span class="sxs-lookup"><span data-stu-id="9df74-163">\<TypeInstantiation></span></span>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|<span data-ttu-id="9df74-164">Applique la stratégie de réflexion à un type générique construit et à tous ses membres.</span><span class="sxs-lookup"><span data-stu-id="9df74-164">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9df74-165">Notes</span><span class="sxs-lookup"><span data-stu-id="9df74-165">Remarks</span></span>  
 <span data-ttu-id="9df74-166">L'élément `<MethodInstantiation>` remplace la stratégie de réflexion runtime de la méthode générique ouverte correspondante.</span><span class="sxs-lookup"><span data-stu-id="9df74-166">The `<MethodInstantiation>` element overrides the runtime reflection policy of its corresponding open generic method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9df74-167">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9df74-167">See Also</span></span>  
 [<span data-ttu-id="9df74-168">Guide de référence du fichier de configuration des directives runtime (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="9df74-168">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [<span data-ttu-id="9df74-169">Éléments de directive runtime</span><span class="sxs-lookup"><span data-stu-id="9df74-169">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)  
 [<span data-ttu-id="9df74-170">Paramètres de stratégie de directive runtime</span><span class="sxs-lookup"><span data-stu-id="9df74-170">Runtime Directive Policy Settings</span></span>](../../../docs/framework/net-native/runtime-directive-policy-settings.md)  
 [<span data-ttu-id="9df74-171">\<Method>, élément</span><span class="sxs-lookup"><span data-stu-id="9df74-171">\<Method> Element</span></span>](../../../docs/framework/net-native/method-element-net-native.md)
