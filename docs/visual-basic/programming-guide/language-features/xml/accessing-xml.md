---
title: "Accès au code XML en Visual Basic | Documents Microsoft"
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
helpviewer_keywords:
- LINQ to XML [Visual Basic], accessing XML
- Visual Basic code, XML
- accessing XML [Visual Basic], axis properties
- XML [Visual Basic], axis properties
- XML [Visual Basic], accessing
ms.assetid: c47f88b2-3cbc-4bb1-b4b9-be60f71ffc6a
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 215f057f0b4d884369aad53cbbdbb98f240b56c4
ms.lasthandoff: 03/13/2017

---
# <a name="accessing-xml-in-visual-basic"></a>Accès au code XML dans Visual Basic
[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]Fournit des propriétés d’axe XML pour accéder à et naviguer [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] structures. Ces propriétés utilisent une syntaxe spéciale pour vous permettent d’accéder aux éléments et attributs en spécifiant les noms XML.  
  
 Le tableau suivant répertorie les fonctionnalités de langage qui vous permettent d’accéder aux éléments et attributs dans XML [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].  
  
### <a name="xml-axis-properties"></a>Propriétés d'axe XML  
  
|Description de la propriété|Exemple|Description|  
|--------------------------|-------------|-----------------|  
|*axe d’enfant*|`contact.<phone>`|Obtient tous les `phone` les éléments qui sont des éléments enfants de le `contact` élément.|  
|*axe d’attribut*|`phone.@type`|Obtient tous les `type` les attributs de la `phone` élément.|  
|*axe descendant*|`contacts...<name>`|Obtient tous les `name` les éléments de la `contacts` élément, quelle que soit la profondeur dans la hiérarchie.|  
|*indexeur d’extension*|`contacts...<name>(0)`|Obtient le premier `name` élément de la séquence.|  
|*value*|`contacts...<name>.Value`|Obtient la représentation sous forme de chaîne du premier objet dans la séquence, ou `Nothing` si la séquence est vide.|  
  
## <a name="in-this-section"></a>Dans cette section  
 [Guide pratique : accéder à des éléments descendants XML](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-descendant-elements.md)  
 Montre comment utiliser une propriété d’axe descendant pour accéder à tous les éléments XML portant un nom spécifié et contenus sous un élément XML spécifié.  
  
 [Guide pratique : accéder à des éléments enfants XML](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-child-elements.md)  
 Montre comment utiliser un enfant de propriété d’axe pour accéder à tous les éléments enfants XML portant un nom spécifié dans un élément XML.  
  
 [Guide pratique : accéder à des attributs XML](../../../../visual-basic/programming-guide/language-features/xml/how-to-access-xml-attributes.md)  
 Montre comment utiliser une propriété d’axe d’attribut pour accéder à tous les attributs XML qui ont un nom spécifié dans un élément XML.  
  
 [Guide pratique : déclarer et utiliser des préfixes d’espaces de noms XML](../../../../visual-basic/programming-guide/language-features/xml/how-to-declare-and-use-xml-namespace-prefixes.md)  
 Montre comment déclarer un préfixe d’espace de noms XML et l’utiliser pour créer et accéder à des éléments XML.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Propriétés d’axe XML](../../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)  
 Fournit des liens vers des sections qui décrivent les différentes propriétés d’accès XML.  
  
 [Vue d’ensemble de LINQ to XML dans Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/overview-of-linq-to-xml.md)  
 Fournit une introduction à l’utilisation de [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] en Visual Basic.  
  
 [Création de code XML en Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 Fournit une introduction à l’utilisation de littéraux XML en Visual Basic.  
  
 [Manipulation de XML en Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)  
 Fournit des liens vers des sections sur le chargement et la modification de XML en Visual Basic.  
  
 [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)  
 Fournit des liens vers des sections qui décrivent comment utiliser [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] dans Visual Basic.
