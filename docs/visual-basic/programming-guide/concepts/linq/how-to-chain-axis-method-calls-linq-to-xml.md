---
title: "Comment : chaîner des appels de méthode d’axe (LINQ to XML) (Visual Basic) | Documents Microsoft"
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
ms.assetid: e4e22942-39bd-460f-b3c0-9f09e53d3aa9
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: a32f50ce8a92fa22d9627a1510a4b3ec1087364e
ms.openlocfilehash: 4997f7e91f968f080c22ca9d3a204c748758f832
ms.contentlocale: fr-fr
ms.lasthandoff: 06/01/2017


---
# <a name="how-to-chain-axis-method-calls-linq-to-xml-visual-basic"></a><span data-ttu-id="f6655-102">Comment : chaîner des appels de méthode d’axe (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f6655-102">How to: Chain Axis Method Calls (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="f6655-103">Un schéma courant que vous utiliserez dans votre code consiste à appeler une méthode d’axe, puis à appeler l’un des axes de méthode d’extension.</span><span class="sxs-lookup"><span data-stu-id="f6655-103">A common pattern that you will use in your code is to call an axis method, then call one of the extension method axes.</span></span>  
  
 <span data-ttu-id="f6655-104">Il existe deux axes avec le nom de `Elements` qui retournent une collection d’éléments : le <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=fullName>(méthode) et le <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=fullName>méthode.</xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=fullName> </xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="f6655-104">There are two axes with the name of `Elements` that return a collection of elements: the <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=fullName> method and the <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=fullName> method.</span></span> <span data-ttu-id="f6655-105">Vous pouvez combiner ces deux axes pour rechercher tous les éléments d’un nom spécifié à une profondeur donnée dans l’arborescence.</span><span class="sxs-lookup"><span data-stu-id="f6655-105">You can combine these two axes to find all elements of a specified name at a given depth in the tree.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f6655-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="f6655-106">Example</span></span>  
 <span data-ttu-id="f6655-107">Cet exemple utilise <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=fullName>et <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=fullName>pour rechercher tous les `Name` tous les éléments `Address` tous les éléments `PurchaseOrder` éléments.</xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=fullName> </xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="f6655-107">This example uses <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=fullName> and <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=fullName> to find all `Name` elements in all `Address` elements in all `PurchaseOrder` elements.</span></span>  
  
 <span data-ttu-id="f6655-108">Cet exemple utilise le document XML suivant : [exemple de fichier XML : plusieurs commandes fournisseur (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="f6655-108">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
```vb  
Dim purchaseOrders As XElement = XElement.Load("PurchaseOrders.xml")  
Dim names As IEnumerable(Of XElement) = _  
    From el In purchaseOrders.<PurchaseOrder>.<Address>.<Name> _  
    Select el  
For Each e As XElement In names  
    Console.WriteLine(e)  
Next  
```  
  
 <span data-ttu-id="f6655-109">Cet exemple génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="f6655-109">This example produces the following output:</span></span>  
  
```xml  
<Name>Ellen Adams</Name>  
<Name>Tai Yee</Name>  
<Name>Cristian Osorio</Name>  
<Name>Cristian Osorio</Name>  
<Name>Jessica Arnold</Name>  
<Name>Jessica Arnold</Name>  
```  
  
 <span data-ttu-id="f6655-110">Cela fonctionne car une des implémentations de la `Elements` axe est comme une méthode d’extension sur <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XContainer>.</xref:System.Xml.Linq.XContainer> </xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="f6655-110">This works because one of the implementations of the `Elements` axis is as an extension method on <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XContainer>.</span></span> <span data-ttu-id="f6655-111"><xref:System.Xml.Linq.XElement>dérive de <xref:System.Xml.Linq.XContainer>, vous pouvez appeler la <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=fullName>méthode sur les résultats d’un appel à la <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=fullName>méthode.</xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=fullName> </xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=fullName> </xref:System.Xml.Linq.XContainer></xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="f6655-111"><xref:System.Xml.Linq.XElement> derives from <xref:System.Xml.Linq.XContainer>, so you can call the <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=fullName> method on the results of a call to the <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=fullName> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f6655-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="f6655-112">Example</span></span>  
 <span data-ttu-id="f6655-113">Quelquefois, vous souhaitez récupérer tous les éléments à une profondeur d'élément spécifique lorsqu'il peut y avoir ou ne pas y avoir d'ancêtres intermédiaires.</span><span class="sxs-lookup"><span data-stu-id="f6655-113">Sometimes you want to retrieve all elements at a particular element depth when there might or might not be intervening ancestors.</span></span> <span data-ttu-id="f6655-114">Par exemple, dans le document suivant, vous pourriez souhaiter récupérer tous les éléments `ConfigParameter` qui sont des enfants de l'élément `Customer`, mais pas le `ConfigParameter` qui est un enfant de l'élément `Root`.</span><span class="sxs-lookup"><span data-stu-id="f6655-114">For example, in the following document, you might want to retrieve all the `ConfigParameter` elements that are children of the `Customer` element, but not the `ConfigParameter` that is a child of the `Root` element.</span></span>  
  
```xml  
<Root>  
  <ConfigParameter>RootConfigParameter</ConfigParameter>  
  <Customer>  
    <Name>Frank</Name>  
    <Config>  
      <ConfigParameter>FirstConfigParameter</ConfigParameter>  
    </Config>  
  </Customer>  
  <Customer>  
    <Name>Bob</Name>  
    <!--This customer doesn't have a Config element-->  
  </Customer>  
  <Customer>  
    <Name>Bill</Name>  
    <Config>  
      <ConfigParameter>SecondConfigParameter</ConfigParameter>  
    </Config>  
  </Customer>  
</Root>  
```  
  
 <span data-ttu-id="f6655-115">Pour ce faire, vous pouvez utiliser la <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=fullName>axe, comme suit :</xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="f6655-115">To do this, you can use the <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=fullName> axis, as follows:</span></span>  
  
```vb  
Dim root As XElement = XElement.Load("Irregular.xml")  
Dim configParameters As IEnumerable(Of XElement) = _  
    root.<Customer>.<Config>.<ConfigParameter>  
For Each cp As XElement In configParameters  
    Console.WriteLine(cp)  
Next  
```  
  
 <span data-ttu-id="f6655-116">Cet exemple génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="f6655-116">This example produces the following output:</span></span>  
  
```xml  
<ConfigParameter>FirstConfigParameter</ConfigParameter>  
<ConfigParameter>SecondConfigParameter</ConfigParameter>  
```  
  
## <a name="example"></a><span data-ttu-id="f6655-117">Exemple</span><span class="sxs-lookup"><span data-stu-id="f6655-117">Example</span></span>  
 <span data-ttu-id="f6655-118">L'exemple suivant illustre la même technique pour du code XML qui est dans un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="f6655-118">The following example shows the same technique for XML that is in a namespace.</span></span> <span data-ttu-id="f6655-119">Pour plus d’informations, consultez [utilisation des espaces de noms XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="f6655-119">For more information, see [Working with XML Namespaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
 <span data-ttu-id="f6655-120">Cet exemple utilise le document XML suivant : [exemple de fichier XML : plusieurs commandes fournisseur dans un Namespace](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="f6655-120">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders in a Namespace](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-in-a-namespace.md).</span></span>  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim purchaseOrders As XElement = XElement.Load("PurchaseOrdersInNamespace.xml")  
        Dim names As IEnumerable(Of XElement) = _  
            From el In purchaseOrders.<aw:PurchaseOrder>.<aw:Address>.<aw:Name> _  
            Select el  
        For Each e As XElement In names  
            Console.WriteLine(e)  
        Next  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="f6655-121">Cet exemple génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="f6655-121">This example produces the following output:</span></span>  
  
```xml  
<aw:Name xmlns:aw="http://www.adventure-works.com">Ellen Adams</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Tai Yee</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Cristian Osorio</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Cristian Osorio</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Jessica Arnold</aw:Name>  
<aw:Name xmlns:aw="http://www.adventure-works.com">Jessica Arnold</aw:Name>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f6655-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f6655-122">See Also</span></span>  
 [<span data-ttu-id="f6655-123">Axes LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f6655-123">LINQ to XML Axes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
