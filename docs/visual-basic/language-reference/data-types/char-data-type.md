---
title: "Char, type de données (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Char
helpviewer_keywords:
- literal type characters [Visual Basic], C
- Char data type
- C literal type character [Visual Basic]
- data types [Visual Basic], assigning
- Char data type [Visual Basic], character literals
ms.assetid: cd7547a9-7855-4e8e-b216-35d74a362657
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 16ff547fccbf4481d31ca79537962cc7090fc9b0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="char-data-type-visual-basic"></a>Char, type de données (Visual Basic)
Contient les points de code de (2 octets) de 16 bits non signé compris entre 0 et 65 535. Chaque *point de code*, ou le code de caractère, représente un caractère Unicode.  
  
## <a name="remarks"></a>Remarques  
 Utilisez le `Char` lorsque vous avez besoin contenir un seul type de données de caractères et n’avez pas besoin de la charge de `String`. Dans certains cas, vous pouvez utiliser `Char()`, un tableau de `Char` éléments, pour contenir plusieurs caractères.  
  
 La valeur par défaut de `Char` est le caractère avec un point de code de 0.  
  
## <a name="unicode-characters"></a>Caractères Unicode  
 Les premiers points de 128 code (0 à 127) Unicode correspondent aux lettres et des symboles sur un clavier américain standard. Ces premiers points de 128 code sont les mêmes que ceux du jeu de caractères ASCII. Les deuxième 128 points de code (128 à 255) représentent des caractères spéciaux, tels que des lettres de l’alphabet de latines, les accents, les symboles monétaires et les fractions. Unicode utilise les points de code restants (256-65 535) pour un large éventail de symboles, y compris les caractères textuels mondiaux, les signes diacritiques et les symboles mathématiques et techniques.  
  
 Vous pouvez utiliser les méthodes, telles que <xref:System.Char.IsDigit%2A> et <xref:System.Char.IsPunctuation%2A> sur une `Char` variable pour déterminer sa classification Unicode.  
  
## <a name="type-conversions"></a>Conversions de type  
 Visual Basic ne convertit pas directement entre `Char` et les types numériques. Vous pouvez utiliser la <xref:Microsoft.VisualBasic.Strings.Asc%2A> ou <xref:Microsoft.VisualBasic.Strings.AscW%2A> fonction pour convertir un `Char` valeur un `Integer` qui représente son point de code. Vous pouvez utiliser la <xref:Microsoft.VisualBasic.Strings.Chr%2A> ou <xref:Microsoft.VisualBasic.Strings.ChrW%2A> fonction pour convertir une `Integer` valeur un `Char` qui a ce point de code.  
  
 Si le commutateur de la vérification de type ([Option Strict, instruction](../../../visual-basic/language-reference/statements/option-strict-statement.md)) est activé, vous devez ajouter le caractère de type littéral à un seul caractère littéral de chaîne à l’identifier en tant que le `Char` type de données. L'exemple suivant illustre ce comportement.  
  
```  
Option Strict On  
Dim charVar As Char  
' The following statement attempts to convert a String literal to Char.  
' Because Option Strict is On, it generates a compiler error.  
charVar = "Z"  
' The following statement succeeds because it specifies a Char literal.  
charVar = "Z"C  
```  
  
## <a name="programming-tips"></a>Conseils de programmation  
  
-   **Nombres négatifs.** `Char`est un type non signé et ne peut pas représenter une valeur négative. Dans tous les cas, vous ne devez pas utiliser `Char` pour contenir des valeurs numériques.  
  
-   **Considérations sur l’interopérabilité.** Si vous utilisez des composants non écrits pour le .NET Framework, par exemple des objets Automation ou COM, n’oubliez pas que les types de caractère ont une largeur de données différente (8 bits) dans d’autres environnements. Si vous passez un argument de 8 bits à un tel composant, déclarez-le en tant que `Byte` au lieu de `Char` dans votre nouveau code Visual Basic.  
  
-   **Étendues.** Le `Char` type de données s’étend à `String`. Cela signifie que vous pouvez convertir `Char` à `String` et vous ne rencontrerez pas un <xref:System.OverflowException?displayProperty=nameWithType> erreur.  
  
-   **Caractères de type.** L’ajout du caractère de type de littéral `C` à une chaîne à un caractère littéral force ce dernier à la `Char` type de données. `Char`n’a aucun caractère de type d’identificateur.  
  
-   **Type .NET Framework.** Le type correspondant dans le .NET Framework est la structure <xref:System.Char?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Char?displayProperty=nameWithType>  
 <xref:Microsoft.VisualBasic.Strings.Asc%2A>  
 <xref:Microsoft.VisualBasic.Strings.AscW%2A>  
 <xref:Microsoft.VisualBasic.Strings.Chr%2A>  
 <xref:Microsoft.VisualBasic.Strings.ChrW%2A>  
 [Types de données](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [String (type de données)](../../../visual-basic/language-reference/data-types/string-data-type.md)  
 [Fonctions de conversion de types](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Liste des conversions](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [Guide pratique : appeler une fonction Windows qui possède des types non signés](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)  
 [Utilisation efficace des types de données](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
