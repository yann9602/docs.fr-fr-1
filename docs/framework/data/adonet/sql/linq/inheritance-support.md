---
title: "Prise en charge de l'héritage"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 19bb2794-b4e7-402e-8307-1d1517381a08
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: b6ee6779814adeab73e21477137db1ed71a23a88
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="inheritance-support"></a><span data-ttu-id="26a1d-102">Prise en charge de l'héritage</span><span class="sxs-lookup"><span data-stu-id="26a1d-102">Inheritance Support</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="26a1d-103">prend en charge *mappage de table simple*.</span><span class="sxs-lookup"><span data-stu-id="26a1d-103"> supports *single-table mapping*.</span></span> <span data-ttu-id="26a1d-104">En d'autres termes, une hiérarchie d'héritage complète est stockée dans une seule table de base de données.</span><span class="sxs-lookup"><span data-stu-id="26a1d-104">In other words, a complete inheritance hierarchy is stored in a single database table.</span></span> <span data-ttu-id="26a1d-105">La table contient l'union au format à plat de toutes les colonnes de données possibles pour l'ensemble de la hiérarchie.</span><span class="sxs-lookup"><span data-stu-id="26a1d-105">The table contains the flattened union of all possible data columns for the whole hierarchy.</span></span> <span data-ttu-id="26a1d-106">Une union est le résultat de la combinaison de deux tables en une table contenant les lignes de l'une ou l'autre des tables d'origine. Chaque ligne comporte des valeurs null dans les colonnes qui ne s'appliquent pas au type de l'instance représenté par la ligne.</span><span class="sxs-lookup"><span data-stu-id="26a1d-106">(A union is the result of combining two tables into one table that has the rows that were present in either of the original tables.) Each row has nulls in the columns that do not apply to the type of the instance represented by the row.</span></span>  
  
 <span data-ttu-id="26a1d-107">La stratégie de mappage de table unique est la représentation la plus simple de l'héritage. Elle fournit des caractéristiques de performances satisfaisantes pour de nombreuses catégories de requêtes.</span><span class="sxs-lookup"><span data-stu-id="26a1d-107">The single-table mapping strategy is the simplest representation of inheritance and provides good performance characteristics for many different categories of queries.</span></span>  
  
 <span data-ttu-id="26a1d-108">Pour implémenter ce mappage dans [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], vous devez spécifier les attributs et les propriétés d'attribut sur la classe racine de la hiérarchie d'héritage.</span><span class="sxs-lookup"><span data-stu-id="26a1d-108">To implement this mapping in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], you must specify the attributes and attribute properties on the root class of the inheritance hierarchy.</span></span> <span data-ttu-id="26a1d-109">Pour plus d’informations, consultez [Comment : mapper des hiérarchies d’héritage](../../../../../../docs/framework/data/adonet/sql/linq/how-to-map-inheritance-hierarchies.md).</span><span class="sxs-lookup"><span data-stu-id="26a1d-109">For more information, see [How to: Map Inheritance Hierarchies](../../../../../../docs/framework/data/adonet/sql/linq/how-to-map-inheritance-hierarchies.md).</span></span>  
  
 <span data-ttu-id="26a1d-110">Les développeurs qui utilisent [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] peuvent également utiliser le [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] pour mapper des hiérarchies d'héritage.</span><span class="sxs-lookup"><span data-stu-id="26a1d-110">Developers using [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] can also use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to map inheritance hierarchies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26a1d-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="26a1d-111">See Also</span></span>  
 [<span data-ttu-id="26a1d-112">Informations générales</span><span class="sxs-lookup"><span data-stu-id="26a1d-112">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
