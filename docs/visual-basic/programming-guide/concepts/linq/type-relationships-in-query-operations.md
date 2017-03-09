---
title: "Type Relationships in Query Operations (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "variable relationships [LINQ in Visual Basic]"
  - "type information inferred [LINQ in Visual Basic]"
  - "type relationships [LINQ in Visual Basic]"
  - "queries [LINQ in Visual Basic], type relationships"
  - "data sources [LINQ in Visual Basic], type relationships"
  - "LINQ [Visual Basic], type relationships"
  - "inferring type information [LINQ in Visual Basic]"
  - "relationships [LINQ in Visual Basic]"
ms.assetid: b5ff4da5-f3fd-4a8e-aaac-1cbf52fa16f6
caps.latest.revision: 34
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 32
---
# Type Relationships in Query Operations (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

Les variables utilisées dans les opérations de requête [!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext-md.md)] sont fortement typées et doivent être compatibles l'une avec l'autre.  Le typage fort est utilisé dans la source de données, dans la requête elle\-même, et dans l'exécution de la requête.  L'illustration suivante identifie les termes utilisés pour décrire une requête [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)].  Pour plus d'informations sur les parties d'une requête, consultez [Opérations de requête de base \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/linq/basic-query-operations.md).  
  
 ![Requête en pseudocode avec éléments en surbrillance.](../../../../visual-basic/programming-guide/concepts/linq/media/sjltyperels.png "SJLtypeRels")  
