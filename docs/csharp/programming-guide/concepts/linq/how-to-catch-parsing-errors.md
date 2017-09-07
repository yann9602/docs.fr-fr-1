---
title: "Guide pratique pour intercepter les erreurs d’analyse (C#)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: bfb612d4-5605-48ef-8c93-915cf9d5dcfb
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 240bc9770475bdf7b6da2102bd8b552a0991eea6
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-catch-parsing-errors-c"></a>Guide pratique pour intercepter les erreurs d’analyse (C#)
Cette rubrique montre comment détecter du code XML incorrect ou non valide.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] est implémenté avec <xref:System.Xml.XmlReader>. Si du code XML incorrect ou non valide est passé à [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], la classe sous-jacente <xref:System.Xml.XmlReader> ève une exception. Les différentes méthodes qui analysent le code XML, telles que <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=fullName>, n’interceptent pas l’exception. Celle-ci peut donc être interceptée par votre application.  
  
## <a name="example"></a>Exemple  
 Le code suivant tente d'analyser du code XML non valide :  
  
```csharp  
try {  
    XElement contacts = XElement.Parse(  
        @"<Contacts>  
            <Contact>  
                <Name>Jim Wilson</Name>  
            </Contact>  
          </Contcts>");  
  
    Console.WriteLine(contacts);  
}  
catch (System.Xml.XmlException e)  
{  
    Console.WriteLine(e.Message);  
}  
```  
  
 Lorsque vous exécutez ce code, l'exception suivante est levée :  
  
```  
The 'Contacts' start tag on line 1 does not match the end tag of 'Contcts'. Line 5, position 13.  
```  
  
 Pour plus d'informations sur les exceptions que les méthodes <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=fullName>, <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=fullName>, <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=fullName> et <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=fullName> peuvent lever, consultez la documentation <xref:System.Xml.XmlReader>.  
  
## <a name="see-also"></a>Voir aussi  
 [Analyse de code XML (C#)](../../../../csharp/programming-guide/concepts/linq/parsing-xml.md)

