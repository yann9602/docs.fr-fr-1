---
title: "On Error Statement (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.OnError"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Visual Basic code, control flow"
  - "Resume Next statement"
  - "errors [Visual Basic], trapping"
  - "error handling, On Error statement"
  - "Next statement, On Error"
  - "control flow, branching"
  - "Error keyword"
  - "execution, conditional"
  - "Resume statement, and On Error statement"
  - "Error statement, and On Error statement"
  - "GoTo statement, and On Error statement"
  - "branching, on error"
  - "conditional statements, On Error"
  - "On Error statement, syntax"
  - "On keyword"
  - "run-time errors, handling"
  - "On Error statement"
ms.assetid: ff947930-fb84-40cf-bd66-1ea219561d5c
caps.latest.revision: 22
caps.handback.revision: 22
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# On Error Statement (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Active une routine de gestion des erreurs et spécifie l'emplacement de la routine dans une procédure ; peut également être utilisée pour désactiver une routine de gestion des erreurs.  
  
 Sans instruction `On Error`, une erreur d'exécution est irrécupérable : un message d'erreur s'affiche et l'exécution s'arrête.  
  
 Si possible, nous vous suggérons vous utilisez la gestion structurée des exceptions dans votre code, plutôt que d'utiliser la gestion non structurée des exceptions et l'instruction d' `On Error` .  Pour plus d'informations, consultez [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
> [!NOTE]
>  Le mot clé `Error` est également utilisé dans l'instruction du même nom \([Error Statement](../../../visual-basic/language-reference/statements/error-statement.md)\), pris en charge pour la compatibilité descendante.  
  
## Syntaxe  
  
```  
On Error { GoTo [ line | 0 | -1 ] | Resume Next }  
```  
  
## Composants  
  
|||  
|-|-|  
|Terme|Définition|  
|`GoTo` `line`|Active la routine de gestion des erreurs qui démarre à la ligne spécifiée dans l'argument `line` requis.  L'argument `line` est une étiquette de ligne ou un numéro de ligne.  Si une erreur d'exécution se produit, le contrôle crée une branche vers la ligne spécifiée, ce qui active le gestionnaire d'erreurs.  La ligne spécifiée doit se trouver dans la même procédure que l'instruction `On Error` ; sinon, une erreur de compilation se produit.|  
|`GoTo` 0|Désactive le gestionnaire d'erreurs activé dans la procédure en cours et le réinitialise à la valeur `Nothing`.|  
|`GoTo` \-1|Désactive l'exception activée dans la procédure en cours et la réinitialise à la valeur `Nothing`.|  
|`Resume Next`|Indique que dans le cadre d'une erreur d'exécution, le contrôle passe à l'instruction qui suit directement celle où s'est produite l'erreur ; l'exécution se poursuit à partir de ce point.  Utilisez ce formulaire plutôt que `On Error GoTo` lors de l'accès aux objets.|  
  
## Notes  
  
> [!NOTE]
>  Nous vous recommandons d'utiliser la gestion structurée des exceptions dans votre code autant que possible, plutôt que d'utiliser la gestion non structurée des exceptions et l'instruction d' `On Error` .  Pour plus d'informations, consultez [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
 Un gestionnaire d'erreurs « actif » est activé par une instruction `On Error`.  Un gestionnaire d'erreurs « actif » est un gestionnaire activé qui figure dans le processus de gestion d'une erreur.  
  
 Si une erreur se produit lorsqu'un gestionnaire d'erreurs est actif \(entre l'occurrence de l'erreur et l'instruction `Resume`, `Exit Sub`, `Exit Function` ou `Exit Property`\), le gestionnaire d'erreurs de la procédure en cours ne peut pas gérer l'erreur.  Le contrôle retourne à la procédure appelante.  
  
 Si la procédure appelante possède un gestionnaire d'erreurs activé, elle peut gérer l'erreur.  Si le gestionnaire d'erreurs de la procédure appelante est également actif, le contrôle est retourné par l'intermédiaire des procédures appelantes précédentes jusqu'à la découverte d'un gestionnaire d'erreurs activé \(mais inactif\).  Si aucun gestionnaire d'erreurs de ce type n'est découvert, l'erreur est irrécupérable au point où elle est apparue.  
  
 Chaque fois que le gestionnaire d'erreurs retourne le contrôle à une procédure appelante, cette procédure devient la procédure en cours.  Dès qu'une erreur est gérée par une gestionnaire d'erreurs dans une procédure, l'exécution reprend dans la procédure en cours au point désigné par l'instruction `Resume`.  
  
> [!NOTE]
>  Une routine de gestion d'erreurs n'est pas une procédure `Sub` ni une procédure `Function`.  C'est une section de code marquée par une étiquette de ligne ou un numéro de ligne.  
  
## Number, propriété  
 Les routines de gestion d'erreurs reposent sur la valeur de la propriété `Number` de l'objet `Err` pour déterminer la cause de l'erreur.  La routine devrait tester ou enregistrer les valeurs de propriétés adéquates dans l'objet `Err` avant qu'une autre erreur ne se produise ou avant qu'une procédure pouvant engendrer une erreur soit appelée.  Les valeurs de propriété de l'objet `Err` reflètent uniquement l'erreur la plus récente.  Le message d'erreur associé à `Err.Number` est contenu dans `Err.Description`.  
  
## Throw, instruction  
 Une erreur qui est déclenchée avec la méthode `Err.Raise` affecte à la propriété `Exception` une instance nouvellement créée de la classe <xref:System.Exception>.  Afin de prendre en charge le déclenchement d'exceptions des types d'exception dérivés, une instruction `Throw` est prise en charge dans le langage.  Elle prend un seul paramètre qui est une instance d'exception à lever.  L'exemple suivant montre comment ces fonctionnalités peuvent être utilisées avec la prise en charge de gestion des exceptions existante :  
  
 [!code-vb[VbVbalrErrorHandling#17](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/on-error-statement_1.vb)]  
  
 Notez que l'instruction `On Error GoTo` intercepte toutes les erreurs quelle que soit la classe d'exception.  
  
## On Error Resume Next  
 `On Error Resume Next` poursuit l'exécution par l'instruction qui suit directement celle qui a engendré l'erreur d'exécution ou par celle qui suit directement le dernier appel de la procédure contenant l'instruction `On Error Resume Next`.  Cette instruction permet la poursuite de l'exécution malgré l'erreur d'exécution.  Vous pouvez placer la routine de gestion des erreurs à l'endroit où l'erreur risque de se produire au lieu de transférer le contrôle à un autre emplacement de la procédure.  Une instruction `On Error Resume Next` devient inactive lors de l'appel d'une autre procédure ; vous devriez donc exécuter une instruction `On Error Resume Next` dans chaque routine appelée si vous souhaitez utiliser une gestion des erreurs inline dans cette routine.  
  
> [!NOTE]
>  La construction `On Error Resume Next` peut être préférable à `On Error GoTo` lors de la gestion des erreurs générées au cours de l'accès à d'autres objets.  La vérification de `Err` après chaque interaction avec un objet supprime l'ambiguïté selon laquelle l'objet est accessible par le code.  Vous pouvez déterminer avec certitude l'objet ayant déclenché le code d'erreur dans `Err.Number`, ainsi que l'objet qui a généré l'erreur à l'origine \(l'objet spécifié dans `Err.Source`\).  
  
## On Error GoTo 0  
 `On Error GoTo 0` désactive la gestion des erreurs dans la procédure actuelle.  Elle ne spécifie pas la ligne 0 comme point de départ du code de gestion des erreurs, même si la procédure contient effectivement une ligne numérotée 0.  Sans instruction `On Error GoTo 0`, un gestionnaire d'erreurs est automatiquement désactivé lorsqu'une procédure se termine.  
  
## On Error GoTo \-1  
 `On Error GoTo -1` désactive l'exception dans la procédure actuelle.  L'instruction ne spécifie pas la ligne \-1 comme le début du code de gestion d'erreur, même si la procédure contient effectivement une ligne numérotée \-1.  Sans une instruction `On Error GoTo -1`, une exception est automatiquement désactivée lorsqu'une procédure se termine.  
  
 Pour empêcher l'exécution du code de gestion des erreurs lorsque aucune erreur ne se produit, insérez une instruction `Exit Sub`, `Exit Function` ou `Exit Property` immédiatement avant la routine de gestion des erreurs, comme illustré dans le fragment suivant :  
  
 [!code-vb[VbVbalrErrorHandling#18](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/on-error-statement_2.vb)]  
  
 Dans cet exemple, le code de gestion des erreurs suit l'instruction `Exit Sub` et précède l'instruction `End Sub` pour la séparer du flux de procédure.  Vous pouvez placer du code de gestion des erreurs à n'importe quel endroit d'une procédure.  
  
## Erreurs non interceptées  
 Les erreurs non interceptées dans les objets sont retournées à l'application de contrôle lorsque l'objet s'exécute comme un fichier exécutable.  Dans l'environnement de développement, les erreurs non interceptées sont retournées à l'application de contrôle uniquement si les options correctes sont définies.  Consultez la documentation de votre application hôte pour obtenir une description des options à définir lors du débogage et savoir comment les définir, ainsi que pour déterminer si l'hôte peut créer des classes.  
  
 Si vous créez un objet qui accède à d'autres objets, vous devez essayer de traiter les erreurs non gérées retournées.  Dans le cas contraire, vous pouvez mapper les codes d'erreur de `Err.Number` vers l'une de vos erreurs, puis passer ces erreurs à l'appelant de votre objet.  Vous devez spécifier votre erreur en ajoutant votre code d'erreur à la constante `VbObjectError`.  Par exemple, si votre code d'erreur est 1052, vous devez l'assigner comme suit :  
  
 [!code-vb[VbVbalrErrorHandling#19](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/on-error-statement_3.vb)]  
  
> [!CAUTION]
>  Les erreurs système lors des appels à des bibliothèques de liens dynamiques \(DLL, Dynamic\-Link Libraries\) Windows ne déclenchent pas d'exceptions et ne peuvent pas être décelées par l'interception des erreurs Visual Basic.  Lors d'un appel aux fonctions DLL, vous devez vérifier si chaque valeur de retour a abouti ou échoué \(selon les spécifications API\) ; en cas d'échec, vérifiez la valeur de la propriété `LastDLLError` dans l'objet `Err`.  
  
## Exemple  
 Cet exemple utilise d'abord l'instruction `On Error GoTo` pour spécifier l'emplacement d'une routine de gestion des erreurs dans une procédure.  Dans l'exemple, une tentative de diviser par zéro génère le numéro d'erreur 6.  L'erreur est contrôlée dans la routine de gestion des erreurs, puis le contrôle est retourné à l'instruction qui a provoqué l'erreur.  L'instruction `On Error GoTo 0` désactive l'interception des erreurs.  L'instruction `On Error Resume Next` est ensuite utilisée pour différer l'interception des erreurs de sorte que le contexte de l'erreur générée par l'instruction suivante peut être déterminé avec certitude.  Notez que `Err.Clear` est utilisé pour effacer les propriétés de l'objet `Err` après la gestion de l'erreur.  
  
 [!code-vb[VbVbalrErrorHandling#20](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/on-error-statement_4.vb)]  
  
## Configuration requise  
 **Espace de noms :** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **Assembly :** bibliothèque Runtime Visual Basic \(dans Microsoft.VisualBasic.dll\)  
  
## Voir aussi  
 <xref:Microsoft.VisualBasic.Information.Err%2A>   
 <xref:Microsoft.VisualBasic.ErrObject.Number%2A>   
 <xref:Microsoft.VisualBasic.ErrObject.Description%2A>   
 <xref:Microsoft.VisualBasic.ErrObject.LastDllError%2A>   
 [End Statement](../../../visual-basic/language-reference/statements/end-statement.md)   
 [Exit Statement](../../../visual-basic/language-reference/statements/exit-statement.md)   
 [Resume Statement](../../../visual-basic/language-reference/statements/resume-statement.md)   
 [Error Messages](../../../visual-basic/language-reference/error-messages/index.md)   
 [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)