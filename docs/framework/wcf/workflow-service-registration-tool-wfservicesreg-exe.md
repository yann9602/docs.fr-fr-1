---
title: Outil WorkFlow Service Registration (WFServicesReg.exe)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9e92c87b-99c5-4e8d-9d53-7944cc2b47d3
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f88d5f63ce77eae013e4df995956dc35771a0274
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="workflow-service-registration-tool-wfservicesregexe"></a><span data-ttu-id="00339-102">Outil WorkFlow Service Registration (WFServicesReg.exe)</span><span class="sxs-lookup"><span data-stu-id="00339-102">WorkFlow Service Registration Tool (WFServicesReg.exe)</span></span>
<span data-ttu-id="00339-103">Workflow Services Registration (WFServicesReg.exe) est un outil autonome qui peut être utilisé pour ajouter, supprimer ou réparer les éléments de configuration correspondant aux services Windows Workflow Foundation (WF).</span><span class="sxs-lookup"><span data-stu-id="00339-103">Workflow Services Registration tool (WFServicesReg.exe) is a stand-alone tool that can be used to add, remove, or repair the configuration elements for Windows Workflow Foundation (WF) services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00339-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="00339-104">Syntax</span></span>  
  
```  
WFServicesReg.exe [-c | -r | -v | -m | -i]  
```  
  
## <a name="remarks"></a><span data-ttu-id="00339-105">Remarques</span><span class="sxs-lookup"><span data-stu-id="00339-105">Remarks</span></span>  
 <span data-ttu-id="00339-106">Cet outil se trouve à l'emplacement d'installation de [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)], c'est-à-dire %windir%\Microsoft.NET\Framework\v3.5 ou %windir%\Microsoft.NET\Framework64\v3.5 pour les ordinateurs 64 bits.</span><span class="sxs-lookup"><span data-stu-id="00339-106">The tool can be found at the [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] installation location, specifically, %windir%\Microsoft.NET\Framework\v3.5, or at %windir%\Microsoft.NET\Framework64\v3.5 in 64-bit machines.</span></span>  
  
 <span data-ttu-id="00339-107">Les tableaux suivants décrivent les options pouvant être utilisées avec l'outil Workflow Services Registration (WFServicesReg.exe).</span><span class="sxs-lookup"><span data-stu-id="00339-107">The following tables describe the options that can be used with the Workflow Services Registration tool (WFServicesReg.exe).</span></span>  
  
|<span data-ttu-id="00339-108">Option</span><span class="sxs-lookup"><span data-stu-id="00339-108">Option</span></span>|<span data-ttu-id="00339-109">Description</span><span class="sxs-lookup"><span data-stu-id="00339-109">Description</span></span>|  
|------------|-----------------|  
|`/c`|<span data-ttu-id="00339-110">Configure les services de workflow Windows.</span><span class="sxs-lookup"><span data-stu-id="00339-110">Configures Windows Workflow Services.</span></span> <span data-ttu-id="00339-111">Utilisé dans les scénarios d'installation et de réparation.</span><span class="sxs-lookup"><span data-stu-id="00339-111">Used in install and repair scenarios.</span></span>|  
|`/r`|<span data-ttu-id="00339-112">Supprime la configuration des services de workflow Windows.</span><span class="sxs-lookup"><span data-stu-id="00339-112">Removes Windows Workflow Services Configuration.</span></span>|  
|`/v`|<span data-ttu-id="00339-113">Imprimez des informations détaillées (pour la configuration ou la suppression).</span><span class="sxs-lookup"><span data-stu-id="00339-113">Print verbose information (for either configuration or removal).</span></span>|  
|`/m`|<span data-ttu-id="00339-114">Active le format d'enregistrement MSI.</span><span class="sxs-lookup"><span data-stu-id="00339-114">Enables MSI logging format.</span></span>|  
|`/i`|<span data-ttu-id="00339-115">Réduit la fenêtre lorsque l'application est exécutée.</span><span class="sxs-lookup"><span data-stu-id="00339-115">Minimizes the window when the application runs.</span></span>|  
  
