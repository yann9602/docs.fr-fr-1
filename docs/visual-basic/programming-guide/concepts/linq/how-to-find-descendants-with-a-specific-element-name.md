---
title: "Comment : rechercher les Descendants avec un nom d’élément spécifique (Visual Basic) | Documents Microsoft"
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
ms.assetid: 78915518-0d25-4051-ab55-929779989510
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 93b69966323b1611648a905c18dba75984b95880
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017


---
# <a name="how-to-find-descendants-with-a-specific-element-name-visual-basic"></a><span data-ttu-id="d326d-102">Comment : rechercher les Descendants avec un nom d’élément spécifique (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d326d-102">How to: Find Descendants with a Specific Element Name (Visual Basic)</span></span>
<span data-ttu-id="d326d-103">Parfois, vous souhaitez rechercher tous les descendants avec un nom particulier.</span><span class="sxs-lookup"><span data-stu-id="d326d-103">Sometimes you want to find all descendants with a particular name.</span></span> <span data-ttu-id="d326d-104">Vous pouvez écrire du code pour itérer au sein de tous les descendants, mais il est plus facile d’utiliser la <xref:System.Xml.Linq.XContainer.Descendants%2A>axe.</xref:System.Xml.Linq.XContainer.Descendants%2A></span><span class="sxs-lookup"><span data-stu-id="d326d-104">You could write code to iterate through all of the descendants, but it is easier to use the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d326d-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="d326d-105">Example</span></span>  
 <span data-ttu-id="d326d-106">L'exemple suivant montre comment rechercher des descendants en fonction du nom d'élément.</span><span class="sxs-lookup"><span data-stu-id="d326d-106">The following example shows how to find descendants based on the element name.</span></span>  
  
```vb  
Dim root As XElement = _  
    <root>  
        <para>  
            <r>  
                <t>Some text </t>  
            </r>  
            <n>  
                <r>  
                    <t>that is broken up into </t>  
                </r>  
            </n>  
            <n>  
                <r>  
                    <t>multiple segments.</t>  
                </r>  
            </n>  
        </para>  
    </root>  
  
Dim textSegs As IEnumerable(Of String) = _  
    From seg In root...<t> _  
    Select seg.Value  
  
Dim str As String = textSegs.Aggregate( _  
    New StringBuilder, _  
    Function(sb, i) sb.Append(i), _  
    Function(sb) sb.ToString)  
  
Console.WriteLine(str)  
```  
  
 <span data-ttu-id="d326d-107">Ce code génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="d326d-107">This code produces the following output:</span></span>  
  
```  
Some text that is broken up into multiple segments.  
```  
  
## <a name="example"></a><span data-ttu-id="d326d-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="d326d-108">Example</span></span>  
 <span data-ttu-id="d326d-109">L'exemple suivant illustre la même requête pour du code XML qui est dans un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="d326d-109">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="d326d-110">Pour plus d’informations, consultez [utilisation des espaces de noms XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="d326d-110">For more information, see [Working with XML Namespaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
```vb  
Imports <xmlns='http://www.adatum.com'>  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = _  
            <root>  
                <para>  
                    <r>  
                        <t>Some text </t>  
                    </r>  
                    <n>  
                        <r>  
                            <t>that is broken up into </t>  
                        </r>  
                    </n>  
                    <n>  
                        <r>  
                            <t>multiple segments.</t>  
                        </r>  
                    </n>  
                </para>  
            </root>  
  
        Dim textSegs As IEnumerable(Of String) = _  
            From seg In root...<t> _  
            Select seg.Value  
  
        Dim str As String = textSegs.Aggregate( _  
            New StringBuilder, _  
            Function(sb, i) sb.Append(i), _  
            Function(sb) sb.ToString)  
  
        Console.WriteLine(str)  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="d326d-111">Ce code génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="d326d-111">This code produces the following output:</span></span>  
  
```  
Some text that is broken up into multiple segments.  
```  
  
## <a name="see-also"></a><span data-ttu-id="d326d-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d326d-112">See Also</span></span>  
 <span data-ttu-id="d326d-113"><xref:System.Xml.Linq.XContainer.Descendants%2A></xref:System.Xml.Linq.XContainer.Descendants%2A></span><span class="sxs-lookup"><span data-stu-id="d326d-113"><xref:System.Xml.Linq.XContainer.Descendants%2A></span></span>   
<span data-ttu-id="d326d-114"> [Requêtes de base (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)</span><span class="sxs-lookup"><span data-stu-id="d326d-114"> [Basic Queries (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)</span></span>
