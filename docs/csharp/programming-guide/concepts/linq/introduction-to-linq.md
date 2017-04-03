---
title: "Présentation de LINQ (C#) | Microsoft Docs"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 54874feb-55e5-4ca8-a9d6-1c1127fd7fb1
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 617fec7a8405116735d7a7510513adf845068f4e
ms.lasthandoff: 03/13/2017

---
# <a name="introduction-to-linq-c"></a>Présentation de LINQ (C#)
LINQ (Language-Integrated Query) est une nouveauté du .NET Framework 3.5 qui crée un pont entre le monde des objets et celui des données.  
  
 En règle générale, les requêtes de données sont exprimées comme de simples chaînes, sans vérification de type au moment de l’exécution, ni prise en charge IntelliSense. En outre, vous devez apprendre un langage de requête différent pour chaque type de source de données : bases de données SQL, documents XML, services web, etc. LINQ fait d’une *requête* une construction de langage de première classe en C#. Vous pouvez écrire des requêtes pour des collections d’objets fortement typées à l’aide de mots clés de langage et d’opérateurs familiers.  
  
 Vous pouvez écrire des requêtes LINQ en C# pour des bases de données SQL Server, des documents XML, des datasets ADO.NET et toute collection d’objets prenant en charge <xref:System.Collections.IEnumerable> ou l’interface générique <xref:System.Collections.Generic.IEnumerable%601>. La prise en charge LINQ est également fournie par des tierces parties pour de nombreux services web et autres implémentations de base de données.  
  
 Vous pouvez utiliser des requêtes LINQ dans de nouveaux projets, ou avec des requêtes non LINQ dans des projets existants. La seule exigence est que le projet cible .NET Framework 3.5 ou version ultérieure.  
  
 L’illustration suivante de Visual Studio montre une requête LINQ partiellement terminée, exécutée sur une base de données SQL Server, en C# et en Visual Basic, avec un contrôle de type complet et une prise en charge IntelliSense.  
  
 ![Requête LINQ avec Intellisense](../../../../csharp/programming-guide/concepts/linq/media/query_intell.png "Query_Intell")  
  
## <a name="next-steps"></a>Étapes suivantes  
 Pour plus d’informations sur LINQ, commencez par vous familiariser avec certains concepts de base expliqués dans la section de prise en main de [Bien démarrer avec LINQ en C#](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md), puis lisez la documentation relative à la technologie LINQ qui vous intéresse :  
  
-   Bases de données SQL Server : [LINQ to SQL](https://msdn.microsoft.com/library/bb386976)  
  
-   Documents XML [LINQ to XML (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml.md)  
  
-   Datasets ADO.NET [LINQ to DataSet](http://msdn.microsoft.com/library/743e3755-3ecb-45a2-8d9b-9ed41f0dcf17)  
  
-   Collections, fichiers, chaînes .NET. : [LINQ to Objects (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)  
  
## <a name="see-also"></a>Voir aussi  
 [LINQ (Language-Integrated Query) (C#)](../../../../csharp/programming-guide/concepts/linq/index.md)
