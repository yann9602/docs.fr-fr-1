---
title: Optimisation des performances des applications WPF
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application rendering [WPF], performance
- application optimization [WPF]
- applications [WPF], optimizing
- WPF application [WPF], optimizing
ms.assetid: ac8c6aa3-3c68-4a24-9827-3b6c829c1ebf
caps.latest.revision: "45"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f9ea154bc7c7a20bcdd57e1f271a4010f50646de
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="optimizing-wpf-application-performance"></a><span data-ttu-id="0306d-102">Optimisation des performances des applications WPF</span><span class="sxs-lookup"><span data-stu-id="0306d-102">Optimizing WPF Application Performance</span></span>
<span data-ttu-id="0306d-103">Cette section s’adresse en tant que référence pour [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] les développeurs d’applications qui recherchent des moyens d’améliorer les performances de leurs applications.</span><span class="sxs-lookup"><span data-stu-id="0306d-103">This section is intended as a reference for [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] application developers who are looking for ways to improve the performance of their applications.</span></span> <span data-ttu-id="0306d-104">Si vous êtes un développeur qui est une nouveauté dans le [!INCLUDE[TLA#tla_avalonwinfx](../../../../includes/tlasharptla-avalonwinfx-md.md)] et [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], vous devez tout d’abord vous familiariser avec ces deux plateformes.</span><span class="sxs-lookup"><span data-stu-id="0306d-104">If you are a developer who is new to the [!INCLUDE[TLA#tla_avalonwinfx](../../../../includes/tlasharptla-avalonwinfx-md.md)] and [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], you should first familiarize yourself with both platforms.</span></span> <span data-ttu-id="0306d-105">Cette section suppose la connaissance des deux et est écrit pour les programmeurs qui savent déjà créer des applications en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="0306d-105">This section assumes working knowledge of both, and is written for programmers who already know enough to get their applications up and running.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0306d-106">Les données de performances fournies dans cette section sont basées sur [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications s’exécutant sur un PC à 2,8 GHz avec 512 RAM et un ATI Radeon 9700 carte graphique.</span><span class="sxs-lookup"><span data-stu-id="0306d-106">The performance data provided in this section are based on [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications running on a 2.8 GHz PC with 512 RAM and an ATI Radeon 9700 graphics card.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0306d-107">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="0306d-107">In This Section</span></span>  
 [<span data-ttu-id="0306d-108">Planification des performances des applications</span><span class="sxs-lookup"><span data-stu-id="0306d-108">Planning for Application Performance</span></span>](../../../../docs/framework/wpf/advanced/planning-for-application-performance.md)  
  
 [<span data-ttu-id="0306d-109">Tirer parti du matériel</span><span class="sxs-lookup"><span data-stu-id="0306d-109">Taking Advantage of Hardware</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-taking-advantage-of-hardware.md)  
  
 [<span data-ttu-id="0306d-110">Disposition et conception</span><span class="sxs-lookup"><span data-stu-id="0306d-110">Layout and Design</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-layout-and-design.md)  
  
 [<span data-ttu-id="0306d-111">Graphiques 2D et acquisition d'images</span><span class="sxs-lookup"><span data-stu-id="0306d-111">2D Graphics and Imaging</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)  
  
 [<span data-ttu-id="0306d-112">Comportement de l’objet</span><span class="sxs-lookup"><span data-stu-id="0306d-112">Object Behavior</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-object-behavior.md)  
  
 [<span data-ttu-id="0306d-113">Ressources d'application</span><span class="sxs-lookup"><span data-stu-id="0306d-113">Application Resources</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-application-resources.md)  
  
 [<span data-ttu-id="0306d-114">Texte</span><span class="sxs-lookup"><span data-stu-id="0306d-114">Text</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-text.md)  
  
 [<span data-ttu-id="0306d-115">Liaison de données</span><span class="sxs-lookup"><span data-stu-id="0306d-115">Data Binding</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)  
  
 [<span data-ttu-id="0306d-116">Contrôles</span><span class="sxs-lookup"><span data-stu-id="0306d-116">Controls</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-controls.md)  
  
 [<span data-ttu-id="0306d-117">Autres recommandations relatives aux performances</span><span class="sxs-lookup"><span data-stu-id="0306d-117">Other Performance Recommendations</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-other-recommendations.md)  
  
 [<span data-ttu-id="0306d-118">Temps de démarrage d’une application</span><span class="sxs-lookup"><span data-stu-id="0306d-118">Application Startup Time</span></span>](../../../../docs/framework/wpf/advanced/application-startup-time.md)  
  
## <a name="see-also"></a><span data-ttu-id="0306d-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0306d-119">See Also</span></span>  
 <xref:System.Windows.Media.RenderOptions>  
 <xref:System.Windows.Media.RenderCapability>  
 [<span data-ttu-id="0306d-120">Couches de rendu graphiques</span><span class="sxs-lookup"><span data-stu-id="0306d-120">Graphics Rendering Tiers</span></span>](../../../../docs/framework/wpf/advanced/graphics-rendering-tiers.md)  
 [<span data-ttu-id="0306d-121">Vue d’ensemble du rendu graphique de WPF</span><span class="sxs-lookup"><span data-stu-id="0306d-121">WPF Graphics Rendering Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)  
 [<span data-ttu-id="0306d-122">Disposition</span><span class="sxs-lookup"><span data-stu-id="0306d-122">Layout</span></span>](../../../../docs/framework/wpf/advanced/layout.md)  
 [<span data-ttu-id="0306d-123">Arborescences dans WPF</span><span class="sxs-lookup"><span data-stu-id="0306d-123">Trees in WPF</span></span>](../../../../docs/framework/wpf/advanced/trees-in-wpf.md)  
 [<span data-ttu-id="0306d-124">Vue d’ensemble des objets de dessin</span><span class="sxs-lookup"><span data-stu-id="0306d-124">Drawing Objects Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)  
 [<span data-ttu-id="0306d-125">Utilisation d’objets DrawingVisual</span><span class="sxs-lookup"><span data-stu-id="0306d-125">Using DrawingVisual Objects</span></span>](../../../../docs/framework/wpf/graphics-multimedia/using-drawingvisual-objects.md)  
 [<span data-ttu-id="0306d-126">Vue d’ensemble des propriétés de dépendance</span><span class="sxs-lookup"><span data-stu-id="0306d-126">Dependency Properties Overview</span></span>](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
 [<span data-ttu-id="0306d-127">Vue d’ensemble des objets Freezable</span><span class="sxs-lookup"><span data-stu-id="0306d-127">Freezable Objects Overview</span></span>](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)  
 [<span data-ttu-id="0306d-128">Ressources XAML</span><span class="sxs-lookup"><span data-stu-id="0306d-128">XAML Resources</span></span>](../../../../docs/framework/wpf/advanced/xaml-resources.md)  
 [<span data-ttu-id="0306d-129">Documents dans WPF</span><span class="sxs-lookup"><span data-stu-id="0306d-129">Documents in WPF</span></span>](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [<span data-ttu-id="0306d-130">Dessin du texte mis en forme</span><span class="sxs-lookup"><span data-stu-id="0306d-130">Drawing Formatted Text</span></span>](../../../../docs/framework/wpf/advanced/drawing-formatted-text.md)  
 [<span data-ttu-id="0306d-131">Typographie dans WPF</span><span class="sxs-lookup"><span data-stu-id="0306d-131">Typography in WPF</span></span>](../../../../docs/framework/wpf/advanced/typography-in-wpf.md)  
 [<span data-ttu-id="0306d-132">Vue d’ensemble de la liaison de données</span><span class="sxs-lookup"><span data-stu-id="0306d-132">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="0306d-133">Vue d’ensemble de la navigation</span><span class="sxs-lookup"><span data-stu-id="0306d-133">Navigation Overview</span></span>](../../../../docs/framework/wpf/app-development/navigation-overview.md)  
 [<span data-ttu-id="0306d-134">Conseils et astuces sur les animations</span><span class="sxs-lookup"><span data-stu-id="0306d-134">Animation Tips and Tricks</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-tips-and-tricks.md)  
 [<span data-ttu-id="0306d-135">Procédure pas à pas : mise en cache de données d’application dans une application WPF</span><span class="sxs-lookup"><span data-stu-id="0306d-135">Walkthrough: Caching Application Data in a WPF Application</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-caching-application-data-in-a-wpf-application.md)
