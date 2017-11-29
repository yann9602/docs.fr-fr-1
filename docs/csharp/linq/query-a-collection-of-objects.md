---
title: "Interroger une collection d’objets"
description: Comment interroger les collections.
keywords: .NET, .NET Core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 11/30/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: 87a76f8a-0b58-4791-90ea-2fe0a30416c9
ms.openlocfilehash: 74d6c1f080c3e70867f5d2f074315bd1d8486bf0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="query-a-collection-of-objects"></a><span data-ttu-id="9631c-104">Interroger une collection d’objets</span><span class="sxs-lookup"><span data-stu-id="9631c-104">Query a collection of objects</span></span>
<span data-ttu-id="9631c-105">Cet exemple montre comment effectuer une requête simple sur une liste d’objets `Student`.</span><span class="sxs-lookup"><span data-stu-id="9631c-105">This example shows how to perform a simple query over a list of `Student` objects.</span></span> <span data-ttu-id="9631c-106">Chaque objet `Student` contient des informations de base sur l’étudiant et une liste qui représente les notes de l’étudiant lors de quatre examens.</span><span class="sxs-lookup"><span data-stu-id="9631c-106">Each `Student` object contains some basic information about the student, and a list that represents the student's scores on four examinations.</span></span>  
  
 <span data-ttu-id="9631c-107">Cette application sert de cadre pour de nombreux autres exemples dans cette section qui utilisent la même source de données `students`.</span><span class="sxs-lookup"><span data-stu-id="9631c-107">This application serves as the framework for many other examples in this section that use the same `students` data source.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9631c-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="9631c-108">Example</span></span>  
 <span data-ttu-id="9631c-109">La requête suivante retourne les étudiants qui ont reçu une note supérieure ou égale à 90 lors de leur premier examen.</span><span class="sxs-lookup"><span data-stu-id="9631c-109">The following query returns the students who received a score of 90 or greater on their first exam.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#15](../../../samples/snippets/csharp/concepts/linq/how-to-query-a-collection-of-objects_1.cs)]  
  
 <span data-ttu-id="9631c-110">Cette requête est volontairement simple pour vous permettre de faire des essais.</span><span class="sxs-lookup"><span data-stu-id="9631c-110">This query is intentionally simple to enable you to experiment.</span></span> <span data-ttu-id="9631c-111">Par exemple, vous pouvez essayer plus de conditions dans la clause `where` ou utiliser une clause `orderby` pour trier les résultats.</span><span class="sxs-lookup"><span data-stu-id="9631c-111">For example, you can try more conditions in the `where` clause, or use an `orderby` clause to sort the results.</span></span>  
  

## <a name="see-also"></a><span data-ttu-id="9631c-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9631c-112">See also</span></span>  
 [<span data-ttu-id="9631c-113">Expressions de requête LINQ</span><span class="sxs-lookup"><span data-stu-id="9631c-113">LINQ Query Expressions</span></span>](index.md)  
 [<span data-ttu-id="9631c-114">Chaînes interpolées</span><span class="sxs-lookup"><span data-stu-id="9631c-114">Interpolated Strings</span></span>](../language-reference/keywords/interpolated-strings.md)
