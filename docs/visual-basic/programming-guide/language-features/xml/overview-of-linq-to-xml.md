---
title: "Overview of LINQ to XML in Visual Basic | Microsoft Docs"
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
  - "LINQ to XML [Visual Basic], about LINQ to XML"
  - "LINQ [Visual Basic], LINQ to XML"
ms.assetid: 01c62a79-6d58-468e-84fb-039c05947701
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Overview of LINQ to XML in Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] offre une prise en charge de [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] via les littéraux et les propriétés d'axe XML.  Vous pouvez ainsi faire appel à une syntaxe pratique et familière pour utiliser du code XML dans votre code [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]. Les *littéraux XML* vous permettent d'inclure du code XML directement dans votre code.  Les *propriétés d'axe XML* vous permettent d'accéder aux nœuds enfants, nœuds descendants et attributs d'un littéral XML.  Pour plus d'informations, consultez [XML Literals Overview](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-overview.md) et [Accessing XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md).  
  
 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] est une API de programmation XML en mémoire qui est spécifiquement conçue pour tirer parti de [!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext_md.md)].  Bien que vous puissiez appeler les API [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] directement, seul [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] vous permet de déclarer des littéraux XML et d'accéder directement aux propriétés d'axe XML.  
  
> [!NOTE]
>  Les littéraux XML et les propriétés d'axe XML ne sont pas prises en charge dans le code déclaratif d'une page ASP.NET.  Pour utiliser les fonctionnalités XML de Visual Basic, insérez votre code dans une page code\-behind dans votre application ASP.NET.  
  
 ![lien vers la vidéo](../../../../csharp/programming-guide/concepts/linq/media/playvideo.png "PlayVideo") Pour des démonstrations vidéo connexes, consultez [How Do I Get Started with LINQ to XML?](http://msdn.microsoft.com/fr-fr/vbasic/bb887653.aspx) et [How Do I Create Excel Spreadsheets using LINQ to XML?](http://msdn.microsoft.com/fr-fr/vbasic/bb927708.aspx).  
  
## Création d'éléments XML  
 Il existe deux manières de créer des arborescences XML dans [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].  Vous pouvez déclarer directement un littéral XML dans le code ou utiliser les API [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] pour créer l'arborescence.  Ces deux processus permettent au code de refléter la structure finale de l'arborescence XML.  Par exemple, l'exemple de code suivant crée un élément XML :  
  
 [!code-vb[VbXmlSamples#5](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/overview-of-linq-to-xml_1.vb)]  
  
 Pour plus d'informations, consultez [Creating XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md).  
  
## Accès et navigation dans XML  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] fournit des propriétés d'axe XML pour accéder aux structures XML et les parcourir.  Ces propriétés vous permettent d'accéder aux éléments et aux attributs XML en spécifiant les noms des éléments enfants XML.  Vous pouvez également appeler explicitement les méthodes [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] pour parcourir et localiser des éléments et des attributs.  Par exemple, l'exemple de code suivant utilise des propriétés d'axe XML pour faire référence aux attributs et éléments enfants d'un élément XML.  L'exemple de code utilise une requête [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] pour récupérer des éléments enfants et les sortir comme éléments XML, en effectuant efficacement une transformation.  
  
 [!code-vb[VbXmlSamples#8](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/overview-of-linq-to-xml_2.vb)]  
  
 Pour plus d'informations, consultez [Accessing XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md).  
  
## Espaces de noms XML  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] vous permet de spécifier un alias pour un espace de noms XML global en utilisant l'instruction `Imports`.  L'exemple suivant indique comment utiliser l'instruction `Imports` pour importer un espace de noms XML :  
  
 [!code-vb[VbXMLSamples#1](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/overview-of-linq-to-xml_3.vb)]  
  
 Vous pouvez utiliser un alias d'espace de noms XML lorsque vous accédez à des propriétés d'axe XML et déclarez des littéraux XML pour les documents et les éléments XML.  
  
 Vous pouvez récupérer un objet <xref:System.Xml.Linq.XNamespace> pour un préfixe d'espace de noms particulier en utilisant le [GetXmlNamespace Operator](../../../../visual-basic/language-reference/operators/getxmlnamespace-operator.md).  
  
 Pour plus d'informations, consultez [Imports Statement \(XML Namespace\)](../../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).  
  
### Utilisation d'espaces de noms XML dans les littéraux XML  
 L'exemple suivant indique comment créer un objet <xref:System.Xml.Linq.XElement> utilisant l'espace de noms global `ns` :  
  
 [!code-vb[VbXMLSamples#2](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/overview-of-linq-to-xml_4.vb)]  
  
 Le compilateur [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] traduit les littéraux XML qui contiennent des alias d'espace de noms XML en code équivalent, qui se sert de la notation XML pour utiliser des espaces de noms XML, avec l'attribut `xmlns`.  Une fois compilé, le code de l'exemple de la section précédente produit essentiellement le même code exécutable que l'exemple suivant :  
  
 [!code-vb[VbXMLSamples#3](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/overview-of-linq-to-xml_5.vb)]  
  
### Utilisation d'espaces de noms XML dans les propriétés d'axe XML  
 Les espaces de noms XML déclarés dans les littéraux XML ne peuvent pas être utilisés dans les propriétés d'axe XML.  Toutefois, les espaces de noms globaux peuvent l'être avec les propriétés d'axe XML.  Utilisez le signe deux\-points pour séparer le préfixe d'espace de noms XML du nom d'élément local.  Voici un exemple :  
  
 [!code-vb[VbXMLSamples#4](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/overview-of-linq-to-xml_6.vb)]  
  
## Voir aussi  
 [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)   
 [Creating XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)   
 [Accessing XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)   
 [Manipulating XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)