---
title: Types pointeur (Guide de programmation C#)
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- unsafe code [C#], pointers
- pointers [C#]
ms.assetid: 3319faf9-336d-4148-9af2-1da2579cdd1e
caps.latest.revision: 19
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
ms.openlocfilehash: 1a4ebc69762f18dc630100b544c18df0f43734ac
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="pointer-types-c-programming-guide"></a>Types pointeur (Guide de programmation C#)
Dans un contexte unsafe, un type peut être un type pointeur, un type valeur ou un type référence. La déclaration d'un type pointeur peut prendre l'une des formes suivantes :  
  
```  
type* identifier;  
void* identifier; //allowed but not recommended  
```  
  
 Chacun des types suivants peut être un type pointeur :  
  
-   [sbyte](../../../csharp/language-reference/keywords/sbyte.md), [byte](../../../csharp/language-reference/keywords/byte.md), [short](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md), [ulong](../../../csharp/language-reference/keywords/ulong.md), [char](../../../csharp/language-reference/keywords/char.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), [decimal](../../../csharp/language-reference/keywords/decimal.md) ou [bool](../../../csharp/language-reference/keywords/bool.md).  
  
-   Tout type [enum](../../../csharp/language-reference/keywords/enum.md).  
  
-   Tout type pointeur.  
  
-   Tout type struct défini par l'utilisateur qui contient des champs de types unmanaged uniquement.  
  
 Les types pointeur n’héritent pas de [object](../../../csharp/language-reference/keywords/object.md), et aucune conversion n’est possible entre les types pointeur et `object`. Par ailleurs, le boxing et l'unboxing ne prennent pas en charge les pointeurs. Cependant, vous pouvez effectuer des conversions entre différents types pointeur ainsi qu'entre des types pointeur et des types intégraux.  
  
 Lorsque vous déclarez plusieurs pointeurs dans la même déclaration, l'astérisque (*) est écrit conjointement au type sous-jacent uniquement, il n'est pas utilisé en tant que préfixe de chaque nom de pointeur. Exemple :  
  
```  
int* p1, p2, p3;   // Ok  
int *p1, *p2, *p3;   // Invalid in C#  
```  
  
 Un pointeur ne peut pas pointer vers une référence ou vers un [struct](../../../csharp/language-reference/keywords/struct.md) qui contient des références, car une référence d’objet peut être collectée par le récupérateur de mémoire, même si un pointeur pointe vers elle. Le récupérateur de mémoire ne se préoccupe pas de savoir si un objet est pointé par des types pointeur.  
  
 La valeur de la variable pointeur de type `myType*` est l'adresse d'une variable de type `myType`. Les éléments suivants sont des exemples de déclarations de type pointeur :  
  
|Exemple|Description|  
|-------------|-----------------|  
|`int* p`|`p` est un pointeur vers un entier.|  
|`int** p`|`p` est un pointeur vers un pointeur vers un entier.|  
|`int*[] p`|`p` est un tableau unidimensionnel de pointeurs vers des entiers.|  
|`char* p`|`p` est un pointeur vers un caractère.|  
|`void* p`|`p` est un pointeur vers un type inconnu.|  
  
 L'opérateur d'indirection de pointeur * peut être utilisé pour accéder au contenu à l'emplacement vers lequel pointe la variable pointeur. Observez par exemple la déclaration suivante :  
  
```  
int* myVariable;  
```  
  
 L'expression `*myVariable` désigne la variable `int` trouvée à l'adresse contenue dans `myVariable`.  
  
 Plusieurs exemples de pointeurs sont présentés dans les rubriques [fixed, instruction](../../../csharp/language-reference/keywords/fixed-statement.md) et [Conversions de pointeur](../../../csharp/programming-guide/unsafe-code-pointers/pointer-conversions.md).  L'exemple suivant montre la nécessité d'un pointeur intérieur pour le mot clé `unsafe` et les instructions `fixed`, et comment l'incrémenter.  Vous pouvez coller ce code dans la fonction Main d'une application console pour l'exécuter. (N’oubliez pas d’autoriser le code unsafe dans le **Concepteur de projet**. Pour cela, choisissez **Projet**, **Propriétés** dans la barre de menus, puis sélectionnez **Autoriser le code unsafe** dans l’onglet **Générer**.)  
  
```  
// Normal pointer to an object.  
int[] a = new int[5] {10, 20, 30, 40, 50};  
// Must be in unsafe code to use interior pointers.  
unsafe  
{  
    // Must pin object on heap so that it doesn't move while using interior pointers.  
    fixed (int* p = &a[0])  
    {  
        // p is pinned as well as object, so create another pointer to show incrementing it.  
        int* p2 = p;  
        Console.WriteLine(*p2);  
        // Incrementing p2 bumps the pointer by four bytes due to its type ...  
        p2 += 1;  
        Console.WriteLine(*p2);  
        p2 += 1;  
        Console.WriteLine(*p2);  
        Console.WriteLine("--------");  
        Console.WriteLine(*p);  
        // Deferencing p and incrementing changes the value of a[0] ...  
        *p += 1;  
        Console.WriteLine(*p);  
        *p += 1;  
        Console.WriteLine(*p);  
    }  
}  
  
Console.WriteLine("--------");  
Console.WriteLine(a[0]);  
Console.ReadLine();  
  
// Output:  
//10  
//20  
//30  
//--------  
//10  
//11  
//12  
//--------  
//12  
```  
  
 L'opérateur d'indirection ne peut pas être appliqué à un pointeur de type `void*`. Toutefois, vous pouvez utiliser un cast pour convertir un pointeur void en n'importe quel autre type pointeur, et inversement.  
  
 Un pointeur peut être `null`. Le fait d'appliquer un opérateur d'indirection à un pointeur Null donne lieu à un comportement défini par l'implémentation.  
  
 Sachez que le passage de pointeurs entre méthodes peut engendrer un comportement non défini. Par exemple, retourner un pointeur à une variable locale via un paramètre Out ou Ref ou en tant que résultat de fonction. Si le pointeur a été défini dans un bloc fixed, la variable vers laquelle il pointe peut ne plus être fixed.  
  
 Le tableau suivant répertorie les opérateurs et les instructions qui peuvent fonctionner sur des pointeurs dans un contexte unsafe :  
  
|Opérateur/Instruction|Utilisation|  
|-------------------------|---------|  
|*|Exécute l'indirection de pointeur.|  
|->|Accède à un membre d'un struct via un pointeur.|  
|[]|Indexe un pointeur.|  
|`&`|Obtient l'adresse d'une variable.|  
|++ et --|Incrémente et décrémente les pointeurs.|  
|+ et -|Exécute des opérations arithmétiques sur les pointeurs.|  
|==, !=, \<, >, \<= et >=|Compare des pointeurs.|  
|`stackalloc`|Alloue de la mémoire sur la pile.|  
|Instruction `fixed`|Résout temporairement une variable afin de pouvoir rechercher son adresse.|  
  
## <a name="c-language-specification"></a>Spécification du langage C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Pointeurs et code unsafe](../../../csharp/programming-guide/unsafe-code-pointers/index.md)   
 [Conversions de pointeur](../../../csharp/programming-guide/unsafe-code-pointers/pointer-conversions.md)   
 [Expressions de pointeur](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)   
 [Types](../../../csharp/language-reference/keywords/types.md)   
 [unsafe](../../../csharp/language-reference/keywords/unsafe.md)   
 [fixed, instruction](../../../csharp/language-reference/keywords/fixed-statement.md)   
 [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)   
 [Conversion boxing et unboxing](../../../csharp/programming-guide/types/boxing-and-unboxing.md)

