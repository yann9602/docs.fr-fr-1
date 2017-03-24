---
title: Option Compare (instruction) | Documents Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Compare
- vb.OptionCompare
dev_langs:
- VB
helpviewer_keywords:
- case sensitivity, Option Compare statement
- Compare keyword
- binary comparison
- strings [Visual Basic], returning from functions
- binary comparison, Option Compare statement
- strings [Visual Basic], comparing
- string comparison [Visual Basic], Option Compare statement
- Text keyword, Option Compare statement
- Binary keyword, Option Compare statement
- string comparison [Visual Basic], sorting data
- Option Compare statement
- text [Visual Basic], comparing
ms.assetid: 54e8eeeb-3b0d-4fb9-acce-fbfbd5975f6e
caps.latest.revision: 37
author: stevehoag
ms.author: shoag
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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 8b1b077a8818315e52ada6b08ff1e1ced9bbd17c
ms.lasthandoff: 03/13/2017

---
# <a name="option-compare-statement"></a>Option Compare, instruction
Déclare la méthode de comparaison par défaut à utiliser lors de la comparaison de données de type chaîne.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Option Compare { Binary | Text }  
```  
  
## <a name="parts"></a>Composants  
  
|Terme|Définition|  
|---|---|  
|`Binary`|Facultatif. Se traduit par des comparaisons de chaînes basées sur un ordre de tri dérivé des représentations binaires internes des caractères.<br /><br /> Ce type de comparaison est utile surtout si les chaînes peuvent contenir des caractères qui ne doivent ne pas être interprétées comme du texte. Dans ce cas, il convient de ne pas fausser les comparaisons avec des équivalences alphabétiques comme, par exemple, quand la casse n'est pas respectée.|  
|`Text`|Facultatif. Se traduit par des comparaisons de chaînes basées sur un ordre de tri de texte sans respect de la casse déterminé par les paramètres régionaux de votre système.<br /><br /> Ce type de comparaison est utile si vos chaînes contiennent toutes des caractères de texte et si vous voulez les comparer en prenant en compte les équivalences alphabétiques, c'est-à-dire des lettres très proches ou de casse différente. Par exemple, vous pouvez faire en sorte que les caractères `A` et `a` soient considérés comme identiques et que les caractères `Ä` et `ä` précèdent `B` et `b`.|  
  
## <a name="remarks"></a>Remarques  
 Si elle est utilisée, l'instruction `Option Compare` doit apparaître dans un fichier avant toute autre instruction de code source.  
  
 L'instruction `Option Compare` permet de spécifier la méthode de comparaison de chaînes (`Binary` ou `Text`).  La méthode de comparaison de texte par défaut est `Binary`.  
  
 Une comparaison de type `Binary` permet de comparer la valeur Unicode numérique de chaque caractère dans chaque chaîne. Une comparaison de type `Text` permet de comparer chaque caractère Unicode selon sa signification lexicale dans la culture actuelle.  
  
 Dans Microsoft Windows, l'ordre de tri est déterminé par la page de code. Pour plus d’informations, consultez [Pages de codes](https://docs.microsoft.com/cpp/c-runtime-library/code-pages).  
  
 Dans l'exemple suivant, les caractères de la page de codes Anglais/Européen (ANSI 1252) sont triés à l'aide de `Option Compare Binary`, qui génère un ordre de tri binaire standard.  
  
 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`  
  
 Quand les mêmes caractères d'une même page de codes sont triés à l'aide de `Option Compare Text`, l'ordre de tri de texte suivant est généré.  
  
 `(A=a) < (À = à) < (B=b) < (E=e) < (Ê = ê) < (Z=z) < (Ø = ø)`  
  
## <a name="when-an-option-compare-statement-is-not-present"></a>En l'absence d'instruction Option Compare  
 Si le code source ne contient pas une `Option Compare` instruction, le **Option Compare** définition sur le [Page Compiler, Concepteur de projets (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/compile-page-project-designer-visual-basic) est utilisé. Si vous utilisez le compilateur de ligne de commande, le paramètre spécifié par le [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md) option du compilateur est utilisée.  
  
[!INCLUDE[note_settings_general](../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
#### <a name="to-set-option-compare-in-the-ide"></a>Pour définir Option Compare dans l'IDE  
  
1.  Dans **l’Explorateur de solutions**, sélectionnez un projet. Sur le **projet** menu, cliquez sur **propriétés**. Pour plus d’informations, consultez [NIB : gestion des propriétés de projet avec le Concepteur de projet](http://msdn.microsoft.com/en-us/983f3c18-832f-4666-afec-74b716ff3e0e).  
  
2.  Cliquez sur l’onglet **Compiler**.  
  
3.  Définissez la valeur de la **Option Compare** boîte.  
  
 Lorsque vous créez un projet, le **Option Compare** définition sur le **compiler** onglet est définie sur le **Option Compare** dans les **Options** boîte de dialogue. Pour modifier ce paramètre, dans le **outils** menu, cliquez sur **Options**. Dans le **Options** boîte de dialogue, développez **projets et Solutions**, puis cliquez sur **valeurs par défaut VB**. Le paramètre par défaut initial dans **valeurs par défaut VB** est **binaire**.  
  
#### <a name="to-set-option-compare-on-the-command-line"></a>Pour définir Option Compare sur la ligne de commande  
  
-   Inclure les [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md) option du compilateur dans le **vbc** commande.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant utilise l'instruction `Option Compare` pour définir la comparaison binaire comme méthode de comparaison de chaînes par défaut. Pour utiliser ce code, supprimez les commentaires de l'instruction `Option Compare Binary` et placez-la en haut du fichier source.  
  
 [!code-vb[VbVbalrStatements n °&45;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-compare-statement_1.vb)]  
  
## <a name="example"></a>Exemple  
 L'exemple suivant utilise l'instruction `Option Compare` pour définir l'ordre de tri de texte sans respect de la casse comme méthode de comparaison de chaînes par défaut. Pour utiliser ce code, supprimez les commentaires de l'instruction `Option Compare Text` et placez-la en haut du fichier source.  
  
 [!code-vb[VbVbalrStatements&#46;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-compare-statement_2.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualBasic.Strings.InStr%2A></xref:Microsoft.VisualBasic.Strings.InStr%2A>   
 <xref:Microsoft.VisualBasic.Strings.InStrRev%2A></xref:Microsoft.VisualBasic.Strings.InStrRev%2A>   
 <xref:Microsoft.VisualBasic.Strings.Replace%2A></xref:Microsoft.VisualBasic.Strings.Replace%2A>   
 <xref:Microsoft.VisualBasic.Strings.Split%2A></xref:Microsoft.VisualBasic.Strings.Split%2A>   
 <xref:Microsoft.VisualBasic.Strings.StrComp%2A></xref:Microsoft.VisualBasic.Strings.StrComp%2A>   
 [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)   
 [Opérateurs de comparaison](../../../visual-basic/language-reference/operators/comparison-operators.md)   
 [Opérateurs de comparaison en Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)   
 [LIKE (opérateur)](../../../visual-basic/language-reference/operators/like-operator.md)   
 [Fonctions de chaîne](../../../visual-basic/language-reference/functions/string-functions.md)   
 [Option Explicit, instruction](../../../visual-basic/language-reference/statements/option-explicit-statement.md)   
 [Option Strict (instruction)](../../../visual-basic/language-reference/statements/option-strict-statement.md)
