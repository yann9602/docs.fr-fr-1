---
title: "Noms d'éléments déclarés (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- declared elements [Visual Basic], case sensitivity
- names [Visual Basic], Visual Basic rules
- naming conventions [Visual Basic]
- element names [Visual Basic]
- declared elements [Visual Basic], identifiers
- declarations [Visual Basic], elements
- declared elements [Visual Basic], valid names
- '[] escape characters [Visual Basic]'
- names [Visual Basic], elements
- declaration statements [Visual Basic], declared elements
- declaring elements [Visual Basic]
- identifiers [Visual Basic], declared elements
- case sensitivity, declared element names
- escape characters [Visual Basic]
- names [Visual Basic], declared elements
- declared elements [Visual Basic], about declared elements
- escaped names [Visual Basic]
- declared elements [Visual Basic], names
- names [Visual Basic], naming conventions
- identifiers [Visual Basic], elements
ms.assetid: 09d8843b-c0dc-4afe-9dab-87c439a69e66
caps.latest.revision: "27"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 691b65280b958edcf8e856ee6df793e0b7b05184
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="declared-element-names-visual-basic"></a>Noms d'éléments déclarés (Visual Basic)
Chaque élément déclaré a un nom, également appelé un *identificateur*, qui est utilisé par le code qui y fait référence.  
  
## <a name="rules"></a>Règles  
 Un nom d’élément dans [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] doit respecter les règles suivantes :  
  
-   Il doit commencer par un caractère alphabétique ou un trait de soulignement (`_`).  
  
-   Il doit contenir uniquement des caractères alphabétiques, des chiffres décimaux et des traits de soulignement.  
  
-   Il doit contenir au moins un caractère alphabétique ou un chiffre décimal s’il commence par un trait de soulignement.  
  
-   Il ne doit pas être plus de 1023 caractères.  
  
 La longueur maximale de 1023 caractères s’applique également à la chaîne entière d’un nom qualifié complet, tel que `outerNamespace.middleNamespace.innerNamespace.thisClass.thisElement`.  
  
 L’exemple suivant illustre certains noms d’élément valide.  
  
 `aB123__45`  
  
 `_567`  
  
 L’exemple suivant illustre certains noms d’élément non valide. Le premier contient uniquement un trait de soulignement, le second commence par un chiffre décimal et le troisième contient un caractère non valide ($).  
  
 `' Three INVALID element names`  
  
 `_`  
  
 `12ABC`  
  
 `xyz$wv`  
  
> [!CAUTION]
>  Les noms d’élément commençant par un trait de soulignement (`_`) ne font pas partie de la [indépendance du langage et composants indépendants du langage](https://msdn.microsoft.com/library/12a7a7h3) (CLS), le code conforme CLS ne peut pas utiliser un composant qui définit les noms de ce type. Toutefois, un trait de soulignement dans n’importe quelle autre position dans un nom d’élément est conforme à CLS.  
  
### <a name="name-length-guidelines"></a>Instructions de longueur de nom  
 Un point de vue pratique, votre nom doit être aussi court que possible tout en identifiant clairement la nature de l’élément. Cela améliore la lisibilité de votre code et réduit la taille du fichier source et de longueur de ligne.  
  
 En revanche, votre nom ne doit pas être court que ne pas correctement décrit ce que représente l’élément et la façon dont votre code utilise. Ceci est important pour la lisibilité de votre code. Si quelqu'un d’autre tente de le comprendre, ou si vous devez l’observer longtemps après que l’avoir écrit, noms d’éléments appropriés peuvent enregistrer un temps considérable.  
  
## <a name="escaped-names"></a>Noms d’échappement  
 En règle générale, un nom d’élément ne doit pas correspondre à un des mots clés réservés par [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)], tel que `Case` ou `Friend`. Toutefois, vous pouvez définir un *nom échappement*, lequel est placé entre crochets (`[ ]`). Un nom d’échappement peut correspondre à tout [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] (mot clé), étant donné que les crochets supprimer toute ambiguïté. Vous utilisez également les crochets lorsque vous faites référence au nom ultérieurement dans votre code.  
  
 En règle générale, vous devez utiliser des noms échappés uniquement lorsque :  
  
-   Votre code a migré à partir d’une version antérieure de [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] qui n’a pas réservé le mot clé utilisé comme un nom ; ou  
  
-   Vous travaillez avec du code écrit dans un autre langage dans lequel le mot clé donné n’est pas réservé.  
  
 Dans le cas contraire, vous devez envisager de renommer l’élément si son nom est en conflit avec un mot clé. L’environnement de développement intégré (IDE) fournit un moyen simple pour ce faire. Pour plus d’informations, consultez [Refactoring](/visualstudio/vb-ide/refactoring-vb).  
  
## <a name="case-sensitivity-in-names"></a>Respect de la casse dans les noms  
 Noms d’élément dans [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] respectent pas la casse. Cela signifie que lorsque le compilateur compare deux noms qui diffèrent uniquement par la casse des lettres, il les interprète comme étant le même nom. Par exemple, il considère que `ABC` et `abc` font référence au même élément déclaré.  
  
 Toutefois, le common language runtime (CLR) utilise une liaison qui respecte la casse. Ainsi, quand vous générez un assembly ou une DLL et que vous le mettez à disposition d’autres assemblys, la casse de vos noms est respectée. Par exemple, si vous définissez une classe avec un élément nommé `ABC`et que d’autres assemblys utilisent votre classe par le biais du Common Language Runtime, ils doivent faire référence à l’élément en tant que `ABC`. Si vous recompilez votre classe par la suite et modifier le nom de l’élément à `abc`, les autres assemblys utilisent votre classe pourraient ne plus accéder à cet élément. Ainsi, quand vous publiez une version mise à jour d’un assembly, vous ne devez pas modifier la casse des éléments publics.  
  
## <a name="names-and-locales"></a>Les noms et les paramètres régionaux  
 Comparaison des noms est indépendante des paramètres régionaux. Si deux noms correspondent dans des paramètres régionaux, ils sont garanties à faire correspondre dans tous les paramètres régionaux.  
  
## <a name="see-also"></a>Voir aussi  
 [Éléments déclarés](../../../../visual-basic/programming-guide/language-features/declared-elements/index.md)  
 [Caractéristiques d’éléments déclarés](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)  
 [Références aux éléments déclarés](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [Instructions](../../../../visual-basic/language-reference/statements/index.md)
