---
title: "extern (référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- extern_CSharpKeyword
- extern
dev_langs:
- CSharp
helpviewer_keywords:
- DllImport attribute
- extern keyword [C#]
ms.assetid: 9c3f02c4-51b8-4d80-9cb2-f2b6e1ae15c7
caps.latest.revision: 26
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: e499ade5ec8a9339b0d425c59809cf7c177466fb
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="extern-c-reference"></a>extern (référence C#)
Le modificateur `extern` permet de déclarer une méthode qui est implémentée en externe. Le modificateur `extern` est souvent utilisé avec l'attribut `DllImport` lors de l'utilisation de services Interop à appeler dans du code non managé. Dans ce cas, la méthode doit également être déclarée comme `static`, comme indiqué dans l'exemple suivant :  
  
```  
[DllImport("avifil32.dll")]  
private static extern void AVIFileInit();  
```  
  
 Le mot clé `extern` peut également définir un alias d'assembly externe, permettant ainsi de référencer différentes versions du même composant à partir d'un seul assembly. Pour plus d’informations, consultez [extern alias](../../../csharp/language-reference/keywords/extern-alias.md).  
  
 C’est une erreur d’utiliser conjointement les modificateurs [abstract](../../../csharp/language-reference/keywords/abstract.md) et `extern` pour modifier le même membre. L'utilisation du modificateur `extern` signifie que la méthode est implémentée en dehors du code C#, tandis que l'utilisation du modificateur `abstract` signifie que l'implémentation de la méthode n'est pas effectuée dans la classe.  
  
 L'utilisation du mot clé extern est plus restreinte dans C# que dans C++. Pour comparer son utilisation dans C# et C++, consultez : Utilisation d'extern pour spécifier la liaison dans le Guide de référence du langage C++.  
  
## <a name="example"></a>Exemple  
 **Example 1.** Dans cet exemple, le programme reçoit une chaîne provenant de l’utilisateur et l’affiche dans une boîte de message. Le programme utilise la méthode `MessageBox` importée de la bibliothèque User32.dll.  
  
 [!code-cs[csrefKeywordsModifiers#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/extern_1.cs)]  
  
## <a name="example"></a>Exemple  
 **Example 2.** Cet exemple illustre un programme C# qui fait appel à une bibliothèque C (une DLL native).  
  
 1. Créez le fichier C suivant et nommez-le `cmdll.c` :  
  
```  
// cmdll.c  
// Compile with: /LD  
int __declspec(dllexport) SampleMethod(int i)  
{  
   return i*10;  
}  
```  
  
## <a name="example"></a>Exemple  
 2. Ouvrez une fenêtre d’invite de commandes d’outils natifs Visual Studio x64 (ou x32) à partir du répertoire d’installation de Visual Studio et compilez le fichier `cmdll.c` en tapant **cl /LD cmdll.c** à l’invite de commandes.  
  
 3. Dans le même répertoire, créez le fichier C# suivant et nommez-le `cm.cs` :  
  
```  
// cm.cs  
using System;  
using System.Runtime.InteropServices;  
public class MainClass   
{  
   [DllImport("Cmdll.dll")]  
   public static extern int SampleMethod(int x);  
  
   static void Main()   
   {  
      Console.WriteLine("SampleMethod() returns {0}.", SampleMethod(5));  
   }  
}  
```  
  
## <a name="example"></a>Exemple  
 3. Ouvrez une fenêtre d'invite de commandes d'outils natifs Visual Studio x64 (ou x32) à partir du répertoire d'installation de Visual Studio et compilez le fichier `cm.cs` en tapant :  
  
> **csc cm.cs** (pour l’invite de commandes x64)   
>  -ou-  
> **csc /platform:x 86 cm.cs** (pour l’invite de commandes x32)  
  
 Cette opération crée le fichier exécutable `cm.exe`.  
  
 4. Exécutez `cm.exe`. La méthode `SampleMethod` passe la valeur 5 au fichier DLL, qui retourne la valeur multipliée par 10.  Le programme génère la sortie suivante :  
  
```  
SampleMethod() returns 50.  
```  
  
## <a name="c-language-specification"></a>Spécification du langage C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>   
 [Informations de référence sur C#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Mots clés C#](../../../csharp/language-reference/keywords/index.md)   
 [Modificateurs](../../../csharp/language-reference/keywords/modifiers.md)

