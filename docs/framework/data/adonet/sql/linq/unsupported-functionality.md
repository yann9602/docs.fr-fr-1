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
ms.workload: dotnet
ms.openlocfilehash: 244d9ee7accd3686729542d0f0a15966bcde7b78
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="unsupported-functionality"></a><span data-ttu-id="103e5-102">Fonctionnalité non prise en charge</span><span class="sxs-lookup"><span data-stu-id="103e5-102">Unsupported Functionality</span></span>
<span data-ttu-id="103e5-103">Dans LINQ to SQL, les fonctionnalités SQL suivantes ne peuvent pas être exposées via la traduction de constructions du Common Language Runtime (CLR) et .NET Framework existantes :</span><span class="sxs-lookup"><span data-stu-id="103e5-103">In LINQ to SQL, the following SQL functionality cannot be exposed through translation of existing common language runtime (CLR) and .NET Framework constructs:</span></span>  
  
-   `STDDEV`  
  
-   `LIKE`  
  
     <span data-ttu-id="103e5-104">Bien que `LIKE` ne soit pas prise en charge par le biais de la traduction directe, il existe des fonctionnalités similaires dans la classe <xref:System.Data.Linq.SqlClient.SqlMethods>.</span><span class="sxs-lookup"><span data-stu-id="103e5-104">Although `LIKE` is not supported through direct translation, similar functionality exists in the <xref:System.Data.Linq.SqlClient.SqlMethods> class.</span></span> <span data-ttu-id="103e5-105">Pour plus d'informations, consultez <xref:System.Data.Linq.SqlClient.SqlMethods.Like%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="103e5-105">For more information, see <xref:System.Data.Linq.SqlClient.SqlMethods.Like%2A?displayProperty=nameWithType>.</span></span>  
  
-   `DATEDIFF`  
  
     <span data-ttu-id="103e5-106">LINQ to SQL a une prise en charge limitée de `DATEDIFF`.</span><span class="sxs-lookup"><span data-stu-id="103e5-106">LINQ to SQL has limited support for `DATEDIFF`.</span></span> <span data-ttu-id="103e5-107">Il existe des fonctionnalités similaires dans la classe <xref:System.Data.Linq.SqlClient.SqlMethods>.</span><span class="sxs-lookup"><span data-stu-id="103e5-107">Similar functionality exists in the <xref:System.Data.Linq.SqlClient.SqlMethods> class.</span></span>  
  
-   `ROUND`  
  
     <span data-ttu-id="103e5-108">LINQ to SQL a une prise en charge limitée de `ROUND`.</span><span class="sxs-lookup"><span data-stu-id="103e5-108">LINQ to SQL has limited support for `ROUND`.</span></span> <span data-ttu-id="103e5-109">Pour plus d’informations, consultez [System.Math, méthodes](system-math-methods.md).</span><span class="sxs-lookup"><span data-stu-id="103e5-109">For more information, see [System.Math Methods](system-math-methods.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="103e5-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="103e5-110">See Also</span></span>  
 [<span data-ttu-id="103e5-111">Fonctions et types de données</span><span class="sxs-lookup"><span data-stu-id="103e5-111">Data Types and Functions</span></span>](data-types-and-functions.md)
