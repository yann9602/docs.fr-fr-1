---
title: "Interroger une collection d’objets"
description: Comment interroger les collections.
keywords: .NET, .NET Core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 11/30/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 87a76f8a-0b58-4791-90ea-2fe0a30416c9
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 9e08f2e5877ffe24f5a238ab19abb9760cb442f2
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="query-a-collection-of-objects"></a><span data-ttu-id="61541-104">Interroger une collection d’objets</span><span class="sxs-lookup"><span data-stu-id="61541-104">Query a collection of objects</span></span>
<span data-ttu-id="61541-105">Cet exemple montre comment effectuer une requête simple sur une liste d’objets `Student`.</span><span class="sxs-lookup"><span data-stu-id="61541-105">This example shows how to perform a simple query over a list of `Student` objects.</span></span> <span data-ttu-id="61541-106">Chaque objet `Student` contient des informations de base sur l’étudiant et une liste qui représente les notes de l’étudiant lors de quatre examens.</span><span class="sxs-lookup"><span data-stu-id="61541-106">Each `Student` object contains some basic information about the student, and a list that represents the student's scores on four examinations.</span></span>  
  
 <span data-ttu-id="61541-107">Cette application sert de cadre pour de nombreux autres exemples dans cette section qui utilisent la même source de données `students`.</span><span class="sxs-lookup"><span data-stu-id="61541-107">This application serves as the framework for many other examples in this section that use the same `students` data source.</span></span>  
  
## <a name="example"></a><span data-ttu-id="61541-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="61541-108">Example</span></span>  
 <span data-ttu-id="61541-109">La requête suivante retourne les étudiants qui ont reçu une note supérieure ou égale à 90 lors de leur premier examen.</span><span class="sxs-lookup"><span data-stu-id="61541-109">The following query returns the students who received a score of 90 or greater on their first exam.</span></span>  
  
 <span data-ttu-id="61541-110">[!code-cs[csProgGuideLINQ#15](../../../samples/snippets/csharp/concepts/linq/how-to-query-a-collection-of-objects_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="61541-110">[!code-cs[csProgGuideLINQ#15](../../../samples/snippets/csharp/concepts/linq/how-to-query-a-collection-of-objects_1.cs)]</span></span>  
  
 <span data-ttu-id="61541-111">Cette requête est volontairement simple pour vous permettre de faire des essais.</span><span class="sxs-lookup"><span data-stu-id="61541-111">This query is intentionally simple to enable you to experiment.</span></span> <span data-ttu-id="61541-112">Par exemple, vous pouvez essayer plus de conditions dans la clause `where` ou utiliser une clause `orderby` pour trier les résultats.</span><span class="sxs-lookup"><span data-stu-id="61541-112">For example, you can try more conditions in the `where` clause, or use an `orderby` clause to sort the results.</span></span>  
  

## <a name="see-also"></a><span data-ttu-id="61541-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="61541-113">See also</span></span>  
 [<span data-ttu-id="61541-114">Expressions de requête LINQ</span><span class="sxs-lookup"><span data-stu-id="61541-114">LINQ Query Expressions</span></span>](index.md)