## <a name="registration"></a><span data-ttu-id="00339-116">Inscription</span><span class="sxs-lookup"><span data-stu-id="00339-116">Registration</span></span>  
 <span data-ttu-id="00339-117">L'outil vérifie le fichier Web.config et enregistre les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="00339-117">The tool inspects the Web.config file and registers the following:</span></span>  
  
-   <span data-ttu-id="00339-118">Assemblys de référence de [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="00339-118">[!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] reference assemblies.</span></span>  
  
-   <span data-ttu-id="00339-119">Fournisseur de version pour fichiers .xoml.</span><span class="sxs-lookup"><span data-stu-id="00339-119">A build provider for .xoml files.</span></span>  
  
-   <span data-ttu-id="00339-120">Gestionnaires HTTP pour fichiers .xoml et .rules.</span><span class="sxs-lookup"><span data-stu-id="00339-120">HTTP handlers for .xoml and .rules files.</span></span>  
  
 <span data-ttu-id="00339-121">L'outil vérifie le fichier Machine.config et enregistre les extensions suivantes :</span><span class="sxs-lookup"><span data-stu-id="00339-121">The tool inspects the Machine.config file and registers the following extensions:</span></span>  
  
-   <span data-ttu-id="00339-122">behaviorExtensions</span><span class="sxs-lookup"><span data-stu-id="00339-122">behaviorExtensions</span></span>  
  
-   <span data-ttu-id="00339-123">bindingElementExtensions</span><span class="sxs-lookup"><span data-stu-id="00339-123">bindingElementExtensions</span></span>  
  
-   <span data-ttu-id="00339-124">bindingExtensions</span><span class="sxs-lookup"><span data-stu-id="00339-124">bindingExtensions</span></span>  
  
 <span data-ttu-id="00339-125">L'outil enregistre également les importateurs de métadonnées clients suivants :</span><span class="sxs-lookup"><span data-stu-id="00339-125">The tool also registers the following client metadata importers:</span></span>  
  
-   <span data-ttu-id="00339-126">policyImporters</span><span class="sxs-lookup"><span data-stu-id="00339-126">policyImporters</span></span>  
  
-   <span data-ttu-id="00339-127">wsdlImporters</span><span class="sxs-lookup"><span data-stu-id="00339-127">wsdlImporters</span></span>  
  
 <span data-ttu-id="00339-128">L'outil enregistre également des mappages de scripts .xoml et .rules ainsi que des gestionnaires dans la métabase IIS.</span><span class="sxs-lookup"><span data-stu-id="00339-128">The tool also registers .xoml and .rules scriptmaps and handlers in the IIS metabase.</span></span>  
  
 <span data-ttu-id="00339-129">Sur les ordinateurs sous [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] et [!INCLUDE[wxp](../../../includes/wxp-md.md)] (IIS 5.1 et [!INCLUDE[iis601](../../../includes/iis601-md.md)]), un jeu de mappages de scripts .xoml et .rules est enregistré.</span><span class="sxs-lookup"><span data-stu-id="00339-129">On [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] and [!INCLUDE[wxp](../../../includes/wxp-md.md)] machines (IIS 5.1 and [!INCLUDE[iis601](../../../includes/iis601-md.md)]), one set of .xoml and .rules scriptmaps are registered.</span></span>  
  
 <span data-ttu-id="00339-130">Sur les ordinateurs 64 bits, l'outil enregistre les mappages de scripts en mode WOW si le commutateur `Enable32BitAppOnWin64` est activé, ou les mappages de scripts 64 bits natifs si le commutateur `Enable32BitAppOnWin64` est désactivé.</span><span class="sxs-lookup"><span data-stu-id="00339-130">On 64-bit machines, the tool registers WOW mode scriptmaps if the `Enable32BitAppOnWin64` switch is enabled, or native 64-bit scriptmaps if the `Enable32BitAppOnWin64` switch is disabled.</span></span>  
  
 <span data-ttu-id="00339-131">Sur [!INCLUDE[wv](../../../includes/wv-md.md)] et Windows Server 2008 (IIS 7.0 et versions ultérieures) machines, deux jeux de gestionnaires .xoml et .rules sont enregistrés : un pour le mode intégré et un pour le mode classique.</span><span class="sxs-lookup"><span data-stu-id="00339-131">On [!INCLUDE[wv](../../../includes/wv-md.md)] and Windows Server 2008 (IIS 7.0 and above) machines, two sets of .xoml and .rules handlers are registered: one for Integrated mode and one for Classic mode.</span></span>  
  
 <span data-ttu-id="00339-132">Sur les ordinateurs 64 bits, trois jeux de gestionnaires sont enregistrés (indépendamment de l'état du commutateur `Enable32BitAppOnWin64`) : un pour le mode intégré, un pour le mode classique WOW et le dernier pour le mode classique 64 bits natif.</span><span class="sxs-lookup"><span data-stu-id="00339-132">On 64-bit machines, three sets of handlers are registered (regardless of the state of the `Enable32BitAppOnWin64` switch): one for Integrated mode, one for WOW Classic mode and one for native 64-bit Classic mode.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="00339-133">Contrairement à ServiceModelReg.exe, WFServicesReg.exe n'autorise pas l'ajout, la suppression ou la réparation des mappages de scripts ou des gestionnaires correspondant à un site Web particulier.</span><span class="sxs-lookup"><span data-stu-id="00339-133">Unlike ServiceModelreg.exe, WFServicesReg.exe does not allow adding, removing, or repairing scriptmaps or handlers for a particular Web site.</span></span> <span data-ttu-id="00339-134">Pour contourner ce problème, consultez la section « Réparation des mappages de scripts ».</span><span class="sxs-lookup"><span data-stu-id="00339-134">For a workaround to this issue, see the "Repairing the Scriptmaps" section.</span></span>  
  
## <a name="usage-scenarios"></a><span data-ttu-id="00339-135">Scénarios d'utilisation</span><span class="sxs-lookup"><span data-stu-id="00339-135">Usage Scenarios</span></span>  
  
### <a name="installing-iis-after-net-framework-35-is-installed"></a><span data-ttu-id="00339-136">Installation des services IIS après l'installation de .NET Framework 3.5</span><span class="sxs-lookup"><span data-stu-id="00339-136">Installing IIS after .NET Framework 3.5 is installed</span></span>  
 <span data-ttu-id="00339-137">Sous [!INCLUDE[ws2003](../../../includes/ws2003-md.md)], [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] est installé avant les services IIS.</span><span class="sxs-lookup"><span data-stu-id="00339-137">On a [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] machine, [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] is installed prior to IIS installation.</span></span> <span data-ttu-id="00339-138">En raison de l'indisponibilité de la métabase IIS, l'installation de [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] aboutit sans installer les mappages de scripts .xoml et .rules.</span><span class="sxs-lookup"><span data-stu-id="00339-138">Due to the unavailability of the IIS metabase, installation of [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] succeeds without installing .xoml and .rules scriptmaps.</span></span>  
  
 <span data-ttu-id="00339-139">Après avoir installé les services IIS, vous pouvez utiliser l'outil WFServicesReg.exe avec le commutateur `/c` pour installer ces mappages de scripts spécifiques.</span><span class="sxs-lookup"><span data-stu-id="00339-139">After IIS is installed, you can use the WFServicesReg.exe tool with the `/c` switch to install these specific scriptmaps.</span></span>  
  
### <a name="repairing-the-scriptmaps"></a><span data-ttu-id="00339-140">Réparation des mappages de scripts</span><span class="sxs-lookup"><span data-stu-id="00339-140">Repairing the Scriptmaps</span></span>  
  
#### <a name="scriptmap-deleted-under-web-sites-node"></a><span data-ttu-id="00339-141">Mappage de scripts supprimé sous le nœud Sites Web</span><span class="sxs-lookup"><span data-stu-id="00339-141">Scriptmap deleted under Web Sites node</span></span>  
 <span data-ttu-id="00339-142">Sous [!INCLUDE[ws2003](../../../includes/ws2003-md.md)], le mappage de scripts .xoml ou .rules est supprimé par erreur du nœud Sites Web.</span><span class="sxs-lookup"><span data-stu-id="00339-142">On a [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] machine, .xoml or .rules is accidentally deleted from the Web Sites node.</span></span> <span data-ttu-id="00339-143">Ce problème peut être résolu en exécutant l'outil WFServicesReg.exe avec le commutateur `/c`.</span><span class="sxs-lookup"><span data-stu-id="00339-143">This can be repaired by running the WFServicesReg.exe tool with the `/c` switch.</span></span>  
  
#### <a name="scriptmap-deleted-under-a-particular-web-site"></a><span data-ttu-id="00339-144">Mappage de scripts supprimé sous un site Web particulier</span><span class="sxs-lookup"><span data-stu-id="00339-144">Scriptmap deleted under a particular Web site</span></span>  
 <span data-ttu-id="00339-145">Sous [!INCLUDE[ws2003](../../../includes/ws2003-md.md)], un mappage de scripts .xoml ou .rules est supprimé par erreur d'un site Web particulier (celui par défaut, par exemple) et non du nœud Sites Web.</span><span class="sxs-lookup"><span data-stu-id="00339-145">On a [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] machine, .xoml or .rules is accidentally deleted from a particular Web site (for example, the Default Web Site) rather than from the Web Sites node.</span></span>  
  
 <span data-ttu-id="00339-146">Pour réparer des gestionnaires supprimés d’un site Web particulier, vous devez exécuter « r WFServicesReg.exe » pour supprimer des gestionnaires de tous les sites Web, puis exécuter « c WFServicesReg.exe » pour créer les gestionnaires appropriés pour tous les sites Web.</span><span class="sxs-lookup"><span data-stu-id="00339-146">To repair deleted handlers for a particular Web site, you should run "WFServicesReg.exe /r" to remove handlers from all Web sites, then run "WFServicesReg.exe /c" to create the appropriate handlers for all Web sites.</span></span>  
  
### <a name="configuring-handlers-after-switching-iis-mode"></a><span data-ttu-id="00339-147">Configuration de gestionnaires après activation du mode IIS</span><span class="sxs-lookup"><span data-stu-id="00339-147">Configuring handlers after switching IIS mode</span></span>  
 <span data-ttu-id="00339-148">Si les services IIS sont en mode de configuration partagé et si [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] est installé, la métabase IIS est configurée sous un emplacement partagé.</span><span class="sxs-lookup"><span data-stu-id="00339-148">When IIS is in shared configuration mode and [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] is installed, the IIS metabase is configured under a shared location.</span></span> <span data-ttu-id="00339-149">Si vous basculez IIS en mode de configuration non partagé, la métabase locale ne contiendra pas les gestionnaires requis.</span><span class="sxs-lookup"><span data-stu-id="00339-149">If you switch IIS to non-shared configuration mode, the local metabase will not contain the required handlers.</span></span> <span data-ttu-id="00339-150">Pour configurer la métabase locale correctement, vous pouvez importer la métabase partagée à local, soit exécuter « /c WFServicesReg.exe », qui configure la métabase locale.</span><span class="sxs-lookup"><span data-stu-id="00339-150">To configure the local metabase properly, you can either import the shared metabase to local, or run "WFServicesReg.exe /c", which configures the local metabase.</span></span>
