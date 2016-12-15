---
title: "Le type de la variable &#171;&#160;&lt;variablename&gt;&#160;&#187; n’est pas d&#233;duit, car il est li&#233; &#224; un champ d’une port&#233;e englobante | Microsoft Docs"
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
  - "vbc42110"
  - "bc42110"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC42110"
ms.assetid: ef4442eb-08d1-434f-a03b-4aa2ed4e4414
caps.latest.revision: 33
caps.handback.revision: 33
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Le type de la variable &#171;&#160;&lt;variablename&gt;&#160;&#187; n’est pas d&#233;duit, car il est li&#233; &#224; un champ d’une port&#233;e englobante
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Le type pour la variable '\<NomVariable\>' ne sera pas déduit, car il est lié à un champ dans une portée clôturante.Modifiez le nom de '\<NomVariable\>', ou utilisez le nom qualifié complet \(par exemple, 'Me.NomVariable' ou 'MyBase.NomVariable'\).  
  
 Une variable de contrôle de boucle dans votre code porte le même nom qu'un champ de la classe ou d'une autre portée englobante.  La variable de contrôle étant utilisée sans clause `As`, elle est liée au champ dans la portée englobante. En outre, le compilateur ne crée pas de nouvelle variable et ne déduit pas son type.  
  
 Dans l'exemple suivant, `Index`, la variable de contrôle de l'instruction `For`, est liée au champ `Index` de la classe `Customer`.  Le compilateur ne crée pas de variable pour la variable de contrôle `Index` ou ne déduit pas son type.  
  
```  
Class Customer  
  
    ' The class has a field named Index.  
    Private Index As Integer  
  
    Sub Main()  
  
    ' The following line will raise this warning.  
        For Index = 1 To 10  
            ' ...  
        Next  
  
    End Sub  
End Class  
  
```  
  
 Par défaut, ce message est un avertissement.  Pour plus d'informations sur le masquage des avertissements ou le traitement des avertissements en tant qu'erreurs, consultez [Configuration d'avertissements en Visual Basic](/visual-studio/ide/configuring-warnings-in-visual-basic).  
  
 **ID d'erreur :** BC42110  
  
### Pour traiter cet avertissement  
  
-   Localisez la variable de contrôle de boucle en modifiant son nom par un identificateur qui ne correspond pas non plus au nom d'un champ de la classe.  
  
    ```  
    For I = 1 To 10  
    ```  
  
-   Précisez que la variable de contrôle de boucle crée une liaison avec le champ de classe en préfixant `Me.` au nom de variable.  
  
    ```  
    For Me.Index = 1 To 10  
    ```  
  
-   Au lieu de l'inférence de type local, utilisez une clause `As` pour spécifier un type pour la variable de contrôle de boucle.  
  
    ```  
    For Index As Integer = 1 To 10  
    ```  
  
## Exemple  
 Le code suivant affiche l'exemple précédent avec la première correction en place.  
  
```  
Class Customer  
  
    ' The class has a field named Index.  
    Private Index As Integer  
  
    Sub Main()  
  
        For I = 1 To 10  
            ' ...  
        Next  
  
    End Sub  
End Class  
```  
  
## Voir aussi  
 [Option Infer Statement](../../../visual-basic/language-reference/statements/option-infer-statement.md)   
 [For Each...Next, instruction](../../../visual-basic/language-reference/statements/for-each-next-statement.md)   
 [For...Next, instruction](../../../visual-basic/language-reference/statements/for-next-statement.md)   
 [How to: Refer to the Current Instance of an Object](../../../visual-basic/programming-guide/language-features/variables/how-to-refer-to-the-current-instance-of-an-object.md)   
 [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)   
 [Me, My, MyBase, and MyClass](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)