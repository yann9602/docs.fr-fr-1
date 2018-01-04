---
title: "Hôte WPF (PresentationHost.exe)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WPF Host application [WPF]
- PresentationHost.exe
ms.assetid: 3215bfa1-722c-4ac8-a7c5-bdd02d30afbd
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1c5a9df438353701932a3e732d6df28b08402ee8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="wpf-host-presentationhostexe"></a><span data-ttu-id="846a3-102">Hôte WPF (PresentationHost.exe)</span><span class="sxs-lookup"><span data-stu-id="846a3-102">WPF Host (PresentationHost.exe)</span></span>
<span data-ttu-id="846a3-103">L’hôte [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] (PresentationHost.exe) est l’application qui permet aux applications [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] d’être hébergées par des navigateurs compatibles (notamment [!INCLUDE[TLA#tla_ie6](../../../../includes/tlasharptla-ie6-md.md)] et les versions ultérieures).</span><span class="sxs-lookup"><span data-stu-id="846a3-103">[!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] Host (PresentationHost.exe) is the application that enables [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] applications to be hosted in compatible browsers (including [!INCLUDE[TLA#tla_ie6](../../../../includes/tlasharptla-ie6-md.md)] and later).</span></span> <span data-ttu-id="846a3-104">Par défaut, l’hôte [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] est inscrit en tant qu’interpréteur de commandes et gestionnaire [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] pour le contenu [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] hébergé par les navigateurs, ce qui inclut :</span><span class="sxs-lookup"><span data-stu-id="846a3-104">By default, [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] Host is registered as the shell and [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] handler for browser-hosted [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] content, which includes:</span></span>  
  
-   <span data-ttu-id="846a3-105">les fichiers [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] (.xaml) libre (non compilés) ;</span><span class="sxs-lookup"><span data-stu-id="846a3-105">Loose (uncompiled) [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] files (.xaml).</span></span>  
  
-   <span data-ttu-id="846a3-106">l’application [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] (.xbap).</span><span class="sxs-lookup"><span data-stu-id="846a3-106">[!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] (.xbap).</span></span>  
  
 <span data-ttu-id="846a3-107">Pour les fichiers de ce type, l’hôte [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] :</span><span class="sxs-lookup"><span data-stu-id="846a3-107">For files of these types, [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] Host:</span></span>  
  
-   <span data-ttu-id="846a3-108">lance le gestionnaire [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] inscrit pour héberger le contenu [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] ;</span><span class="sxs-lookup"><span data-stu-id="846a3-108">Launches the registered [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] handler to host the [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] content.</span></span>  
  
-   <span data-ttu-id="846a3-109">charge les versions appropriées des assemblys [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] et [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] ;</span><span class="sxs-lookup"><span data-stu-id="846a3-109">Loads the right versions of the required [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] and [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] assemblies.</span></span>  
  
-   <span data-ttu-id="846a3-110">vérifie la mise en place des niveaux d’autorisation appropriés pour la zone de déploiement.</span><span class="sxs-lookup"><span data-stu-id="846a3-110">Ensures the appropriate permission levels for the zone of deployment are in place.</span></span>  
  
 <span data-ttu-id="846a3-111">Cette rubrique décrit les paramètres de ligne de commande qui peuvent être utilisés avec PresentationHost.exe.</span><span class="sxs-lookup"><span data-stu-id="846a3-111">This topic describes the command line parameters that can be used with PresentationHost.exe.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="846a3-112">Utilisation</span><span class="sxs-lookup"><span data-stu-id="846a3-112">Usage</span></span>  
 `PresentationHost.exe [parameters] uri|filename`  
  
## <a name="parameters"></a><span data-ttu-id="846a3-113">Paramètres</span><span class="sxs-lookup"><span data-stu-id="846a3-113">Parameters</span></span>  
  
|<span data-ttu-id="846a3-114">Paramètre</span><span class="sxs-lookup"><span data-stu-id="846a3-114">Parameter</span></span>|<span data-ttu-id="846a3-115">Description</span><span class="sxs-lookup"><span data-stu-id="846a3-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="846a3-116">filename</span><span class="sxs-lookup"><span data-stu-id="846a3-116">filename</span></span>|<span data-ttu-id="846a3-117">Chemin du fichier à activer.</span><span class="sxs-lookup"><span data-stu-id="846a3-117">The path of the file to be activated.</span></span> <span data-ttu-id="846a3-118">Il peut également s’agir d’un [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span><span class="sxs-lookup"><span data-stu-id="846a3-118">Can also be a [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)].</span></span>|  
|<span data-ttu-id="846a3-119">-debug</span><span class="sxs-lookup"><span data-stu-id="846a3-119">-debug</span></span>|<span data-ttu-id="846a3-120">Au moment d’activer une application, n’effectue pas sa validation ou son exécution à partir du magasin.</span><span class="sxs-lookup"><span data-stu-id="846a3-120">When activating an application, does not commit it to or run it from the store.</span></span> <span data-ttu-id="846a3-121">Fonctionne uniquement quand un fichier local est activé.</span><span class="sxs-lookup"><span data-stu-id="846a3-121">This only works when a local file is activated.</span></span>|  
|<span data-ttu-id="846a3-122">-debugSecurityZoneURL \<url></span><span class="sxs-lookup"><span data-stu-id="846a3-122">-debugSecurityZoneURL \<url></span></span>|<span data-ttu-id="846a3-123">Utilisé avec une valeur [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)] pour indiquer à PresentationHost.exe qu’une application doit être déboguée comme si elle était déployée à partir de la valeur [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)] spécifiée.</span><span class="sxs-lookup"><span data-stu-id="846a3-123">Used with a [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)] value to indicate to PresentationHost.exe that an application should be debugged as if it were deployed from the specified [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)].</span></span> <span data-ttu-id="846a3-124">Cela permet de déterminer à la fois la zone de déploiement et le site d’origine.</span><span class="sxs-lookup"><span data-stu-id="846a3-124">This determines both the deployment zone and the site of origin.</span></span>|  
|<span data-ttu-id="846a3-125">-embedding</span><span class="sxs-lookup"><span data-stu-id="846a3-125">-embedding</span></span>|<span data-ttu-id="846a3-126">Imposé par OLE.</span><span class="sxs-lookup"><span data-stu-id="846a3-126">Required by OLE.</span></span> <span data-ttu-id="846a3-127">Si le paramètre `-event` ou `-debug` est spécifié, il n’est pas nécessaire de spécifier le paramètre `-embedding`, car celui-ci est défini de façon interne.</span><span class="sxs-lookup"><span data-stu-id="846a3-127">If the `-event` or `-debug` parameter are specified, it is not necessary to specify the `-embedding` parameter, since that parameter is set internally.</span></span>|  
|<span data-ttu-id="846a3-128">-event \<eventname></span><span class="sxs-lookup"><span data-stu-id="846a3-128">-event \<eventname></span></span>|<span data-ttu-id="846a3-129">Ouvrez l’événement ayant ce nom, puis signalez-le quand PresentationHost.exe est initialisé et prêt à héberger le contenu [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].</span><span class="sxs-lookup"><span data-stu-id="846a3-129">Open the event with this name and signal it when PresentationHost.exe is initialized and ready to host [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] content.</span></span> <span data-ttu-id="846a3-130">PresentationHost.exe se termine si une erreur se produit à l’ouverture de l’événement, par exemple s’il n’a pas encore été créé.</span><span class="sxs-lookup"><span data-stu-id="846a3-130">PresentationHost.exe will terminate if there was an error opening the event, such as if it has not already been created.</span></span>|  
|<span data-ttu-id="846a3-131">-launchApplication \<url></span><span class="sxs-lookup"><span data-stu-id="846a3-131">-launchApplication \<url></span></span>|<span data-ttu-id="846a3-132">Lance une application [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] autonome à partir de l’URL spécifiée.</span><span class="sxs-lookup"><span data-stu-id="846a3-132">Launches a standalone [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] application from the specified URL.</span></span> <span data-ttu-id="846a3-133">Les stratégies de sécurité [!INCLUDE[TLA2#tla_iegeneric](../../../../includes/tla2sharptla-iegeneric-md.md)] et WinINet relatives aux applications .NET sont appliquées.</span><span class="sxs-lookup"><span data-stu-id="846a3-133">[!INCLUDE[TLA2#tla_iegeneric](../../../../includes/tla2sharptla-iegeneric-md.md)] and WinINet security policy concerning .NET applications are applied.</span></span>|  
  
## <a name="scenarios"></a><span data-ttu-id="846a3-134">Scénarios</span><span class="sxs-lookup"><span data-stu-id="846a3-134">Scenarios</span></span>  
  
### <a name="shell-handler"></a><span data-ttu-id="846a3-135">Gestionnaire d’interpréteur de commandes</span><span class="sxs-lookup"><span data-stu-id="846a3-135">Shell Handler</span></span>  
 `PresentationHost.exe example.xbap`  
  
### <a name="mime-handler"></a><span data-ttu-id="846a3-136">Gestionnaire MIME</span><span class="sxs-lookup"><span data-stu-id="846a3-136">MIME Handler</span></span>  
 `PresentationHost.exe -embedding example.xbap`  
  
### <a name="visual-studio-debugging"></a><span data-ttu-id="846a3-137">Débogage Visual Studio</span><span class="sxs-lookup"><span data-stu-id="846a3-137">Visual Studio Debugging</span></span>  
 `PresentationHost.exe -debug example.xbap`  
  
### <a name="visual-studio-debugging-in-zone"></a><span data-ttu-id="846a3-138">Débogage Visual Studio dans la zone</span><span class="sxs-lookup"><span data-stu-id="846a3-138">Visual Studio Debugging In Zone</span></span>  
 `PresentationHost.exe -debug -debugSecurityZoneURL http://www.example.com c:\folderpath\example.xbap`  
  
## <a name="see-also"></a><span data-ttu-id="846a3-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="846a3-139">See Also</span></span>  
 [<span data-ttu-id="846a3-140">Sécurité</span><span class="sxs-lookup"><span data-stu-id="846a3-140">Security</span></span>](../../../../docs/framework/wpf/security-wpf.md)
