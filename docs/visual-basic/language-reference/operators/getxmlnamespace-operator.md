---
title: "GetXmlNamespace Operator (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.GetXmlNamespace"
  - "GetXmlNamespace"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "GetXmlNamespace operator"
  - "GetXmlNamespace keyword"
ms.assetid: d0d28cfd-0755-4896-ae0b-4981aa35517c
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 14
---
# GetXmlNamespace Operator (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Obtient l'objet <xref:System.Xml.Linq.XNamespace> qui correspond au préfixe d'espace de noms XML spécifié.  
  
## Syntaxe  
  
```  
GetXmlNamespace(xmlNamespacePrefix)  
```  
  
## Composants  
 `xmlNamespacePrefix`  
 Facultatif.  Chaîne qui identifie le préfixe d'espace de noms XML.  Si elle est fournie, cette chaîne doit être un identificateur XML valide.  Pour plus d'informations, consultez [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).  Si aucun préfixe n'est spécifié, l'espace de noms par défaut est retourné.  Si aucun espace de noms par défaut n'est spécifié, un espace de noms vide est retourné.  
  
## Valeur de retour  
 Objet <xref:System.Xml.Linq.XNamespace> correspondant au préfixe d'espace de noms XML.  
  
## Notes  
 L'opérateur `GetXmlNamespace` obtient l'objet <xref:System.Xml.Linq.XNamespace> correspondant au préfixe d'espace de noms XML `xmlNamespacePrefix`.  
  
 Vous pouvez utiliser directement les préfixes d'espace de noms XML dans les littéraux XML et les propriétés d'axe XML.  Vous devez toutefois utiliser l'opérateur `GetXmlNamespace` pour convertir un préfixe d'espace de noms en un objet <xref:System.Xml.Linq.XNamespace>, avant de pouvoir l'utiliser dans votre code.  Vous pouvez ajouter un nom d'élément non qualifié à un objet <xref:System.Xml.Linq.XNamespace> pour obtenir un objet <xref:System.Xml.Linq.XName> qualifié complet, que de nombreuses méthodes [!INCLUDE[sqltecxlinq](../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq-md.md)] requièrent.  
  
## Exemple  
 L'exemple suivant importe `ns` en tant que préfixe d'espace de noms XML.  Il utilise ensuite le préfixe d'espace de noms pour créer un littéral XML et accéder au premier nœud enfant avec le nom qualifié `ns:phone`.  Il passe alors ce nœud enfant à la sous\-routine `ShowName`, qui construit un nom qualifié en utilisant l'opérateur `GetXmlNamespace`.  La sous\-routine `ShowName` passe ensuite le nom qualifié à la méthode <xref:System.Xml.Linq.XNode.Ancestors%2A> pour obtenir le nœud parent `ns:contact`.  
  
 [!code-vb[VbXMLSamples#38](../../../visual-basic/language-reference/operators/codesnippet/visualbasic/getxmlnamespace-operator_1.vb)]  
  
 Lorsque vous appelez `TestGetXmlNamespace.RunSample()`, une boîte de message s'affiche, qui contient le texte suivant :  
  
 `Name: Patrick Hines`  
  
## Voir aussi  
 [Imports Statement \(XML Namespace\)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)   
 [Accessing XML in Visual Basic](../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)