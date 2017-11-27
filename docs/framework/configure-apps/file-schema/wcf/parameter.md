---
title: "&lt;paramètre&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0fb41e2d-64f7-44ab-993e-05892eac6d82
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e9db1921e2a6ee1ae2780f744c45fdb25efbf797
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltparametergt"></a><span data-ttu-id="8bdd0-102">&lt;paramètre&gt;</span><span class="sxs-lookup"><span data-stu-id="8bdd0-102">&lt;parameter&gt;</span></span>
<span data-ttu-id="8bdd0-103">Indique le paramètre générique lorsqu'un type déclaré est générique.</span><span class="sxs-lookup"><span data-stu-id="8bdd0-103">Specifies the generic parameter when a declared type is a generic type.</span></span>  
  
 <span data-ttu-id="8bdd0-104">\<System.Runtime.Serialization ></span><span class="sxs-lookup"><span data-stu-id="8bdd0-104">\<system.runtime.serialization></span></span>  
<span data-ttu-id="8bdd0-105">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="8bdd0-105">\<dataContractSerializer></span></span>  
<span data-ttu-id="8bdd0-106">\<declaredTypes > élément</span><span class="sxs-lookup"><span data-stu-id="8bdd0-106">\<declaredTypes> Element</span></span>  
<span data-ttu-id="8bdd0-107">\<Ajouter >, élément pour \<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="8bdd0-107">\<add> element for \<declaredTypes></span></span>  
<span data-ttu-id="8bdd0-108">\<knownType > élément</span><span class="sxs-lookup"><span data-stu-id="8bdd0-108">\<knownType> Element</span></span>  
<span data-ttu-id="8bdd0-109">\<paramètre > élément</span><span class="sxs-lookup"><span data-stu-id="8bdd0-109">\<parameter> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8bdd0-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8bdd0-110">Syntax</span></span>  
  
