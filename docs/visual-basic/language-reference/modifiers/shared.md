---
title: Shared (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Shared
helpviewer_keywords:
- Shared keyword [Visual Basic]
- members [Visual Basic], shared
- shared members
- nonshared
- shared [elements VB]
- elements [Visual Basic], shared
ms.assetid: 2bf7cf2c-b0dd-485e-8749-b5d674dab4cd
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: fce13c308a449e63eacc2bc4c94c274c7e25506a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="shared-visual-basic"></a>Shared (Visual Basic)
Spécifie qu’un ou plusieurs éléments de programmation déclarés sont associés à une classe ou structure à grande et pas avec une instance spécifique de la classe ou structure.  
  
## <a name="remarks"></a>Remarques  
  
## <a name="when-to-use-shared"></a>Quand utiliser Shared  
 Partage d’un membre d’une classe ou structure le rend disponible pour chaque instance, au lieu de *non partagée*, où chaque instance conserve sa propre copie. Cela est utile, par exemple, si la valeur d’une variable s’applique à l’application entière. Si vous déclarez la variable comme étant `Shared`, puis toutes les instances accèdent au même emplacement de stockage, et si une instance modifie la valeur de la variable, toutes les instances accèdent à la valeur mise à jour.  
  
 Partage n’altère pas le niveau d’accès d’un membre. Par exemple, un membre de classe peut être partagé et privé (accessible uniquement à partir de la classe), ou non partagé et public. Pour plus d’informations, consultez [niveaux en Visual Basic d’accès](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
## <a name="rules"></a>Règles  
  
-   **Contexte de déclaration.** Vous pouvez utiliser `Shared` seulement au niveau du module. Cela signifie que le contexte de déclaration pour un `Shared` élément doit être une classe ou structure et ne peut pas être un fichier source, un espace de noms ou une procédure.  
  
-   **Modificateurs combinés.** Vous ne pouvez pas spécifier `Shared` avec [substitue](../../../visual-basic/language-reference/modifiers/overrides.md), [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md), [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md), [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md), ou [ Statique](../../../visual-basic/language-reference/modifiers/static.md) dans la même déclaration.  
  
-   **L’accès à.** Vous accédez à un élément partagé en le qualifiant avec son nom de classe ou structure, et non avec le nom de variable d’une instance spécifique de sa classe ou structure. Il est même inutile créer une instance d’une classe ou structure pour accéder à ses membres partagés.  
  
     L’exemple suivant appelle la procédure partagée <xref:System.Double.IsNaN%2A> exposées par le <xref:System.Double> structure.  
  
     `If Double.IsNaN(result) Then MsgBox("Result is mathematically undefined.")`  
  
-   **Partage implicite.** Vous ne pouvez pas utiliser le `Shared` modificateur dans une [instruction Const](../../../visual-basic/language-reference/statements/const-statement.md), mais les constantes sont partagées implicitement. De même, vous ne pouvez pas déclarer un membre d’un module ou une interface `Shared`, mais ils sont partagés implicitement.  
  
## <a name="behavior"></a>Comportement  
  
-   **Stockage.** Une variable partagée ou un événement est stockée en mémoire uniquement une fois, quel que soit le nombre d’instances de sa classe ou structure. De même, une procédure partagée ou une propriété conserve uniquement un ensemble de variables locales.  
  
-   **L’accès via une Variable d’Instance.** Il est possible d’accéder à un élément partagé en qualifiant avec le nom d’une variable qui contient une instance spécifique de sa classe ou structure. Bien que cela ne pose généralement comme prévu, le compilateur génère un message d’avertissement et autorise l’accès via le nom de classe ou une structure au lieu de la variable.  
  
-   **L’accès via une Expression d’Instance.** Si vous accédez à un élément partagé via une expression qui retourne une instance de sa classe ou structure, le compilateur autorise l’accès via le nom de classe ou une structure au lieu d’évaluer l’expression. Cela produit des résultats inattendus si vous souhaitez que l’expression pour effectuer d’autres actions ainsi que de retourner l’instance. L'exemple suivant illustre ce comportement.  
  
    ```  
    Sub main()  
        shareTotal.total = 10  
        ' The preceding line is the preferred way to access total.  
        Dim instanceVar As New shareTotal  
        instanceVar.total += 100  
        ' The preceding line generates a compiler warning message and  
        ' accesses total through class shareTotal instead of through  
        ' the variable instanceVar. This works as expected and adds  
        ' 100 to total.  
        returnClass().total += 1000  
        ' The preceding line generates a compiler warning message and  
        ' accesses total through class shareTotal instead of calling  
        ' returnClass(). This adds 1000 to total but does not work as  
        ' expected, because the MsgBox in returnClass() does not run.  
        MsgBox("Value of total is " & CStr(shareTotal.total))  
    End Sub  
    Public Function returnClass() As shareTotal  
        MsgBox("Function returnClass() called")  
        Return New shareTotal  
    End Function  
    Public Class shareTotal  
        Public Shared total As Integer  
    End Class  
    ```  
  
     Dans l’exemple précédent, le compilateur génère un message d’avertissement à chaque fois que le code accède à la variable partagée `total` via une instance. Dans chaque cas, il autorise l’accès directement par le biais de la classe `shareTotal` et n’utilise aucune instance. Dans le cas de l’appel prévu pour la procédure `returnClass`, cela signifie qu’il ne génère pas même un appel à `returnClass`, donc l’action supplémentaire d’affichage « Function returnClass() called » n’est pas exécutée.  
  
 Le modificateur `Shared` peut être utilisé dans les contextes suivants :  
  
 [Dim (instruction)](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Event (instruction)](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [Function (instruction)](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Operator (instruction)](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 [Property (instruction)](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Sub (instruction)](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)  
 [Static](../../../visual-basic/language-reference/modifiers/static.md)  
 [Durée de vie dans Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)  
 [Procédures](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [Structures](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [Objets et classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
