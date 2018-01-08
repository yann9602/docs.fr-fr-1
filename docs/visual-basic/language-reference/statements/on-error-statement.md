---
title: On Error, instruction (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.OnError
helpviewer_keywords:
- Visual Basic code, control flow
- Resume Next statement [Visual Basic]
- errors [Visual Basic], trapping
- error handling, On Error statement
- Next statement [Visual Basic], On Error
- control flow [Visual Basic], branching
- Error keyword [Visual Basic]
- execution [Visual Basic], conditional
- Resume statement [Visual Basic], and On Error statement
- Error statement [Visual Basic], and On Error statement
- GoTo statement [Visual Basic], and On Error statement
- branching [Visual Basic], on error
- conditional statements [Visual Basic], On Error
- On Error statement [Visual Basic], syntax
- On keyword [Visual Basic]
- run-time errors [Visual Basic], handling
- On Error statement [Visual Basic]
ms.assetid: ff947930-fb84-40cf-bd66-1ea219561d5c
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 96baa5d91d0a600b84ed832fb1e3b1ed71a9d89d
ms.sourcegitcommit: 2142a4732bb4ff519b9817db4c24a237b9810d4b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/05/2018
---
# <a name="on-error-statement-visual-basic"></a>On Error, instruction (Visual Basic)
Permet à une routine de gestion des erreurs et spécifie l’emplacement de la routine au sein d’une procédure ; peut également être utilisé pour désactiver une routine de gestion des erreurs.  
  
 Sans la gestion des erreurs, une erreur d’exécution est irrécupérable : un message d’erreur s’affiche et l’exécution s’arrête.  
  
 Chaque fois que possible, nous vous suggérons d’utiliser de gestion dans votre code, plutôt que d’à l’aide de la gestion des exceptions structurées gestion structurée des exceptions et la `On Error` instruction. Pour plus d’informations, consultez [Try...Catch...Finally, instruction](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
> [!NOTE]
>  Le `Error` clé est également utilisé dans le [Error, instruction](../../../visual-basic/language-reference/statements/error-statement.md), qui est pris en charge pour la compatibilité descendante.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
On Error { GoTo [ line | 0 | -1 ] | Resume Next }  
```  
  
## <a name="parts"></a>Composants  
  
|Terme|Définition|  
|---|---|  
|`GoTo` `line`|Active la routine de gestion des erreurs qui démarre à la ligne spécifiée dans le champ obligatoire `line` argument. Le `line` argument est une étiquette de ligne ou un numéro de ligne. Si une erreur d’exécution se produit, contrôler les branches de la ligne spécifiée, ce qui rend le Gestionnaire d’erreurs actif. La ligne spécifiée doit être dans la même procédure que la `On Error` instruction, ou une erreur de compilation se produit.|  
|`GoTo` 0|Désactive le Gestionnaire d’erreurs activé dans la procédure actuelle et réinitialise à `Nothing`.|  
|`GoTo` -1|Désactive l’exception activée dans la procédure actuelle et réinitialise à `Nothing`.|  
|`Resume Next`|Spécifie que lorsqu’une erreur d’exécution se produit, contrôle passe à l’instruction qui suit immédiatement l’instruction où l’erreur s’est produite, et l’exécution se poursuit à partir de ce point. Utilisez ce formulaire plutôt que `On Error GoTo` lors de l’accès aux objets.|  
  
## <a name="remarks"></a>Notes  
  
> [!NOTE]
>  Nous vous recommandons d’utiliser Gestion structurée des exceptions dans votre code autant que possible, au lieu d’utiliser la gestion des exceptions structurées et `On Error` instruction. Pour plus d’informations, consultez [Try...Catch...Finally, instruction](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
 Un gestionnaire d’erreurs « activé » est activé par un `On Error` instruction. Un gestionnaire d’erreurs « actif » est un gestionnaire activé qui est en cours de la gestion d’une erreur.  
  
 Si une erreur se produit lors d’un gestionnaire d’erreurs est actif (entre l’occurrence de l’erreur et un `Resume`, `Exit Sub`, `Exit Function`, ou `Exit Property` instruction), gestionnaire d’erreurs de la procédure en cours ne peut pas gérer l’erreur. Contrôle retourne à la procédure appelante.  
  
 Si la procédure appelante possède un gestionnaire d’erreurs activé, il est activé pour traiter l’erreur. Si le Gestionnaire d’erreurs de la procédure appelante est également actif, contrôle passe par le biais de procédures précédentes de l’appelant jusqu'à ce qu’un gestionnaire d’erreurs activé, mais il est inactif, est trouvé. Si aucun gestionnaire d’erreurs de ce type n’est trouvée, l’erreur est irrécupérable au point où elle s’est produite.  
  
 Chaque fois que le Gestionnaire d’erreurs repasse le contrôle à une procédure appelante, cette procédure devient la procédure en cours. Une fois qu’une erreur est gérée par un gestionnaire d’erreurs dans une procédure, l’exécution reprend dans la procédure en cours à l’emplacement désigné par la `Resume` instruction.  
  
> [!NOTE]
>  Une routine de gestion des erreurs n’est pas un `Sub` procédure ou un `Function` procédure. Il s’agit d’une section de code marqué par une étiquette de ligne ou un numéro de ligne.  
  
## <a name="number-property"></a>Propriété Number  
 Routines de gestion des erreurs reposent sur la valeur de la `Number` propriété de la `Err` objet afin de déterminer la cause de l’erreur. La routine doit tester ou enregistrer les valeurs de propriété pertinents dans le `Err` avant toute autre erreur peut se produire ou avant une procédure qui peut provoquer une erreur est appelée de l’objet. Les valeurs des propriétés dans le `Err` objet reflètent uniquement l’erreur la plus récente. Le message d’erreur associé `Err.Number` est contenue dans `Err.Description`.  
  
## <a name="throw-statement"></a>Throw, instruction  
 Une erreur est générée avec la `Err.Raise` méthode définit la `Exception` propriété à une nouvelle instance de la <xref:System.Exception> classe. Pour prendre en charge le déclenchement d’exceptions des types d’exception dérivés, une `Throw` instruction est pris en charge dans le langage. Cela prend un seul paramètre qui est l’instance de l’exception levée. L’exemple suivant montre comment ces fonctionnalités peuvent être utilisées avec prise en charge de la gestion des exceptions existantes :  
  
 [!code-vb[VbVbalrErrorHandling#17](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/on-error-statement_1.vb)]  
  
 Notez que la `On Error GoTo` instruction intercepte toutes les erreurs, quelle que soit la classe d’exception.  
  
## <a name="on-error-resume-next"></a>On Error Resume Next  
 `On Error Resume Next`l’exécution continue avec l’instruction qui suit immédiatement l’instruction ayant provoqué l’erreur d’exécution, ou avec l’instruction qui suit le dernier appel de la procédure contenant la `On Error Resume Next` instruction. Cette instruction permet de continuer en dépit d’une erreur d’exécution de l’exécution. Vous pouvez placer la routine de gestion des erreurs où l’erreur peut se produire au lieu de transférer le contrôle à un autre emplacement dans la procédure. Un `On Error Resume Next` instruction devient inactive lorsqu’une autre procédure est appelée, vous devez exécuter une `On Error Resume Next` instruction dans chaque appelée routine si vous souhaitez qu’erreur inline gestion au sein de cette routine.  
  
> [!NOTE]
>  Le `On Error Resume Next` construction peut être préférable `On Error GoTo` lors de la gestion des erreurs générées pendant l’accès à d’autres objets. Vérification `Err` après chaque interaction avec un objet supprime l’ambiguïté à laquelle l’objet est accessible par le code. Vous pouvez être certain objet qui a placé le code d’erreur `Err.Number`, ainsi que l’objet qui a généré l’erreur (l’objet spécifié dans `Err.Source`).  
  
## <a name="on-error-goto-0"></a>On Error GoTo 0  
 `On Error GoTo 0`désactive la gestion des erreurs dans la procédure en cours. Il ne spécifie pas la ligne 0 comme le début du code de gestion des erreurs, même si la procédure contient une ligne numérotée 0. Sans un `On Error GoTo 0` instruction, un gestionnaire d’erreurs est automatiquement désactivée lorsqu’une procédure se termine.  
  
## <a name="on-error-goto--1"></a>On Error GoTo -1  
 `On Error GoTo -1`désactive l’exception dans la procédure en cours. Il ne spécifie pas la ligne -1 comme le début du code de gestion des erreurs, même si la procédure contienne une ligne numérotée -1. Sans un `On Error GoTo -1` instruction, une exception est automatiquement désactivée lorsqu’une procédure se termine.  
  
 Pour éviter que le code de gestion des erreurs en cours d’exécution lorsque aucune erreur ne s’est produite, placez une `Exit Sub`, `Exit Function`, ou `Exit Property` instruction immédiatement avant la routine de gestion des erreurs, comme dans le fragment suivant :  
  
 [!code-vb[VbVbalrErrorHandling#18](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/on-error-statement_2.vb)]  
  
 Ici, le code de gestion des erreurs suit la `Exit Sub` instruction et précède la `End Sub` instruction pour le séparer du flux de procédure. Vous pouvez placer le code de gestion des erreurs n’importe où dans une procédure.  
  
## <a name="untrapped-errors"></a>Erreurs non interceptées  
 Erreurs non interceptées dans les objets sont retournés à l’application de contrôle lorsque l’objet s’exécute comme un fichier exécutable. Dans l’environnement de développement, les erreurs non interceptées sont retournées à l’application de contrôle uniquement si les options appropriées sont définies. Consultez la documentation de votre application hôte pour obtenir une description des options doivent être ensemble pendant le débogage, comment les définir et la création de classes.  
  
 Si vous créez un objet qui accède à d’autres objets, vous devez tenter de gérer les erreurs non gérées retournées. Si vous ne pouvez pas mapper les codes d’erreur dans `Err.Number` à un de vos propres erreurs puis passer les sauvegarder à l’appelant de votre objet. Vous devez spécifier votre erreur en ajoutant votre code d’erreur à le `VbObjectError` constante. Par exemple, si votre code d’erreur est 1052, l’affecter comme suit :  
  
 [!code-vb[VbVbalrErrorHandling#19](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/on-error-statement_3.vb)]  
  
> [!CAUTION]
>  Les erreurs système lors des appels à des bibliothèques de liens dynamiques Windows (DLL) ne pas lever d’exceptions et ne peut pas être interceptées par Visual Basic. Lors de l’appel des fonctions DLL, vous devez vérifier chaque valeur de retour pour la réussite ou l’échec (selon les spécifications des API) et en cas de défaillance, vérifiez la valeur la `Err` l’objet `LastDLLError` propriété.  
  
## <a name="example"></a>Exemple  
 Cet exemple utilise d’abord la `On Error GoTo` instruction pour spécifier l’emplacement d’une routine de gestion des erreurs dans une procédure. Dans l’exemple, une tentative de division par zéro génère une erreur numéro 6. L’erreur est gérée dans la routine de gestion des erreurs et le contrôle est ensuite retourné à l’instruction qui a provoqué l’erreur. La `On Error GoTo 0` instruction désactive l’interception des erreurs. La `On Error Resume Next` instruction est utilisée pour différer l’interception des erreurs afin que le contexte de l’erreur générée par l’instruction suivante peut être déterminé avec certitude. Notez que `Err.Clear` est utilisée pour effacer le `Err` des propriétés de l’objet une fois que l’erreur est gérée.  
  
 [!code-vb[VbVbalrErrorHandling#20](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/on-error-statement_4.vb)]  
  
## <a name="requirements"></a>Configuration requise  
 **Namespace :** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **Assembly :** bibliothèque Visual Basic Runtime (dans Microsoft.VisualBasic.dll)  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualBasic.Information.Err%2A>  
 <xref:Microsoft.VisualBasic.ErrObject.Number%2A>  
 <xref:Microsoft.VisualBasic.ErrObject.Description%2A>  
 <xref:Microsoft.VisualBasic.ErrObject.LastDllError%2A>  
 [End (instruction)](../../../visual-basic/language-reference/statements/end-statement.md)  
 [Exit (instruction)](../../../visual-basic/language-reference/statements/exit-statement.md)  
 [Resume (instruction)](../../../visual-basic/language-reference/statements/resume-statement.md)  
 [Messages d’erreur](../../../visual-basic/language-reference/error-messages/index.md)  
 [Try...Catch...Finally (instruction)](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
