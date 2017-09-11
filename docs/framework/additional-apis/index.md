---
title: "API et bibliothèques de classes supplémentaires | Microsoft Docs"
ms.custom: 
ms.date: 04/12/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Additional class libraries
- Additional managed libraries
- .NET Framework out-of-band releases
- out-of-band releases
ms.assetid: cf2d9006-b631-4e5d-81cd-20aab78c60f1
caps.latest.revision: 12
author: mairaw
ms.author: mairaw
manager: wpickett
ms.translationtype: Human Translation
ms.sourcegitcommit: b53b8acc2a6c56db6a9d8a9b7c685a2d400a53e1
ms.openlocfilehash: 34815268b707aa70d174a1bbc04c32276db8412d
ms.contentlocale: fr-fr
ms.lasthandoff: 05/02/2017

---

# <a name="additional-class-libraries-and-apis"></a><span data-ttu-id="4be35-102">API et bibliothèques de classes supplémentaires</span><span class="sxs-lookup"><span data-stu-id="4be35-102">Additional class libraries and APIs</span></span>

<span data-ttu-id="4be35-103">Le .NET Framework est en constante évolution et pour améliorer le développement multiplateforme ou proposer des nouveautés à nos clients à un stade précoce, nous diffusons les nouvelles fonctionnalités hors bande (OOB).</span><span class="sxs-lookup"><span data-stu-id="4be35-103">The .NET Framework is constantly evolving and in order to improve cross-platform development or to introduce new functionality early to our customers, we release new features out of band (OOB).</span></span> <span data-ttu-id="4be35-104">Cette rubrique répertorie les projets OOB pour lesquels nous fournissons une documentation.</span><span class="sxs-lookup"><span data-stu-id="4be35-104">This topic lists the OOB projects that we provide documentation for.</span></span>  
  
<span data-ttu-id="4be35-105">En outre, certaines bibliothèques ciblent des plateformes ou des implémentations précises du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4be35-105">In addition, some libraries target specific platforms or implementations of the .NET Framework.</span></span> <span data-ttu-id="4be35-106">Par exemple, la classe <xref:System.Text.CodePagesEncodingProvider> met des codages de pages de codes à la disposition des applications UWP développées avec le .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4be35-106">For example, the <xref:System.Text.CodePagesEncodingProvider> class makes code page encodings available to UWP apps developed using the .NET Framework.</span></span> <span data-ttu-id="4be35-107">Cette rubrique liste également ces bibliothèques.</span><span class="sxs-lookup"><span data-stu-id="4be35-107">This topic lists these libraries as well.</span></span>  
  
## <a name="oob-projects"></a><span data-ttu-id="4be35-108">Projets OOB</span><span class="sxs-lookup"><span data-stu-id="4be35-108">OOB projects</span></span>
  
