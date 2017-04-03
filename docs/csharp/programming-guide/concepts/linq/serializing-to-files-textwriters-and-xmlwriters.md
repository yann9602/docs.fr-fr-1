---
title: "Sérialisation vers des fichiers, TextWriters et XmlWriters1 | Microsoft Docs"
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
ms.assetid: bd3ea6f7-895b-4ff4-a625-fe2bb55b1886
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
ms.openlocfilehash: f61324395e81509e5800e99b654a8c669d4397f0
ms.lasthandoff: 03/13/2017

---
# <a name="serializing-to-files-textwriters-and-xmlwriters"></a>Sérialisation vers des fichiers, TextWriters et XmlWriters
Vous pouvez sérialiser des arborescences XML vers un <xref:System.IO.File>, un <xref:System.IO.TextWriter> ou un <xref:System.Xml.XmlWriter>.  
  
 Vous pouvez sérialiser n’importe quel composant XML, y compris <xref:System.Xml.Linq.XDocument> et <xref:System.Xml.Linq.XElement>, en une chaîne à l’aide de la méthode `ToString`.  
  
 Si vous souhaitez supprimer la mise en forme lors de la sérialisation vers une chaîne, vous pouvez utiliser la méthode <xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=fullName>.  
  
 Le comportement par défaut lors de la sérialisation vers un fichier consiste à mettre en forme (mettre en retrait) le document XML obtenu. Lorsque vous mettez en retrait, les espaces blancs non significatifs dans l’arborescence XML ne sont pas conservés. Pour sérialiser avec la mise en forme, utilisez l’une des surcharges des méthodes suivantes qui ne prennent pas <xref:System.Xml.Linq.SaveOptions> comme argument :  
  
-   <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=fullName>  
  
-   <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=fullName>  
  
 Si vous souhaitez avoir l’option de ne pas mettre en retrait et de conserver les espaces blancs non significatifs dans l’arborescence XML, utilisez l’une des surcharges des méthodes suivantes qui prennent <xref:System.Xml.Linq.SaveOptions> comme argument :  
  
-   <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=fullName>  
  
-   <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=fullName>  
  
 Pour obtenir des exemples, consultez la rubrique de référence appropriée.  
  
## <a name="see-also"></a>Voir aussi  
 [Sérialisation d’arborescences XML (C#)](../../../../csharp/programming-guide/concepts/linq/serializing-xml-trees.md)
