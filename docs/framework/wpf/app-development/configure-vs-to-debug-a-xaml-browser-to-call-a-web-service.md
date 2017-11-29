---
title: "Comment : configurer Visual Studio pour déboguer une application de navigateur XAML et appeler un service Web"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging XBAPs that call a Web service [WPF]
- debugging security exceptions for XBAPs [WPF]
- security exception for XBAPs [WPF], debugging
- configuring Visual Studio to debug XAML browser applications [WPF]
- configuring Visual Studio to debug XBAPs [WPF]
ms.assetid: fd1db082-a7bb-4c4b-9331-6ad74a0682d0
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5db89cf6220f086d2d71b99f3e6440e584d6a5d7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-configure-visual-studio-to-debug-a-xaml-browser-application-to-call-a-web-service"></a><span data-ttu-id="18726-102">Comment : configurer Visual Studio pour déboguer une application de navigateur XAML et appeler un service Web</span><span class="sxs-lookup"><span data-stu-id="18726-102">How to: Configure Visual Studio to Debug a XAML Browser Application to Call a Web Service</span></span>
[!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)]<span data-ttu-id="18726-103">exécuter dans un sandbox de sécurité de confiance partielle est limité à l’ensemble de la zone Internet d’autorisations.</span><span class="sxs-lookup"><span data-stu-id="18726-103"> run within a partial-trust security sandbox that is restricted to the Internet zone set of permissions.</span></span> <span data-ttu-id="18726-104">Ce jeu d’autorisations restreint les appels de service Web uniquement les services Web qui sont trouvent dans le [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] site de l’application d’origine.</span><span class="sxs-lookup"><span data-stu-id="18726-104">This permission set restricts Web service calls to only Web services that are located at the [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] application's site of origin.</span></span> <span data-ttu-id="18726-105">Lorsqu’un [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] du débogage à partir de [!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)], bien qu’il n’est pas censé avoir le même site d’origine que le service Web qu’il référence.</span><span class="sxs-lookup"><span data-stu-id="18726-105">When an [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] is debugged from [!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)], though, it is not considered to have the same site of origin as the Web service it references.</span></span> <span data-ttu-id="18726-106">Cette causes des exceptions de sécurité à déclencher lorsque le [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] tente d’appeler le service Web.</span><span class="sxs-lookup"><span data-stu-id="18726-106">This causes security exceptions to be raised when the [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] attempts to call the Web service.</span></span> <span data-ttu-id="18726-107">Toutefois, un [!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)] [!INCLUDE[TLA#tla_wpfbrowserappproj](../../../../includes/tlasharptla-wpfbrowserappproj-md.md)] projet peut être configuré pour avoir le même site d’origine que le service Web qu’elle appelle lors du débogage.</span><span class="sxs-lookup"><span data-stu-id="18726-107">However, a [!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)] [!INCLUDE[TLA#tla_wpfbrowserappproj](../../../../includes/tlasharptla-wpfbrowserappproj-md.md)] project can be configured to simulate having the same site of origin as the Web service it calls while debugging.</span></span> <span data-ttu-id="18726-108">Cela permet la [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] en toute sécurité appeler le service Web sans provoquer des exceptions de sécurité.</span><span class="sxs-lookup"><span data-stu-id="18726-108">This allows the [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] to safely call the Web service without causing security exceptions.</span></span>  
  
## <a name="configuring-visual-studio"></a><span data-ttu-id="18726-109">Configuration de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="18726-109">Configuring Visual Studio</span></span>  
 <span data-ttu-id="18726-110">Pour configurer [!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)] pour déboguer un [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] qui appelle un service Web :</span><span class="sxs-lookup"><span data-stu-id="18726-110">To configure [!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)] to debug an [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] that calls a Web service:</span></span>  
  
1.  <span data-ttu-id="18726-111">Après avoir sélectionné un projet dans l’ **Explorateur de solutions**, dans le menu **Projet** , cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="18726-111">With a project selected in **Solution Explorer**, on the **Project** menu, click **Properties**.</span></span>  
  
2.  <span data-ttu-id="18726-112">Dans le **Concepteur de projets**, cliquez sur le **déboguer** onglet.</span><span class="sxs-lookup"><span data-stu-id="18726-112">In the **Project Designer**, click the **Debug** tab.</span></span>  
  
3.  <span data-ttu-id="18726-113">Dans le **Action de démarrage** section, sélectionnez **démarrer le programme externe** et entrez les informations suivantes :</span><span class="sxs-lookup"><span data-stu-id="18726-113">In the **Start Action** section, select **Start external program** and enter the following:</span></span>  
  
     `C:\WINDOWS\System32\PresentationHost.exe`  
  
