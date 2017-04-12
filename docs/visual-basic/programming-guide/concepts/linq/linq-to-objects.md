---
title: LINQ to Objects (Visual Basic) | Documents Microsoft
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
ms.assetid: dd4c30bc-1c9b-4781-a482-b5eada38deb2
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: d2bc048fea9affd4998430783d20b978317f3897
ms.lasthandoff: 03/13/2017

---
# <a name="linq-to-objects-visual-basic"></a>LINQ to Objects (Visual Basic)
Le terme « LINQ to Objects » fait référence à l’utilisation de LINQ interroge avec n’importe quel <xref:System.Collections.IEnumerable>ou <xref:System.Collections.Generic.IEnumerable%601>collection directement, sans utiliser un fournisseur LINQ intermédiaires ou les API comme [LINQ to SQL](https://msdn.microsoft.com/library/bb386976) ou [LINQ to XML](http://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13).</xref:System.Collections.Generic.IEnumerable%601> </xref:System.Collections.IEnumerable> Vous pouvez utiliser LINQ pour interroger les collections énumérables telles que <xref:System.Collections.Generic.List%601>, <xref:System.Array>, ou <xref:System.Collections.Generic.Dictionary%602>.</xref:System.Collections.Generic.Dictionary%602> </xref:System.Array> </xref:System.Collections.Generic.List%601> La collection peut être définie par l’utilisateur ou peut-être être renvoyée par une API .NET Framework.  
  
 Dans un sens de base, LINQ to Objects représente une nouvelle approche des collections. Auparavant, vous deviez écrire des boucles `For Each` complexes pour spécifier comment récupérer les données d'une collection. Dans l’approche LINQ, vous écrivez du code déclaratif qui décrit ce que vous souhaitez récupérer.  
  
 En outre, les requêtes LINQ offrent trois principaux avantages par rapport aux `For Each` boucles :  
  
1.  Elles sont plus concises et lisibles, en particulier durant le filtrage de plusieurs conditions.  
  
2.  Elles fournissent de puissantes fonctionnalités de filtrage, de classement et de regroupement avec un minimum de code d'application.  
  
3.  Elles peuvent être portées vers d'autres sources de données avec peu ou pas de changements.  
  
 En général, plus complexe l’opération à effectuer sur les données, plus vous aurez intérêt à l’aide de LINQ au lieu de techniques d’itération traditionnelles.  
  
 Cette section vise à illustrent l’approche LINQ avec quelques exemples sélectionnés. Elle ne se veut pas exhaustive.  
  
## <a name="in-this-section"></a>Dans cette section  
 [LINQ et chaînes (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)  
 Explique comment utiliser LINQ pour interroger et transformer des chaînes et des collections de chaînes. Inclut également des liens vers les rubriques qui présentent ces principes.  
  
 [LINQ et réflexion (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-reflection.md)  
 Contient des liens vers un exemple qui montre comment LINQ utilise la réflexion.  
  
 [LINQ et répertoires de fichiers (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)  
 Explique comment utiliser LINQ pour interagir avec les systèmes de fichiers. Inclut également des liens vers les rubriques qui présentent ces concepts.  
  
 [Comment : interroger un ArrayList avec LINQ (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md)  
 Montre comment interroger un ArrayList dans c#.  
  
 [Comment : ajouter des méthodes personnalisées pour les requêtes LINQ (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-add-custom-methods-for-linq-queries.md)  
 Explique comment étendre le jeu de méthodes que vous pouvez utiliser pour les requêtes LINQ en ajoutant des méthodes d’extension pour le <xref:System.Collections.Generic.IEnumerable%601>interface.</xref:System.Collections.Generic.IEnumerable%601>  
  
 [Language-Integrated Query (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/index.md)  
 Fournit des liens vers des rubriques qui expliquent LINQ et fournissent des exemples de code effectuant des requêtes.
