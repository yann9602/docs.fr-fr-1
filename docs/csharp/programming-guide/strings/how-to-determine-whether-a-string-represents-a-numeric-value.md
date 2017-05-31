---
title: "Guide pratique pour déterminer si une chaîne représente une valeur numérique (Guide de programmation C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- numeric strings [C#]
- validating numeric input [C#]
- strings [C#], numeric
ms.assetid: a4e84e10-ea0a-489f-a868-503dded9d85f
caps.latest.revision: 9
author: BillWagner
ms.author: wiwagn
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
ms.translationtype: Human Translation
ms.sourcegitcommit: fe32676f0e39ed109a68f39584cf41aec5f5ce90
ms.openlocfilehash: 343e7304a83f396b8bdcc9c92e9123eed206be56
ms.contentlocale: fr-fr
ms.lasthandoff: 05/10/2017

---
# <a name="how-to-determine-whether-a-string-represents-a-numeric-value-c-programming-guide"></a>Guide pratique pour déterminer si une chaîne représente une valeur numérique (Guide de programmation C#)
Pour déterminer si une chaîne est une représentation valide d’un type numérique spécifié, utilisez la méthode statique `TryParse` implémentée par tous les types numériques primitifs et par les types tels que <xref:System.DateTime> et <xref:System.Net.IPAddress>. L’exemple suivant montre comment déterminer si « 108 » est une chaîne [int](../../../csharp/language-reference/keywords/int.md) valide.  
  
```  
int i = 0;   
string s = "108";  
bool result = int.TryParse(s, out i); //i now = 108  
```  
  
 Si la chaîne contient des caractères non numériques ou si la valeur numérique est trop grande ou trop petite pour le type particulier que vous avez spécifié, `TryParse` retourne la valeur false et affecte la valeur zéro comme paramètre de sortie. Sinon, elle retourne la valeur true et affecte la valeur numérique de la chaîne comme paramètre de sortie.  
  
> [!NOTE]
>  Une chaîne peut contenir uniquement des caractères numériques et ne pas être valide pour le type dont vous utilisez la méthode `TryParse`. Par exemple, « 256 » n’est pas une valeur valide pour `byte`, mais elle est valide pour `int`. « 98,6 » n’est pas une valeur valide pour `int`, mais elle est valide pour `decimal`.  
  
## <a name="example"></a>Exemple  
 Les exemples suivants montrent comment utiliser `TryParse` avec des représentations sous forme de chaîne de valeurs `long`, `byte` et `decimal`.  
  
 [!code-cs[csProgGuideStrings#14](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-determine-whether-a-string-represents-a-numeric-value_1.cs)]  
  
## <a name="robust-programming"></a>Programmation fiable  
 Les types numériques primitifs implémentent également la méthode statique `Parse`, qui lève une exception si la chaîne n’est pas un nombre valide. `TryParse` est généralement plus efficace, car elle retourne simplement false si le nombre n’est pas valide.  
  
## <a name="net-framework-security"></a>Sécurité .NET Framework  
 Utilisez toujours la méthode `TryParse` ou `Parse` pour valider l’entrée utilisateur à partir de contrôles tels que des zones de texte et des zones de liste déroulante.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour convertir un tableau d’octets en int](../../../csharp/programming-guide/types/how-to-convert-a-byte-array-to-an-int.md)   
 [Guide pratique pour convertir une chaîne en nombre](../../../csharp/programming-guide/types/how-to-convert-a-string-to-a-number.md)   
 [Guide pratique pour effectuer une conversion entre des chaînes hexadécimales et des types numériques](../../../csharp/programming-guide/types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md)   
 [Analyse de chaînes numériques](../../../standard/base-types/parsing-numeric.md)   
 [Mise en forme des types](../../../standard/base-types/formatting-types.md)
