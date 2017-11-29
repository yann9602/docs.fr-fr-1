---
title: "Schéma des paramètres web"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Web.config configuration file [ASP.NET]
- ASP.NET configuration system, Web settings schema
- schema Web settings
- Web settings, schema [ASP.NET]
- configuration files [ASP.NET]
- configuration schema [.NET Framework], Web settings
ms.assetid: ae1ac356-267d-4753-8d7a-7a04eb45a9be
caps.latest.revision: "6"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: efdfba94bd2d2a64b3434c97f30a035f210fda9a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="web-settings-schema"></a><span data-ttu-id="46de6-102">Schéma des paramètres web</span><span class="sxs-lookup"><span data-stu-id="46de6-102">Web Settings Schema</span></span>
<span data-ttu-id="46de6-103">Les paramètres web spécifient les paramètres d’UC et d’ASP.NET au niveau de l’exécution qui s’appliquent au comportement à l’échelle des processus géré par la couche d’hébergement ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="46de6-103">Web settings specify CPU and execution-level ASP.NET settings that apply to process-wide behavior managed by the ASP.NET hosting layer.</span></span> <span data-ttu-id="46de6-104">Ces paramètres se distinguent des paramètres de type de domaine d’application spécifiés dans le fichier Web.config d’une application ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="46de6-104">These settings differ from application domain-type settings that are specified in the Web.config file of an ASP.NET application.</span></span>  
  
 <span data-ttu-id="46de6-105">Les paramètres web sont contenus dans les fichiers Aspnet.config, qui se trouvent dans les dossiers d’installation du .NET Framework, qui varient en fonction des versions.</span><span class="sxs-lookup"><span data-stu-id="46de6-105">Web settings are contained in Aspnet.config files, which are located in the installation folders for versions of the .NET Framework.</span></span> <span data-ttu-id="46de6-106">Par exemple, le fichier Aspnet.config pour [!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)] se trouve dans le dossier suivant :</span><span class="sxs-lookup"><span data-stu-id="46de6-106">For example, the Aspnet.config file for [!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)] is in the following folder:</span></span>  
  
 `C:\Windows\Microsoft.NET\Framework\v2.0.50727\`  
  
 <span data-ttu-id="46de6-107">Les paramètres web ne sont utilisés dans aucun autre des fichiers de configuration, tels que le fichier machine.config, le fichier racine Web.config ou les fichiers Web.config au niveau de l’application.</span><span class="sxs-lookup"><span data-stu-id="46de6-107">Web settings are not used in any other configuration files such as the machine.config file, the root Web.config, or application-level Web.config files.</span></span>  
  
 [<span data-ttu-id="46de6-108">\<configuration>, élément</span><span class="sxs-lookup"><span data-stu-id="46de6-108">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [<span data-ttu-id="46de6-109">\<system.web>, élément (paramètres web)</span><span class="sxs-lookup"><span data-stu-id="46de6-109">\<system.web> Element (Web Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/web/system-web-element-web-settings.md)  
  
 [<span data-ttu-id="46de6-110">\<applicationPool >, élément (paramètres Web)</span><span class="sxs-lookup"><span data-stu-id="46de6-110">\<applicationPool> Element (Web Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/web/applicationpool-element-web-settings.md)  
  
|<span data-ttu-id="46de6-111">Élément</span><span class="sxs-lookup"><span data-stu-id="46de6-111">Element</span></span>|<span data-ttu-id="46de6-112">Description</span><span class="sxs-lookup"><span data-stu-id="46de6-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="46de6-113">\<system.web></span><span class="sxs-lookup"><span data-stu-id="46de6-113">\<system.web></span></span>](../../../../../docs/framework/configure-apps/file-schema/web/system-web-element-web-settings.md)|<span data-ttu-id="46de6-114">Contient les informations utilisées par la couche d’hébergement ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="46de6-114">Contains information that the ASP.NET hosting layer uses.</span></span>|  
|[<span data-ttu-id="46de6-115">\<applicationPool></span><span class="sxs-lookup"><span data-stu-id="46de6-115">\<applicationPool></span></span>](../../../../../docs/framework/configure-apps/file-schema/web/applicationpool-element-web-settings.md)|<span data-ttu-id="46de6-116">Spécifie les paramètres d’UC et d’ASP.NET au niveau de l’exécution qui s’appliquent au comportement à l’échelle des processus géré par la couche d’hébergement ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="46de6-116">Specifies CPU and execution-level ASP.NET settings that apply to process-wide behavior managed by the ASP.NET hosting layer.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="46de6-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="46de6-117">See Also</span></span>  
 [<span data-ttu-id="46de6-118">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="46de6-118">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
