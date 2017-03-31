---
title: "nameof (référence C# et Visual Basic) | Microsoft Docs"
ms.date: 2017-03-03
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- nameof_CSharpKeyword
- nameof
dev_langs:
- CSharp
ms.assetid: 33601bf3-cc2c-4496-846d-f9679bccf2a7
caps.latest.revision: 3
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
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: ce73de9177d6138b9acb00f3c7d3ace8e7a064f2
ms.lasthandoff: 03/13/2017

---
# <a name="nameof-c-and-visual-basic-reference"></a>nameof (référence C# et Visual Basic)

Permet d'obtenir le nom de chaîne simple (non qualifié) d'une variable, d'un type ou d'un membre.  

Pour le signalement des erreurs dans le code, le raccordement aux liens MVC (model-view-controller) et le déclenchement des événements de modification de propriété, entre autres, il est souvent utile de capturer le nom de chaîne d'une méthode.  L'utilisation de `nameof` vous aide à garantir la validité de votre code quand vous renommez des définitions.  Auparavant, vous deviez utiliser des littéraux de chaîne pour faire référence aux définitions, ce qui présentait un risque quand vous renommiez des éléments de code, car les outils ne vérifiaient pas ces littéraux de chaîne.  
  
 Une expression `nameof` se présente comme suit :  
  
```csharp  
if (x == null) throw new ArgumentNullException(nameof(x));  
WriteLine(nameof(person.Address.ZipCode)); // prints "ZipCode”  
  
```  
  
## <a name="key-use-cases"></a>Principaux cas d'usage  
 Ces exemples montrent les principaux cas d'usage de `nameof`.  
  
 Validation des paramètres :  
 ```csharp  
void f(string s) {  
    if (s == null) throw new ArgumentNullException(nameof(s));  
}  
  
```  
  
 Liens d'action MVC :  
 ```html  
<%= Html.ActionLink("Sign up",  
             @typeof(UserController),  
             @nameof(UserController.SignUp))  
%>  
  
```  
  
 INotifyPropertyChanged :  
 ```csharp  
int p {  
    get { return this.p; }  
    set { this.p = value; PropertyChanged(this, new PropertyChangedEventArgs(nameof(this.p)); } // nameof(p) works too  
}  
  
```  
  
 Propriété de dépendance XAML :  
 ```csharp  
public static DependencyProperty AgeProperty = DependencyProperty.Register(nameof(Age), typeof(int), typeof(C));  
  
```  
  
 Journalisation :  
 ```csharp  
void f(int i) {  
    Log(nameof(f), "method entry");  
}  
  
```  
  
 Attributs :  
 ```csharp  
[DebuggerDisplay("={" + nameof(GetString) + "()}")]  
class C {  
    string GetString() { }  
}  
```  
  
## <a name="examples"></a>Exemples  
 Exemples C# :  
  
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
nameof(f) -> “f”  
nameof(f<T>) -> syntax error  
nameof(f<>) -> syntax error  
nameof(Method2()) -> error “This expression does not have a name”  
  
```  
  
 Une grande partie des exemples ci-dessus s'appliquent aussi à Visual Basic.  Voici quelques exemples propres à Visual Basic :  
  
```vb  
NameOf(a!Foo) -> ' error  "This expression does not have a name"  
NameOf(dict("Foo")) -> ' error  "This expression does not have a name": default property access  
NameOf(dict.Item("Foo")) -> ' error  "This expression does not have a name"  
NameOf(arr(2)) -> ' error  "This expression does not have a name": array element index  
Dim x = Nothing   
NameOf(x.ToString(2)) -> ' error  "This expression does not have a name"  
Dim o = Nothing  
NameOf(o.Equals) -> ' result "Equals".  Warning: "Access of static member of instance; instance will not be evaluated"  
  
```  
  
## <a name="remarks"></a>Notes  
 L'argument de `nameof` doit être un nom simple, un nom qualifié, un accès au membre, un accès de base avec un membre spécifié ou cet accès avec un membre spécifié.  L'expression d'argument identifie une définition de code, mais n'est jamais évaluée.  
  
 L'argument doit être une expression d'un point de vue syntaxique. Il existe donc beaucoup d'éléments non autorisés qu'il n'est pas utile de répertorier ici.  En revanche, nous mentionnerons les éléments suivants qui génèrent des erreurs : les types prédéfinis (par exemple, `int` ou `void`), les types Nullable (`Point?`), les types tableau (`Customer[,]`), les types pointeur (`Buffer*`), les alias qualifiés (`A::B`), les types génériques indépendants (`Dictionary<,>`), les symboles de prétraitement (`DEBUG`) et les étiquettes (`loop:`).  
  
 Si vous avez besoin d'obtenir le nom qualifié complet, vous pouvez utiliser l'expression `typeof` avec `nameof`.  
  
 Les exemples montrent que vous pouvez utiliser un nom de type et accéder à un nom de méthode d'instance.  Il n'est pas nécessaire d'avoir une instance du type, comme c'est le cas dans les expressions évaluées.  Utiliser le nom de type peut être très pratique dans certains cas et, comme vous référencez seulement le nom et que vous n'utilisez pas de données d'instance, vous n'avez pas besoin de combiner une variable d'instance ou une expression.  
  
 Vous pouvez référencer les membres d'une classe dans les expressions d'attribut sur la classe.  
  
 Il n'existe aucun moyen pour obtenir des informations de signature comme « `Method1 (str, str)` ».  Pour cela, vous pouvez utiliser une expression, `Expression e = () => A.B.Method1("s1", "s2")`, puis extraire MemberInfo de l'arborescence de l'expression qui en résulte.  
  
## <a name="language-specifications"></a>Spécifications du langage  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
 Pour plus d’informations, consultez [Informations de référence sur le langage Visual Basic](../../../visual-basic/language-reference/index.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur C#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [typeof](../../../csharp/language-reference/keywords/typeof.md)   
 [Informations de référence sur le langage Visual Basic](../../../visual-basic/language-reference/index.md)   
 [Guide de programmation Visual Basic](../../../visual-basic/programming-guide/index.md)
