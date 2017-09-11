---
title: "Préatomisation des objets XName (LINQ to XML) (Visual Basic) | Documents Microsoft"
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
ms.assetid: 06ea104b-f44c-4bb2-9c34-889ae025c80d
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 4871fab18d04ce9d715299fd06138c493e666466
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017


---
# <a name="pre-atomization-of-xname-objects-linq-to-xml-visual-basic"></a><span data-ttu-id="e496e-102">Préatomisation des objets XName (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e496e-102">Pre-Atomization of XName Objects (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="e496e-103">Pour améliorer les performances dans LINQ to XML est de préatomiser <xref:System.Xml.Linq.XName>objets.</xref:System.Xml.Linq.XName></span><span class="sxs-lookup"><span data-stu-id="e496e-103">One way to improve performance in LINQ to XML is to pre-atomize <xref:System.Xml.Linq.XName> objects.</span></span> <span data-ttu-id="e496e-104">Préatomisation signifie que vous affectez une chaîne à un <xref:System.Xml.Linq.XName>de l’objet avant de créer l’arborescence XML à l’aide des constructeurs de la <xref:System.Xml.Linq.XElement>et <xref:System.Xml.Linq.XAttribute>classes.</xref:System.Xml.Linq.XAttribute> </xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XName></span><span class="sxs-lookup"><span data-stu-id="e496e-104">Pre-atomization means that you assign a string to an <xref:System.Xml.Linq.XName> object before you create the XML tree by using the constructors of the <xref:System.Xml.Linq.XElement> and  <xref:System.Xml.Linq.XAttribute> classes.</span></span> <span data-ttu-id="e496e-105">Ensuite, au lieu de transmettre une chaîne au constructeur, ce qui utiliserait la conversion implicite d’une chaîne en <xref:System.Xml.Linq.XName>, vous passez l’initialisé <xref:System.Xml.Linq.XName>objet.</xref:System.Xml.Linq.XName> </xref:System.Xml.Linq.XName></span><span class="sxs-lookup"><span data-stu-id="e496e-105">Then, instead of passing a string to the constructor, which would use the implicit conversion from string to <xref:System.Xml.Linq.XName>, you pass the initialized <xref:System.Xml.Linq.XName> object.</span></span>  
  
 <span data-ttu-id="e496e-106">Ceci améliore la performance lorsque vous créez une grande arborescence XML dans laquelle des noms spécifiques sont répétés.</span><span class="sxs-lookup"><span data-stu-id="e496e-106">This improves performance when you create a large XML tree in which specific names are repeated.</span></span> <span data-ttu-id="e496e-107">Pour ce faire, vous déclarez et initialisez <xref:System.Xml.Linq.XName>objets avant de construire l’arborescence XML, puis utiliser le <xref:System.Xml.Linq.XName>objets au lieu de spécifier des chaînes pour les noms d’élément et d’attribut.</xref:System.Xml.Linq.XName> </xref:System.Xml.Linq.XName></span><span class="sxs-lookup"><span data-stu-id="e496e-107">To do this, you declare and initialize <xref:System.Xml.Linq.XName> objects before you construct the XML tree, and then use the <xref:System.Xml.Linq.XName> objects instead of specifying strings for the element and attribute names.</span></span> <span data-ttu-id="e496e-108">Cette technique peut apporter une amélioration significative de la performance si vous créez un grand nombre d'éléments (ou d'attributs) avec le même nom.</span><span class="sxs-lookup"><span data-stu-id="e496e-108">This technique can yield significant performance gains if you are creating a large number of elements (or attributes) with the same name.</span></span>  
  
 <span data-ttu-id="e496e-109">Vous devez tester la préatomisation avec votre scénario pour décider si vous devez l'utiliser.</span><span class="sxs-lookup"><span data-stu-id="e496e-109">You should test pre-atomization with your scenario to decide if you should use it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e496e-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="e496e-110">Example</span></span>  
 <span data-ttu-id="e496e-111">Cela est illustré par l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="e496e-111">The following example demonstrates this.</span></span>  
  
