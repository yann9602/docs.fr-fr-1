---
title: "Shared (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Shared"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Shared keyword"
  - "members, shared"
  - "shared members"
  - "nonshared"
  - "shared elements"
  - "elements, shared"
ms.assetid: 2bf7cf2c-b0dd-485e-8749-b5d674dab4cd
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 16
---
# Shared (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Spécifie que les éléments de programmation déclarés sont associés à une classe ou structure, et non à une instance spécifique de la classe ou structure.  
  
## Notes  
  
## Quand utiliser Shared  
 Le partage d'un membre d'une classe ou structure le rend disponible à chaque instance, contrairement à *non partagé* où chaque instance conserve sa propre copie.  Par exemple, le fait que la valeur d'une variable s'applique à l'application entière est utile.  Si vous déclarez la variable comme étant `Shared`, toutes les instances accéderont au même emplacement de stockage, et si une instance modifie la valeur de la variable, toutes les instances accèdent à la valeur mise à jour.  
  
 Le partage n'altère pas le niveau d'accès d'un membre.  Par exemple, un membre de classe peut être partagé et privé \(accessible uniquement à partir de la classe\), ou non partagé et public.  Pour plus d'informations, consultez [Access Levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
## Règles  
  
-   **Contexte de déclaration.** Vous pouvez utiliser `Shared` seulement au niveau du module.  Cela signifie que le contexte de déclaration d'un élément `Shared` doit être une classe ou une structure, et ne peut pas être un fichier source, un espace de noms, ou une procédure.  
  
-   **Modificateurs combinés.** Vous ne pouvez pas spécifier `Shared` avec [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md), [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md), [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md), [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md) ou [Static](../../../visual-basic/language-reference/modifiers/static.md) dans la même déclaration.  
  
-   **Accès.** Vous pouvez accéder à un élément partagé en le qualifiant avec son nom de classe ou de structure, non avec le nom de variable d'une instance spécifique de sa classe ou structure.  Vous n'êtes même pas obligé de créer une instance d'une classe ou structure pour accéder à ses membres partagés.  
  
     L'exemple suivant appelle la procédure <xref:System.Double.IsNaN%2A> partagée exposée par la structure <xref:System.Double>.  
  
     `If Double.IsNaN(result) Then MsgBox("Result is mathematically undefined.")`  
  
-   **Partage implicite.** Vous ne pouvez pas utiliser le modificateur `Shared` dans une [Const Statement](../../../visual-basic/language-reference/statements/const-statement.md), mais les constantes sont partagées implicitement.  De la même façon, vous ne pouvez pas déclarer un membre de module ou d'interface comme étant `Shared`, mais ils sont partagés implicitement.  
  
## Comportement  
  
-   **Stockage.** Une variable ou un événement partagé est stocké une seule fois dans la mémoire, sans tenir compte du nombre d'instances de sa classe ou structure que vous créez.  De la même façon, une procédure ou une propriété partagée contient seulement un jeu de variables locales.  
  
-   **Accès via une variable d'instance.** Il est possible d'accéder à un élément partagé en le qualifiant avec le nom d'une variable qui contient une instance spécifique de sa classe ou structure.  Bien que cette technique fonctionne normalement, le compilateur génère un message d'avertissement et autorise l'accès via la classe ou le nom de structure au lieu de la variable.  
  
-   **Accès via une expression d'instance.** Si vous accédez à un élément partagé via une expression qui retourne une instance de sa classe ou structure, le compilateur autorise l'accès via la classe ou le nom de structure au lieu d'évaluer l'expression.  Des résultats inattendus se produisent, autres que l'exécution par l'expression d'autres actions ainsi que le retour de l'instance.  L'exemple suivant illustre ce comportement.  
  
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
  
     Dans l'exemple précédent, le compilateur génère un message d'avertissement les deux fois que le code accède à la variable partagée `total` via une instance.  Dans chaque cas, il autorise un accès direct via le `shareTotal` de classe et n'utilise aucune instance.  Dans le cas où l'appel prévu au `returnClass` de la procédure se produit, il ne génère même pas d'appel à `returnClass`, donc l'action supplémentaire d'affichage de "Function returnClass\(\) called" n'est pas exécutée.  
  
 Le modificateur `Shared` peut être utilisé dans les contextes suivants :  
  
 [Dim, instruction](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Event, instruction](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [Function, instruction](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Operator, instruction](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 [Property, instruction](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Sub, instruction](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## Voir aussi  
 [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)   
 [Static](../../../visual-basic/language-reference/modifiers/static.md)   
 [Lifetime in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)   
 [Procedures](../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Structures](../../../visual-basic/programming-guide/language-features/data-types/structures.md)   
 [Objects and Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)