```xml  
<parameter index="integer"  
                      type=String" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8bdd0-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="8bdd0-111">Attributes and Elements</span></span>  
 <span data-ttu-id="8bdd0-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="8bdd0-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8bdd0-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="8bdd0-113">Attributes</span></span>  
  
|<span data-ttu-id="8bdd0-114">Attribut</span><span class="sxs-lookup"><span data-stu-id="8bdd0-114">Attribute</span></span>|<span data-ttu-id="8bdd0-115">Description</span><span class="sxs-lookup"><span data-stu-id="8bdd0-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8bdd0-116">index</span><span class="sxs-lookup"><span data-stu-id="8bdd0-116">index</span></span>|<span data-ttu-id="8bdd0-117">Lorsque le type déclaré est générique, spécifie le paramètre générique qui renverra le type connu.</span><span class="sxs-lookup"><span data-stu-id="8bdd0-117">When the declared type is a generic type, specifies the generic parameter that will return the known type.</span></span>|  
|<span data-ttu-id="8bdd0-118">type</span><span class="sxs-lookup"><span data-stu-id="8bdd0-118">type</span></span>|<span data-ttu-id="8bdd0-119">Chaîne décrivant le type connu utilisé pour la sérialisation et la désérialisation.</span><span class="sxs-lookup"><span data-stu-id="8bdd0-119">A string that describes the known type used for serialization and deserialization.</span></span>|  
  
## <a name="index-attribute"></a><span data-ttu-id="8bdd0-120">Indexer l'Attribut</span><span class="sxs-lookup"><span data-stu-id="8bdd0-120">index Attribute</span></span>  
  
|<span data-ttu-id="8bdd0-121">Valeur</span><span class="sxs-lookup"><span data-stu-id="8bdd0-121">Value</span></span>|<span data-ttu-id="8bdd0-122">Description</span><span class="sxs-lookup"><span data-stu-id="8bdd0-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="8bdd0-123">"0"</span><span class="sxs-lookup"><span data-stu-id="8bdd0-123">"0"</span></span>|<span data-ttu-id="8bdd0-124">Premier paramètre du type générique.</span><span class="sxs-lookup"><span data-stu-id="8bdd0-124">The first parameter in the generic type.</span></span> <span data-ttu-id="8bdd0-125">Par exemple, <xref:System.Collections.Generic.List%601> dispose d'un seul paramètre.</span><span class="sxs-lookup"><span data-stu-id="8bdd0-125">For example, a <xref:System.Collections.Generic.List%601> has only one parameter.</span></span> <span data-ttu-id="8bdd0-126">S'il est utilisé comme type déclaré, l'index a la valeur « 0 ».</span><span class="sxs-lookup"><span data-stu-id="8bdd0-126">If it is used as the declared type, the index would be set to "0".</span></span>|  
|<span data-ttu-id="8bdd0-127">"1"</span><span class="sxs-lookup"><span data-stu-id="8bdd0-127">"1"</span></span>|<span data-ttu-id="8bdd0-128">Second paramètre d'un type générique.</span><span class="sxs-lookup"><span data-stu-id="8bdd0-128">The second parameter in a generic type.</span></span> <span data-ttu-id="8bdd0-129">Par exemple, <xref:System.Collections.Generic.Dictionary%602> dispose de deux paramètres.</span><span class="sxs-lookup"><span data-stu-id="8bdd0-129">For example, a <xref:System.Collections.Generic.Dictionary%602> has two parameters.</span></span> <span data-ttu-id="8bdd0-130">Si le type connu est renvoyé par le second paramètre, affectez à l'attribut d'index la valeur « 1 ».</span><span class="sxs-lookup"><span data-stu-id="8bdd0-130">If the known type is returned by the second parameter, set the index attribute to "1".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8bdd0-131">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="8bdd0-131">Child Elements</span></span>  
 <span data-ttu-id="8bdd0-132">Aucun.</span><span class="sxs-lookup"><span data-stu-id="8bdd0-132">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8bdd0-133">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="8bdd0-133">Parent Elements</span></span>  
  
|<span data-ttu-id="8bdd0-134">Élément</span><span class="sxs-lookup"><span data-stu-id="8bdd0-134">Element</span></span>|<span data-ttu-id="8bdd0-135">Description</span><span class="sxs-lookup"><span data-stu-id="8bdd0-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8bdd0-136">\<knownType ></span><span class="sxs-lookup"><span data-stu-id="8bdd0-136">\<knownType></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/knowntype.md)|<span data-ttu-id="8bdd0-137">Spécifie un type connu pouvant être renvoyé par un champ ou une propriété du type déclaré.</span><span class="sxs-lookup"><span data-stu-id="8bdd0-137">Specifies a known type that can be returned by a field or property of the declared type.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8bdd0-138">Remarques</span><span class="sxs-lookup"><span data-stu-id="8bdd0-138">Remarks</span></span>  
 [!INCLUDE[crabout](../../../../../includes/crabout-md.md)]<span data-ttu-id="8bdd0-139">types connus, consultez [Types connus de contrat de données](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) et <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="8bdd0-139"> known types, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="8bdd0-140">Consultez le [ \<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) pour obtenir un exemple d’utilisation de cet élément.</span><span class="sxs-lookup"><span data-stu-id="8bdd0-140">See the [\<dataContractSerializer>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) for an example of using this element.</span></span>  
  
 <span data-ttu-id="8bdd0-141">Cet élément de configuration ne peut pas contenir les deux attributs simultanément.</span><span class="sxs-lookup"><span data-stu-id="8bdd0-141">This configuration element cannot have both attributes at the same time.</span></span> <span data-ttu-id="8bdd0-142">Si c'est le cas, un <xref:System.Configuration.ConfigurationErrorsException> survient.</span><span class="sxs-lookup"><span data-stu-id="8bdd0-142">If both attributes are set, a <xref:System.Configuration.ConfigurationErrorsException> occurs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8bdd0-143">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8bdd0-143">See Also</span></span>  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 [<span data-ttu-id="8bdd0-144">Types connus de contrat de données</span><span class="sxs-lookup"><span data-stu-id="8bdd0-144">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)  
 [<span data-ttu-id="8bdd0-145">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="8bdd0-145">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)  
 [<span data-ttu-id="8bdd0-146">\<add></span><span class="sxs-lookup"><span data-stu-id="8bdd0-146">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)