4.  <span data-ttu-id="18726-114">Dans le **Options de démarrage** section, entrez le texte suivant dans le **arguments de ligne de commande** zone de texte :</span><span class="sxs-lookup"><span data-stu-id="18726-114">In the **Start Options** section, enter the following into the **Command line arguments** text box:</span></span>  
  
     <span data-ttu-id="18726-115">`-debug`  *nom de fichier*</span><span class="sxs-lookup"><span data-stu-id="18726-115">`-debug`  *filename*</span></span>  
  
     <span data-ttu-id="18726-116">Le *nom de fichier* la valeur pour le **-déboguer** paramètre est le nom de fichier .xbap ; par exemple :</span><span class="sxs-lookup"><span data-stu-id="18726-116">The *filename* value for the **-debug** parameter is the .xbap filename; for example:</span></span>  
  
     `-debug c:\example.xbap`  
  
> [!NOTE]
>  <span data-ttu-id="18726-117">Cette configuration est la valeur par défaut pour les solutions qui sont créés avec le [!INCLUDE[TLA2#tla_visualstu2005](../../../../includes/tla2sharptla-visualstu2005-md.md)] [!INCLUDE[TLA#tla_wpfbrowserappproj](../../../../includes/tlasharptla-wpfbrowserappproj-md.md)] modèle de projet.</span><span class="sxs-lookup"><span data-stu-id="18726-117">This is the default configuration for solutions that are created with the [!INCLUDE[TLA2#tla_visualstu2005](../../../../includes/tla2sharptla-visualstu2005-md.md)] [!INCLUDE[TLA#tla_wpfbrowserappproj](../../../../includes/tlasharptla-wpfbrowserappproj-md.md)] project template.</span></span>  
  
1.  <span data-ttu-id="18726-118">Après avoir sélectionné un projet dans l’ **Explorateur de solutions**, dans le menu **Projet** , cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="18726-118">With a project selected in **Solution Explorer**, on the **Project** menu, click **Properties**.</span></span>  
  
2.  <span data-ttu-id="18726-119">Dans le **Concepteur de projets**, cliquez sur le **déboguer** onglet.</span><span class="sxs-lookup"><span data-stu-id="18726-119">In the **Project Designer**, click the **Debug** tab.</span></span>  
  
3.  <span data-ttu-id="18726-120">Dans le **Options de démarrage** section, ajoutez le paramètre de ligne de commande suivant à la **arguments de ligne de commande** zone de texte :</span><span class="sxs-lookup"><span data-stu-id="18726-120">In the **Start Options** section, add the following command-line parameter to the **Command line arguments** text box:</span></span>  
  
     <span data-ttu-id="18726-121">`-debugSecurityZoneURL`  *URL*</span><span class="sxs-lookup"><span data-stu-id="18726-121">`-debugSecurityZoneURL`  *URL*</span></span>  
  
     <span data-ttu-id="18726-122">Le *URL* la valeur pour le **- debugSecurityZoneURL** paramètre est le [!INCLUDE[TLA#tla_url](../../../../includes/tlasharptla-url-md.md)] pour l’emplacement que vous souhaitez simuler comme site d’origine de votre application.</span><span class="sxs-lookup"><span data-stu-id="18726-122">The *URL* value for the **-debugSecurityZoneURL** parameter is the [!INCLUDE[TLA#tla_url](../../../../includes/tlasharptla-url-md.md)] for the location that you want to simulate as being the site of origin of your application.</span></span>  
  
 <span data-ttu-id="18726-123">Par exemple, considérez un [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] qui utilise un service Web par le code suivant [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="18726-123">As an example, consider a [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] that uses a Web service with the following [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)]:</span></span>  
  
 `http://services.msdn.microsoft.com/ContentServices/ContentService.asmx`  
  
 <span data-ttu-id="18726-124">Le site d’origine [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)] pour ce site Web service est :</span><span class="sxs-lookup"><span data-stu-id="18726-124">The site of origin [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)] for this Web service is:</span></span>  
  
 `http://services.msdn.microsoft.com`  
  
 <span data-ttu-id="18726-125">Par conséquent, le texte complet **- debugSecurityZoneURL** paramètre de ligne de commande et la valeur est :</span><span class="sxs-lookup"><span data-stu-id="18726-125">Consequently, the complete **-debugSecurityZoneURL** command-line parameter and value is:</span></span>  
  
 `-debugSecurityZoneURL http://services.msdn.microsoft.com`  
  
## <a name="see-also"></a><span data-ttu-id="18726-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="18726-126">See Also</span></span>  
 [<span data-ttu-id="18726-127">Hôte WPF (PresentationHost.exe)</span><span class="sxs-lookup"><span data-stu-id="18726-127">WPF Host (PresentationHost.exe)</span></span>](../../../../docs/framework/wpf/app-development/wpf-host-presentationhost-exe.md)
