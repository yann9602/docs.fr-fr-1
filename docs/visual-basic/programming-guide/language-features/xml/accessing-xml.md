---
title: "Accessing XML in Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "LINQ to XML [Visual Basic], accessing XML"
  - "Visual Basic code, XML"
  - "accessing XML [Visual Basic], axis properties"
  - "XML [Visual Basic], axis properties"
  - "XML [Visual Basic], accessing"
ms.assetid: c47f88b2-3cbc-4bb1-b4b9-be60f71ffc6a
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Accessing XML in Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] fournit des propriétés d'axe XML pour accéder aux structures  [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] et les parcourir.  Ces propriétés utilisent une syntaxe spéciale pour vous permettre d'accéder aux éléments et aux attributs, en spécifiant les noms XML.  
  
 La table qui suit répertorie les fonctionnalités de langage qui vous permettent d'accéder aux éléments XML et aux attributs dans [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].  
  
### Propriétés d'axe XML  
  
|Description, propriété|Exemple|Description|  
|----------------------------|-------------|-----------------|  
|*axe enfant*|`contact.<phone>`|Obtient tous les éléments enfants `phone` de l'élément `contact`.|  
|*axe d'attribut*|`phone.@type`|Obtient tous les attributs `type` de l'élément `phone`.|  
|*axe descendant*|`contacts...<name>`|Obtient tous les éléments `name` de l'élément `contacts`, indépendamment de leur niveau hiérarchique.|  
|*indexeur d'extension*|`contacts...<name>(0)`|Obtient le premier élément `name` de la séquence.|  
|*value*|`contacts...<name>.Value`|Obtient la représentation sous forme de chaîne du premier objet dans la séquence, ou `Nothing` si la séquence est vide.|  
  
## Dans cette section  
 [How to: Access XML Descendant Elements](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-descendant-elements.md)  
 Indique comment utiliser une propriété d'axe descendant pour accéder à tous les éléments XML portant un nom spécifié et contenus sous un élément XML spécifié.  
  
 [How to: Access XML Child Elements](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-child-elements.md)  
 Indique comment utiliser une propriété d'axe enfant pour accéder à tous les éléments enfants XML portant un nom spécifié dans un élément XML.  
  
 [How to: Access XML Attributes](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-attributes.md)  
 Indique comment utiliser une propriété d'axe d'attribut pour accéder à tous les attributs XML portant un nom spécifié dans un élément XML.  
  
 [How to: Declare and Use XML Namespace Prefixes](../../../../visual-basic/programming-guide/language-features/xml/how-to-declare-and-use-xml-namespace-prefixes.md)  
 Indique comment déclarer un préfixe d'espace de noms XML et l'utiliser pour créer des éléments XML et y accéder.  
  
## Rubriques connexes  
 [XML Axis Properties](../../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)  
 Fournit des liens vers des sections qui décrivent les différentes propriétés d'accès XML.  
  
 [Overview of LINQ to XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/overview-of-linq-to-xml.md)  
 Présente l'utilisation de [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] dans Visual Basic.  
  
 [Creating XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 Présente l'utilisation de littéraux XML dans Visual Basic.  
  
 [Manipulating XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)  
 Fournit des liens aux sections sur le chargement et la modification de XML dans Visual Basic.  
  
 [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)  
 Fournit des liens vers des sections qui décrivent l'utilisation de [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] dans Visual Basic.