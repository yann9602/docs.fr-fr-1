---
title: "Comment :déterminer la version installée de WPF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: version [WPF], finding
ms.assetid: 99971cef-e218-4f9f-a4c1-350332741860
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 60f2dd65702a5dfcff4cbafa97e5a48080b8e5be
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-determine-the-installed-version-of-wpf"></a><span data-ttu-id="ca88d-102">Comment :déterminer la version installée de WPF</span><span class="sxs-lookup"><span data-stu-id="ca88d-102">How to: Determine the Installed Version of WPF</span></span>
<span data-ttu-id="ca88d-103">Le numéro de version pour la version actuellement installée de [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] se trouve dans le **Registre**.</span><span class="sxs-lookup"><span data-stu-id="ca88d-103">The version number for the current installed version of [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] is located in the **Registry**.</span></span>  
  
 <span data-ttu-id="ca88d-104">Pour trouver le numéro de version :</span><span class="sxs-lookup"><span data-stu-id="ca88d-104">To find the version number:</span></span>  
  
1.  <span data-ttu-id="ca88d-105">Dans le menu **Démarrer** , cliquez sur **Exécuter**.</span><span class="sxs-lookup"><span data-stu-id="ca88d-105">On the **Start** menu, click **Run**.</span></span>  
  
2.  <span data-ttu-id="ca88d-106">Dans **ouvrir**, type **regedit.exe**.</span><span class="sxs-lookup"><span data-stu-id="ca88d-106">In **Open**, type **regedit.exe**.</span></span>  
  
3.  <span data-ttu-id="ca88d-107">Ouvrez la clé suivante :</span><span class="sxs-lookup"><span data-stu-id="ca88d-107">Open the following key:</span></span>  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v3.0\Setup\Windows Presentation Foundation`  
  
 <span data-ttu-id="ca88d-108">Le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] numéro de version est stocké dans le **Version** valeur.</span><span class="sxs-lookup"><span data-stu-id="ca88d-108">The [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] version number is stored in the **Version** value.</span></span>
