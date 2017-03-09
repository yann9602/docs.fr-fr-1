---
title: "Value Types and Reference Types | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "reference data types"
  - "reference types"
  - "value types"
  - "value data types"
  - "types [Visual Basic]"
  - "data types [Visual Basic], value types"
  - "data types [Visual Basic], reference types"
ms.assetid: fc82ce15-5a40-4c5c-a1e1-a556830e7391
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 14
---
# Value Types and Reference Types
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

En Visual Basic, les types de données sont implémentés en fonction de leur classification.  Les types de données [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] peuvent être classés selon qu'une variable d'un certain type stocke ses propres données ou un pointeur vers les données.  Si elle enregistre ses propres données, il s'agit d'un *type valeur* ; si elle contient un pointeur vers les données stockées à un autre endroit de la mémoire, il s'agit d'un *type référence*.  
  
## Types valeur  
 Un type de données est un *type valeur* s'il contient des données dans l'espace qui lui est alloué en mémoire.  Les types valeur incluent les éléments suivants :  
  
-   Tous les types de données numériques  
  
-   `Boolean`, `Char` et `Date`  
  
-   Toutes les structures, même si leurs membres sont des types référence  
  
-   Les énumérations, dans la mesure où leur type sous\-jacent est toujours `SByte`, `Short`, `Integer`, `Long`, `Byte`, `UShort`, `UInteger` ou `ULong`.  
  
 chaque structure est un type valeur, même si elle contient des membres de type référence.  Pour cette raison, les types valeur comme `Char` et l' `Integer` sont implémentés par les structures .NET Framework.  
  
 Vous pouvez déclarer un type valeur en utilisant le mot clé réservé \(par exemple, `Decimal`\).  Vous pouvez également utiliser le mot clé `New` pour initialiser un type valeur.  Cela s'avère particulièrement utile si le type possède un constructeur qui accepte des paramètres.  Le constructeur <xref:System.Decimal.%23ctor%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%2CSystem.Byte%29> en constitue un exemple ; il génère une nouvelle valeur `Decimal` à partir des parties fournies.  
  
## Types référence  
 Un *type référence* contient un pointeur vers un autre emplacement en mémoire contenant les données.  Les types référence incluent les éléments suivants :  
  
-   `String`  
  
-   Tous les tableaux, même si leurs éléments sont des types valeur  
  
-   Les types classe, tels que <xref:System.Windows.Forms.Form>.  
  
-   Délégués  
  
 Une classe est un *type référence*.  C'est pour cette raison que les types référence comme `Object` et `String` sont pris en charge par les classes [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort-md.md)].  Notez que chaque tableau est un type référence, même si ses membres sont des types valeur.  
  
 Étant donné que chaque type référence représente une classe sous\-jacente.NET Framework, vous devez utiliser le mot clé de [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md) lorsque vous l'initialisez.  L'instruction suivante initialise un tableau.  
  
```  
Dim totals() As Single = New Single(8) {}  
```  
  
## Éléments qui ne sont pas des types  
 Les éléments de programmation suivants ne sont pas considérés comme des types car vous ne pouvez les spécifier comme type de données pour un élément déclaré :  
  
-   Espaces de noms  
  
-   Modules  
  
-   Événements  
  
-   Propriétés et procédures  
  
-   Variables, constantes et champs  
  
## Utilisation du type de données Object  
 Vous pouvez assigner au choix un type référence ou un type valeur à une variable de type de données `Object`.  Une variable `Object` contient toujours un pointeur vers les données, jamais les données elles\-mêmes.  Toutefois, si vous assignez un type valeur à une variable `Object`, elle se comporte comme si elle contenait ses propres données.  Pour plus d'informations, consultez [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md).  
  
 Vous pouvez déterminer si une variable d' `Object` fonctionne comme un type référence ou un type valeur en la passant à la méthode d' <xref:Microsoft.VisualBasic.Information.IsReference%2A> dans la classe d' <xref:Microsoft.VisualBasic.Information> de l'espace de noms d' <xref:Microsoft.VisualBasic?displayProperty=fullName> .  <xref:Microsoft.VisualBasic.Information.IsReference%2A?displayProperty=fullName> retourne la valeur `True` si le contenu de la variable `Object` représente un type référence.  
  
## Voir aussi  
 [Nullable Value Types](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)   
 [Type Conversions in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)   
 [Structure Statement](../../../../visual-basic/language-reference/statements/structure-statement.md)   
 [Efficient Use of Data Types](../../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)   
 [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md)   
 [Types de données](../../../../visual-basic/programming-guide/language-features/data-types/index.md)