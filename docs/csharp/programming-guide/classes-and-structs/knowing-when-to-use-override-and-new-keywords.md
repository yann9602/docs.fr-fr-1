---
title: "Savoir quand utiliser les mots cl&#233;s override et new (Guide de programmation C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "new (mot clé C#)"
  - "override (mot clé C#)"
  - "polymorphisme (C#), utiliser override et new (C#)"
ms.assetid: 323db184-b136-46fc-8839-007886e7e8b0
caps.latest.revision: 16
caps.handback.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Savoir quand utiliser les mots cl&#233;s override et new (Guide de programmation C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

En C\#, une méthode dans une classe dérivée peut avoir le même nom qu'une méthode dans la classe de base.  Vous pouvez spécifier comment les méthodes interagissent en utilisant les mots clés [new](../../../csharp/language-reference/keywords/new.md) et [override](../../../csharp/language-reference/keywords/override.md).  Le modificateur `override` *étend* la méthode de classe de base, et le modificateur `new` *le masque*.  La différence est illustrée dans les exemples de cette rubrique.  
  
 Dans une application de console, déclarez les deux classes suivantes, `BaseClass` et `DerivedClass`.  `DerivedClass` hérite de `BaseClass`.  
  
```c#  
class BaseClass  
{  
    public void Method1()  
    {  
        Console.WriteLine("Base - Method1");  
    }  
}  
  
class DerivedClass : BaseClass  
{  
    public void Method2()  
    {  
        Console.WriteLine("Derived - Method2");  
    }  
}  
  
```  
  
 Dans la méthode `Main`, déclarez les variables `bc`, `dc` et `bcdc`.  
  
-   `bc` est du type `BaseClass` et sa valeur est du type `BaseClass`.  
  
-   `dc` est du type `DerivedClass` et sa valeur est du type `DerivedClass`.  
  
-   `bcdc` est du type `BaseClass` et sa valeur est du type `DerivedClass`.  Il s'agit de la variable à laquelle prêter attention.  
  
 Étant donné que `bc` et `bcdc` ont le type `BaseClass`, ils peuvent uniquement accéder directement à `Method1`, à moins que vous n'utilisiez le casting.  La variable `dc` peut accéder à `Method1` et `Method2`.  Ces relations sont illustrées dans le code suivant.  
  
```c#  
class Program  
{  
    static void Main(string[] args)  
    {  
        BaseClass bc = new BaseClass();  
        DerivedClass dc = new DerivedClass();  
        BaseClass bcdc = new DerivedClass();  
  
        bc.Method1();  
        dc.Method1();  
        dc.Method2();  
        bcdc.Method1();  
    }  
    // Output:  
    // Base - Method1  
    // Base - Method1  
    // Derived - Method2  
    // Base - Method1  
}  
  
```  
  
 Ensuite, ajoutez le code suivant à la méthode `Method2` à `BaseClass`.  La signature de cette méthode correspond à celle de la méthode `Method2` dans `DerivedClass`.  
  
```c#  
public void Method2()  
{  
    Console.WriteLine("Base - Method2");  
}  
  
```  
  
 Étant donné que `BaseClass` a maintenant une méthode `Method2`, une deuxième instruction d'appel peut être ajoutée pour les variables `bc` et `bcdc` de `BaseClass`, comme indiqué dans le code suivant.  
  
```c#  
bc.Method1();  
bc.Method2();  
dc.Method1();  
dc.Method2();  
bcdc.Method1();  
bcdc.Method2();  
  
```  
  
 Lorsque vous générez le projet, vous constatez que l'ajout de la méthode `Method2` dans `BaseClass` provoque un avertissement.  L'avertissement indique que la méthode `Method2` dans `DerivedClass` masque la méthode `Method2` dans `BaseClass`.  Il est recommandé d'utiliser le mot clé `new` dans la définition de `Method2` si vous envisagez de provoquer ce résultat.  Vous pouvez également renommer l'une des méthodes `Method2` pour résoudre l'avertissement, mais ce n'est pas toujours pratique.  
  
 Avant d'ajouter `new`, exécutez le programme pour consulter la sortie générée par les instructions d'appel supplémentaires.  Les résultats suivantes s'affichent.  
  
```c#  
// Output:  
// Base - Method1  
// Base - Method2  
// Base - Method1  
// Derived - Method2  
// Base - Method1  
// Base - Method2  
  
```  
  
 Le mot clé `new` conserve les relations qui génèrent cette sortie, mais il supprime l'avertissement.  Les variables qui ont le type `BaseClass` continuent à accéder aux membres de `BaseClass`, et la variable qui a le type `DerivedClass` continue à accéder d'abord aux membres dans `DerivedClass`, et à considérer ensuite les membres hérités de `BaseClass`.  
  
 Pour supprimer l'avertissement, ajoutez le modificateur `new` à la définition de `Method2` dans `DerivedClass`, comme indiqué dans le code suivant.  Le modificateur peut être ajouté avant ou après `public`.  
  
```c#  
public new void Method2()  
{  
    Console.WriteLine("Derived - Method2");  
}  
  
```  
  
 Exécutez à nouveau le programme afin de vérifier que la sortie n'a pas changé.  Vérifiez également que l'avertissement ne s'affiche plus.  À l'aide de `new`, vous déclarez que vous réalisez que le membre qu'il modifie masque un membre hérité de la classe de base.  Pour plus d'informations sur le masquage des noms par l'intermédiaire de l'héritage, consultez [new, modificateur](../../../csharp/language-reference/keywords/new-modifier.md).  
  
 Pour contraster ce comportement aux effets de l'utilisation de `override`, ajoutez la méthode suivante à `DerivedClass`.  Le modificateur `override` peut être ajouté avant ou après `public`.  
  
```c#  
public override void Method1()  
{  
    Console.WriteLine("Derived - Method1");  
}  
  
```  
  
 Ajoutez le modificateur `virtual` à la définition de `Method1` dans `BaseClass`.  Le modificateur `virtual` peut être ajouté avant ou après `public`.  
  
```c#  
public virtual void Method1()  
{  
    Console.WriteLine("Base - Method1");  
}  
  
```  
  
 Réexécutez le projet.  Notez en particulier les deux dernières lignes de la sortie suivante.  
  
```c#  
// Output:  
// Base - Method1  
// Base - Method2  
// Derived - Method1  
// Derived - Method2  
// Derived - Method1  
// Base - Method2  
  
```  
  
 L'utilisation du modificateur `override` permet à `bcdc` d'accéder à la méthode `Method1` définie dans `DerivedClass`.  En général, c'est le comportement voulu dans les hiérarchies d'héritage.  Vous voulez des objets dont les valeurs sont créées depuis  la classe dérivée pour utiliser les méthodes définies dans la classe dérivée.  Vous réalisez ce comportement avec `override` pour étendre la méthode de la classe de base.  
  
 Le code suivant inclut l'exemple complet.  
  
```c#  
using System;  
using System.Text;  
  
namespace OverrideAndNew  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            BaseClass bc = new BaseClass();  
            DerivedClass dc = new DerivedClass();  
            BaseClass bcdc = new DerivedClass();  
  
            // The following two calls do what you would expect. They call  
            // the methods that are defined in BaseClass.  
            bc.Method1();  
            bc.Method2();  
            // Output:  
            // Base - Method1  
            // Base - Method2  
  
            // The following two calls do what you would expect. They call  
            // the methods that are defined in DerivedClass.  
            dc.Method1();  
            dc.Method2();  
            // Output:  
            // Derived - Method1  
            // Derived - Method2  
  
            // The following two calls produce different results, depending   
            // on whether override (Method1) or new (Method2) is used.  
            bcdc.Method1();  
            bcdc.Method2();  
            // Output:  
            // Derived - Method1  
            // Base - Method2  
        }  
    }  
  
    class BaseClass  
    {  
        public virtual void Method1()  
        {  
            Console.WriteLine("Base - Method1");  
        }  
  
        public virtual void Method2()  
        {  
            Console.WriteLine("Base - Method2");  
        }  
    }  
  
    class DerivedClass : BaseClass  
    {  
        public override void Method1()  
        {  
            Console.WriteLine("Derived - Method1");  
        }  
  
        public new void Method2()  
        {  
            Console.WriteLine("Derived - Method2");  
        }  
    }  
}  
  
```  
  
 L'exemple suivant illustre un comportement similaire dans un contexte différent.  L'exemple définit trois classes : une classe de base nommée `Car` et deux classes dérivés de celle\-ci, `ConvertibleCar` et `Minivan`.  La classe de base contient une méthode `DescribeCar`.  La méthode affiche une description de base d'une voiture, puis appelle `ShowDetails` pour fournir des informations supplémentaires.  Chacune des trois classes définit une méthode `ShowDetails`.  Le modificateur `new` est utilisé pour définir `ShowDetails` dans la classe `ConvertibleCar`.  Le modificateur `override` est utilisé pour définir `ShowDetails` dans la classe `Minivan`.  
  
```c#  
// Define the base class, Car. The class defines two methods,  
// DescribeCar and ShowDetails. DescribeCar calls ShowDetails, and each derived  
// class also defines a ShowDetails method. The example tests which version of  
// ShowDetails is selected, the base class method or the derived class method.  
class Car  
{  
    public void DescribeCar()  
    {  
        System.Console.WriteLine("Four wheels and an engine.");  
        ShowDetails();  
    }  
  
    public virtual void ShowDetails()  
    {  
        System.Console.WriteLine("Standard transportation.");  
    }  
}  
  
// Define the derived classes.  
  
// Class ConvertibleCar uses the new modifier to acknowledge that ShowDetails  
// hides the base class method.  
class ConvertibleCar : Car  
{  
    public new void ShowDetails()  
    {  
        System.Console.WriteLine("A roof that opens up.");  
    }  
}  
  
// Class Minivan uses the override modifier to specify that ShowDetails  
// extends the base class method.  
class Minivan : Car  
{  
    public override void ShowDetails()  
    {  
        System.Console.WriteLine("Carries seven people.");  
    }  
}  
  
```  
  
 L'exemple teste quelle version de `ShowDetails` est appelée.  La méthode suivante, `TestCars1`, déclare une instance de chaque classe, puis appelle `DescribeCar` sur chaque instance.  
  
```c#  
public static void TestCars1()  
{  
    System.Console.WriteLine("\nTestCars1");  
    System.Console.WriteLine("----------");  
  
    Car car1 = new Car();  
    car1.DescribeCar();  
    System.Console.WriteLine("----------");  
  
    // Notice the output from this test case. The new modifier is  
    // used in the definition of ShowDetails in the ConvertibleCar  
    // class.    
  
    ConvertibleCar car2 = new ConvertibleCar();  
    car2.DescribeCar();  
    System.Console.WriteLine("----------");  
  
    Minivan car3 = new Minivan();  
    car3.DescribeCar();  
    System.Console.WriteLine("----------");  
}  
  
```  
  
 `TestCars1` génère la sortie suivante.  Notez en particulier les résultats de `car2`, qui ne correspondent probablement pas à ce que vous attendiez.  Le type de l'objet est `ConvertibleCar`, mais `DescribeCar` n'accède pas à la version de `ShowDetails` qui est définie dans la classe `ConvertibleCar`, car cette méthode est déclarée avec le modificateur `new`, et non le modificateur `override`.  Par conséquent, un objet `ConvertibleCar` affiche la même description qu'un objet `Car`.  Comparez les résultats pour `car3`, qui est un objet `Minivan`.  Dans ce cas, la méthode `ShowDetails` déclarée dans la classe `Minivan` écrase la méthode `ShowDetails` déclarée dans la classe `Car` et la description affichée décrit un espacement fixe.  
  
```c#  
  
// TestCars1  
// ----------  
// Four wheels and an engine.  
// Standard transportation.  
// ----------  
// Four wheels and an engine.  
// Standard transportation.  
// ----------  
// Four wheels and an engine.  
// Carries seven people.  
// ----------  
  
```  
  
 `TestCars2` crée une liste d'objets qui ont le type `Car`.  Les valeurs des objets sont instanciées à partir des classes `Car`, `ConvertibleCar` et `Minivan`.  `DescribeCar` est appelé sur chaque élément de la liste.  Le code suivant montre la définition de `TestCars2`.  
  
```c#  
public static void TestCars2()  
{  
    System.Console.WriteLine("\nTestCars2");  
    System.Console.WriteLine("----------");  
  
    var cars = new List<Car> { new Car(), new ConvertibleCar(),   
        new Minivan() };  
  
    foreach (var car in cars)  
    {  
        car.DescribeCar();  
        System.Console.WriteLine("----------");  
    }  
}  
  
```  
  
 Le code suivant s'affiche.  Notez qu'il est identique à la sortie affichée par `TestCars1`.  La méthode `ShowDetails` de la classe `ConvertibleCar` n'est pas appelée, que le type de l'objet soit `ConvertibleCar`, comme dans `TestCars1` ou `Car`, comme dans `TestCars2`.  Inversement, `car3` appelle la méthode `ShowDetails` de la classe `Minivan` dans les deux cas, avec le type `Minivan` ou `Car`.  
  
```c#  
// TestCars2  
// ----------  
// Four wheels and an engine.  
// Standard transportation.  
// ----------  
// Four wheels and an engine.  
// Standard transportation.  
// ----------  
// Four wheels and an engine.  
// Carries seven people.  
// ----------  
  
```  
  
 Les méthodes `TestCars3` et `TestCars4` terminent l'exemple.  Ces méthodes appellent `ShowDetails` directement, tout d'abord à partir d'objets déclarés comme ayant le type `ConvertibleCar` et `Minivan` \(`TestCars3`\), puis à partir d'objets déclarés comme ayant le type `Car` \(`TestCars4`\).  Le code suivant définit ces deux méthodes.  
  
```c#  
  
public static void TestCars3()  
{  
    System.Console.WriteLine("\nTestCars3");  
    System.Console.WriteLine("----------");  
    ConvertibleCar car2 = new ConvertibleCar();  
    Minivan car3 = new Minivan();  
    car2.ShowDetails();  
    car3.ShowDetails();  
}  
  
public static void TestCars4()  
{  
    System.Console.WriteLine("\nTestCars4");  
    System.Console.WriteLine("----------");  
    Car car2 = new ConvertibleCar();  
    Car car3 = new Minivan();  
    car2.ShowDetails();  
    car3.ShowDetails();  
}  
  
```  
  
 Les méthodes produisent la sortie suivante, qui correspond aux résultats du premier exemple de cette rubrique.  
  
```c#  
// TestCars3  
// ----------  
// A roof that opens up.  
// Carries seven people.  
  
// TestCars4  
// ----------  
// Standard transportation.  
// Carries seven people.  
  
```  
  
 Le code suivant montre le projet terminé et sa sortie.  
  
```c#  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
  
namespace OverrideAndNew2  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            // Declare objects of the derived classes and test which version  
            // of ShowDetails is run, base or derived.  
            TestCars1();  
  
            // Declare objects of the base class, instantiated with the  
            // derived classes, and repeat the tests.  
            TestCars2();  
  
            // Declare objects of the derived classes and call ShowDetails  
            // directly.  
            TestCars3();  
  
            // Declare objects of the base class, instantiated with the  
            // derived classes, and repeat the tests.  
            TestCars4();  
        }  
  
        public static void TestCars1()  
        {  
            System.Console.WriteLine("\nTestCars1");  
            System.Console.WriteLine("----------");  
  
            Car car1 = new Car();  
            car1.DescribeCar();  
            System.Console.WriteLine("----------");  
  
            // Notice the output from this test case. The new modifier is  
            // used in the definition of ShowDetails in the ConvertibleCar  
            // class.    
            ConvertibleCar car2 = new ConvertibleCar();  
            car2.DescribeCar();  
            System.Console.WriteLine("----------");  
  
            Minivan car3 = new Minivan();  
            car3.DescribeCar();  
            System.Console.WriteLine("----------");  
        }  
        // Output:  
        // TestCars1  
        // ----------  
        // Four wheels and an engine.  
        // Standard transportation.  
        // ----------  
        // Four wheels and an engine.  
        // Standard transportation.  
        // ----------  
        // Four wheels and an engine.  
        // Carries seven people.  
        // ----------  
  
        public static void TestCars2()  
        {  
            System.Console.WriteLine("\nTestCars2");  
            System.Console.WriteLine("----------");  
  
            var cars = new List<Car> { new Car(), new ConvertibleCar(),   
                new Minivan() };  
  
            foreach (var car in cars)  
            {  
                car.DescribeCar();  
                System.Console.WriteLine("----------");  
            }  
        }  
        // Output:  
        // TestCars2  
        // ----------  
        // Four wheels and an engine.  
        // Standard transportation.  
        // ----------  
        // Four wheels and an engine.  
        // Standard transportation.  
        // ----------  
        // Four wheels and an engine.  
        // Carries seven people.  
        // ----------  
  
        public static void TestCars3()  
        {  
            System.Console.WriteLine("\nTestCars3");  
            System.Console.WriteLine("----------");  
            ConvertibleCar car2 = new ConvertibleCar();  
            Minivan car3 = new Minivan();  
            car2.ShowDetails();  
            car3.ShowDetails();  
        }  
        // Output:  
        // TestCars3  
        // ----------  
        // A roof that opens up.  
        // Carries seven people.  
  
        public static void TestCars4()  
        {  
            System.Console.WriteLine("\nTestCars4");  
            System.Console.WriteLine("----------");  
            Car car2 = new ConvertibleCar();  
            Car car3 = new Minivan();  
            car2.ShowDetails();  
            car3.ShowDetails();  
        }  
        // Output:  
        // TestCars4  
        // ----------  
        // Standard transportation.  
        // Carries seven people.  
    }  
  
    // Define the base class, Car. The class defines two virtual methods,  
    // DescribeCar and ShowDetails. DescribeCar calls ShowDetails, and each derived  
    // class also defines a ShowDetails method. The example tests which version of  
    // ShowDetails is used, the base class method or the derived class method.  
    class Car  
    {  
        public virtual void DescribeCar()  
        {  
            System.Console.WriteLine("Four wheels and an engine.");  
            ShowDetails();  
        }  
  
        public virtual void ShowDetails()  
        {  
            System.Console.WriteLine("Standard transportation.");  
        }  
    }  
  
    // Define the derived classes.  
  
    // Class ConvertibleCar uses the new modifier to acknowledge that ShowDetails  
    // hides the base class method.  
    class ConvertibleCar : Car  
    {  
        public new void ShowDetails()  
        {  
            System.Console.WriteLine("A roof that opens up.");  
        }  
    }  
  
    // Class Minivan uses the override modifier to specify that ShowDetails  
    // extends the base class method.  
    class Minivan : Car  
    {  
        public override void ShowDetails()  
        {  
            System.Console.WriteLine("Carries seven people.");  
        }  
    }  
  
}  
  
```  
  
## Voir aussi  
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Classes et structs](../../../csharp/programming-guide/classes-and-structs/index.md)   
 [Versioning avec les mots clés override et new](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md)   
 [de base](../../../csharp/language-reference/keywords/base.md)   
 [abstract](../../../csharp/language-reference/keywords/abstract.md)