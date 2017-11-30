---
title: "String, type de données (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.String
helpviewer_keywords:
- strings [Visual Basic], character
- strings [Visual Basic], fixed-length
- string keyword [Visual Basic]
- fixed-length strings [Visual Basic], string data type
- literals [Visual Basic], string
- text [Visual Basic], String data type
- $ identifier type character
- String data type
- fixed-length strings
- string literals [Visual Basic]
- data types [Visual Basic], assigning
- String literals [Visual Basic]
- identifier type characters [Visual Basic], $
ms.assetid: 15ac03f5-cabd-42cc-a754-1df3893c25d9
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 90f126a5cca36969617446e81a8d13434e39df75
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="string-data-type-visual-basic"></a>String, type de données (Visual Basic)
Contient des séquences de points de code de non signé 16 bits (2 octets) cette plage dans une valeur comprise entre 0 et 65 535. Chaque *point de code*, ou le code de caractère, représente un caractère Unicode. Une chaîne peut contenir de 0 à environ deux milliards (2 ^ 31) caractères Unicode.  
  
## <a name="remarks"></a>Remarques  
 Utilisez le `String` type de données pour contenir plusieurs caractères sans les charges de gestion tableau de `Char()`, un tableau de `Char` éléments.  
  
 La valeur par défaut `String` est `Nothing` (une référence null). Notez que cela n’est pas identique à la chaîne vide (valeur `""`).  
  
## <a name="unicode-characters"></a>Caractères Unicode  
 Les premiers points de 128 code (0 à 127) Unicode correspondent aux lettres et des symboles sur un clavier américain standard. Ces premiers points de 128 code sont les mêmes que ceux du jeu de caractères ASCII. Les deuxième 128 points de code (128 à 255) représentent des caractères spéciaux, tels que des lettres de l’alphabet de latines, les accents, les symboles monétaires et les fractions. Unicode utilise les points de code restants (256-65 535) pour une large gamme de symboles. Cela inclut les caractères textuels mondiaux, les signes diacritiques et les symboles mathématiques et techniques.  
  
 Vous pouvez utiliser des méthodes telles que <xref:System.Char.IsDigit%2A> et <xref:System.Char.IsPunctuation%2A> sur un caractère dans un `String` variable pour déterminer sa classification Unicode.  
  
## <a name="format-requirements"></a>Exigences relatives au format  
 Vous devez placer un `String` littérale entre guillemets (`" "`). Si vous devez inclure un guillemet comme l’un des caractères dans la chaîne, vous utilisez deux guillemets contigus (`""`). L'exemple suivant illustre ce comportement.  
  
```  
Dim j As String = "Joe said ""Hello"" to me."  
Dim h As String = "Hello"  
' The following messages all display the same thing:  
' "Joe said "Hello" to me."  
MsgBox(j)  
MsgBox("Joe said " & """" & h & """" & " to me.")  
MsgBox("Joe said """ & h & """ to me.")  
```  
  
 Notez que les guillemets contigus qui représentent un guillemet dans la chaîne sont indépendants des guillemets qui commencent et terminent le `String` littéral.  
  
## <a name="string-manipulations"></a>Manipulations de chaînes  
 Une fois que vous assignez une chaîne à un `String` variable, cette chaîne est *immuable*, ce qui signifie que vous ne pouvez pas modifier sa longueur ou son contenu. Lorsque vous modifiez une chaîne en aucune façon, Visual Basic crée une nouvelle chaîne et abandonne la précédente. Le `String` variable puis pointe vers la nouvelle chaîne.  
  
 Vous pouvez manipuler le contenu d’un `String` variable à l’aide de diverses fonctions de chaîne. L’exemple suivant illustre la <xref:Microsoft.VisualBasic.Strings.Left%2A> (fonction)  
  
```  
Dim S As String = "Database"  
' The following statement sets S to a new string containing "Data".  
S = Microsoft.VisualBasic.Left(S, 4)  
```  
  
 Une chaîne créée par un autre composant peut être remplie avec les espaces à gauche ou. Si vous recevez une telle chaîne, vous pouvez utiliser la <xref:Microsoft.VisualBasic.Strings.Trim%2A>, <xref:Microsoft.VisualBasic.Strings.LTrim%2A>, et <xref:Microsoft.VisualBasic.Strings.RTrim%2A> fonctions pour supprimer ces espaces.  
  
 Pour plus d’informations sur les manipulations de chaînes, consultez [chaînes](../../../visual-basic/programming-guide/language-features/strings/index.md).  
  
## <a name="programming-tips"></a>Conseils de programmation  
  
-   **Nombres négatifs.** Souvenez-vous que les caractères stockés par `String` ne sont pas signés et ne peut pas représenter des valeurs négatives. Dans tous les cas, vous ne devez pas utiliser `String` pour contenir des valeurs numériques.  
  
-   **Considérations sur l’interopérabilité.** Si vous utilisez des composants non écrits pour le .NET Framework, par exemple des objets Automation ou COM, n’oubliez pas que les chaînes de caractères possèdent une largeur de données différente (8 bits) dans d’autres environnements. Si vous passez un argument de chaîne de caractères 8 bits à un tel composant, déclarez-le en tant que `Byte()`, un tableau de `Byte` éléments, au lieu de `String` dans votre nouveau code Visual Basic.  
  
-   **Caractères de type.** L’ajout du caractère de type identificateur `$` à n’importe quel identificateur force ce dernier à la `String` type de données. `String`n’a aucun caractère de type de littéral. Toutefois, le compilateur traite les littéraux compris entre guillemets (`" "`) en tant que `String`.  
  
-   **Type .NET Framework.** Le type correspondant dans le .NET Framework est la <xref:System.String?displayProperty=nameWithType> classe.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.String?displayProperty=nameWithType>  
 [Types de données](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [Char (type de données)](../../../visual-basic/language-reference/data-types/char-data-type.md)  
 [Fonctions de conversion de types](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Liste des conversions](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [Guide pratique : appeler une fonction Windows qui possède des types non signés](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)  
 [Utilisation efficace des types de données](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
