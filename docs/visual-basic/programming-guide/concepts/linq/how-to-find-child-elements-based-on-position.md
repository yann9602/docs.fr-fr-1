---
title: "Comment : rechercher des éléments enfants en fonction de la Position (XPath-LINQ to XML) (Visual Basic) | Documents Microsoft"
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
ms.assetid: 6831e1db-5e97-444f-a7a1-d0a87104b005
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: 14abadaf548e228244a1ff7ca72fa3896ef4eb5d
ms.openlocfilehash: 5e42a12605eecc6633da45342ee0111dcc4b0cc1
ms.contentlocale: fr-fr
ms.lasthandoff: 05/23/2017


---
# <a name="how-to-find-child-elements-based-on-position-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="4daf8-102">Comment : rechercher des éléments enfants en fonction de la Position (XPath-LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4daf8-102">How to: Find Child Elements Based on Position (XPath-LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="4daf8-103">Parfois, vous souhaitez rechercher des éléments en fonction de leur position.</span><span class="sxs-lookup"><span data-stu-id="4daf8-103">Sometimes you want to find elements based on their position.</span></span> <span data-ttu-id="4daf8-104">Vous pourriez souhaiter rechercher le deuxième élément, ou les troisième, quatrième et cinquième éléments.</span><span class="sxs-lookup"><span data-stu-id="4daf8-104">You might want to find the second element, or you might want to find the third through the fifth element.</span></span>  
  
 <span data-ttu-id="4daf8-105">L'expression XPath est la suivante :</span><span class="sxs-lookup"><span data-stu-id="4daf8-105">The XPath expression is:</span></span>  
  
 `Test[position() >= 2 and position() <= 4]`  
  
 <span data-ttu-id="4daf8-106">Il existe deux approches pour l'écriture de cette requête [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] d'une manière différée.</span><span class="sxs-lookup"><span data-stu-id="4daf8-106">There are two approaches to writing this [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] query in a lazy way.</span></span> <span data-ttu-id="4daf8-107">Vous pouvez utiliser la <xref:System.Linq.Enumerable.Skip%2A>et <xref:System.Linq.Enumerable.Take%2A>opérateurs, ou vous pouvez utiliser la <xref:System.Linq.Enumerable.Where%2A>la surcharge qui prend un index.</xref:System.Linq.Enumerable.Where%2A> </xref:System.Linq.Enumerable.Take%2A> </xref:System.Linq.Enumerable.Skip%2A></span><span class="sxs-lookup"><span data-stu-id="4daf8-107">You can use the <xref:System.Linq.Enumerable.Skip%2A> and <xref:System.Linq.Enumerable.Take%2A> operators, or you can use the <xref:System.Linq.Enumerable.Where%2A> overload that takes an index.</span></span> <span data-ttu-id="4daf8-108">Lorsque vous utilisez la <xref:System.Linq.Enumerable.Where%2A>surcharge, vous utilisez une expression lambda qui prend deux arguments.</xref:System.Linq.Enumerable.Where%2A></span><span class="sxs-lookup"><span data-stu-id="4daf8-108">When you use the <xref:System.Linq.Enumerable.Where%2A> overload, you use a lambda expression that takes two arguments.</span></span> <span data-ttu-id="4daf8-109">L'exemple suivant illustre les deux méthodes de sélection basée sur la position.</span><span class="sxs-lookup"><span data-stu-id="4daf8-109">The following example shows both methods of selecting based on position.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4daf8-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="4daf8-110">Example</span></span>  
 <span data-ttu-id="4daf8-111">Cet exemple recherche les deuxième, troisième et quatrième éléments `Test`.</span><span class="sxs-lookup"><span data-stu-id="4daf8-111">This example finds the second through the fourth `Test` element.</span></span> <span data-ttu-id="4daf8-112">Le résultat est une collection d’éléments.</span><span class="sxs-lookup"><span data-stu-id="4daf8-112">The result is a collection of elements.</span></span>  
  
 <span data-ttu-id="4daf8-113">Cet exemple utilise le document XML suivant : [exemple de fichier XML : Configuration Test (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-test-configuration-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="4daf8-113">This example uses the following XML document: [Sample XML File: Test Configuration (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-test-configuration-linq-to-xml.md).</span></span>  
  
```vb  
Dim testCfg As XElement = XElement.Load("TestConfig.xml")  
  
' LINQ to XML query  
Dim list1 As IEnumerable(Of XElement) = _  
    testCfg.Elements("Test").Skip(1).Take(3)  
  
'LINQ to XML query  
Dim list2 As IEnumerable(Of XElement) = _  
    testCfg.Elements("Test"). _  
    Where(Function(ByVal el, ByVal idx) idx >= 1 And idx <= 3)  
  
' XPath expression  
Dim list3 As IEnumerable(Of XElement) = _  
    testCfg.XPathSelectElements("Test[position() >= 2 and position() <= 4]")  
  
If list1.Count() = list2.Count() And _  
       list1.Count() = list3.Count() And _  
       list1.Intersect(list2).Count() = list1.Count() And _  
       list1.Intersect(list3).Count() = list1.Count() Then  
  
    Console.WriteLine("Results are identical")  
Else  
    Console.WriteLine("Results differ")  
End If  
  
For Each el As XElement In list1  
    Console.WriteLine(el)  
Next  
```  
  
 <span data-ttu-id="4daf8-114">Cet exemple génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="4daf8-114">This example produces the following output:</span></span>  
  
```  
Results are identical  
<Test TestId="0002" TestType="CMD">  
  <Name>Find succeeding characters</Name>  
  <CommandLine>Examp2.EXE</CommandLine>  
  <Input>abc</Input>  
  <Output>def</Output>  
</Test>  
<Test TestId="0003" TestType="GUI">  
  <Name>Convert multiple numbers to strings</Name>  
  <CommandLine>Examp2.EXE /Verbose</CommandLine>  
  <Input>123</Input>  
  <Output>One Two Three</Output>  
</Test>  
<Test TestId="0004" TestType="GUI">  
  <Name>Find correlated key</Name>  
  <CommandLine>Examp3.EXE</CommandLine>  
  <Input>a1</Input>  
  <Output>b1</Output>  
</Test>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4daf8-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4daf8-115">See Also</span></span>  
 [<span data-ttu-id="4daf8-116">LINQ to XML pour les utilisateurs XPath (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4daf8-116">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)

