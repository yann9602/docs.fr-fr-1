---
title: "Déclaré des noms d’élément (Visual Basic) | Documents Microsoft"
ms.custom: 
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
- declared elements, case sensitivity
- names, Visual Basic rules
- naming conventions
- element names
- declared elements, identifiers
- declarations, elements
- declared elements, valid names
- '[] escape characters [Visual Basic]'
- names, elements
- declaration statements, declared elements
- declaring elements
- identifiers, declared elements
- case sensitivity, declared element names
- escape characters
- names, declared elements
- declared elements, about declared elements
- escaped names
- declared elements, names
- names, naming conventions
- identifiers, elements
ms.assetid: 09d8843b-c0dc-4afe-9dab-87c439a69e66
caps.latest.revision: 27
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
ms.openlocfilehash: 56ac0684e5176f33aa6f9600f20d9fe3fcf09416
ms.lasthandoff: 03/13/2017

---
# <a name="declared-element-names-visual-basic"></a>Noms d'éléments déclarés (Visual Basic)
Chaque élément déclaré a un nom, également appelé un *identificateur*, qui est utilisée par le code qui y fait référence.  
  
## <a name="rules"></a>Règles  
 Un nom d’élément dans [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] doit respecter les règles suivantes :  
  
-   Il doit commencer par un caractère alphabétique ou un trait de soulignement (`_`).  
  
-   Il doit uniquement contenir des caractères alphabétiques, des chiffres et des traits de soulignement.  
  
-   Il doit contenir au moins un caractère alphabétique ou un chiffre décimal s’il commence par un trait de soulignement.  
  
-   Il ne doit pas être 1023 caractères.  
  
 La longueur maximale de 1023 caractères s’applique également à la chaîne entière d’un nom qualifié complet, tel que `outerNamespace.middleNamespace.innerNamespace.thisClass.thisElement`.  
  
 L’exemple suivant illustre certains noms d’éléments valides.  
  
 `aB123__45`  
  
 `_567`  
  
 L’exemple suivant illustre certains noms d’élément non valide. Le premier contient uniquement un trait de soulignement, le second commence par un chiffre décimal et le troisième contient un caractère non valide ($).  
  
 `' Three INVALID element names`  
  
 `_`  
  
 `12ABC`  
  
 `xyz$wv`  
  
> [!CAUTION]
>  Les noms d’élément commençant par un trait de soulignement (`_`) ne font pas partie de la [indépendance du langage et composants indépendants du langage](https://msdn.microsoft.com/library/12a7a7h3) (CLS), le code conforme CLS ne peut pas utiliser un composant qui définit ces noms. Toutefois, un trait de soulignement dans n’importe quelle autre position dans un nom d’élément est conforme à CLS.  
  
### <a name="name-length-guidelines"></a>Instructions de longueur de nom  
 Un point de vue pratique, votre nom doit être aussi court que possible tout en identifiant clairement la nature de l’élément. Cela améliore la lisibilité de votre code et réduit la taille de fichier source et de longueur de ligne.  
  
 En revanche, votre nom ne doit pas être court qu’il ne pas décrire suffisamment ce que l’élément représente et comment votre code l’utilise. Ceci est important pour la lisibilité de votre code. Si une autre personne essaie de le comprendre ou si vous devez l’observer longtemps après que l’avoir écrit, noms d’éléments appropriés peuvent enregistrer un temps considérable.  
  
## <a name="escaped-names"></a>Noms d’échappement  
 En règle générale, un nom d’élément ne doit pas correspondre à aucun des mots clés réservés par [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], tel que `Case` ou `Friend`. Toutefois, vous pouvez définir un *nom échappement*, qui est placé entre crochets (`[ ]`). Un nom d’échappement peut correspondre à une [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] (mot clé), puisque les crochets lève toute ambiguïté. Vous utilisez également les crochets lorsque vous faites référence au nom ultérieurement dans votre code.  
  
 En général, vous devez utiliser des noms échappés uniquement lorsque :  
  
-   Votre code a migré à partir d’une version précédente de [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] qui n’a pas réservé le mot clé utilisé comme un nom ; ou  
  
-   Vous travaillez avec du code écrit dans un autre langage dans lequel le mot clé donné n’est pas réservé.  
  
 Sinon, vous devez envisager de renommer l’élément si son nom est en conflit avec un mot clé. L’environnement de développement intégré (IDE) fournit un moyen simple de le faire. Pour plus d’informations, consultez [Refactoring](https://docs.microsoft.com/visualstudio/vb-ide/refactoring-vb).  
  
## <a name="case-sensitivity-in-names"></a>Respect de la casse dans les noms  
 Noms de l’élément dans [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] respectent la casse. Cela signifie que lorsque le compilateur compare deux noms qui diffèrent uniquement par la casse des lettres, il les interprète comme le même nom. Par exemple, il considère que `ABC` et `abc` font référence au même élément déclaré.  
  
 Néanmoins, le common language runtime (CLR) utilise des liaisons qui respecte la casse. Ainsi, quand vous générez un assembly ou une DLL et que vous le mettez à disposition d’autres assemblys, la casse de vos noms est respectée. Par exemple, si vous définissez une classe avec un élément nommé `ABC`et que d’autres assemblys utilisent votre classe par le biais du Common Language Runtime, ils doivent faire référence à l’élément en tant que `ABC`. Si vous recompilez votre classe par la suite et modifier le nom de l’élément à `abc`, les autres assemblys qui utilisent votre classe peuvent ne plus accéder à cet élément. Ainsi, quand vous publiez une version mise à jour d’un assembly, vous ne devez pas modifier la casse des éléments publics.  
  
## <a name="names-and-locales"></a>Les noms et les paramètres régionaux  
 Comparaison des noms est indépendante des paramètres régionaux. Si deux noms correspondent dans des paramètres régionaux, ils sont assurés à faire correspondre dans tous les paramètres régionaux.  
  
## <a name="see-also"></a>Voir aussi  
 [Éléments déclarés](../../../../visual-basic/programming-guide/language-features/declared-elements/index.md)   
 [Caractéristiques d’éléments déclarés](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)   
 [Références aux éléments déclarés](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)   
 [Instructions](../../../../visual-basic/language-reference/statements/index.md)
