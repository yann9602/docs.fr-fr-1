---
title: "Embedded Expressions in XML (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.XmlEmbeddedExpression"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "embedded expressions [Visual Basic]"
  - "LINQ to XML [Visual Basic], embedded expressions"
  - "XML literals [Visual Basic], embedded expressions"
ms.assetid: bf2eb779-b751-4b7c-854f-9f2161482352
caps.latest.revision: 22
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 22
---
# Embedded Expressions in XML (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

Les expressions incorporées vous permettent de créer des littéraux XML qui contiennent des expressions évaluées au moment de l'exécution.  La syntaxe pour une expression incorporée est `<%=``expression``%>`, ce qui est identique à la syntaxe utilisé dans [!INCLUDE[vstecasp](../../../../csharp/language-reference/preprocessor-directives/includes/vstecasp-md.md)].  
  
 Vous pouvez, par exemple, créer un littéral d'élément XML, en combinant des expressions incorporées au contenu d'un texte littéral.  
  
 [!code-vb[VbXMLSamples#27](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_1.vb)]  
  
 Si `isbnNumber` contient l'entier 12345 et `modifiedDate` contient la date 3\/5\/2006, lorsque ce code s'exécute, la valeur de `book` est :  
  
```  
<book category="fiction" isbn="12345">  
  <modifiedDate>3/5/2006</modifiedDate>  
</book>  
```  
  
## Emplacement d'expression incorporée et validation  
 Les expressions incorporées ne peuvent apparaître qu'à certains emplacements, dans des expressions littérales XML.  L'emplacement de l'expression contrôle les types renvoyés par l'expression et la manière dont `Nothing` est géré.  Le tableau suivant décrit les emplacements autorisés et les types d'expressions incorporées.  
  
||||  
|-|-|-|  
|Emplacement dans le littéral|Type d'expression|Gestion de `Nothing`|  
|Nom d'élément XML|<xref:System.Xml.Linq.XName>|Erreur|  
|Contenu d'élément XML|`Object` ou tableau d'éléments `Object`|Ignoré|  
|Nom d'attribut d'élément XML|<xref:System.Xml.Linq.XName>|Erreur, à moins que la valeur d'attribut ne soit également `Nothing`|  
|Valeur d'attribut d'élément XML|`Object`|Déclaration attribute ignorée|  
|Attribut d'élément XML|<xref:System.Xml.Linq.XAttribute> ou une collection d'objets <xref:System.Xml.Linq.XAttribute>|Ignoré|  
|Élément racine de document XML|<xref:System.Xml.Linq.XElement> ou collection d'un objet <xref:System.Xml.Linq.XElement> et nombre arbitraire d'objets <xref:System.Xml.Linq.XProcessingInstruction> et <xref:System.Xml.Linq.XComment>|Ignoré|  
  
-   Exemple d'expression incorporée dans un nom d'élément XML :  
  
     [!code-vb[VbXMLSamples#32](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_2.vb)]  
  
-   Exemple d'expression incorporée dans le contenu d'un élément XML :  
  
     [!code-vb[VbXMLSamples#33](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_3.vb)]  
  
-   Exemple d'expression incorporée dans un nom d'attribut d'élément XML :  
  
     [!code-vb[VbXMLSamples#34](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_4.vb)]  
  
-   Exemple d'expression incorporée dans une valeur d'attribut d'élément XML :  
  
     [!code-vb[VbXMLSamples#35](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_5.vb)]  
  
-   Exemple d'expression incorporée dans un attribut d'élément XML :  
  
     [!code-vb[VbXMLSamples#36](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_6.vb)]  
  
-   Exemple d'expression incorporée dans un élément racine de document XML :  
  
     [!code-vb[VbXMLSamples#37](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_7.vb)]  
  
 Si vous activez `Option Strict`, le compilateur vérifie que le type de chaque expression incorporée s'étend au type requis.  La seule exception est l'élément racine d'un document XML, vérifié quand le code s'exécute.  Si vous compilez sans `Option Strict`, vous pouvez incorporer des expressions de type `Object` et leur type est vérifié au moment de l'exécution.  
  
 Dans les emplacements où le contenu est facultatif, les expressions incorporées qui contiennent `Nothing` sont ignorées.  Cela signifie que vous n'avez pas à vérifier que le contenu d'élément, les valeurs d'attribut et les éléments de la table diffèrent de `Nothing` avant d'utiliser un littéral XML.  Les valeurs requises, telles que les noms d'élément et d'attribut, ne peuvent pas être `Nothing`.  
  
 Pour plus d'informations sur l'utilisation d'une expression incorporée dans un type particulier de littéral, consultez [XML Document Literal](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md) et [XML Element Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).  
  
## Règles de portée  
 Le compilateur convertit chaque littéral XML en un appel de constructeur pour le type de littéral approprié.  Le contenu du littéral et les expressions incorporées dans un littéral XML sont communiquées au constructeur en tant qu'arguments.  Cela signifie que tous les éléments de programmation [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] disponibles pour un littéral XML sont également disponibles pour ses expressions incorporées.  
  
 Dans un littéral XML, vous pouvez accéder aux préfixes d'espace de noms XML déclarés avec l'instruction `Imports`.  Vous pouvez déclarer un nouveau préfixe d'espace de noms XML ou masquer un préfixe d'espace de noms XML existant dans un élément, en utilisant l'attribut `xmlns`.  Le nouvel espace de noms est disponible pour les nœuds enfants de cet élément, mais pas pour les littéraux XML des expressions incorporées.  
  
> [!NOTE]
>  Lorsque vous déclarez un préfixe d'espace de noms XML en utilisant l'attribut d'espace de noms `xmlns`, la valeur d'attribut doit être une chaîne constante.  C'est pourquoi l'utilisation de l'attribut `xmlns` revient à utiliser l'instruction `Imports` pour déclarer un espace de noms XML.  Vous ne pouvez pas utiliser d'expression incorporée pour spécifier une valeur d'espace de noms XML.  
  
## Voir aussi  
 [Creating XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)   
 [XML Document Literal](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)   
 [XML Element Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)   
 [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)   
 [Imports Statement \(.NET Namespace and Type\)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)   
 [XML Literals Overview](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-overview.md)