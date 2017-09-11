---
title: "Guide pratique pour calculer des valeurs intermédiaires (C#)"
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
ms.assetid: 7fd3001f-f8f9-4bce-879f-d4c7af8a04fe
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 17f3deb790f48173fbef189fcc8f4fd569f33036
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-calculate-intermediate-values-c"></a><span data-ttu-id="9433c-102">Guide pratique pour calculer des valeurs intermédiaires (C#)</span><span class="sxs-lookup"><span data-stu-id="9433c-102">How to: Calculate Intermediate Values (C#)</span></span>
<span data-ttu-id="9433c-103">Cet exemple montre comment calculer des valeurs intermédiaires qui peuvent être utilisées dans le tri, le filtrage et la sélection.</span><span class="sxs-lookup"><span data-stu-id="9433c-103">This example shows how to calculate intermediate values that can be used in sorting, filtering, and selecting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9433c-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="9433c-104">Example</span></span>  
 <span data-ttu-id="9433c-105">L'exemple suivant utilise la clause `Let`.</span><span class="sxs-lookup"><span data-stu-id="9433c-105">The following example uses the `Let` clause.</span></span>  
  
 <span data-ttu-id="9433c-106">Cet exemple utilise le document XML suivant : [Exemple de fichier XML : Données numériques (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="9433c-106">This example uses the following XML document: [Sample XML File: Numerical Data (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).</span></span>  
  
```csharp  
XElement root = XElement.Load("Data.xml");  
IEnumerable<decimal> extensions =  
    from el in root.Elements("Data")  
    let extension = (decimal)el.Element("Quantity") * (decimal)el.Element("Price")  
    where extension >= 25  
    orderby extension  
    select extension;  
foreach (decimal ex in extensions)  
    Console.WriteLine(ex);  
```  
  
 <span data-ttu-id="9433c-107">Ce code génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="9433c-107">This code produces the following output:</span></span>  
  
```  
55.92  
73.50  
89.99  
198.00  
435.00  
```  
  
## <a name="example"></a><span data-ttu-id="9433c-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="9433c-108">Example</span></span>  
 <span data-ttu-id="9433c-109">L'exemple suivant illustre la même requête pour du code XML qui est dans un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="9433c-109">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="9433c-110">Pour plus d’informations, consultez [Utilisation des espaces de noms XML (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="9433c-110">For more information, see [Working with XML Namespaces (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
 <span data-ttu-id="9433c-111">Cet exemple utilise le document XML suivant : [Exemple de fichier XML : Données numériques dans un espace de noms](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-numerical-data-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="9433c-111">This example uses the following XML document: [Sample XML File: Numerical Data in a Namespace](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-numerical-data-in-a-namespace.md).</span></span>  
  
```csharp  
XElement root = XElement.Load("DataInNamespace.xml");  
XNamespace ad = "http://www.adatum.com";  
IEnumerable<decimal> extensions =  
    from el in root.Elements(ad + "Data")  
    let extension = (decimal)el.Element(ad + "Quantity") * (decimal)el.Element(ad + "Price")  
    where extension >= 25  
    orderby extension  
    select extension;  
foreach (decimal ex in extensions)  
    Console.WriteLine(ex);  
```  
  
 <span data-ttu-id="9433c-112">Ce code génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="9433c-112">This code produces the following output:</span></span>  
  
```  
55.92  
73.50  
89.99  
198.00  
435.00  
```  
  
## <a name="see-also"></a><span data-ttu-id="9433c-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9433c-113">See Also</span></span>  
 [<span data-ttu-id="9433c-114">Requêtes de base (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="9433c-114">Basic Queries (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)

