---
title: Imports, instruction (.NET Namespace et Type) | Documents Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Imports
- imports
dev_langs:
- VB
helpviewer_keywords:
- declared element names [Visual Basic], qualification
- imports [Visual Basic]
- Imports statement [Visual Basic]
- aliases [Visual Basic], Imports statement
- container elements [Visual Basic]
- namespaces [Visual Basic], importing
- Imports statement [Visual Basic], syntax
- import aliases [Visual Basic]
- aliases [Visual Basic], import
- declared elements [Visual Basic], container elements
ms.assetid: 7062f8aa-d890-4232-9eed-92836e13fb6e
caps.latest.revision: 40
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
ms.openlocfilehash: 393f3e9a264817d8658585267c954d973290530a
ms.lasthandoff: 03/13/2017

---
# <a name="imports-statement-net-namespace-and-type"></a>Imports, instruction (espace de noms et type .NET)
Permet d’attribuer des noms d’être référencés sans qualification d’espace de noms.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Imports [ aliasname = ] namespace  
-or-  
Imports [ aliasname = ] namespace.element  
```  
  
## <a name="parts"></a>Composants  
  
|Terme|Définition|  
|---|---|  
|`aliasname`|Facultatif. Un *alias d’importation* ou le nom par lequel le code peut faire référence à `namespace` au lieu de la chaîne de qualification complète. Consultez la page [noms d’éléments déclarés](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|  
|`namespace`|Obligatoire. Le nom qualifié complet de l’espace de noms importé. Une chaîne d’espaces de noms imbriquée à n’importe quel niveau.|  
|`element`|Facultatif. Le nom d’un élément de programmation déclaré dans l’espace de noms. Peut être n’importe quel élément conteneur.|  
  
## <a name="remarks"></a>Notes  
 La `Imports` instruction permet aux types qui sont contenus dans un espace de noms donné soient référencés directement.  
  
 Vous pouvez fournir un nom d’espace de noms unique ou une chaîne d’espaces de noms imbriqués. Chaque espace de noms imbriqué est séparé de l’espace de noms au niveau supérieur suivant par un point (`.`), comme l’illustre l’exemple suivant.  
  
 `Imports System.Collections.Generic`  
  
 Chaque fichier source peut contenir un nombre quelconque de `Imports` instructions. Ces derniers doivent respecter les déclarations d’option, telles que la `Option Strict` instruction et elles doivent précéder les déclarations d’élément de programmation, telles que `Module` ou `Class` instructions.  
  
 Vous pouvez utiliser `Imports` uniquement au niveau fichier. Cela signifie que le contexte de déclaration pour l’importation doit être un fichier source et ne peut pas être un espace de noms, classe, structure, module, interface, procédure ou bloc.  
  
 Notez que la `Imports` instruction ne rend pas les éléments d’autres projets et assemblys disponibles à votre projet. L’importation ne prend pas la place de la définition d’une référence. Il supprime uniquement la nécessité pour qualifier des noms qui sont déjà disponibles pour votre projet. Pour plus d’informations, consultez « Importation d’éléments conteneurs » dans [références aux éléments déclarés](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
> [!NOTE]
>  Vous pouvez définir implicite `Imports` les instructions à l’aide de la [Page références, Concepteur de projets (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/references-page-project-designer-visual-basic). Pour plus d’informations, consultez [Comment : ajouter ou supprimer des espaces de noms importés (Visual Basic)](http://msdn.microsoft.com/library/44cebec3-0ea0-47c2-8406-4edeab6a997e).  
  
## <a name="import-aliases"></a>Alias d’importation  
 Un *alias d’importation* définit l’alias d’espace de noms ou type. Alias d’importation sont utiles lorsque vous devez utiliser des éléments portant le même nom sont déclarées dans un ou plusieurs espaces de noms. Pour plus d’informations et un exemple, consultez « Qualification d’un nom d’élément » dans [références aux éléments déclarés](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
 Vous ne devez pas déclarer un membre au niveau du module avec le même nom que `aliasname`. Si vous le faites, le compilateur Visual Basic utilise `aliasname` uniquement pour le membre déclaré et ne plus l’identifie comme un alias d’importation.  
  
 Bien que la syntaxe utilisée pour déclarer un alias d’importation est celui utilisée pour importer un préfixe d’espace de noms XML, les résultats sont différents. Un alias d’importation peut être utilisé comme expression dans votre code, alors qu’un préfixe d’espace de noms XML peut être utilisé uniquement dans les littéraux XML ou de propriétés d’axe XML comme préfixe pour un élément qualifié ou un nom d’attribut.  
  
### <a name="element-names"></a>Noms des éléments  
 Si vous fournissez `element`, il doit représenter un *élément conteneur*, autrement dit, un élément de programmation qui peut contenir d’autres éléments. Éléments conteneurs comprennent des classes, structures, modules, interfaces et énumérations.  
  
 La portée des éléments mis à disposition par une `Imports` instruction varie selon que vous spécifiez `element`. Si vous spécifiez uniquement `namespace`, tout unique nommé membres de cet espace de noms et les membres des éléments conteneurs présents dans cet espace de noms, sont disponibles sans qualification. Si vous spécifiez les deux `namespace` et `element`, seuls les membres de cet élément sont disponibles sans qualification.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant retourne tous les dossiers dans le répertoire C:\ à l’aide de la <xref:System.IO.DirectoryInfo>classe.</xref:System.IO.DirectoryInfo>  
  
 Le code n’a pas `Imports` au début du fichier. Par conséquent, le `DirectoryInfo`, <xref:System.Text.StringBuilder>, et <xref:Microsoft.VisualBasic.ControlChars.CrLf>les références sont entièrement qualifiées avec les espaces de noms.</xref:Microsoft.VisualBasic.ControlChars.CrLf> </xref:System.Text.StringBuilder>  
  
 [!code-vb[VbVbalrStatements&#152;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_1.vb)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant inclut `Imports` instructions pour les espaces de noms référencés. Par conséquent, les types n’ont pas à être entièrement qualifiés avec les espaces de noms.  
  
 [!code-vb[VbVbalrStatements&#153;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_2.vb)]  
  
 [!code-vb[VbVbalrStatements&#154;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_3.vb)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant inclut `Imports` instructions qui créent des alias pour les espaces de noms référencés. Les types sont qualifiés avec les alias.  
  
 [!code-vb[VbVbalrStatements&#155;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_4.vb)]  
  
 [!code-vb[VbVbalrStatements&#156;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_5.vb)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant inclut `Imports` instructions qui créent des alias pour les types référencés. Alias sont utilisés pour spécifier les types.  
  
 [!code-vb[VbVbalrStatements&#157;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_6.vb)]  
  
 [!code-vb[VbVbalrStatements&#158;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_7.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 [Déclaration de Namespace](../../../visual-basic/language-reference/statements/namespace-statement.md)   
 [Espaces de noms dans Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md)   
 [Références et l’instruction Imports](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)   
 [Imports, instruction (Namespace XML)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)   
 [Références aux éléments déclarés](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
