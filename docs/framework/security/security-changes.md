---
title: "Modifications de sécurité dans le .NET Framework"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Allow Partially Trusted Callers attribute
- .NET Framework 4, security changes
- .NET Framework security
- security-transparent code
- security-critical code
- code access security, changes
ms.assetid: 5e87881c-9c13-4b52-8ad1-e34bb46e8aaa
caps.latest.revision: 52
author: mairaw
ms.author: mairaw
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: b2ee4194f6e6788d99222badeb88e2702247904e
ms.contentlocale: fr-fr
ms.lasthandoff: 08/21/2017

---
# <a name="security-changes-in-the-net-framework"></a><span data-ttu-id="58875-102">Modifications de sécurité dans le .NET Framework</span><span class="sxs-lookup"><span data-stu-id="58875-102">Security Changes in the .NET Framework</span></span>
<span data-ttu-id="58875-103">L'évolution la plus importante sur le plan de la sécurité dans le [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] est l'utilisation de noms forts.</span><span class="sxs-lookup"><span data-stu-id="58875-103">The most important change to security in the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] is in strong naming.</span></span> <span data-ttu-id="58875-104">Pour obtenir une description de ces modifications, consultez [Enhanced Strong Naming](../../../docs/framework/app-domains/enhanced-strong-naming.md) .</span><span class="sxs-lookup"><span data-stu-id="58875-104">See [Enhanced Strong Naming](../../../docs/framework/app-domains/enhanced-strong-naming.md) for a description of those changes.</span></span>  
  
 <span data-ttu-id="58875-105">Le .NET Framework fournit un modèle de sécurité à deux niveaux pour les applications managées.</span><span class="sxs-lookup"><span data-stu-id="58875-105">The .NET Framework provides a two-tier security model for managed applications.</span></span> <span data-ttu-id="58875-106">Les applications[!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] s'exécutent dans un conteneur de sécurité Windows qui limite l'accès aux ressources.</span><span class="sxs-lookup"><span data-stu-id="58875-106">[!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] apps run in a Windows security container that limits access to resources.</span></span> <span data-ttu-id="58875-107">Dans ce conteneur, les applications managées s'exécutent en mode confiance totale.</span><span class="sxs-lookup"><span data-stu-id="58875-107">Within that container, managed applications run fully trusted.</span></span> <span data-ttu-id="58875-108">Du point de vue de la sécurité d'accès du code (CAS), un développeur ne peut rien faire pour élever les privilèges.</span><span class="sxs-lookup"><span data-stu-id="58875-108">From a code access security (CAS) perspective, there is nothing a developer can do to elevate privileges.</span></span> <span data-ttu-id="58875-109">Pour plus d’informations sur les privilèges octroyés par Windows, consultez [Déclarations des fonctionnalités d’application (applications du Windows Store)](http://go.microsoft.com/fwlink/?LinkId=230436) dans le centre de développement Windows.</span><span class="sxs-lookup"><span data-stu-id="58875-109">For information about the privileges granted by Windows, see [App capability declarations (Windows Store apps)](http://go.microsoft.com/fwlink/?LinkId=230436) in the Windows Dev Center.</span></span> <span data-ttu-id="58875-110">Pour plus d’informations sur la création d’une application [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] , consultez [Créer votre première application Windows Runtime en C# ou Visual Basic](http://go.microsoft.com/fwlink/?LinkId=230461).</span><span class="sxs-lookup"><span data-stu-id="58875-110">For information about creating a [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] app, see [Create your first Windows Store app using C# or Visual Basic](http://go.microsoft.com/fwlink/?LinkId=230461).</span></span>