Parties d'une requête LINQ  
  
 Le type de la variable de portée dans la requête doit être compatible avec le type des éléments dans la source de données.  Le type de la variable de requête doit être compatible avec l'élément de séquence défini dans la clause `Select`.  Enfin, le type des éléments de séquence doit également être compatible avec le type de la variable de contrôle de boucle utilisée dans l'instruction `For Each` qui exécute la requête.  Ce typage fort facilite l'identification des erreurs de type au moment de la compilation.  
  
 En implémentant l'inférence de type local, également connue sous le nom de *type implicite*, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] rend le typage plus pratique.  Cette fonctionnalité est utilisée dans l'exemple précédent et vous verrez qu'elle est utilisée dans les exemples et la documentation [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)].  En Visual Basic, l'inférence de type local s'effectue en utilisant simplement une instruction `Dim` sans clause `As`.  Dans l'exemple suivant, `city` est fortement typé comme chaîne \(string\).  
  
 [!code-vb[VbLINQTypeRels#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/visualbasic/type-relationships-in-qu_1.vb)]  
  
> [!NOTE]
>  L'inférence de type local fonctionne uniquement lorsque `Option Infer` a la valeur `On`.  Pour plus d'informations, consultez [Option Infer Statement](../../../../visual-basic/language-reference/statements/option-infer-statement.md).  
  
 Toutefois, même si vous utilisez l'inférence de type local dans une requête, les mêmes relations de types sont présentes parmi les variables dans la source de données, la variable de requête et la boucle d'exécution de la requête.  Il est utile de bien comprendre les notions fondamentales de ces relations de types lorsque vous écrivez des requêtes [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)] ou que vous utilisez les exemples et exemples de code dans la documentation.  
  
 Vous devrez peut\-être spécifier un type explicite pour une variable de portée qui ne correspond pas au type retourné par la source de données.  Vous pouvez spécifier le type de la variable de portée à l'aide d'une clause `As`.  Toutefois, une erreur se produit si la conversion est une [conversion restrictive](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) et que `Option Strict` a la valeur `On`.  Par conséquent, il est recommandé d'exécuter la conversion sur les valeurs récupérées à partir de la source de données.  Vous pouvez convertir les valeurs de la source de données en type de variable de portée explicite à l'aide de la méthode <xref:System.Linq.Enumerable.Cast%2A>.  Vous pouvez également effectuer un cast des valeurs sélectionnées dans la clause `Select` vers un type explicite qui est différent du type de la variable de portée.  Ces points sont illustrés dans le code suivant.  
  
 [!code-vb[VbLINQTypeRels#4](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/visualbasic/type-relationships-in-qu_2.vb)]  
  
## Requêtes qui retournent des éléments entiers des données source  
 L'exemple suivant présente une opération de requête [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)] qui retourne une séquence d'éléments sélectionnés à partir des données source.  La source, `names`, contient un tableau de chaînes, et le résultat de la requête est une séquence contenant des chaînes qui commencent par la lettre M.  
  
 [!code-vb[VbLINQTypeRels#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/visualbasic/type-relationships-in-qu_3.vb)]  
  
 Cela équivaut au code suivant, mais est beaucoup plus court et plus facile écrire.  Le style privilégié par Visual Basic est la fiabilité de l'inférence de type local dans les requêtes.  
  
 [!code-vb[VbLINQTypeRels#3](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/visualbasic/type-relationships-in-qu_4.vb)]  
  
 Les relations suivantes existent dans les deux exemples de code précédents, que les types soient déterminés implicitement ou explicitement.  
  
1.  Le type des éléments dans la source de données, `names`, est le type de la variable de portée, `name`, dans la requête.  
  
2.  Le type de l'objet sélectionné, `name`, détermine le type de la variable de requête, `mNames`.  Ici, `name` est une chaîne, donc la variable de requête est IEnumerable\(Of String\) en Visual Basic.  
  
3.  La requête définie dans `mNames` est exécutée dans la boucle `For Each`.  La boucle itère au sein du résultat de l'exécution de la requête.  La variable d'itération de boucle, `nm`, est une chaîne, étant donné que `mNames`, retourne une séquence de chaînes lors de son exécution.  
  
## Requêtes qui retournent un champ d'éléments sélectionnés  
 L'exemple suivant présente une opération de requête [!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq-md.md)] qui retourne une séquence contenant une seule partie de chaque élément sélectionné à partir de la source de données.  La requête prend une collection d'objets `Customer` comme sa source de données et projette uniquement la propriété `Name` dans le résultat.  Étant donné que le nom de client est une chaîne, la requête produit une séquence de chaînes comme sortie.  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
 Les relations entre les variables sont identiques à celles de l'exemple simplifié.  
  
1.  Le type des éléments dans la source de données, `customers`, est le type de la variable de portée, `cust`, dans la requête.  Dans cet exemple, ce type est `Customer`.  
  
2.  L'instruction `Select` retourne la propriété `Name` de chaque objet `Customer` au lieu de l'objet complet.  Étant donné que `Name` est une chaîne, la variable de requête, `custNames`, sera à nouveau IEnumerable\(Of String\), et non `Customer`.  
  
3.  Étant donné que `custNames` représente une séquence de chaînes, la variable d'itération de boucle `For Each`, `custName`, doit être une chaîne.  
  
 Sans inférence de type local, l'exemple précédent serait plus fastidieux à écrire et à comprendre, comme le montre l'exemple suivant.  
  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
## Requêtes qui requièrent des types anonymes  
 L'exemple suivant montre une situation plus complexe.  Dans l'exemple précédent, il était fastidieux de spécifier explicitement des types pour toutes les variables.  Dans cet exemple, c'est impossible.  Au lieu de sélectionner des éléments `Customer` entiers de la source de données ou un champ unique de chaque élément, la clause `Select` dans cette requête retourne deux propriétés de l'objet `Customer` d'origine : `Name` et `City`.  En réponse à la clause `Select`, le compilateur définit un type anonyme qui contient ces deux propriétés.  Le résultat de l'exécution de `nameCityQuery` dans la boucle `For Each` est une collection d'instances du nouveau type anonyme.  Étant donné que le type anonyme n'a pas de nom utilisable, vous ne pouvez pas spécifier explicitement le type de `nameCityQuery` ou `custInfo`.  Autrement dit, avec un type anonyme, vous n'avez aucun nom de type à utiliser à la place de `String` dans `IEnumerable(Of String)`.  Pour plus d'informations, consultez [Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).  
  
<CodeContentPlaceHolder>2</CodeContentPlaceHolder>  
 Même s'il n'est pas possible de spécifier des types pour toutes les variables dans l'exemple précédent, les relations restent les mêmes.  
  
1.  Le type des éléments dans la source de données est encore le type de la variable de portée dans la requête.  Dans cet exemple, `cust` est une instance de `Customer`.  
  
2.  Étant donné que l'instruction `Select` produit un type anonyme, la variable de requête, `nameCityQuery`, doit être implicitement typée comme type anonyme.  Un type anonyme n'a pas de nom utilisable et ne peut donc pas être spécifié explicitement.  
  
3.  Le type de la variable d'itération de la boucle `For Each` est le type anonyme créé à l'étape 2.  Étant donné que le type n'a pas de nom utilisable, le type de la variable d'itération de la boucle doit être déterminé implicitement.  
  
## Voir aussi  
 [Getting Started with LINQ in Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)   
 [Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)   
 [Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)   
 [Introduction to LINQ in Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)   
 [Queries](../../../../visual-basic/language-reference/queries/queries.md)