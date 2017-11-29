---
title: MEF pour .NET pour les applications du Windows Store
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7667770e-d163-4ad6-a303-085cf73db2f2
caps.latest.revision: "3"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7f427656f9b385214db5b3bd26c4addb1122b35a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="mef-for-net-for-windows-store-apps"></a><span data-ttu-id="0065b-102">MEF pour .NET pour les applications du Windows Store</span><span class="sxs-lookup"><span data-stu-id="0065b-102">MEF for .NET for Windows Store Apps</span></span>
<span data-ttu-id="0065b-103"><xref:System.Composition?displayProperty=nameWithType>et ses espaces de noms enfants contiennent des types pour le développement extensibles [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] applications avec Managed Extensibility Framework (MEF).</span><span class="sxs-lookup"><span data-stu-id="0065b-103"><xref:System.Composition?displayProperty=nameWithType> and its child namespaces contain types for developing extensible [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] apps with Managed Extensibility Framework (MEF).</span></span> <span data-ttu-id="0065b-104">Ces espaces de noms font partie de la [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] sous-ensemble pour la [!INCLUDE[win8](../../../includes/win8-md.md)] système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="0065b-104">These namespaces are part of the [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] subset for the [!INCLUDE[win8](../../../includes/win8-md.md)] operating system.</span></span>  
  
 <span data-ttu-id="0065b-105">Ces espaces de noms ne font pas partie de la principale bibliothèque de classes distribuée avec .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0065b-105">These namespaces are not part of the core class library distributed with the .NET Framework.</span></span> <span data-ttu-id="0065b-106">Pour installer ces espaces de noms, ouvrez votre projet dans [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], choisissez **gérer les Packages NuGet** à partir de la **projet** menu, puis recherchez en ligne le package Microsoft.Composition.</span><span class="sxs-lookup"><span data-stu-id="0065b-106">To install these namespaces, open your project in [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], choose **Manage NuGet Packages** from the **Project** menu, and search online for the Microsoft.Composition package.</span></span>  
  
-   <span data-ttu-id="0065b-107"><xref:System.Composition?displayProperty=nameWithType>Fournit des classes qui constituent le cœur MEF pour [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] applications.</span><span class="sxs-lookup"><span data-stu-id="0065b-107"><xref:System.Composition?displayProperty=nameWithType> provides classes that constitute the core MEF for [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] apps.</span></span>  
  
-   <span data-ttu-id="0065b-108"><xref:System.Composition.Convention?displayProperty=nameWithType>Fournit des types qui prennent en charge de l’aide de MEF avec un modèle de configuration basée sur une convention.</span><span class="sxs-lookup"><span data-stu-id="0065b-108"><xref:System.Composition.Convention?displayProperty=nameWithType> provides types that support using MEF with a convention-based configuration model.</span></span>  
  
-   <span data-ttu-id="0065b-109"><xref:System.Composition.Hosting?displayProperty=nameWithType>Fournit des types MEF qui sont utiles pour les développeurs d’applications de l’hôte.</span><span class="sxs-lookup"><span data-stu-id="0065b-109"><xref:System.Composition.Hosting?displayProperty=nameWithType> provides MEF types that are useful to developers of host applications.</span></span>  
  
-   <span data-ttu-id="0065b-110"><xref:System.Composition.Hosting.Core?displayProperty=nameWithType>Fournit des types MEF utilisées en interne par le moteur de composition.</span><span class="sxs-lookup"><span data-stu-id="0065b-110"><xref:System.Composition.Hosting.Core?displayProperty=nameWithType> provides MEF types used internally by the composition engine.</span></span>  
  
 <span data-ttu-id="0065b-111">Pour plus d’informations sur [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] et une liste des espaces de noms et les types qu’il contient, consultez [vue d’ensemble des applications .NET pour le Windows Store](http://go.microsoft.com/fwlink/p/?LinkID=238312) dans le centre de développement Windows.</span><span class="sxs-lookup"><span data-stu-id="0065b-111">For more information about [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] and a list of namespaces and types that it contains, see [.NET for Windows Store apps overview](http://go.microsoft.com/fwlink/p/?LinkID=238312) in the Windows Dev Center.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0065b-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0065b-112">See Also</span></span>  
 [<span data-ttu-id="0065b-113">Vue d’ensemble des applications .NET pour le Windows Store</span><span class="sxs-lookup"><span data-stu-id="0065b-113">.NET for Windows Store apps overview</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=238312)  
 [<span data-ttu-id="0065b-114">.NET pour les applications du Windows Store : API prises en charge</span><span class="sxs-lookup"><span data-stu-id="0065b-114">.NET for Windows Store apps – supported APIs</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=247912)  
 [<span data-ttu-id="0065b-115">Managed Extensibility Framework (MEF)</span><span class="sxs-lookup"><span data-stu-id="0065b-115">Managed Extensibility Framework (MEF)</span></span>](../../../docs/framework/mef/index.md)
