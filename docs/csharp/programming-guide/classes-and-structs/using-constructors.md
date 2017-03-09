---
title: "Utilisation de constructeurs (Guide de programmation C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "constructeurs (C#), à propos des constructeurs"
ms.assetid: 464253b2-fd5d-469a-836d-df0fdf2a43f7
caps.latest.revision: 26
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 26
---
# Utilisation de constructeurs (Guide de programmation C#)
Lorsque [classe](../../../csharp/language-reference/keywords/class.md) ou [struct](../../../csharp/language-reference/keywords/struct.md) est créé, son constructeur est appelé.  Les constructeurs portent le même nom que la classe ou le struct, et elles initialisent habituellement les données membres du nouvel objet.  
  
 Dans l'exemple suivant, une classe nommée `Taxi` est définie à l'aide d'un simple constructeur.  Cette classe est ensuite instanciée avec un opérateur [new](../../../csharp/language-reference/keywords/new.md).  Le constructeur `Taxi` est appelé par l'opérateur `new` immédiatement après que la mémoire été allouée pour le nouvel objet.  
  
 [!code-cs[csProgGuideObjects#53](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/using-constructors_1.cs)]  
  
 Un constructeur qui ne prend pas de paramètres est appelé  *constructeur par défaut*.  Les constructeurs par défaut sont appelés à chaque fois qu'un objet est instancié à l'aide de l'opérateur `new` et qu'aucun argument n'est fourni à `new`.  Pour plus d'informations, consultez [Constructeurs d'instances](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md).  
  
 À moins que la classe soit [statique](../../../csharp/language-reference/keywords/static.md), les classes sans constructeurs se voient attribuer un constructeur public par défaut par le compilateur C\# pour activer l'instanciation de classe.  Pour plus d'informations, consultez [Classes statiques et membres de classe statique](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).  
  
 Vous pouvez empêcher qu'une classe soit instanciée en rendant le constructeur privé, comme suit :  
  
 [!code-cs[csProgGuideObjects#11](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/using-constructors_2.cs)]  
  
 Pour plus d'informations, consultez [Constructeurs privés](../../../csharp/programming-guide/classes-and-structs/private-constructors.md).  
  
 Les constructeurs pour les types [struct](../../../csharp/language-reference/keywords/struct.md) ressemblent aux constructeurs de classe, mais les `structs` ne peuvent pas contenir de constructeur par défaut explicite, car le compilateur en fournit automatiquement un.  Ce constructeur initialise chaque champ dans le `struct` aux valeurs par défaut.  Pour plus d'informations, consultez [Tableau des valeurs par défaut](../../../csharp/language-reference/keywords/default-values-table.md).  Toutefois, ce constructeur par défaut est appelé uniquement si le `struct` est instancié avec `new`.  Par exemple, ce code utilise le constructeur par défaut pour <xref:System.Int32>. Vous êtes par conséquent assuré que l'entier est initialisé :  
  
```  
int i = new int();  
Console.WriteLine(i);  
```  
  
 Toutefois, le code suivant provoque une erreur de compilateur, car il n'utilise pas `new` et parce qu'il essaie d'utiliser un objet qui n'a pas été initialisé :  
  
```  
int i;  
Console.WriteLine(i);  
```  
  
 Les objets basés sur des `structs` \(y compris tous les types numériques intégrés\) peuvent également être initialisés ou assignés, puis utilisés, comme dans l'exemple suivant :  
  
```  
int a = 44;  // Initialize the value type...  
int b;  
b = 33;      // Or assign it before using it.  
Console.WriteLine("{0}, {1}", a, b);  
```  
  
 Ainsi, l'appel du constructeur par défaut pour un type valeur n'est pas obligatoire.  
  
 Les classes et les `structs` peuvent définir des constructeurs qui prennent des paramètres.  Les constructeurs qui prennent des paramètres doivent être appelés à l'aide d'une instruction `new` ou d'une instruction [de base](../../../csharp/language-reference/keywords/base.md).  Les classes et les `structs` peuvent également définir plusieurs constructeurs, et aucun n'est requis pour définir un constructeur par défaut.  Par exemple :  
  
 [!code-cs[csProgGuideObjects#54](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/using-constructors_3.cs)]  
  
 Cette classe peut être créée à l'aide de l'une ou l'autre des instructions suivantes :  
  
 [!code-cs[csProgGuideObjects#55](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/using-constructors_4.cs)]  
  
 Un constructeur peut utiliser le mot clé `base` pour appeler le constructeur d'une classe de base.  Par exemple :  
  
 [!code-cs[csProgGuideObjects#56](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/using-constructors_5.cs)]  
  
 Dans cet exemple, le constructeur de la classe de base est appelé avant que le bloc du constructeur soit exécuté.  Le mot clé `base` peut être utilisé avec ou sans paramètres.  Tous les paramètres du constructeur peuvent être utilisés comme paramètres de `base`, ou dans le cadre d'une expression.  Pour plus d'informations, consultez [de base](../../../csharp/language-reference/keywords/base.md).  
  
 Dans une classe dérivée, si un constructeur de classe de base n'est pas appelé explicitement à l'aide du mot clé `base`, le constructeur par défaut, s'il existe, est appelé implicitement.  Cela signifie que les déclarations de constructeur suivantes sont en réalité les mêmes :  
  
 [!code-cs[csProgGuideObjects#58](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/using-constructors_6.cs)]  
  
 [!code-cs[csProgGuideObjects#57](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/using-constructors_7.cs)]  
  
 Si une classe de base n'offre pas de constructeur par défaut, la classe dérivée doit faire un appel explicite à un constructeur de base à l'aide du mot clé `base`.  
  
 Un constructeur peut appeler un autre constructeur dans le même objet à l'aide du mot clé [this](../../../csharp/language-reference/keywords/this.md).  Comme `base`, `this` peut être utilisé avec ou sans paramètres, et tous les paramètres dans le constructeur sont disponibles en tant que paramètres pour `this`, ou dans le cadre d'une expression.  Par exemple, le deuxième constructeur de l'exemple précédent peut être réécrit à l'aide de `this` :  
  
 [!code-cs[csProgGuideObjects#59](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/using-constructors_8.cs)]  
  
 L'utilisation du mot clé `this` dans l'exemple précédent provoque l'appel de ce constructeur :  
  
 [!code-cs[csProgGuideObjects#60](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/using-constructors_9.cs)]  
  
 Les constructeurs peuvent être marqués comme étant [publics](../../../csharp/language-reference/keywords/public.md), [privés](../../../csharp/language-reference/keywords/private.md), [protégés](../../../csharp/language-reference/keywords/protected.md), [internes](../../../csharp/language-reference/keywords/internal.md) ou  `protected` `internal`.  Ces modificateurs d'accès définissent comment les utilisateurs de la classe peuvent construire la classe.  Pour plus d'informations, consultez [Modificateurs d'accès](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).  
  
 Un constructeur peut être déclaré statique à l'aide du mot clé [static](../../../csharp/language-reference/keywords/static.md).  Les constructeurs statiques sont appelés automatiquement, juste avant qu'un champ statique soit accessible, et ils sont généralement utilisés pour initialiser des membres de classe statique.  Pour plus d'informations, consultez [Constructeurs statiques](../../../csharp/programming-guide/classes-and-structs/static-constructors.md).  
  
## Spécification du langage C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## Voir aussi  
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Classes et structs](../../../csharp/programming-guide/classes-and-structs/index.md)   
 [Constructeurs](../../../csharp/programming-guide/classes-and-structs/constructors.md)   
 [Destructeurs](../../../csharp/programming-guide/classes-and-structs/destructors.md)