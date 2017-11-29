---
title: Structure d'un programme Visual Basic
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- conditional compilation [Visual Basic], Visual Basic
- program structure [Visual Basic], Visual Basic
- procedures [Visual Basic], structure
- Visual Basic code, program structure
ms.assetid: ad0c6531-d762-4c77-a700-de16b07b6119
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 136be5e2eab3ed0226e0ca471ee1d84cdc7a52d1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="structure-of-a-visual-basic-program"></a>Structure d'un programme Visual Basic
A [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] programme est développé à partir de blocs de construction standard. A *solution* comprend un ou plusieurs projets. A *projet* à son tour peut contenir un ou plusieurs assemblys. Chaque *assembly* est compilé à partir d’un ou plusieurs fichiers de code source. A *fichier source* fournit la définition et l’implémentation de classes, structures, modules et interfaces qui contiennent l’ensemble de votre code.  
  
 Pour plus d’informations sur ces blocs de construction d’un [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] du programme, consultez [Solutions et projets](/visualstudio/ide/solutions-and-projects-in-visual-studio) et [assemblys et le Global Assembly Cache](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md).  
  
## <a name="file-level-programming-elements"></a>Éléments de programmation au niveau des fichiers  
 Lorsque vous démarrez un projet ou un fichier et que vous ouvrez l’éditeur de code, vous consultez du code déjà en place et dans l’ordre approprié. Tout code que vous écrivez doit respecter la séquence suivante :  
  
1.  `Option`instructions  
  
2.  `Imports`instructions  
  
3.  `Namespace`instructions et des éléments au niveau de l’espace de noms  
  
 Si vous entrez les instructions dans un ordre différent, peuvent entraîner des erreurs de compilation.  
  
 Un programme peut également contenir des instructions de compilation conditionnelle. Vous pouvez les intercaler dans le fichier source entre les instructions de la séquence précédente.  
  
### <a name="option-statements"></a>Instructions option  
 `Option`les instructions définissent les règles pour le code suivant, permettent d’éviter les erreurs de syntaxe et de logique. Le [Option Explicit, instruction](../../../visual-basic/language-reference/statements/option-explicit-statement.md) garantit que toutes les variables sont déclarées et correctement orthographiés, ce qui réduit le temps de débogage. Le [Option Strict, instruction](../../../visual-basic/language-reference/statements/option-strict-statement.md) permet de minimiser la perte de données et les erreurs de logique qui peut se produire lorsque vous travaillez avec des variables de différents types de données. Le [instruction Option Compare](../../../visual-basic/language-reference/statements/option-compare-statement.md) spécifie les façon dont les chaînes sont comparées aux autres, en fonction de leur `Binary` ou `Text` valeurs.  
  
### <a name="imports-statements"></a>Instructions Imports  
 Vous pouvez inclure une [Imports, instruction (.NET Namespace et Type)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) pour importer des noms définis à l’extérieur de votre projet. Un `Imports` instruction permet à votre code faire référence à des classes et d’autres types définis dans l’espace de noms importé sans devoir les qualifier. Vous pouvez utiliser autant `Imports` instructions selon le cas. Pour plus d’informations, consultez [références et l’instruction Imports](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md).  
  
### <a name="namespace-statements"></a>Instructions Namespace  
 Espaces de noms vous aident à organisez et classer vos éléments de programmation pour faciliter leur regroupement et l’accès à. Vous utilisez la [Namespace instruction](../../../visual-basic/language-reference/statements/namespace-statement.md) pour classer les instructions suivantes dans un espace de noms particulier. Pour plus d’informations, consultez l’article [Espaces de noms dans Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md).  
  
### <a name="conditional-compilation-statements"></a>Instructions de Compilation conditionnelle  
 Instructions de compilation conditionnelle peuvent apparaître presque n’importe où dans votre fichier source. Ils empêchent les parties de votre code pour être incluse ou exclue à la compilation en fonction de certaines conditions. Vous pouvez également utiliser les pour déboguer votre application, car le code conditionnel s’exécute uniquement en mode débogage. Pour plus d’informations, consultez [Compilation conditionnelle](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md).  
  
## <a name="namespace-level-programming-elements"></a>Éléments de programmation au niveau du Namespace  
 Classes, structures et les modules contiennent tout le code dans votre fichier source. Ils sont *au niveau de l’espace de noms* éléments, qui peuvent apparaître dans un espace de noms ou au niveau du fichier source. Ils contiennent les déclarations de tous les autres éléments de programmation. Les interfaces, qui définissent les signatures d’élément mais ne fournissent aucune implémentation, apparaissent également au niveau du module. Pour plus d’informations sur les éléments au niveau du module, consultez les rubriques suivantes :  
  
-   [Class (instruction)](../../../visual-basic/language-reference/statements/class-statement.md)  
  
-   [Structure (instruction)](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
-   [Module (instruction)](../../../visual-basic/language-reference/statements/module-statement.md)  
  
-   [Interface (instruction)](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 Les éléments de données au niveau de l’espace de noms sont les énumérations et délégués.  
  
## <a name="module-level-programming-elements"></a>Éléments de programmation au niveau du module  
 Les procédures, les opérateurs, les propriétés et les événements sont les seuls éléments de programmation qui peuvent contenir du code exécutable (instructions qui effectuent des actions en cours d’exécution). Ils sont le *au niveau du module* éléments de votre programme. Pour plus d’informations sur les éléments de niveau de la procédure, consultez les rubriques suivantes :  
  
-   [Function (instruction)](../../../visual-basic/language-reference/statements/function-statement.md)  
  
-   [Sub (instruction)](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
-   [Declare (instruction)](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
-   [Operator (instruction)](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
-   [Property (instruction)](../../../visual-basic/language-reference/statements/property-statement.md)  
  
-   [Event (instruction)](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 Les éléments de données au niveau du module sont les variables, de constantes, énumérations et délégués.  
  
## <a name="procedure-level-programming-elements"></a>Éléments de programmation au niveau de la procédure  
 La plupart du contenu de *au niveau de la procédure* éléments sont des instructions exécutables qui constituent le code d’exécution de votre programme. Tout le code exécutable doit être dans une procédure (`Function`, `Sub`, `Operator`, `Get`, `Set`, `AddHandler`, `RemoveHandler`, `RaiseEvent`). Pour plus d’informations, consultez [Instructions](../../../visual-basic/programming-guide/language-features/statements.md).  
  
 Éléments de données au niveau de la procédure sont limités à des constantes et des variables locales.  
  
## <a name="the-main-procedure"></a>La procédure principale  
 Le `Main` procédure est le premier code à exécuter lorsque votre application a été chargée. `Main`sert de point de départ et de contrôle global de votre application. Il existe quatre types de `Main`:  
  
-   `Sub Main()`  
  
-   `Sub Main(ByVal cmdArgs() As String)`  
  
-   `Function Main() As Integer`  
  
-   `Function Main(ByVal cmdArgs() As String) As Integer`  
  
 Le plus courant de cette procédure est `Sub Main()`. Pour plus d’informations, consultez [procédure Main dans Visual Basic](../../../visual-basic/programming-guide/program-structure/main-procedure.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Procédure Main dans Visual Basic](../../../visual-basic/programming-guide/program-structure/main-procedure.md)  
 [Conventions d’affectation de noms de Visual Basic](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)  
 [Limitations de Visual Basic](../../../visual-basic/programming-guide/program-structure/limitations.md)
