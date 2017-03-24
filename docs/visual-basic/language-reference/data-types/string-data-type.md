---
title: "La chaîne de Type de données (Visual Basic) | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.String
dev_langs:
- VB
helpviewer_keywords:
- strings [Visual Basic], character
- strings [Visual Basic], fixed-length
- string keyword [Visual Basic]
- fixed-length strings, string data type
- literals, string
- text [Visual Basic], String data type
- $ identifier type character
- String data type
- fixed-length strings
- string literals
- data types [Visual Basic], assigning
- String literals
- identifier type characters, $
ms.assetid: 15ac03f5-cabd-42cc-a754-1df3893c25d9
caps.latest.revision: 19
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
ms.openlocfilehash: 9221a89a1fb46609b4b8550968e3a2bbe874772c
ms.lasthandoff: 03/13/2017

---
# <a name="string-data-type-visual-basic"></a>String, type de données (Visual Basic)
Contient des séquences de points de code de non signé 16 bits (2 octets) cette plage dans une valeur comprise entre 0 et 65 535. Chaque *point de code*, ou code de caractère, représente un caractère Unicode. Une chaîne peut contenir entre 0 et environ deux milliards (2 ^ 31) caractères Unicode.  
  
## <a name="remarks"></a>Remarques  
 Utilisez le `String` type de données pour contenir plusieurs caractères sans la surcharge de gestion tableau de `Char()`, un tableau de `Char` éléments.  
  
 La valeur par défaut `String` est `Nothing` (une référence null). Notez que cela n’est pas identique à la chaîne vide (valeur `""`).  
  
## <a name="unicode-characters"></a>Caractères Unicode  
 Les premiers points de 128 code (0 à 127) Unicode correspondent aux lettres et les symboles d’un clavier américain standard. Ces premiers points de 128 code sont les mêmes que celles définit le jeu de caractères ASCII. Les deuxième 128 points de code (128 à 255) représentent des caractères spéciaux, tels que les lettres de l’alphabet Latin-basé, les accents, les symboles monétaires et les fractions. Unicode utilise les points de code restants (256-65&535;) pour une large gamme de symboles. Cela inclut les caractères textuels mondiaux, les signes diacritiques et des symboles mathématiques et techniques.  
  
 Vous pouvez utiliser des méthodes telles que <xref:System.Char.IsDigit%2A>et <xref:System.Char.IsPunctuation%2A>sur un caractère dans une `String` variable pour déterminer sa classification Unicode.</xref:System.Char.IsPunctuation%2A> </xref:System.Char.IsDigit%2A>  
  
## <a name="format-requirements"></a>Exigences relatives au format  
 Vous devez placer un `String` littéral entre guillemets (`" "`). Si vous devez inclure un guillemet en tant que l’un des caractères dans la chaîne, vous utilisez deux guillemets contigus (`""`). L'exemple suivant illustre ce comportement.  
  
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
 Une fois que vous affectez une chaîne à un `String` variable, cette chaîne est *immuable*, ce qui signifie que vous ne pouvez pas modifier sa longueur ou son contenu. Lorsque vous modifiez une chaîne de toute façon, Visual Basic crée une nouvelle chaîne et abandonne la précédente. Le `String` variable pointe alors vers la nouvelle chaîne.  
  
 Vous pouvez manipuler le contenu d’un `String` variable à l’aide d’une variété de fonctions de chaîne. L’exemple suivant illustre la <xref:Microsoft.VisualBasic.Strings.Left%2A>fonction</xref:Microsoft.VisualBasic.Strings.Left%2A>  
  
```  
Dim S As String = "Database"  
' The following statement sets S to a new string containing "Data".  
S = Microsoft.VisualBasic.Left(S, 4)  
```  
  
 Une chaîne créée par un autre composant peut être remplie avec des espaces à gauche ou. Si vous recevez une telle chaîne, vous pouvez utiliser le <xref:Microsoft.VisualBasic.Strings.Trim%2A>, <xref:Microsoft.VisualBasic.Strings.LTrim%2A>, et <xref:Microsoft.VisualBasic.Strings.RTrim%2A>fonctions pour supprimer ces espaces.</xref:Microsoft.VisualBasic.Strings.RTrim%2A> </xref:Microsoft.VisualBasic.Strings.LTrim%2A> </xref:Microsoft.VisualBasic.Strings.Trim%2A>  
  
 Pour plus d’informations sur les manipulations de chaînes, consultez [chaînes](../../../visual-basic/programming-guide/language-features/strings/index.md).  
  
## <a name="programming-tips"></a>Conseils de programmation  
  
-   **Nombres négatifs.** N’oubliez pas que les caractères stockés dans `String` ne sont pas signés et ne peut pas représenter de valeurs négatives. Dans tous les cas, vous ne devez pas utiliser `String` pour stocker des valeurs numériques.  
  
-   **Considérations sur l’interopérabilité.** Si vous utilisez des composants non écrits pour le .NET Framework, par exemple des objets Automation ou COM, n’oubliez pas que les chaînes de caractères possèdent une largeur de données différente (8 bits) dans d’autres environnements. Si vous passez un argument de chaîne de caractères 8 bits à un tel composant, déclarez-le en tant que `Byte()`, un tableau de `Byte` éléments, au lieu de `String` dans votre nouveau code Visual Basic.  
  
-   **Caractères de type.** L’ajout du caractère de type identificateur `$` à un identificateur force ce dernier en le `String` type de données. `String`n’a aucun caractère de type de littéral. Toutefois, le compilateur traite les littéraux placés entourés guillemets (`" "`) en tant que `String`.  
  
-   **Type .NET Framework.** Le type correspondant dans le .NET Framework est la <xref:System.String?displayProperty=fullName>classe.</xref:System.String?displayProperty=fullName>  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.String?displayProperty=fullName></xref:System.String?displayProperty=fullName>   
 [Types de données](../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Type de données char](../../../visual-basic/language-reference/data-types/char-data-type.md)   
 [Fonctions de Conversion de type](../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [Résumé de la conversion](../../../visual-basic/language-reference/keywords/conversion-summary.md)   
 [Comment : appeler une fonction Windows qui possède des Types non signés](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)   
 [Utilisation efficace des types de données](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)

