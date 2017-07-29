---
title: "dynamic (Référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- dynamic_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- dynamic [C#]
- dynamic keyword [C#]
ms.assetid: 9e797102-cc83-4964-bf58-afe4f54d16bc
caps.latest.revision: 25
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
ms.openlocfilehash: b68a6ef4dc3dda01638b9bb84db58ba77214f490
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="dynamic-c-reference"></a>dynamic (Référence C#)
Le type `dynamic` permet aux opérations dans lesquelles il se produit de contourner la vérification de type au moment de la compilation. Au lieu de cela, ces opérations sont résolues au moment de l’exécution. Le type `dynamic` simplifie l’accès aux API COM telles que les API Office Automation, et également aux API dynamiques telles que les bibliothèques IronPython et au modèle DOM (Document Object Model) HTML.  
  
 Le type `dynamic` se comporte comme le type `object` dans la plupart des cas. Toutefois, les opérations qui contiennent des expressions de type `dynamic` ne sont pas résolues et leur type n’est pas vérifié par le compilateur. Le compilateur empaquète des informations sur l’opération, qui sont ensuite utilisées pour évaluer l’opération au moment de l’exécution. Dans le cadre du processus, les variables de type `dynamic` sont compilées dans des variables de type `object`. Ainsi, le type `dynamic` existe seulement au moment de la compilation, et non au moment de l’exécution.  
  
 L’exemple suivant compare une variable de type `dynamic` à une variable de type `object`. Pour vérifier le type de chaque variable au moment de la compilation, placez le pointeur de la souris sur `dyn` ou `obj` dans les instructions `WriteLine`. IntelliSense affiche **dynamic** pour `dyn` et **object** pour `obj`.  
  
 [!code-cs[csrefKeywordsTypes#21](../../../csharp/language-reference/keywords/codesnippet/CSharp/dynamic_1.cs)]  
  
 Les instructions `WriteLine` affichent les types d’exécution de `dyn` et `obj`. À ce stade, tous deux ont le même type, entier. La sortie suivante est produite :  
  
 `System.Int32`  
  
 `System.Int32`  
  
 Pour voir la différence entre `dyn` et `obj` au moment de la compilation, ajoutez les deux lignes suivantes entre les déclarations et les instructions `WriteLine` de l’exemple précédent.  
  
```csharp  
dyn = dyn + 3;  
obj = obj + 3;  
```  
  
 Une erreur du compilateur est signalée pour la tentative d’ajout d’un entier et un d’objet dans l’expression `obj + 3`. Toutefois, aucune erreur n’est signalée pour `dyn + 3`. L’expression qui contient `dyn` n’est pas vérifié au moment de la compilation, car le type de `dyn` est `dynamic`.  
  
## <a name="context"></a>Contexte  
 Le mot clé `dynamic` peut apparaître directement ou en tant que composant d’un type construit dans les situations suivantes :  
  
-   Dans les déclarations, comme le type d’une propriété, d’un champ, d’un indexeur, d’un paramètre, d’une valeur de retour, d’une variable locale ou d’une contrainte de type. La définition de classe suivante utilise `dynamic` dans plusieurs déclarations différentes.  
  
     [!code-cs[csrefKeywordsTypes#22](../../../csharp/language-reference/keywords/codesnippet/CSharp/dynamic_2.cs)]  
  
-   Dans les conversions de type explicites, comme le type cible d’une conversion.  
  
     [!code-cs[csrefKeywordsTypes#23](../../../csharp/language-reference/keywords/codesnippet/CSharp/dynamic_3.cs)]  
  
-   Dans tout contexte où les types servent de valeurs, comme sur le côté droit d’un opérateur `is` ou d’un opérateur `as`, ou comme argument de `typeof` dans le cadre d’un type construit. Par exemple, `dynamic` peut être utilisé dans les expressions suivantes.  
  
     [!code-cs[csrefKeywordsTypes#24](../../../csharp/language-reference/keywords/codesnippet/CSharp/dynamic_4.cs)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise `dynamic` dans plusieurs déclarations. La méthode `Main` compare également la vérification de type au moment de la compilation avec la vérification de type au moment de l’exécution.  
  
 [!code-cs[csrefKeywordsTypes#25](../../../csharp/language-reference/keywords/codesnippet/CSharp/dynamic_5.cs)]  
  
 Pour obtenir plus d’informations et d’exemples, consultez [Utilisation du type dynamic](../../../csharp/programming-guide/types/using-type-dynamic.md).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Dynamic.ExpandoObject?displayProperty=fullName>   
 <xref:System.Dynamic.DynamicObject?displayProperty=fullName>   
 [Utilisation du type dynamic](../../../csharp/programming-guide/types/using-type-dynamic.md)   
 [object](../../../csharp/language-reference/keywords/object.md)   
 [is](../../../csharp/language-reference/keywords/is.md)   
 [as](../../../csharp/language-reference/keywords/as.md)   
 [typeof](../../../csharp/language-reference/keywords/typeof.md)   
 [Guide pratique pour effectuer sans risque un cast à l’aide des opérateurs as et is](../../../csharp/programming-guide/types/how-to-safely-cast-by-using-as-and-is-operators.md)   
 [Procédure pas à pas : création et utilisation d’objets dynamiques](../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)

