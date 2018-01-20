---
title: "Schéma des paramètres de démarrage"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- startup settings schema
- schema startup settings
- configuration schema [.NET Framework], startup settings
ms.assetid: 03de6972-442a-4648-9f3e-efa654e3b949
caps.latest.revision: "10"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: f344139fd7d7c84aa75ab5e17b6312f3b0c3e031
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="startup-settings-schema"></a><span data-ttu-id="9cfac-102">Schéma des paramètres de démarrage</span><span class="sxs-lookup"><span data-stu-id="9cfac-102">Startup Settings Schema</span></span>
<span data-ttu-id="9cfac-103">Les paramètres de démarrage spécifient la version du common language runtime qui doit exécuter l’application.</span><span class="sxs-lookup"><span data-stu-id="9cfac-103">Startup settings specify the version of the common language runtime that should run the application.</span></span>  
  
|<span data-ttu-id="9cfac-104">Élément</span><span class="sxs-lookup"><span data-stu-id="9cfac-104">Element</span></span>|<span data-ttu-id="9cfac-105">Description</span><span class="sxs-lookup"><span data-stu-id="9cfac-105">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9cfac-106">\<requiredRuntime></span><span class="sxs-lookup"><span data-stu-id="9cfac-106">\<requiredRuntime></span></span>](../../../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md)|<span data-ttu-id="9cfac-107">Spécifie que l’application prend en charge uniquement la version 1.0 du common language runtime.</span><span class="sxs-lookup"><span data-stu-id="9cfac-107">Specifies that the application supports only version 1.0 of the common language runtime.</span></span> <span data-ttu-id="9cfac-108">Les applications générées avec la version 1.1 du runtime doivent utiliser l’élément **\<supportedRuntime>**.</span><span class="sxs-lookup"><span data-stu-id="9cfac-108">Applications built with runtime version 1.1 should use the **\<supportedRuntime>** element.</span></span>|  
|[<span data-ttu-id="9cfac-109">\<supportedRuntime></span><span class="sxs-lookup"><span data-stu-id="9cfac-109">\<supportedRuntime></span></span>](../../../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md)|<span data-ttu-id="9cfac-110">Spécifie quelles versions du Common Language Runtime sont prises en charge par l'application.</span><span class="sxs-lookup"><span data-stu-id="9cfac-110">Specifies which versions of the common language runtime the application supports.</span></span>|  
|[<span data-ttu-id="9cfac-111">\<startup></span><span class="sxs-lookup"><span data-stu-id="9cfac-111">\<startup></span></span>](../../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)|<span data-ttu-id="9cfac-112">Contient les éléments **\<requiredRuntime>** et **\<supportedRuntime>**.</span><span class="sxs-lookup"><span data-stu-id="9cfac-112">Contains the **\<requiredRuntime>** and **\<supportedRuntime>** elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9cfac-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9cfac-113">See Also</span></span>  
 [<span data-ttu-id="9cfac-114">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="9cfac-114">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="9cfac-115">\<PaveOver> Spécification de la version du runtime à utiliser</span><span class="sxs-lookup"><span data-stu-id="9cfac-115">\<PaveOver> Specifying Which Runtime Version to Use</span></span>](http://msdn.microsoft.com/library/c376208d-980d-42b4-865b-fbe0d9cc97c2)
