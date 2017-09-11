---
title: "Comment : rechercher des éléments connexes (XPath-LINQ to XML) (Visual Basic) | Documents Microsoft"
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
ms.assetid: 6b0ef058-d704-48a5-98cd-33f00d088af9
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: 14abadaf548e228244a1ff7ca72fa3896ef4eb5d
ms.openlocfilehash: e7e5bfc249e0bdeeeefd56508354ac62e5c73465
ms.contentlocale: fr-fr
ms.lasthandoff: 05/23/2017


---
# <a name="how-to-find-related-elements-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="06437-102">Comment : rechercher des éléments connexes (XPath-LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="06437-102">How to: Find Related Elements (XPath-LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="06437-103">Cette rubrique montre comment obtenir un élément en sélectionnant un attribut auquel il est fait référence par la valeur d'un autre élément.</span><span class="sxs-lookup"><span data-stu-id="06437-103">This topic shows how to get an element selecting on an attribute that is referred to by the value of another element.</span></span>  
  
 <span data-ttu-id="06437-104">L’expression XPath est la suivante :</span><span class="sxs-lookup"><span data-stu-id="06437-104">The XPath expression is:</span></span>  
  
 `.//Customer[@CustomerID=/Root/Orders/Order[12]/CustomerID]`  
  
## <a name="example"></a><span data-ttu-id="06437-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="06437-105">Example</span></span>  
 <span data-ttu-id="06437-106">Cet exemple recherche le douzième élément `Order`, puis recherche le client associé à cette commande.</span><span class="sxs-lookup"><span data-stu-id="06437-106">This example finds the 12th `Order` element, and then finds the customer for that order.</span></span>  
  
 <span data-ttu-id="06437-107">Notez que l'indexation dans une liste dans .Net est basée sur « zéro ».</span><span class="sxs-lookup"><span data-stu-id="06437-107">Note that indexing into a list in .Net is 'zero' based.</span></span> <span data-ttu-id="06437-108">L'indexation dans une collection de nœuds dans un prédicat XPath est basée sur « un ».</span><span class="sxs-lookup"><span data-stu-id="06437-108">Indexing into a collection of nodes in an XPath predicate is 'one' based.</span></span> <span data-ttu-id="06437-109">Cet exemple reflète cette différence.</span><span class="sxs-lookup"><span data-stu-id="06437-109">This example reflects this difference.</span></span>  
  
 <span data-ttu-id="06437-110">Cet exemple utilise le document XML suivant : [exemple de fichier XML : clients et commandes (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="06437-110">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md).</span></span>  
  
```vb  
Dim co As XDocument = XDocument.Load("CustomersOrders.xml")  
  
' LINQ to XML query  
Dim customer1 As XElement = ( _  
    From el In co...<Customer> _  
    Where el.@CustomerID = co.<Root>.<Orders>.<Order>. _  
        ToList()(11).<CustomerID>(0).Value _  
    Select el).First()  
  
' An alternate way to write the query that avoids creation  
' of a System.Collections.Generic.List:  
Dim customer2 As XElement = ( _  
    From el In co...<Customer> _  
    Where el.@CustomerID = co.<Root>.<Orders>.<Order>. _  
        Skip(11).First().<CustomerID>(0).Value _  
    Select el).First()  
  
' XPath expression  
Dim customer3 As XElement = co.XPathSelectElement _  
    (".//Customer[@CustomerID=/Root/Orders/Order[12]/CustomerID]")  
  
If customer1 Is customer2 And customer1 Is customer3 Then  
    Console.WriteLine("Results are identical")  
Else  
    Console.WriteLine("Results differ")  
End If  
Console.WriteLine(customer1)  
```  
  
 <span data-ttu-id="06437-111">Cet exemple génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="06437-111">This example produces the following output:</span></span>  
  
```  
Results are identical  
<Customer CustomerID="HUNGC">  
  <CompanyName>Hungry Coyote Import Store</CompanyName>  
  <ContactName>Yoshi Latimer</ContactName>  
  <ContactTitle>Sales Representative</ContactTitle>  
  <Phone>(503) 555-6874</Phone>  
  <Fax>(503) 555-2376</Fax>  
  <FullAddress>  
    <Address>City Center Plaza 516 Main St.</Address>  
    <City>Elgin</City>  
    <Region>OR</Region>  
    <PostalCode>97827</PostalCode>  
    <Country>USA</Country>  
  </FullAddress>  
</Customer>  
```  
  
## <a name="see-also"></a><span data-ttu-id="06437-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="06437-112">See Also</span></span>  
 [<span data-ttu-id="06437-113">LINQ to XML pour les utilisateurs XPath (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="06437-113">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)

