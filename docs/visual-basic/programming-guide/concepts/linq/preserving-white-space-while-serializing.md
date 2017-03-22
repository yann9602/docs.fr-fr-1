---
title: Conservation des espaces lors Serializing2 | Documents Microsoft
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
ms.assetid: 2d7abbd4-37f4-422b-89dd-0a694b5edc17
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 9efa2940af9321401e7f9c01d6fb9d1f48616711
ms.lasthandoff: 03/13/2017

---
# <a name="preserving-white-space-while-serializing"></a>Conservation des espaces blancs lors de la sérialisation
Cette rubrique décrit comment contrôler les espaces blancs lors de la sérialisation d'une arborescence XML.  
  
 Un scénario courant consiste à lire le code XML mis en retrait, à créer une arborescence XML en mémoire sans nœuds d'espaces (autrement dit, ne pas conserver les espaces), à effectuer certaines opérations sur le code XML, puis à enregistrer le code XML avec mise en retrait. Lorsque vous sérialisez le code XML avec mise en forme, seuls les espaces significatifs dans l'arborescence XML sont conservés. Il s'agit du comportement par défaut pour [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].  
  
 Un autre scénario courant consiste à lire et à modifier du code XML qui a déjà été intentionnellement mis en retrait. Vous ne souhaiterez peut-être modifier cette mise en retrait en aucune manière. Pour ce faire dans [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)], vous devez conserver les espaces lorsque vous chargez ou analysez le code XML et que vous désactivez la mise en forme lors de la sérialisation du code XML.  
  
## <a name="white-space-behavior-of-methods-that-serialize-xml-trees"></a>Comportement d'espace blanc des méthodes qui sérialisent des arborescences XML  
 Les méthodes suivantes dans le <xref:System.Xml.Linq.XElement>et <xref:System.Xml.Linq.XDocument>classes sérialisent une arborescence XML.</xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XElement> Vous pouvez sérialiser une arborescence XML dans un fichier, un <xref:System.IO.TextReader>, ou un <xref:System.Xml.XmlReader>.</xref:System.Xml.XmlReader> </xref:System.IO.TextReader> La méthode `ToString` sérialise vers une chaîne.  
  
-   <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.Save%2A?displayProperty=fullName>  
  
-   <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=fullName></xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=fullName>  
  
-   <xref:System.Xml.Linq.XElement.ToString%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.ToString%2A?displayProperty=fullName>  
  
-   <xref:System.Xml.Linq.XDocument.ToString%2A?displayProperty=fullName></xref:System.Xml.Linq.XDocument.ToString%2A?displayProperty=fullName>  
  
 Si la méthode ne prend pas <xref:System.Xml.Linq.SaveOptions>en tant qu’argument, la méthode formatera (en retrait) le code XML sérialisé.</xref:System.Xml.Linq.SaveOptions> Dans ce cas, tous les espaces blancs non significatifs dans l'arborescence XML seront ignorés.  
  
 Si la méthode prend <xref:System.Xml.Linq.SaveOptions>en tant qu’argument, vous pouvez spécifier que la méthode pas mettre en forme (en retrait) le code XML sérialisé.</xref:System.Xml.Linq.SaveOptions> Dans ce cas, tous les espaces blancs dans l’arborescence XML seront conservés.  
  
## <a name="see-also"></a>Voir aussi  
 [Sérialisation d’arborescences XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/serializing-xml-trees.md)
