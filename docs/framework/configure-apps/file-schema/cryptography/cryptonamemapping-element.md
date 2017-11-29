---
title: "&lt;cryptoNameMapping&gt; élément"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#cryptoNameMapping
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/cryptoNameMapping
helpviewer_keywords:
- <cryptoNameMapping> element
- cryptoNameMapping element
ms.assetid: c59c9494-149b-4ce6-b38d-371f896ae85c
caps.latest.revision: "12"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 2156c6441190b530c48a70e67e93e4806d20b199
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltcryptonamemappinggt-element"></a><span data-ttu-id="de585-102">&lt;cryptoNameMapping&gt; élément</span><span class="sxs-lookup"><span data-stu-id="de585-102">&lt;cryptoNameMapping&gt; Element</span></span>
<span data-ttu-id="de585-103">Contient des mappages de classes à des noms conviviaux.</span><span class="sxs-lookup"><span data-stu-id="de585-103">Contains mappings of classes to friendly names.</span></span>  
  
 <span data-ttu-id="de585-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="de585-104">\<configuration></span></span>  
<span data-ttu-id="de585-105">\<mscorlib ></span><span class="sxs-lookup"><span data-stu-id="de585-105">\<mscorlib></span></span>  
<span data-ttu-id="de585-106">\<cryptographySettings ></span><span class="sxs-lookup"><span data-stu-id="de585-106">\<cryptographySettings></span></span>  
<span data-ttu-id="de585-107">\<cryptoNameMapping ></span><span class="sxs-lookup"><span data-stu-id="de585-107">\<cryptoNameMapping></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de585-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="de585-108">Syntax</span></span>  
  
```xml  
      <cryptoNameMapping>   
</cryptoNameMapping>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="de585-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="de585-109">Attributes and Elements</span></span>  
 <span data-ttu-id="de585-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="de585-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="de585-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="de585-111">Attributes</span></span>  
 <span data-ttu-id="de585-112">Aucun</span><span class="sxs-lookup"><span data-stu-id="de585-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="de585-113">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="de585-113">Child Elements</span></span>  
  
|<span data-ttu-id="de585-114">Élément</span><span class="sxs-lookup"><span data-stu-id="de585-114">Element</span></span>|<span data-ttu-id="de585-115">Description</span><span class="sxs-lookup"><span data-stu-id="de585-115">Description</span></span>|  
|-------------|-----------------|  
|`cryptoClasses`|<span data-ttu-id="de585-116">Contient la liste des classes de chiffrement qui ont un mappage à un nom convivial dans l’élément **\<nameEntry>**.</span><span class="sxs-lookup"><span data-stu-id="de585-116">Contains a list of cryptography classes that have a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|`nameEntry`|<span data-ttu-id="de585-117">Mappe un nom de classe à un nom d’algorithme convivial, ce qui permet à une classe d’avoir plusieurs noms conviviaux.</span><span class="sxs-lookup"><span data-stu-id="de585-117">Maps a class name to a friendly algorithm name, which allows one class to have many friendly names.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="de585-118">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="de585-118">Parent Elements</span></span>  
  
|<span data-ttu-id="de585-119">Élément</span><span class="sxs-lookup"><span data-stu-id="de585-119">Element</span></span>|<span data-ttu-id="de585-120">Description</span><span class="sxs-lookup"><span data-stu-id="de585-120">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="de585-121">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="de585-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="de585-122">Contient des paramètres de chiffrement.</span><span class="sxs-lookup"><span data-stu-id="de585-122">Contains cryptography settings.</span></span>|  
|`cryptoNameMapping`|<span data-ttu-id="de585-123">Contient des mappages de classes à des noms conviviaux.</span><span class="sxs-lookup"><span data-stu-id="de585-123">Contains mappings of classes to friendly names.</span></span>|  
|`mscorlib`|<span data-ttu-id="de585-124">Contient le \<cryptographySettings > élément.</span><span class="sxs-lookup"><span data-stu-id="de585-124">Contains the \<cryptographySettings> element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="de585-125">Exemple</span><span class="sxs-lookup"><span data-stu-id="de585-125">Example</span></span>  
 <span data-ttu-id="de585-126">L’exemple suivant montre comment utiliser le  **\<cryptoNameMapping >** élément pour référencer une classe de chiffrement et configurer le runtime.</span><span class="sxs-lookup"><span data-stu-id="de585-126">The following example shows how to use the **\<cryptoNameMapping>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="de585-127">Vous pouvez ensuite passer la chaîne « RSA » pour le <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> méthode et l’utilisation du <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> méthode pour retourner un `MyCryptoRSAClass` objet.</span><span class="sxs-lookup"><span data-stu-id="de585-127">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass   MyCryptoRSA="MyCryptoRSAClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
            </cryptoClasses>  
            <nameEntry name="RSA" class="MyCryptoRSA"/>  
            <nameEntry name="System.Security.Cryptography.AsymmetricAlgorithm"  
                       class="MyCryptoRSA"/>  
         </cryptoNameMapping>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="de585-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="de585-128">See Also</span></span>  
 [<span data-ttu-id="de585-129">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="de585-129">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="de585-130">Schéma des paramètres de chiffrement</span><span class="sxs-lookup"><span data-stu-id="de585-130">Cryptography Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/index.md)  
 [<span data-ttu-id="de585-131">Services de chiffrement</span><span class="sxs-lookup"><span data-stu-id="de585-131">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)  
 [<span data-ttu-id="de585-132">Configuration des classes de chiffrement</span><span class="sxs-lookup"><span data-stu-id="de585-132">Configuring Cryptography Classes</span></span>](../../../../../docs/framework/configure-apps/configure-cryptography-classes.md)
