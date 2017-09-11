---
title: "Comment : récupérer la valeur d’un attribut (LINQ to XML) (Visual Basic) | Documents Microsoft"
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
ms.assetid: 5f4b3790-c83f-4eb3-a889-e3587edf3ca1
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: a32f50ce8a92fa22d9627a1510a4b3ec1087364e
ms.openlocfilehash: 6ecc1368832b9c98efeae65c95438efb80f164f6
ms.contentlocale: fr-fr
ms.lasthandoff: 06/01/2017


---
# <a name="how-to-retrieve-the-value-of-an-attribute-linq-to-xml-visual-basic"></a><span data-ttu-id="31a93-102">Comment : récupérer la valeur d’un attribut (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="31a93-102">How to: Retrieve the Value of an Attribute (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="31a93-103">Cette rubrique montre comment obtenir la valeur d'attributs.</span><span class="sxs-lookup"><span data-stu-id="31a93-103">This topic shows how to obtain the value of attributes.</span></span> <span data-ttu-id="31a93-104">Il existe deux façons : vous pouvez convertir un <xref:System.Xml.Linq.XAttribute>vers le type souhaité ; l’opérateur de conversion explicite convertit alors le contenu de l’élément ou attribut dans le type spécifié.</xref:System.Xml.Linq.XAttribute></span><span class="sxs-lookup"><span data-stu-id="31a93-104">There are two main ways: You can cast an <xref:System.Xml.Linq.XAttribute> to the desired type; the explicit conversion operator then converts the contents of the element or attribute to the specified type.</span></span> <span data-ttu-id="31a93-105">Vous pouvez également utiliser le <xref:System.Xml.Linq.XAttribute.Value%2A>propriété.</xref:System.Xml.Linq.XAttribute.Value%2A></span><span class="sxs-lookup"><span data-stu-id="31a93-105">Alternatively, you can use the <xref:System.Xml.Linq.XAttribute.Value%2A> property.</span></span> <span data-ttu-id="31a93-106">Toutefois, la conversion est généralement la meilleure approche.</span><span class="sxs-lookup"><span data-stu-id="31a93-106">However, casting is generally the better approach.</span></span> <span data-ttu-id="31a93-107">Si vous convertissez l'attribut vers un type Nullable, le code est plus simple à écrire lors de la récupération de la valeur d'un attribut qui peut exister ou ne pas exister.</span><span class="sxs-lookup"><span data-stu-id="31a93-107">If you cast the attribute to a nullable type, the code is simpler to write when retrieving the value of an attribute that might or might not exist.</span></span> <span data-ttu-id="31a93-108">Pour obtenir des exemples de cette technique, consultez la page [Comment : récupérer la valeur d’un élément (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-element-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="31a93-108">For examples of this technique, see [How to: Retrieve the Value of an Element (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-element-linq-to-xml.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="31a93-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="31a93-109">Example</span></span>  
 <span data-ttu-id="31a93-110">En Visual Basic, vous pouvez utiliser la propriété d'attribut intégrée pour récupérer la valeur d'un attribut.</span><span class="sxs-lookup"><span data-stu-id="31a93-110">In Visual Basic, you can use the integrated attribute property to retrieve the value of an attribute.</span></span>  
  
```vb  
Dim root As XElement = <Root Attr="abcde"/>  
Console.WriteLine(root)  
Dim str As String = root.@Attr  
Console.WriteLine(str)  
```  
  
 <span data-ttu-id="31a93-111">Cet exemple génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="31a93-111">This example produces the following output:</span></span>  
  
```xml  
<Root Attr="abcde" />  
abcde  
```  
  
## <a name="example"></a><span data-ttu-id="31a93-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="31a93-112">Example</span></span>  
 <span data-ttu-id="31a93-113">En Visual Basic, vous pouvez utiliser la propriété d'attribut intégrée pour définir la valeur d'un attribut.</span><span class="sxs-lookup"><span data-stu-id="31a93-113">In Visual Basic, you can use the integrated attribute property to set the value of an attribute.</span></span> <span data-ttu-id="31a93-114">En outre, si vous utilisez la propriété d'attribut intégrée pour définir la valeur d'un attribut qui n'existe pas, l'attribut sera créé.</span><span class="sxs-lookup"><span data-stu-id="31a93-114">Further, if you use the integrated attribute property to set the value of an attribute that does not exist, the attribute will be created.</span></span>  
  
```vb  
Dim root As XElement = <Root Att1="content"/>  
root.@Att1 = "new content"  
root.@Att2 = "new attribute"  
Console.WriteLine(root)  
```  
  
 <span data-ttu-id="31a93-115">Cet exemple génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="31a93-115">This example produces the following output:</span></span>  
  
```xml  
<Root Att1="new content" Att2="new attribute" />  
```  
  
## <a name="example"></a><span data-ttu-id="31a93-116">Exemple</span><span class="sxs-lookup"><span data-stu-id="31a93-116">Example</span></span>  
 <span data-ttu-id="31a93-117">L'exemple suivant montre comment récupérer la valeur d'un attribut lorsque celui-ci se trouve dans un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="31a93-117">The following example shows how to retrieve the value of an attribute where the attribute is in a namespace.</span></span> <span data-ttu-id="31a93-118">Pour plus d’informations, consultez [utilisation des espaces de noms XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="31a93-118">For more information, see [Working with XML Namespaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = <aw:Root aw:Attr="abcde"/>  
        Dim str As String = root.@aw:Attr  
        Console.WriteLine(str)  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="31a93-119">Cet exemple génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="31a93-119">This example produces the following output:</span></span>  
  
```  
abcde  
```  
  
## <a name="see-also"></a><span data-ttu-id="31a93-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="31a93-120">See Also</span></span>  
 [<span data-ttu-id="31a93-121">Axes LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="31a93-121">LINQ to XML Axes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
