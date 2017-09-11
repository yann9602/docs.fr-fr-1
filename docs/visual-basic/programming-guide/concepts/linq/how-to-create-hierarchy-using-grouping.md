---
title: "Comment : créer la hiérarchie à l’aide de regroupement (Visual Basic) | Documents Microsoft"
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
ms.assetid: 4eb3ca6b-1aed-43de-b8b9-41c769c993f8
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 1fa84959fc90de81e7dec22d70cd524df9c09e1c
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017


---
# <a name="how-to-create-hierarchy-using-grouping-visual-basic"></a><span data-ttu-id="5eae8-102">Comment : créer la hiérarchie à l’aide de regroupement (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5eae8-102">How to: Create Hierarchy Using Grouping (Visual Basic)</span></span>
<span data-ttu-id="5eae8-103">Cet exemple montre comment grouper des données, puis générer du code XML basé sur le regroupement.</span><span class="sxs-lookup"><span data-stu-id="5eae8-103">This example shows how to group data, and then generate XML based on the grouping.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5eae8-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="5eae8-104">Example</span></span>  
 <span data-ttu-id="5eae8-105">Cet exemple groupe tout d'abord les données par catégorie, puis il génère un nouveau fichier XML dans lequel la hiérarchie XML reflète le regroupement.</span><span class="sxs-lookup"><span data-stu-id="5eae8-105">This example first groups data by a category, then generates a new XML file in which the XML hierarchy reflects the grouping.</span></span>  
  
 <span data-ttu-id="5eae8-106">Cet exemple utilise le document XML suivant : [exemple de fichier XML : données numériques (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="5eae8-106">This example uses the following XML document: [Sample XML File: Numerical Data (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).</span></span>  
  
```vb  
Dim doc As XElement = XElement.Load("Data.xml")  
Dim newData As XElement = _  
    <Root>  
        <%= _  
            From data In doc.<Data> _  
            Group By category = data.<Category>(0).Value _  
            Into groupedData = Group _  
            Select <Group ID=<%= category %>>  
                       <%= _  
                           From g In groupedData _  
                           Select _  
                           <Data>  
                               <%= g.<Quantity>(0) %>  
                               <%= g.<Price>(0) %>  
                           </Data> _  
                       %>  
                   </Group> _  
        %>  
    </Root>  
Console.WriteLine(newData)  
```  
  
 <span data-ttu-id="5eae8-107">Cet exemple génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="5eae8-107">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Group ID="A">  
    <Data>  
      <Quantity>3</Quantity>  
      <Price>24.50</Price>  
    </Data>  
    <Data>  
      <Quantity>5</Quantity>  
      <Price>4.95</Price>  
    </Data>  
    <Data>  
      <Quantity>3</Quantity>  
      <Price>66.00</Price>  
    </Data>  
    <Data>  
      <Quantity>15</Quantity>  
      <Price>29.00</Price>  
    </Data>  
  </Group>  
  <Group ID="B">  
    <Data>  
      <Quantity>1</Quantity>  
      <Price>89.99</Price>  
    </Data>  
    <Data>  
      <Quantity>10</Quantity>  
      <Price>.99</Price>  
    </Data>  
    <Data>  
      <Quantity>8</Quantity>  
      <Price>6.99</Price>  
    </Data>  
  </Group>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5eae8-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5eae8-108">See Also</span></span>  
 [<span data-ttu-id="5eae8-109">Techniques de requêtes (LINQ to XML) avancées (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5eae8-109">Advanced Query Techniques (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)
