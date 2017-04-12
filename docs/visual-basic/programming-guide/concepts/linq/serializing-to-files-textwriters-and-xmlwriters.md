---
title: "Sérialisation vers des fichiers, TextWriters et XmlWriters3 | Documents Microsoft"
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
ms.assetid: 7a0c24df-79ef-41a0-87f5-e6cf79382da9
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
ms.openlocfilehash: 98662b8d84459ed051d048084c2755fa7aaf8247
ms.lasthandoff: 03/13/2017

---
# <a name="serializing-to-files-textwriters-and-xmlwriters"></a>Sérialisation vers des fichiers, TextWriters et XmlWriters
Vous pouvez sérialiser des arborescences XML vers un <xref:System.IO.File>, un <xref:System.IO.TextWriter>, ou un <xref:System.Xml.XmlWriter>.</xref:System.Xml.XmlWriter> </xref:System.IO.TextWriter> </xref:System.IO.File>  
  
 Vous pouvez sérialiser n’importe quel composant XML, y compris <xref:System.Xml.Linq.XDocument>et <xref:System.Xml.Linq.XElement>, en une chaîne à l’aide de la `ToString` méthode.</xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XDocument>  
  
 Si vous souhaitez supprimer la mise en forme lors de la sérialisation vers une chaîne, vous pouvez utiliser la <xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=fullName>méthode.</xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=fullName>  
  
 Comportement Thedefault lors de la sérialisation vers un fichier consiste à mettre en forme (en retrait) le code XML résultant document. Lorsque vous mettez en retrait, les espaces blancs non significatifs dans l’arborescence XML ne sont pas conservés. Pour sérialiser avec mise en forme, utilisez une des surcharges des méthodes suivantes qui ne prennent pas <xref:System.Xml.Linq.SaveOptions>en tant qu’argument :</xref:System.Xml.Linq.SaveOptions>  
  
-   <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=fullName></xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=fullName>  
  
-   <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.Save%2A?displayProperty=fullName>  
  
 Si vous souhaitez que l’option ne pas pour mettre en retrait et de conserver les espaces non significatifs dans l’arborescence XML, utilisez une des surcharges des méthodes suivantes qui prennent <xref:System.Xml.Linq.SaveOptions>en tant qu’argument :</xref:System.Xml.Linq.SaveOptions>  
  
-   <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=fullName></xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=fullName>  
  
-   <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.Save%2A?displayProperty=fullName>  
  
 Pour obtenir des exemples, consultez la rubrique de référence appropriée.  
  
## <a name="see-also"></a>Voir aussi  
 [Sérialisation d’arborescences XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/serializing-xml-trees.md)
