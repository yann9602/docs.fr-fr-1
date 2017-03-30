---
title: Types (Guide de programmation C#) | Microsoft Docs
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- value types [C#]
- reference types [C#]
- types [C#]
- C# language, data types
- common type system [C#]
- data types [C#]
- C# language, types
- strong typing [C#]
ms.assetid: f782d7cc-035e-4500-b1b1-36a9881130ad
caps.latest.revision: 53
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 5fbd7c5e08d862f079e0596cbe394afd0538bccc
ms.lasthandoff: 03/13/2017

---
# <a name="types-c-programming-guide"></a>Types (Guide de programmation C#)
## <a name="types-variables-and-values"></a>Types, variables et valeurs  
 C# est un langage fortement typé. Chaque variable et constante a un type, tout comme chaque expression qui prend une valeur. Chaque signature de méthode spécifie un type pour chaque paramètre d’entrée et pour la valeur de retour. La bibliothèque de classes .NET Framework définit un ensemble de types numériques intégrés, ainsi que des types plus complexes qui représentent un large éventail de constructions logiques, telles que le système de fichiers, les connexions réseau, les collections et les tableaux d’objets, et les dates. Un programme C# type utilise les types à partir de la bibliothèque de classes, ainsi que des types définis par l’utilisateur qui modélisent les concepts qui sont spécifiques au domaine du problème du programme.  
  
 Les informations stockées dans un type peuvent être les suivantes :  
  
-   L’espace de stockage qu’une variable du type requiert.  
  
-   Les valeurs minimales et maximales qu’il peut représenter.  
  
-   Les membres (méthodes, champs, événements, etc.) qu’il contient.  
  
-   Le type de base dont il hérite.  
  
-   L’emplacement où la mémoire pour les variables sera allouée au moment de l’exécution.  
  
-   Les types d’opérations qui sont autorisées.  
  
 Le compilateur utilise les informations de type pour s’assurer que toutes les opérations qui sont effectuées dans votre code sont *de type sécurisé*. Par exemple, si vous déclarez une variable de type [int](../../../csharp/language-reference/keywords/int.md), le compilateur vous permet d’utiliser la variable dans des opérations d’addition et de soustraction. Si vous essayez d’effectuer ces mêmes opérations avec une variable de type [bool](../../../csharp/language-reference/keywords/bool.md), le compilateur génère une erreur, comme illustré dans l’exemple suivant :  
  
 [!code-cs[csProgGuideTypes#42](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/index_1.cs)]  
  
> [!NOTE]
>  Développeurs C et C++ : notez que dans C#, [bool](../../../csharp/language-reference/keywords/bool.md) n’est pas convertible en [int](../../../csharp/language-reference/keywords/int.md).  
  
 Le compilateur incorpore les informations de type dans le fichier exécutable en tant que métadonnées. Le common language runtime (CLR) utilise ces métadonnées au moment de l’exécution pour garantir que le type est sécurisé lorsqu’il alloue et libère de la mémoire.  
  
### <a name="specifying-types-in-variable-declarations"></a>Spécification de types dans les déclarations de variable  
 Lorsque vous déclarez une variable ou une constante dans un programme, vous devez spécifier son type ou utiliser le mot clé [var](../../../csharp/language-reference/keywords/var.md) pour permettre au compilateur de déduire le type. L’exemple suivant montre des déclarations de variable qui utilisent des types numériques intégrés et des types complexes définis par l’utilisateur :  
  
 [!code-cs[csProgGuideTypes#36](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/index_2.cs)]  
  
 Les types de paramètres de méthode et de valeurs de retour sont spécifiés dans la signature de méthode. La signature suivante présente une méthode qui requiert [int](../../../csharp/language-reference/keywords/int.md) comme argument d’entrée et retourne une chaîne :  
  
 [!code-cs[csProgGuideTypes#35](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/index_3.cs)]  
  
 Après qu’une variable est déclarée, elle ne peut pas être déclarée de nouveau avec un nouveau type et elle ne peut pas être définie sur une valeur qui n’est pas compatible avec son type déclaré. Par exemple, vous ne pouvez pas déclarer [int](../../../csharp/language-reference/keywords/int.md) et lui attribuer une valeur booléenne [true](../../../csharp/language-reference/keywords/true-literal.md). Toutefois, les valeurs peuvent être converties en d’autres types, par exemple lorsqu’elles sont affectées à des nouvelles variables ou transférées comme arguments de méthode. Une *conversion de type* qui ne cause pas de perte de données est effectuée automatiquement par le compilateur. Une conversion susceptible de causer la perte de données exige une variable *cast* dans le code source.  
  
 Pour plus d'informations, consultez [Cast et conversions de types](../../../csharp/programming-guide/types/casting-and-type-conversions.md).  
  
## <a name="built-in-types"></a>Types intégrés  
 C# fournit un jeu standard de types numériques intégrés pour représenter les nombres entiers, les valeurs à virgule flottante, les expressions booléennes, les caractères de texte, les valeurs décimales et d’autres types de données. Il existe également des types `string` et `object` intégrés. Ceux-ci sont disponibles dans n’importe quel programme C#. Pour plus d’informations sur les types intégrés, consultez [Tableaux de référence des types](../../../csharp/language-reference/keywords/reference-tables-for-types.md).  
  
## <a name="custom-types"></a>Types personnalisés  
 Vous utilisez les constructions [struct](../../../csharp/language-reference/keywords/struct.md), [classe](../../../csharp/language-reference/keywords/class.md), [interface](../../../csharp/language-reference/keywords/interface.md) et [enum](../../../csharp/language-reference/keywords/enum.md) pour créer vos propres types personnalisés. La bibliothèque de classes .NET Framework est une collection de types personnalisés fournie par Microsoft que vous pouvez utiliser dans vos propres applications. Par défaut, les types les plus fréquemment utilisés dans la bibliothèque de classes sont disponibles dans n’importe quel programme C#. Les autres types deviennent disponibles uniquement lorsque vous ajoutez explicitement une référence de projet à l’assembly dans lequel ils sont définis. Une fois que le compilateur a une référence à l’assembly, vous pouvez déclarer des variables (et des constantes) des types déclarés dans cet assembly dans le code source. Pour plus d’informations, consultez [Bibliothèque de classes .NET Framework](http://go.microsoft.com/fwlink/?LinkID=217856).  
  
## <a name="the-common-type-system"></a>Système de type commun  
 Il est important de comprendre deux points fondamentaux à propos du système de type dans le [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] :  
  
-   Il prend en charge le principe d’héritage. Les types peuvent dériver d’autres types appelés *types de base*. Le type dérivé hérite (avec certaines restrictions) des méthodes, des propriétés et des autres membres du type de base. Le type de base peut à son tour dériver d’un autre type, auquel cas le type dérivé hérite des membres des deux types de base dans sa hiérarchie d’héritage. Tous les types, notamment les types numériques intégrés comme <xref:System.Int32?displayProperty=fullName> (C# keyword: [int](../../../csharp/language-reference/keywords/int.md)), dérivent en fin de compte d’un seul type de base : <xref:System.Object?displayProperty=fullName> (C# keyword: [object](../../../csharp/language-reference/keywords/object.md)). Cette hiérarchie de types unifiée est appelée [Système de type commun](http://msdn.microsoft.com/library/53c57c96-83e1-4ee3-9543-9ac832671a89) (CTS). Pour plus d’informations sur l’héritage dans C#, consultez [Héritage](../../../csharp/programming-guide/classes-and-structs/inheritance.md).  
  
-   Chaque type du CTS est défini comme *type valeur* ou *type référence*. Cela inclut tous les types personnalisés dans la bibliothèque de classes .NET Framework, ainsi que les types définis par l’utilisateur. Les types que vous définissez à l’aide du mot clé [struct](../../../csharp/language-reference/keywords/struct.md) sont des types valeur ; tous les types numériques intégrés sont `structs`. Les types que vous définissez à l’aide du mot clé [class](../../../csharp/language-reference/keywords/class.md) sont des types référence. Les types référence et les types valeur ont des règles différentes lors de la compilation et un comportement différent au moment de l’exécution.  
  
 L’illustration suivante montre la relation entre les types valeur et les types référence dans le CTS.  
  
 ![Types valeur et types référence](../../../csharp/programming-guide/types/media/valuetypescts.png "ValueTypesCTS")  
Types valeur et types référence dans le CTS  
  
> [!NOTE]
>  Vous pouvez voir que les types couramment utilisés sont organisés dans l’espace de noms <xref:System>. Toutefois, l’espace de noms qui contient un type n’a aucune incidence sur le fait qu’il s’agisse d’un type valeur ou d’un type référence.  
  
### <a name="value-types"></a>Types valeur  
 Les types valeur sont dérivés de <xref:System.ValueType?displayProperty=fullName>, qui est dérivé de <xref:System.Object?displayProperty=fullName>. Les types dérivés de <xref:System.ValueType?displayProperty=fullName> ont un comportement spécifique dans le CLR. Les variables de type valeur contiennent directement leurs valeurs, ce qui signifie que la mémoire est allouée inline dans le contexte où la variable est déclarée. Aucune allocation des tas ni surcharge de garbage collection distincte n’a lieu pour les variables de type valeur.  
  
 Il existe deux catégories de types valeur : [struct](../../../csharp/language-reference/keywords/struct.md) et [enum](../../../csharp/language-reference/keywords/enum.md).  
  
 Les types numériques intégrés sont des structs et disposent de propriétés et de méthodes auxquelles vous pouvez accéder :  
  
```csharp  
// Static method on type Byte.  
byte b = Byte.MaxValue;  
```  
  
 Mais vous les déclarez et leur affectez des valeurs comme s’ils étaient de simples types non agrégés :  
  
```csharp  
byte num = 0xA;  
int i = 5;  
char c = 'Z';  
```  
  
 Les types valeur sont scellés (*sealed*), ce qui signifie par exemple que vous ne pouvez pas dériver un type de <xref:System.Int32?displayProperty=fullName>. Vous ne pouvez pas non plus définir un struct pour qu’il hérite d’une classe ou d’un struct défini par l’utilisateur car un struct peut uniquement hériter de <xref:System.ValueType?displayProperty=fullName>. Toutefois, un struct peut implémenter une ou plusieurs interfaces. Vous pouvez effectuer un cast d’un type struct en un type interface. En conséquence, une opération de *boxing* encapsule le struct dans un objet de type référence sur le tas managé. Les opérations de boxing surviennent lorsque vous passez un type valeur à une méthode qui accepte un <xref:System.Object?displayProperty=fullName> comme paramètre d’entrée. Pour plus d’informations, consultez [Conversion boxing et unboxing](../../../csharp/programming-guide/types/boxing-and-unboxing.md).  
  
 Vous utilisez le mot clé [struct](../../../csharp/language-reference/keywords/struct.md) pour créer vos propres types valeur personnalisés. En règle générale, un struct est utilisé comme conteneur pour un petit jeu de variables connexes, comme le montre l'exemple suivant :  
  
 [!code-cs[csProgGuideObjects#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/index_4.cs)]  
  
 Pour plus d’informations sur les structs, consultez [Structs](../../../csharp/programming-guide/classes-and-structs/structs.md). Pour plus d’informations sur les types valeur dans le [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)], consultez [Système de type commun](http://msdn.microsoft.com/library/53c57c96-83e1-4ee3-9543-9ac832671a89).  
  
 L’autre catégorie de types valeur est [enum](../../../csharp/language-reference/keywords/enum.md). Un enum définit un jeu de constantes intégrales nommées. Par exemple l’énumération <xref:System.IO.FileMode?displayProperty=fullName> dans la bibliothèque de classes .NET Framework contient un ensemble de nombres entiers constants nommés qui spécifient comment un fichier doit être ouvert. Ceci est défini comme indiqué dans l’exemple suivant :  
 
 [!code-cs[csProgGuideTypes#44](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/index_5.cs)]  
  
 La constante `System.IO.FileMode.Create` a la valeur 2. Toutefois, le nom est beaucoup plus explicite pour les êtres humains qui lisent le code source et c’est pourquoi il est préférable d’utiliser des énumérations au lieu de chiffres littéraux constants. Pour plus d’informations, consultez <xref:System.IO.FileMode?displayProperty=fullName>.  
  
 Tous les enums héritent de <xref:System.Enum?displayProperty=fullName>, qui hérite de <xref:System.ValueType?displayProperty=fullName>. Toutes les règles qui s’appliquent aux structs s’appliquent également aux enums. Pour plus d’informations sur les enums, consultez [Types énumération](../../../csharp/programming-guide/enumeration-types.md).  
  
### <a name="reference-types"></a>Types référence  
 Un type qui est défini comme une [classe](../../../csharp/language-reference/keywords/class.md), un [délégué](../../../csharp/language-reference/keywords/delegate.md), un tableau ou une [interface](../../../csharp/language-reference/keywords/interface.md) est un *type référence*. Au moment de l’exécution, quand vous déclarez une variable de type référence, celle-ci contient la valeur [null](../../../csharp/language-reference/keywords/null.md) tant que vous n’avez pas explicitement créé une instance de l’objet à l’aide de l’opérateur [new](../../../csharp/language-reference/keywords/new.md) ou que vous ne lui avez pas assigné un objet créé ailleurs à l’aide de `new, as shown in the following example:`  
  
```csharp  
MyClass mc = new MyClass();  
MyClass mc2 = mc;  
```  
   Une interface doit être initialisée avec un objet de classe qui l’implémente. Si `MyClass` implémente `IMyInterface`, vous créez une instance de `IMyInterface` comme indiqué dans l’exemple suivant :  
  
```csharp  
IMyInterface iface = new MyClass();  
```  
  
 Quand l’objet est créé, la mémoire est allouée sur le tas managé et la variable contient uniquement une référence à l’emplacement de l’objet. Les types sur le tas managé entraînent une surcharge quand ils sont alloués et récupérés par la fonctionnalité de gestion automatique de la mémoire du CLR (appelée *garbage collection*). Toutefois, le garbage collection est également optimisé, et dans la plupart des cas, ne nuit pas aux performances. Pour plus d’informations sur le garbage collection, consultez [Gestion automatique de la mémoire](http://msdn.microsoft.com/library/d4850de5-fa63-4936-a250-5678d118acba).  
  
 Tous les tableaux sont des types référence, même si leurs éléments sont des types valeur. Les tableaux sont implicitement dérivés de la classe <xref:System.Array?displayProperty=fullName>, mais vous les déclarer et les utiliser avec la syntaxe simplifiée fournie par C#, comme illustré dans l’exemple suivant :  
  
 [!code-cs[csProgGuideTypes#45](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/index_6.cs)]  
  
 Les types référence prennent en charge l’héritage. Quand vous créez une classe, vous pouvez hériter de toute autre interface ou classe qui n’est pas définie comme [sealed](../../../csharp/language-reference/keywords/sealed.md), et d’autres classes peuvent hériter de votre classe et substituer vos méthodes virtuelles. Pour plus d’informations sur la création de vos propres classes, consultez [Classes et structures](../../../csharp/programming-guide/classes-and-structs/index.md). Pour plus d’informations sur l’héritage et les méthodes virtuelles, consultez [Héritage](../../../csharp/programming-guide/classes-and-structs/inheritance.md).  
  
## <a name="types-of-literal-values"></a>Types de valeurs littérales  
 Dans C#, les valeurs littérales reçoivent un type du compilateur. Vous pouvez spécifier la façon dont un littéral numérique doit être typé en ajoutant une lettre à la fin du nombre. Par exemple, pour spécifier que la valeur 4,56 doit être traitée comme une valeur float, ajoutez « f » ou « F » après le nombre : `4.56f`. Si aucune lettre n’est ajoutée, le compilateur déduit un type pour le littéral. Pour plus d’informations sur les types qui peuvent être spécifiés avec une lettre en suffixe, consultez les pages de référence des différents types dans [Types valeur](../../../csharp/language-reference/keywords/value-types.md).  
  
 Comme les littéraux sont typés et que tous les types dérivent en fin de compte de <xref:System.Object?displayProperty=fullName>, vous pouvez écrire et compiler du code, tel que le suivant :  
  
 [!code-cs[csProgGuideTypes#37](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/index_7.cs)]  
  
## <a name="generic-types"></a>Types génériques  
 Un type peut être déclaré avec un ou plusieurs *paramètres de type* qui servent d’espace réservé pour le type réel (le *type concret*) que le code client fournit lorsqu’il crée une instance du type. Ces types sont appelés *types génériques*. Par exemple, le type .NET Framework <xref:System.Collections.Generic.List%601?displayProperty=fullName> a un paramètre de type qui, par convention, porte le nom *T*. Lorsque vous créez une instance du type, vous spécifiez le type des objets contenus dans la liste, par exemple, une chaîne :  
 
```csharp
List<string> stringList = new List<string>();
stringList.Add("String example");
// compile time error adding a type other than a string:
stringList.Add(4);
```
 L’utilisation du paramètre de type rend possible la réutilisation de la même classe pour contenir tout type d’élément, sans avoir à convertir chaque élément en [object](../../../csharp/language-reference/keywords/object.md). Les classes de collection génériques sont appelées *collections fortement typées* car le compilateur connaît le type spécifique des éléments de la collection et peut déclencher une erreur au moment de la compilation si, par exemple, vous essayez d’ajouter un entier à l’objet `strings` dans l’exemple précédent. Pour plus d’informations, consultez [Génériques](../../../csharp/programming-guide/generics/index.md).  
  
## <a name="implicit-types-anonymous-types-and-nullable-types"></a>Types implicites, types anonymes et types Nullable  
 Comme indiqué précédemment, vous pouvez attribuer implicitement un type à une variable locale (mais pas les membres de la classe) à l’aide du mot clé [var](../../../csharp/language-reference/keywords/var.md). La variable reçoit toujours un type au moment de la compilation, mais le type est fourni par le compilateur. Pour plus d’informations, consultez [Variables locales implicitement typées](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).  
  
 Dans certains cas, il est difficile de créer un type nommé pour des ensembles simples de valeurs associées que vous ne souhaitez pas stocker ou transférer en dehors des limites de la méthode. Vous pouvez créer des *types anonymes* à cet effet. Pour plus d’informations, consultez [Types anonymes](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).  
  
 Les types valeur ordinaires ne peuvent pas avoir la valeur [Null](../../../csharp/language-reference/keywords/null.md). Toutefois, vous pouvez créer des types valeur Nullable en apposant un `?` après le type. Par exemple, `int?` est un type `int` qui peut également avoir la valeur [null](../../../csharp/language-reference/keywords/null.md). Dans le CTS, les types Nullable sont des instances du type struct générique <xref:System.Nullable%601?displayProperty=fullName>. Les types Nullable sont particulièrement utiles lorsque vous passez des données vers et à partir de bases de données dans lesquelles les valeurs numériques peuvent être Null. Pour plus d’informations, consultez [Types Nullable](../../../csharp/programming-guide/nullable-types/index.md).  
  
## <a name="related-sections"></a>Rubriques connexes  
 Pour plus d’informations, consultez les rubriques suivantes :  
  
-   [Cast et conversions de types](../../../csharp/programming-guide/types/casting-and-type-conversions.md)  
  
-   [Conversion boxing et unboxing](../../../csharp/programming-guide/types/boxing-and-unboxing.md)  
  
-   [Utilisation du type dynamic](../../../csharp/programming-guide/types/using-type-dynamic.md)  
  
-   [Types valeur](../../../csharp/language-reference/keywords/value-types.md)  
  
-   [Types référence](../../../csharp/language-reference/keywords/reference-types.md)  
  
-   [Classes et structs](../../../csharp/programming-guide/classes-and-structs/index.md)  
  
-   [Types anonymes](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)  
  
-   [Génériques](../../../csharp/programming-guide/generics/index.md)  
  
-   [Variables et Expressions](http://go.microsoft.com/fwlink/?LinkId=221228) dans [Pour démarrer dans Visual C# 2010](http://go.microsoft.com/fwlink/?LinkId=221214)  
  
## <a name="c-language-specification"></a>Spécification du langage C#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur C#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Conversion des types de données XML](http://msdn.microsoft.com/library/a2aa99ba-8239-4818-9281-f1d72ee40bde)   
 [Tableau des types intégraux](../../../csharp/language-reference/keywords/integral-types-table.md)

