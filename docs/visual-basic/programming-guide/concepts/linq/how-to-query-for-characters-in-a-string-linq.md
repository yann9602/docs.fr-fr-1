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
ms.translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: dabd63e52707f3078c6cdc41db8c4f0e7dfbf70e
ms.contentlocale: fr-fr
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-query-for-characters-in-a-string-linq-visual-basic"></a><span data-ttu-id="dd02d-102">Comment : interroger des caractères dans une chaîne (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dd02d-102">How to: Query for Characters in a String (LINQ) (Visual Basic)</span></span>
<span data-ttu-id="dd02d-103">Étant donné que la <xref:System.String>classe implémente l’objet générique <xref:System.Collections.Generic.IEnumerable%601>interface, toute chaîne peut être interrogée comme une séquence de caractères.</xref:System.Collections.Generic.IEnumerable%601> </xref:System.String></span><span class="sxs-lookup"><span data-stu-id="dd02d-103">Because the <xref:System.String> class implements the generic <xref:System.Collections.Generic.IEnumerable%601> interface, any string can be queried as a sequence of characters.</span></span> <span data-ttu-id="dd02d-104">Toutefois, cela n’est pas une utilisation courante de LINQ.</span><span class="sxs-lookup"><span data-stu-id="dd02d-104">However, this is not a common use of LINQ.</span></span> <span data-ttu-id="dd02d-105">Pour les opérations de mise en correspondance de modèles complexes, utilisez la <xref:System.Text.RegularExpressions.Regex>classe.</xref:System.Text.RegularExpressions.Regex></span><span class="sxs-lookup"><span data-stu-id="dd02d-105">For complex pattern matching operations, use the <xref:System.Text.RegularExpressions.Regex> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dd02d-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="dd02d-106">Example</span></span>  
 <span data-ttu-id="dd02d-107">L’exemple suivant interroge une chaîne pour déterminer le nombre de chiffres qu’elle contient.</span><span class="sxs-lookup"><span data-stu-id="dd02d-107">The following example queries a string to determine the number of numeric digits it contains.</span></span> <span data-ttu-id="dd02d-108">Notez que la requête est « réutilisée » après sa première exécution.</span><span class="sxs-lookup"><span data-stu-id="dd02d-108">Note that the query is "reused" after it is executed the first time.</span></span> <span data-ttu-id="dd02d-109">Cela est possible, car la requête elle-même ne stocke pas les résultats réels.</span><span class="sxs-lookup"><span data-stu-id="dd02d-109">This is possible because the query itself does not store any actual results.</span></span>  
  
<span data-ttu-id="dd02d-110"><CodeContentPlaceHolder>0</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="dd02d-110"><CodeContentPlaceHolder>0</CodeContentPlaceHolder></span></span>  
## <a name="compiling-the-code"></a><span data-ttu-id="dd02d-111">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="dd02d-111">Compiling the Code</span></span>  
 <span data-ttu-id="dd02d-112">Créer un projet qui cible le .NET Framework version 3.5 ou une version ultérieure avec une référence à System.Core.dll et une `Imports` instruction pour l’espace de noms System.Linq.</span><span class="sxs-lookup"><span data-stu-id="dd02d-112">Create a project that targets the .NET Framework version 3.5 or higher with a reference to System.Core.dll and a `Imports` statement for the System.Linq namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd02d-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dd02d-113">See Also</span></span>  
 <span data-ttu-id="dd02d-114">[LINQ et chaînes (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md) </span><span class="sxs-lookup"><span data-stu-id="dd02d-114">[LINQ and Strings (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md) </span></span>  
<span data-ttu-id="dd02d-115"> [Comment : combiner des requêtes LINQ avec des Expressions régulières (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-combine-linq-queries-with-regular-expressions.md)</span><span class="sxs-lookup"><span data-stu-id="dd02d-115"> [How to: Combine LINQ Queries with Regular Expressions (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-combine-linq-queries-with-regular-expressions.md)</span></span>
