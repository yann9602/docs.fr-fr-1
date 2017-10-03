---
title: "internal (référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- internal_CSharpKeyword
- internal
dev_langs:
- CSharp
helpviewer_keywords:
- internal keyword [C#]
ms.assetid: 6ee0785c-d7c8-49b8-bb72-0a4dfbcb6461
caps.latest.revision: 23
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
ms.openlocfilehash: 5674a78e2c317357c31d9e2661a25ce86cbf4f6a
ms.contentlocale: fr-fr
ms.lasthandoff: 09/25/2017

---
# <a name="internal-c-reference"></a>internal (référence C#)
Le mot clé `internal` est un [modificateur d’accès](../../../csharp/language-reference/keywords/access-modifiers.md) pour les types et les membres de type. Les types et les membres internes (internal) sont accessibles uniquement dans les fichiers d’un même assembly, comme dans l’exemple suivant :  
  
```  
public class BaseClass   
{  
    // Only accessible within the same assembly  
    internal static int x = 0;  
}  
```  
  
 Les types et les membres ayant le modificateur d’accès `protected internal` sont accessibles à partir de l’assembly actuel ou des types dérivés de la classe conteneur.  
  
 Pour obtenir une comparaison de `internal` et des autres modificateurs d’accès, consultez [Niveaux d’accessibilité](../../../csharp/language-reference/keywords/accessibility-levels.md) et [Modificateurs d’accès](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).  
  
 Pour plus d’informations, consultez [Assemblys et le Global Assembly Cache](../../../csharp/programming-guide/concepts/assemblies-gac/index.md).  
  
 L’accès interne est fréquemment utilisé lors du développement basé sur les composants, car il permet à un groupe de composants de collaborer de façon privée sans être exposés au reste du code de l’application. Par exemple, un framework de création d’interfaces graphiques utilisateur peut fournir les classes `Control` et `Form` qui coopèrent en utilisant des membres ayant un accès interne. Étant donné que ces membres sont internes, ils ne sont pas exposés au code qui utilise le framework.  
  
 Le fait de référencer un type ou un membre avec accès interne en dehors de l’assembly dans lequel il a été défini constitue une erreur.  
  
## <a name="example"></a>Exemple  
 Cet exemple contient deux fichiers : `Assembly1.cs` et `Assembly1_a.cs`. Le premier fichier contient la classe de base interne `BaseClass`. Dans le deuxième fichier, une tentative d’instanciation de `BaseClass` génère une erreur.  
  
```  
// Assembly1.cs  
// Compile with: /target:library  
internal class BaseClass   
{  
   public static int intM = 0;  
}  
```  
  
```  
// Assembly1_a.cs  
// Compile with: /reference:Assembly1.dll  
class TestAccess   
{  
   static void Main()   
   {  
      BaseClass myBase = new BaseClass();   // CS0122  
   }  
}  
```  
  
## <a name="example"></a>Exemple  
 Dans cet exemple, utilisez les mêmes fichiers que vous avez utilisés dans l’exemple 1, et remplacez le niveau d’accessibilité `BaseClass` par `public`. Remplacez également le niveau d’accessibilité du membre `IntM` par `internal`. Dans ce cas, vous pouvez instancier la classe, mais vous ne pouvez pas accéder au membre interne.  
  
```  
// Assembly2.cs  
// Compile with: /target:library  
public class BaseClass   
{  
   internal static int intM = 0;  
}  
```  
  
```  
// Assembly2_a.cs  
// Compile with: /reference:Assembly1.dll  
public class TestAccess   
{  
   static void Main()   
   {  
      BaseClass myBase = new BaseClass();   // Ok.  
      BaseClass.intM = 444;    // CS0117  
   }  
}  
```  
  
## <a name="c-language-specification"></a>Spécification du langage C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur C#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Mots clés C#](../../../csharp/language-reference/keywords/index.md)   
 [Modificateurs d’accès](../../../csharp/language-reference/keywords/access-modifiers.md)   
 [Niveaux d’accessibilité](../../../csharp/language-reference/keywords/accessibility-levels.md)   
 [Modificateurs](../../../csharp/language-reference/keywords/modifiers.md)   
 [public](../../../csharp/language-reference/keywords/public.md)   
 [private](../../../csharp/language-reference/keywords/private.md)   
 [protected](../../../csharp/language-reference/keywords/protected.md)

