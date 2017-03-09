---
title: "Using Statement (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.using"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "resource disposal"
  - "Try...Catch...Finally statements, equivalent to Using statement"
  - "resources [Visual Basic], disposing"
  - "Using statement"
ms.assetid: 665d1580-dd54-4e96-a9a9-6be2a68948f1
caps.latest.revision: 36
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 36
---
# Using Statement (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Déclare le début d'un bloc `Using` et acquiert éventuellement les ressources système contrôlées par le bloc.  
  
## Syntaxe  
  
```  
Using { resourcelist | resourceexpression }  
    [ statements ]  
End Using  
```  
  
## Composants  
  
|||  
|-|-|  
|Terme|Définition|  
|`resourcelist`|Obligatoire si vous ne fournissez pas `resourceexpression`.  Liste d'une ou de plusieurs ressources système qui contrôles de ce bloc d' `Using` , séparés par des virgules.|  
|`resourceexpression`|Obligatoire si vous ne fournissez pas `resourcelist`.  Variable ou expression de référence qui fait référence à une ressource système à contrôler par ce bloc `Using`.|  
|`statements`|Optionnel.  Bloc d'instructions exécutées par le bloc `Using`.|  
|`End Using`|Requis.  Met fin à la définition du bloc `Using` et supprime toutes les ressources qu'il contrôle.|  
  
 Chaque ressource de l'élément `resourcelist` comporte la syntaxe et les éléments suivants :  
  
 `resourcename As New resourcetype [ ( [ arglist ] ) ]`  
  
 ou  
  
 `resourcename As resourcetype = resourceexpression`  
  
## Éléments resourcelist  
  
|||  
|-|-|  
|Terme|Définition|  
|`resourcename`|Requis.  Variable de référence qui fait référence à une ressource système contrôlée par le bloc `Using`.|  
|`New`|Obligatoire si l'instruction `Using` acquiert la ressource.  Si vous avez déjà acquis la ressource, utilisez la deuxième possibilité de syntaxe.|  
|`resourcetype`|Requis.  Classe de la ressource.  La classe doit implémenter l'interface <xref:System.IDisposable>.|  
|`arglist`|Optionnel.  Liste d'arguments que vous passez au constructeur pour créer une instance de `resourcetype`.  Consultez [Parameter List](../../../visual-basic/language-reference/statements/parameter-list.md).|  
|`resourceexpression`|Requis.  Variable ou expression qui fait référence à une ressource système qui répond aux exigences de `resourcetype`.  Si vous utilisez la deuxième possibilité de syntaxe, vous devez acquérir la ressource avant de passer le contrôle à l'instruction `Using`.|  
  
## Notes  
 Votre code requiert parfois une ressource non managée, par exemple un handle de fichier, un wrapper COM ou une connexion SQL.  Un bloc `Using` garantit la suppression d'une ou de plusieurs de ces ressources lorsque votre code a fini de les utiliser.  Cela permet de les mettre à la disposition d'un autre code.  
  
 Les ressources managées sont supprimées par le garbage collector \(GC\) du .NET Framework sans nécessiter de codage supplémentaire de votre part.  Vous n'avez pas besoin d'un bloc `Using` pour les ressources managées.  Cependant, vous pouvez toujours utiliser un bloc `Using` pour forcer la suppression d'une ressource managée au lieu d'attendre le garbage collector.  
  
 Un bloc `Using` se compose de trois parties : acquisition, utilisation et suppression.  
  
-   L'*acquisition* consiste à créer une variable et à l'initialiser pour faire référence à la ressource système.  L'instruction `Using` peut acquérir une ou plusieurs ressources, ou vous pouvez acquérir exactement une ressource avant d'entrer dans le bloc et la fournir à l'instruction `Using`.  Si vous fournissez `resourceexpression`, vous devez acquérir la ressource avant de passer le contrôle à l'instruction `Using`.  
  
-   L'*utilisation* consiste à accéder aux ressources et à les utiliser pour exécuter des opérations.  Les instructions entre `Using` et `End Using` représentent l'utilisation des ressources.  
  
-   La *suppression* consiste à appeler la méthode <xref:System.IDisposable.Dispose%2A> de l'objet dans `resourcename`.  Cela permet à l'objet d'arrêter correctement ses ressources.  L'instruction `End Using` supprime les ressources sous le contrôle du bloc `Using`.  
  
## Comportement  
 Un bloc `Using` se comporte comme une construction `Try`...`Finally` dans laquelle le bloc `Try` utilise les ressources et le bloc `Finally` les supprime.  C'est pourquoi le bloc `Using` garantit la suppression des ressources, peu importe comment vous quittez le bloc.  Cela est vrai même dans le cas d'une exception non gérée, sauf pour <xref:System.StackOverflowException>.  
  
 La portée de chaque variable de ressource acquise par l'instruction `Using` est limitée au bloc `Using`.  
  
 Si vous spécifiez plusieurs ressources système dans l'instruction `Using`, vous obtenez le même effet que si vous imbriquez des blocs `Using` les uns dans les autres.  
  
 Si `resourcename` est `Nothing`, aucun appel à <xref:System.IDisposable.Dispose%2A> n'est effectué, et aucune exception n'est levée.  
  
## Gestion structurée des exceptions dans un bloc Using  
 Si vous devez gérer une exception qui peut se produire dans le bloc `Using`, vous pouvez lui ajouter une construction `Try`...`Finally` complète.  Si vous devez gérer le cas où l'instruction `Using` n'a pas réussi à acquérir une ressource, vous pouvez la tester pour déterminer si `resourcename` a la valeur `Nothing`.  
  
## Gestion structurée des exceptions à la place d'un bloc Using  
 Si vous devez exercer un plus grand contrôle sur l'acquisition des ressources, ou si vous avez besoin de code supplémentaire dans le bloc `Finally`, vous pouvez réécrire le bloc `Using` en tant que construction `Try`...`Finally`.  L'exemple suivant présente les structures des constructions `Try` et `Using` qui sont équivalentes dans l'acquisition et la suppression de `resource`.  
  
```vb  
Using resource As New resourceType   
    ' Insert code to work with resource.  
End Using  
  
' For the acquisition and disposal of resource, the following  
' Try construction is equivalent to the Using block.  
Dim resource As New resourceType  
Try   
    ' Insert code to work with resource.  
Finally   
    If resource IsNot Nothing Then  
        resource.Dispose()   
    End If  
End Try   
```  
  
> [!NOTE]
>  Le code contenu dans le bloc `Using` ne doit pas assigner l'objet dans `resourcename` à une autre variable.  Lorsque vous quittez le bloc `Using`, la ressource est supprimée, et l'autre variable ne peut pas accéder à la ressource vers laquelle il pointe.  
  
## Exemple  
 L'exemple suivant crée un fichier nommé log.txt et entre deux lignes de texte au fichier.  L'exemple lit également ce même fichier et affiche les lignes de texte.  
  
 Étant donné que les classes d' <xref:System.IO.TextWriter> et d' <xref:System.IO.TextReader> implémentent l'interface d' <xref:System.IDisposable> , le code peut utiliser des instructions d' `Using` pour garantir que le fichier est fermé correctement après l'écriture et les opérations de lecture.  
  
 [!code-vb[VbVbalrStatements#50](../../../visual-basic/language-reference/error-messages/codesnippet/visualbasic/using-statement_1.vb)]  
  
## Voir aussi  
 <xref:System.IDisposable>   
 [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)   
 [How to: Dispose of a System Resource](../../../visual-basic/programming-guide/language-features/control-flow/how-to-dispose-of-a-system-resource.md)