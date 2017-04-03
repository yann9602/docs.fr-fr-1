---
title: "Retourner une requête à partir d’une méthode"
description: "Comment retourner une requête."
keywords: .NET, .NET Core, C#
author: stevehoag
manager: wpickett
ms.author: wiwagn
ms.date: 11/30/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: db220f79-c35b-41f2-886c-cd068672d42d
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 0a83e3cc0e131351ef581fc15c68a3d0fda2bcce
ms.lasthandoff: 03/13/2017


---
# <a name="how-to-return-a-query-from-a-method-c-programming-guide"></a>Guide pratique pour retourner une requête à partir d'une méthode (Guide de programmation C#)
Cet exemple montre comment retourner une requête à partir d’une méthode en tant que valeur de retour et en tant que paramètre `out`.  
  
 Les objets de requête sont composables, ce qui signifie que vous pouvez retourner une requête à partir d’une méthode. Les objets qui représentent des requêtes ne stockent pas la collection résultante, mais plutôt les étapes pour générer les résultats lorsque cela est nécessaire. L’avantage de retourner des objets de requête à partir de méthodes est qu’il est possible de les composer ou modifier encore. Par conséquent, toute valeur de retour ou paramètre `out` d’une méthode qui retourne une requête doit également avoir ce type. Si une méthode matérialise une requête en un type <xref:System.Collections.Generic.List%601> ou <xref:System.Array> concret, elle est considérée comme retournant les résultats de la requête à la place de la requête elle-même. Une variable de requête retournée à partir d’une méthode peut encore être composée ou modifiée.  
  
## <a name="example"></a>Exemple  
 Dans l’exemple suivant, la première méthode retourne une requête comme valeur de retour et la seconde méthode retourne une requête comme paramètre `out`. Notez que, dans les deux cas, une requête est retournée et non pas les résultats d’une requête.  
  
 [!code-cs[csProgGuideLINQ#80](../../../samples/snippets/csharp/concepts/linq/how-to-return-a-query-from-a-method_1.cs)]  

## <a name="see-also"></a>Voir aussi  
 [Expressions de requête LINQ](index.md)
