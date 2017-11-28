---
title: "Comparaison entre la programmation fonctionnelle Programmation procédurale (LINQ to XML) (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: fc64e39c-a487-4882-9169-da4de97917d9
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b6aa8ce45afdb68f7ff544b8c8f2f5e1e4a79533
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="functional-vs-procedural-programming-linq-to-xml-c"></a>Comparaison entre la programmation fonctionnelle Programmation procédurale (LINQ to XML) (C#)
Il existe différents types d'applications XML :  
  
-   Certaines applications prennent des documents XML sources et produisent de nouveaux documents XML d'une forme différente des documents sources.  
  
-   Certaines applications prennent des documents XML sources et produisent des documents d'une forme totalement différente, tels que des fichiers texte CSV ou HTML.  
  
-   Certaines applications prennent des documents XML sources et insèrent des enregistrements dans une base de données.  
  
-   Certaines applications prennent des données à partir d'une autre source, telle qu'une base de données, et créent des documents XML à partir de celle-ci.  
  
 Il existe d'autres types d'applications XML, mais ceux-ci sont représentatifs des types de fonctionnalités qu'un programmateur XML doit implémenter.  
  
 Avec tous ces types d'applications, un développeur peut suivre deux approches contrastées :  
  
-   Construction fonctionnelle à l'aide d'une approche déclarative.  
  
-   Modification d'arborescence XML en mémoire à l'aide de procédures de code.  
  
 LINQ to XML prend en charge les deux approches.  
  
 Lors de l'utilisation de l'approche fonctionnelle, vous écrivez des transformations qui prennent les documents sources et génèrent des documents de résultats complètement nouveaux de la forme souhaitée.  
  
 Lors de la modification d'une arborescence XML en place, vous écrivez du code qui traverse et parcourt les nœuds d'une arborescence XML en mémoire, en insérant, supprimant et modifiant des nœuds si nécessaire.  
  
 Vous pouvez utiliser LINQ to XML avec l'une ou l'autre de ces approches. Vous utilisez les mêmes classes et, dans certains cas, les mêmes méthodes. Toutefois, la structure et les objectifs des deux approches sont très différents. Par exemple, dans différentes situations, l'une ou l'autre approche fournira souvent de meilleures performances et utilisera plus ou moins de mémoire. En outre, l'une ou l'autre approche sera plus facile à écrire et génèrera du code plus facile à maintenir.  
  
 Pour voir une comparaison de ces deux approches, consultez [Comparaison de la modification d’arborescence XML en mémoire et de la construction fonctionnelle (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md).  
  
 Pour obtenir un didacticiel sur l’écriture de transformations fonctionnelles, consultez [Transformations fonctionnelles pures de données XML (C#)](../../../../csharp/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de la programmation LINQ to XML (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
