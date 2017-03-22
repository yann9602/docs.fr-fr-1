---
title: "Littéral de Document XML (Visual Basic) | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.XmlLiteralDocument
dev_langs:
- VB
helpviewer_keywords:
- XML document literal [Visual Basic]
- XML literals [Visual Basic], document
- XML documents [Visual Basic], creating
- document literal [Visual Basic]
ms.assetid: f7bbee56-0911-41de-b907-96f20450137b
caps.latest.revision: 20
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: 5d64faddad66eba4029969654388ba7df17e5854
ms.lasthandoff: 03/13/2017

---
# <a name="xml-document-literal-visual-basic"></a>Littéral de document XML (Visual Basic)
Littéral représentant un <xref:System.Xml.Linq.XDocument>objet.</xref:System.Xml.Linq.XDocument>  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
|`piCommentList`|Facultatif. Liste des instructions de traitement XML et de commentaires XML. Prend le format suivant :<br /><br /> `piComment [` `piComment` `... ]`<br /><br /> Chaque `piComment`peut être une des opérations suivantes :<br /><br /> -   [Littéral d’Instruction de traitement XML](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md).<br />-   [Littéral de commentaire XML](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md).|  
|`rootElement`|Obligatoire. Élément racine du document. Le format est une des opérations suivantes :<br /><br /> <ul><li>[Littéral d’élément XML](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</li><li>L’écran expression incorporée, `<%=` `elementExp` `%>`. Le `elementExp` renvoie une des opérations suivantes :<br /><br /> <ul><li>Un <xref:System.Xml.Linq.XElement>objet.</xref:System.Xml.Linq.XElement></li><li>Une collection qui contient un <xref:System.Xml.Linq.XElement>objet et n’importe quel nombre de <xref:System.Xml.Linq.XProcessingInstruction>et <xref:System.Xml.Linq.XComment>objets.</xref:System.Xml.Linq.XComment> </xref:System.Xml.Linq.XProcessingInstruction> </xref:System.Xml.Linq.XElement></li></ul></li></ul><br /> Pour plus d’informations, consultez [Expressions incorporées en XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).|  
  
## <a name="return-value"></a>Valeur de retour  
 Un <xref:System.Xml.Linq.XDocument>objet.</xref:System.Xml.Linq.XDocument>  
  
## <a name="remarks"></a>Remarques  
 Un littéral de document XML est identifié par la déclaration XML au démarrage du littéral. Bien que chaque littéral de document XML doit avoir exactement un élément XML racine, il peut avoir n’importe quel nombre d’instructions de traitement XML et de commentaires XML.  
  
 Un littéral de document XML ne peut pas apparaître dans un élément XML.  
  
> [!NOTE]
>  Un littéral XML peut couvrir plusieurs lignes sans utiliser de caractères de continuation de ligne. Cela vous permet de copier le contenu d’un document XML et coller directement dans un [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] programme.  
  
 Le [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compilateur convertit le littéral de document XML en appels à la <xref:System.Xml.Linq.XDocument.%23ctor%2A>et <xref:System.Xml.Linq.XDeclaration.%23ctor%2A>constructeurs.</xref:System.Xml.Linq.XDeclaration.%23ctor%2A> </xref:System.Xml.Linq.XDocument.%23ctor%2A>  
  
## <a name="example"></a>Exemple  
 L’exemple suivant crée un document XML qui possède une déclaration XML, une instruction de traitement, un commentaire et un élément contenant un autre élément.  
  
 [!code-vb[30 VbXMLSamples](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-document-literal_1.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Xml.Linq.XElement>   
 <xref:System.Xml.Linq.XProcessingInstruction></xref:System.Xml.Linq.XProcessingInstruction>   
 <xref:System.Xml.Linq.XComment></xref:System.Xml.Linq.XComment>   
 <xref:System.Xml.Linq.XDocument></xref:System.Xml.Linq.XDocument>   
 [Littéral d’Instruction de traitement XML](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md)   
 [Littéraux de commentaires XML](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md)   
 [Littéral d’élément XML](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)   
 [Littéraux XML](../../../visual-basic/language-reference/xml-literals/index.md)   
 [Création de code XML en Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)   
 [Expressions incorporées en XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)
