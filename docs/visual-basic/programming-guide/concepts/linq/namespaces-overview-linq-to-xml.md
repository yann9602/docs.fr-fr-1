---
title: "Vue d’ensemble des espaces de noms (LINQ to XML) | Documents Microsoft"
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
ms.assetid: b8eb31fa-4b26-4acf-8050-6e705687f458
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
ms.openlocfilehash: cec2efd31c96af17ad717abaa8f4359210e99a78
ms.lasthandoff: 03/13/2017

---
# <a name="namespaces-overview-linq-to-xml"></a>Vue d'ensemble des espaces de noms (LINQ to XML)
Cette rubrique présente les espaces de noms, <xref:System.Xml.Linq.XName>classe et la <xref:System.Xml.Linq.XNamespace>classe.</xref:System.Xml.Linq.XNamespace> </xref:System.Xml.Linq.XName>  
  
## <a name="xml-names"></a>Noms XML  
 Les noms XML constituent souvent une source de complexité dans la programmation XML. Un nom XML est constitué d'un espace de noms XML (également appelé URI d'espace de noms XML) et d'un nom local. Un espace de noms XML est similaire à un espace de noms dans un programme [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)]. Il permet de qualifier de manière unique les noms d'éléments et d'attributs. Cela permet d'éviter les conflits de noms entre différentes parties d'un document XML. Lorsque vous avez déclaré un espace de noms XML, vous pouvez sélectionner un nom local qui n'exige d'être unique que dans cet espace de noms.  
  
 Un autre aspect des noms XML est XML *les préfixes d’espace de noms*. Les préfixes XML sont la cause de la plupart de la complexité des noms XML. Ces préfixes vous permettent de créer un raccourci pour un espace de noms XML, ce qui rend le document XML plus concis et plus compréhensible. Toutefois, la signification des préfixes XML dépend de leur contexte, ce qui augmente la complexité. Par exemple, le préfixe XML `aw` pourrait être associé à un espace de noms XML dans une partie d'une arborescence XML et à un espace de noms XML différent dans une autre partie de l'arborescence XML.  
  
 Lorsque vous utilisez [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] avec Visual Basic et des littéraux XML, vous devez utiliser des préfixes d’espace de noms lorsque vous travaillez avec des documents dans des espaces de noms.  
  
 Dans [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)], la classe qui représente les noms XML est <xref:System.Xml.Linq.XName>.</xref:System.Xml.Linq.XName> Les noms XML apparaissent fréquemment dans le [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] API, et chaque fois qu’un nom XML est requis, vous trouverez un <xref:System.Xml.Linq.XName>paramètre.</xref:System.Xml.Linq.XName> Toutefois, vous travaillez rarement directement avec un <xref:System.Xml.Linq.XName>.</xref:System.Xml.Linq.XName> <xref:System.Xml.Linq.XName>contient une conversion implicite de chaîne.</xref:System.Xml.Linq.XName>  
  
 Pour plus d’informations, consultez <xref:System.Xml.Linq.XNamespace>et <xref:System.Xml.Linq.XName>.</xref:System.Xml.Linq.XName> </xref:System.Xml.Linq.XNamespace>  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation des espaces de noms XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)
