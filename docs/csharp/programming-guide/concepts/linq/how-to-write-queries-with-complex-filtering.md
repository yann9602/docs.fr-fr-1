---
title: "Guide pratique pour écrire des requêtes avec un filtrage complexe (C#)"
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
ms.assetid: 4065d901-cf89-4e47-8bf9-abb65acfb003
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: c5b212796df6e65263b8b35514b6807bcdf5797f
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-write-queries-with-complex-filtering-c"></a><span data-ttu-id="51296-102">Guide pratique pour écrire des requêtes avec un filtrage complexe (C#)</span><span class="sxs-lookup"><span data-stu-id="51296-102">How to: Write Queries with Complex Filtering (C#)</span></span>
<span data-ttu-id="51296-103">Il peut arriver que vous souhaitiez écrire des requêtes LINQ to XML à l'aide de filtres complexes.</span><span class="sxs-lookup"><span data-stu-id="51296-103">Sometimes you want to write LINQ to XML queries with complex filters.</span></span> <span data-ttu-id="51296-104">Par exemple, il se peut que vous deviez rechercher tous les éléments qui ont un élément enfant avec un nom et une valeur spécifiques.</span><span class="sxs-lookup"><span data-stu-id="51296-104">For example, you might have to find all elements that have a child element with a particular name and value.</span></span> <span data-ttu-id="51296-105">Cette rubrique fournit un exemple d'écriture de requête avec un filtrage complexe.</span><span class="sxs-lookup"><span data-stu-id="51296-105">This topic gives an example of writing a query with complex filtering.</span></span>  
  
## <a name="example"></a><span data-ttu-id="51296-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="51296-106">Example</span></span>  
 <span data-ttu-id="51296-107">Cet exemple montre comment rechercher tous les éléments `PurchaseOrder` qui ont un élément `Address` enfant ayant un attribut `Type` égal à « Shipping » et un élément `State` enfant égal à « NY ».</span><span class="sxs-lookup"><span data-stu-id="51296-107">This example shows how to find all `PurchaseOrder` elements that have a child `Address` element that has a `Type` attribute equal to "Shipping" and a child `State` element equal to "NY".</span></span> <span data-ttu-id="51296-108">Il utilise une sous-requête dans la clause `Where` et l'opérateur `Any` retourne `true` si la collection possède des éléments.</span><span class="sxs-lookup"><span data-stu-id="51296-108">It uses a nested query in the `Where` clause, and the `Any` operator returns `true` if the collection has any elements in it.</span></span> <span data-ttu-id="51296-109">Pour plus d’informations sur la syntaxe de requête basée sur une méthode, consultez [Syntaxe de requête et syntaxe de méthode dans LINQ](../../../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md).</span><span class="sxs-lookup"><span data-stu-id="51296-109">For information about using method-based query syntax, see [Query Syntax and Method Syntax in LINQ](../../../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md).</span></span>  
  
 <span data-ttu-id="51296-110">Cet exemple utilise le document XML suivant : [Exemple de fichier XML : Plusieurs commandes fournisseur (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="51296-110">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="51296-111">Pour plus d’informations sur l’opérateur `Any`, consultez [Opérations de quantificateur (C#)](../../../../csharp/programming-guide/concepts/linq/quantifier-operations.md).</span><span class="sxs-lookup"><span data-stu-id="51296-111">For more information about the `Any` operator, see [Quantifier Operations (C#)](../../../../csharp/programming-guide/concepts/linq/quantifier-operations.md).</span></span>  
  
```csharp  
XElement root = XElement.Load("PurchaseOrders.xml");  
IEnumerable<XElement> purchaseOrders =  
    from el in root.Elements("PurchaseOrder")  
    where   
        (from add in el.Elements("Address")  
        where  
            (string)add.Attribute("Type") == "Shipping" &&  
            (string)add.Element("State") == "NY"  
        select add)  
        .Any()  
    select el;  
foreach (XElement el in purchaseOrders)  
    Console.WriteLine((string)el.Attribute("PurchaseOrderNumber"));  
```  
  
 <span data-ttu-id="51296-112">Ce code génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="51296-112">This code produces the following output:</span></span>  
  
```  
99505  
```  
  
## <a name="example"></a><span data-ttu-id="51296-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="51296-113">Example</span></span>  
 <span data-ttu-id="51296-114">L'exemple suivant illustre la même requête pour du code XML qui est dans un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="51296-114">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="51296-115">Pour plus d’informations, consultez [Utilisation des espaces de noms XML (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="51296-115">For more information, see [Working with XML Namespaces (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
 <span data-ttu-id="51296-116">Cet exemple utilise le document XML suivant : [Exemple de fichier XML : Plusieurs commandes fournisseur dans un espace de noms](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="51296-116">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders in a Namespace](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-in-a-namespace.md).</span></span>  
  
```csharp  
XElement root = XElement.Load("PurchaseOrdersInNamespace.xml");  
XNamespace aw = "http://www.adventure-works.com";  
IEnumerable<XElement> purchaseOrders =  
    from el in root.Elements(aw + "PurchaseOrder")  
    where  
        (from add in el.Elements(aw + "Address")  
         where  
             (string)add.Attribute(aw + "Type") == "Shipping" &&  
             (string)add.Element(aw + "State") == "NY"  
         select add)  
        .Any()  
    select el;  
foreach (XElement el in purchaseOrders)  
    Console.WriteLine((string)el.Attribute(aw + "PurchaseOrderNumber"));  
```  
  
 <span data-ttu-id="51296-117">Ce code génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="51296-117">This code produces the following output:</span></span>  
  
```  
99505  
```  
  
## <a name="see-also"></a><span data-ttu-id="51296-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="51296-118">See Also</span></span>  
 <span data-ttu-id="51296-119"><xref:System.Xml.Linq.XElement.Attribute%2A></span><span class="sxs-lookup"><span data-stu-id="51296-119"><xref:System.Xml.Linq.XElement.Attribute%2A></span></span>   
 <span data-ttu-id="51296-120"><xref:System.Xml.Linq.XContainer.Elements%2A></span><span class="sxs-lookup"><span data-stu-id="51296-120"><xref:System.Xml.Linq.XContainer.Elements%2A></span></span>   
 <span data-ttu-id="51296-121">[Requêtes de base (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/basic-queries-linq-to-xml.md) </span><span class="sxs-lookup"><span data-stu-id="51296-121">[Basic Queries (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/basic-queries-linq-to-xml.md) </span></span>  
 <span data-ttu-id="51296-122">[Opérations de projection (C#)](../../../../csharp/programming-guide/concepts/linq/projection-operations.md) </span><span class="sxs-lookup"><span data-stu-id="51296-122">[Projection Operations (C#)](../../../../csharp/programming-guide/concepts/linq/projection-operations.md) </span></span>  
 [<span data-ttu-id="51296-123">Opérations de quantificateur (C#)</span><span class="sxs-lookup"><span data-stu-id="51296-123">Quantifier Operations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/quantifier-operations.md)