```vb  
Dim Root__1 As XName = "Root"  
Dim Data As XName = "Data"  
Dim ID As XName = "ID"  
  
Dim root__2 As New XElement(Root__1, New XElement(Data, New XAttribute(ID, "1"), "4,100,000"), New XElement(Data, New XAttribute(ID, "2"), "3,700,000"), New XElement(Data, New XAttribute(ID, "3"), "1,150,000"))  
  
Console.WriteLine(root__2)  
```  
  
 <span data-ttu-id="e496e-112">Cet exemple génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="e496e-112">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Data ID="1">4,100,000</Data>  
  <Data ID="2">3,700,000</Data>  
  <Data ID="3">1,150,000</Data>  
</Root>  
```  
  
 <span data-ttu-id="e496e-113">L'exemple suivant illustre la même technique dans laquelle le document XML est dans un espace de noms :</span><span class="sxs-lookup"><span data-stu-id="e496e-113">The following example shows the same technique where the XML document is in a namespace:</span></span>  
  
```vb  
Dim aw As XNamespace = "http://www.adventure-works.com"  
Dim Root__1 As XName = aw + "Root"  
Dim Data As XName = aw + "Data"  
Dim ID As XName = "ID"  
  
Dim root__2 As New XElement(Root__1, New XAttribute(XNamespace.Xmlns + "aw", aw), New XElement(Data, New XAttribute(ID, "1"), "4,100,000"), New XElement(Data, New XAttribute(ID, "2"), "3,700,000"), New XElement(Data, New XAttribute(ID, "3"), "1,150,000"))  
  
Console.WriteLine(root__2)  
```  
  
 <span data-ttu-id="e496e-114">Cet exemple génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="e496e-114">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com">  
  <aw:Data ID="1">4,100,000</aw:Data>  
  <aw:Data ID="2">3,700,000</aw:Data>  
  <aw:Data ID="3">1,150,000</aw:Data>  
</aw:Root>  
```  
  
 <span data-ttu-id="e496e-115">L'exemple suivant reflète mieux la situation que vous êtes susceptible de rencontrer dans le monde réel.</span><span class="sxs-lookup"><span data-stu-id="e496e-115">The following example is more similar to what you will likely encounter in the real world.</span></span> <span data-ttu-id="e496e-116">Dans cet exemple, le contenu de l'élément est fourni par une requête :</span><span class="sxs-lookup"><span data-stu-id="e496e-116">In this example, the content of the element is supplied by a query:</span></span>  
  
```vb  
Dim Root__1 As XName = "Root"  
Dim Data As XName = "Data"  
Dim ID As XName = "ID"  
  
Dim t1 As DateTime = DateTime.Now  
Dim root__2 As New XElement(Root__1, From i In System.Linq.Enumerable.Range(1, 100000)New XElement(Data, New XAttribute(ID, i), i * 5))  
Dim t2 As DateTime = DateTime.Now  
  
Console.WriteLine("Time to construct:{0}", t2 - t1)  
```  
  
 <span data-ttu-id="e496e-117">L'exemple suivant produit une meilleure performance que l'exemple précédent, dans lequel les noms ne sont pas préatomisés :</span><span class="sxs-lookup"><span data-stu-id="e496e-117">The previous example performs better than the following example, in which names are not pre-atomized:</span></span>  
  
```vb  
Dim t1 As DateTime = DateTime.Now  
Dim root As New XElement("Root", From i In System.Linq.Enumerable.Range(1, 100000)New XElement("Data", New XAttribute("ID", i), i * 5))  
Dim t2 As DateTime = DateTime.Now  
  
Console.WriteLine("Time to construct:{0}", t2 - t1)  
```  
  
## <a name="see-also"></a><span data-ttu-id="e496e-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e496e-118">See Also</span></span>  
 <span data-ttu-id="e496e-119">[Performances (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/performance-linq-to-xml.md) </span><span class="sxs-lookup"><span data-stu-id="e496e-119">[Performance (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/performance-linq-to-xml.md) </span></span>  
<span data-ttu-id="e496e-120"> [L’atomisation XName et XNamespace atomisés (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/atomized-xname-and-xnamespace-objects-linq-to-xml.md)</span><span class="sxs-lookup"><span data-stu-id="e496e-120"> [Atomized XName and XNamespace Objects (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/atomized-xname-and-xnamespace-objects-linq-to-xml.md)</span></span>
