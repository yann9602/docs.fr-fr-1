---
title: "WindowsRuntimeStreamExtensions.AsRandomAccessStream(System.IO.Stream), méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
api_name: System.IO.WindowsRuntimeStreamExtensions.AsRandomAccessStream
api_location: System.Runtime.WindowsRuntime.dll
ms.assetid: dcc72283-caed-49ee-b45d-ccaf94e97129
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 9057eabb7e3dfdfaa872fbcf2fe1180d0bbc7920
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2017
---
# <a name="windowsruntimestreamextensionsasrandomaccessstreamsystemiostream-method"></a><span data-ttu-id="ccbc8-102">WindowsRuntimeStreamExtensions.AsRandomAccessStream(System.IO.Stream), méthode</span><span class="sxs-lookup"><span data-stu-id="ccbc8-102">WindowsRuntimeStreamExtensions.AsRandomAccessStream(System.IO.Stream) Method</span></span>
<span data-ttu-id="ccbc8-103">[Pris en charge dans le .NET Framework 4.5.1 et versions ultérieures]</span><span class="sxs-lookup"><span data-stu-id="ccbc8-103">[Supported in the .NET Framework 4.5.1 and later versions]</span></span>  
  
 <span data-ttu-id="ccbc8-104">Convertit le flux spécifié en flux d'accès aléatoire.</span><span class="sxs-lookup"><span data-stu-id="ccbc8-104">Converts the specified stream to a random access stream.</span></span>  
  
 <span data-ttu-id="ccbc8-105">**Namespace :**<xref:System.IO?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="ccbc8-105">**Namespace:** <xref:System.IO?displayProperty=nameWithType></span></span>  
 <span data-ttu-id="ccbc8-106">**Assembly :** System.Runtime.WindowsRuntime (dans System.Runtime.WindowsRuntime.dll)</span><span class="sxs-lookup"><span data-stu-id="ccbc8-106">**Assembly:** System.Runtime.WindowsRuntime (in System.Runtime.WindowsRuntime.dll)</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ccbc8-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ccbc8-107">Syntax</span></span>  
  
```csharp  
[CLSCompliantAttribute(false)]  
public static  IRandomAccessStream AsRandomAccessStream(Stream stream)  
```  
  
```vb  
'Declaration  
<ExtensionAttribute> _  
<CLSCompliantAttribute(False)> _  
Public Shared Function AsRandomAccessStream ( _  
        stream As Stream) As IRandomAccessStream  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ccbc8-108">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ccbc8-108">Parameters</span></span>  
 `stream`  
  
 <span data-ttu-id="ccbc8-109">Type : <xref:System.IO.Stream?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="ccbc8-109">Type: <xref:System.IO.Stream?displayProperty=nameWithType></span></span>  
<span data-ttu-id="ccbc8-110">Flux à convertir.</span><span class="sxs-lookup"><span data-stu-id="ccbc8-110">The stream to convert.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ccbc8-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="ccbc8-111">Return Value</span></span>  
 <span data-ttu-id="ccbc8-112">Type : [Windows.Storage.Streams.RandomAccessStream](http://msdn.microsoft.com/library/windows/apps/windows.storage.streams.randomaccessstream.aspx)</span><span class="sxs-lookup"><span data-stu-id="ccbc8-112">Type: [Windows.Storage.Streams.RandomAccessStream](http://msdn.microsoft.com/library/windows/apps/windows.storage.streams.randomaccessstream.aspx)</span></span>  
<span data-ttu-id="ccbc8-113">A [!INCLUDE[wrt](../../../includes/wrt-md.md)] flux d’accès aléatoire, qui représente le flux converti.</span><span class="sxs-lookup"><span data-stu-id="ccbc8-113">A [!INCLUDE[wrt](../../../includes/wrt-md.md)] random access stream, which represents the converted stream.</span></span>  
  
## <a name="exceptions"></a><span data-ttu-id="ccbc8-114">Exceptions</span><span class="sxs-lookup"><span data-stu-id="ccbc8-114">Exceptions</span></span>  
  
|<span data-ttu-id="ccbc8-115">Exception</span><span class="sxs-lookup"><span data-stu-id="ccbc8-115">Exception</span></span>|<span data-ttu-id="ccbc8-116">Condition</span><span class="sxs-lookup"><span data-stu-id="ccbc8-116">Condition</span></span>|  
|---------------|---------------|  
|<xref:System.NotSupportedException>|<span data-ttu-id="ccbc8-117">Le flux à convertir ne prend pas en charge la recherche.</span><span class="sxs-lookup"><span data-stu-id="ccbc8-117">The stream to convert does not support seeking.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ccbc8-118">Notes</span><span class="sxs-lookup"><span data-stu-id="ccbc8-118">Remarks</span></span>  
 <span data-ttu-id="ccbc8-119">Cette méthode d'extension est disponible uniquement lorsque vous développez des applications Windows Store.</span><span class="sxs-lookup"><span data-stu-id="ccbc8-119">This extension method is available only when you develop Windows Store apps.</span></span> <span data-ttu-id="ccbc8-120">Cette méthode offre un moyen pratique de travailler avec des flux dans les applications Windows Store.</span><span class="sxs-lookup"><span data-stu-id="ccbc8-120">This method provides a convenient way of working with streams in Windows Store apps.</span></span> <span data-ttu-id="ccbc8-121">Le flux .NET Framework à convertir doit prendre en charge la recherche.</span><span class="sxs-lookup"><span data-stu-id="ccbc8-121">The .NET Framework stream you want to convert must support seeking.</span></span> <span data-ttu-id="ccbc8-122">Pour plus d'informations, voir la méthode <xref:System.IO.Stream.Seek%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ccbc8-122">For more information, see the <xref:System.IO.Stream.Seek%2A?displayProperty=nameWithType> method.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ccbc8-123">Cette API est prise en charge dans le .NET Framework 4.5.1 et versions ultérieures, mais pas dans la version 4.5.</span><span class="sxs-lookup"><span data-stu-id="ccbc8-123">This API is supported in the .NET Framework 4.5.1 and later versions, but not in version 4.5.</span></span>  
  
## <a name="version-information"></a><span data-ttu-id="ccbc8-124">Informations sur la version</span><span class="sxs-lookup"><span data-stu-id="ccbc8-124">Version Information</span></span>  
 <span data-ttu-id="ccbc8-125">**.NET pour les applications du Windows Store**</span><span class="sxs-lookup"><span data-stu-id="ccbc8-125">**.NET for Windows Store apps**</span></span>  
  
 <span data-ttu-id="ccbc8-126">Prise en charge dans : Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="ccbc8-126">Supported in: Windows 8.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ccbc8-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ccbc8-127">See Also</span></span>  
 <!--zz <xref:System.IO.WindowsRuntimeStreamExtensions>--> `System.IO.WindowsRuntimeStreamExtensions`  
 [<span data-ttu-id="ccbc8-128">Guide pratique pour effectuer une conversion entre les flux .NET Framework et les flux Windows Runtime</span><span class="sxs-lookup"><span data-stu-id="ccbc8-128">How to: Convert Between .NET Framework Streams and Windows Runtime Streams</span></span>](../../../docs/standard/io/how-to-convert-between-dotnet-streams-and-winrt-streams.md)
