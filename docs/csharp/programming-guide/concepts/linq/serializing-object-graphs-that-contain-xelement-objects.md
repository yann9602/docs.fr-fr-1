---
title: "Sérialisation de graphiques d’objets qui contiennent des objets XElement (C#) | Microsoft Docs"
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
ms.assetid: fcbc3951-3cc4-4d0f-9259-e97549ed68f0
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 752092f7455fa0a10efcaa41166b66ff1f87b16e
ms.lasthandoff: 03/13/2017

---
# <a name="serializing-object-graphs-that-contain-xelement-objects-c"></a>Sérialisation de graphiques d’objets qui contiennent des objets XElement (C#)
Cette rubrique présente la fonctionnalité de sérialisation de graphiques d’objets contenant des références à des objets de type <xref:System.Xml.Linq.XElement>. Afin de faciliter ce type de sérialisation, <xref:System.Xml.Linq.XElement> implémente l’interface <xref:System.Xml.Serialization.IXmlSerializable>.  
  
 Notez que seule la classe <xref:System.Xml.Linq.XElement> implémente la sérialisation.  
  
## <a name="in-this-section"></a>Dans cette section  
  
|Rubrique|Description|  
|-----------|-----------------|  
|[Guide pratique pour sérialiser à l’aide de XmlSerializer (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-serialize-using-xmlserializer.md)|Montre comment sérialiser à l’aide de <xref:System.Xml.Serialization.XmlSerializer>.|  
|[Guide pratique pour sérialiser à l’aide de DataContractSerializer (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-serialize-using-datacontractserializer.md)|Montre comment sérialiser à l’aide de <xref:System.Runtime.Serialization.DataContractSerializer>.|  
  
## <a name="see-also"></a>Voir aussi  
 [Programmation LINQ to XML avancée (C#)](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
