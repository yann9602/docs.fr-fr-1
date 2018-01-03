---
title: "&lt;mscorlib&gt; , élément pour les paramètres de chiffrement"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#mscorlib
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib
helpviewer_keywords:
- mscorlib element
- <mscorlib> element
ms.assetid: d549668f-31f1-4b92-8021-a9135c09ca3c
caps.latest.revision: "13"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 18948d538b01304e90cac3b36988ccf29a586da0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltmscorlibgt-element-for-cryptography-settings"></a><span data-ttu-id="6a6c2-102">&lt;mscorlib&gt; , élément pour les paramètres de chiffrement</span><span class="sxs-lookup"><span data-stu-id="6a6c2-102">&lt;mscorlib&gt; Element for Cryptography Settings</span></span>
<span data-ttu-id="6a6c2-103">Contient le [ \<cryptographySettings > élément](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptographysettings-element.md).</span><span class="sxs-lookup"><span data-stu-id="6a6c2-103">Contains the [\<cryptographySettings> element](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptographysettings-element.md).</span></span>  
  
 <span data-ttu-id="6a6c2-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="6a6c2-104">\<configuration></span></span>  
<span data-ttu-id="6a6c2-105">\<mscorlib ></span><span class="sxs-lookup"><span data-stu-id="6a6c2-105">\<mscorlib></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a6c2-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6a6c2-106">Syntax</span></span>  
  
```xml  
      <mscorlib>   
</mscorlib>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6a6c2-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="6a6c2-107">Attributes and Elements</span></span>  
 <span data-ttu-id="6a6c2-108">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="6a6c2-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6a6c2-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="6a6c2-109">Attributes</span></span>  
 <span data-ttu-id="6a6c2-110">Aucun.</span><span class="sxs-lookup"><span data-stu-id="6a6c2-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="6a6c2-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="6a6c2-111">Child Elements</span></span>  
  
|<span data-ttu-id="6a6c2-112">Élément</span><span class="sxs-lookup"><span data-stu-id="6a6c2-112">Element</span></span>|<span data-ttu-id="6a6c2-113">Description</span><span class="sxs-lookup"><span data-stu-id="6a6c2-113">Description</span></span>|  
|-------------|-----------------|  
|`cryptographySettings`|<span data-ttu-id="6a6c2-114">Contient des paramètres de chiffrement.</span><span class="sxs-lookup"><span data-stu-id="6a6c2-114">Contains cryptography settings.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6a6c2-115">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="6a6c2-115">Parent Elements</span></span>  
  
|<span data-ttu-id="6a6c2-116">Élément</span><span class="sxs-lookup"><span data-stu-id="6a6c2-116">Element</span></span>|<span data-ttu-id="6a6c2-117">Description</span><span class="sxs-lookup"><span data-stu-id="6a6c2-117">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="6a6c2-118">Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6a6c2-118">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="6a6c2-119">Exemple</span><span class="sxs-lookup"><span data-stu-id="6a6c2-119">Example</span></span>  
 <span data-ttu-id="6a6c2-120">L’exemple suivant montre comment utiliser le  **\<mscorlib >** élément pour référencer une classe de chiffrement et configurer le runtime.</span><span class="sxs-lookup"><span data-stu-id="6a6c2-120">The following example shows how to use the **\<mscorlib>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="6a6c2-121">Vous pouvez ensuite passer la chaîne « RSA » pour le <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> méthode et l’utilisation du <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> méthode pour retourner un `MyCryptoRSAClass` objet.</span><span class="sxs-lookup"><span data-stu-id="6a6c2-121">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6a6c2-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6a6c2-122">See Also</span></span>  
 <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A>  
 <xref:System.Security.Cryptography>  
 [<span data-ttu-id="6a6c2-123">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="6a6c2-123">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="6a6c2-124">Schéma des paramètres de chiffrement</span><span class="sxs-lookup"><span data-stu-id="6a6c2-124">Cryptography Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/index.md)  
 [<span data-ttu-id="6a6c2-125">Services de chiffrement</span><span class="sxs-lookup"><span data-stu-id="6a6c2-125">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)  
 [<span data-ttu-id="6a6c2-126">Configuration des classes de chiffrement</span><span class="sxs-lookup"><span data-stu-id="6a6c2-126">Configuring Cryptography Classes</span></span>](../../../../../docs/framework/configure-apps/configure-cryptography-classes.md)
