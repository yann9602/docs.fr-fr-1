---
title: Imports, instruction (espace de noms XML)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.ImportsXmlns
helpviewer_keywords:
- XML namespace [Visual Basic], importing
- imports [Visual Basic]
- Imports statement [Visual Basic]
- namespaces [Visual Basic], importing
ms.assetid: 1f4d50a6-08c7-4c2e-8206-ccae35fcd1b4
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a0fe6d37c58ead94f2c03736318209abb67cd6dc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="imports-statement-xml-namespace"></a>Imports, instruction (espace de noms XML)
Importe des préfixes d’espace de noms XML pour une utilisation dans les littéraux XML et les propriétés d’axe XML.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Imports <xmlns:xmlNamespacePrefix = "xmlNamespaceName">  
```  
  
## <a name="parts"></a>Composants  
 `xmlNamespacePrefix`  
 Facultatif. La chaîne par laquelle le langage XML éléments et attributs peuvent faire référence à `xmlNamespaceName`. Si aucun `xmlNamespacePrefix` est fourni, l’espace de noms XML importé est l’espace de noms XML par défaut. Doit être un identificateur XML valide. Pour plus d’informations, consultez [les attributs et les noms des éléments XML déclarés](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).  
  
 `xmlNamespaceName`  
 Obligatoire. Chaîne identifiant l’espace de noms XML importé.  
  
## <a name="remarks"></a>Remarques  
 Vous pouvez utiliser la `Imports` instruction afin de définir des espaces de noms XML global que vous pouvez utiliser avec les littéraux XML et les propriétés d’axe XML, ou comme paramètres passés à la `GetXmlNamespace` opérateur. (Pour plus d’informations sur l’utilisation de la `Imports` instruction pour importer un alias qui peut être utilisé lorsque des noms de type sont utilisés dans votre code, consultez [Imports, instruction (.NET Namespace et Type)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).) La syntaxe de déclaration d’espace de noms XML à l’aide de la `Imports` instruction est identique à la syntaxe utilisée dans XML. Par conséquent, vous pouvez copier une déclaration d’espace de noms à partir d’un fichier XML et l’utiliser dans un `Imports` instruction.  
  
 Les préfixes d’espace de noms XML sont utiles lorsque vous souhaitez créer des éléments XML qui sont du même espace de noms à plusieurs reprises. Le préfixe d’espace de noms XML déclaré avec le `Imports` instruction est globale en ce sens qu’il est disponible à tout le code dans le fichier. Vous pouvez l’utiliser lorsque vous créez des littéraux d’éléments XML et lorsque vous accédez à des propriétés d’axe XML. Pour plus d’informations, consultez [XML élément Literal](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md) et [propriétés d’axe XML](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md).  
  
 Si vous définissez un espace de noms XML global sans préfixe d’espace de noms (par exemple, `Imports <xmlns="http://SomeNameSpace>"`), cet espace de noms est considéré comme l’espace de noms XML par défaut. L’espace de noms XML par défaut est utilisé pour les littéraux d’élément XML ou les propriétés d’axe d’attribut XML qui ne spécifient pas explicitement un espace de noms. L’espace de noms par défaut est également utilisée si l’espace de noms spécifié est l’espace de noms vide (autrement dit, `xmlns=""`). L’espace de noms XML par défaut ne s’applique pas aux attributs XML dans les littéraux XML ou aux propriétés d’axe d’attribut XML qui n’ont pas d’un espace de noms.  
  
 Espaces de noms XML qui sont définis dans un littéral XML, qui sont appelés *des espaces de noms XML local*, sont prioritaires sur les espaces de noms XML qui sont définis par le `Imports` instruction comme étant global. Les espaces de noms XML qui sont définis par le `Imports` instruction sont prioritaires sur les espaces de noms XML importé pour un projet Visual Basic. Si un littéral XML définit un espace de noms XML, cet espace de noms local ne s’applique pas aux expressions incorporées.  
  
 Espaces de noms XML globaux suivent les mêmes règles de portée et de définition en tant que les espaces de noms .NET Framework. Par conséquent, vous pouvez inclure une `Imports` instruction afin de définir un espace de noms XML global partout où vous pouvez importer un espace de noms .NET Framework. Cela inclut les fichiers de code et les espaces de noms importés au niveau du projet. Pour plus d’informations sur les espaces de noms importés au niveau du projet, consultez [Page références, Concepteur de projets (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic).  
  
 Chaque fichier source peut contenir un nombre quelconque de `Imports` instructions. Ces derniers doivent respecter les déclarations d’option, telles que la `Option Strict` instruction et doivent précéder les déclarations d’élément de programmation, tels que `Module` ou `Class` instructions.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant importe un espace de noms XML par défaut et un espace de noms XML identifié par le préfixe `ns`. Il crée ensuite des littéraux XML qui utilisent les deux espaces de noms.  
  
 [!code-vb[VbXMLSamples#45](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/imports-statement-xml-namespace_1.vb)]  
  
 Ce code affiche le texte suivant :  
  
```xml  
<ns:outer xmlns="http://DefaultNamespace"   
          xmlns:ns="http://NewNamespace">  
  <ns:innerElement></ns:innerElement>  
  <siblingElement></siblingElement>  
  <innerElement />  
</ns:outer>  
```  
  
## <a name="example"></a>Exemple  
 L’exemple suivant importe le préfixe d’espace de noms XML `ns`. Il crée ensuite un littéral XML qui utilise le préfixe d’espace de noms et affiche la forme finale de l’élément.  
  
 [!code-vb[VbXMLSamples#22](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/imports-statement-xml-namespace_2.vb)]  
  
 Ce code affiche le texte suivant :  
  
```xml  
<ns:outer xmlns:ns="http://SomeNamespace">  
  <ns:middle xmlns:ns="http://NewNamespace">  
    <ns:inner1 />  
    <inner2 xmlns="http://SomeNamespace" />  
  </ns:middle>  
</ns:outer>  
```  
  
 Notez que le compilateur a converti le préfixe d’espace de noms XML à partir d’un préfixe global à une définition de préfixe local.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant importe le préfixe d’espace de noms XML `ns`. Il utilise ensuite le préfixe de l'espace de noms pour créer un littéral XML et accéder au premier nœud enfant avec le nom qualifié `ns:name`.  
  
 [!code-vb[VbXMLSamples#19](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/imports-statement-xml-namespace_3.vb)]  
  
 Ce code affiche le texte suivant :  
  
 `Patrick Hines`  
  
## <a name="see-also"></a>Voir aussi  
 [Littéral d’élément XML](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)  
 [Propriétés d’axe XML](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)  
 [Nom des attributs et des éléments XML déclarés](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)  
 [GetXmlNamespace (opérateur)](../../../visual-basic/language-reference/operators/getxmlnamespace-operator.md)
