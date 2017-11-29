---
title: "Schéma des paramètres de chiffrement"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuration schema [.NET Framework], cryptography
- elements [.NET Framework], cryptography
- schema configuration settings
- cryptography, settings schema
- cryptography, mapping algorithm names
- configuration sections [.NET Framework]
- configuration settings [.NET Framework], cryptography
ms.assetid: 1f55050a-b2a3-4868-a3c0-da20826150f3
caps.latest.revision: "10"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: c7d1e193236528c96e8253668c742883090ae188
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="cryptography-settings-schema"></a><span data-ttu-id="a6749-102">Schéma des paramètres de chiffrement</span><span class="sxs-lookup"><span data-stu-id="a6749-102">Cryptography Settings Schema</span></span>
<span data-ttu-id="a6749-103">Le schéma des paramètres de chiffrement contient des éléments qui spécifient comment mapper des noms d’algorithmes conviviaux à des classes qui implémentent des algorithmes de chiffrement.</span><span class="sxs-lookup"><span data-stu-id="a6749-103">The cryptography settings schema contains elements that specify how to map friendly algorithm names to classes that implement cryptography algorithms.</span></span>  
  
 [<span data-ttu-id="a6749-104">**\<configuration>**</span><span class="sxs-lookup"><span data-stu-id="a6749-104">**\<configuration>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [<span data-ttu-id="a6749-105">**\<mscorlib>**</span><span class="sxs-lookup"><span data-stu-id="a6749-105">**\<mscorlib>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/mscorlib-element-for-cryptography-settings.md)  
  
 [<span data-ttu-id="a6749-106">**\<cryptographySettings>**</span><span class="sxs-lookup"><span data-stu-id="a6749-106">**\<cryptographySettings>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptographysettings-element.md)  
  
 [<span data-ttu-id="a6749-107">**\<cryptoNameMapping>**</span><span class="sxs-lookup"><span data-stu-id="a6749-107">**\<cryptoNameMapping>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptonamemapping-element.md)  
  
 [<span data-ttu-id="a6749-108">**\<cryptoClasses>**</span><span class="sxs-lookup"><span data-stu-id="a6749-108">**\<cryptoClasses>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclasses-element.md)  
  
 [<span data-ttu-id="a6749-109">**\<cryptoClass>**</span><span class="sxs-lookup"><span data-stu-id="a6749-109">**\<cryptoClass>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md)  
  
 [<span data-ttu-id="a6749-110">**\<nameEntry>**</span><span class="sxs-lookup"><span data-stu-id="a6749-110">**\<nameEntry>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md)  
  
 [<span data-ttu-id="a6749-111">**\<oidMap>**</span><span class="sxs-lookup"><span data-stu-id="a6749-111">**\<oidMap>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidmap-element.md)  
  
 [<span data-ttu-id="a6749-112">**\<oidEntry>**</span><span class="sxs-lookup"><span data-stu-id="a6749-112">**\<oidEntry>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidentry-element.md)  
  
|<span data-ttu-id="a6749-113">Élément</span><span class="sxs-lookup"><span data-stu-id="a6749-113">Element</span></span>|<span data-ttu-id="a6749-114">Description</span><span class="sxs-lookup"><span data-stu-id="a6749-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a6749-115">**\<cryptoClasses**></span><span class="sxs-lookup"><span data-stu-id="a6749-115">**\<cryptoClasses**></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclasses-element.md)|<span data-ttu-id="a6749-116">Contient la liste des classes de chiffrement qui ont un mappage à un nom convivial dans l’élément **\<nameEntry>**.</span><span class="sxs-lookup"><span data-stu-id="a6749-116">Contains a list of cryptography classes that have a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|[<span data-ttu-id="a6749-117">**\<cryptoClass**></span><span class="sxs-lookup"><span data-stu-id="a6749-117">**\<cryptoClass**></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md)|<span data-ttu-id="a6749-118">Contient une classe de chiffrement qui a un mappage à un nom convivial dans l’élément **\<nameEntry>**.</span><span class="sxs-lookup"><span data-stu-id="a6749-118">Contains a cryptography class that has a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|[<span data-ttu-id="a6749-119">**\<cryptographySettings**></span><span class="sxs-lookup"><span data-stu-id="a6749-119">**\<cryptographySettings**></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptographysettings-element.md)|<span data-ttu-id="a6749-120">Contient des paramètres de chiffrement.</span><span class="sxs-lookup"><span data-stu-id="a6749-120">Contains cryptography settings.</span></span>|  
|[<span data-ttu-id="a6749-121">**\<cryptoNameMapping**></span><span class="sxs-lookup"><span data-stu-id="a6749-121">**\<cryptoNameMapping**></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptonamemapping-element.md)|<span data-ttu-id="a6749-122">Contient des mappages de classes à des noms conviviaux.</span><span class="sxs-lookup"><span data-stu-id="a6749-122">Contains mappings of classes to friendly names.</span></span>|  
|[<span data-ttu-id="a6749-123">**\<mscorlib>**, élément pour les paramètres de chiffrement</span><span class="sxs-lookup"><span data-stu-id="a6749-123">**\<mscorlib>** element for cryptography settings</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/mscorlib-element-for-cryptography-settings.md)|<span data-ttu-id="a6749-124">Contient l’élément **\<cryptographySettings>**.</span><span class="sxs-lookup"><span data-stu-id="a6749-124">Contains the **\<cryptographySettings>** element.</span></span>|  
|[<span data-ttu-id="a6749-125">**\<nameEntry>**</span><span class="sxs-lookup"><span data-stu-id="a6749-125">**\<nameEntry>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md)|<span data-ttu-id="a6749-126">Mappe un nom de classe à un nom d’algorithme convivial, ce qui permet à une classe d’avoir plusieurs noms conviviaux.</span><span class="sxs-lookup"><span data-stu-id="a6749-126">Maps a class name to a friendly algorithm name, which allows one class to have many friendly names.</span></span>|  
|[<span data-ttu-id="a6749-127">**\<oidEntry>**</span><span class="sxs-lookup"><span data-stu-id="a6749-127">**\<oidEntry>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidentry-element.md)|<span data-ttu-id="a6749-128">Mappe un identificateur d’objet (OID) ASN.1 à un nom convivial.</span><span class="sxs-lookup"><span data-stu-id="a6749-128">Maps an ASN.1 object identifier (OID) to a friendly name.</span></span>|  
|[<span data-ttu-id="a6749-129">**\<oidMap>**</span><span class="sxs-lookup"><span data-stu-id="a6749-129">**\<oidMap>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidmap-element.md)|<span data-ttu-id="a6749-130">Contient les mappages d’OID ASN.1 aux classes.</span><span class="sxs-lookup"><span data-stu-id="a6749-130">Contains ASN.1 OID mappings to classes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a6749-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a6749-131">See Also</span></span>  
 [<span data-ttu-id="a6749-132">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="a6749-132">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="a6749-133">Services de chiffrement</span><span class="sxs-lookup"><span data-stu-id="a6749-133">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)
