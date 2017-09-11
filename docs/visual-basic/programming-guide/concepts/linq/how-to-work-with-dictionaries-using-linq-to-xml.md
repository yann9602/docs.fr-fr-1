---
title: "Comment : travailler avec des dictionnaires à l’aide de LINQ to XML (Visual Basic) | Documents Microsoft"
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
ms.assetid: 6cb3f969-1986-414a-b850-87418712edea
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: 14abadaf548e228244a1ff7ca72fa3896ef4eb5d
ms.openlocfilehash: 0b3b800c332ce9d3f976e0bb82dff96c2a8233b8
ms.contentlocale: fr-fr
ms.lasthandoff: 05/23/2017


---
# <a name="how-to-work-with-dictionaries-using-linq-to-xml-visual-basic"></a><span data-ttu-id="e0551-102">Comment : travailler avec des dictionnaires à l’aide de LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e0551-102">How to: Work with Dictionaries Using LINQ to XML (Visual Basic)</span></span>
<span data-ttu-id="e0551-103">Il est souvent plus pratique de convertir différentes structures de données au format XML et du format XML vers d'autres structures de données.</span><span class="sxs-lookup"><span data-stu-id="e0551-103">It is often convenient to convert varieties of data structures to XML, and XML back to other data structures.</span></span> <span data-ttu-id="e0551-104">Cette rubrique présente une implémentation spécifique de cette approche générale en convertissant un <xref:System.Collections.Generic.Dictionary%602>au format XML et inversement.</xref:System.Collections.Generic.Dictionary%602></span><span class="sxs-lookup"><span data-stu-id="e0551-104">This topic shows a specific implementation of this general approach by converting a <xref:System.Collections.Generic.Dictionary%602> to XML and back.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e0551-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="e0551-105">Example</span></span>  
 <span data-ttu-id="e0551-106">Cet exemple utilise des littéraux XML et une requête dans une expression incorporée.</span><span class="sxs-lookup"><span data-stu-id="e0551-106">This example uses XML literals and a query in an embedded expression.</span></span> <span data-ttu-id="e0551-107">La requête projette de nouveaux <xref:System.Xml.Linq.XElement>objets, puis devenir le nouveau contenu de la `Root` <xref:System.Xml.Linq.XElement>objet.</xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="e0551-107">The query projects new <xref:System.Xml.Linq.XElement> objects, which then become the new content for the `Root` <xref:System.Xml.Linq.XElement> object.</span></span>  
  
```vb  
Dim dict As Dictionary(Of String, String) = New Dictionary(Of String, String)()  
dict.Add("Child1", "Value1")  
dict.Add("Child2", "Value2")  
dict.Add("Child3", "Value3")  
dict.Add("Child4", "Value4")  
Dim root As XElement = _  
    <Root>  
        <%= From keyValue In dict _  
            Select New XElement(keyValue.Key, keyValue.Value) %>  
    </Root>  
Console.WriteLine(root)  
```  
  
 <span data-ttu-id="e0551-108">Ce code génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="e0551-108">This code produces the following output:</span></span>  
  
```xml  
          <Root>  
  <Child1>Value1</Child1>  
  <Child2>Value2</Child2>  
  <Child3>Value3</Child3>  
  <Child4>Value4</Child4>  
</Root>  
```  
  
## <a name="example"></a><span data-ttu-id="e0551-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="e0551-109">Example</span></span>  
 <span data-ttu-id="e0551-110">Le code suivant crée un dictionnaire à partir de données XML.</span><span class="sxs-lookup"><span data-stu-id="e0551-110">The following code creates a dictionary from XML.</span></span>  
  
```vb  
Dim root As XElement = _  
        <Root>  
            <Child1>Value1</Child1>  
            <Child2>Value2</Child2>  
            <Child3>Value3</Child3>  
            <Child4>Value4</Child4>  
        </Root>  
  
Dim dict As Dictionary(Of String, String) = New Dictionary(Of String, String)  
For Each el As XElement In root.Elements  
    dict.Add(el.Name.LocalName, el.Value)  
Next  
For Each str As String In dict.Keys  
    Console.WriteLine("{0}:{1}", str, dict(str))  
Next  
```  
  
 <span data-ttu-id="e0551-111">Ce code génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="e0551-111">This code produces the following output:</span></span>  
  
```  
Child1:Value1  
Child2:Value2  
Child3:Value3  
Child4:Value4  
```  
  
## <a name="see-also"></a><span data-ttu-id="e0551-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e0551-112">See Also</span></span>  
 [<span data-ttu-id="e0551-113">Projections et Transformations (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e0551-113">Projections and Transformations (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)

