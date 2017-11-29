---
title: "nameof  (informations de référence sur C#)"
ms.date: 06/16/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- nameof_CSharpKeyword
- nameof
ms.assetid: 33601bf3-cc2c-4496-846d-f9679bccf2a7
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 95f50f45ec25c1eb3bacaa5051dc0407b11b7c34
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="nameof-c-reference"></a><span data-ttu-id="9f54c-102">nameof (informations de référence sur C#)</span><span class="sxs-lookup"><span data-stu-id="9f54c-102">nameof (C# Reference)</span></span>

<span data-ttu-id="9f54c-103">Permet d'obtenir le nom de chaîne simple (non qualifié) d'une variable, d'un type ou d'un membre.</span><span class="sxs-lookup"><span data-stu-id="9f54c-103">Used to obtain the simple (unqualified) string name of a variable, type, or member.</span></span>  

<span data-ttu-id="9f54c-104">Pour le signalement des erreurs dans le code, le raccordement aux liens MVC (model-view-controller) et le déclenchement des événements de modification de propriété, entre autres, il est souvent utile de capturer le nom de chaîne d'une méthode.</span><span class="sxs-lookup"><span data-stu-id="9f54c-104">When reporting errors in code, hooking up model-view-controller (MVC) links, firing property changed events, etc., you often want to capture the string name of a method.</span></span>  <span data-ttu-id="9f54c-105">L'utilisation de `nameof` vous aide à garantir la validité de votre code quand vous renommez des définitions.</span><span class="sxs-lookup"><span data-stu-id="9f54c-105">Using `nameof` helps keep your code valid when renaming definitions.</span></span>  <span data-ttu-id="9f54c-106">Auparavant, vous deviez utiliser des littéraux de chaîne pour faire référence aux définitions, ce qui présentait un risque quand vous renommiez des éléments de code, car les outils ne vérifiaient pas ces littéraux de chaîne.</span><span class="sxs-lookup"><span data-stu-id="9f54c-106">Before, you had to use string literals to refer to definitions, which is brittle when renaming code elements because tools do not know to check these string literals.</span></span>  
  
 <span data-ttu-id="9f54c-107">Une expression `nameof` se présente comme suit :</span><span class="sxs-lookup"><span data-stu-id="9f54c-107">A `nameof` expression has this form:</span></span>  
  
```csharp  
if (x == null) throw new ArgumentNullException(nameof(x));  
WriteLine(nameof(person.Address.ZipCode)); // prints "ZipCode"  
```  
  
## <a name="key-use-cases"></a><span data-ttu-id="9f54c-108">Principaux cas d'usage</span><span class="sxs-lookup"><span data-stu-id="9f54c-108">Key Use Cases</span></span>  
 <span data-ttu-id="9f54c-109">Ces exemples montrent les principaux cas d'usage de `nameof`.</span><span class="sxs-lookup"><span data-stu-id="9f54c-109">These examples show the key use cases for `nameof`.</span></span>  
  
 <span data-ttu-id="9f54c-110">Validation des paramètres :</span><span class="sxs-lookup"><span data-stu-id="9f54c-110">Validate parameters:</span></span>  
 ```csharp  
void f(string s) {  
    if (s == null) throw new ArgumentNullException(nameof(s));  
}  
```  
  
 <span data-ttu-id="9f54c-111">Liens d'action MVC :</span><span class="sxs-lookup"><span data-stu-id="9f54c-111">MVC Action links:</span></span>  
 ```html  
<%= Html.ActionLink("Sign up",  
             @typeof(UserController),  
             @nameof(UserController.SignUp))  
%>  
```  
  
 <span data-ttu-id="9f54c-112">INotifyPropertyChanged :</span><span class="sxs-lookup"><span data-stu-id="9f54c-112">INotifyPropertyChanged:</span></span>  
 ```csharp  
int p {  
    get { return this.p; }  
    set { this.p = value; PropertyChanged(this, new PropertyChangedEventArgs(nameof(this.p)); } // nameof(p) works too  
}  
```  
  
 <span data-ttu-id="9f54c-113">Propriété de dépendance XAML :</span><span class="sxs-lookup"><span data-stu-id="9f54c-113">XAML dependency property:</span></span>  
 ```csharp  
public static DependencyProperty AgeProperty = DependencyProperty.Register(nameof(Age), typeof(int), typeof(C));  
```  
  
 <span data-ttu-id="9f54c-114">Journalisation :</span><span class="sxs-lookup"><span data-stu-id="9f54c-114">Logging:</span></span>  
 ```csharp  
void f(int i) {  
    Log(nameof(f), "method entry");  
}  
```  
  
 <span data-ttu-id="9f54c-115">Attributs :</span><span class="sxs-lookup"><span data-stu-id="9f54c-115">Attributes:</span></span>  
 ```csharp  
[DebuggerDisplay("={" + nameof(GetString) + "()}")]  
class C {  
    string GetString() { }  
}  
```  
  
## <a name="examples"></a><span data-ttu-id="9f54c-116">Exemples</span><span class="sxs-lookup"><span data-stu-id="9f54c-116">Examples</span></span>  
 <span data-ttu-id="9f54c-117">Exemples C# :</span><span class="sxs-lookup"><span data-stu-id="9f54c-117">Some C# examples:</span></span>  
  
```csharp  
using Stuff = Some.Cool.Functionality  
class C {  
    static int Method1 (string x, int y) {}  
    static int Method1 (string x, string y) {}  
    int Method2 (int z) {}  
    string f<T>() => nameof(T);  
}  
  
var c = new C()  
  
nameof(C) -> "C"  
nameof(C.Method1) -> "Method1"   
nameof(C.Method2) -> "Method2"  
nameof(c.Method1) -> "Method1"   
nameof(c.Method2) -> "Method2"  
nameof(z) -> "z" // inside of Method2 ok, inside Method1 is a compiler error  
nameof(Stuff) = "Stuff"  
nameof(T) -> "T" // works inside of method but not in attributes on the method  
nameof(f) -> "f"  
nameof(f<T>) -> syntax error  
nameof(f<>) -> syntax error  
nameof(Method2()) -> error "This expression does not have a name"  
```  
  
## <a name="remarks"></a><span data-ttu-id="9f54c-118">Remarques</span><span class="sxs-lookup"><span data-stu-id="9f54c-118">Remarks</span></span>  
 <span data-ttu-id="9f54c-119">L'argument de `nameof` doit être un nom simple, un nom qualifié, un accès au membre, un accès de base avec un membre spécifié ou cet accès avec un membre spécifié.</span><span class="sxs-lookup"><span data-stu-id="9f54c-119">The argument to `nameof` must be a simple name, qualified name, member access, base access with a specified member, or this access with a specified member.</span></span>  <span data-ttu-id="9f54c-120">L'expression d'argument identifie une définition de code, mais n'est jamais évaluée.</span><span class="sxs-lookup"><span data-stu-id="9f54c-120">The argument expression identifies a code definition, but it is never evaluated.</span></span>  
  
 <span data-ttu-id="9f54c-121">L'argument doit être une expression d'un point de vue syntaxique. Il existe donc beaucoup d'éléments non autorisés qu'il n'est pas utile de répertorier ici.</span><span class="sxs-lookup"><span data-stu-id="9f54c-121">Because the argument needs to be an expression syntactically, there are many things disallowed that are not useful to list.</span></span>  <span data-ttu-id="9f54c-122">En revanche, nous mentionnerons les éléments suivants qui génèrent des erreurs : les types prédéfinis (par exemple, `int` ou `void`), les types Nullable (`Point?`), les types tableau (`Customer[,]`), les types pointeur (`Buffer*`), les alias qualifiés (`A::B`), les types génériques indépendants (`Dictionary<,>`), les symboles de prétraitement (`DEBUG`) et les étiquettes (`loop:`).</span><span class="sxs-lookup"><span data-stu-id="9f54c-122">The following are worth mentioning that produce errors: predefined types (for example, `int` or `void`), nullable types (`Point?`), array types (`Customer[,]`), pointer types (`Buffer*`), qualified alias (`A::B`), and unbound generic types (`Dictionary<,>`), preprocessing symbols (`DEBUG`), and labels (`loop:`).</span></span>  
  
 <span data-ttu-id="9f54c-123">Si vous avez besoin d'obtenir le nom qualifié complet, vous pouvez utiliser l'expression `typeof` avec `nameof`.</span><span class="sxs-lookup"><span data-stu-id="9f54c-123">If you need to get the fully-qualified name, you can use the `typeof` expression along with `nameof`.</span></span>  <span data-ttu-id="9f54c-124">Exemple :</span><span class="sxs-lookup"><span data-stu-id="9f54c-124">For example:</span></span>
```csharp  
class C {
    void f(int i) {  
        Log($"{typeof(C)}.{nameof(f)}", "method entry");  
    }
}
``` 

 <span data-ttu-id="9f54c-125">Malheureusement, `typeof` n’est pas une expression constante comme `nameof`, `typeof` ne peut donc pas être utilisé en conjonction avec `nameof` dans les mêmes emplacements que `nameof`.</span><span class="sxs-lookup"><span data-stu-id="9f54c-125">Unfortunately `typeof` is not a constant expression like `nameof`, so `typeof` cannot be used in conjunction with `nameof` in all the same places as `nameof`.</span></span>  <span data-ttu-id="9f54c-126">Par exemple, le code suivant entraîne une erreur de compilation CS0182 :</span><span class="sxs-lookup"><span data-stu-id="9f54c-126">For example, the following would cause a CS0182 compile error:</span></span>
 ```csharp  
[DebuggerDisplay("={" + typeof(C) + nameof(GetString) + "()}")]  
class C {  
    string GetString() { }  
}  
```    
 <span data-ttu-id="9f54c-127">Les exemples montrent que vous pouvez utiliser un nom de type et accéder à un nom de méthode d'instance.</span><span class="sxs-lookup"><span data-stu-id="9f54c-127">In the examples you see that you can use a type name and access an instance method name.</span></span>  <span data-ttu-id="9f54c-128">Il n'est pas nécessaire d'avoir une instance du type, comme c'est le cas dans les expressions évaluées.</span><span class="sxs-lookup"><span data-stu-id="9f54c-128">You do not need to have an instance of the type, as required in evaluated expressions.</span></span>  <span data-ttu-id="9f54c-129">Utiliser le nom de type peut être très pratique dans certains cas et, comme vous référencez seulement le nom et que vous n'utilisez pas de données d'instance, vous n'avez pas besoin de combiner une variable d'instance ou une expression.</span><span class="sxs-lookup"><span data-stu-id="9f54c-129">Using the type name can be very convenient in some situations, and since you are just referring to the name and not using instance data, you do not need to contrive an instance variable or expression.</span></span>  
  
 <span data-ttu-id="9f54c-130">Vous pouvez référencer les membres d'une classe dans les expressions d'attribut sur la classe.</span><span class="sxs-lookup"><span data-stu-id="9f54c-130">You can reference the members of a class in attribute expressions on the class.</span></span>  
  
 <span data-ttu-id="9f54c-131">Il n'existe aucun moyen pour obtenir des informations de signature comme « `Method1 (str, str)` ».</span><span class="sxs-lookup"><span data-stu-id="9f54c-131">There is no way to get a signatures information such as "`Method1 (str, str)`".</span></span>  <span data-ttu-id="9f54c-132">Pour cela, vous pouvez utiliser une expression, `Expression e = () => A.B.Method1("s1", "s2")`, puis extraire MemberInfo de l'arborescence de l'expression qui en résulte.</span><span class="sxs-lookup"><span data-stu-id="9f54c-132">One way to do that is to use an Expression, `Expression e = () => A.B.Method1("s1", "s2")`, and pull the MemberInfo from the resulting expression tree.</span></span>  
  
## <a name="language-specifications"></a><span data-ttu-id="9f54c-133">Spécifications du langage</span><span class="sxs-lookup"><span data-stu-id="9f54c-133">Language Specifications</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9f54c-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9f54c-134">See Also</span></span>  
 [<span data-ttu-id="9f54c-135">Référence C#</span><span class="sxs-lookup"><span data-stu-id="9f54c-135">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="9f54c-136">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="9f54c-136">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="9f54c-137">typeof</span><span class="sxs-lookup"><span data-stu-id="9f54c-137">typeof</span></span>](../../../csharp/language-reference/keywords/typeof.md)  
 
