---
title: "Vue d’ensemble des espaces de noms (LINQ to XML) | Microsoft Docs"
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
ms.assetid: 16283322-8238-4918-ab11-802ac6748eb7
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
ms.openlocfilehash: 73eb9d0808666238e55abdf53888ec0f9b501fe2
ms.lasthandoff: 03/13/2017

---
# <a name="namespaces-overview-linq-to-xml"></a>Vue d'ensemble des espaces de noms (LINQ to XML)
Cette rubrique présente les espaces de noms, la classe <xref:System.Xml.Linq.XName> et la classe <xref:System.Xml.Linq.XNamespace>.  
  
## <a name="xml-names"></a>Noms XML  
 Les noms XML constituent souvent une source de complexité dans la programmation XML. Un nom XML est constitué d'un espace de noms XML (également appelé URI d'espace de noms XML) et d'un nom local. Un espace de noms XML est similaire à un espace de noms dans un programme [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)]. Il permet de qualifier de manière unique les noms d'éléments et d'attributs. Cela permet d'éviter les conflits de noms entre différentes parties d'un document XML. Lorsque vous avez déclaré un espace de noms XML, vous pouvez sélectionner un nom local qui n'exige d'être unique que dans cet espace de noms.  
  
 Les *préfixes d’espace de noms* XML constituent un autre aspect des noms XML. Les préfixes XML sont la cause de la plupart de la complexité des noms XML. Ces préfixes vous permettent de créer un raccourci pour un espace de noms XML, ce qui rend le document XML plus concis et plus compréhensible. Toutefois, la signification des préfixes XML dépend de leur contexte, ce qui augmente la complexité. Par exemple, le préfixe XML `aw` pourrait être associé à un espace de noms XML dans une partie d'une arborescence XML et à un espace de noms XML différent dans une autre partie de l'arborescence XML.  
  
 L’un des avantages d’utiliser [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] avec C# est que vous n’avez pas besoin de spécifier des préfixes XML. Quand [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] charge ou analyse un document XML, chaque préfixe XML est résolu à son espace de noms XML correspondant. Après cela, lorsque vous travaillez avec un document qui utilise des espaces de noms, vous accédez presque toujours aux espaces de noms par le biais de l'URI d'espace de noms, et non par le biais du préfixe d'espace de noms. Quand les développeurs utilisent des noms XML dans [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)], ils choisissent toujours un nom XML complet (autrement dit, un espace de noms XML et un nom local). Toutefois, en cas de nécessité, [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] vous permet de travailler avec les préfixes d'espaces de noms et de les contrôler.  
  
 Dans [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)], <xref:System.Xml.Linq.XName> est la classe qui représente les noms XML. Les noms XML apparaissent fréquemment dans l’API [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] et, chaque fois qu’un nom XML est requis, vous trouverez un paramètre <xref:System.Xml.Linq.XName>. Toutefois, vous utiliserez rarement directement un <xref:System.Xml.Linq.XName>. <xref:System.Xml.Linq.XName> contient une conversion implicite de chaîne.  
  
 Pour plus d’informations, consultez <xref:System.Xml.Linq.XNamespace> et <xref:System.Xml.Linq.XName>.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation des espaces de noms XML (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md)
