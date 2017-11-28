---
title: Guide pratique pour interroger un ArrayList avec LINQ (C#)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 2bfb471c-6e9a-4e60-bd83-4a1778abde11
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: fe1426bb77f4e958abda83814632e61ee9ce415c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-query-an-arraylist-with-linq-c"></a><span data-ttu-id="73cd8-102">Guide pratique pour interroger un ArrayList avec LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="73cd8-102">How to: Query an ArrayList with LINQ (C#)</span></span>
<span data-ttu-id="73cd8-103">Quand vous utilisez LINQ pour interroger des collections <xref:System.Collections.IEnumerable> non génériques telles que <xref:System.Collections.ArrayList>, vous devez déclarer explicitement le type de la variable de portée pour qu’il reflète le type spécifique des objets de la collection.</span><span class="sxs-lookup"><span data-stu-id="73cd8-103">When using LINQ to query non-generic <xref:System.Collections.IEnumerable> collections such as <xref:System.Collections.ArrayList>, you must explicitly declare the type of the range variable to reflect the specific type of the objects in the collection.</span></span> <span data-ttu-id="73cd8-104">Par exemple, si vous avez un <xref:System.Collections.ArrayList> d’objets `Student`, votre [clause from](../../../../csharp/language-reference/keywords/from-clause.md) doit ressembler à ceci :</span><span class="sxs-lookup"><span data-stu-id="73cd8-104">For example, if you have an <xref:System.Collections.ArrayList> of `Student` objects, your [from clause](../../../../csharp/language-reference/keywords/from-clause.md) should look like this:</span></span>  
  
```  
var query = from Student s in arrList  
...  
```  
  
 <span data-ttu-id="73cd8-105">En spécifiant le type de la variable de portée, vous effectuez un cast de chaque élément du `Student` en <xref:System.Collections.ArrayList>.</span><span class="sxs-lookup"><span data-stu-id="73cd8-105">By specifying the type of the range variable, you are casting each item in the <xref:System.Collections.ArrayList> to a `Student`.</span></span>  
  
 <span data-ttu-id="73cd8-106">L’utilisation d’une variable de portée explicitement typée dans une expression de requête équivaut à appeler la méthode <xref:System.Linq.Enumerable.Cast%2A>.</span><span class="sxs-lookup"><span data-stu-id="73cd8-106">The use of an explicitly typed range variable in a query expression is equivalent to calling the <xref:System.Linq.Enumerable.Cast%2A> method.</span></span> <span data-ttu-id="73cd8-107"><xref:System.Linq.Enumerable.Cast%2A> lève une exception si le cast spécifié ne peut pas être effectué.</span><span class="sxs-lookup"><span data-stu-id="73cd8-107"><xref:System.Linq.Enumerable.Cast%2A> throws an exception if the specified cast cannot be performed.</span></span> <span data-ttu-id="73cd8-108"><xref:System.Linq.Enumerable.Cast%2A> et <xref:System.Linq.Enumerable.OfType%2A> sont les deux méthodes d’opérateur de requête standard qui fonctionnent sur les types <xref:System.Collections.IEnumerable> non génériques.</span><span class="sxs-lookup"><span data-stu-id="73cd8-108"><xref:System.Linq.Enumerable.Cast%2A> and <xref:System.Linq.Enumerable.OfType%2A> are the two Standard Query Operator methods that operate on non-generic <xref:System.Collections.IEnumerable> types.</span></span> <span data-ttu-id="73cd8-109">Pour plus d’informations, consultez [Relations des types dans des opérations de requête LINQ](../../../../csharp/programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).</span><span class="sxs-lookup"><span data-stu-id="73cd8-109">For more information, see[Type Relationships in LINQ Query Operations](../../../../csharp/programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="73cd8-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="73cd8-110">Example</span></span>  
 <span data-ttu-id="73cd8-111">L’exemple suivant montre une requête simple sur un <xref:System.Collections.ArrayList>.</span><span class="sxs-lookup"><span data-stu-id="73cd8-111">The following example shows a simple query over an <xref:System.Collections.ArrayList>.</span></span> <span data-ttu-id="73cd8-112">Notez que cet exemple utilise des initialiseurs d’objets quand le code appelle la méthode <xref:System.Collections.ArrayList.Add%2A>, mais cela n’est pas une obligation.</span><span class="sxs-lookup"><span data-stu-id="73cd8-112">Note that this example uses object initializers when the code calls the <xref:System.Collections.ArrayList.Add%2A> method, but this is not a requirement.</span></span>  
  
```csharp  
using System;  
using System.Collections;  
using System.Linq;  
  
namespace NonGenericLINQ  
{  
    public class Student  
    {  
        public string FirstName { get; set; }  
        public string LastName { get; set; }  
        public int[] Scores { get; set; }  
    }  
  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            ArrayList arrList = new ArrayList();  
            arrList.Add(  
                new Student  
                    {  
                        FirstName = "Svetlana", LastName = "Omelchenko", Scores = new int[] { 98, 92, 81, 60 }  
                    });  
            arrList.Add(  
                new Student  
                    {  
                        FirstName = "Claire", LastName = "O’Donnell", Scores = new int[] { 75, 84, 91, 39 }  
                    });  
            arrList.Add(  
                new Student  
                    {  
                        FirstName = "Sven", LastName = "Mortensen", Scores = new int[] { 88, 94, 65, 91 }  
                    });  
            arrList.Add(  
                new Student  
                    {  
                        FirstName = "Cesar", LastName = "Garcia", Scores = new int[] { 97, 89, 85, 82 }  
                    });  
  
            var query = from Student student in arrList  
                        where student.Scores[0] > 95  
                        select student;  
  
            foreach (Student s in query)  
                Console.WriteLine(s.LastName + ": " + s.Scores[0]);  
  
            // Keep the console window open in debug mode.  
            Console.WriteLine("Press any key to exit.");  
            Console.ReadKey();  
        }  
    }  
}  
/* Output:   
    Omelchenko: 98  
    Garcia: 97  
*/  
```  
  
## <a name="see-also"></a><span data-ttu-id="73cd8-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="73cd8-113">See Also</span></span>  
 [<span data-ttu-id="73cd8-114">LINQ to Objects (C#)</span><span class="sxs-lookup"><span data-stu-id="73cd8-114">LINQ to Objects (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)
