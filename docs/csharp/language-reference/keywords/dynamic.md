---
title: "dynamic (R&#233;f&#233;rence C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "dynamic_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "dynamic (C#)"
  - "dynamic (mot clé C#)"
ms.assetid: 9e797102-cc83-4964-bf58-afe4f54d16bc
caps.latest.revision: 25
caps.handback.revision: 25
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# dynamic (R&#233;f&#233;rence C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Le type `dynamic` permet les opérations dans lesquelles il ignore la vérification de type de compilation.  À la place, ces opérations sont résolues au moment de l'exécution.  Le type `dynamic` simplifie l'accès aux API COM telles que les API d'Automation d'Office, et également aux API dynamiques telles que les bibliothèques IronPython et au DOM \(Document Object Model\) HTML.  
  
 Le type `dynamic` se comporte comme le type `object` dans la plupart des circonstances.  Toutefois, les opérations qui contiennent des expressions de type `dynamic` ne sont pas résolues ou le type est vérifié par le compilateur.  Le compilateur crée un package des informations concernant l'opération. Ces informations sont utilisées ultérieurement pour évaluer l'opération au moment de l'exécution.  Dans le cadre du processus, les variables de type `dynamic` sont compilées dans les variables de type `object`.  Par conséquent, le type `dynamic` existe uniquement au moment de la compilation, pas au moment de l'exécution.  
  
 L'exemple suivant compare une variable de type `dynamic` à une variable de type `object`.  Pour vérifier le type de chaque variable au moment de la compilation, placez le pointeur de la souris sur `dyn` ou `obj` dans les instructions `WriteLine`.  IntelliSense affiche **dynamique** pour `dyn` et **objet** pour `obj`.  
  
 [!code-cs[csrefKeywordsTypes#21](../../../csharp/language-reference/keywords/codesnippet/CSharp/dynamic_1.cs)]  
  
 Les instructions `WriteLine` affichent les types d'exécution de `dyn` et `obj`.  À ce stade, les deux ont le même type, entier.  La sortie suivante est produite :  
  
 `System.Int32`  
  
 `System.Int32`  
  
 Pour voir la différence entre `dyn` et `obj` au moment de la compilation, ajoutez les deux lignes suivantes entre les déclarations et les instructions `WriteLine` de l'exemple précédent.  
  
```c#  
dyn = dyn + 3;  
obj = obj + 3;  
  
```  
  
 Une erreur du compilateur est signalée pour l'ajout tentée d'un entier et un objet dans l'expression `obj + 3`.  Toutefois, aucune erreur n'est signalée pour `dyn + 3`.  L'expression qui contient `dyn` n'est pas vérifiée au moment de la compilation parce que le type de `dyn` est `dynamic`.  
  
## Contexte  
 Le mot clé `dynamic` peut s'afficher directement ou comme un composant d'un type construit dans les situations suivantes :  
  
-   Dans les déclarations, comme le type d'une propriété, d'un champ, d'un indexeur, d'un paramètre, d'une valeur de retour, d'une variable locale ou d'une contrainte de type.  La définition de classe suivante utilise `dynamic` dans plusieurs déclarations différentes.  
  
     [!code-cs[csrefKeywordsTypes#22](../../../csharp/language-reference/keywords/codesnippet/CSharp/dynamic_2.cs)]  
  
-   Dans les conversions de type explicites, comme le type de cible d'une conversion.  
  
     [!code-cs[csrefKeywordsTypes#23](../../../csharp/language-reference/keywords/codesnippet/CSharp/dynamic_3.cs)]  
  
-   Dans tout contexte où les types servent comme valeurs, comme sur le côté droit d'un opérateur `is` ou d'un opérateur `as` ou comme pour l'argument à `typeof` dans le cadre d'un type construit.  Par exemple, `dynamic` peut être utilisé dans les expressions suivantes.  
  
     [!code-cs[csrefKeywordsTypes#24](../../../csharp/language-reference/keywords/codesnippet/CSharp/dynamic_4.cs)]  
  
## Exemple  
 L'exemple suivant utilise `dynamic` dans plusieurs déclarations.  La méthode `Main` compare également la vérification de type de compilation avec la vérification de type d'exécution.  
  
 [!code-cs[csrefKeywordsTypes#25](../../../csharp/language-reference/keywords/codesnippet/CSharp/dynamic_5.cs)]  
  
 Pour plus d'informations et d'exemples, consultez [Utilisation du type dynamic](../../../csharp/programming-guide/types/using-type-dynamic.md).  
  
## Voir aussi  
 <xref:System.Dynamic.ExpandoObject?displayProperty=fullName>   
 <xref:System.Dynamic.DynamicObject?displayProperty=fullName>   
 [Utilisation du type dynamic](../../../csharp/programming-guide/types/using-type-dynamic.md)   
 [objet](../../../csharp/language-reference/keywords/object.md)   
 [is](../../../csharp/language-reference/keywords/is.md)   
 [as](../../../csharp/language-reference/keywords/as.md)   
 [typeof](../../../csharp/language-reference/keywords/typeof.md)   
 [Comment : effectuer sans risque un cast à l'aide des opérateurs as et is](../../../csharp/programming-guide/types/how-to-safely-cast-by-using-as-and-is-operators.md)   
 [Procédure pas à pas : création et utilisation d'objets dynamiques](../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)