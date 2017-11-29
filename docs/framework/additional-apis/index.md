---
title: "API et bibliothèques de classes supplémentaires"
ms.custom: 
ms.date: 04/12/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Additional class libraries
- Additional managed libraries
- .NET Framework out-of-band releases
- out-of-band releases
ms.assetid: cf2d9006-b631-4e5d-81cd-20aab78c60f1
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e3bb7a7c53cbca8bbd4026b46ce59589cef22382
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="additional-class-libraries-and-apis"></a><span data-ttu-id="079fd-102">API et bibliothèques de classes supplémentaires</span><span class="sxs-lookup"><span data-stu-id="079fd-102">Additional class libraries and APIs</span></span>

<span data-ttu-id="079fd-103">Le .NET Framework est en constante évolution et pour améliorer le développement multiplateforme ou proposer des nouveautés à nos clients à un stade précoce, nous diffusons les nouvelles fonctionnalités hors bande (OOB).</span><span class="sxs-lookup"><span data-stu-id="079fd-103">The .NET Framework is constantly evolving and in order to improve cross-platform development or to introduce new functionality early to our customers, we release new features out of band (OOB).</span></span> <span data-ttu-id="079fd-104">Cette rubrique répertorie les projets OOB pour lesquels nous fournissons une documentation.</span><span class="sxs-lookup"><span data-stu-id="079fd-104">This topic lists the OOB projects that we provide documentation for.</span></span>  
  
<span data-ttu-id="079fd-105">En outre, certaines bibliothèques ciblent des plateformes ou des implémentations précises du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="079fd-105">In addition, some libraries target specific platforms or implementations of the .NET Framework.</span></span> <span data-ttu-id="079fd-106">Par exemple, la <xref:System.Text.CodePagesEncodingProvider> classe rend les codages de pages de code disponibles pour les applications UWP développées à l’aide de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="079fd-106">For example, the <xref:System.Text.CodePagesEncodingProvider> class makes code page encodings available to UWP apps developed using the .NET Framework.</span></span> <span data-ttu-id="079fd-107">Cette rubrique liste également ces bibliothèques.</span><span class="sxs-lookup"><span data-stu-id="079fd-107">This topic lists these libraries as well.</span></span>  
  
## <a name="oob-projects"></a><span data-ttu-id="079fd-108">Projets OOB</span><span class="sxs-lookup"><span data-stu-id="079fd-108">OOB projects</span></span>
  
