---
title: "How to: Load XML from a File, String, or Stream (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "XML [Visual Basic], loading"
  - "LINQ to XML [Visual Basic], loading XML from files"
ms.assetid: 2b02dcec-4cca-4575-b4ad-89ceb87b984c
caps.latest.revision: 13
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 13
---
# How to: Load XML from a File, String, or Stream (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

Vous pouvez créer des [XML Literals](../../../../visual-basic/language-reference/xml-literals/index.md) et les remplir avec le contenu d'une source externe telle qu'un fichier, une chaîne ou un flux de données en utilisant plusieurs méthodes.  Ces méthodes sont illustrées dans les exemples suivants.  
  
 [!INCLUDE[note_settings_general](../../../../csharp/language-reference/compiler-messages/includes/note-settings-general-md.md)]  
  
### Pour charger du XML à partir d'un fichier  
  
-   Pour remplir un littéral XML tel qu'un objet <xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XDocument> à partir d'un fichier, utilisez la méthode `Load`.  Cette méthode peut prendre un chemin d'accès de fichier, un flux de texte ou du XML comme entrée.  
  
     L'exemple de code suivant indique comment utiliser la méthode <xref:System.Xml.Linq.XDocument.Load%28System.String%29> pour remplir un objet <xref:System.Xml.Linq.XDocument> avec le code XML d'un fichier texte.  
  
     [!code-vb[VbXMLSamples#43](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-load-xml-from-a-file-string-or-stream_1.vb)]  
  
### Pour charger du XML à partir d'une chaîne  
  
-   Pour remplir un littéral XML tel qu'un objet <xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XDocument> à partir d'une chaîne, vous pouvez utiliser la méthode `Parse`.  
  
     L'exemple de code suivant indique comment utiliser la méthode <xref:System.Xml.Linq.XDocument.Parse%28System.String%29?displayProperty=fullName> pour remplir un objet <xref:System.Xml.Linq.XDocument> avec le code XML d'une chaîne.  
  
     [!code-vb[VbXMLSamples#47](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-load-xml-from-a-file-string-or-stream_2.vb)]  
  
### Pour charger du XML à partir d'un flux de données  
  
-   Pour remplir un littéral XML tel qu'un objet <xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XDocument> à partir d'un flux, vous pouvez utiliser la méthode `Load` ou <xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=fullName>.  
  
 L'exemple de code suivant indique comment utiliser la méthode <xref:System.Xml.Linq.XNode.ReadFrom%2A> pour remplir un objet <xref:System.Xml.Linq.XDocument> avec le XML d'un flux XML.  
  
 [!code-vb[VbXMLSamples#46](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-load-xml-from-a-file-string-or-stream_3.vb)]  
  
## Voir aussi  
 <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=fullName>   
 <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=fullName>   
 <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=fullName>   
 <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=fullName>   
 <xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=fullName>   
 [XML Literals](../../../../visual-basic/language-reference/xml-literals/index.md)   
 [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)   
 [Manipulating XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)