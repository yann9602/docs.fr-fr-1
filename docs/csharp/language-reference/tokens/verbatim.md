---
title: "@ (référence C#)"
ms.date: 2017-02-09
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '@_CSharpKeyword'
- '@'
dev_langs:
- CSharp
helpviewer_keywords:
- '@ special character [C#]'
- '@ language element [C#]'
ms.assetid: 89bc7e53-85f5-478a-866d-1cca003c4e8c
author: rpetrusha
ms.author: ronpet
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
ms.openlocfilehash: 08e3da6aaeee037d7272ea8cddc4382a436b683b
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="-c-reference"></a><span data-ttu-id="5d037-102">@ (référence C#)</span><span class="sxs-lookup"><span data-stu-id="5d037-102">@ (C# Reference)</span></span>

<span data-ttu-id="5d037-103">Le caractère spécial `@` sert d’identificateur de chaîne textuelle.</span><span class="sxs-lookup"><span data-stu-id="5d037-103">The `@` special character serves as a verbatim identifier.</span></span> <span data-ttu-id="5d037-104">Il peut être utilisé des façons suivantes :</span><span class="sxs-lookup"><span data-stu-id="5d037-104">It can be used in the following ways:</span></span>

1. <span data-ttu-id="5d037-105">Pour activer les mots clés C# à utiliser comme identificateurs.</span><span class="sxs-lookup"><span data-stu-id="5d037-105">To enable C# keywords to be used as identifiers.</span></span> <span data-ttu-id="5d037-106">Le caractère `@` est le préfixe d’un élément de code que le compilateur doit interpréter comme un identificateur plutôt qu’un mot clé C#.</span><span class="sxs-lookup"><span data-stu-id="5d037-106">The `@` character prefixes a code element that the compiler is to interpret as an identifier rather than a C# keyword.</span></span> <span data-ttu-id="5d037-107">L’exemple suivant utilise le caractère `@` pour définir un identificateur nommé `for` qu’il utilise dans une boucle `for`.</span><span class="sxs-lookup"><span data-stu-id="5d037-107">The following example uses the `@` character to define an identifier named `for` that it uses in a `for` loop.</span></span>

   <span data-ttu-id="5d037-108">[!code-cs[verbatim1](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#1)]</span><span class="sxs-lookup"><span data-stu-id="5d037-108">[!code-cs[verbatim1](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#1)]</span></span>

1. <span data-ttu-id="5d037-109">Pour indiquer qu’un littéral de chaîne doit être interprété textuellement.</span><span class="sxs-lookup"><span data-stu-id="5d037-109">To indicate that a string literal is to be interpreted verbatim.</span></span> <span data-ttu-id="5d037-110">Le caractère `@` dans cette instance définit un *littéral de chaîne textuelle*.</span><span class="sxs-lookup"><span data-stu-id="5d037-110">The `@` character in this instance defines a *verbatim string literal*.</span></span> <span data-ttu-id="5d037-111">Les séquences d’échappement simples (comme `"\\"` pour une barre oblique inverse), hexadécimales (comme `"\x0041"` pour un A majuscule) et Unicode (comme `"\u0041"` pour un A majuscule), sont interprétées littéralement.</span><span class="sxs-lookup"><span data-stu-id="5d037-111">Simple escape sequences (such as `"\\"` for a backslash), hexadecimal escape sequences (such as `"\x0041"` for an uppercase A, and Unicode escape sequences, such as `"\u0041"` for an uppercase A, are interpreted literally.</span></span> <span data-ttu-id="5d037-112">Seule une séquence d’échappement de guillemet (`""`) n’est pas interprétée littéralement ; elle génère un guillemet simple.</span><span class="sxs-lookup"><span data-stu-id="5d037-112">Only a quote escape sequence (`""`) is not interpreted literally; it produces a single quotation mark.</span></span> <span data-ttu-id="5d037-113">L’exemple suivant définit deux chemins de fichier identiques, un à l’aide d’un littéral de chaîne standard et l’autre à l’aide d’un littéral de chaîne textuelle.</span><span class="sxs-lookup"><span data-stu-id="5d037-113">The following example defines two identical file paths, one by using a regular string literal and the other by using a verbatim string literal.</span></span> <span data-ttu-id="5d037-114">Il s’agit là de l’une des utilisations les plus courantes de littéraux de chaîne textuelle.</span><span class="sxs-lookup"><span data-stu-id="5d037-114">This is one of the more common uses of verbatim string literals.</span></span>

   <span data-ttu-id="5d037-115">[!code-cs[verbatim2](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#2)]</span><span class="sxs-lookup"><span data-stu-id="5d037-115">[!code-cs[verbatim2](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#2)]</span></span>

   <span data-ttu-id="5d037-116">L’exemple suivant illustre l’effet de la définition d’un littéral de chaîne standard et d’un littéral de chaîne textuelle qui contiennent des séquences de caractères identiques.</span><span class="sxs-lookup"><span data-stu-id="5d037-116">The following example illustrates the effect of defining a regular string literal and a verbatim string literal that contain identical character sequences.</span></span>

   <span data-ttu-id="5d037-117">[!code-cs[verbatim3](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#3)]</span><span class="sxs-lookup"><span data-stu-id="5d037-117">[!code-cs[verbatim3](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#3)]</span></span>

1. <span data-ttu-id="5d037-118">Pour permettre au compilateur de faire la distinction entre les attributs en cas de conflit de noms.</span><span class="sxs-lookup"><span data-stu-id="5d037-118">To enable the compiler to distinguish between attributes in cases of a naming conflict.</span></span> <span data-ttu-id="5d037-119">Un attribut est un type qui dérive de @System.Attribute.</span><span class="sxs-lookup"><span data-stu-id="5d037-119">An attribute is a type that derives from @System.Attribute.</span></span> <span data-ttu-id="5d037-120">Son nom de type comprend généralement le suffixe **Attribute**, bien que le compilateur n’applique pas cette convention.</span><span class="sxs-lookup"><span data-stu-id="5d037-120">Its type name typically includes the suffix **Attribute**, although the compiler does not enforce this convention.</span></span> <span data-ttu-id="5d037-121">L’attribut peut ensuite être référencé dans le code par son nom de type complet (par exemple, `[InfoAttribute]`) ou son nom abrégé (par exemple, `[Info]`).</span><span class="sxs-lookup"><span data-stu-id="5d037-121">The attribute can then be referenced in code either by its full type name (for example, `[InfoAttribute]` or its shortened name (for example, `[Info]`).</span></span> <span data-ttu-id="5d037-122">Toutefois, un conflit survient si deux noms de type d’attribut abrégés sont identiques et que l’un d’eux inclut le suffixe **Attribute**, mais pas l’autre.</span><span class="sxs-lookup"><span data-stu-id="5d037-122">However, a naming conflict occurs if two shortened attribute type names are identical, and one type name includes the **Attribute** suffix but the other does not.</span></span> <span data-ttu-id="5d037-123">Par exemple, la compilation du code suivant échoue, car le compilateur ne peut pas déterminer si l’attribut `Info` ou `InfoAttribute` est appliqué à la méthode `Main`.</span><span class="sxs-lookup"><span data-stu-id="5d037-123">For example, the following code fails to compile because the compiler cannot determine whether the `Info` or `InfoAttribute` attribute is applied to the `Main` method.</span></span>

   ```csharp
   using System;

   [AttributeUsage(AttributeTargets.Class)]
   public class Info : Attribute
   {
      private string information;
      
      public Info(string info)
      {
          information = info;
      }
   }

   [AttributeUsage(AttributeTargets.Method)]
   public class InfoAttribute : Attribute
   {
      private string information;
      
      public InfoAttribute(string info)
      {
          information = info;
      }
   }

   [Info("A simple executable.")]
   public class Example
   {
      [InfoAttribute("The entry point.")]
      public static void Main()
      {
      }
   }
   ```  

   <span data-ttu-id="5d037-124">Si l’identificateur de chaîne textuelle est utilisé pour identifier l’attribut `Info`, l’exemple est correctement compilé.</span><span class="sxs-lookup"><span data-stu-id="5d037-124">If the verbatim identifier is used to identify the `Info` attribute, the example compiles successfully.</span></span>

   <span data-ttu-id="5d037-125">[!code-cs[verbatim4](../../../../samples/snippets/csharp/language-reference/keywords/verbatim4.cs#1)]</span><span class="sxs-lookup"><span data-stu-id="5d037-125">[!code-cs[verbatim4](../../../../samples/snippets/csharp/language-reference/keywords/verbatim4.cs#1)]</span></span>

## <a name="see-also"></a><span data-ttu-id="5d037-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5d037-126">See Also</span></span>  
 <span data-ttu-id="5d037-127">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="5d037-127">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="5d037-128">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="5d037-128">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="5d037-129">Caractères spéciaux C#</span><span class="sxs-lookup"><span data-stu-id="5d037-129">C# Special Characters</span></span>](../../../csharp/language-reference/tokens/index.md)

