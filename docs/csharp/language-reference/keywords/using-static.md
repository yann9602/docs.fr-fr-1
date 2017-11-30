---
title: "using static, directive (référence C#)"
ms.date: 03/10/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: using static directive [C#]
ms.assetid: 8b8f9e34-c75e-469b-ba85-6f2eb4090314
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5838bede475cf2ad1b72518770241e86206a06bb
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2017
---
# <a name="using-static-directive-c-reference"></a><span data-ttu-id="3e332-102">using static, directive (référence C#)</span><span class="sxs-lookup"><span data-stu-id="3e332-102">using static Directive (C# Reference)</span></span>

<span data-ttu-id="3e332-103">La directive `using static` désigne un type aux membres statiques duquel vous pouvez accéder sans spécifier un nom de type.</span><span class="sxs-lookup"><span data-stu-id="3e332-103">The `using static` directive designates a type whose static members you can access without specifying a type name.</span></span> <span data-ttu-id="3e332-104">Sa syntaxe est la suivante :</span><span class="sxs-lookup"><span data-stu-id="3e332-104">Its syntax is:</span></span>

```csharp
using static <fully-qualified-type-name>
```

<span data-ttu-id="3e332-105">où *fully-qualified-type-name* est le nom du type dont les membres statiques peuvent être référencés sans spécifier de nom de type.</span><span class="sxs-lookup"><span data-stu-id="3e332-105">where *fully-qualified-type-name* is the name of the type whose static members can be referenced without specifying a type name.</span></span> <span data-ttu-id="3e332-106">Si vous ne fournissez pas de nom de type complet (le nom de l’espace de noms complet avec le nom du type), C# génère l’erreur du compilateur CS0246 : "Le nom du type ou de l’espace de noms '<nom_type>' est introuvable".</span><span class="sxs-lookup"><span data-stu-id="3e332-106">If you do not provide a fully qualified type name (the full namespace name along with the type name), C# generates compiler error CS0246: "The type or namespace name '<type-name>' could not be found."</span></span>

<span data-ttu-id="3e332-107">La directive `using static` s’applique à tout type ayant des membres statiques, même s’il a également des membres d’instance.</span><span class="sxs-lookup"><span data-stu-id="3e332-107">The `using static` directive applies to any type that has static members, even if it also has instance members.</span></span> <span data-ttu-id="3e332-108">Toutefois, les membres d’instance ne peuvent être appelés que par l’instance du type.</span><span class="sxs-lookup"><span data-stu-id="3e332-108">However, instance members can only be invoked through the type instance.</span></span>

<span data-ttu-id="3e332-109">La directive `using static` a été introduite avec C# 6.</span><span class="sxs-lookup"><span data-stu-id="3e332-109">The `using static` directive was introduced in C# 6.</span></span>

## <a name="remarks"></a><span data-ttu-id="3e332-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="3e332-110">Remarks</span></span>
 
<span data-ttu-id="3e332-111">En général, quand vous appelez un membre statique, vous indiquez le nom du type, ainsi que le nom du membre.</span><span class="sxs-lookup"><span data-stu-id="3e332-111">Ordinarily, when you call a static member, you provide the type name along with the member name.</span></span> <span data-ttu-id="3e332-112">Entrer plusieurs fois le même nom de type pour appeler des membres du type peut produire du code détaillé et peu clair.</span><span class="sxs-lookup"><span data-stu-id="3e332-112">Repeatedly entering the same type name to invoke members of the type can result in verbose, obscure code.</span></span> <span data-ttu-id="3e332-113">Par exemple, la définition suivante d’une classe `Circle` référence un certain nombre de membres de la classe <xref:System.Math>.</span><span class="sxs-lookup"><span data-stu-id="3e332-113">For example, the following definition of a `Circle` class references a number of members of the <xref:System.Math> class.</span></span>
  
[!code-csharp[using-static#1](../../../../samples/snippets/csharp/language-reference/keywords/using/using-static1.cs#1)]

<span data-ttu-id="3e332-114">En éliminant la nécessité de référencer explicitement la classe <xref:System.Math> chaque fois qu’un membre est référencé, la directive `using static` génère du code beaucoup plus clair :</span><span class="sxs-lookup"><span data-stu-id="3e332-114">By eliminating the need to explicitly reference the <xref:System.Math> class each time a member is referenced, the `using static` directive produces much cleaner code:</span></span>

[!code-csharp[using-static#2](../../../../samples/snippets/csharp/language-reference/keywords/using/using-static2.cs#1)]

<span data-ttu-id="3e332-115">`using static` importe uniquement les membres statiques accessibles et les types imbriqués déclarés dans le type spécifié.</span><span class="sxs-lookup"><span data-stu-id="3e332-115">`using static` imports only accessible static members and nested types declared in the specified type.</span></span>  <span data-ttu-id="3e332-116">Les membres hérités ne sont pas importés.</span><span class="sxs-lookup"><span data-stu-id="3e332-116">Inherited members are not imported.</span></span>  <span data-ttu-id="3e332-117">Vous pouvez importer à partir de n'importe quel type nommé avec une directive static, notamment des modules Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="3e332-117">You can import from any named type with a using static directive, including Visual Basic modules.</span></span>  <span data-ttu-id="3e332-118">Si des fonctions de niveau supérieur F# apparaissent dans les métadonnées comme membres statiques d’un type nommé dont le nom est un identificateur C# valide, les fonctions F# peuvent être importées.</span><span class="sxs-lookup"><span data-stu-id="3e332-118">If F# top-level functions appear in metadata as static members of a named type whose name is a valid C# identifier, then the F# functions can be imported.</span></span>  
  
 <span data-ttu-id="3e332-119">`using static` rend les méthodes d'extension déclarées dans le type spécifié disponibles pour la recherche de méthode d'extension.</span><span class="sxs-lookup"><span data-stu-id="3e332-119">`using static` makes extension methods declared in the specified type available for extension method lookup.</span></span>  <span data-ttu-id="3e332-120">Toutefois, les noms des méthodes d’extension ne sont pas importés dans la portée pour la référence non qualifiée dans le code.</span><span class="sxs-lookup"><span data-stu-id="3e332-120">However, the names of the extension methods are not imported into scope for unqualified reference in code.</span></span>  
  
 <span data-ttu-id="3e332-121">Les méthodes portant le même nom et qui sont importées à partir de différents types par différentes directives `using static` dans la même unité de compilation ou le même espace de noms forment un groupe de méthodes.</span><span class="sxs-lookup"><span data-stu-id="3e332-121">Methods with the same name imported from different types by different `using static` directives in the same compilation unit or namespace form a method group.</span></span>  <span data-ttu-id="3e332-122">La résolution de surcharge au sein de ces groupes de méthodes suit des règles C# normales.</span><span class="sxs-lookup"><span data-stu-id="3e332-122">Overload resolution within these method groups follows normal C# rules.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3e332-123">Exemple</span><span class="sxs-lookup"><span data-stu-id="3e332-123">Example</span></span>

<span data-ttu-id="3e332-124">L’exemple suivant utilise la directive `using static` pour que les membres statiques des classes <xref:System.Console>, <xref:System.Math> et <xref:System.String> soient disponibles sans que vous ayez à spécifier leur nom de type.</span><span class="sxs-lookup"><span data-stu-id="3e332-124">The following example uses the `using static` directive to make the static members of the <xref:System.Console>, <xref:System.Math>, and <xref:System.String> classes available without having to specify their type name.</span></span>

[!code-csharp[using-static#3](../../../../samples/snippets/csharp/language-reference/keywords/using/using-static3.cs)]

<span data-ttu-id="3e332-125">Dans cet exemple, la directive `using static` aurait également pu être appliquée au type <xref:System.Double>.</span><span class="sxs-lookup"><span data-stu-id="3e332-125">In the example, the `using static` directive could also have been applied to the <xref:System.Double> type.</span></span> <span data-ttu-id="3e332-126">Cela aurait il possible d’appeler le <xref:System.Double.TryParse(System.String,System.Double@)> méthode sans spécifier un nom de type.</span><span class="sxs-lookup"><span data-stu-id="3e332-126">This would have made it possible to call the <xref:System.Double.TryParse(System.String,System.Double@)> method without specifying a type name.</span></span> <span data-ttu-id="3e332-127">Toutefois, cela crée un code moins lisible, car il est nécessaire de vérifier les instructions `using static` pour déterminer quelle méthode `TryParse` du type numérique est appelée.</span><span class="sxs-lookup"><span data-stu-id="3e332-127">However, this creates less readable code, since it becomes necessary to check the `using static` statements to determine which numeric type's `TryParse` method is called.</span></span>

## <a name="see-also"></a><span data-ttu-id="3e332-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3e332-128">See also</span></span>

<span data-ttu-id="3e332-129">[using, directive](using-directive.md) </span><span class="sxs-lookup"><span data-stu-id="3e332-129">[using directive](using-directive.md) </span></span>  
<span data-ttu-id="3e332-130">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="3e332-130">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
<span data-ttu-id="3e332-131">[Mots clés C#](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="3e332-131">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
<span data-ttu-id="3e332-132">[Utilisation d’espaces de noms](../../../csharp/programming-guide/namespaces/using-namespaces.md) </span><span class="sxs-lookup"><span data-stu-id="3e332-132">[Using Namespaces](../../../csharp/programming-guide/namespaces/using-namespaces.md) </span></span>  
<span data-ttu-id="3e332-133">[Mots clés d’espaces de noms](../../../csharp/language-reference/keywords/namespace-keywords.md) </span><span class="sxs-lookup"><span data-stu-id="3e332-133">[Namespace Keywords](../../../csharp/language-reference/keywords/namespace-keywords.md) </span></span>  
[<span data-ttu-id="3e332-134">Espaces de noms</span><span class="sxs-lookup"><span data-stu-id="3e332-134">Namespaces</span></span>](../../../csharp/programming-guide/namespaces/index.md)   
