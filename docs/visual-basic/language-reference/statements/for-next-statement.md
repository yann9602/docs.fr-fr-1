---
title: "For...Next, instruction (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Step"
  - "vb.Next"
  - "vb.To"
  - "vb.for"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "boucles infinies"
  - "mot clé Next, instructions For...Next"
  - "mot clé For [Visual Basic], instructions For...Next"
  - "mot clé Step, instructions For...Next"
  - "surcharge d’opérateur, instruction For...Next"
  - "mot clé To, instructions For...Next"
  - "boucles infinies"
  - "boucles, infinies"
  - "instructions, répéter"
  - "instruction Next, For...Next"
  - "instructions For...Next"
  - "structures de boucle, For...Next"
  - "boucles, infinies"
  - "instruction Exit, instructions For...Next"
  - "For (instruction)"
ms.assetid: f5fc0d51-67ce-4c36-9f09-31c9a91c94e9
caps.latest.revision: 64
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 64
---
# For...Next, instruction (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Répète un groupe d'instructions un nombre spécifié de fois.  
  
## Syntaxe  
  
```  
For counter [ As datatype ] = start To end [ Step step ]  
    [ statements ]  
    [ Continue For ]  
    [ statements ]  
    [ Exit For ]  
    [ statements ]  
Next [ counter ]  
```  
  
## Composants  
  
