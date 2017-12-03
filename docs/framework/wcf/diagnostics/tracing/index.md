---
title: "Traçage"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2649eae2-dbf8-421c-9cfb-cfa9e01de87f
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3d57517daaf78e737ea4417d5d46cf33400ff97a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="tracing"></a><span data-ttu-id="17d48-102">Traçage</span><span class="sxs-lookup"><span data-stu-id="17d48-102">Tracing</span></span>
[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]<span data-ttu-id="17d48-103"> fournit des données de diagnostic et d'instrumentation d'application à des fins de contrôle et d'analyse des erreurs.</span><span class="sxs-lookup"><span data-stu-id="17d48-103"> provides application instrumentation and diagnostic data for fault monitoring and analysis.</span></span> <span data-ttu-id="17d48-104">Vous pouvez utiliser le suivi au lieu d'un débogueur pour comprendre le comportement d'une application ou la raison de sa défaillance.</span><span class="sxs-lookup"><span data-stu-id="17d48-104">You can use tracing instead of a debugger to understand how an application is behaving, or why it faults.</span></span> <span data-ttu-id="17d48-105">Vous pouvez également mettre en corrélation les erreurs et le traitement sur l'ensemble des composants afin de fournir une expérience de bout en bout.</span><span class="sxs-lookup"><span data-stu-id="17d48-105">You can also correlate faults and processing across components to provide an end-to-end experience.</span></span>  
  
 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]<span data-ttu-id="17d48-106"> génère les données suivantes pour le suivi de diagnostic :</span><span class="sxs-lookup"><span data-stu-id="17d48-106"> outputs the following data for diagnostic tracing:</span></span>  
  
-   <span data-ttu-id="17d48-107">Suivis pour les jalons de processus sur l'ensemble des composants des applications, tels que les appels d'opération, exceptions de code, avertissements et autres événements de traitement significatifs.</span><span class="sxs-lookup"><span data-stu-id="17d48-107">Traces for process milestones across all components of the applications, such as operation calls, code exceptions, warnings and other significant processing events."</span></span>  
  
-   <span data-ttu-id="17d48-108">Événements d’erreur Windows en cas de dysfonctionnement de la fonctionnalité de suivi.</span><span class="sxs-lookup"><span data-stu-id="17d48-108">Windows error events when the tracing feature malfunctions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="17d48-109">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="17d48-109">In This Section</span></span>  
 [<span data-ttu-id="17d48-110">Configuration du traçage</span><span class="sxs-lookup"><span data-stu-id="17d48-110">Configuring Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)  
  
 <span data-ttu-id="17d48-111">Cette rubrique décrit comment configurer le suivi à différents niveaux en fonction de vos besoins spécifiques.</span><span class="sxs-lookup"><span data-stu-id="17d48-111">This topic describes how you can configure tracing at different levels to suit your specific need.</span></span>  
  
 [<span data-ttu-id="17d48-112">Suivi de bout en bout</span><span class="sxs-lookup"><span data-stu-id="17d48-112">End-to-End Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing.md)  
  
 <span data-ttu-id="17d48-113">Cette section décrit comment utiliser le suivi et la propagation d'activité pour la corrélation de bout en bout à des fins de débogage.</span><span class="sxs-lookup"><span data-stu-id="17d48-113">This section describes how you can use Activity Tracing and Propagation for end-to-end correlation to assist debugging.</span></span>  
  
 [<span data-ttu-id="17d48-114">Utilisation du suivi pour dépanner votre Application</span><span class="sxs-lookup"><span data-stu-id="17d48-114">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
  
 <span data-ttu-id="17d48-115">Cette section décrit comment utiliser le suivi pour déboguer votre application.</span><span class="sxs-lookup"><span data-stu-id="17d48-115">This section describes how you can use tracing to debug your application.</span></span>  
  
 [<span data-ttu-id="17d48-116">Problèmes de sécurité et des conseils utiles pour le suivi</span><span class="sxs-lookup"><span data-stu-id="17d48-116">Security Concerns and Useful Tips for Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/security-concerns-and-useful-tips-for-tracing.md)  
  
 <span data-ttu-id="17d48-117">Cette rubrique décrit comment empêcher l'exposition des informations sensibles et fournit également des conseils utiles en cas d'utilisation de WebHost.</span><span class="sxs-lookup"><span data-stu-id="17d48-117">This topic describes how you can protect sensitive information from being exposed, as well as useful tips when using WebHost.</span></span>  
  
 [<span data-ttu-id="17d48-118">Référence des suivis</span><span class="sxs-lookup"><span data-stu-id="17d48-118">Traces Reference</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/traces-reference.md)  
  
 <span data-ttu-id="17d48-119">Cette rubrique répertorie l'ensemble des suivis générés par [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="17d48-119">This topic lists all the traces generated by [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17d48-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="17d48-120">See Also</span></span>  
 [<span data-ttu-id="17d48-121">Outil Service Trace Viewer (SvcTraceViewer.exe)</span><span class="sxs-lookup"><span data-stu-id="17d48-121">Service Trace Viewer Tool (SvcTraceViewer.exe)</span></span>](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)
