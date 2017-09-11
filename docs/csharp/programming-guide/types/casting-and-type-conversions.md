---
title: Cast et conversions de types (Guide de programmation C#)
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- type conversion [C#]
- data type conversion [C#]
- numeric conversions [C#]
- conversions [C#], type
- casting [C#]
- converting types [C#]
ms.assetid: 568df58a-d292-4b55-93ba-601578722878
caps.latest.revision: 52
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
ms.openlocfilehash: 20743c07c8e9c6b7ec24cf52a28bb9f451ba9df5
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="casting-and-type-conversions-c-programming-guide"></a><span data-ttu-id="95d6a-102">Cast et conversions de types (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="95d6a-102">Casting and Type Conversions (C# Programming Guide)</span></span>
<span data-ttu-id="95d6a-103">C# est typé statiquement au moment de la compilation. Ainsi, quand une variable est déclarée, elle ne peut plus être redéclarée ou utilisée pour stocker des valeurs d’un autre type, sauf si ce type peut être converti au type de la variable.</span><span class="sxs-lookup"><span data-stu-id="95d6a-103">Because C# is statically-typed at compile time, after a variable is declared, it cannot be declared again or used to store values of another type unless that type is convertible to the variable's type.</span></span> <span data-ttu-id="95d6a-104">Par exemple, il est impossible de convertir un entier en chaîne arbitraire.</span><span class="sxs-lookup"><span data-stu-id="95d6a-104">For example, there is no conversion from an integer to any arbitrary string.</span></span> <span data-ttu-id="95d6a-105">Après avoir déclaré `i` comme entier, vous ne pouvez donc pas lui assigner la chaîne « Hello » comme le montre le code suivant.</span><span class="sxs-lookup"><span data-stu-id="95d6a-105">Therefore, after you declare `i` as an integer, you cannot assign the string "Hello" to it, as is shown in the following code.</span></span>  
  
```csharp  
int i;  
i = "Hello"; // Error: "Cannot implicitly convert type 'string' to 'int'"  
```  
  
 <span data-ttu-id="95d6a-106">Cependant, vous pouvez être amené à copier une valeur dans un paramètre de variable ou de méthode d’un autre type.</span><span class="sxs-lookup"><span data-stu-id="95d6a-106">However, you might sometimes need to copy a value into a variable or method parameter of another type.</span></span> <span data-ttu-id="95d6a-107">C’est notamment le cas si vous avez une variable de type entier que vous devez passer à une méthode dont le paramètre est de type `double`.</span><span class="sxs-lookup"><span data-stu-id="95d6a-107">For example, you might have an integer variable that you need to pass to a method whose parameter is typed as `double`.</span></span> <span data-ttu-id="95d6a-108">Il peut également arriver que vous deviez assigner une variable de classe à une variable de type interface.</span><span class="sxs-lookup"><span data-stu-id="95d6a-108">Or you might need to assign a class variable to a variable of an interface type.</span></span> <span data-ttu-id="95d6a-109">Les opérations de ce genre sont appelées « *conversions de types* ».</span><span class="sxs-lookup"><span data-stu-id="95d6a-109">These kinds of operations are called *type conversions*.</span></span> <span data-ttu-id="95d6a-110">En C#, vous pouvez effectuer les conversions suivantes :</span><span class="sxs-lookup"><span data-stu-id="95d6a-110">In C#, you can perform the following kinds of conversions:</span></span>  
  
-   <span data-ttu-id="95d6a-111">**Conversions implicites** : aucune syntaxe spéciale n’est requise, car la conversion est de type sécurisé et les données ne sont pas perdues.</span><span class="sxs-lookup"><span data-stu-id="95d6a-111">**Implicit conversions**: No special syntax is required because the conversion is type safe and no data will be lost.</span></span> <span data-ttu-id="95d6a-112">Citons par exemple les conversions de types intégraux en d’autres plus importants, et les conversions de classes dérivées en classes de base.</span><span class="sxs-lookup"><span data-stu-id="95d6a-112">Examples include conversions from smaller to larger integral types, and conversions from derived classes to base classes.</span></span>  
  
-   <span data-ttu-id="95d6a-113">**Conversions explicites (casts)** : les conversions explicites nécessitent un opérateur de cast.</span><span class="sxs-lookup"><span data-stu-id="95d6a-113">**Explicit conversions (casts)**: Explicit conversions require a cast operator.</span></span> <span data-ttu-id="95d6a-114">Un cast est exigé quand les informations peuvent être perdues durant la conversion, ou quand la conversion peut échouer pour d’autres raisons.</span><span class="sxs-lookup"><span data-stu-id="95d6a-114">Casting is required when information might be lost in the conversion, or when the conversion might not succeed for other reasons.</span></span>  <span data-ttu-id="95d6a-115">Exemples classiques : conversion numérique en type qui a moins de précision ou une plus petite plage, et conversion d’une instance de classe de base en classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="95d6a-115">Typical examples include numeric conversion to a type that has less precision or a smaller range, and conversion of a base-class instance to a derived class.</span></span>  
  
-   <span data-ttu-id="95d6a-116">**Conversions définies par l’utilisateur** : les conversions définies par l’utilisateur sont effectuées par des méthodes spéciales que vous pouvez définir pour permettre des conversions explicites ou implicites entre des types personnalisés qui n’ont pas de relation classe de base/classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="95d6a-116">**User-defined conversions**: User-defined conversions are performed by special methods that you can define to enable explicit and implicit conversions between custom types that do not have a base class–derived class relationship.</span></span> <span data-ttu-id="95d6a-117">Pour plus d’informations, consultez [Conversion, opérateurs](../../../csharp/programming-guide/statements-expressions-operators/conversion-operators.md).</span><span class="sxs-lookup"><span data-stu-id="95d6a-117">For more information, see [Conversion Operators](../../../csharp/programming-guide/statements-expressions-operators/conversion-operators.md).</span></span>  
  
-   <span data-ttu-id="95d6a-118">**Conversions avec les classes d’assistance** : pour effectuer une conversion entre des types non compatibles, tels que des entiers et des objets <xref:System.DateTime?displayProperty=fullName> ou des chaînes hexadécimales et des tableaux d’octets, vous pouvez utiliser la classe <xref:System.BitConverter?displayProperty=fullName>, la classe <xref:System.Convert?displayProperty=fullName> et les méthodes `Parse` des types numériques intégrés, comme <xref:System.Int32.Parse%2A?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="95d6a-118">**Conversions with helper classes**: To convert between non-compatible types, such as integers and <xref:System.DateTime?displayProperty=fullName> objects, or hexadecimal strings and byte arrays, you can use the <xref:System.BitConverter?displayProperty=fullName> class, the <xref:System.Convert?displayProperty=fullName> class, and the `Parse` methods of the built-in numeric types, such as <xref:System.Int32.Parse%2A?displayProperty=fullName>.</span></span> <span data-ttu-id="95d6a-119">Pour plus d’informations, consultez [Guide pratique pour convertir un tableau d’octets en int](../../../csharp/programming-guide/types/how-to-convert-a-byte-array-to-an-int.md), [Guide pratique pour convertir une chaîne en nombre](../../../csharp/programming-guide/types/how-to-convert-a-string-to-a-number.md) et [Guide pratique pour effectuer une conversion entre des chaînes hexadécimales et des types numériques](../../../csharp/programming-guide/types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md).</span><span class="sxs-lookup"><span data-stu-id="95d6a-119">For more information, see [How to: Convert a byte Array to an int](../../../csharp/programming-guide/types/how-to-convert-a-byte-array-to-an-int.md), [How to: Convert a String to a Number](../../../csharp/programming-guide/types/how-to-convert-a-string-to-a-number.md), and [How to: Convert Between Hexadecimal Strings and Numeric Types](../../../csharp/programming-guide/types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md).</span></span>  
  
## <a name="implicit-conversions"></a><span data-ttu-id="95d6a-120">Conversions implicites</span><span class="sxs-lookup"><span data-stu-id="95d6a-120">Implicit Conversions</span></span>  
 <span data-ttu-id="95d6a-121">Pour les types numériques intégrés, une conversion implicite peut être effectuée quand la valeur à stocker peut tenir dans la variable sans être tronquée ni arrondie.</span><span class="sxs-lookup"><span data-stu-id="95d6a-121">For built-in numeric types, an implicit conversion can be made when the value to be stored can fit into the variable without being truncated or rounded off.</span></span> <span data-ttu-id="95d6a-122">Par exemple, une variable de type [long](../../../csharp/language-reference/keywords/long.md) (entier sur 8 octets) peut stocker n’importe quelle valeur stockée par un [int](../../../csharp/language-reference/keywords/int.md) (4 octets sur un ordinateur 32 bits).</span><span class="sxs-lookup"><span data-stu-id="95d6a-122">For example, a variable of type [long](../../../csharp/language-reference/keywords/long.md) (8 byte integer) can store any value that an [int](../../../csharp/language-reference/keywords/int.md) (4 bytes on a 32-bit computer) can store.</span></span> <span data-ttu-id="95d6a-123">Dans l’exemple suivant, le compilateur convertit implicitement la valeur à droite en type `long` avant de l’assigner à `bigNum`.</span><span class="sxs-lookup"><span data-stu-id="95d6a-123">In the following example, the compiler implicitly converts the value on the right to a type `long` before assigning it to `bigNum`.</span></span>  
  
 <span data-ttu-id="95d6a-124">[!code-cs[csProgGuideTypes#34](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/casting-and-type-conversions_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="95d6a-124">[!code-cs[csProgGuideTypes#34](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/casting-and-type-conversions_1.cs)]</span></span>  
  
 <span data-ttu-id="95d6a-125">Pour obtenir la liste complète de toutes les conversions numériques implicites, consultez [Tableau des conversions numériques implicites](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).</span><span class="sxs-lookup"><span data-stu-id="95d6a-125">For a complete list of all implicit numeric conversions, see [Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).</span></span>  
  
 <span data-ttu-id="95d6a-126">Pour les types référence, il existe toujours une conversion implicite entre une classe et l’une de ses interfaces ou classes de base directes ou indirectes.</span><span class="sxs-lookup"><span data-stu-id="95d6a-126">For reference types, an implicit conversion always exists from a class to any one of its direct or indirect base classes or interfaces.</span></span> <span data-ttu-id="95d6a-127">Aucune syntaxe spéciale n’est nécessaire, car une classe dérivée contient toujours tous les membres d’une classe de base.</span><span class="sxs-lookup"><span data-stu-id="95d6a-127">No special syntax is necessary because a derived class always contains all the members of a base class.</span></span>  
  
```  
Derived d = new Derived();  
Base b = d; // Always OK.  
```  
  
## <a name="explicit-conversions"></a><span data-ttu-id="95d6a-128">Conversions explicites</span><span class="sxs-lookup"><span data-stu-id="95d6a-128">Explicit Conversions</span></span>  
 <span data-ttu-id="95d6a-129">Toutefois, si une conversion ne peut pas être réalisée sans risque de perte d’informations, le compilateur exige une conversion explicite, aussi appelée *cast*.</span><span class="sxs-lookup"><span data-stu-id="95d6a-129">However, if a conversion cannot be made without a risk of losing information, the compiler requires that you perform an explicit conversion, which is called a *cast*.</span></span> <span data-ttu-id="95d6a-130">Un cast est une façon d’informer explicitement le compilateur que vous prévoyez de faire la conversion et que vous savez qu’une perte de données peut se produire.</span><span class="sxs-lookup"><span data-stu-id="95d6a-130">A cast is a way of explicitly informing the compiler that you intend to make the conversion and that you are aware that data loss might occur.</span></span> <span data-ttu-id="95d6a-131">Pour effectuer un cast, spécifiez le type voulu entre parenthèses devant la valeur ou la variable à convertir.</span><span class="sxs-lookup"><span data-stu-id="95d6a-131">To perform a cast, specify the type that you are casting to in parentheses in front of the value or variable to be converted.</span></span> <span data-ttu-id="95d6a-132">Le programme suivant effectue un cast d’un [double](../../../csharp/language-reference/keywords/double.md) en [int](../../../csharp/language-reference/keywords/int.md).</span><span class="sxs-lookup"><span data-stu-id="95d6a-132">The following program casts a [double](../../../csharp/language-reference/keywords/double.md) to an [int](../../../csharp/language-reference/keywords/int.md).</span></span> <span data-ttu-id="95d6a-133">Le programme ne se compile pas sans le cast.</span><span class="sxs-lookup"><span data-stu-id="95d6a-133">The program will not compile without the cast.</span></span>  
  
 <span data-ttu-id="95d6a-134">[!code-cs[csProgGuideTypes#2](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/casting-and-type-conversions_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="95d6a-134">[!code-cs[csProgGuideTypes#2](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/casting-and-type-conversions_2.cs)]</span></span>  
  
 <span data-ttu-id="95d6a-135">Pour obtenir la liste des conversions numériques explicites autorisées, consultez [Tableau des conversions numériques explicites](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md).</span><span class="sxs-lookup"><span data-stu-id="95d6a-135">For a list of the explicit numeric conversions that are allowed, see [Explicit Numeric Conversions Table](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md).</span></span>  
  
 <span data-ttu-id="95d6a-136">Pour les types référence, un cast explicite est exigé si vous devez effectuer une conversion d’un type de base en type dérivé :</span><span class="sxs-lookup"><span data-stu-id="95d6a-136">For reference types, an explicit cast is required if you need to convert from a base type to a derived type:</span></span>  
  
```csharp  
// Create a new derived type.  
Giraffe g = new Giraffe();  
  
// Implicit conversion to base type is safe.  
Animal a = g;  
  
// Explicit conversion is required to cast back  
// to derived type. Note: This will compile but will  
// throw an exception at run time if the right-side  
// object is not in fact a Giraffe.  
Giraffe g2 = (Giraffe) a;  
```  
  
 <span data-ttu-id="95d6a-137">Une opération cast entre types référence ne change pas le type au moment de l’exécution de l’objet sous-jacent. Elle change seulement le type de la valeur utilisée comme référence à cet objet.</span><span class="sxs-lookup"><span data-stu-id="95d6a-137">A cast operation between reference types does not change the run-time type of the underlying object; it only changes the type of the value that is being used as a reference to that object.</span></span> <span data-ttu-id="95d6a-138">Pour plus d’informations, consultez [Polymorphisme](../../../csharp/programming-guide/classes-and-structs/polymorphism.md).</span><span class="sxs-lookup"><span data-stu-id="95d6a-138">For more information, see [Polymorphism](../../../csharp/programming-guide/classes-and-structs/polymorphism.md).</span></span>  
  
## <a name="type-conversion-exceptions-at-run-time"></a><span data-ttu-id="95d6a-139">Exceptions de conversion de type au moment de l’exécution</span><span class="sxs-lookup"><span data-stu-id="95d6a-139">Type Conversion Exceptions at Run Time</span></span>  
 <span data-ttu-id="95d6a-140">Dans certaines conversions de types référence, le compilateur ne peut pas déterminer si un cast sera valide.</span><span class="sxs-lookup"><span data-stu-id="95d6a-140">In some reference type conversions, the compiler cannot determine whether a cast will be valid.</span></span> <span data-ttu-id="95d6a-141">Il est possible qu’une opération cast dont la compilation fonctionne échoue au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="95d6a-141">It is possible for a cast operation that compiles correctly to fail at run time.</span></span> <span data-ttu-id="95d6a-142">Comme l’illustre l’exemple suivant, un cast de type qui échoue au moment de l’exécution provoque la levée d’une exception <xref:System.InvalidCastException>.</span><span class="sxs-lookup"><span data-stu-id="95d6a-142">As shown in the following example, a type cast that fails at run time will cause an <xref:System.InvalidCastException> to be thrown.</span></span>  
  
 <span data-ttu-id="95d6a-143">[!code-cs[csProgGuideTypes#41](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/casting-and-type-conversions_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="95d6a-143">[!code-cs[csProgGuideTypes#41](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/casting-and-type-conversions_3.cs)]</span></span>  
  
 <span data-ttu-id="95d6a-144">C# fournit les opérateurs [is](../../../csharp/language-reference/keywords/is.md) et [as](../../../csharp/language-reference/keywords/as.md) pour vous permettre de tester la compatibilité avant d’effectuer réellement un cast.</span><span class="sxs-lookup"><span data-stu-id="95d6a-144">C# provides the [is](../../../csharp/language-reference/keywords/is.md) and [as](../../../csharp/language-reference/keywords/as.md) operators to enable you to test for compatibility before actually performing a cast.</span></span> <span data-ttu-id="95d6a-145">Pour plus d’informations, consultez [Guide pratique pour effectuer sans risque un cast à l’aide des opérateurs as et is](../../../csharp/programming-guide/types/how-to-safely-cast-by-using-as-and-is-operators.md).</span><span class="sxs-lookup"><span data-stu-id="95d6a-145">For more information, see [How to: Safely Cast by Using as and is Operators](../../../csharp/programming-guide/types/how-to-safely-cast-by-using-as-and-is-operators.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="95d6a-146">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="95d6a-146">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  

## <a name="see-also"></a><span data-ttu-id="95d6a-147">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="95d6a-147">See Also</span></span>  
 <span data-ttu-id="95d6a-148">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="95d6a-148">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="95d6a-149">[Types](../../../csharp/programming-guide/types/index.md) </span><span class="sxs-lookup"><span data-stu-id="95d6a-149">[Types](../../../csharp/programming-guide/types/index.md) </span></span>  
 <span data-ttu-id="95d6a-150">[(), opérateur](../../../csharp/language-reference/operators/invocation-operator.md) </span><span class="sxs-lookup"><span data-stu-id="95d6a-150">[() Operator](../../../csharp/language-reference/operators/invocation-operator.md) </span></span>  
 <span data-ttu-id="95d6a-151">[explicit](../../../csharp/language-reference/keywords/explicit.md) </span><span class="sxs-lookup"><span data-stu-id="95d6a-151">[explicit](../../../csharp/language-reference/keywords/explicit.md) </span></span>  
 <span data-ttu-id="95d6a-152">[implicit](../../../csharp/language-reference/keywords/implicit.md) </span><span class="sxs-lookup"><span data-stu-id="95d6a-152">[implicit](../../../csharp/language-reference/keywords/implicit.md) </span></span>  
 <span data-ttu-id="95d6a-153">[Opérateurs de conversion](../../../csharp/programming-guide/statements-expressions-operators/conversion-operators.md) </span><span class="sxs-lookup"><span data-stu-id="95d6a-153">[Conversion Operators](../../../csharp/programming-guide/statements-expressions-operators/conversion-operators.md) </span></span>  
 <span data-ttu-id="95d6a-154">[Conversion de type généralisée](http://msdn.microsoft.com/library/49253ae6-7657-4810-82ab-1176a6feeada) </span><span class="sxs-lookup"><span data-stu-id="95d6a-154">[Generalized Type Conversion](http://msdn.microsoft.com/library/49253ae6-7657-4810-82ab-1176a6feeada) </span></span>  
 <span data-ttu-id="95d6a-155">[Conversion d’un type exporté](http://msdn.microsoft.com/en-us/1dfe55f4-07a2-4b61-aabf-a8cf65783a6b) </span><span class="sxs-lookup"><span data-stu-id="95d6a-155">[Exported Type Conversion](http://msdn.microsoft.com/en-us/1dfe55f4-07a2-4b61-aabf-a8cf65783a6b) </span></span>  
 [<span data-ttu-id="95d6a-156">Guide pratique pour convertir une chaîne en nombre</span><span class="sxs-lookup"><span data-stu-id="95d6a-156">How to: Convert a String to a Number</span></span>](../../../csharp/programming-guide/types/how-to-convert-a-string-to-a-number.md)

