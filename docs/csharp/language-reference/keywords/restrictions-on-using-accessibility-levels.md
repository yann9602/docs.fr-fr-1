---
title: "Limitations sur l'utilisation des niveaux d'accessibilité (référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- access modifiers [C#], accessibility level restrictions
ms.assetid: 987e2f22-46bf-4fea-80ee-270b9cd01045
caps.latest.revision: 21
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
ms.openlocfilehash: 8e49afd38fd776593b87f065a079da0d546df4a6
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="restrictions-on-using-accessibility-levels-c-reference"></a>Limitations sur l'utilisation des niveaux d'accessibilité (référence C#)
Lorsque vous spécifiez un type dans une déclaration, vérifiez si le niveau d’accessibilité du type dépend du niveau d’accessibilité d’un membre ou d’un autre type. Par exemple, la classe de base directe doit être au moins aussi accessible que la classe dérivée. Les déclarations suivantes entraînent une erreur du compilateur, car la classe de base `BaseClass` est moins accessible que `MyClass` :  
  
```  
class BaseClass {...}  
public class MyClass: BaseClass {...} // Error  
```  
  
 Le tableau suivant résume les limitations sur les niveaux d’accessibilité déclarés.  
  
|Contexte|Remarques|  
|-------------|-------------|  
|[Classes](../../../csharp/programming-guide/classes-and-structs/classes.md)|La classe de base directe d’un type de classe doit être au moins aussi accessible que le type de classe lui-même.|  
|[Interfaces](../../../csharp/programming-guide/interfaces/index.md)|Les interfaces de base explicites d’un type d’interface doivent être au moins aussi accessibles que le type d’interface lui-même.|  
|[Délégués](../../../csharp/programming-guide/delegates/index.md)|Le type de retour et les types de paramètres d’un type délégué doivent être au moins aussi accessibles que le type délégué lui-même.|  
|[Constantes](../../../csharp/programming-guide/classes-and-structs/constants.md)|Le type d’une constante doit être au moins aussi accessible que la constante elle-même.|  
|[Champs](../../../csharp/programming-guide/classes-and-structs/fields.md)|Le type d’un champ doit être au moins aussi accessible que le champ lui-même.|  
|[Méthodes](../../../csharp/programming-guide/classes-and-structs/methods.md)|Le type de retour et les types de paramètres d’une méthode doivent être au moins aussi accessibles que la méthode elle-même.|  
|[Propriétés](../../../csharp/programming-guide/classes-and-structs/properties.md)|Le type d’une propriété doit être au moins aussi accessible que la propriété elle-même.|  
|[Événements](../../../csharp/programming-guide/events/index.md)|Le type d’un événement doit être au moins aussi accessible que l’événement lui-même.|  
|[Indexeurs](../../../csharp/programming-guide/indexers/index.md)|Le type et les types de paramètres d’un indexeur doivent être au moins aussi accessibles que l’indexeur lui-même.|  
|[Opérateurs](../../../csharp/programming-guide/statements-expressions-operators/operators.md)|Le type de retour et les types de paramètres d’un opérateur doivent être au moins aussi accessibles que l’opérateur lui-même.|  
|[Constructeurs](../../../csharp/programming-guide/classes-and-structs/constructors.md)|Les types de paramètres d’un constructeur doivent être au moins aussi accessibles que le constructeur lui-même.|  
  
## <a name="example"></a>Exemple  
 L’exemple suivant contient des déclarations erronées de différents types. Le commentaire qui suit chaque déclaration indique l’erreur du compilateur à attendre.  
  
```  
// Restrictions on Using Accessibility Levels  
// CS0052 expected as well as CS0053, CS0056, and CS0057  
// To make the program work, change access level of both class B  
// and MyPrivateMethod() to public.  
  
using System;  
  
// A delegate:  
delegate int MyDelegate();  
  
class B  
{  
    // A private method:  
    static int MyPrivateMethod()  
    {  
        return 0;  
    }  
}  
  
public class A  
{  
    // Error: The type B is less accessible than the field A.myField.  
    public B myField = new B();  
  
    // Error: The type B is less accessible  
    // than the constant A.myConst.  
    public readonly B myConst = new B();  
  
    public B MyMethod()  
    {  
        // Error: The type B is less accessible   
        // than the method A.MyMethod.  
        return new B();  
    }  
  
    // Error: The type B is less accessible than the property A.MyProp  
    public B MyProp  
    {  
        set  
        {  
        }  
    }  
  
    MyDelegate d = new MyDelegate(B.MyPrivateMethod);  
    // Even when B is declared public, you still get the error:   
    // "The parameter B.MyPrivateMethod is not accessible due to   
    // protection level."  
  
    public static B operator +(A m1, B m2)  
    {  
        // Error: The type B is less accessible  
        // than the operator A.operator +(A,B)  
        return new B();  
    }  
  
    static void Main()  
    {  
        Console.Write("Compiled successfully");  
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
 [Domaine d’accessibilité](../../../csharp/language-reference/keywords/accessibility-domain.md)   
 [Niveaux d’accessibilité](../../../csharp/language-reference/keywords/accessibility-levels.md)   
 [Modificateurs d’accès](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)   
 [public](../../../csharp/language-reference/keywords/public.md)   
 [private](../../../csharp/language-reference/keywords/private.md)   
 [protected](../../../csharp/language-reference/keywords/protected.md)   
 [internal](../../../csharp/language-reference/keywords/internal.md)

