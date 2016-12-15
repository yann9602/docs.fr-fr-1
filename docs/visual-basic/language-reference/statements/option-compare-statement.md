---
title: "Option Compare Statement | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.Compare"
  - "vb.OptionCompare"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "case sensitivity, Option Compare statement"
  - "Compare keyword"
  - "binary comparison"
  - "strings [Visual Basic], returning from functions"
  - "binary comparison, Option Compare statement"
  - "strings [Visual Basic], comparing"
  - "string comparison [Visual Basic], Option Compare statement"
  - "Text keyword, Option Compare statement"
  - "Binary keyword, Option Compare statement"
  - "string comparison [Visual Basic], sorting data"
  - "Option Compare statement"
  - "text [Visual Basic], comparing"
ms.assetid: 54e8eeeb-3b0d-4fb9-acce-fbfbd5975f6e
caps.latest.revision: 37
caps.handback.revision: 37
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Option Compare Statement
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Déclare la méthode de comparaison par défaut à utiliser lors de la comparaison de données de type chaîne.  
  
## Syntaxe  
  
```  
Option Compare { Binary | Text }  
```  
  
## Composants  
  
|||  
|-|-|  
|Terme|Définition|  
|`Binary`|Facultatif.  Se traduit par des comparaisons de chaînes basées sur un ordre de tri dérivé des représentations binaires internes des caractères.<br /><br /> Ce type de comparaison est utile surtout si les chaînes peuvent contenir des caractères qui ne doivent ne pas être interprétées comme du texte.  Dans ce cas, il convient de ne pas fausser les comparaisons avec des équivalences alphabétiques comme, par exemple, quand la casse n'est pas respectée.|  
|`Text`|Facultatif.  Se traduit par des comparaisons de chaînes basées sur un ordre de tri de texte sans respect de la casse déterminé par les paramètres régionaux de votre système.<br /><br /> Ce type de comparaison est utile si vos chaînes contiennent toutes des caractères de texte et si vous voulez les comparer en prenant en compte les équivalences alphabétiques, c'est\-à\-dire des lettres très proches ou de casse différente.  Par exemple, vous pouvez faire en sorte que les caractères `A` et `a` soient considérés comme identiques et que les caractères `Ä` et `ä` précèdent `B` et `b`.|  
  
## Notes  
 Si elle est utilisée, l'instruction `Option Compare` doit apparaître dans un fichier avant toute autre instruction de code source.  
  
 L'instruction `Option Compare` permet de spécifier la méthode de comparaison de chaînes \(`Binary` ou `Text`\).  La méthode de comparaison de texte par défaut est `Binary`.  
  
 Une comparaison de type `Binary` permet de comparer la valeur Unicode numérique de chaque caractère dans chaque chaîne.  Une comparaison de type `Text` permet de comparer chaque caractère Unicode selon sa signification lexicale dans la culture actuelle.  
  
 Dans Microsoft Windows, l'ordre de tri est déterminé par la page de code.  Pour plus d'informations, consultez [Pages de codes](/visual-cpp/c-runtime-library/code-pages).  
  
 Dans l'exemple suivant, les caractères de la page de codes Anglais\/Européen \(ANSI 1252\) sont triés à l'aide de `Option Compare Binary`, qui génère un ordre de tri binaire standard.  
  
 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`  
  
 Quand les mêmes caractères d'une même page de codes sont triés à l'aide de `Option Compare Text`, l'ordre de tri de texte suivant est généré.  
  
 `(A=a) < (À = à) < (B=b) < (E=e) < (Ê = ê) < (Z=z) < (Ø = ø)`  
  
## En l'absence d'instruction Option Compare  
 Si le code source ne contient pas d'instruction `Option Compare`, la définition de **Option Compare** dans la [Page Compiler, Concepteur de projets \(Visual Basic\)](/visual-studio/ide/reference/compile-page-project-designer-visual-basic) est utilisée.  Si vous utilisez le compilateur de ligne de commande, le paramétrage spécifié par l'option de compilateur [\/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md) est utilisé.  
  
 [!INCLUDE[note_settings_general](../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
#### Pour définir Option Compare dans l'IDE  
  
1.  Dans l'**Explorateur de solutions**, sélectionnez un projet.  Dans le menu **Projet**, cliquez sur **Propriétés**.  Pour plus d'informations, consultez [NIB: Managing Project Properties with the Project Designer](http://msdn.microsoft.com/fr-fr/983f3c18-832f-4666-afec-74b716ff3e0e).  
  
2.  Cliquez sur l'onglet **Compiler**.  
  
3.  Définissez la valeur dans la zone **Option Compare**.  
  
 Quand vous créez un projet, le paramètre **Option Compare** de l'onglet **Compiler** reprend la définition de **Option Compare** dans la boîte de dialogue **Options**.  Pour modifier ce paramètre, dans le menu **Outils**, cliquez sur **Options**.  Dans la boîte de dialogue **Options**, développez **Projets et solutions**, puis cliquez sur **Valeurs par défaut VB**.  Le paramètre par défaut initial dans **Valeurs par défaut VB** est **Binaire**.  
  
#### Pour définir Option Compare sur la ligne de commande  
  
-   Incluez l'option de compilateur [\/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md) dans la commande **vbc**.  
  
## Exemple  
 L'exemple suivant utilise l'instruction `Option Compare` pour définir la comparaison binaire comme méthode de comparaison de chaînes par défaut.  Pour utiliser ce code, supprimez les commentaires de l'instruction `Option Compare Binary` et placez\-la en haut du fichier source.  
  
 [!code-vb[VbVbalrStatements#45](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-compare-statement_1.vb)]  
  
## Exemple  
 L'exemple suivant utilise l'instruction `Option Compare` pour définir l'ordre de tri de texte sans respect de la casse comme méthode de comparaison de chaînes par défaut.  Pour utiliser ce code, supprimez les commentaires de l'instruction `Option Compare Text` et placez\-la en haut du fichier source.  
  
 [!code-vb[VbVbalrStatements#46](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-compare-statement_2.vb)]  
  
## Voir aussi  
 <xref:Microsoft.VisualBasic.Strings.InStr%2A>   
 <xref:Microsoft.VisualBasic.Strings.InStrRev%2A>   
 <xref:Microsoft.VisualBasic.Strings.Replace%2A>   
 <xref:Microsoft.VisualBasic.Strings.Split%2A>   
 <xref:Microsoft.VisualBasic.Strings.StrComp%2A>   
 [\/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)   
 [Comparison Operators](../../../visual-basic/language-reference/operators/comparison-operators.md)   
 [Comparison Operators in Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)   
 [Like Operator](../../../visual-basic/language-reference/operators/like-operator.md)   
 [Fonctions de chaîne](../../../visual-basic/language-reference/functions/string-functions.md)   
 [Option Explicit Statement](../../../visual-basic/language-reference/statements/option-explicit-statement.md)   
 [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md)