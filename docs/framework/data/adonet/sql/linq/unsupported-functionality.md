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
# <a name="unsupported-functionality"></a>Fonctionnalité non prise en charge
Dans LINQ to SQL, les fonctionnalités SQL suivantes ne peuvent pas être exposées via la traduction de constructions du Common Language Runtime (CLR) et .NET Framework existantes :  
  
-   `STDDEV`  
  
-   `LIKE`  
  
     Bien que `LIKE` ne soit pas prise en charge par le biais de la traduction directe, il existe des fonctionnalités similaires dans la classe <xref:System.Data.Linq.SqlClient.SqlMethods>. Pour plus d'informations, consultez <xref:System.Data.Linq.SqlClient.SqlMethods.Like%2A?displayProperty=nameWithType>.  
  
-   `DATEDIFF`  
  
     LINQ to SQL a une prise en charge limitée de `DATEDIFF`. Il existe des fonctionnalités similaires dans la classe <xref:System.Data.Linq.SqlClient.SqlMethods>.  
  
-   `ROUND`  
  
     LINQ to SQL a une prise en charge limitée de `ROUND`. Pour plus d’informations, consultez [System.Math, méthodes](system-math-methods.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions et Types de données](data-types-and-functions.md)
