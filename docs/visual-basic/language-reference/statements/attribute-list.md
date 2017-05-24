---
title: Attribut liste (Visual Basic) | Documents Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- attribute list
- attributes [Visual Basic], applying
ms.assetid: 5880073a-68a4-4b6b-8a07-ace32959a4e2
caps.latest.revision: 18
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: e360794ad217784e2358967bfbcc03959cd043b1
ms.contentlocale: fr-fr
ms.lasthandoff: 03/13/2017

---
# <a name="attribute-list-visual-basic"></a>Liste d'attributs (Visual Basic)
Spécifie les attributs à appliquer à un élément de programmation déclaré. Les attributs multiples sont séparés par des virgules. Voici la syntaxe pour un attribut.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[ attributemodifier ] attributename [ ( attributearguments | attributeinitializer ) ]  
```  
  
## <a name="parts"></a>Composants  
 `attributemodifier`  
 Requis pour les attributs appliqués au début d’un fichier source. Peut être [Assembly](../../../visual-basic/language-reference/modifiers/assembly.md) ou [Module](../../../visual-basic/language-reference/modifiers/module-keyword.md).  
  
 `attributename`  
 Obligatoire. Nom de l'attribut.  
  
 `attributearguments`  
 Facultatif. Liste d’arguments de position pour cet attribut. Plusieurs arguments sont séparés par des virgules.  
  
 `attributeinitializer`  
 Facultatif. Liste d’initialiseurs de variable ou une propriété de cet attribut. Les initialiseurs multiples sont séparées par des virgules.  
  
## <a name="remarks"></a>Remarques  
 Vous pouvez appliquer un ou plusieurs attributs à quasiment n’importe quel élément de programmation (types, procédures, propriétés, etc.). Les attributs apparaissent dans les métadonnées de votre assembly, et ils peuvent vous aider à annoter votre code ou de spécifier la façon d’utiliser un élément de programmation particulier. Vous pouvez appliquer des attributs définis par Visual Basic et le .NET Framework, et vous pouvez définir vos propres attributs.  

 Pour plus d’informations sur l’utilisation d’attributs, consultez [vue d’ensemble des attributs](../../../visual-basic/programming-guide/concepts/attributes/index.md). Pour plus d’informations sur les noms d’attributs, consultez [noms d’éléments déclarés](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
## <a name="rules"></a>Règles  
  
-   **Sélection élective.** Vous pouvez appliquer des attributs aux éléments de programmation plus déclarés. Pour appliquer un ou plusieurs attributs, placez un *bloc d’attributs* au début de la déclaration d’élément. Chaque entrée dans la liste d’attributs Spécifie un attribut que vous souhaitez appliquer, et le modificateur et les arguments que vous utilisez pour cet appel de l’attribut.  
  
-   **Crochets pointus.** Si vous fournissez une liste d’attributs, vous devez le placer entre crochets pointus («`<`« et »`>`»).  
  
-   **Partie de la déclaration.** L’attribut doit faire partie de la déclaration d’élément, pas une instruction séparée. Vous pouvez utiliser la séquence de continuation de ligne (« `_`») pour étendre l’instruction de déclaration sur plusieurs lignes de code source.  
  
-   **Modificateurs.** Un modificateur d’attribut (`Assembly` ou `Module`) est requis sur chaque attribut appliqué à un élément de programmation au début d’un fichier source. Les modificateurs d’attribut ne sont pas autorisés sur les attributs appliqués à des éléments qui ne sont pas au début d’un fichier source.  
  
-   **Arguments.** Tous les arguments positionnels d’un attribut doivent précéder les initialiseurs de variable ou propriété.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant applique le <xref:System.Runtime.InteropServices.DllImportAttribute>attribut à une définition squelette d’un `Function` procédure.</xref:System.Runtime.InteropServices.DllImportAttribute>  
  
 [!code-vb[VbVbalrStatements n °&1;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/attribute-list_1.vb)]  
  
 <xref:System.Runtime.InteropServices.DllImportAttribute>Indique que la procédure attribuée représente un point d’entrée dans une bibliothèque de liens dynamiques (DLL) non managée.</xref:System.Runtime.InteropServices.DllImportAttribute> L’attribut fournit le nom de la DLL comme argument positionnel et l’autre information comme initialiseurs de variable.  
  
## <a name="see-also"></a>Voir aussi  
 [Assemblage](../../../visual-basic/language-reference/modifiers/assembly.md)   
 [Module \<mot-clé >](../../../visual-basic/language-reference/modifiers/module-keyword.md)   
 [Vue d’ensemble des attributs](../../../visual-basic/programming-guide/concepts/attributes/index.md)   
 [Guide pratique : diviser et combiner des instructions dans le code](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)

