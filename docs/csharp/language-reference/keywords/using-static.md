---
title: "using static, directive (référence C#)"
ms.date: 2017-03-10
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- using static directive [C#]
ms.assetid: 8b8f9e34-c75e-469b-ba85-6f2eb4090314
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
ms.openlocfilehash: b7d69d0262ba6f450e2cc0d5b30692bba181f9d9
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="using-static-directive-c-reference"></a><span data-ttu-id="81497-102">using static, directive (référence C#)</span><span class="sxs-lookup"><span data-stu-id="81497-102">using static Directive (C# Reference)</span></span>

<span data-ttu-id="81497-103">La directive `using static` désigne un type aux membres statiques duquel vous pouvez accéder sans spécifier un nom de type.</span><span class="sxs-lookup"><span data-stu-id="81497-103">The `using static` directive designates a type whose static members you can access without specifying a type name.</span></span> <span data-ttu-id="81497-104">Sa syntaxe est la suivante :</span><span class="sxs-lookup"><span data-stu-id="81497-104">Its syntax is:</span></span>

```csharp
using static <fully-qualified-type-name>
```

<span data-ttu-id="81497-105">où *fully-qualified-type-name* est le nom du type dont les membres statiques peuvent être référencés sans spécifier de nom de type.</span><span class="sxs-lookup"><span data-stu-id="81497-105">where *fully-qualified-type-name* is the name of the type whose static members can be referenced without specifying a type name.</span></span> <span data-ttu-id="81497-106">Si vous ne fournissez pas de nom de type complet (le nom de l’espace de noms complet avec le nom du type), C# génère l’erreur du compilateur CS0246 : "Le nom du type ou de l’espace de noms '<nom_type>' est introuvable".</span><span class="sxs-lookup"><span data-stu-id="81497-106">If you do not provide a fully qualified type name (the full namespace name along with the type name), C# generates compiler error CS0246: "The type or namespace name '<type-name>' could not be found."</span></span>

<span data-ttu-id="81497-107">La directive `using static` s’applique à tout type ayant des membres statiques, même s’il a également des membres d’instance.</span><span class="sxs-lookup"><span data-stu-id="81497-107">The `using static` directive applies to any type that has static members, even if it also has instance members.</span></span> <span data-ttu-id="81497-108">Toutefois, les membres d’instance ne peuvent être appelés que par l’instance du type.</span><span class="sxs-lookup"><span data-stu-id="81497-108">However, instance members can only be invoked through the type instance.</span></span>

<span data-ttu-id="81497-109">La directive `using static` a été introduite avec C# 6.</span><span class="sxs-lookup"><span data-stu-id="81497-109">The `using static` directive was introduced in C# 6.</span></span>

## <a name="remarks"></a><span data-ttu-id="81497-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="81497-110">Remarks</span></span>
 
<span data-ttu-id="81497-111">En général, quand vous appelez un membre statique, vous indiquez le nom du type, ainsi que le nom du membre.</span><span class="sxs-lookup"><span data-stu-id="81497-111">Ordinarily, when you call a static member, you provide the type name along with the member name.</span></span> <span data-ttu-id="81497-112">Entrer plusieurs fois le même nom de type pour appeler des membres du type peut produire du code détaillé et peu clair.</span><span class="sxs-lookup"><span data-stu-id="81497-112">Repeatedly entering the same type name to invoke members of the type can result in verbose, obscure code.</span></span> <span data-ttu-id="81497-113">Par exemple, la définition suivante d’une classe `Circle` référence un certain nombre de membres de la classe @System.Math.</span><span class="sxs-lookup"><span data-stu-id="81497-113">For example, the following definition of a `Circle` class references a number of members of the @System.Math class.</span></span>
  
<span data-ttu-id="81497-114">[!code-cs[using-static#1](../../../../samples/snippets/csharp/language-reference/keywords/using/using-static1.cs#1)]</span><span class="sxs-lookup"><span data-stu-id="81497-114">[!code-cs[using-static#1](../../../../samples/snippets/csharp/language-reference/keywords/using/using-static1.cs#1)]</span></span>

<span data-ttu-id="81497-115">En éliminant la nécessité de référencer explicitement la classe @System.Math chaque fois qu’un membre est référencé, la directive `using static` génère du code beaucoup plus clair :</span><span class="sxs-lookup"><span data-stu-id="81497-115">By eliminating the need to explicitly reference the @System.Math class each time a member is referenced, the `using static` directive produces much cleaner code:</span></span>

<span data-ttu-id="81497-116">[!code-cs[using-static#2](../../../../samples/snippets/csharp/language-reference/keywords/using/using-static2.cs#1)]</span><span class="sxs-lookup"><span data-stu-id="81497-116">[!code-cs[using-static#2](../../../../samples/snippets/csharp/language-reference/keywords/using/using-static2.cs#1)]</span></span>

<span data-ttu-id="81497-117">`using static` importe uniquement les membres statiques accessibles et les types imbriqués déclarés dans le type spécifié.</span><span class="sxs-lookup"><span data-stu-id="81497-117">`using static` imports only accessible static members and nested types declared in the specified type.</span></span>  <span data-ttu-id="81497-118">Les membres hérités ne sont pas importés.</span><span class="sxs-lookup"><span data-stu-id="81497-118">Inherited members are not imported.</span></span>  <span data-ttu-id="81497-119">Vous pouvez importer à partir de n'importe quel type nommé avec une directive static, notamment des modules Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="81497-119">You can import from any named type with a using static directive, including Visual Basic modules.</span></span>  <span data-ttu-id="81497-120">Si des fonctions de niveau supérieur F# apparaissent dans les métadonnées comme membres statiques d’un type nommé dont le nom est un identificateur C# valide, les fonctions F# peuvent être importées.</span><span class="sxs-lookup"><span data-stu-id="81497-120">If F# top-level functions appear in metadata as static members of a named type whose name is a valid C# identifier, then the F# functions can be imported.</span></span>  
  
 <span data-ttu-id="81497-121">`using static` rend les méthodes d'extension déclarées dans le type spécifié disponibles pour la recherche de méthode d'extension.</span><span class="sxs-lookup"><span data-stu-id="81497-121">`using static` makes extension methods declared in the specified type available for extension method lookup.</span></span>  <span data-ttu-id="81497-122">Toutefois, les noms des méthodes d’extension ne sont pas importés dans la portée pour la référence non qualifiée dans le code.</span><span class="sxs-lookup"><span data-stu-id="81497-122">However, the names of the extension methods are not imported into scope for unqualified reference in code.</span></span>  
  
 <span data-ttu-id="81497-123">Les méthodes portant le même nom et qui sont importées à partir de différents types par différentes directives `using static` dans la même unité de compilation ou le même espace de noms forment un groupe de méthodes.</span><span class="sxs-lookup"><span data-stu-id="81497-123">Methods with the same name imported from different types by different `using static` directives in the same compilation unit or namespace form a method group.</span></span>  <span data-ttu-id="81497-124">La résolution de surcharge au sein de ces groupes de méthodes suit des règles C# normales.</span><span class="sxs-lookup"><span data-stu-id="81497-124">Overload resolution within these method groups follows normal C# rules.</span></span>  
  
## <a name="example"></a><span data-ttu-id="81497-125">Exemple</span><span class="sxs-lookup"><span data-stu-id="81497-125">Example</span></span>

<span data-ttu-id="81497-126">L’exemple suivant utilise la directive `using static` pour que les membres statiques des classes @System.Console, @System.Math et @System.String soient disponibles sans que vous ayez à spécifier leur nom de type.</span><span class="sxs-lookup"><span data-stu-id="81497-126">The following example uses the `using static` directive to make the static members of the @System.Console, @System.Math, and @System.String classes available without having to specify their type name.</span></span>

<span data-ttu-id="81497-127">[!code-cs[using-static#3](../../../../samples/snippets/csharp/language-reference/keywords/using/using-static3.cs)]</span><span class="sxs-lookup"><span data-stu-id="81497-127">[!code-cs[using-static#3](../../../../samples/snippets/csharp/language-reference/keywords/using/using-static3.cs)]</span></span>

<span data-ttu-id="81497-128">Dans cet exemple, la directive `using static` aurait également pu être appliquée au type @System.Double.</span><span class="sxs-lookup"><span data-stu-id="81497-128">In the example, the `using static` directive could also have been applied to the @System.Double type.</span></span> <span data-ttu-id="81497-129">Cela aurait permis d’appeler la méthode @System.Double.TryParse(System.String,System.Double@) sans spécifier un nom de type.</span><span class="sxs-lookup"><span data-stu-id="81497-129">This would have made it possible to call the @System.Double.TryParse(System.String,System.Double@) method without specifying a type name.</span></span> <span data-ttu-id="81497-130">Toutefois, cela crée un code moins lisible, car il est nécessaire de vérifier les instructions `using static` pour déterminer quelle méthode `TryParse` du type numérique est appelée.</span><span class="sxs-lookup"><span data-stu-id="81497-130">However, this creates less readable code, since it becomes necessary to check the `using static` statements to determine which numeric type's `TryParse` method is called.</span></span>

## <a name="see-also"></a><span data-ttu-id="81497-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="81497-131">See also</span></span>

<span data-ttu-id="81497-132">[using, directive](using-directive.md) </span><span class="sxs-lookup"><span data-stu-id="81497-132">[using directive](using-directive.md) </span></span>  
<span data-ttu-id="81497-133">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="81497-133">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
<span data-ttu-id="81497-134">[Mots clés C#](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="81497-134">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
<span data-ttu-id="81497-135">[Utilisation d’espaces de noms](../../../csharp/programming-guide/namespaces/using-namespaces.md) </span><span class="sxs-lookup"><span data-stu-id="81497-135">[Using Namespaces](../../../csharp/programming-guide/namespaces/using-namespaces.md) </span></span>  
<span data-ttu-id="81497-136">[Mots clés d’espaces de noms](../../../csharp/language-reference/keywords/namespace-keywords.md) </span><span class="sxs-lookup"><span data-stu-id="81497-136">[Namespace Keywords](../../../csharp/language-reference/keywords/namespace-keywords.md) </span></span>  
[<span data-ttu-id="81497-137">Espaces de noms</span><span class="sxs-lookup"><span data-stu-id="81497-137">Namespaces</span></span>](../../../csharp/programming-guide/namespaces/index.md)   

