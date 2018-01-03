---
title: Champ de ServicePointManager.s_ServicePointTable
ms.date: 05/01/2017
ms.prod: .net-framework
ms.technology: 
ms.topic: reference
topic_type: apiref
api_name: System.Net.ServicePointManager.s_ServicePointTable
api_location: System.dll
api_type: Assembly
ms.assetid: 24459679-291c-401a-9def-e42b29466fcf
author: guardrex
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8dfdbab78d8efab13487575218820f8b0455248d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="servicepointmanagersservicepointtable-field"></a><span data-ttu-id="1b746-102">ServicePointManager.s\_ServicePointTable champ</span><span class="sxs-lookup"><span data-stu-id="1b746-102">ServicePointManager.s\_ServicePointTable Field</span></span>

<span data-ttu-id="1b746-103">`ServicePointManager.s_ServicePointTable`est un <xref:System.Collections.Hashtable> qui contient la liste des connexions HTTP actives (<xref:System.Net.ServicePoint>s) dans le <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="1b746-103">`ServicePointManager.s_ServicePointTable` is a <xref:System.Collections.Hashtable> that contains the list of active HTTP connections (<xref:System.Net.ServicePoint>s) in the <xref:System.AppDomain>.</span></span>

## <a name="syntax"></a><span data-ttu-id="1b746-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1b746-104">Syntax</span></span>
  
```csharp  
private static Hashtable s_ServicePointTable
```

> [!WARNING]
> <span data-ttu-id="1b746-105">Le `ServicePointManager.s_ServicePointTable` champ est privée et ne revient pas à être utilisée directement dans votre code.</span><span class="sxs-lookup"><span data-stu-id="1b746-105">The `ServicePointManager.s_ServicePointTable` field is private and not meant to be used directly in your code.</span></span>
> 
> <span data-ttu-id="1b746-106">Microsoft ne prend pas en charge l’utilisation de ce champ dans une application de production en toutes circonstances.</span><span class="sxs-lookup"><span data-stu-id="1b746-106">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="1b746-107">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="1b746-107">Requirements</span></span>

<span data-ttu-id="1b746-108">**Namespace :**<xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="1b746-108">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="1b746-109">**Assembly :** système (dans System.dll)</span><span class="sxs-lookup"><span data-stu-id="1b746-109">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="1b746-110">**Versions du .NET framework :** disponible depuis la version 2.0.</span><span class="sxs-lookup"><span data-stu-id="1b746-110">**.NET Framework versions:** Available since 2.0.</span></span>
