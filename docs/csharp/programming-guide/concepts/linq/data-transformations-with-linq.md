---
title: "Transformations de donn&#233;es avec LINQ (C#) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "LINQ [C#], transformations de données"
  - "éléments sources [LINQ en C#]"
  - "joindre plusieurs entrées [LINQ en C#]"
  - "plusieurs sorties en une séquence de sortie [LINQ en C#]"
  - "sous-ensemble d’éléments sources [LINQ en C#]"
  - "sources de données [LINQ en C#], transformations de données"
  - "transformations de données [LINQ en C#]"
ms.assetid: 674eae9e-bc72-4a88-aed3-802b45b25811
caps.latest.revision: 17
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 15
---
# Transformations de donn&#233;es avec LINQ (C#)
[!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext-md.md)] ne gère pas uniquement la récupération des données.  C'est également un outil puissant pour la transformation de données.  En utilisant une requête [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)], vous pouvez utiliser une séquence source en entrée et la modifier de nombreuses façons pour créer une séquence de sortie.  Vous pouvez modifier la séquence elle\-même sans modifier les éléments eux\-mêmes triant et en le regroupement. Mais éventuellement la plupart de fonctionnalité puissante des requêtes d' [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)] est la possibilité de créer de nouveaux types.  Cette opération est effectuée dans la clause [select](../../../../csharp/language-reference/keywords/select-clause.md).  Par exemple, il est possible de réaliser les tâches suivantes :  
  
-   Fusionner plusieurs séquences d'entrée dans une séquence de sortie unique avec un type nouveau.  
  
-   Créer des séquences de sortie dont les éléments se composent d'une seule propriété ou de plusieurs propriétés de chaque élément de la séquence source.  
  
-   Créer des séquences de sortie dont les éléments se composent des résultats des opérations effectuées sur les données sources.  
  
-   Créer des séquences de sortie dans un format différent.  Par exemple, vous pouvez transformer des données de lignes ou de fichiers texte SQL en XML.  
  
 Cette liste d'exemples n'est pas exhaustive.  Bien sûr, ces transformations peuvent être combinées de plusieurs façons dans la même requête.  Par ailleurs, la séquence de sortie d'une requête peut être utilisée comme séquence d'entrée pour une nouvelle requête.  
  
## Combinaison de plusieurs entrées en une séquence de sortie  
 Vous pouvez utiliser une requête [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)] pour créer une séquence de sortie qui contient des éléments de plusieurs séquences d'entrée.  L'exemple suivant montre comment combiner deux structures de données en mémoire, mais ces principes peuvent être appliqués pour combiner des données de sources XML, SQL ou DataSet.  Prenons l'exemple des deux types de classe suivants :  
  
 [!code-cs[CsLINQGettingStarted#7](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/data-transformations-with-linq_1.cs)]  
  
 L'exemple suivant présente la requête :  
  
 [!code-cs[CSLinqGettingStarted#8](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/data-transformations-with-linq_2.cs)]  
  
 Pour plus d'informations, consultez [join, clause](../../../../csharp/language-reference/keywords/join-clause.md) et [select, clause](../../../../csharp/language-reference/keywords/select-clause.md).  
  
## Sélection d'un sous\-ensemble de chaque élément source  
 Il existe deux méthodes principales pour sélectionner un sous\-ensemble de chaque élément de la séquence source :  
  
1.  Pour sélectionner un seul membre de l'élément source, utilisez l'opérateur point.  Dans l'exemple suivant, supposons qu'un objet `Customer` contient plusieurs propriétés publiques y compris une chaîne nommée `City`.  Une fois exécutée, cette requête génère une séquence de sortie de chaînes.  
  
    ```  
    var query = from cust in Customers  
                select cust.City;  
    ```  
  
2.  Pour créer des éléments qui contiennent plusieurs propriétés de l'élément source, vous pouvez utiliser un initialiseur d'objet avec un objet nommé ou un type anonyme.  L'exemple suivant montre comment utiliser un type anonyme pour encapsuler deux propriétés de chaque élément `Customer` :  
  
    ```  
    var query = from cust in Customer  
                select new {Name = cust.Name, City = cust.City};  
    ```  
  
 Pour plus d'informations, consultez [Initialiseurs d'objets et de collections](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md) et [Types anonymes](../../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).  
  
## Transformation d'objets en mémoire en XML  
 Les requêtes [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)] permettent de transformer facilement des données entre des structures de données en mémoire, des bases de données SQL, des groupes de données [!INCLUDE[vstecado](../../../../csharp/programming-guide/concepts/linq/includes/vstecado-md.md)] et des flux de données ou des documents XML.  L'exemple suivant transforme des objets d'une structure de données en mémoire en éléments XML.  
  
 [!code-cs[CsLINQGettingStarted#9](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/data-transformations-with-linq_3.cs)]  
  
 Le code génère la sortie XML suivante :  
  
```  
< Root>  
  <student>  
    <First>Svetlana</First>  
    <Last>Omelchenko</Last>  
    <Scores>97,92,81,60</Scores>  
  </student>  
  <student>  
    <First>Claire</First>  
    <Last>O'Donnell</Last>  
    <Scores>75,84,91,39</Scores>  
  </student>  
  <student>  
    <First>Sven</First>  
    <Last>Mortensen</Last>  
    <Scores>88,94,65,91</Scores>  
  </student>  
</Root>  
```  
  
 Pour plus d'informations, consultez [Création d'arborescences XML en C\#](../Topic/Creating%20XML%20Trees%20in%20C%23%20\(LINQ%20to%20XML\)1.md).  
  
## Opérations sur les éléments sources  
 Une séquence de sortie ne contient pas toujours des éléments ou des propriétés d'élément de la séquence source.  La sortie peut être une séquence de valeurs calculée avec les éléments sources comme arguments d'entrée.  La requête simple suivante, lorsqu'elle est exécutée, génère en sortie une séquence de chaînes dont les valeurs représentent un calcul basé sur la séquence source d'éléments de type `double`.  
  
> [!NOTE]
>  Les méthodes d'appel dans les expressions de requête ne sont pas prises en charge si la requête est traduite dans un autre domaine.  Par exemple, vous ne pouvez pas appeler de méthode C\# ordinaire dans [!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq-md.md)] car SQL Server n'a pas de contexte pour cette méthode.  Toutefois, vous pouvez mapper des procédures stockées à des méthodes et appeler celles\-ci.  Pour plus d'informations, consultez [Procédures stockées](../Topic/Stored%20Procedures.md).  
  
 [!code-cs[CsLINQGettingStarted#10](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/data-transformations-with-linq_4.cs)]  
  
## Voir aussi  
 [LINQ \(Language\-Integrated Query\)](../Topic/LINQ%20\(Language-Integrated%20Query\).md)   
 [LINQ à SQL](../Topic/LINQ%20to%20SQL.md)   
 [LINQ to DataSet](../Topic/LINQ%20to%20DataSet.md)   
 [LINQ to XML](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md)   
 [Expressions de requête \(LINQ\)](../../../../csharp/programming-guide/linq-query-expressions/index.md)   
 [select, clause](../../../../csharp/language-reference/keywords/select-clause.md)   
 [How to: Combine Data with Joins](../../../../visual-basic/programming-guide/language-features/linq/how-to-combine-data-with-linq-by-using-joins.md)