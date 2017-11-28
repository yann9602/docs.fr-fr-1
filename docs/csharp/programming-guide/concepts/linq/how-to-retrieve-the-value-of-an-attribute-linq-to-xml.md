---
title: "Guide pratique pour récupérer la valeur d’un attribut (LINQ to XML) (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 817bbe89-5979-4234-bf0c-46f63692ac8c
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 12720ca8bd1937d37f8d30400e0b25afa22a40cc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-retrieve-the-value-of-an-attribute-linq-to-xml-c"></a><span data-ttu-id="b01b8-102">Guide pratique pour récupérer la valeur d’un attribut (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="b01b8-102">How to: Retrieve the Value of an Attribute (LINQ to XML) (C#)</span></span>
<span data-ttu-id="b01b8-103">Cette rubrique montre comment obtenir la valeur d'attributs.</span><span class="sxs-lookup"><span data-stu-id="b01b8-103">This topic shows how to obtain the value of attributes.</span></span> <span data-ttu-id="b01b8-104">Vous pouvez procéder de deux manières : tout d'abord, vous pouvez convertir un objet <xref:System.Xml.Linq.XAttribute> vers le type souhaité ; l'opérateur de conversion. explicite convertit alors le contenu de l'élément ou attribut vers le type spécifié.</span><span class="sxs-lookup"><span data-stu-id="b01b8-104">There are two main ways: You can cast an <xref:System.Xml.Linq.XAttribute> to the desired type; the explicit conversion operator then converts the contents of the element or attribute to the specified type.</span></span> <span data-ttu-id="b01b8-105">En guise d'alternative, vous pouvez utiliser la propriété <xref:System.Xml.Linq.XAttribute.Value%2A>.</span><span class="sxs-lookup"><span data-stu-id="b01b8-105">Alternatively, you can use the <xref:System.Xml.Linq.XAttribute.Value%2A> property.</span></span> <span data-ttu-id="b01b8-106">Toutefois, la conversion est généralement la meilleure approche.</span><span class="sxs-lookup"><span data-stu-id="b01b8-106">However, casting is generally the better approach.</span></span> <span data-ttu-id="b01b8-107">Si vous convertissez l'attribut vers un type Nullable, le code est plus simple à écrire lors de la récupération de la valeur d'un attribut qui peut exister ou ne pas exister.</span><span class="sxs-lookup"><span data-stu-id="b01b8-107">If you cast the attribute to a nullable type, the code is simpler to write when retrieving the value of an attribute that might or might not exist.</span></span> <span data-ttu-id="b01b8-108">Pour obtenir des exemples de cette technique, consultez [Guide pratique pour récupérer la valeur d’un élément (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-element-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="b01b8-108">For examples of this technique, see [How to: Retrieve the Value of an Element (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-element-linq-to-xml.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b01b8-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="b01b8-109">Example</span></span>  
 <span data-ttu-id="b01b8-110">Pour récupérer la valeur d'un attribut, il vous suffit de convertir l'objet <xref:System.Xml.Linq.XAttribute> vers le type souhaité.</span><span class="sxs-lookup"><span data-stu-id="b01b8-110">To retrieve the value of an attribute, you just cast the <xref:System.Xml.Linq.XAttribute> object to your desired type.</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
                    new XAttribute("Attr", "abcde")  
                );  
Console.WriteLine(root);  
string str = (string)root.Attribute("Attr");  
Console.WriteLine(str);  
```  
  
 <span data-ttu-id="b01b8-111">Cet exemple génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="b01b8-111">This example produces the following output:</span></span>  
  
```  
<Root Attr="abcde" />  
abcde  
```  
  
## <a name="example"></a><span data-ttu-id="b01b8-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="b01b8-112">Example</span></span>  
 <span data-ttu-id="b01b8-113">L'exemple suivant montre comment récupérer la valeur d'un attribut lorsque celui-ci se trouve dans un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="b01b8-113">The following example shows how to retrieve the value of an attribute where the attribute is in a namespace.</span></span> <span data-ttu-id="b01b8-114">Pour plus d’informations, consultez [Utilisation des espaces de noms XML (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="b01b8-114">For more information, see [Working with XML Namespaces (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = new XElement(aw + "Root",  
                    new XAttribute(aw + "Attr", "abcde")  
                );  
string str = (string)root.Attribute(aw + "Attr");  
Console.WriteLine(str);  
```  
  
 <span data-ttu-id="b01b8-115">Cet exemple génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="b01b8-115">This example produces the following output:</span></span>  
  
```  
abcde  
```  
  
## <a name="see-also"></a><span data-ttu-id="b01b8-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b01b8-116">See Also</span></span>  
 [<span data-ttu-id="b01b8-117">Axes LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="b01b8-117">LINQ to XML Axes (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes.md)
