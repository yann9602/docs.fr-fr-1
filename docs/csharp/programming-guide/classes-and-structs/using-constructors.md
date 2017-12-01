---
title: Utilisation de constructeurs (Guide de programmation C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: constructors [C#], about constructors
ms.assetid: 464253b2-fd5d-469a-836d-df0fdf2a43f7
caps.latest.revision: "26"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: eb9fcd1e4090da300de17c7fd808669ba51767c6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="using-constructors-c-programming-guide"></a>Utilisation de constructeurs (Guide de programmation C#)
Quand une [classe](../../../csharp/language-reference/keywords/class.md) ou un [struct](../../../csharp/language-reference/keywords/struct.md) est créé, son constructeur est appelé. Les constructeurs portent le même nom que la classe ou le struct, et ils initialisent généralement les membres de données du nouvel objet.  
  
 Dans l’exemple suivant, une classe nommée `Taxi` est définie en utilisant un constructeur simple. Cette classe est ensuite instanciée à l’aide de l’opérateur [new](../../../csharp/language-reference/keywords/new.md). Le constructeur `Taxi` est appelé par l’opérateur `new` immédiatement après l’allocation de la mémoire pour le nouvel objet.  
  
 [!code-csharp[csProgGuideObjects#53](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_1.cs)]  
  
 Un constructeur qui ne prend pas de paramètres est appelé *constructeur par défaut*. Les constructeurs par défaut sont appelés chaque fois qu’un objet est instancié à l’aide de l’opérateur `new` et qu’aucun argument n’est fourni à `new`. Pour plus d’informations, consultez [Constructeurs d’instances](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md).  
  
 À moins que la classe soit [statique](../../../csharp/language-reference/keywords/static.md), les classes sans constructeurs se voient attribuer un constructeur public par défaut par le compilateur C# pour activer l’instanciation de classe. Pour plus d’informations, consultez [Classes statiques et membres de classe statique](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).  
  
 Vous pouvez empêcher qu’une classe soit instanciée en rendant le constructeur privé, comme suit :  
  
 [!code-csharp[csProgGuideObjects#11](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_2.cs)]  
  
 Pour plus d’informations, consultez [Constructeurs privés](../../../csharp/programming-guide/classes-and-structs/private-constructors.md).  
  
 Les constructeurs pour les types [struct](../../../csharp/language-reference/keywords/struct.md) ressemblent aux constructeurs de classe, mais les `structs` ne peuvent pas contenir de constructeur par défaut explicite, car le compilateur en fournit automatiquement un. Ce constructeur initialise chaque champ du `struct` aux valeurs par défaut. Pour plus d’informations, consultez [Tableau des valeurs par défaut](../../../csharp/language-reference/keywords/default-values-table.md). Toutefois, ce constructeur par défaut est appelé uniquement si le `struct` est instancié avec `new`. Par exemple, ce code utilise le constructeur par défaut pour <xref:System.Int32>. Vous êtes par conséquent assuré que l’entier est initialisé :  
  
```  
int i = new int();  
Console.WriteLine(i);  
```  
  
 Toutefois, le code suivant provoque une erreur de compilateur, car il n’utilise pas `new` et il essaie d’utiliser un objet qui n’a pas été initialisé :  
  
```  
int i;  
Console.WriteLine(i);  
```  
  
 Les objets basés sur des `structs` (notamment tous les types numériques intégrés) peuvent également être initialisés ou assignés, puis utilisés, comme dans l’exemple suivant :  
  
```  
int a = 44;  // Initialize the value type...  
int b;  
b = 33;      // Or assign it before using it.  
Console.WriteLine("{0}, {1}", a, b);  
```  
  
 Ainsi, l’appel du constructeur par défaut pour un type valeur n’est pas obligatoire.  
  
 Les classes et les `structs` peuvent tous les deux définir des constructeurs qui prennent des paramètres. Les constructeurs qui prennent des paramètres doivent être appelés à l’aide d’une instruction `new` ou d’une instruction [base](../../../csharp/language-reference/keywords/base.md). Les classes et les `structs` peuvent également définir plusieurs constructeurs, et ni l’un ni l’autre n’est nécessaire pour définir un constructeur par défaut. Exemple :  
  
 [!code-csharp[csProgGuideObjects#54](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_3.cs)]  
  
 Cette classe peut être créée à l’aide de l’une ou l’autre des instructions suivantes :  
  
 [!code-csharp[csProgGuideObjects#55](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_4.cs)]  
  
 Un constructeur peut utiliser le mot clé `base` pour appeler le constructeur d’une classe de base. Exemple :  
  
 [!code-csharp[csProgGuideObjects#56](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_5.cs)]  
  
 Dans cet exemple, le constructeur de la classe de base est appelé avant que le bloc du constructeur ne soit exécuté. Le mot clé `base` peut être utilisé avec ou sans paramètres. Tous les paramètres du constructeur peuvent être utilisés comme paramètres pour `base` ou comme partie d’une expression. Pour plus d’informations, consultez [base](../../../csharp/language-reference/keywords/base.md).  
  
 Dans une classe dérivée, si un constructeur de classe de base n’est pas appelé explicitement à l’aide du mot clé `base`, le constructeur par défaut, s’il existe, est appelé implicitement. Cela signifie que les déclarations de constructeur suivantes sont en fait les mêmes :  
  
 [!code-csharp[csProgGuideObjects#58](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_6.cs)]  
  
 [!code-csharp[csProgGuideObjects#57](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_7.cs)]  
  
 Si une classe de base n’offre pas de constructeur par défaut, la classe dérivée doit faire un appel explicite à un constructeur de base à l’aide du mot clé `base`.  
  
 Un constructeur peut appeler un autre constructeur dans le même objet à l’aide du mot clé [this](../../../csharp/language-reference/keywords/this.md). Comme `base`, `this` peut être utilisé avec ou sans paramètres, et tous les paramètres dans le constructeur sont disponibles comme paramètres pour `this` ou comme partie d’une expression. Par exemple, le deuxième constructeur de l’exemple précédent peut être récrit à l’aide de `this` :  
  
 [!code-csharp[csProgGuideObjects#59](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_8.cs)]  
  
 L’utilisation du mot clé `this` dans l’exemple précédent provoque l’appel de ce constructeur :  
  
 [!code-csharp[csProgGuideObjects#60](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_9.cs)]  
  
 Les constructeurs peuvent être marqués comme [public](../../../csharp/language-reference/keywords/public.md), [privé](../../../csharp/language-reference/keywords/private.md), [protégé](../../../csharp/language-reference/keywords/protected.md), [interne](../../../csharp/language-reference/keywords/internal.md), [protégéinterne](../../../csharp/language-reference/keywords/protected-internal.md)ou [protégé privé](../../../csharp/language-reference/keywords/private-protected.md). Ces modificateurs d’accès définissent la façon dont les utilisateurs de la classe peuvent construire la classe. Pour plus d’informations, consultez [Modificateurs d’accès](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).  
  
 Un constructeur peut être déclaré statique à l’aide du mot clé [static](../../../csharp/language-reference/keywords/static.md). Les constructeurs statiques sont appelés automatiquement, juste avant que des champs statiques soient accessibles, et ils sont généralement utilisés pour initialiser des membres de classe statique. Pour plus d’informations, consultez [Constructeurs statiques](../../../csharp/programming-guide/classes-and-structs/static-constructors.md).  
  
## <a name="c-language-specification"></a>Spécification du langage C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)  
 [Classes et structs](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [Constructeurs](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
 [Finaliseurs](../../../csharp/programming-guide/classes-and-structs/destructors.md)
