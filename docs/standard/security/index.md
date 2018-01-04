---
title: "Sécurité dans le .NET Framework"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- .NET Framework, security
- security [.NET Framework], about security
- application development [.NET Framework], security
- security [.NET Framework]
ms.assetid: 9a9621d7-8883-4a4f-a874-65e8e09e20a6
caps.latest.revision: "37"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 7f8600da624ff75ce2dbd5c417f886d6b3b1ac37
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2017
---
# <a name="security-in-the-net-framework"></a><span data-ttu-id="d29a8-102">Sécurité dans le .NET Framework</span><span class="sxs-lookup"><span data-stu-id="d29a8-102">Security in the .NET Framework</span></span>
<span data-ttu-id="d29a8-103">Le Common Language Runtime et le .NET Framework offrent un grand nombre de classes et de services utiles aux développeurs pour écrire facilement du code sécurisé. Ils permettent aux administrateurs système de personnaliser les autorisations accordées au code afin qu'il puisse accéder à des ressources protégées.</span><span class="sxs-lookup"><span data-stu-id="d29a8-103">The common language runtime and the .NET Framework provide many useful classes and services that enable developers to easily write secure code and enable system administrators to customize the permissions granted to code so that it can access protected resources.</span></span> <span data-ttu-id="d29a8-104">En outre, le runtime et le .NET Framework offrent des classes et des services facilitant l'utilisation du chiffrement et de la sécurité basée sur les rôles.</span><span class="sxs-lookup"><span data-stu-id="d29a8-104">In addition, the runtime and the .NET Framework provide useful classes and services that facilitate the use of cryptography and role-based security.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d29a8-105">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="d29a8-105">In This Section</span></span>  
 [<span data-ttu-id="d29a8-106">Modifications de sécurité</span><span class="sxs-lookup"><span data-stu-id="d29a8-106">Security Changes</span></span>](../../../docs/framework/security/security-changes.md)  
 <span data-ttu-id="d29a8-107">Décrit les modifications importantes apportées au système de sécurité du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d29a8-107">Describes important changes to the .NET Framework security system.</span></span>  
  
 [<span data-ttu-id="d29a8-108">Concepts fondamentaux sur la sécurité</span><span class="sxs-lookup"><span data-stu-id="d29a8-108">Key Security Concepts</span></span>](../../../docs/standard/security/key-security-concepts.md)  
 <span data-ttu-id="d29a8-109">Offre une vue d’ensemble des fonctionnalités de sécurité du Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="d29a8-109">Provides an overview of common language runtime security features.</span></span> <span data-ttu-id="d29a8-110">Cette section s'adresse aux développeurs et aux administrateurs système.</span><span class="sxs-lookup"><span data-stu-id="d29a8-110">This section is of interest to developers and system administrators.</span></span>  
  
 [<span data-ttu-id="d29a8-111">Sécurité basée sur les rôles</span><span class="sxs-lookup"><span data-stu-id="d29a8-111">Role-Based Security</span></span>](../../../docs/standard/security/role-based-security.md)  
 <span data-ttu-id="d29a8-112">Explique comment interagir avec la sécurité basée sur les rôles dans votre code.</span><span class="sxs-lookup"><span data-stu-id="d29a8-112">Describes how to interact with role-based security in your code.</span></span> <span data-ttu-id="d29a8-113">Cette section s'adresse aux développeurs.</span><span class="sxs-lookup"><span data-stu-id="d29a8-113">This section is of interest to developers.</span></span>  
  
 [<span data-ttu-id="d29a8-114">Modèle de chiffrement</span><span class="sxs-lookup"><span data-stu-id="d29a8-114">Cryptography Model</span></span>](../../../docs/standard/security/cryptography-model.md)  
 <span data-ttu-id="d29a8-115">Offre une vue d'ensemble des services de chiffrement fournis par le .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d29a8-115">Provides an overview of cryptographic services provided by the .NET Framework.</span></span> <span data-ttu-id="d29a8-116">Cette section s'adresse aux développeurs.</span><span class="sxs-lookup"><span data-stu-id="d29a8-116">This section is of interest to developers.</span></span>  
  
 [<span data-ttu-id="d29a8-117">Instructions de codage sécurisé</span><span class="sxs-lookup"><span data-stu-id="d29a8-117">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)  
 <span data-ttu-id="d29a8-118">Décrit certaines des meilleures pratiques pour la création d'applications .NET Framework fiables.</span><span class="sxs-lookup"><span data-stu-id="d29a8-118">Describes some of the best practices for creating reliable .NET Framework applications.</span></span> <span data-ttu-id="d29a8-119">Cette section s'adresse aux développeurs.</span><span class="sxs-lookup"><span data-stu-id="d29a8-119">This section is of interest to developers.</span></span>  
  
 [<span data-ttu-id="d29a8-120">Instructions de codage sécurisé pour le code non managé</span><span class="sxs-lookup"><span data-stu-id="d29a8-120">Secure Coding Guidelines for Unmanaged Code</span></span>](../../../docs/framework/security/secure-coding-guidelines-for-unmanaged-code.md)  
 <span data-ttu-id="d29a8-121">Aborde certaines meilleures pratiques, ainsi que les problèmes de sécurité rencontrés pendant l'appel de code non managé.</span><span class="sxs-lookup"><span data-stu-id="d29a8-121">Describes some of the best practices and security concerns when calling unmanaged code.</span></span>  
  
 [<span data-ttu-id="d29a8-122">Windows Identity Foundation</span><span class="sxs-lookup"><span data-stu-id="d29a8-122">Windows Identity Foundation</span></span>](../../../docs/framework/security/index.md)  
 <span data-ttu-id="d29a8-123">Explique comment vous pouvez implémenter l'identité basée sur des demandes dans vos applications.</span><span class="sxs-lookup"><span data-stu-id="d29a8-123">Describes how you can implement claims-based identity in your applications.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="d29a8-124">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="d29a8-124">Related Sections</span></span>  
 [<span data-ttu-id="d29a8-125">Guide de développement</span><span class="sxs-lookup"><span data-stu-id="d29a8-125">Development Guide</span></span>](../../../docs/framework/development-guide.md)  
 <span data-ttu-id="d29a8-126">Fournit un guide sur tous les domaines technologiques clés et les tâches relatives au développement d’applications, notamment la création, la configuration, le débogage, la sécurisation et le déploiement de votre application, ainsi que des informations sur la programmation dynamique, l’interopérabilité, l’extensibilité, la gestion de mémoire et les threads.</span><span class="sxs-lookup"><span data-stu-id="d29a8-126">Provides a guide to all key technology areas and tasks for application development, including creating, configuring, debugging, securing, and deploying your application, and information about dynamic programming, interoperability, extensibility, memory management, and threading.</span></span>
