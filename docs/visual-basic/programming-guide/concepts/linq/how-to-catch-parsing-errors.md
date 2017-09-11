---
title: "Comment : intercepter des erreurs (Visual Basic) d’analyse | Documents Microsoft"
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
ms.assetid: 22e9068e-ea58-447b-816e-cd1852c11787
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 6065bb7656151392e4a5b7ad1078706284ba5616
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-catch-parsing-errors-visual-basic"></a><span data-ttu-id="60637-102">Comment : intercepter des erreurs (Visual Basic) d’analyse</span><span class="sxs-lookup"><span data-stu-id="60637-102">How to: Catch Parsing Errors (Visual Basic)</span></span>
<span data-ttu-id="60637-103">Cette rubrique montre comment détecter du code XML incorrect ou non valide.</span><span class="sxs-lookup"><span data-stu-id="60637-103">This topic shows how to detect badly formed or invalid XML.</span></span>  
  
 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]<span data-ttu-id="60637-104">est implémenté à l’aide de <xref:System.Xml.XmlReader>.</xref:System.Xml.XmlReader></span><span class="sxs-lookup"><span data-stu-id="60637-104"> is implemented using <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="60637-105">Si le code XML incorrect ou non valide est passé à [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)], sous-jacent <xref:System.Xml.XmlReader>classe lève une exception.</xref:System.Xml.XmlReader></span><span class="sxs-lookup"><span data-stu-id="60637-105">If badly formed or invalid XML is passed to [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)], the underlying <xref:System.Xml.XmlReader> class will throw an exception.</span></span> <span data-ttu-id="60637-106">Les différentes méthodes qui analysent du code XML, tel que <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=fullName>, n’interceptez pas l’exception, l’exception peut alors être interceptée par votre application.</xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="60637-106">The various methods that parse XML, such as <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=fullName>, do not catch the exception; the exception can then be caught by your application.</span></span>  
  
 <span data-ttu-id="60637-107">Notez que vous ne pouvez pas obtenir d'erreurs d'analyse si vous utilisez des littéraux XML.</span><span class="sxs-lookup"><span data-stu-id="60637-107">Note that you cannot get parse errors if you use XML literals.</span></span> <span data-ttu-id="60637-108">Le compilateur Visual Basic intercepte les erreurs de code XML incorrect ou non valide.</span><span class="sxs-lookup"><span data-stu-id="60637-108">The Visual Basic compiler will catch errors of badly formed or invalid XML.</span></span>  
  
## <a name="example"></a><span data-ttu-id="60637-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="60637-109">Example</span></span>  
 <span data-ttu-id="60637-110">Le code suivant tente d'analyser du code XML non valide :</span><span class="sxs-lookup"><span data-stu-id="60637-110">The following code tries to parse invalid XML:</span></span>  
  
```vb  
Try  
    Dim contacts As XElement = XElement.Parse("<Contacts>" & vbCrLf & _  
        "    <Contact>" & vbCrLf & _  
        "        <Name>Jim Wilson</Name>" & vbCrLf & _  
        "    </Contact>" & vbCrLf & _  
        "</Contcts>")  
  
    Console.WriteLine(contacts)  
Catch e As System.Xml.XmlException  
    Console.WriteLine(e.Message)  
End Try  
```  
  
 <span data-ttu-id="60637-111">Lorsque vous exécutez ce code, l'exception suivante est levée :</span><span class="sxs-lookup"><span data-stu-id="60637-111">When you run this code, it throws the following exception:</span></span>  
  
```  
The 'Contacts' start tag on line 1 does not match the end tag of 'Contcts'. Line 5, position 13.  
```  
  
 <span data-ttu-id="60637-112">Pour plus d’informations sur les exceptions que vous pouvez attendre la <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=fullName>, <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=fullName>, <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=fullName>, et <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=fullName>méthodes lever, consultez la <xref:System.Xml.XmlReader>documentation.</xref:System.Xml.XmlReader> </xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=fullName> </xref:System.Xml.Linq.XElement.Load%2A?displayProperty=fullName> </xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=fullName> </xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="60637-112">For information about the exceptions that you can expect the <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=fullName>, <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=fullName>, <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=fullName>, and <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=fullName> methods to throw, see the <xref:System.Xml.XmlReader> documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60637-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="60637-113">See Also</span></span>  
 [<span data-ttu-id="60637-114">L’analyse XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="60637-114">Parsing XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)
