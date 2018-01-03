---
title: "Comment : stocker et réutiliser des requêtes"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: a012bd79-1809-45e3-adea-0229532396cc
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 8170b1219bf66c1f90fb5db3143916f7a41aab94
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-store-and-reuse-queries"></a>Comment : stocker et réutiliser des requêtes
Lorsque vous possédez une application qui exécute de nombreuses fois des requêtes similaires d'un point de vue structurel, vous pouvez souvent améliorer les performances en compilant la requête une fois et en l'exécutant plusieurs fois avec des paramètres différents. Par exemple, une application peut avoir besoin de récupérer tous les clients d'une ville spécifique, où la ville est spécifiée à l'exécution par l'utilisateur dans un formulaire. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]prend en charge l’utilisation de *des requêtes compilées* à cet effet.  
  
> [!NOTE]
>  Ce modèle d’utilisation représente l’utilisation la plus courante pour les requêtes compilées. D'autres approches sont possibles. Par exemple, les requêtes compilées peuvent être stockées comme des membres statiques sur une classe partielle qui étend le code généré par le concepteur.  
  
## <a name="example"></a>Exemple  
 Dans de nombreux scénarios, vous pouvez avoir besoin de réutiliser des requêtes au-delà des limites de thread. Dans ce type de situations, le stockage des requêtes compilées dans des variables statiques est particulièrement efficace. L'exemple de code suivant suppose l'existence d'une classe `Queries` conçue pour stocker des requêtes compilées et d'une classe Northwind qui représente un <xref:System.Data.Linq.DataContext> fortement typé.  
  
 [!code-csharp[DLinqQuerying#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#6)]
 [!code-vb[DLinqQuerying#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#6)]  
  
 [!code-csharp[DLinqQuerying#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#7)]
 [!code-vb[DLinqQuerying#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#7)]  
  
## <a name="example"></a>Exemple  
 Vous ne pouvez pas actuellement stocker (dans des variables statiques) des requêtes qui retournent un *type anonyme*, car le type ne possède pas de nom à utiliser comme argument générique. L’exemple suivant montre comment vous pouvez contourner le problème en créant un type qui peut représenter le résultat et en l’utilisant comme argument générique.  
  
 [!code-csharp[DLinqQuerying#8](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#8)]
 [!code-vb[DLinqQuerying#8](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#8)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Data.Linq.CompiledQuery>  
 [Concepts relatifs aux requêtes](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)  
 [Interrogation de la base de données](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)
