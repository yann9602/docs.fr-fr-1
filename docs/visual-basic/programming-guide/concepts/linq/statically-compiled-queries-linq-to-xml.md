---
title: "Compilé statiquement des requêtes (LINQ to XML) (Visual Basic) | Documents Microsoft"
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
ms.assetid: 3f4825c7-c3b0-48da-ba4e-8e97fb2a2f34
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: 14abadaf548e228244a1ff7ca72fa3896ef4eb5d
ms.openlocfilehash: 83d6e37a00477cedc4a5a4c520ad79ff764d5ff7
ms.contentlocale: fr-fr
ms.lasthandoff: 05/23/2017


---
# <a name="statically-compiled-queries-linq-to-xml-visual-basic"></a><span data-ttu-id="001d8-102">Compilé statiquement des requêtes (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="001d8-102">Statically Compiled Queries (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="001d8-103">Un des performances plus importants avantages de LINQ to XML, par opposition à <xref:System.Xml.XmlDocument>, sont que les requêtes dans LINQ to XML sont compilées statiquement, tandis que les requêtes XPath doivent être interprétés au moment de l’exécution.</xref:System.Xml.XmlDocument></span><span class="sxs-lookup"><span data-stu-id="001d8-103">One of the most important performance benefits LINQ to XML, as opposed to <xref:System.Xml.XmlDocument>, is that queries in LINQ to XML are statically compiled, whereas XPath queries must be interpreted at run time.</span></span> <span data-ttu-id="001d8-104">Cette fonctionnalité étant intégrée dans LINQ to XML, vous n’avez pas à effectuer d’étapes supplémentaires pour en bénéficier, mais il est utile de comprendre cette distinction pour pouvoir choisir entre ces deux technologies.</span><span class="sxs-lookup"><span data-stu-id="001d8-104">This feature is built in to LINQ to XML, so you do not have to perform extra steps to take advantage of it, but it is helpful to understand the distinction when choosing between the two technologies.</span></span> <span data-ttu-id="001d8-105">Cette rubrique explique en quoi consiste la différence.</span><span class="sxs-lookup"><span data-stu-id="001d8-105">This topic explains the difference.</span></span>  
  
## <a name="statically-compiled-queries-vs-xpath"></a><span data-ttu-id="001d8-106">Requêtes compilées statiquement et XPath</span><span class="sxs-lookup"><span data-stu-id="001d8-106">Statically Compiled Queries vs. XPath</span></span>  
 <span data-ttu-id="001d8-107">L'exemple suivant montre comment obtenir les éléments descendants avec un nom spécifié et avec un attribut avec une valeur spécifiée.</span><span class="sxs-lookup"><span data-stu-id="001d8-107">The following example shows how to get the descendant elements with a specified name, and with an attribute with a specified value.</span></span>  
  
 <span data-ttu-id="001d8-108">L'expression XPath équivalente est indiquée ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="001d8-108">The following is the equivalent XPath expression:</span></span>  
  
```  
//Address[@Type='Shipping']  
```  
  
```vb  
Dim po = XDocument.Load("PurchaseOrders.xml")  
  
Dim list1 = From el In po.Descendants("Address")  
            Where el.@Type = "Shipping"  
  
For Each el In list1  
    Console.WriteLine(el)  
Next  
```  
  
 <span data-ttu-id="001d8-109">L'expression de requête contenue dans cet exemple est réécrite par le compilateur en syntaxe de requête fondée sur une méthode.</span><span class="sxs-lookup"><span data-stu-id="001d8-109">The query expression in this example is re-written by the compiler to method-based query syntax.</span></span> <span data-ttu-id="001d8-110">L'exemple suivant, qui est écrit dans la syntaxe de requête fondée sur une méthode, produit les mêmes résultats que l'exemple précédent :</span><span class="sxs-lookup"><span data-stu-id="001d8-110">The following example, which is written in method-based query syntax, produces the same results as the previous one:</span></span>  
  
