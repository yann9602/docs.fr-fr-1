---
title: "Structure of a Visual Basic Program | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "conditional compilation, Visual Basic"
  - "program structure, Visual Basic"
  - "procedures, structure"
  - "Visual Basic code, program structure"
ms.assetid: ad0c6531-d762-4c77-a700-de16b07b6119
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Structure of a Visual Basic Program
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Un programme [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] est développé à partir de blocs de construction standard.  Une *solution* comprend un ou plusieurs projets.  Un *projet*, à son tour, peut contenir un ou plusieurs assemblys.  Chaque *assembly* est compilé à partir d'un ou de plusieurs fichiers sources.  Un *fichier source* fournit la définition et l'implémentation des classes, structures, modules et interfaces qui contiennent l'ensemble de votre code.  
  
 Pour plus d'informations sur ces blocs de construction d'un programme [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], consultez [Projets et solutions](/visual-studio/ide/solutions-and-projects-in-visual-studio) et [Assemblys et le Global Assembly Cache](../Topic/Assemblies%20and%20the%20Global%20Assembly%20Cache%20\(C%23%20and%20Visual%20Basic\).md).  
  
## Éléments de programmation au niveau du fichier  
 Lorsque vous lancez un projet ou un fichier et ouvrez l'éditeur de code, vous constatez que figurent déjà dans cette fenêtre quelques lignes de code disposées dans le bon ordre.  Tout code que vous créez doit respecter l'ordre suivant :  
  
1.  instructions `Option` ;  
  
2.  instructions `Imports` ;  
  
3.  instructions `Namespace` et éléments au niveau de l'espace de noms.  
  
 Si vous entrez les instructions dans un ordre différent, vous risquez de créer des erreurs de compilation.  
  
 Un programme peut également contenir des instructions de compilation conditionnelles.  Vous pouvez les intercaler dans le fichier source entre les instructions de la séquence précédente.  
  
### Instructions Options  
 Les instructions `Option` définissent les règles à suivre pour l'écriture du code ultérieur, ce qui permet d'éviter les erreurs de syntaxe et de logique.  L'instruction [Option Explicit Statement](../../../visual-basic/language-reference/statements/option-explicit-statement.md) vérifie que toutes les variables sont déclarées et orthographiées correctement, ce qui réduit le temps de débogage.  [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md) contribue à réduire les erreurs de logique et la perte de données susceptibles de se produire lorsque vous travaillez avec des variables de types de données différents.  [Option Compare Statement](../../../visual-basic/language-reference/statements/option-compare-statement.md) spécifie la manière dont les chaînes sont comparées les unes aux autres, en fonction de leurs valeurs `Binary` ou `Text`.  
  
### Instructions Imports  
 Vous pouvez inclure une [Imports Statement \(.NET Namespace and Type\)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) pour importer des noms définis à l'extérieur de votre projet.  Une instruction `Imports` permet à votre code de référencer des classes et d'autres types définis à l'intérieur de l'espace de noms importé sans devoir les qualifier.  Vous pouvez utiliser autant d'instructions `Imports` que nécessaire.  Pour plus d'informations, consultez [References and the Imports Statement](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md).  
  
### Instructions Namespace  
 Les espaces de noms vous aident à organiser et à classer vos éléments de programmation pour faciliter leur regroupement et leur accès.  Vous utilisez [Namespace Statement](../../../visual-basic/language-reference/statements/namespace-statement.md) pour classer les instructions suivantes dans un espace de noms particulier.  Pour plus d'informations, consultez [Espaces de noms dans Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md).  
  
### Instructions de compilation conditionnelle  
 Les instructions de compilation conditionnelles peuvent apparaître quasiment n'importe où dans votre fichier source.  Elles provoquent l'inclusion ou l'exclusion de parties de votre code au moment de la compilation, en fonction de certaines conditions.  Vous pouvez également les utiliser pour déboguer votre application, car le code conditionnel s'exécute uniquement en mode débogage.  Pour plus d'informations, consultez [Conditional Compilation](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md).  
  
## Éléments de programmation au niveau de l'espace de noms  
 Les classes, les structures et les modules contiennent l'ensemble du code de votre fichier source.  Ce sont des éléments *au niveau de l'espace de noms*, qui peuvent apparaître dans un espace de noms ou au niveau du fichier source.  Ils contiennent les déclarations de tous les autres éléments de programmation.  Les interfaces, qui définissent les signatures d'élément mais ne fournissent aucune implémentation, apparaissent également au niveau du module.  Pour plus d'informations sur les éléments au niveau du module, consultez les rubriques suivantes :  
  
-   [Class Statement](../../../visual-basic/language-reference/statements/class-statement.md)  
  
-   [Structure Statement](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
-   [Module Statement](../../../visual-basic/language-reference/statements/module-statement.md)  
  
-   [Interface Statement](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 Les éléments de données au niveau de l'espace de noms sont les énumérations et les délégués.  
  
## Éléments de programmation au niveau du module  
 Les procédures, les opérateurs, les propriétés et les événements sont les seuls éléments de programmation qui peuvent contenir du code exécutable \(instructions qui exécutent des opérations au moment de l'exécution\).  Ce sont les éléments *au niveau du module* de votre programme.  Pour plus d'informations sur les éléments au niveau de la procédure, consultez les rubriques suivantes :  
  
-   [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md)  
  
-   [Sub Statement](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
-   [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
-   [Operator Statement](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
-   [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md)  
  
-   [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 Les éléments de données au niveau du module sont les variables, les constantes, les énumérations et les délégués.  
  
## Éléments de programmation au niveau de la procédure  
 La majeure partie du contenu des éléments *au niveau de la procédure* sont des instructions exécutables qui constituent le code d'exécution de votre programme.  Tout le code exécutable doit être contenu dans une procédure \(`Function`, `Sub`, `Operator`, `Get`, `Set`, `AddHandler`, `RemoveHandler`, `RaiseEvent`\).  Pour plus d'informations, consultez [Statements](../../../visual-basic/programming-guide/language-features/statements.md).  
  
 Les éléments de données au niveau de la procédure se limitent aux variables et aux constantes locales.  
  
## Procédure Main  
 La procédure `Main` est le premier code à exécuter lorsque votre application a été chargée.  `Main` sert de point de départ et de contrôle général de l'application.  Il existe quatre types de `Main` :  
  
-   `Sub Main()`  
  
-   `Sub Main(ByVal cmdArgs() As String)`  
  
-   `Function Main() As Integer`  
  
-   `Function Main(ByVal cmdArgs() As String) As Integer`  
  
 `Sub Main()` est le type le plus courant de cette procédure.  Pour plus d'informations, consultez [Main Procedure in Visual Basic](../../../visual-basic/programming-guide/program-structure/main-procedure.md).  
  
## Voir aussi  
 [NIB: Visual Basic Version of Hello, World](http://msdn.microsoft.com/fr-fr/9d030b60-e148-4366-a462-69532f02294c)   
 [Main Procedure in Visual Basic](../../../visual-basic/programming-guide/program-structure/main-procedure.md)   
 [Visual Basic Naming Conventions](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)   
 [Visual Basic Limitations](../../../visual-basic/programming-guide/program-structure/limitations.md)