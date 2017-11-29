---
title: "Comment : analyser des chaînes à l’aide de String.Split (Guide de programmation C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- splitting strings [C#]
- Split method [C#]
- strings [C#], splitting
- parse strings
ms.assetid: 729c2923-4169-41c6-9c90-ef176c1e2953
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 7b97d1d89a4c74a4c759d1ed41a0bc2476b3b07a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-parse-strings-using-stringsplit-c-programming-guide"></a>Comment : analyser des chaînes à l’aide de String.Split (Guide de programmation C#)
L’exemple de code suivant montre comment analyser une chaîne à l’aide de la méthode <xref:System.String.Split%2A?displayProperty=nameWithType> . <xref:System.String.Split%2A> accepte comme entrée un tableau qui indique les caractères séparant les sous-chaînes intéressantes de la chaîne cible.  La fonction retourne un tableau des sous-chaînes.  
  
 Cet exemple utilise des caractères de séparation (espaces, virgules, points, deux-points et onglets) qui sont tous passés dans un tableau à <xref:System.String.Split%2A>.  Chaque mot dans la phrase de la chaîne cible est affiché séparément du tableau de chaînes résultant.  
  
## <a name="example"></a>Exemple  
 [!code-csharp[csProgGuideStrings#16](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-parse-strings-using-string-split_1.cs)]  
  
## <a name="example"></a>Exemple  
 Par défaut, String.Split retourne des chaînes vides quand deux caractères de séparation apparaissent de façon contiguë dans la chaîne cible.  Vous pouvez passer un paramètre StringSplitOptions.RemoveEmptyEntries facultatif pour exclure toutes les chaînes vides dans la sortie.  
  
 String.Split peut accepter un tableau de chaînes (séquences de caractères, à la place de caractères uniques, qui agissent comme séparateurs lors de l’analyse de la chaîne cible).  
  
```csharp  
class TestStringSplit  
{  
    static void Main()  
    {  
        string[] separatingChars = { "<<", "..." };  
  
        string text = "one<<two......three<four";  
        System.Console.WriteLine("Original text: '{0}'", text);  
  
        string[] words = text.Split(separatingChars, System.StringSplitOptions.RemoveEmptyEntries );  
        System.Console.WriteLine("{0} substrings in text:", words.Length);  
  
        foreach (string s in words)  
        {  
            System.Console.WriteLine(s);  
        }  
  
        // Keep the console window open in debug mode.  
        System.Console.WriteLine("Press any key to exit.");  
        System.Console.ReadKey();  
    }  
}  
/* Output:  
    Original text: 'one<<two......three<four'  
    3 words in text:  
    one  
    two  
    three<four  
*/  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)  
 [Chaînes](../../../csharp/programming-guide/strings/index.md)  
 [.NET Framework (expressions régulières)](https://msdn.microsoft.com/library/hs600312)
