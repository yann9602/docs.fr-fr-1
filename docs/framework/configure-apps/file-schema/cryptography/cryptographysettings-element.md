---
title: "&lt;cryptographySettings&gt; élément"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings
- http://schemas.microsoft.com/.NetConfiguration/v2.0#cryptographySettings
helpviewer_keywords:
- cryptographySettings element
- <cryptographySettings> element
ms.assetid: 6201b7da-bcb7-49f7-b9f5-ba1fe05573b9
caps.latest.revision: "11"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 73a4f362be1612658e6911b7e7ea7a6c3e670e01
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltcryptographysettingsgt-element"></a><span data-ttu-id="b6e79-102">&lt;cryptographySettings&gt; élément</span><span class="sxs-lookup"><span data-stu-id="b6e79-102">&lt;cryptographySettings&gt; Element</span></span>
<span data-ttu-id="b6e79-103">Contient des paramètres de chiffrement.</span><span class="sxs-lookup"><span data-stu-id="b6e79-103">Contains cryptography settings.</span></span>  
  
 <span data-ttu-id="b6e79-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="b6e79-104">\<configuration></span></span>  
<span data-ttu-id="b6e79-105">\<mscorlib ></span><span class="sxs-lookup"><span data-stu-id="b6e79-105">\<mscorlib></span></span>  
<span data-ttu-id="b6e79-106">\<cryptographySettings ></span><span class="sxs-lookup"><span data-stu-id="b6e79-106">\<cryptographySettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6e79-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b6e79-107">Syntax</span></span>  
  
```xml  
      <cryptographySettings>   
</cryptographySettings>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b6e79-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="b6e79-108">Attributes and Elements</span></span>  
 <span data-ttu-id="b6e79-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="b6e79-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b6e79-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="b6e79-110">Attributes</span></span>  
 <span data-ttu-id="b6e79-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="b6e79-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b6e79-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="b6e79-112">Child Elements</span></span>  
  
|<span data-ttu-id="b6e79-113">Élément</span><span class="sxs-lookup"><span data-stu-id="b6e79-113">Element</span></span>|<span data-ttu-id="b6e79-114">Description</span><span class="sxs-lookup"><span data-stu-id="b6e79-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b6e79-115">\<cryptoNameMapping ></span><span class="sxs-lookup"><span data-stu-id="b6e79-115">\<cryptoNameMapping></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptonamemapping-element.md)|<span data-ttu-id="b6e79-116">Contient des mappages de classes à des noms conviviaux.</span><span class="sxs-lookup"><span data-stu-id="b6e79-116">Contains mappings of classes to friendly names.</span></span>|  
|[<span data-ttu-id="b6e79-117">\<oidMap ></span><span class="sxs-lookup"><span data-stu-id="b6e79-117">\<oidMap></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidmap-element.md)|<span data-ttu-id="b6e79-118">Contient les mappages de d’identificateur d’objet ASN.1 aux classes.</span><span class="sxs-lookup"><span data-stu-id="b6e79-118">Contains ASN.1 object identifier (OID) mappings to classes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b6e79-119">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="b6e79-119">Parent Elements</span></span>  
  
|<span data-ttu-id="b6e79-120">Élément</span><span class="sxs-lookup"><span data-stu-id="b6e79-120">Element</span></span>|<span data-ttu-id="b6e79-121">Description</span><span class="sxs-lookup"><span data-stu-id="b6e79-121">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="b6e79-122">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b6e79-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`mscorlib`|<span data-ttu-id="b6e79-123">Contient le `cryptographySettings` élément.</span><span class="sxs-lookup"><span data-stu-id="b6e79-123">Contains the `cryptographySettings` element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="b6e79-124">Exemple</span><span class="sxs-lookup"><span data-stu-id="b6e79-124">Example</span></span>  
 <span data-ttu-id="b6e79-125">L’exemple suivant montre comment utiliser le  **\<cryptographySettings >** élément doit contenir les mappages de noms de chiffrement et les mappages de l’OID.</span><span class="sxs-lookup"><span data-stu-id="b6e79-125">The following example shows how use the **\<cryptographySettings>** element to contain cryptography name mappings and OID mappings.</span></span> <span data-ttu-id="b6e79-126">Cet exemple configure l’exécution afin que <xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType> retourne un `MyHashClass` objet et la `MyCryptoClass` classe correspond à l’OID 1.3.36.2.1.</span><span class="sxs-lookup"><span data-stu-id="b6e79-126">This example configures the runtime so that <xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType> returns a `MyHashClass` object and the `MyCryptoClass` class maps to the object identifier 1.3.36.2.1.</span></span>  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass   MyHash="MyHashClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
               <cryptoClass   MyCrypto="MyCryptoClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
            </cryptoClasses>  
            <nameEntry name="System.Security.Cryptography.HashAlgorithm"  
                       class="MyHash"/>  
         </cryptoNameMapping>  
         <oidMap>  
            <oidEntry OID="1.3.36.3.2.1"   name="MyCryptoClass"/>  
         </oidMap>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b6e79-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b6e79-127">See Also</span></span>  
 [<span data-ttu-id="b6e79-128">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="b6e79-128">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="b6e79-129">Schéma des paramètres de chiffrement</span><span class="sxs-lookup"><span data-stu-id="b6e79-129">Cryptography Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/index.md)  
 [<span data-ttu-id="b6e79-130">Services de chiffrement</span><span class="sxs-lookup"><span data-stu-id="b6e79-130">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)
