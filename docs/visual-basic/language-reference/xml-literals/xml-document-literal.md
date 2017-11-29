---
title: "Littéral de document XML (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.XmlLiteralDocument
helpviewer_keywords:
- XML document literal [Visual Basic]
- XML literals [Visual Basic], document
- XML documents [Visual Basic], creating
- document literal [Visual Basic]
ms.assetid: f7bbee56-0911-41de-b907-96f20450137b
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 008b5857418a572046797bf061a05f265669d427
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="xml-document-literal-visual-basic"></a>Littéral de document XML (Visual Basic)
Littéral représentant un <xref:System.Xml.Linq.XDocument> objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<?xml version="1.0" [encoding="encoding"] [standalone="standalone"] ?>  
[ piCommentList ]  
rootElement  
[ piCommentList ]  
```  
  
## <a name="parts"></a>Composants  
  
|Terme|Définition|  
|---|---|  
|`encoding`|Facultatif. Utilise du texte littéral qui déclare l’encodage du document.|  
|`standalone`|Facultatif. Texte littéral. Doit être « Oui » ou « non ».|  
|`piCommentList`|Facultatif. Liste des instructions de traitement XML et de commentaires XML. Prend le format suivant :<br /><br /> `piComment [` `piComment` `... ]`<br /><br /> Chaque `piComment` peut prendre l’une des opérations suivantes :<br /><br /> -   [Littéral d’Instruction de traitement XML](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md).<br />-   [Littéral de commentaire XML](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md).|  
|`rootElement`|Obligatoire. Élément racine du document. Le format est une des opérations suivantes :<br /><br /> <ul><li>[Littéral d’élément XML](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</li><li>Expression sous la forme incorporée `<%=` `elementExp` `%>`. Le `elementExp` renvoie l’une des opérations suivantes :<br /><br /> <ul><li>Objet <xref:System.Xml.Linq.XElement>.</li><li>Une collection qui contient un <xref:System.Xml.Linq.XElement> objet et un nombre quelconque de <xref:System.Xml.Linq.XProcessingInstruction> et <xref:System.Xml.Linq.XComment> objets.</li></ul></li></ul><br /> Pour plus d’informations, consultez [Expressions incorporées en XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).|  
  
## <a name="return-value"></a>Valeur de retour  
 Objet <xref:System.Xml.Linq.XDocument>.  
  
## <a name="remarks"></a>Remarques  
 Un littéral de document XML est identifié par la déclaration XML au début du littéral. Bien que chaque littéral de document XML doit avoir exactement un élément XML racine, il peut avoir n’importe quel nombre d’instructions de traitement XML et de commentaires XML.  
  
 Un littéral de document XML ne peut pas apparaître dans un élément XML.  
  
> [!NOTE]
>  Un littéral XML peut couvrir plusieurs lignes sans utiliser de caractères de continuation de ligne. Cela vous permet de copier le contenu d’un document XML et coller directement dans un [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] programme.  
  
 Le [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compilateur convertit le littéral de document XML en appels à la <xref:System.Xml.Linq.XDocument.%23ctor%2A> et <xref:System.Xml.Linq.XDeclaration.%23ctor%2A> constructeurs.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant crée un document XML qui possède une déclaration XML, une instruction de traitement, un commentaire et un élément qui contient un autre élément.  
  
 [!code-vb[VbXMLSamples#30](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-document-literal_1.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Xml.Linq.XElement>  
 <xref:System.Xml.Linq.XProcessingInstruction>  
 <xref:System.Xml.Linq.XComment>  
 <xref:System.Xml.Linq.XDocument>  
 [Littéral d’instruction de traitement XML](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md)  
 [Littéraux de commentaires XML](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md)  
 [Littéral d’élément XML](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)  
 [Littéraux XML](../../../visual-basic/language-reference/xml-literals/index.md)  
 [Création de code XML dans Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [Expressions incorporées en XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)
