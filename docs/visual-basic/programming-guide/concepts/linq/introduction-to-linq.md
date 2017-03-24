---
title: "Introduction à LINQ (Visual Basic) | Documents Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: c6339c12-9b2d-433e-961c-0d2b7f0091c2
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 41964e2fcbb079b7650c3132c9035fc2f754f3de
ms.lasthandoff: 03/13/2017

---
# <a name="introduction-to-linq-visual-basic"></a>Introduction à LINQ (Visual Basic)
Language-Integrated Query (LINQ) est qu'une innovation dans le .NET Framework version 3.5 qui permet l’écart entre le monde des objets et le monde des données.  
  
 En règle générale, les requêtes sur les données sont exprimées compiler les chaînes simples sans vérification de type au moment ou la prise en charge IntelliSense. En outre, vous devez apprendre un langage de requête différente pour chaque type de source de données : SQL bases de données, documents XML, divers services Web et ainsi de suite. LINQ permet une *requête* une construction de langage de premier ordre en Visual Basic. Vous écrivez des requêtes sur des collections fortement typées d’objets à l’aide de mots clés du langage et des opérateurs familiers.  
  
 Vous pouvez écrire des requêtes LINQ en Visual Basic pour SQL Server bases de données XML des documents, des groupes de données ADO.NET et toute collection d’objets qui prend en charge <xref:System.Collections.IEnumerable>ou générique <xref:System.Collections.Generic.IEnumerable%601>interface.</xref:System.Collections.Generic.IEnumerable%601> </xref:System.Collections.IEnumerable> Prise en charge LINQ est également fournie par des tiers pour de nombreux services Web et d’autres implémentations de base de données.  
  
 Vous pouvez utiliser des requêtes LINQ dans les nouveaux projets ou avec des requêtes non-LINQ dans des projets existants. La seule exigence est que le projet cible .NET Framework 3.5 ou version ultérieure.  
  
 L’illustration suivante à partir de Visual Studio affiche une requête LINQ partiellement terminée sur une base de données SQL Server dans les langages c# et Visual Basic avec vérification de type complet et la prise en charge IntelliSense.  
  
 ![Requête LINQ avec Intellisense](../../../../csharp/programming-guide/concepts/linq/media/query_intell.png "Query_Intell")  
  
## <a name="next-steps"></a>Étapes suivantes  
 Pour en savoir plus sur LINQ, commencez par vous familiariser avec certains concepts de base dans la section mise en route [mise en route de LINQ en Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md), puis lisez la documentation de la technologie LINQ qui vous intéresse :  
  
-   Bases de données SQL Server : [LINQ to SQL](https://msdn.microsoft.com/library/bb386976)  
  
-   Documents XML : [LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md)  
  
-   Groupes de données ADO.NET : [LINQ to DataSet](http://msdn.microsoft.com/library/743e3755-3ecb-45a2-8d9b-9ed41f0dcf17)  
  
-   Collections .NET, fichiers, chaînes et ainsi de suite : [LINQ to Objects (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Language-Integrated Query (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/index.md)
