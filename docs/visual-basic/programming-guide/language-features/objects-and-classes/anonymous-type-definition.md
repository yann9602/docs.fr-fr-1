---
title: "Anonymous Type Definition (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "anonymous types [Visual Basic], type definition"
ms.assetid: 7a8a0ddc-55ba-4d67-869e-87a84d938bac
caps.latest.revision: 21
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 21
---
# Anonymous Type Definition (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

En réponse à la déclaration d'une instance d'un type anonyme, le compilateur crée une nouvelle définition de classe qui contient les propriétés spécifiées pour le type.  
  
## Code généré par le compilateur  
 Pour la définition suivante de `product`, le compilateur crée une nouvelle définition de classe qui contient des propriétés `Name`, `Price`et `OnHand`.  
  
 [!code-vb[VbVbalrAnonymousTypes#25](../../../../visual-basic/language-reference/modifiers/codesnippet/visualbasic/anonymous-type-definition_1.vb)]  
  
 La définition de classe contient des définitions de propriété semblables à celles qui suivent.  Notez qu'il n'existe aucune méthode `Set` pour les propriétés de clé.  Les valeurs des propriétés de clé sont en lecture seule.  
  
```vb#  
Public Class $Anonymous1  
    Private _name As String  
    Private _price As Double  
    Private _onHand As Integer  
     Public ReadOnly Property Name() As String  
        Get  
            Return _name  
        End Get  
    End Property  
  
    Public ReadOnly Property Price() As Double  
        Get  
            Return _price  
        End Get  
    End Property  
  
    Public Property OnHand() As Integer  
        Get  
            Return _onHand  
        End Get  
        Set(ByVal Value As Integer)  
            _onHand = Value  
        End Set  
    End Property  
  
End Class  
```  
  
 De plus, les définitions de type anonymes contiennent un constructeur par défaut.  Les constructeurs qui nécessitent des paramètres ne sont pas autorisés.  
  
 Si une déclaration de type anonyme contient au moins une propriété de clé, la définition du type substitue trois membres hérités de <xref:System.Object> : <xref:System.Object.Equals%2A>, <xref:System.Object.GetHashCode%2A> et <xref:System.Object.ToString%2A>.  Si aucune propriété de clé n'est déclarée, seul <xref:System.Object.ToString%2A> est substitué.  Les substitutions fournissent les fonctionnalités suivantes :  
  
-   `Equals` retourne la valeur `True` si deux instances de type anonyme sont identiques ou si elles remplissent les conditions suivantes :  
  
    -   Elles ont le même nombre de propriétés.  
  
    -   Les propriétés sont déclarées dans le même ordre, avec les mêmes noms et les mêmes types déduits.  Les comparaisons de nom ne respectent pas la casse.  
  
    -   Au moins une des propriétés est une propriété de clé et le mot clé `Key` est appliqué aux propriétés identiques.  
  
    -   La comparaison de chaque paire de propriétés de clé correspondante retourne la valeur `True`.  
  
     Par exemple, `Equals` retourne uniquement la valeur `True` pour `employee01` et `employee08` dans les exemples suivants.  Le commentaire précédant chaque ligne spécifie la raison pour laquelle la nouvelle instance ne correspond pas à `employee01`.  
  
     [!code-vb[VbVbalrAnonymousTypes#24](../../../../visual-basic/language-reference/modifiers/codesnippet/visualbasic/anonymous-type-definition_2.vb)]  
  
-   `GetHashcode` fournit un algorithme GetHashCode unique approprié.  L'algorithme utilise uniquement les propriétés de clé pour calculer le code de hachage.  
  
-   `ToString` retourne une chaîne de valeurs de propriété concaténées, comme l'illustre l'exemple suivant.  Les propriétés de clé et celles ne correspondant pas à une clé sont incluses.  
  
     [!code-vb[VbVbalrAnonymousTypes#29](../../../../visual-basic/language-reference/modifiers/codesnippet/visualbasic/anonymous-type-definition_3.vb)]  
  
 Les propriétés d'un type anonyme nommées explicitement ne peuvent pas être en conflit avec ces méthodes générées.  Autrement dit, vous ne pouvez pas utiliser `.Equals`, `.GetHashCode` ou `.ToString` pour nommer une propriété.  
  
 Les définitions de type anonyme qui incluent au moins une propriété de clé implémentent également l'interface <xref:System.IEquatable%601?displayProperty=fullName>, où `T` est le type du type anonyme.  
  
> [!NOTE]
>  Les déclarations de type anonyme créent le même type anonyme uniquement si elles se produisent dans le même assembly, si leurs propriétés ont les mêmes noms et les mêmes types déduits, si les propriétés sont déclarées dans le même ordre et si les mêmes propriétés sont marquées comme propriétés de clé.  
  
## Voir aussi  
 [Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)   
 [Comment : déduire les types et les noms de propriétés dans des déclarations de types anonymes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)