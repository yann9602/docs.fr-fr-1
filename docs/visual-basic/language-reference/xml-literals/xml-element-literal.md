---
title: "Littéral d'élément XML (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.XmlLiteralElement
helpviewer_keywords:
- XML element literal [Visual Basic]
- element literal [Visual Basic]
- XML literals [Visual Basic], element
ms.assetid: 95039642-7893-48b7-b23f-45a6c55d8f67
caps.latest.revision: "32"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: de5825a6af1dd1b93c3c85651125cf817dc564f2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="xml-element-literal-visual-basic"></a>Littéral d'élément XML (Visual Basic)

Un littéral qui représente un <xref:System.Xml.Linq.XElement> objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<name [ attributeList ] />  
-or-  
<name [ attributeList ] > [ elementContents ] </[ name ]>  
```  
  
## <a name="parts"></a>Composants  
  
-   `<`  
  
     Obligatoire. Ouvre la balise d’élément initiale.  
  
-   `name`  
  
     Obligatoire. Nom de l'élément. Le format est une des opérations suivantes :  
  
    -   Texte littéral pour le nom de l’élément, sous la forme `[ePrefix:]eName`, où :  
  
        |Élément|Description|  
        |---|---|  
        |`ePrefix`|Facultatif. Préfixe d’espace de noms XML pour l’élément. Doit être un espace de noms XML global défini avec un `Imports` instruction dans le fichier ou au niveau du projet, ou un espace de noms XML local défini dans cet élément ou un élément parent.|  
        |`eName`|Obligatoire. Nom de l'élément. Le format est une des opérations suivantes :<br /><br /> -Texte littéral. Consultez [nom des attributs et éléments XML déclarés](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).<br />-Incorporé expression sous la forme `<%= eNameExp %>`. Le type de `eNameExp` doit être `String` ou un type qui est implicitement convertible en <xref:System.Xml.Linq.XName>.|  
  
    -   Expression sous la forme incorporée `<%= nameExp %>`. Le type de `nameExp` doit être `String` ou un type implicitement convertible en <xref:System.Xml.Linq.XName>. Une expression incorporée n’est pas autorisée dans une balise de fermeture d’un élément.  
  
-   `attributeList`  
  
     Facultatif. Liste d’attributs déclarés dans le littéral.  
  
     `attribute [ attribute ... ]`  
  
     Chaque `attribute` a l’une des syntaxes suivantes :  
  
    -   Attribut d’affectation, sous la forme `[aPrefix:]aName=aValue`, où :  
  
        |Élément|Description|  
        |---|---|  
        |`aPrefix`|Facultatif. Préfixe d’espace de noms XML pour l’attribut. Doit être un espace de noms XML global défini avec un `Imports` instruction ou un espace de noms XML local défini dans cet élément ou un élément parent.|  
        |`aName`|Obligatoire. Nom de l'attribut. Le format est une des opérations suivantes :<br /><br /> -Texte littéral. Consultez [nom des attributs et éléments XML déclarés](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).<br />-Incorporé expression sous la forme `<%= aNameExp %>`. Le type de `aNameExp` doit être `String` ou un type qui est implicitement convertible en <xref:System.Xml.Linq.XName>.|  
        |`aValue`|Facultatif. Valeur de l’attribut. Le format est une des opérations suivantes :<br /><br /> -Texte littéral, entourée guillemets.<br />-Incorporé expression sous la forme `<%= aValueExp %>`. N’importe quel type est autorisé.|  
  
    -   Expression sous la forme incorporée `<%= aExp %>`.  
  
-   `/>`  
  
     Facultatif. Indique que l’élément est un élément vide, sans contenu.  
  
-   `>`  
  
     Obligatoire. Met fin à la balise d’élément initiale ou vide.  
  
-   `elementContents`  
  
     Facultatif. Contenu de l’élément.  
  
     `content [ content ... ]`  
  
     Chaque `content` peut prendre l’une des opérations suivantes :  
  
    -   Texte littéral. Tous les espaces blancs dans `elementContents` devient significatif si du texte littéral est.  
  
    -   Expression sous la forme incorporée `<%= contentExp %>`.  
  
    -   Littéral d’élément XML.  
  
    -   Littéral de commentaire XML. Consultez [littéral de commentaire XML](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md).  
  
    -   Instruction de traitement XML littéral. Consultez [littéral d’Instruction de traitement XML](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md).  
  
    -   Littéral CDATA XML. Consultez [littéral CDATA XML](../../../visual-basic/language-reference/xml-literals/xml-cdata-literal.md).  
  
-   `</[name]>`  
  
     Facultatif. Représente la balise de fermeture de l’élément. Le paramètre facultatif `name` paramètre n’est pas autorisé lorsqu’il est le résultat d’une expression incorporée.  
  
## <a name="return-value"></a>Valeur de retour  
 Objet <xref:System.Xml.Linq.XElement>.  
  
## <a name="remarks"></a>Remarques  
 Vous pouvez utiliser la syntaxe de littéral d’élément XML pour créer <xref:System.Xml.Linq.XElement> objets dans votre code.  
  
> [!NOTE]
>  Un littéral XML peut couvrir plusieurs lignes sans utiliser de caractères de continuation de ligne. Cette fonctionnalité vous permet de copier le contenu d’un document XML et coller directement dans un [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] programme.  
  
 Les expressions incorporées du formulaire `<%= exp %>` vous permettent d’ajouter des informations dynamiques à un littéral d’élément XML. Pour plus d’informations, consultez [Expressions incorporées en XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).  
  
 Le [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compilateur convertit le littéral d’élément XML en appels à la <xref:System.Xml.Linq.XElement.%23ctor%2A> constructeur et, si nécessaire, le <xref:System.Xml.Linq.XAttribute.%23ctor%2A> constructeur.  
  
## <a name="xml-namespaces"></a>Espaces de noms XML  
 Les préfixes d’espace de noms XML sont utiles lorsque vous avez besoin de créer des littéraux XML avec des éléments du même espace de noms plusieurs fois dans le code. Vous pouvez utiliser les préfixes d’espace de noms XML globaux, que vous définissez à l’aide de la `Imports` instruction, ou les préfixes locaux, que vous définissez à l’aide de la `xmlns:xmlPrefix="xmlNamespace"` la syntaxe d’attribut. Pour plus d’informations, consultez [Imports, instruction (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).  
  
 Conformément aux règles de portée pour les espaces de noms XML, les préfixes locaux sont prioritaires sur les préfixes globaux. Toutefois, si un littéral XML définit un espace de noms XML, cet espace de noms n’est pas disponible pour les expressions qui apparaissent dans une expression incorporée. L’expression incorporée peut accéder uniquement l’espace de noms XML global.  
  
 Le [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compilateur convertit chaque espace de noms XML global utilisé par un littéral XML dans une définition d’espace de noms locale dans le code généré. Espaces de noms XML globaux qui ne sont pas utilisés n’apparaissent pas dans le code généré.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment créer un élément XML simple qui a deux éléments vides imbriqués.  
  
 [!code-vb[VbXMLSamples#20](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-element-literal_1.vb)]  
  
 L’exemple affiche le texte suivant. Notez que le littéral conserve la structure des éléments vides.  
  
```xml  
<outer>  
  <inner1></inner1>  
  <inner2 />  
