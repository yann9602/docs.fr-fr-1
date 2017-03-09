---
title: "Object Variable Declaration (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "early binding"
  - "declarations, class"
  - "classes [Visual Basic], declaring"
  - "binding, late and early"
  - "object variables, declaring"
  - "variables [Visual Basic], object"
  - "declaring variables, object variables"
  - "declaring classes"
  - "late binding"
ms.assetid: 2a5a41a3-1aa8-4236-b1f0-2382af7bf715
caps.latest.revision: 33
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 33
---
# Object Variable Declaration (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

Utilisez une instruction de déclaration normale pour déclarer une variable objet.  Pour le type de données, spécifiez soit `Object` \(c'est\-à\-dire le [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md)\) soit une classe plus spécifique à partir de laquelle l'objet doit être créé.  
  
 Déclarer une variable comme `Object` revient à la déclarer comme <xref:System.Object?displayProperty=fullName>.  
  
 Lorsque vous déclarez une variable à l'aide d'une classe d'objet spécifique, elle peut accéder à toutes les méthodes et propriétés exposées par cette classe et les classes dont elle hérite.  Si vous déclarez la variable à l'aide de <xref:System.Object>, elle peut accéder uniquement aux membres de la classe <xref:System.Object>, sauf si vous tournez `Option Strict Off` pour autoriser la liaison tardive.  
  
## Syntaxe de déclaration  
 Utilisez la syntaxe suivante pour déclarer une variable objet :  
  
```  
Dim variablename As [New] { objectclass | Object }  
```  
  
 Vous pouvez spécifier également [Public](../../../../visual-basic/language-reference/modifiers/public.md), [Protected](../../../../visual-basic/language-reference/modifiers/protected.md), [Friend](../../../../visual-basic/language-reference/modifiers/friend.md), `Protected Friend`, [Private](../../../../visual-basic/language-reference/modifiers/private.md), [Shared](../../../../visual-basic/language-reference/modifiers/shared.md) ou [Static](../../../../visual-basic/language-reference/modifiers/static.md) dans la déclaration.  Les exemples de déclarations suivants sont valides :  
  
```  
Private objA As Object  
Static objB As System.Windows.Forms.Label  
Dim objC As System.OperatingSystem  
```  
  
## Liaison tardive et liaison anticipée  
 Parfois, la classe spécifique n'est pas connue jusqu'à l'exécution du code.  Dans ce cas, vous devez déclarer la variable objet à l'aide du type de données `Object`.  Cette opération crée une référence générale à tout type d'objet, et la classe spécifique est assignée au moment de l'exécution.  Cette situation s'appelle une *liaison tardive*.  La liaison tardive requiert un temps d'exécution supplémentaire.  Elle limite également votre code aux méthodes et aux propriétés de la classe qui lui ont été assignées le plus récemment.  Cette situation peut provoquer des erreurs d'exécution si votre code tente d'accéder aux membres d'une classe différente.  
  
 Lorsque vous connaissez la classe spécifique au moment de la compilation, vous devez déclarer la variable objet de telle sorte qu'elle appartienne à cette classe.  On appelle cela une *liaison anticipée*.  La liaison anticipée améliore les performances et garantit l'accès de votre code à toutes les méthodes et propriétés de la classe spécifique.  Dans les exemples de déclarations précédents, si la variable `objA` utilise uniquement des objets de classe <xref:System.Windows.Forms.Label?displayProperty=fullName>, vous devez spécifier `As System.Windows.Forms.Label` dans sa déclaration.  
  
### Avantages de la liaison anticipée  
 La déclaration d'une variable objet en tant que classe spécifique présente plusieurs avantages :  
  
-   Vérification automatique du type  
  
-   Accès garanti à tous les membres de la classe spécifique  
  
-   Prise en charge de Microsoft IntelliSense dans l'éditeur de code  
  
-   Lisibilité améliorée de votre code  
  
-   Réduction des erreurs dans votre code  
  
-   Les erreurs sont interceptées au moment de la compilation plutôt qu'au moment de l'exécution  
  
-   Exécution plus rapide du code  
  
## Accès aux membres des variables objets  
 Lorsque `Option Strict` a la valeur `On`, une variable objet ne peut accéder qu'aux méthodes et aux propriétés de la classe utilisée pour sa déclaration.  L'exemple suivant illustre ce comportement.  
  
```  
' Option statements must precede all other source file lines.  
Option Strict On  
' Imports statement must precede all declarations in the source file.  
Imports System.Windows.Forms  
Public Sub accessMembers()  
    Dim p As Object  
    Dim q As System.Windows.Forms.Label  
    p = New System.Windows.Forms.Label  
    q = New System.Windows.Forms.Label  
    Dim j, k As Integer  
    ' The following statement generates a compiler ERROR.  
    j = p.Left  
    ' The following statement retrieves the left edge of the label in pixels.  
    k = q.Left  
End Sub  
```  
  
 Dans cet exemple, `p` peut utiliser uniquement les membres de la classe <xref:System.Object> elle\-même, lesquels n'incluent pas la propriété `Left`.  D'un autre côté, `q` a été déclaré comme étant de type <xref:System.Windows.Forms.Label>, aussi il peut utiliser toutes les méthodes et les propriétés de la classe <xref:System.Windows.Forms.Label> dans l'espace de noms <xref:System.Windows.Forms>.  
  
## Flexibilité des variables objets  
 Lorsque vous travaillez avec des objets dans une hiérarchie d'héritage, vous pouvez choisir la classe à utiliser pour la déclaration de vos variables objets.  Lors de ce choix, vous devez comparer la flexibilité de l'assignation d'objets à l'accès aux membres d'une classe.  Par exemple, examinez la hiérarchie d'héritage menant à la classe <xref:System.Windows.Forms.Form?displayProperty=fullName> :  
  
 <xref:System.Object>  
  
 `` <xref:System.ComponentModel.Component>  
  
 `` <xref:System.Windows.Forms.Control>  
  
 `` <xref:System.Windows.Forms.ScrollableControl>  
  
 `` <xref:System.Windows.Forms.ContainerControl>  
  
 `` <xref:System.Windows.Forms.Form>  
  
 Supposons que votre application définisse une classe form appelée `specialForm` qui hérite de la classe <xref:System.Windows.Forms.Form>.  Vous pouvez déclarer une variable objet qui fait référence spécifiquement à `specialForm` comme le montre l'exemple suivant.  
  
<CodeContentPlaceHolder>3</CodeContentPlaceHolder>  
 La déclaration de l'exemple précédent permet de limiter la variable `nextForm` aux objets de la classe `specialForm`, mais également de rendre toutes les méthodes et propriétés de `specialForm` disponibles pour `nextForm` ainsi que tous les membres de toutes les classes dont hérite `specialForm`.  
  
 Vous pouvez rendre une variable objet plus générale en la déclarant pour qu'elle soit du type <xref:System.Windows.Forms.Form> comme le montre l'exemple suivant :  
  
<CodeContentPlaceHolder>4</CodeContentPlaceHolder>  
 La déclaration dans l'exemple précédent vous permet d'assigner tout formulaire dans votre application à `anyForm`.  Toutefois, bien que `anyForm` puisse accéder à tous les membres de classe <xref:System.Windows.Forms.Form>, il ne peut pas utiliser des méthodes supplémentaires ou des propriétés définies pour les formulaires spécifiques, tels que `specialForm`.  
  
 Tous les membres d'une classe de base sont disponibles pour les classes dérivées, mais les membres supplémentaires d'une classe dérivée ne sont pas disponibles pour la classe de base.  
  
## Voir aussi  
 [Object Variables](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)   
 [Object Variable Assignment](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)   
 [Object Variable Values](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)   
 [How to: Declare an Object Variable and Assign an Object to It in Visual Basic](../../../../visual-basic/programming-guide/language-features/variables/how-to-declare-an-object-variable-and-assign-an-object-to-it.md)   
 [How to: Access Members of an Object](../../../../visual-basic/programming-guide/language-features/variables/how-to-access-members-of-an-object.md)   
 [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md)   
 [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)   
 [Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)