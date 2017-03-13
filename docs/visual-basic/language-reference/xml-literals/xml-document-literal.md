---
title: "XML Document Literal (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.XmlLiteralDocument"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "XML document literal [Visual Basic]"
  - "XML literals [Visual Basic], document"
  - "XML documents [Visual Basic], creating"
  - "document literal [Visual Basic]"
ms.assetid: f7bbee56-0911-41de-b907-96f20450137b
caps.latest.revision: 20
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 20
---
# XML Document Literal (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Littéral représentant un objet <xref:System.Xml.Linq.XDocument>.  
  
## Syntaxe  
  
```  
<?xml version="1.0" [encoding="encoding"] [standalone="standalone"] ?>  
[ piCommentList ]  
rootElement  
[ piCommentList ]  
```  
  
## Composants  
  
|||  
|-|-|  
|Terme|Définition|  
|`encoding`|Facultatif.  Texte littéral qui déclare l'encodage utilisé par le document.|  
|`standalone`|Facultatif.  Texte littéral.  Doit être "oui" ou "non".|  
|`piCommentList`|Facultatif.  Liste d'instructions de traitement XML et de commentaires XML.  Prend le format suivant :<br /><br /> `piComment [` `piComment` `... ]`<br /><br /> Chaque `piComment` `` peut correspondre à l'un des éléments suivants :<br /><br /> -   [XML Processing Instruction Literal](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md).<br />-   [XML Comment Literal](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md).|  
|`rootElement`|Obligatoire.  Élément racine du document.  Le format est l'un des suivants :<br /><br /> <ul><li>[XML Element Literal](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</li><li>Expression incorporée, sous la forme `<%=` `elementExp` `%>`.  L'`elementExp` retourne l'un des éléments suivants :<br /><br /> <ul><li>Objet <xref:System.Xml.Linq.XElement>.</li><li>Collection contenant un objet <xref:System.Xml.Linq.XElement> et tout nombre d'objets <xref:System.Xml.Linq.XProcessingInstruction> et <xref:System.Xml.Linq.XComment>.</li></ul></li></ul><br /> Pour plus d'informations, consultez [Embedded Expressions in XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).|  
  
## Valeur de retour  
 Objet <xref:System.Xml.Linq.XDocument>.  
  
## Notes  
 Littéral de document XML identifié par la déclaration XML au démarrage du littéral.  Bien que chaque littéral de document XML doive comporter précisément un élément XML racine, il peut comporter tout nombre d'instructions de traitement XML et de commentaires XML.  
  
 Un littéral de document XML ne peut pas apparaître dans un élément XML.  
  
> [!NOTE]
>  Un littéral XML peut couvrir plusieurs lignes, sans utiliser de caractères de continuation de ligne.  Cela vous permet de copier le contenu d'un document XML et de le coller directement dans un programme [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)].  
  
 Le compilateur [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] convertit le littéral de document XML en appels aux constructeurs <xref:System.Xml.Linq.XDocument.%23ctor%2A> et <xref:System.Xml.Linq.XDeclaration.%23ctor%2A>.  
  
## Exemple  
 L'exemple suivant crée un document XML qui possède une déclaration XML, une instruction de traitement, un commentaire et un élément contenant un autre élément.  
  
 [!code-vb[VbXMLSamples#30](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-document-literal_1.vb)]  
  
## Voir aussi  
 <xref:System.Xml.Linq.XElement>   
 <xref:System.Xml.Linq.XProcessingInstruction>   
 <xref:System.Xml.Linq.XComment>   
 <xref:System.Xml.Linq.XDocument>   
 [XML Processing Instruction Literal](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md)   
 [XML Comment Literal](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md)   
 [XML Element Literal](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)   
 [XML Literals](../../../visual-basic/language-reference/xml-literals/index.md)   
 [Creating XML in Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)   
 [Embedded Expressions in XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)