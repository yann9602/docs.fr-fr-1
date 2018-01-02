---
title: "&lt;add&gt;, élément de &lt;declaredTypes&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data contracts
- dataContractSerializer element
- DataContractSerializer
- DataContractAttribute
ms.assetid: c3d37ae4-8f1c-463f-b195-658c5a7e90a1
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 908982437197964489d27e4d7d77b0fffdbebb6e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltaddgt-of-ltdeclaredtypesgt-element"></a><span data-ttu-id="afa91-102">&lt;add&gt;, élément de &lt;declaredTypes&gt;</span><span class="sxs-lookup"><span data-stu-id="afa91-102">&lt;add&gt; of &lt;declaredTypes&gt; Element</span></span>
<span data-ttu-id="afa91-103">Ajoute un type utilisé par le <xref:System.Runtime.Serialization.DataContractSerializer> pendant la désérialisation.</span><span class="sxs-lookup"><span data-stu-id="afa91-103">Adds a type used by the <xref:System.Runtime.Serialization.DataContractSerializer> during deserialization.</span></span> <span data-ttu-id="afa91-104">Chaque type déclaré inclut les types connus qui seront renvoyés comme champ ou propriété du type déclaré.</span><span class="sxs-lookup"><span data-stu-id="afa91-104">Each declared type includes the known types that will be returned as a field or property of the declared type.</span></span>  
  
 <span data-ttu-id="afa91-105">system.runtime.serialization</span><span class="sxs-lookup"><span data-stu-id="afa91-105">system.runtime.serialization</span></span>  
<span data-ttu-id="afa91-106">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="afa91-106">\<dataContractSerializer></span></span>  
<span data-ttu-id="afa91-107">\<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="afa91-107">\<declaredTypes></span></span>  
<span data-ttu-id="afa91-108">\<Ajouter > de \<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="afa91-108">\<add> of \<declaredTypes></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="afa91-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="afa91-109">Syntax</span></span>  
  
```xml  
<add type="String">  
   <knownType type="String">  
       <parameter index="Integer"  
                  type="String" />  
   </knownType>  
</add>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="afa91-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="afa91-110">Attributes and Elements</span></span>  
 <span data-ttu-id="afa91-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="afa91-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="afa91-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="afa91-112">Attributes</span></span>  
  
|<span data-ttu-id="afa91-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="afa91-113">Attribute</span></span>|<span data-ttu-id="afa91-114">Description</span><span class="sxs-lookup"><span data-stu-id="afa91-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="afa91-115">type</span><span class="sxs-lookup"><span data-stu-id="afa91-115">type</span></span>|<span data-ttu-id="afa91-116">Attribut de chaîne requis.</span><span class="sxs-lookup"><span data-stu-id="afa91-116">Required string attribute.</span></span><br /><br /> <span data-ttu-id="afa91-117">Indique le nom du type (espace de noms compris), celui de l'assembly, le numéro de version, la culture et le jeton de clé publique.</span><span class="sxs-lookup"><span data-stu-id="afa91-117">Specifies the type name (including namespace), assembly name, version number, culture, and public key token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="afa91-118">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="afa91-118">Child Elements</span></span>  
  
|<span data-ttu-id="afa91-119">Élément</span><span class="sxs-lookup"><span data-stu-id="afa91-119">Element</span></span>|<span data-ttu-id="afa91-120">Description</span><span class="sxs-lookup"><span data-stu-id="afa91-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="afa91-121">\<knownType ></span><span class="sxs-lookup"><span data-stu-id="afa91-121">\<knownType></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/knowntype.md)|<span data-ttu-id="afa91-122">Spécifie le type connu correspondant au type déclaré en cours d'ajout.</span><span class="sxs-lookup"><span data-stu-id="afa91-122">Specifies the known type for the declared type that is being added.</span></span> <span data-ttu-id="afa91-123">Si le type déclaré est un type générique, vous devez également ajouter un élément de paramètre à l'élément `<knownType>` pour spécifier le paramètre générique utilisé pour renvoyer le type connu.</span><span class="sxs-lookup"><span data-stu-id="afa91-123">If the declared type is a generic type, then you must also add a parameter element to the `<knownType>` element to specify which generic parameter is used to return the known type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="afa91-124">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="afa91-124">Parent Elements</span></span>  
  
|<span data-ttu-id="afa91-125">Élément</span><span class="sxs-lookup"><span data-stu-id="afa91-125">Element</span></span>|<span data-ttu-id="afa91-126">Description</span><span class="sxs-lookup"><span data-stu-id="afa91-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="afa91-127">\<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="afa91-127">\<declaredTypes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/declaredtypes.md)|<span data-ttu-id="afa91-128">Contient les types qui requièrent des types connus pendant la désérialisation effectuée par le <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="afa91-128">Contains the types that require known types during deserialization by the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="afa91-129">Notes</span><span class="sxs-lookup"><span data-stu-id="afa91-129">Remarks</span></span>  
 <span data-ttu-id="afa91-130">Pour plus d’informations sur les types connus, consultez [Types connus de contrat de données](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) et <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="afa91-130">For more information about known types, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="afa91-131">Consultez le [ \<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) pour obtenir un exemple d’utilisation de cet élément.</span><span class="sxs-lookup"><span data-stu-id="afa91-131">See the [\<dataContractSerializer>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) for an example of using this element.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="afa91-132">Si vous ajoutez le type <xref:System.Object> comme `<declaredType>`, une <xref:System.Configuration.ConfigurationErrorsException> est levée.</span><span class="sxs-lookup"><span data-stu-id="afa91-132">If you add the <xref:System.Object> type as a `<declaredType>`, a <xref:System.Configuration.ConfigurationErrorsException> is thrown.</span></span> <span data-ttu-id="afa91-133">Ceci est dû au fait que le type <xref:System.Object> ne peut pas être utilisé comme type déclaré dans la configuration.</span><span class="sxs-lookup"><span data-stu-id="afa91-133">This is because the <xref:System.Object> type cannot be used as a declared type in configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="afa91-134">Exemple</span><span class="sxs-lookup"><span data-stu-id="afa91-134">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="afa91-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="afa91-135">See Also</span></span>  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 [<span data-ttu-id="afa91-136">Types connus de contrats de données</span><span class="sxs-lookup"><span data-stu-id="afa91-136">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)  
 [<span data-ttu-id="afa91-137">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="afa91-137">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)  
 [<span data-ttu-id="afa91-138">\<Ajouter > de \<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="afa91-138">\<add> of \<declaredTypes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)