```vb  
Dim po = XDocument.Load("PurchaseOrders.xml")  
  
Dim list1 As IEnumerable(Of XElement) = po.Descendants("Address").Where(Function(el) el.@Type = "Shipping")  
  
For Each el In list1  
    Console.WriteLine(el)  
Next   
```  
  
 <span data-ttu-id="001d8-111">Le <xref:System.Linq.Enumerable.Where%2A>méthode est une méthode d’extension.</xref:System.Linq.Enumerable.Where%2A></span><span class="sxs-lookup"><span data-stu-id="001d8-111">The <xref:System.Linq.Enumerable.Where%2A> method is an extension method.</span></span> <span data-ttu-id="001d8-112">Pour plus d’informations, consultez [les méthodes d’Extension](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="001d8-112">For more information, see [Extension Methods](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md).</span></span> <span data-ttu-id="001d8-113">Étant donné que <xref:System.Linq.Enumerable.Where%2A>est une méthode d’extension, la requête ci-dessus est compilée comme si elle était écrite comme suit :</xref:System.Linq.Enumerable.Where%2A></span><span class="sxs-lookup"><span data-stu-id="001d8-113">Because <xref:System.Linq.Enumerable.Where%2A> is an extension method, the query above is compiled as though it were written as follows:</span></span>  
  
```vb  
Dim po = XDocument.Load("PurchaseOrders.xml")  
  
Dim list1 = Enumerable.Where(po.Descendants("Address"), Function(el) el.@Type = "Shipping")  
  
For Each el In list1  
    Console.WriteLine(el)  
Next  
```  
  
 <span data-ttu-id="001d8-114">Cet exemple produit exactement les mêmes résultats que les deux exemples précédents.</span><span class="sxs-lookup"><span data-stu-id="001d8-114">This example produces exactly the same results as the previous two examples.</span></span> <span data-ttu-id="001d8-115">Ceci illustre le fait que les requêtes sont effectivement compilées en appels de méthodes liés statiquement.</span><span class="sxs-lookup"><span data-stu-id="001d8-115">This illustrates the fact that queries are effectively compiled into statically linked method calls.</span></span> <span data-ttu-id="001d8-116">Ceci, combiné à la sémantique d'exécution différée des itérateurs, améliore la performance.</span><span class="sxs-lookup"><span data-stu-id="001d8-116">This, combined with the deferred execution semantics of iterators, improves performance.</span></span> <span data-ttu-id="001d8-117">Pour plus d’informations sur la sémantique d’exécution différée des itérateurs, consultez [l’exécution différée et évaluation différées dans LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="001d8-117">For more information about the deferred execution semantics of iterators, see [Deferred Execution and Lazy Evaluation in LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="001d8-118">Ces exemples sont représentatifs du code susceptible d'être écrit par le compilateur.</span><span class="sxs-lookup"><span data-stu-id="001d8-118">These examples are representative of the code that the compiler might write.</span></span> <span data-ttu-id="001d8-119">L'implémentation réelle peut différer légèrement de ces exemples, mais la performance sera identique ou similaire à celle de ces exemples.</span><span class="sxs-lookup"><span data-stu-id="001d8-119">The actual implementation might differ slightly from these examples, but the performance will be the same or similar to these examples.</span></span>  
  
## <a name="executing-xpath-expressions-with-xmldocument"></a><span data-ttu-id="001d8-120">Exécution d’expressions XPath avec XmlDocument</span><span class="sxs-lookup"><span data-stu-id="001d8-120">Executing XPath Expressions with XmlDocument</span></span>  
 <span data-ttu-id="001d8-121">L’exemple suivant utilise <xref:System.Xml.XmlDocument>pour obtenir les mêmes résultats que les exemples précédents :</xref:System.Xml.XmlDocument></span><span class="sxs-lookup"><span data-stu-id="001d8-121">The following example uses <xref:System.Xml.XmlDocument> to accomplish the same results as the previous examples:</span></span>  
  
```vb  
Dim reader = Xml.XmlReader.Create("PurchaseOrders.xml")  
Dim doc As New Xml.XmlDocument()  
doc.Load(reader)  
Dim nl As Xml.XmlNodeList = doc.SelectNodes(".//Address[@Type='Shipping']")  
For Each n As Xml.XmlNode In nl  
    Console.WriteLine(n.OuterXml)  
Next  
reader.Close()  
```  
  
 <span data-ttu-id="001d8-122">Cette requête renvoie le même résultat que les exemples qui utilisent LINQ to XML ; la seule différence est que LINQ to XML met en retrait le XML imprimé, tandis que <xref:System.Xml.XmlDocument>ne.</xref:System.Xml.XmlDocument></span><span class="sxs-lookup"><span data-stu-id="001d8-122">This query returns the same output as the examples that use LINQ to XML; the only difference is that LINQ to XML indents the printed XML, whereas <xref:System.Xml.XmlDocument> does not.</span></span>  
  
 <span data-ttu-id="001d8-123">Toutefois, les <xref:System.Xml.XmlDocument>approche généralement n’exécute pas et LINQ to XML, car la <xref:System.Xml.XmlNode.SelectNodes%2A>méthode procédez comme suit en interne chaque fois qu’elle est appelée :</xref:System.Xml.XmlNode.SelectNodes%2A> </xref:System.Xml.XmlDocument></span><span class="sxs-lookup"><span data-stu-id="001d8-123">However, the <xref:System.Xml.XmlDocument> approach generally does not perform as well as LINQ to XML, because the <xref:System.Xml.XmlNode.SelectNodes%2A> method must do the following internally every time it is called:</span></span>  
  
-   <span data-ttu-id="001d8-124">Elle analyse la chaîne qui contient l’expression XPath, en scindant la chaîne en jetons.</span><span class="sxs-lookup"><span data-stu-id="001d8-124">It parses the string that contains the XPath expression, breaking the string into tokens.</span></span>  
  
-   <span data-ttu-id="001d8-125">Elle valide les jetons pour s'assurer que l'expression XPath est valide.</span><span class="sxs-lookup"><span data-stu-id="001d8-125">It validates the tokens to make sure that the XPath expression is valid.</span></span>  
  
-   <span data-ttu-id="001d8-126">Elle traduit l'expression en arborescence d'expression interne.</span><span class="sxs-lookup"><span data-stu-id="001d8-126">It translates the expression into an internal expression tree.</span></span>  
  
-   <span data-ttu-id="001d8-127">Elle effectue l'itération sur les nœuds, en sélectionnant de façon appropriée les nœuds pour le jeu de résultats basé sur l'évaluation de l'expression.</span><span class="sxs-lookup"><span data-stu-id="001d8-127">It iterates through the nodes, appropriately selecting the nodes for the result set based on the evaluation of the expression.</span></span>  
  
 <span data-ttu-id="001d8-128">Ces opérations représentent un travail considérablement plus important que celui effectué par la requête LINQ to XML correspondant.</span><span class="sxs-lookup"><span data-stu-id="001d8-128">This is significantly more than the work done by the corresponding LINQ to XML query.</span></span> <span data-ttu-id="001d8-129">La différence de performance spécifique varie selon les différents types de requêtes, mais en général les requêtes LINQ to XML effectuent moins de tâches et par conséquent plus performant, que l’évaluation des expressions XPath à l’aide de <xref:System.Xml.XmlDocument>.</xref:System.Xml.XmlDocument></span><span class="sxs-lookup"><span data-stu-id="001d8-129">The specific performance difference varies for different types of queries, but in general LINQ to XML queries do less work, and therefore perform better, than evaluating XPath expressions using <xref:System.Xml.XmlDocument>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="001d8-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="001d8-130">See Also</span></span>  
 [<span data-ttu-id="001d8-131">Performances (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="001d8-131">Performance (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/performance-linq-to-xml.md)

