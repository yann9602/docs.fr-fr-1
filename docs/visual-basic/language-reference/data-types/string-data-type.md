---
title: "String Data Type (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.String"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "strings [Visual Basic], character"
  - "strings [Visual Basic], fixed-length"
  - "string keyword [Visual Basic]"
  - "fixed-length strings, string data type"
  - "literals, string"
  - "text [Visual Basic], String data type"
  - "$ identifier type character"
  - "String data type"
  - "fixed-length strings"
  - "string literals"
  - "data types [Visual Basic], assigning"
  - "" String literals"
  - "identifier type characters, $"
ms.assetid: 15ac03f5-cabd-42cc-a754-1df3893c25d9
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 19
---
# String Data Type (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Maintient des séquences de points de code 16 bits \(2 octets\) non signés dont la valeur varie entre 0 et 65535.  Chaque *point de code*, ou code de caractère, représente un caractère Unicode unique.  Une chaîne peut contenir jusqu'à environ deux milliards \(2 ^ 31\) de caractères Unicode.  
  
## Notes  
 Utilisez le type de données `String` pour maintenir plusieurs caractères sans les charges mémoire de la gestion du tableau de `Char()`, un tableau d'éléments `Char`.  
  
 La valeur par défaut de `String` est `Nothing` \(référence nulle\).  Notez que ce n'est pas la même valeur que la chaîne vide \(valeur `""`\).  
  
## Caractères Unicode  
 Les 128 premiers points de code \(0 à 127\) Unicode correspondent aux lettres et symboles sur un clavier américain standard.  clavier.  Ces 128 premiers points de code sont les mêmes que ceux définis par le jeu de caractères ASCII.  Les 128 points de code suivants \(128–255\) représentent les caractères spéciaux, tels que les lettres de l'alphabet latin, les accents, les symboles monétaires et les fractions.  Unicode utilise les points de code restants \(256\-65 535\) pour une large gamme de symboles.  Cela inclut les caractères textuels mondiaux, les signes diacritiques, ainsi que les symboles mathématiques et techniques.  
  
 Vous pouvez utiliser des méthodes telles que <xref:System.Char.IsDigit%2A> et <xref:System.Char.IsPunctuation%2A> sur un caractère dans une variable `String` pour déterminer sa classification Unicode.  
  
## Pré\-requis de format  
 Vous devez joindre un littéral `String` entre des guillemets \(`" "`\).  Si vous devez inclure un guillemet en tant que caractère dans la chaîne, utilisez deux guillemets contigus \(`""`\).  L'exemple suivant illustre ce comportement.  
  
```  
Dim j As String = "Joe said ""Hello"" to me."  
Dim h As String = "Hello"  
' The following messages all display the same thing:  
' "Joe said "Hello" to me."  
MsgBox(j)  
MsgBox("Joe said " & """" & h & """" & " to me.")  
MsgBox("Joe said """ & h & """ to me.")  
```  
  
 Notez que les guillemets contigus qui représentent un guillemet dans la chaîne sont indépendants des guillemets qui commencent et terminent le littéral `String`.  
  
## Manipulations de chaînes  
 Une fois que vous assignez une chaîne à une variable `String`, cette chaîne est *immuable*, ce qui signifie que vous ne pouvez pas modifier sa longueur ou son contenu.  Lorsque vous modifiez une chaîne d'une manière ou d'une autre, Visual Basic crée une nouvelle chaîne et abandonne la précédente.  La variable `String` pointe ensuite vers la nouvelle chaîne.  
  
 Vous pouvez manipuler le contenu d'une variable `String` à l'aide de diverses fonctions de chaîne.  L'exemple suivant illustre la fonction <xref:Microsoft.VisualBasic.Strings.Left%2A>.  
  
```  
Dim S As String = "Database"  
' The following statement sets S to a new string containing "Data".  
S = Microsoft.VisualBasic.Left(S, 4)  
```  
  
 Une chaîne créée par un autre composant peut être remplie avec des espaces à gauche ou à droite.  Si vous recevez une telle chaîne, vous pouvez utiliser les fonctions <xref:Microsoft.VisualBasic.Strings.Trim%2A>, <xref:Microsoft.VisualBasic.Strings.LTrim%2A> et <xref:Microsoft.VisualBasic.Strings.RTrim%2A> pour supprimer ces espaces.  
  
 Pour plus d'informations sur les manipulations de chaînes, consultez [Strings](../../../visual-basic/programming-guide/language-features/strings/index.md).  
  
## Conseils de programmation  
  
-   **Nombres négatifs.** N'oubliez pas que les caractères stockés dans `String` ne sont pas signés et ne peuvent pas représenter de valeurs négatives.  Dans tous les cas, vous ne devez pas utiliser `String` pour stocker des valeurs numériques.  
  
-   **Considérations sur l'interopérabilité.** Si vous utilisez des composants non écrits pour le .NET Framework, par exemple des objets Automation ou COM, n'oubliez pas que les chaînes de caractères possèdent une largeur de données différente \(8 bits\) dans d'autres environnements.  Si vous transmettez un argument string de caractères de 8 bits à un tel composant, déclarez\-le comme `Byte()`, un tableau d'éléments `Byte`, au lieu de `String` dans votre nouveau code Visual Basic.  
  
-   **Caractères de type.** L'ajout du caractère de type d'identificateur `$` à un identificateur force ce dernier en un type de données `String`.  `String` n'a aucun caractère de type littéral.  Toutefois, le compilateur assimile les littéraux compris entre guillemets \(`" "`\) en tant que `String`.  
  
-   **Type Framework.** Le type correspondant dans le .NET Framework est la classe <xref:System.String?displayProperty=fullName>.  
  
## Voir aussi  
 <xref:System.String?displayProperty=fullName>   
 [Data Types](../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Char Data Type](../../../visual-basic/language-reference/data-types/char-data-type.md)   
 [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [Résumé de la conversion](../../../visual-basic/language-reference/keywords/conversion-summary.md)   
 [How to: Call a Windows Function that Takes Unsigned Types](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)   
 [Efficient Use of Data Types](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)