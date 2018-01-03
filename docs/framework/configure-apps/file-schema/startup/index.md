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
ms.openlocfilehash: 0536197d4cb8b30d99f514d8066e94bf84bffdf3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="startup-settings-schema"></a><span data-ttu-id="d3380-102">Schéma des paramètres de démarrage</span><span class="sxs-lookup"><span data-stu-id="d3380-102">Startup Settings Schema</span></span>
<span data-ttu-id="d3380-103">Les paramètres de démarrage spécifient la version du common language runtime qui doit exécuter l’application.</span><span class="sxs-lookup"><span data-stu-id="d3380-103">Startup settings specify the version of the common language runtime that should run the application.</span></span>  
  
|<span data-ttu-id="d3380-104">Élément</span><span class="sxs-lookup"><span data-stu-id="d3380-104">Element</span></span>|<span data-ttu-id="d3380-105">Description</span><span class="sxs-lookup"><span data-stu-id="d3380-105">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d3380-106">\<requiredRuntime></span><span class="sxs-lookup"><span data-stu-id="d3380-106">\<requiredRuntime></span></span>](../../../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md)|<span data-ttu-id="d3380-107">Spécifie que l’application prend en charge uniquement la version 1.0 du common language runtime.</span><span class="sxs-lookup"><span data-stu-id="d3380-107">Specifies that the application supports only version 1.0 of the common language runtime.</span></span> <span data-ttu-id="d3380-108">Les applications générées avec la version 1.1 du runtime doivent utiliser l’élément **\<supportedRuntime>**.</span><span class="sxs-lookup"><span data-stu-id="d3380-108">Applications built with runtime version 1.1 should use the **\<supportedRuntime>** element.</span></span>|  
|[<span data-ttu-id="d3380-109">\<supportedRuntime></span><span class="sxs-lookup"><span data-stu-id="d3380-109">\<supportedRuntime></span></span>](../../../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md)|<span data-ttu-id="d3380-110">Spécifie quelles versions du Common Language Runtime sont prises en charge par l'application.</span><span class="sxs-lookup"><span data-stu-id="d3380-110">Specifies which versions of the common language runtime the application supports.</span></span>|  
|[<span data-ttu-id="d3380-111">\<startup></span><span class="sxs-lookup"><span data-stu-id="d3380-111">\<startup></span></span>](../../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)|<span data-ttu-id="d3380-112">Contient les éléments **\<requiredRuntime>** et **\<supportedRuntime>**.</span><span class="sxs-lookup"><span data-stu-id="d3380-112">Contains the **\<requiredRuntime>** and **\<supportedRuntime>** elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d3380-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d3380-113">See Also</span></span>  
 [<span data-ttu-id="d3380-114">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="d3380-114">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="d3380-115">\<PaveOver> Spécification de la version du runtime à utiliser</span><span class="sxs-lookup"><span data-stu-id="d3380-115">\<PaveOver> Specifying Which Runtime Version to Use</span></span>](http://msdn.microsoft.com/en-us/c376208d-980d-42b4-865b-fbe0d9cc97c2)
