---
title: "Comment : interroger des caractères dans une chaîne (LINQ) (Visual Basic) | Documents Microsoft"
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
ms.assetid: 499ebbe0-746c-4235-9dba-ce722c12b50e
caps.latest.revision: 4
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: dabd63e52707f3078c6cdc41db8c4f0e7dfbf70e
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-query-for-characters-in-a-string-linq-visual-basic"></a>Comment : interroger des caractères dans une chaîne (LINQ) (Visual Basic)
Étant donné que la <xref:System.String>classe implémente l’objet générique <xref:System.Collections.Generic.IEnumerable%601>interface, toute chaîne peut être interrogée comme une séquence de caractères.</xref:System.Collections.Generic.IEnumerable%601> </xref:System.String> Toutefois, cela n’est pas une utilisation courante de LINQ. Pour les opérations de mise en correspondance de modèles complexes, utilisez la <xref:System.Text.RegularExpressions.Regex>classe.</xref:System.Text.RegularExpressions.Regex>  
  
## <a name="example"></a>Exemple  
 L’exemple suivant interroge une chaîne pour déterminer le nombre de chiffres qu’elle contient. Notez que la requête est « réutilisée » après sa première exécution. Cela est possible, car la requête elle-même ne stocke pas les résultats réels.  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
## <a name="compiling-the-code"></a>Compilation du code  
 Créer un projet qui cible le .NET Framework version 3.5 ou une version ultérieure avec une référence à System.Core.dll et une `Imports` instruction pour l’espace de noms System.Linq.  
  
## <a name="see-also"></a>Voir aussi  
 [LINQ et chaînes (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)   
 [Comment : combiner des requêtes LINQ avec des Expressions régulières (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-combine-linq-queries-with-regular-expressions.md)