| <span data-ttu-id="079fd-109">Projet</span><span class="sxs-lookup"><span data-stu-id="079fd-109">Project</span></span> | <span data-ttu-id="079fd-110">Description</span><span class="sxs-lookup"><span data-stu-id="079fd-110">Description</span></span> |  
| ------- | ----------- |  
| <xref:System.Collections.Immutable> | <span data-ttu-id="079fd-111">Fournit des collections thread-safe dont le contenu est assuré de ne jamais changer.</span><span class="sxs-lookup"><span data-stu-id="079fd-111">Provides collections that are thread safe and guaranteed to never change their contents.</span></span> |
| <xref:System.Net.Http.WinHttpHandler> | <span data-ttu-id="079fd-112">Fournit un gestionnaire de messages pour <xref:System.Net.Http.HttpClient> basé sur l’interface WinHTTP de Windows.</span><span class="sxs-lookup"><span data-stu-id="079fd-112">Provides a message handler for <xref:System.Net.Http.HttpClient> based on the WinHTTP interface of Windows.</span></span> |
| [<span data-ttu-id="079fd-113">System.Numerics.Vectors</span><span class="sxs-lookup"><span data-stu-id="079fd-113">System.Numerics.Vectors</span></span>](https://msdn.microsoft.com/library/mt452176.aspx) | <span data-ttu-id="079fd-114">Fournit une bibliothèque de types de vecteurs qui peuvent tirer parti de l’accélération matérielle SIMD.</span><span class="sxs-lookup"><span data-stu-id="079fd-114">Provides a library of vector types that can take advantage of SIMD hardware-based acceleration.</span></span>| 
| <xref:System.Threading.Tasks.Dataflow> | <span data-ttu-id="079fd-115">La bibliothèque de flux de données TPL fournit des composants de flux de données destinés à accroître la robustesse des applications prenant en charge l’accès concurrentiel.</span><span class="sxs-lookup"><span data-stu-id="079fd-115">The TPL Dataflow Library provides dataflow components to help increase the robustness of concurrency-enabled applications.</span></span> |  

## <a name="platform-specific-libraries"></a><span data-ttu-id="079fd-116">Bibliothèques propres à une plateforme</span><span class="sxs-lookup"><span data-stu-id="079fd-116">Platform-specific libraries</span></span>
  
| <span data-ttu-id="079fd-117">Projet</span><span class="sxs-lookup"><span data-stu-id="079fd-117">Project</span></span> | <span data-ttu-id="079fd-118">Description</span><span class="sxs-lookup"><span data-stu-id="079fd-118">Description</span></span> |  
| ------- | ----------- |  
| <xref:System.Text.CodePagesEncodingProvider> | <span data-ttu-id="079fd-119">Étend la <xref:System.Text.EncodingProvider> classe pour rendre les codages de pages de code disponibles pour les applications qui ciblent la plateforme Windows universelle.</span><span class="sxs-lookup"><span data-stu-id="079fd-119">Extends the <xref:System.Text.EncodingProvider> class to make code page encodings available to apps that target the Universal Windows Platform.</span></span> |  
  
## <a name="private-apis"></a><span data-ttu-id="079fd-120">API privées</span><span class="sxs-lookup"><span data-stu-id="079fd-120">Private APIs</span></span>  

<span data-ttu-id="079fd-121">Ces API prennent en charge l'infrastructure du produit et ne sont ni utilisables ni destinées à être utilisées directement à partir du code.</span><span class="sxs-lookup"><span data-stu-id="079fd-121">These APIs support the product infrastructure and are not intended/supported to be used directly from your code.</span></span>  
  
| <span data-ttu-id="079fd-122">Nom de l'API</span><span class="sxs-lookup"><span data-stu-id="079fd-122">API Name</span></span> |
| -------- |
| [<span data-ttu-id="079fd-123">Classe de System.Net.Connection</span><span class="sxs-lookup"><span data-stu-id="079fd-123">System.Net.Connection Class</span></span>](../../../docs/framework/additional-apis/connection.md) |
| [<span data-ttu-id="079fd-124">System.Net.Connection.m\_WriteList champ</span><span class="sxs-lookup"><span data-stu-id="079fd-124">System.Net.Connection.m\_WriteList Field</span></span>](../../../docs/framework/additional-apis/m_writelist.md) |
| [<span data-ttu-id="079fd-125">Classe de System.Net.ConnectionGroup</span><span class="sxs-lookup"><span data-stu-id="079fd-125">System.Net.ConnectionGroup Class</span></span>](../../../docs/framework/additional-apis/connectiongroup.md) |
| [<span data-ttu-id="079fd-126">System.Net.ConnectionGroup.m\_ConnectionList champ</span><span class="sxs-lookup"><span data-stu-id="079fd-126">System.Net.ConnectionGroup.m\_ConnectionList Field</span></span>](../../../docs/framework/additional-apis/m_connectionlist.md) |
| [<span data-ttu-id="079fd-127">System.Net.HttpWebRequest. \_HttpResponse champ</span><span class="sxs-lookup"><span data-stu-id="079fd-127">System.Net.HttpWebRequest.\_HttpResponse Field</span></span>](../../../docs/framework/additional-apis/_httpresponse.md) |
| [<span data-ttu-id="079fd-128">System.Net.HttpWebRequest. \_AutoRedirects champ</span><span class="sxs-lookup"><span data-stu-id="079fd-128">System.Net.HttpWebRequest.\_AutoRedirects Field</span></span>](../../../docs/framework/additional-apis/_autoredirects.md) |
| [<span data-ttu-id="079fd-129">System.Net.ServicePoint.m\_ConnectionGroupList champ</span><span class="sxs-lookup"><span data-stu-id="079fd-129">System.Net.ServicePoint.m\_ConnectionGroupList Field</span></span>](../../../docs/framework/additional-apis/m_connectiongrouplist.md) |
| [<span data-ttu-id="079fd-130">System.Net.ServicePointManager.s\_ServicePointTable champ</span><span class="sxs-lookup"><span data-stu-id="079fd-130">System.Net.ServicePointManager.s\_ServicePointTable Field</span></span>](../../../docs/framework/additional-apis/s_servicepointtable.md) |
| [<span data-ttu-id="079fd-131">System.Windows.Diagnostics.VisualDiagnostics.s\_isDebuggerCheckDisabledForTestPurposes champ</span><span class="sxs-lookup"><span data-stu-id="079fd-131">System.Windows.Diagnostics.VisualDiagnostics.s\_isDebuggerCheckDisabledForTestPurposes Field</span></span>](../../../docs/framework/additional-apis/s-isdebuggercheckdisabledfortestpurposes-field.md) |
| [<span data-ttu-id="079fd-132">Classe de System.Windows.Forms.Design.DataMemberFieldEditor</span><span class="sxs-lookup"><span data-stu-id="079fd-132">System.Windows.Forms.Design.DataMemberFieldEditor Class</span></span>](../../../docs/framework/additional-apis/datamemberfieldeditor-class.md) |
| [<span data-ttu-id="079fd-133">Classe de System.Windows.Forms.Design.DataMemberListEditor</span><span class="sxs-lookup"><span data-stu-id="079fd-133">System.Windows.Forms.Design.DataMemberListEditor Class</span></span>](../../../docs/framework/additional-apis/datamemberlisteditor-class.md) |
  
## <a name="see-also"></a><span data-ttu-id="079fd-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="079fd-134">See also</span></span>

[<span data-ttu-id="079fd-135">Versions finales hors plage de .NET Framework</span><span class="sxs-lookup"><span data-stu-id="079fd-135">The .NET Framework and Out-of-Band Releases</span></span>](../../../docs/framework/get-started/the-net-framework-and-out-of-band-releases.md)
