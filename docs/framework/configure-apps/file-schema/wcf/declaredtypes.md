---
title: '&lt;declaredTypes&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- dataContractSerializer element
- declaredTypes element
- DataContractSerializer
- KnownTypes
- <declaredTypes> element
ms.assetid: f35184e4-9d9e-4d37-8fb4-d5b58220eb3e
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 80a2959395cf8f10ae8c5bc2ccd47ea97ffdaa30
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="ltdeclaredtypesgt"></a><span data-ttu-id="94d26-102">&lt;declaredTypes&gt;</span><span class="sxs-lookup"><span data-stu-id="94d26-102">&lt;declaredTypes&gt;</span></span>
<span data-ttu-id="94d26-103">Contient les types connus utilisés par le <xref:System.Runtime.Serialization.DataContractSerializer> lors de la désérialisation.</span><span class="sxs-lookup"><span data-stu-id="94d26-103">Contains the known types that the <xref:System.Runtime.Serialization.DataContractSerializer> uses when deserializing.</span></span>  
  
 <span data-ttu-id="94d26-104">Pour plus d’informations sur les contrats de données et les types connus, consultez [Types connus de contrat de données](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="94d26-104">For more information about data contracts and known types, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span>  
  
 <span data-ttu-id="94d26-105">system.runtime.serialization</span><span class="sxs-lookup"><span data-stu-id="94d26-105">system.runtime.serialization</span></span>  
<span data-ttu-id="94d26-106">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="94d26-106">\<dataContractSerializer></span></span>  
<span data-ttu-id="94d26-107">\<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="94d26-107">\<declaredTypes></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94d26-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="94d26-108">Syntax</span></span>  
  
```xml  
<configuration>  
  <system.runtime.serialization>  
    <dataContractSerializer>  
      <declaredTypes>  
        <add type="String ">  
          <knownType type="String">  
                <parameter index="Integer"/>  
          </knownType>  
        </add>  
      </declaredTypes>  
    <dataContractSerializer>  
  </system.runtime.serialization>  
</configuration>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="94d26-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="94d26-109">Attributes and Elements</span></span>  
 <span data-ttu-id="94d26-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="94d26-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="94d26-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="94d26-111">Attributes</span></span>  
 <span data-ttu-id="94d26-112">Aucun</span><span class="sxs-lookup"><span data-stu-id="94d26-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="94d26-113">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="94d26-113">Child Elements</span></span>  
  
|<span data-ttu-id="94d26-114">Élément</span><span class="sxs-lookup"><span data-stu-id="94d26-114">Element</span></span>|<span data-ttu-id="94d26-115">Description</span><span class="sxs-lookup"><span data-stu-id="94d26-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="94d26-116">\<add></span><span class="sxs-lookup"><span data-stu-id="94d26-116">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)|<span data-ttu-id="94d26-117">Ajoute des types qui requièrent des types connus.</span><span class="sxs-lookup"><span data-stu-id="94d26-117">Adds types that require known types.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="94d26-118">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="94d26-118">Parent Elements</span></span>  
  
|<span data-ttu-id="94d26-119">Élément</span><span class="sxs-lookup"><span data-stu-id="94d26-119">Element</span></span>|<span data-ttu-id="94d26-120">Description</span><span class="sxs-lookup"><span data-stu-id="94d26-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="94d26-121">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="94d26-121">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-of-system-runtime-serialization.md)|<span data-ttu-id="94d26-122">Contient les données de configuration correspondant au <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="94d26-122">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="94d26-123">Remarques</span><span class="sxs-lookup"><span data-stu-id="94d26-123">Remarks</span></span>  
 [!INCLUDE[crabout](../../../../../includes/crabout-md.md)]<span data-ttu-id="94d26-124">types connus, consultez [Types connus de contrat de données](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) et <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="94d26-124"> known types, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="94d26-125">Exemple</span><span class="sxs-lookup"><span data-stu-id="94d26-125">Example</span></span>  
 <span data-ttu-id="94d26-126">Le code XML suivant montre les types déclarés et connus types ajoutés à un `DataContractSerializer` élément.</span><span class="sxs-lookup"><span data-stu-id="94d26-126">The following XML code shows declared types and known types added to a `DataContractSerializer` element.</span></span> <span data-ttu-id="94d26-127">L'exemple montre l'ajout de trois types.</span><span class="sxs-lookup"><span data-stu-id="94d26-127">The example shows three types being added.</span></span> <span data-ttu-id="94d26-128">Le premier est un type personnalisé nommé « Orders » qui utilise un type connu nommé « Item ».</span><span class="sxs-lookup"><span data-stu-id="94d26-128">The first is a custom type named "Orders" that uses a known type named "Item".</span></span> <span data-ttu-id="94d26-129">Le deuxième est un <xref:System.Collections.Generic.List%601> qui utilise `Item` comme un type connu.</span><span class="sxs-lookup"><span data-stu-id="94d26-129">The second declared type is a <xref:System.Collections.Generic.List%601> that uses `Item` as a known type.</span></span> <span data-ttu-id="94d26-130">Le troisième et dernier est un <xref:System.Collections.Generic.Dictionary%602>.</span><span class="sxs-lookup"><span data-stu-id="94d26-130">Finally the third declared type is a <xref:System.Collections.Generic.Dictionary%602>.</span></span> <span data-ttu-id="94d26-131">Le type de classe <xref:System.Collections.Generic.Dictionary%602> est un type générique contenant deux paramètres de type.</span><span class="sxs-lookup"><span data-stu-id="94d26-131">The <xref:System.Collections.Generic.Dictionary%602> class type is a generic type, with two type parameters.</span></span> <span data-ttu-id="94d26-132">Le premier représente la clé et le second représente la valeur.</span><span class="sxs-lookup"><span data-stu-id="94d26-132">The first represents the key and the second represents the value.</span></span> <span data-ttu-id="94d26-133">L'exemple suivant ajoute un <xref:System.Collections.Generic.List%601> du deuxième type (la valeur) à la liste de types connus.</span><span class="sxs-lookup"><span data-stu-id="94d26-133">The following example adds a <xref:System.Collections.Generic.List%601> of the second type (the value) to the list of known types.</span></span> <span data-ttu-id="94d26-134">Vous devez utiliser l'attribut `index` pour spécifier le paramètre de type à utiliser dans le type connu.</span><span class="sxs-lookup"><span data-stu-id="94d26-134">You must use the `index` attribute to specify which type parameter to use in the known type.</span></span> <span data-ttu-id="94d26-135">Dans ce cas, le type de valeur est indiqué par l’ensemble d’attributs d’index ayant la valeur "1" (la collection est de base zéro).</span><span class="sxs-lookup"><span data-stu-id="94d26-135">In this case, the value type is indicated by the index attribute set to "1" (the collection is zero-based).</span></span>  
  
```xml  
<configuration>  
  <system.runtime.serialization>  
    <dataContractSerializer>  
      <declaredTypes>  
        <add type="Examples.Types.Orders, SerializationTypes, Version = 2.0.0.0, Culture = neutral, PublicKeyToken=null">  
          <knownType type="Examples.Types.Item, SerializationTypes, Version=2.0.0.0, Culture=neutral, PublicKey=null" />  
        </add>  
        <add type="System.Collections.Generic.List`1, SerializationTypes, Version = 2.0.0.0, Culture = neutral, PublicKeyToken=null">  
          <knownType type="Examples.Types.Item, SerializationTypes, Version=2.0.0.0, Culture=neutral, PublicKey=null" />  
        </add>  
        <add type="System.Collections.Generic.Dictionary`2, SerializationTypes, Version = 2.0.0.0, Culture = neutral, PublicKeyToken=null">  
          <knownType type="System.Collections.Generic.List`1, SerializationTypes, Version = 2.0.0.0, Culture = neutral, PublicKeyToken=null">  
            <parameter index="1"/>  
          </knownType>  
        </add>  
      </declaredTypes>  
    <dataContractSerializer>  
  </system.runtime.serialization>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="94d26-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="94d26-136">See Also</span></span>  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 [<span data-ttu-id="94d26-137">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="94d26-137">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)  
 [<span data-ttu-id="94d26-138">Types connus de contrat de données</span><span class="sxs-lookup"><span data-stu-id="94d26-138">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)  
 [<span data-ttu-id="94d26-139">\<add></span><span class="sxs-lookup"><span data-stu-id="94d26-139">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)
