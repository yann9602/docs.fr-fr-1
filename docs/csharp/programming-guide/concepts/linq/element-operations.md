---
title: "Opérations d’éléments (C#) | Microsoft Docs"
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
ms.assetid: 283206c9-3246-4c48-b01a-d9de409a7231
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
ms.openlocfilehash: 0cada4f5dae6eab5511870395133c2ef67ca796e
ms.lasthandoff: 03/13/2017

---
# <a name="element-operations-c"></a>Opérations d’éléments (C#)
Les opérations d’éléments retournent un élément unique et spécifique à partir d’une séquence.  
  
 Les méthodes d’opérateurs de requête standard qui effectuent des opérations d’éléments sont répertoriées dans la section suivante.  
  
## <a name="methods"></a>Méthodes  
  
|Nom de la méthode|Description|Syntaxe d'expression de requête C#|Informations complémentaires|  
|-----------------|-----------------|---------------------------------|----------------------|  
|ElementAt|Retourne l’élément situé à un index spécifié dans une collection.|Non applicable.|<xref:System.Linq.Enumerable.ElementAt%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.ElementAt%2A?displayProperty=fullName>|  
|ElementAtOrDefault|Retourne l’élément situé à un index spécifié dans une collection ou une valeur par défaut si l’index est hors limites.|Non applicable.|<xref:System.Linq.Enumerable.ElementAtOrDefault%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.ElementAtOrDefault%2A?displayProperty=fullName>|  
|First|Retourne le premier élément d’une collection ou le premier élément qui satisfait à une condition.|Non applicable.|<xref:System.Linq.Enumerable.First%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.First%2A?displayProperty=fullName>|  
|FirstOrDefault|Retourne le premier élément d’une collection ou le premier élément qui remplit une condition. Retourne une valeur par défaut s’il n’existe aucun élément répondant aux critères.|Non applicable.|<xref:System.Linq.Enumerable.FirstOrDefault%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.FirstOrDefault%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.FirstOrDefault%60%601%28System.Linq.IQueryable%7B%60%600%7D%29?displayProperty=fullName>|  
|Dernier|Retourne le dernier élément d’une collection ou le dernier élément qui remplit une condition.|Non applicable.|<xref:System.Linq.Enumerable.Last%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Last%2A?displayProperty=fullName>|  
|LastOrDefault|Retourne le dernier élément d’une collection ou le dernier élément qui remplit une condition. Retourne une valeur par défaut s’il n’existe aucun élément répondant aux critères.|Non applicable.|<xref:System.Linq.Enumerable.LastOrDefault%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.LastOrDefault%2A?displayProperty=fullName>|  
|Single|Retourne le seul élément d’une collection ou le seul élément qui remplit une condition.|Non applicable.|<xref:System.Linq.Enumerable.Single%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Single%2A?displayProperty=fullName>|  
|SingleOrDefault|Retourne le seul élément d’une collection ou le seul élément qui remplit une condition. Retourne une valeur par défaut s’il n’existe aucun élément remplissant les critères ou si la collection ne contient pas exactement un élément.|Non applicable.|<xref:System.Linq.Enumerable.SingleOrDefault%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.SingleOrDefault%2A?displayProperty=fullName>|  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Linq>   
 [Vue d’ensemble des opérateurs de requête standard (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)   
 [Guide pratique pour interroger les fichiers les plus volumineux dans une arborescence de répertoires (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq.md)
