---
title: "Fonctionnalité non prise en charge"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e480cfb5-697e-42c8-bed5-9264c945c4f9
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 6dd8ccebd278fdc36c536c49f7f1d4262b2de8c1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="unsupported-functionality"></a><span data-ttu-id="c2dcd-102">Fonctionnalité non prise en charge</span><span class="sxs-lookup"><span data-stu-id="c2dcd-102">Unsupported Functionality</span></span>
<span data-ttu-id="c2dcd-103">Dans LINQ to SQL, les fonctionnalités SQL suivantes ne peuvent pas être exposées via la traduction de constructions du Common Language Runtime (CLR) et .NET Framework existantes :</span><span class="sxs-lookup"><span data-stu-id="c2dcd-103">In LINQ to SQL, the following SQL functionality cannot be exposed through translation of existing common language runtime (CLR) and .NET Framework constructs:</span></span>  
  
-   `STDDEV`  
  
-   `LIKE`  
  
     <span data-ttu-id="c2dcd-104">Bien que `LIKE` ne soit pas prise en charge par le biais de la traduction directe, il existe des fonctionnalités similaires dans la classe <xref:System.Data.Linq.SqlClient.SqlMethods>.</span><span class="sxs-lookup"><span data-stu-id="c2dcd-104">Although `LIKE` is not supported through direct translation, similar functionality exists in the <xref:System.Data.Linq.SqlClient.SqlMethods> class.</span></span> <span data-ttu-id="c2dcd-105">Pour plus d'informations, consultez <xref:System.Data.Linq.SqlClient.SqlMethods.Like%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c2dcd-105">For more information, see <xref:System.Data.Linq.SqlClient.SqlMethods.Like%2A?displayProperty=nameWithType>.</span></span>  
  
-   `DATEDIFF`  
  
     <span data-ttu-id="c2dcd-106">LINQ to SQL a une prise en charge limitée de `DATEDIFF`.</span><span class="sxs-lookup"><span data-stu-id="c2dcd-106">LINQ to SQL has limited support for `DATEDIFF`.</span></span> <span data-ttu-id="c2dcd-107">Il existe des fonctionnalités similaires dans la classe <xref:System.Data.Linq.SqlClient.SqlMethods>.</span><span class="sxs-lookup"><span data-stu-id="c2dcd-107">Similar functionality exists in the <xref:System.Data.Linq.SqlClient.SqlMethods> class.</span></span>  
  
-   `ROUND`  
  
     <span data-ttu-id="c2dcd-108">LINQ to SQL a une prise en charge limitée de `ROUND`.</span><span class="sxs-lookup"><span data-stu-id="c2dcd-108">LINQ to SQL has limited support for `ROUND`.</span></span> <span data-ttu-id="c2dcd-109">Pour plus d’informations, consultez [System.Math, méthodes](system-math-methods.md).</span><span class="sxs-lookup"><span data-stu-id="c2dcd-109">For more information, see [System.Math Methods](system-math-methods.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2dcd-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c2dcd-110">See Also</span></span>  
 [<span data-ttu-id="c2dcd-111">Fonctions et Types de données</span><span class="sxs-lookup"><span data-stu-id="c2dcd-111">Data Types and Functions</span></span>](data-types-and-functions.md)
