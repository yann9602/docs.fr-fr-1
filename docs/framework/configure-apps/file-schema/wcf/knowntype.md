---
title: '&lt;knownType&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ee2b7be3-7148-4a3a-b861-48e7330615e5
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bedebb98e5fc48292c503eef30cee30c8d29c41c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="ltknowntypegt"></a><span data-ttu-id="65793-102">&lt;knownType&gt;</span><span class="sxs-lookup"><span data-stu-id="65793-102">&lt;knownType&gt;</span></span>
<span data-ttu-id="65793-103">Indique un type devant être utilisé par le <xref:System.Runtime.Serialization.DataContractSerializer> pendant la désérialisation.</span><span class="sxs-lookup"><span data-stu-id="65793-103">Specifies a type to be used by <xref:System.Runtime.Serialization.DataContractSerializer> during deserialization.</span></span> <span data-ttu-id="65793-104">L'élément indique un « type connu » renvoyé par un champ ou une propriété d'un « type déclaré ».</span><span class="sxs-lookup"><span data-stu-id="65793-104">The element specifies a "known type" that is returned by a field or property of a "declared type."</span></span> <span data-ttu-id="65793-105">Pour plus d’informations, consultez [Types connus de contrat de données](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="65793-105">For more information, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span>  
  
 <span data-ttu-id="65793-106">\<System.Runtime.Serialization ></span><span class="sxs-lookup"><span data-stu-id="65793-106">\<system.runtime.serialization></span></span>  
<span data-ttu-id="65793-107">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="65793-107">\<dataContractSerializer></span></span>  
<span data-ttu-id="65793-108">\<declaredTypes > élément</span><span class="sxs-lookup"><span data-stu-id="65793-108">\<declaredTypes> Element</span></span>  
<span data-ttu-id="65793-109">\<Ajouter > de \<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="65793-109">\<add> of \<declaredTypes></span></span>  
<span data-ttu-id="65793-110">\<knownType > élément</span><span class="sxs-lookup"><span data-stu-id="65793-110">\<knownType> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65793-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="65793-111">Syntax</span></span>  
  
```xml  
<knownType type="String">  
     <parameter index="Integer"  
                type="String" />  
</knownType>  
```  
  
## <a name="type"></a><span data-ttu-id="65793-112">Type</span><span class="sxs-lookup"><span data-stu-id="65793-112">Type</span></span>  
 `string`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="65793-113">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="65793-113">Attributes and Elements</span></span>  
 <span data-ttu-id="65793-114">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="65793-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="65793-115">Attributs</span><span class="sxs-lookup"><span data-stu-id="65793-115">Attributes</span></span>  
  
|<span data-ttu-id="65793-116">Attribut</span><span class="sxs-lookup"><span data-stu-id="65793-116">Attribute</span></span>|<span data-ttu-id="65793-117">Description</span><span class="sxs-lookup"><span data-stu-id="65793-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="65793-118">type</span><span class="sxs-lookup"><span data-stu-id="65793-118">type</span></span>|<span data-ttu-id="65793-119">Indique le type (espace de noms compris), le nom de l'assembly, la version, la culture et le jeton de clé publique.</span><span class="sxs-lookup"><span data-stu-id="65793-119">Specifies the type (including namespace), assembly name, version, culture, and public key token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="65793-120">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="65793-120">Child Elements</span></span>  
  
|<span data-ttu-id="65793-121">Élément</span><span class="sxs-lookup"><span data-stu-id="65793-121">Element</span></span>|<span data-ttu-id="65793-122">Description</span><span class="sxs-lookup"><span data-stu-id="65793-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="65793-123">\<paramètre ></span><span class="sxs-lookup"><span data-stu-id="65793-123">\<parameter></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/parameter.md)|<span data-ttu-id="65793-124">Indique un index de paramètre lorsque le type déclaré est générique.</span><span class="sxs-lookup"><span data-stu-id="65793-124">Specifies a parameter index when the declared type is a generic type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="65793-125">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="65793-125">Parent Elements</span></span>  
  
|<span data-ttu-id="65793-126">Élément</span><span class="sxs-lookup"><span data-stu-id="65793-126">Element</span></span>|<span data-ttu-id="65793-127">Description</span><span class="sxs-lookup"><span data-stu-id="65793-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="65793-128">\<add></span><span class="sxs-lookup"><span data-stu-id="65793-128">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)|<span data-ttu-id="65793-129">Ajoute un type déclaré à la collection de types déclarés.</span><span class="sxs-lookup"><span data-stu-id="65793-129">Adds a declared type to the collection of declared types.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="65793-130">Remarques</span><span class="sxs-lookup"><span data-stu-id="65793-130">Remarks</span></span>  
 <span data-ttu-id="65793-131">Pour plus d’informations sur les types connus, consultez [Types connus de contrat de données](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) et <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="65793-131">For more information about known types, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="65793-132">Consultez le [ \<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) pour obtenir un exemple d’utilisation de cet élément.</span><span class="sxs-lookup"><span data-stu-id="65793-132">See the [\<dataContractSerializer>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) for an example of using this element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="65793-133">Exemple</span><span class="sxs-lookup"><span data-stu-id="65793-133">Example</span></span>  
  
```xml  
<add type="MyCompany.Library.Shape,   
           MyAssembly, Version=2.0.0.0, Culture=neutral,  
           PublicKeyToken=XXXXXX, processorArchitecture=MSIL">  
           <knownType type="MyCompany.Library.Circle,   
                      MyAssembly, Version=2.0.0.0, Culture=neutral,  
                      PublicKeyToken=XXXXXX,  
                      processorArchitecture=MSIL"/>  
</add>  
```  
  
## <a name="see-also"></a><span data-ttu-id="65793-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="65793-134">See Also</span></span>  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 [<span data-ttu-id="65793-135">Types connus de contrat de données</span><span class="sxs-lookup"><span data-stu-id="65793-135">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)  
 [<span data-ttu-id="65793-136">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="65793-136">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)  
 [<span data-ttu-id="65793-137">\<add></span><span class="sxs-lookup"><span data-stu-id="65793-137">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)