| <span data-ttu-id="4be35-109">Projet</span><span class="sxs-lookup"><span data-stu-id="4be35-109">Project</span></span> | <span data-ttu-id="4be35-110">Description</span><span class="sxs-lookup"><span data-stu-id="4be35-110">Description</span></span> |  
| ------- | ----------- |  
| <span data-ttu-id="4be35-111"><xref:System.Collections.Immutable></span><span class="sxs-lookup"><span data-stu-id="4be35-111"><xref:System.Collections.Immutable></span></span> | <span data-ttu-id="4be35-112">Fournit des collections thread-safe dont le contenu est assuré de ne jamais changer.</span><span class="sxs-lookup"><span data-stu-id="4be35-112">Provides collections that are thread safe and guaranteed to never change their contents.</span></span> |
| <span data-ttu-id="4be35-113"><xref:System.Net.Http.WinHttpHandler></span><span class="sxs-lookup"><span data-stu-id="4be35-113"><xref:System.Net.Http.WinHttpHandler></span></span> | <span data-ttu-id="4be35-114">Fournit un gestionnaire de messages pour <xref:System.Net.Http.HttpClient> à partir de l’interface WinHTTP de Windows.</span><span class="sxs-lookup"><span data-stu-id="4be35-114">Provides a message handler for <xref:System.Net.Http.HttpClient> based on the WinHTTP interface of Windows.</span></span> |
| [<span data-ttu-id="4be35-115">System.Numerics.Vectors</span><span class="sxs-lookup"><span data-stu-id="4be35-115">System.Numerics.Vectors</span></span>](https://msdn.microsoft.com/library/mt452176.aspx) | <span data-ttu-id="4be35-116">Fournit une bibliothèque de types de vecteurs qui peuvent tirer parti de l’accélération matérielle SIMD.</span><span class="sxs-lookup"><span data-stu-id="4be35-116">Provides a library of vector types that can take advantage of SIMD hardware-based acceleration.</span></span>| 
| <span data-ttu-id="4be35-117"><xref:System.Threading.Tasks.Dataflow></span><span class="sxs-lookup"><span data-stu-id="4be35-117"><xref:System.Threading.Tasks.Dataflow></span></span> | <span data-ttu-id="4be35-118">La bibliothèque de flux de données TPL fournit des composants de flux de données destinés à accroître la robustesse des applications prenant en charge l’accès concurrentiel.</span><span class="sxs-lookup"><span data-stu-id="4be35-118">The TPL Dataflow Library provides dataflow components to help increase the robustness of concurrency-enabled applications.</span></span> |  

## <a name="platform-specific-libraries"></a><span data-ttu-id="4be35-119">Bibliothèques propres à une plateforme</span><span class="sxs-lookup"><span data-stu-id="4be35-119">Platform-specific libraries</span></span>
  
| <span data-ttu-id="4be35-120">Projet</span><span class="sxs-lookup"><span data-stu-id="4be35-120">Project</span></span> | <span data-ttu-id="4be35-121">Description</span><span class="sxs-lookup"><span data-stu-id="4be35-121">Description</span></span> |  
| ------- | ----------- |  
| <span data-ttu-id="4be35-122"><xref:System.Text.CodePagesEncodingProvider></span><span class="sxs-lookup"><span data-stu-id="4be35-122"><xref:System.Text.CodePagesEncodingProvider></span></span> | <span data-ttu-id="4be35-123">Étend la classe <xref:System.Text.EncodingProvider> pour mettre des codages de pages de codes à la disposition des applications qui ciblent la plateforme Windows universelle.</span><span class="sxs-lookup"><span data-stu-id="4be35-123">Extends the <xref:System.Text.EncodingProvider> class to make code page encodings available to apps that target the Universal Windows Platform.</span></span> |  
  
## <a name="private-apis"></a><span data-ttu-id="4be35-124">API privées</span><span class="sxs-lookup"><span data-stu-id="4be35-124">Private APIs</span></span>  

<span data-ttu-id="4be35-125">Ces API prennent en charge l'infrastructure du produit et ne sont ni utilisables ni destinées à être utilisées directement à partir du code.</span><span class="sxs-lookup"><span data-stu-id="4be35-125">These APIs support the product infrastructure and are not intended/supported to be used directly from your code.</span></span>  
  
| <span data-ttu-id="4be35-126">Nom de l'API</span><span class="sxs-lookup"><span data-stu-id="4be35-126">API Name</span></span> |  
| -------- |  
| [<span data-ttu-id="4be35-127">s_isDebuggerCheckDisabledForTestPurposes Field</span><span class="sxs-lookup"><span data-stu-id="4be35-127">s_isDebuggerCheckDisabledForTestPurposes Field</span></span>](../../../docs/framework/additional-apis/s-isdebuggercheckdisabledfortestpurposes-field.md) |  
| [<span data-ttu-id="4be35-128">Classe DataMemberFieldEditor</span><span class="sxs-lookup"><span data-stu-id="4be35-128">DataMemberFieldEditor Class</span></span>](../../../docs/framework/additional-apis/datamemberfieldeditor-class.md) |  
| [<span data-ttu-id="4be35-129">Classe DataMemberListEditor</span><span class="sxs-lookup"><span data-stu-id="4be35-129">DataMemberListEditor Class</span></span>](../../../docs/framework/additional-apis/datamemberlisteditor-class.md) |  
  
## <a name="see-also"></a><span data-ttu-id="4be35-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4be35-130">See also</span></span>

[<span data-ttu-id="4be35-131">Versions finales hors plage de .NET Framework</span><span class="sxs-lookup"><span data-stu-id="4be35-131">The .NET Framework and Out-of-Band Releases</span></span>](../../../docs/framework/get-started/the-net-framework-and-out-of-band-releases.md)