|Élément|Description|  
|-------------|-----------------|  
|`counter`|Requis dans l'instruction `For`.  Variable numérique.  Variable de contrôle de la boucle.  Pour plus d'informations, consultez [Argument de compteur](#BKMK_Counter) plus loin dans cette rubrique.|  
|`datatype`|Optionnel.  Type de données de `counter`.  Pour plus d'informations, consultez [Argument de compteur](#BKMK_Counter) plus loin dans cette rubrique.|  
|`start`|Requis.  Expression numérique.  Valeur initiale de `counter`.|  
|`end`|Requis.  Expression numérique.  Valeur finale de `counter`.|  
|`step`|Optionnel.  Expression numérique.  Valeur d'incrémentation de `counter` à chaque itération de la boucle.|  
|`statements`|Optionnel.  Une ou plusieurs instructions entre `For` et `Next` à exécuter le nombre de fois spécifié.|  
|`Continue For`|Optionnel.  Transfère le contrôle à l'itération suivante de la boucle.|  
|`Exit For`|Optionnel.  Transfert le contrôle hors de la boucle `For`.|  
|`Next`|Requis.  Termine la définition de la boucle `For`.|  
  
> [!NOTE]
>  Le mot clé d' `To` est utilisé dans cette instruction pour spécifier l'intervalle pour le compteur.  Vous pouvez également utiliser ce mot clé dans [Select...Case Statement](../../../visual-basic/language-reference/statements/select-case-statement.md) et dans les déclarations de tableau.  Pour plus d'informations sur les déclarations de tableau, consultez [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md).  
  
## Exemples simples  
 Vous utilisez une structure d' `For`…`Next` lorsque vous voulez répéter un jeu d'instructions un nombre de fois.  
  
 Dans l'exemple suivant, la variable d' `index` démarre avec une valeur de 1 et est incrémenté à chaque itération de la boucle, en terminant après que la valeur des portées 5. d' `index` .  
  
 [!code-vb[VbVbalrStatements#111](../../../visual-basic/language-reference/error-messages/codesnippet/visualbasic/for-next-statement_1.vb)]  
  
 Dans l'exemple suivant, la variable d' `number` commence à 2 et est réduite par 0,25 sur chaque itération de la boucle, en terminant après que la valeur des portées 0 d' `number` .  L'argument d' `Step` d' `-.25` réduit la valeur de 0,25 sur chaque itération de la boucle.  
  
 [!code-vb[VbVbalrStatements#112](../../../visual-basic/language-reference/error-messages/codesnippet/visualbasic/for-next-statement_2.vb)]  
  
> [!TIP]
>  [While...End While Statement](../../../visual-basic/language-reference/statements/while-end-while-statement.md) ou [Do...Loop Statement](../../../visual-basic/language-reference/statements/do-loop-statement.md) convient lorsque vous ne connaissez pas à l'avance le nombre de fois pour exécuter les instructions de la boucle.  Toutefois, si vous devez exécuter la boucle un certain nombre de fois, il est préférable d'utiliser `For`...`Next`.  Vous déterminez le nombre d'itérations lorsque vous entrez la boucle pour la première fois.  
  
## Imbrication de boucles  
 Vous pouvez imbriquer les boucles `For` en plaçant une boucle à l'intérieur d'une autre.  L'exemple suivant illustre des structures `For`...`Next` imbriquées avec différentes valeurs d'étape.  La boucle externe crée une chaîne pour chaque itération de la boucle.  La boucle interne décrémente une variable de compteur de boucle pour chaque itération de la boucle.  
  
 [!code-vb[VbVbalrStatements#113](../../../visual-basic/language-reference/error-messages/codesnippet/visualbasic/for-next-statement_3.vb)]  
  
 Lorsque les boucles d'imbrication, chaque aller\-retour doivent avoir une seule variable d' `counter` .  
  
 Vous pouvez également imbriquer divers types de structures de contrôle l'un dans l'autre.  Pour plus d'informations, consultez [Nested Control Structures](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).  
  
## Quittez pour & continuer pour  
 L'instruction d' `Exit For` quitte immédiatement la boucle et transfère le contrôle d' `For`…`Next` à l'instruction qui suit l'instruction d' `Next` .  
  
 L'instruction `Continue For` transfère immédiatement le contrôle vers l'itération suivante de la boucle.  Pour plus d'informations, consultez [Continue Statement](../../../visual-basic/language-reference/statements/continue-statement.md).  
  
 L'exemple ci\-dessous illustre l'utilisation des instructions `Continue For` et `Exit For`.  
  
 [!code-vb[VbVbalrStatements#115](../../../visual-basic/language-reference/error-messages/codesnippet/visualbasic/for-next-statement_4.vb)]  
  
 Vous pouvez placer n'importe quel nombre d'instructions `Exit For` dans une boucle `For`...`Next`.  Utilisée dans des boucles `For`…`Next` imbriquées, l'instruction `Exit For` quitte la boucle la plus profonde et transfère le contrôle au niveau d'imbrication supérieur suivant.  
  
 `Exit For` est souvent une fois que vous évaluiez une condition \(par exemple, dans une structure d' `If`…`Then`…`Else` \).  Vous pouvez utiliser `Exit For` pour les conditions suivantes :  
  
-   La poursuite de l'itération est inutile ou impossible.  Une valeur ou par une demande d'arrêt peut créer cette condition.  
  
-   Une instruction d' `Try`…`Catch`…`Finally` intercepte une exception.  Vous pouvez utiliser `Exit For` à la fin du bloc `Finally`.  
  
-   Vous avez une boucle sans fin, qui est une boucle qui peut exécuter différents ou même infini nombre de fois.  Si vous détectez une telle condition, vous pouvez utiliser `Exit For` pour abandonner la boucle.  Pour plus d'informations, consultez [Do...Loop Statement](../../../visual-basic/language-reference/statements/do-loop-statement.md).  
  
## Implémentation technique  
 Lorsque la boucle `For`...`Next` commence, Visual Basic évalue `start`, `end` et `step`.  Visual Basic prend les valeurs uniquement à ce stade puis assigne `start` à `counter`.  Avant que le bloc d'instructions fonctionne, Visual Basic compare `counter` à `end`.  Si `counter` est déjà supérieure à la valeur d' `end` \(ou le plus petit si `step` est négatif\), des fins de boucle d' `For` et le contrôle passe à l'instruction qui suit l'instruction d' `Next` .  Sinon, le bloc d'instructions fonctionne.  
  
 Chaque fois que Visual Basic rencontre l'instruction `Next`, il incrémente `counter` de la valeur de `step` et retourne à l'instruction `For`.  Il compare de nouveau `counter` à `end` et exécute à nouveau le bloc ou quitte la boucle selon le résultat.  Ce processus continue jusqu'à ce que `counter` passe `end` ou qu'une instruction `Exit For` soit rencontrée.  
  
 La boucle ne s'arrête pas jusqu'à ce qu' `counter` être passé `end`.  Si `counter` est égal à `end`, la boucle continue.  La comparaison qui détermine l'exécution du bloc est `counter` \<\= `end` si `step` est positif et `counter` \>\= `end` si `step` est négatif.  
  
 Si vous modifiez la valeur d' `counter` alors qu'à l'intérieur d'une boucle, il peut être plus difficile à lire et à déboguer votre code.  Modifiant la valeur d' `start`, `end`, ou `step` n'affecte pas les valeurs d'itération qui ont été déterminées lorsque la boucle a été écrite la première fois.  
  
 Si vous emboîtez des boucles, le compilateur signale une erreur s'il rencontre l'instruction d' `Next` d'un niveau d'imbrication externe avant l'instruction d' `Next` d'un niveau interne.  Toutefois, le compilateur peut détecter cette erreur de chevauchement uniquement si vous spécifiez `counter` dans chaque instruction `Next`.  
  
### Argument d'étape  
 La valeur de `step` peut être positive ou négative.  Ce paramètre détermine la boucle de traitement selon le tableau suivant :  
  
|**Valeur de step**|**Condition d'exécution de la boucle**|  
|------------------------|--------------------------------------------|  
|Positive ou zéro|`counter` \<\= `end`|  
|Négatif|`counter` \>\= `end`|  
  
 La valeur par défaut de `step` est 1.  
  
###  <a name="BKMK_Counter"></a> Argument de compteur  
 Le tableau suivant indique si `counter` définit une variable locale qui est limitée à la boucle entière d' `For…Next` .  Cette détermination dépend de si `datatype` est présent et si `counter` est déjà défini.  
  
|`datatype` présent \-t\-elle ?|`counter` \-t\-elle déjà défini ?|Résultat \(si `counter` définit une variable locale qui est limitée à la boucle entière d' `For...Next` \)|  
|------------------------------------|---------------------------------------|----------------------------------------------------------------------------------------------------------------|  
|Non|Oui|Non, car `counter` est déjà défini.  Si la portée d' `counter` n'est pas locale à la procédure, un avertissement de compilation se produit.|  
|Non|Non|Oui.  Le type de données est déduit d' `start`, d' `end`, et les expressions d' `step` .  Pour plus d'informations sur l'inférence de type, consultez [Option Infer Statement](../../../visual-basic/language-reference/statements/option-infer-statement.md) et le [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).|  
|Oui|Oui|Oui, mais uniquement si la variable existante d' `counter` est définie en dehors de la procédure.  Cette variable reste distincte.  Si la portée de la variable existante d' `counter` est locale à la procédure, une erreur de compilation se produit.|  
|Oui|Non|Oui.|  
  
 Le type de données d' `counter` détermine le type de l'itération, qui doit être l'un des types suivants :  
  
-   `Byte`, `SByte`, `UShort`, `Short`, `UInteger`, `Integer`, `ULong`, `Long`, `Decimal`, `Single` ou `Double`.  
  
-   Énumération que vous déclarez à l'aide d'une [Enum Statement](../../../visual-basic/language-reference/statements/enum-statement.md).  
  
-   Élément `Object`.  
  
-   Type `T` qui a les opérateurs suivants, où `B` est un type qui peut être utilisé dans une expression `Boolean`.  
  
     `Public Shared Operator >= (op1 As T, op2 As T) As B`  
  
     `Public Shared Operator <= (op1 As T, op2 As T) As B`  
  
     `Public Shared Operator - (op1 As T, op2 As T) As T`  
  
     `Public Shared Operator + (op1 As T, op2 As T) As T`  
  
 Vous pouvez éventuellement spécifier la variable d' `counter` dans l'instruction d' `Next` .  Cette syntaxe améliore la lisibilité de votre programme, surtout si vous avez des boucles imbriquées d' `For` .  Vous devez spécifier la variable qui apparaît dans l'instruction correspondante d' `For` .  
  
 Les expressions `start`, `end` et `step` peuvent avoir pour valeur tout type de données qui s'étend au type de `counter`.  Si vous utilisez un type défini par l'utilisateur pour `counter`, vous devrez peut\-être définir l'opérateur de conversion d' `CType` pour convertir les types d' `start`, d' `end`, ou d' `step` au type d' `counter`.  
  
## Exemple  
 L'exemple suivant supprime tous les éléments d'une liste générique.  Au lieu de [For Each...Next, instruction](../../../visual-basic/language-reference/statements/for-each-next-statement.md), l'exemple illustre une instruction d' `For`…`Next` qui itère dans l'ordre décroissant.  L'exemple utilise cette technique car la méthode d' `removeAt` fait avoir des éléments après l'élément supprimé une valeur d'index la plus basse.  
  
 [!code-vb[VbVbalrStatements#114](../../../visual-basic/language-reference/error-messages/codesnippet/visualbasic/for-next-statement_5.vb)]  
  
## Exemple  
 L'exemple suivant effectue une itération au sein d'une énumération qui est déclarée à l'aide de [Enum Statement](../../../visual-basic/language-reference/statements/enum-statement.md).  
  
 [!code-vb[VbVbalrStatements#116](../../../visual-basic/language-reference/error-messages/codesnippet/visualbasic/for-next-statement_6.vb)]  
  
## Exemple  
 Dans l'exemple suivant, les paramètres d'instruction utilisent une classe ayant des surcharges d'opérateurs pour les opérateurs `+`, `-`, `>=` et `<=`.  
  
 [!code-vb[VbVbalrStatements#117](../../../visual-basic/language-reference/error-messages/codesnippet/visualbasic/for-next-statement_7.vb)]  
  
## Voir aussi  
 <xref:System.Collections.Generic.List%601>   
 [Loop Structures](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)   
 [While...End While Statement](../../../visual-basic/language-reference/statements/while-end-while-statement.md)   
 [Do...Loop Statement](../../../visual-basic/language-reference/statements/do-loop-statement.md)   
 [Nested Control Structures](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)   
 [Exit Statement](../../../visual-basic/language-reference/statements/exit-statement.md)   
 [Collections](../Topic/Collections%20\(C%23%20and%20Visual%20Basic\).md)