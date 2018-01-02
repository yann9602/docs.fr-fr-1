---
title: "&lt;oidEntry&gt; élément"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/oidMap/oidEntry
- http://schemas.microsoft.com/.NetConfiguration/v2.0#oidEntry
helpviewer_keywords:
- <oidEntry> element
- oidEntry element
ms.assetid: 22fb88b0-bf27-489c-9ca0-e65950ac136c
caps.latest.revision: "11"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 2d6dfe38f8e632a31f7a20191678f1fff7fd88ee
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltoidentrygt-element"></a><span data-ttu-id="35f61-102">&lt;oidEntry&gt; élément</span><span class="sxs-lookup"><span data-stu-id="35f61-102">&lt;oidEntry&gt; Element</span></span>
<span data-ttu-id="35f61-103">Mappe un identificateur d’objet (OID) ASN.1 à un nom convivial.</span><span class="sxs-lookup"><span data-stu-id="35f61-103">Maps an ASN.1 object identifier (OID) to a friendly name.</span></span>  
  
 <span data-ttu-id="35f61-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="35f61-104">\<configuration></span></span>  
<span data-ttu-id="35f61-105">\<mscorlib ></span><span class="sxs-lookup"><span data-stu-id="35f61-105">\<mscorlib></span></span>  
<span data-ttu-id="35f61-106">\<cryptographySettings ></span><span class="sxs-lookup"><span data-stu-id="35f61-106">\<cryptographySettings></span></span>  
<span data-ttu-id="35f61-107">\<oidMap ></span><span class="sxs-lookup"><span data-stu-id="35f61-107">\<oidMap></span></span>  
<span data-ttu-id="35f61-108">\<oidEntry ></span><span class="sxs-lookup"><span data-stu-id="35f61-108">\<oidEntry></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35f61-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="35f61-109">Syntax</span></span>  
  
```xml  
<oidEntry OID="object identifier number" name="friendly name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="35f61-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="35f61-110">Attributes and Elements</span></span>  
 <span data-ttu-id="35f61-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="35f61-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="35f61-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="35f61-112">Attributes</span></span>  
  
|<span data-ttu-id="35f61-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="35f61-113">Attribute</span></span>|<span data-ttu-id="35f61-114">Description</span><span class="sxs-lookup"><span data-stu-id="35f61-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="35f61-115">**OID**</span><span class="sxs-lookup"><span data-stu-id="35f61-115">**OID**</span></span>|<span data-ttu-id="35f61-116">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="35f61-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="35f61-117">Spécifie l’OID ASN.1 correspondant à l’algorithme implémenté par votre classe.</span><span class="sxs-lookup"><span data-stu-id="35f61-117">Specifies the ASN.1 OID corresponding to the algorithm implemented by your class.</span></span>|  
|<span data-ttu-id="35f61-118">**name**</span><span class="sxs-lookup"><span data-stu-id="35f61-118">**name**</span></span>|<span data-ttu-id="35f61-119">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="35f61-119">Required attribute.</span></span><br /><br /> <span data-ttu-id="35f61-120">Spécifie la valeur de la **nom** d’attribut dans le [ \<nameEntry >](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md) balise.</span><span class="sxs-lookup"><span data-stu-id="35f61-120">Specifies the value for the **name** attribute in the [\<nameEntry>](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md) tag.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="35f61-121">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="35f61-121">Child Elements</span></span>  
 <span data-ttu-id="35f61-122">Aucun.</span><span class="sxs-lookup"><span data-stu-id="35f61-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="35f61-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="35f61-123">Parent Elements</span></span>  
  
|<span data-ttu-id="35f61-124">Élément</span><span class="sxs-lookup"><span data-stu-id="35f61-124">Element</span></span>|<span data-ttu-id="35f61-125">Description</span><span class="sxs-lookup"><span data-stu-id="35f61-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="35f61-126">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="35f61-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="35f61-127">Contient des paramètres de chiffrement.</span><span class="sxs-lookup"><span data-stu-id="35f61-127">Contains cryptography settings.</span></span>|  
|`mscorlib`|<span data-ttu-id="35f61-128">Contient le `cryptographySettings` élément.</span><span class="sxs-lookup"><span data-stu-id="35f61-128">Contains the `cryptographySettings` element.</span></span>|  
|`oidMap`|<span data-ttu-id="35f61-129">Contient les mappages de d’identificateur d’objet ASN.1 aux classes.</span><span class="sxs-lookup"><span data-stu-id="35f61-129">Contains ASN.1 object identifier (OID) mappings to classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="35f61-130">Notes</span><span class="sxs-lookup"><span data-stu-id="35f61-130">Remarks</span></span>  
 <span data-ttu-id="35f61-131">OID ASN.1 identifient les algorithmes dans certains formats de chiffrement.</span><span class="sxs-lookup"><span data-stu-id="35f61-131">ASN.1 object identifiers identify algorithms in some cryptographic formats.</span></span> <span data-ttu-id="35f61-132">Mapper des identificateurs d’objet aux noms conviviaux des algorithmes que vous souhaitez identifier.</span><span class="sxs-lookup"><span data-stu-id="35f61-132">Map object identifiers to friendly names for the algorithms you want to identify.</span></span>  
  
## <a name="example"></a><span data-ttu-id="35f61-133">Exemple</span><span class="sxs-lookup"><span data-stu-id="35f61-133">Example</span></span>  
 <span data-ttu-id="35f61-134">L’exemple suivant montre comment utiliser le  **\<oidEntry >** élément pour mapper un identificateur d’objet pour l’algorithme de hachage RIPEMD-160 à une implémentation de cet algorithme de hachage.</span><span class="sxs-lookup"><span data-stu-id="35f61-134">The following example shows how to use the **\<oidEntry>** element to map an object identifier for the RIPEMD-160 hash algorithm to an implementation of that hash algorithm.</span></span>  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass   MyCrypto="MyCryptoClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
            </cryptoClasses>  
            <nameEntry name="RIPEMD-160" class="MyCrypto"/>  
         </cryptoNameMapping>  
         <oidMap>  
            <oidEntry OID="1.3.36.3.2.1"   name="MyCryptoClass"/>  
         </oidMap>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="35f61-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="35f61-135">See Also</span></span>  
 [<span data-ttu-id="35f61-136">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="35f61-136">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="35f61-137">Schéma des paramètres de chiffrement</span><span class="sxs-lookup"><span data-stu-id="35f61-137">Cryptography Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/index.md)  
 [<span data-ttu-id="35f61-138">Services de chiffrement</span><span class="sxs-lookup"><span data-stu-id="35f61-138">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)  
 [<span data-ttu-id="35f61-139">Configuration des classes de chiffrement</span><span class="sxs-lookup"><span data-stu-id="35f61-139">Configuring Cryptography Classes</span></span>](../../../../../docs/framework/configure-apps/configure-cryptography-classes.md)  
 [<span data-ttu-id="35f61-140">Mappage d'identificateurs d'objet à des algorithmes de chiffrement</span><span class="sxs-lookup"><span data-stu-id="35f61-140">Mapping Object Identifiers to Cryptography Algorithms</span></span>](../../../../../docs/framework/configure-apps/map-object-identifiers-to-cryptography-algorithms.md)
