---
title: Liste d'attributs (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- attribute list
- attributes [Visual Basic], applying
ms.assetid: 5880073a-68a4-4b6b-8a07-ace32959a4e2
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: adfb980380bb787280715ca0185950657e174eb1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
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
 Facultatif. Liste des arguments de position pour cet attribut. Plusieurs arguments sont séparés par des virgules.  
  
 `attributeinitializer`  
 Facultatif. Liste d’initialiseurs de variable ou une propriété pour cet attribut. Les initialiseurs multiples sont séparées par des virgules.  
  
## <a name="remarks"></a>Remarques  
 Vous pouvez appliquer un ou plusieurs attributs à quasiment n’importe quel élément de programmation (types, procédures, propriétés et ainsi de suite). Les attributs apparaissent dans les métadonnées de votre assembly, et ils peuvent vous aider à annoter votre code ou de spécifier l’utilisation d’un élément de programmation particulier. Vous pouvez appliquer des attributs définis par Visual Basic et .NET Framework, et vous pouvez définir vos propres attributs.  

 Pour plus d’informations sur l’utilisation d’attributs, consultez [vue d’ensemble des attributs](../../../visual-basic/programming-guide/concepts/attributes/index.md). Pour plus d’informations sur les noms d’attributs, consultez [noms d’élément déclaré](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
## <a name="rules"></a>Règles  
  
-   **Sélection élective.** Vous pouvez appliquer des attributs aux éléments de programmation déclarés plus. Pour appliquer un ou plusieurs attributs, placez un *bloc d’attributs* au début de la déclaration d’élément. Chaque entrée dans la liste d’attributs Spécifie un attribut que vous souhaitez appliquer, et le modificateur et les arguments que vous utilisez pour cet appel de l’attribut.  
  
-   **Crochets pointus.** Si vous fournissez une liste d’attributs, vous devez le placer entre crochets pointus («`<`« et »`>`»).  
  
-   **Partie de la déclaration.** L’attribut doit faire partie de la déclaration d’élément, pas une instruction séparée. Vous pouvez utiliser la séquence de continuation de ligne (« `_`») pour étendre l’instruction de déclaration sur plusieurs lignes de code source.  
  
-   **Modificateurs.** Un modificateur d’attribut (`Assembly` ou `Module`) est requis sur chaque attribut appliqué à un élément de programmation au début d’un fichier source. Les modificateurs d’attribut ne sont pas autorisés sur les attributs appliqués à des éléments qui ne sont pas au début d’un fichier source.  
  
-   **Arguments.** Tous les arguments de position d’un attribut doivent précéder les initialiseurs de variable ou propriété.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant applique la <xref:System.Runtime.InteropServices.DllImportAttribute> d’attribut à une définition squelette d’une `Function` procédure.  
  
 [!code-vb[VbVbalrStatements#1](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/attribute-list_1.vb)]  
  
 <xref:System.Runtime.InteropServices.DllImportAttribute>Indique que la procédure attribuée représente un point d’entrée dans une bibliothèque de liens dynamiques (DLL) non managée. L’attribut fournit le nom de la DLL comme argument positionnel et l’autre information comme initialiseurs de variable.  
  
## <a name="see-also"></a>Voir aussi  
 [Assembly](../../../visual-basic/language-reference/modifiers/assembly.md)  
 [\<mot clé> du module](../../../visual-basic/language-reference/modifiers/module-keyword.md)  
 [Vue d’ensemble des attributs](../../../visual-basic/programming-guide/concepts/attributes/index.md)  
 [Guide pratique : diviser et combiner des instructions dans le code](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
