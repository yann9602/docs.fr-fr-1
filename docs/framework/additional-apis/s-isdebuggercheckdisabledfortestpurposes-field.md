---
title: s_isDebuggerCheckDisabledForTestPurposes champ
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
api_name: System.Windows.Diagnostics.VisualDiagnostics.s_isDebuggerCheckDisabledForTestPurposes
api_location: PresentationCore.dll
api_type: Assembly
ms.assetid: 9033a513-c255-4f31-b6d7-09b8d8c50e2d
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
robots: noindex,nofollow
ms.workload: dotnet
ms.openlocfilehash: 67da38d958d153ebe526f298785b39afb7be6513
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="sisdebuggercheckdisabledfortestpurposes-field"></a><span data-ttu-id="fe7fe-102">s_isDebuggerCheckDisabledForTestPurposes champ</span><span class="sxs-lookup"><span data-stu-id="fe7fe-102">s_isDebuggerCheckDisabledForTestPurposes Field</span></span>

<span data-ttu-id="fe7fe-103">Ce champ privé dans la `System.Windows.Diagnostics.VisualDiagnostics` classe est utilisée par Visual Studio pour déterminer si une vérification interne pour le débogueur actif sera effectuée.</span><span class="sxs-lookup"><span data-stu-id="fe7fe-103">This private field in the `System.Windows.Diagnostics.VisualDiagnostics` class is used by Visual Studio to determine whether an internal check for an active debugger will be performed.</span></span>

## <a name="syntax"></a><span data-ttu-id="fe7fe-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fe7fe-104">Syntax</span></span>
  
```csharp  
private static bool s_isDebuggerCheckDisabledForTestPurposes
```
  
> [!WARNING]
>  <span data-ttu-id="fe7fe-105">L’API dans la `System.Windows.Diagnostics.VisualDiagnostics` classe sont disponibles uniquement quand une application s’exécute sous un débogueur.</span><span class="sxs-lookup"><span data-stu-id="fe7fe-105">API's in the `System.Windows.Diagnostics.VisualDiagnostics` class are only available when an application is running under a debugger.</span></span> <span data-ttu-id="fe7fe-106">Définissez `s_isDebuggerCheckDisabledForTestPurposes` à `true` pour accéder aux API en dehors d’un débogueur.</span><span class="sxs-lookup"><span data-stu-id="fe7fe-106">Set `s_isDebuggerCheckDisabledForTestPurposes` to `true` to access the APIs outside of a debugger.</span></span>  
>   
>  <span data-ttu-id="fe7fe-107">Microsoft ne prend pas en charge l’utilisation de ce champ dans une application de production en toutes circonstances.</span><span class="sxs-lookup"><span data-stu-id="fe7fe-107">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>  

## <a name="requirements"></a><span data-ttu-id="fe7fe-108">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="fe7fe-108">Requirements</span></span>

<span data-ttu-id="fe7fe-109">**Namespace :**<xref:System.Windows.Diagnostics></span><span class="sxs-lookup"><span data-stu-id="fe7fe-109">**Namespace:** <xref:System.Windows.Diagnostics></span></span>

<span data-ttu-id="fe7fe-110">**Assembly :** PresentationCore (dans PresentationCore.dll)</span><span class="sxs-lookup"><span data-stu-id="fe7fe-110">**Assembly:** PresentationCore (in PresentationCore.dll)</span></span>

<span data-ttu-id="fe7fe-111">**Versions du .NET framework :** disponible depuis 4.6.</span><span class="sxs-lookup"><span data-stu-id="fe7fe-111">**.NET Framework versions:** Available since 4.6.</span></span>