</outer>  
```  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment utiliser des expressions incorporées pour nommer un élément et de créer des attributs.  
  
 [!code-vb[VbXMLSamples#21](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-element-literal_2.vb)]  
  
 Ce code affiche le texte suivant :  
  
```xml  
<book isbn="1234" author="My Author" year="1999" title="My Book" />  
```  
  
## <a name="example"></a>Exemple  
 L'exemple suivant déclare `ns` en tant que préfixe d'espace de noms XML. Ensuite, il utilise le préfixe de l’espace de noms pour créer un littéral XML et affiche la forme finale de l’élément.  
  
 [!code-vb[VbXMLSamples#22](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-element-literal_3.vb)]  
  
 Ce code affiche le texte suivant :  
  
```xml  
<ns:outer xmlns:ns="http://SomeNamespace">  
  <ns:middle xmlns:ns="http://NewNamespace">  
    <ns:inner1 />  
    <inner2 xmlns="http://SomeNamespace" />  
  </ns:middle>  
</ns:outer>  
```  
  
 Notez que le compilateur a converti le préfixe d’espace de noms XML global dans une définition de préfixe pour l’espace de noms XML. Le \<ns:middle > élément redéfinit le préfixe d’espace de noms XML pour le \<ns:inner1 > élément. Toutefois, le \<ns:inner2 > élément utilise l’espace de noms défini par le `Imports` instruction.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Xml.Linq.XElement>  
 [Nom des attributs et des éléments XML déclarés](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)  
 [Littéraux de commentaires XML](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md)  
 [Littéral CDATA XML](../../../visual-basic/language-reference/xml-literals/xml-cdata-literal.md)  
 [Littéraux XML](../../../visual-basic/language-reference/xml-literals/index.md)  
 [Création de code XML dans Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [Expressions incorporées en XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)  
 [Imports (instruction) (espace de noms XML)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)
