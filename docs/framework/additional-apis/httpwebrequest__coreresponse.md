---
title: Champ de HttpWebRequest._CoreResponse
ms.date: 01/29/2018
ms.prod: .net-framework
ms.technology: 
ms.topic: reference
topic_type:
- apiref
api_name:
- System.Net.HttpWebRequest._CoreResponse
api_location:
- System.dll
api_type:
- Assembly
author: stevewhims
ms.author: stwhi
manager: markl
ms.workload:
- dotnet
ms.openlocfilehash: e6493747cf6c894357223f011da026770778e26c
ms.sourcegitcommit: cf22b29db780e532e1090c6e755aa52d28273fa6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2018
---
# <a name="httpwebrequestcoreresponse-field"></a><span data-ttu-id="66237-102">HttpWebRequest. \_CoreResponse champ</span><span class="sxs-lookup"><span data-stu-id="66237-102">HttpWebRequest.\_CoreResponse Field</span></span>

<span data-ttu-id="66237-103">`HttpWebRequest._CoreResponse`est un objet (soit un [CoreResponseData](coreresponsedata.md) ou <xref:System.Exception>) qui contient le résultat de l’analyse de réponse HTTP.</span><span class="sxs-lookup"><span data-stu-id="66237-103">`HttpWebRequest._CoreResponse` is an object (either a [CoreResponseData](coreresponsedata.md) or an <xref:System.Exception>) containing the result of HTTP response parsing.</span></span>

## <a name="syntax"></a><span data-ttu-id="66237-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="66237-104">Syntax</span></span>
  
```csharp
private object _CoreResponse
```

> [!WARNING]
> <span data-ttu-id="66237-105">Cette API n’est pas destinée à être utilisé directement dans votre code.</span><span class="sxs-lookup"><span data-stu-id="66237-105">This API is not meant to be used directly in your code.</span></span> <span data-ttu-id="66237-106">Au lieu de cela, vous devez utiliser un <xref:System.Diagnostics.DiagnosticSource> raccordement du code de mise en réseau.</span><span class="sxs-lookup"><span data-stu-id="66237-106">Instead, you should use a <xref:System.Diagnostics.DiagnosticSource> to hook networking code.</span></span> <span data-ttu-id="66237-107">Consultez [le Guide d’utilisation de DiagnosticSource](https://github.com/dotnet/corefx/blob/master/src/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).</span><span class="sxs-lookup"><span data-stu-id="66237-107">See [DiagnosticSource User's Guide](https://github.com/dotnet/corefx/blob/master/src/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).</span></span>
> 
> <span data-ttu-id="66237-108">Microsoft ne prend pas en charge l’utilisation de cette classe dans une application de production en toutes circonstances.</span><span class="sxs-lookup"><span data-stu-id="66237-108">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="66237-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="66237-109">Requirements</span></span>

<span data-ttu-id="66237-110">**Namespace :**<xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="66237-110">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="66237-111">**Assembly :** système (dans System.dll)</span><span class="sxs-lookup"><span data-stu-id="66237-111">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="66237-112">**Versions du .NET framework :** disponible depuis la version 2.0.</span><span class="sxs-lookup"><span data-stu-id="66237-112">**.NET Framework versions:** Available since 2.0.</span></span>
