---
title: "Op&#233;rations de requ&#234;te de base (Visual Basic) | Microsoft Docs"
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
  - "sources de données (LINQ en Visual Basic)"
  - "Join (clause) (LINQ en Visual Basic)"
  - "classer des données (LINQ en Visual Basic)"
  - "projections (LINQ en Visual Basic)"
  - "LINQ [Visual Basic], opérations de requête"
  - "Order By (clause) (LINQ en Visual Basic)"
  - "joindre des données (LINQ en Visual Basic)"
  - "requêtes [LINQ en Visual Basic], opérations de base"
  - "sélectionner des données (LINQ en Visual Basic)"
  - "Group By (clause) (LINQ en Visual Basic)"
  - "grouper des données (LINQ en Visual Basic)"
  - "Select (clause) (LINQ en Visual Basic)"
ms.assetid: 1146f6d0-fcb8-4f4d-8223-c9db52620d21
caps.latest.revision: 37
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 35
---
# Op&#233;rations de requ&#234;te de base (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

Cette rubrique présente brièvement les expressions [!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext-md.md)] dans Visual Basic et certains types d'opérations classiques effectués dans une requête.  Pour plus d'informations, consultez les rubriques suivantes :  
  
 [Introduction to LINQ in Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
  
 [Queries](../../../../visual-basic/language-reference/queries/queries.md)  
  
 [Procédure pas à pas : écriture de requêtes dans Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/walkthrough-writing-queries.md)  
  
## Spécification de la source de données \(From\)  
 Dans une requête [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)], la première étape consiste à spécifier la source de données à interroger.  Par conséquent, la clause d' `From` dans une requête est toujours en premier. Les opérateurs de requête et sélectionnez façonnent le résultat selon le type de la source.  
  
 [!code-vb[VbLINQBasicOps#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_1.vb)]  
  
 La clause `From` spécifie la source de données \(`customers`\) et une *variable de portée* \(`cust`\).  La variable de portée est similaire à une variable d'itération de boucle, à la différence que dans une expression de requête, aucune itération réelle ne se produit.  Lorsque la requête est exécutée, souvent à l'aide d'une boucle `For Each`, la variable de portée sert de référence à chaque élément consécutif dans `customers`.  Étant donné que le compilateur peut déduire le type de `cust`, vous n'avez pas à le spécifier explicitement.  Pour obtenir des exemples de requêtes écrites avec et sans type explicite, consultez [Type Relationships in Query Operations \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/linq/type-relationships-in-query-operations.md).  
  
 Pour plus d'informations sur l'utilisation de la clause `From` dans Visual Basic, consultez [From Clause](../../../../visual-basic/language-reference/queries/from-clause.md).  
  
## Filtrage de données \(Where\)  
 L'opération de requête la plus courante est probablement l'application d'un filtre sous forme d'expression booléenne.  La requête retourne alors uniquement les éléments pour lesquels l'expression a la valeur true.  Une clause `Where` est utilisée pour effectuer le filtrage.  Le filtre spécifie les éléments de la source de données à inclure dans la séquence résultante.  Dans l'exemple suivant, seuls les clients qui ont une adresse à Londres \(London\) sont inclus.  
  
 [!code-vb[VbLINQBasicOps#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_2.vb)]  
  
 Vous pouvez utiliser des opérateurs logiques tels que `And` et `Or` pour associer des expressions de filtre dans une clause `Where`.  Par exemple, pour retourner uniquement les clients de Londres et dont le nom est Devon, utilisez le code suivant :  
  
```vb#  
Where cust.City = "London" And cust.Name = "Devon"   
```  
  
 Pour retourner les clients de Londres ou de Paris, utilisez le code suivant :  
  
```vb#  
Where cust.City = "London" Or cust.City = "Paris"   
```  
  
 Pour plus d'informations sur l'utilisation de la clause `Where` dans Visual Basic, consultez [Where Clause](../../../../visual-basic/language-reference/queries/where-clause.md).  
  
## Classement de données \(Order By\)  
 Il est souvent pratique de trier les données retournées dans un ordre spécifique.  La clause `Order By` permet de trier les éléments de la séquence retournée selon un ou plusieurs champs spécifiés.  Par exemple, la requête suivante trie les résultats selon la propriété `Name`.  Étant donné que `Name` est une chaîne, les données retournées seront triées par ordre alphabétique, de A à Z.  
  
 [!code-vb[VbLINQBasicOps#3](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_3.vb)]  
  
 Pour classer les résultats dans l'ordre inverse, de Z à A, utilisez la clause `Order By...Descending`.  La valeur par défaut est `Ascending` lorsque ni `Ascending`, ni `Descending` ne sont spécifiés.  
  
 Pour plus d'informations sur l'utilisation de la clause `Order By` dans Visual Basic, consultez [Order By Clause](../../../../visual-basic/language-reference/queries/order-by-clause.md).  
  
## Sélection de données \(Select\)  
 La clause `Select` spécifie la forme et le contenu d'éléments retournés.  Par exemple, vous pouvez spécifier si vos résultats se composeront d'objets `Customer` complets, d'une seule propriété `Customer`, d'un sous\-ensemble de propriétés, d'une combinaison de propriétés de sources de données diverses ou d'un nouveau type de résultat basé sur un calcul.  Lorsque la clause `Select` produit autre chose qu'une copie de l'élément source, l'opération est appelée *projection*.  
  
 Pour récupérer une collection qui se compose d'objets `Customer` complets, sélectionnez la variable de portée elle\-même :  
  
 [!code-vb[VbLINQBasicOps#4](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_4.vb)]  
  
 Si une instance de `Customer` est un objet volumineux comportant de nombreux champs et que vous souhaitez uniquement récupérer le nom, vous pouvez sélectionner `cust.Name`, comme indiqué dans l'exemple suivant.  L'inférence de type de variable locale reconnaît que cela modifie le type de résultat d'une collection d'objets `Customer` en une collection de chaînes.  
  
 [!code-vb[VbLINQBasicOps#5](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_5.vb)]  
  
 Pour sélectionner plusieurs champs de la source de données, vous avez deux possibilités :  
  
-   Dans la clause `Select`, spécifiez les champs que vous souhaitez inclure dans le résultat.  Le compilateur définira un type anonyme dont ces champs constituent les propriétés.  Pour plus d'informations, consultez [Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).  
  
     Étant donné que les éléments retournés dans l'exemple suivant sont des instances d'un type anonyme, vous ne pouvez pas faire référence au type par son nom ailleurs dans votre code.  Le nom désigné par le compilateur pour le type contient des caractères qui ne sont pas valides dans le code Visual Basic normal.  Dans l'exemple suivant, les éléments de la collection retournée par la requête dans `londonCusts4` sont des instances d'un type anonyme.  
  
     [!code-vb[VbLINQBasicOps#6](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_6.vb)]  
  
     ou  
  
-   Définissez un type nommé qui contient les champs spécifiques à inclure dans le résultat, puis créez et initialisez des instances du type dans la clause `Select`.  Utilisez cette option uniquement si vous devez utiliser des résultats individuels en dehors de la collection dans laquelle ils sont retournés ou si vous devez les passer comme paramètres dans des appels de méthode.  Dans l'exemple suivant, le type de `londonCusts5` est IEnumerable \(Of NamePhone\).  
  
     [!code-vb[VbLINQBasicOps#7](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_7.vb)]  
  
     [!code-vb[VbLINQBasicOps#8](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_8.vb)]  
  
 Pour plus d'informations sur l'utilisation de la clause `Select` dans Visual Basic, consultez [Select Clause](../../../../visual-basic/language-reference/queries/select-clause.md).  
  
## Jointure de données \(Join et Group Join\)  
 Vous pouvez associer plusieurs sources de données dans la clause `From` de diverses façons.  Par exemple, le code suivant utilise deux sources de données et associe implicitement les propriétés des deux dans le résultat.  La requête sélectionne les étudiants dont le nom commence par une voyelle.  
  
 [!code-vb[VbLINQBasicOps#9](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_9.vb)]  
  
> [!NOTE]
>  Vous pouvez exécuter ce code avec la liste d'étudiants créée dans [How to: Create a List of Items](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md).  
  
 Le mot clé `Join` est équivalent à `INNER JOIN` dans SQL.  Il associe deux collections basées sur des valeurs de clés correspondantes entre les éléments des deux collections.  La requête retourne tout ou partie des éléments de la collection qui ont des valeurs de clés correspondantes.  Par exemple, le code suivant duplique l'action de la jointure implicite précédente.  
  
 [!code-vb[VbLINQBasicOps#10](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_10.vb)]  
  
 `Group Join` rassemble des collections dans une collection hiérarchique unique, tout comme `LEFT JOIN` dans SQL.  Pour plus d'informations, consultez [Join Clause](../../../../visual-basic/language-reference/queries/join-clause.md) et [Group Join Clause](../../../../visual-basic/language-reference/queries/group-join-clause.md).  
  
## Regroupement de données \(Group By\)  
 Vous pouvez ajouter une clause `Group By` pour regrouper les éléments d'un résultat de requête d'après un ou plusieurs champs des éléments.  Par exemple, le code suivant regroupe les étudiants par année de classe.  
  
 [!code-vb[VbLINQBasicOps#11](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_11.vb)]  
  
 Si vous exécutez ce code à l'aide de la liste d'étudiants créée dans [How to: Create a List of Items](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md), la sortie de l'instruction `For Each` est la suivante :  
  
 Year: Junior \(Année : 1re\)  
  
 Tucker, Michael  
  
 Garcia, Hugo  
  
 Garcia, Debra  
  
 Tucker, Lance  
  
 Year: Senior \(Année : Terminale\)  
  
 Omelchenko, Svetlana  
  
 Osada, Michiko  
  
 Fakhouri, Fadi  
  
 Feng, Hanying  
  
 Adams, Terry  
  
 Year: Freshman \(Année : 3e\)  
  
 Mortensen, Sven  
  
 Garcia, Cesar  
  
 La variante indiquée dans le code suivant trie les années de classe, puis trie les étudiants de chaque année par nom.  
  
 [!code-vb[VbLINQBasicOps#12](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/basic-query-operations_12.vb)]  
  
 Pour plus d'informations sur `Group By`, consultez [Group By, clause](../../../../visual-basic/language-reference/queries/group-by-clause.md).  
  
## Voir aussi  
 <xref:System.Collections.Generic.IEnumerable%601>   
 [Getting Started with LINQ in Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)   
 [Queries](../../../../visual-basic/language-reference/queries/queries.md)   
 [Standard Query Operators Overview](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)   
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)   
 [Basic LINQ Query Operations](../../../../csharp/programming-guide/concepts/linq/basic-linq-query-operations.md)