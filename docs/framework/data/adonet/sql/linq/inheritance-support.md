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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: e15f0194586cc8d4e069f04a95089cbef709581f
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="inheritance-support"></a>Prise en charge de l'héritage
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]prend en charge *mappage de table simple*. En d'autres termes, une hiérarchie d'héritage complète est stockée dans une seule table de base de données. La table contient l'union au format à plat de toutes les colonnes de données possibles pour l'ensemble de la hiérarchie. Une union est le résultat de la combinaison de deux tables en une table contenant les lignes de l'une ou l'autre des tables d'origine. Chaque ligne comporte des valeurs null dans les colonnes qui ne s'appliquent pas au type de l'instance représenté par la ligne.  
  
 La stratégie de mappage de table unique est la représentation la plus simple de l'héritage. Elle fournit des caractéristiques de performances satisfaisantes pour de nombreuses catégories de requêtes.  
  
 Pour implémenter ce mappage dans [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], vous devez spécifier les attributs et les propriétés d'attribut sur la classe racine de la hiérarchie d'héritage. Pour plus d’informations, consultez [Comment : mapper des hiérarchies d’héritage](../../../../../../docs/framework/data/adonet/sql/linq/how-to-map-inheritance-hierarchies.md).  
  
 Les développeurs qui utilisent [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] peuvent également utiliser le [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] pour mapper des hiérarchies d'héritage.  
  
## <a name="see-also"></a>Voir aussi  
 [Informations générales](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
