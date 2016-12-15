---
title: "Types valeur (r&#233;f&#233;rence C#) | Microsoft Docs"
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
  - "cs.valuetypes"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "langage C#, types valeur"
  - "types (C#), types valeur"
  - "types valeur (C#)"
ms.assetid: 471eb994-2958-49d5-a6be-19b4313f80a3
caps.latest.revision: 18
caps.handback.revision: 18
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Types valeur (r&#233;f&#233;rence C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Les types valeur sont répartis en deux catégories principales :  
  
-   [Structures](../../../csharp/language-reference/keywords/struct.md)  
  
-   [Énumérations](../../../csharp/language-reference/keywords/enum.md)  
  
 Les struct sont répartis dans les catégories suivantes :  
  
-   Types numériques  
  
    -   [Types intégraux](../../../csharp/language-reference/keywords/integral-types-table.md)  
  
    -   [Types virgule flottante](../../../csharp/language-reference/keywords/floating-point-types-table.md)  
  
    -   [decimal](../../../csharp/language-reference/keywords/decimal.md)  
  
-   [bool](../../../csharp/language-reference/keywords/bool.md)  
  
-   Structures définies par l'utilisateur.  
  
## Principales fonctionnalités des types valeur  
 Les variables basées sur des types valeur contiennent directement des valeurs.  L'attribution d'une variable de type valeur à une autre copie la valeur contenue.  Cela est différent de l'assignation des variables de type référence, qui copient une référence vers l'objet mais pas l'objet lui\-même.  
  
 Tous les types valeur sont dérivés implicitement de <xref:System.ValueType?displayProperty=fullName>.  
  
 Contrairement aux types référence, il n'est pas possible de dériver un nouveau type à partir d'un type valeur.  En revanche, comme les types référence, les types struct peuvent implémenter des interfaces.  
  
 Contrairement aux types référence, les types valeur ne peuvent pas contenir la valeur `null`.  Toutefois, la fonctionnalité de [types Nullable](../../../csharp/programming-guide/nullable-types/index.md) autorise pour les types valeur sont assignés à `null`.  
  
 Chaque type valeur possède implicitement un constructeur par défaut qui initialise la valeur par défaut du type associé.  Pour plus d'informations sur les valeurs par défaut des types valeur, consultez [Tableau des valeurs par défaut](../../../csharp/language-reference/keywords/default-values-table.md).  
  
## Principales fonctionnalités des types simples  
 Tous les types simples \(qui font partie du langage C\#\) sont des alias des types .NET Framework System.  Par exemple, [int](../../../csharp/language-reference/keywords/int.md) est un alias de <xref:System.Int32?displayProperty=fullName>.  Pour obtenir la liste complète des alias, consultez [Tableau des types intégrés](../../../csharp/language-reference/keywords/built-in-types-table.md).  
  
 Les expressions constantes, dont les opérandes sont tous des constantes de type simple, sont évaluées au moment de la compilation.  
  
 Les types simples peuvent être initialisés à l'aide de littéraux.  Par exemple, 'A' est un littéral du type `char` et 2001, un littéral du type `int`.  
  
## Initialisation des types valeur  
 En C\#, les variables locales doivent être initialisées avant de pouvoir être utilisées.  Par exemple, vous pouvez déclarer une variable locale sans l'initialiser, comme l'illustre l'exemple suivant :  
  
```  
int myInt;  
```  
  
 vous ne pourrez pas l'utiliser tant qu'elle n'aura pas été initialisée.  Vous pouvez initialiser la variable locale avec l'instruction suivante :  
  
```  
myInt = new int();  // Invoke default constructor for int type.  
```  
  
 Cette instruction équivaut à l'instruction suivante :  
  
```  
myInt = 0;         // Assign an initial value, 0 in this example.  
```  
  
 Vous pouvez bien sûr déclarer et initialiser la variable à l'aide d'une seule instruction, comme illustré ci\-dessous :  
  
```  
int myInt = new int();  
```  
  
 \- ou \-  
  
```  
int myInt = 0;  
```  
  
 L'opérateur [new](../../../csharp/language-reference/keywords/new.md) appelle le constructeur par défaut associé au type spécifique, puis assigne la valeur par défaut à la variable.  Dans l'exemple précédent, le constructeur par défaut a assigné la valeur `0` à la variable `myInt`.  Pour plus d'informations sur les valeurs assignées par les constructeurs par défaut appelés, consultez [Tableau des valeurs par défaut](../../../csharp/language-reference/keywords/default-values-table.md).  
  
 Pour les types définis par l'utilisateur, l'opérateur [new](../../../csharp/language-reference/keywords/new.md) permet d'appeler le constructeur par défaut.  Par exemple, l'instruction suivante appelle le constructeur par défaut associé à l'objet `Point` de type struct :  
  
```  
Point p = new Point(); // Invoke default constructor for the struct.  
```  
  
 Après l'appel, le type struct est considéré comme ayant été assigné, c'est\-à\-dire que tous ses membres sont initialisés à leur valeur par défaut respective.  
  
 Pour plus d'informations sur l'opérateur new, consultez [new](../../../csharp/language-reference/keywords/new.md).  
  
 Pour plus d'informations sur les formats des résultats de types numériques, consultez [Tableau des formats des résultats numériques](../../../csharp/language-reference/keywords/formatting-numeric-results-table.md).  
  
## Voir aussi  
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Mots clés C\#](../../../csharp/language-reference/keywords/index.md)   
 [Types](../../../csharp/language-reference/keywords/types.md)   
 [Tableaux de référence des types](../../../csharp/language-reference/keywords/reference-tables-for-types.md)   
 [Types référence](../../../csharp/language-reference/keywords/reference-types.md)