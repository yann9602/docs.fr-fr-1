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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 0c4ba619d1f269352b3288f6cadf3b6f37a0dc2d
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-catch-parsing-errors-visual-basic"></a>Comment : intercepter des erreurs (Visual Basic) d’analyse
Cette rubrique montre comment détecter du code XML incorrect ou non valide.  
  
 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]est implémenté à l’aide de <xref:System.Xml.XmlReader>.</xref:System.Xml.XmlReader> Si le code XML incorrect ou non valide est passé à [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)], sous-jacent <xref:System.Xml.XmlReader>classe lève une exception.</xref:System.Xml.XmlReader> Les différentes méthodes qui analysent du code XML, tel que <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=fullName>, n’interceptez pas l’exception, l’exception peut alors être interceptée par votre application.</xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=fullName>  
  
 Notez que vous ne pouvez pas obtenir d'erreurs d'analyse si vous utilisez des littéraux XML. Le compilateur Visual Basic intercepte les erreurs de code XML incorrect ou non valide.  
  
## <a name="example"></a>Exemple  
 Le code suivant tente d'analyser du code XML non valide :  
  
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
  
 Lorsque vous exécutez ce code, l'exception suivante est levée :  
  
```  
The 'Contacts' start tag on line 1 does not match the end tag of 'Contcts'. Line 5, position 13.  
```  
  
 Pour plus d’informations sur les exceptions que vous pouvez attendre la <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=fullName>, <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=fullName>, <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=fullName>, et <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=fullName>méthodes lever, consultez la <xref:System.Xml.XmlReader>documentation.</xref:System.Xml.XmlReader> </xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=fullName> </xref:System.Xml.Linq.XElement.Load%2A?displayProperty=fullName> </xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=fullName> </xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=fullName>  
  
## <a name="see-also"></a>Voir aussi  
 [L’analyse XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)
