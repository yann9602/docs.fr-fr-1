---
title: "Type of &#39;&lt;variablename&gt;&#39; cannot be inferred because the loop bounds and the step variable do not widen to the same type | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "bc30982"
  - "vbc30982"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30982"
ms.assetid: 741e85d9-a747-42ad-a1e1-a3f1928aaff5
caps.latest.revision: 30
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 30
---
# Type of &#39;&lt;variablename&gt;&#39; cannot be inferred because the loop bounds and the step variable do not widen to the same type
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Vous avez écrit une boucle `For...Next` dans laquelle le compilateur ne peut pas déduire de type de données pour la variable de contrôle de boucle, car les conditions suivantes sont vraies :  
  
-   Le type de données de la variable de contrôle de boucle n'est pas spécifié avec une clause `As`.  
  
-   Les limites de la boucle et la clause d'incrémentation contiennent au moins deux types de données.  
  
-   Aucune conversion standard n'existe entre les types de données.  
  
 Par conséquent, le compilateur ne peut pas déduire le type de données de la variable de contrôle d'une boucle.  
  
 Dans l'exemple suivant, la clause d'incrémentation est un caractère et les limites de la boucle sont toutes les deux des entiers.  Étant donné qu'il n'existe aucune conversion standard entre les caractères et les entiers, cette erreur est signalée.  
  
```vb#  
Dim stepVar = "1"c  
Dim m = 0  
Dim n = 20  
  
' Not valid.  
' For i = 1 To 10 Step stepVar  
    ' Loop processing  
' Next  
```  
  
 **ID d'erreur :** BC30982  
  
### Pour corriger cette erreur  
  
-   Modifiez les types des limites de la boucle et de la clause d'incrémentation selon vos besoins afin qu'au moins un des types soit un type de conversion.  Dans l'exemple précédent, modifiez le type de `stepVar` en `Integer`.  
  
    ```  
    Dim stepVar = 1  
    ```  
  
     \- ou \-  
  
    ```  
    Dim stepVar As Integer = 1  
    ```  
  
-   Utilisez les fonctions de conversion explicite pour convertir les limites de la boucle et la clause d'incrémentation en types appropriés.  Dans l'exemple précédent, appliquez la fonction `Val` à `stepVar`.  
  
    ```  
    For i = 1 To 10 Step Val(stepVar)  
        ' Loop processing  
    Next  
    ```  
  
## Voir aussi  
 <xref:Microsoft.VisualBasic.Conversion.Val%2A>   
 [For...Next, instruction](../../../visual-basic/language-reference/statements/for-next-statement.md)   
 [Implicit and Explicit Conversions](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)   
 [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)   
 [Option Infer Statement](../../../visual-basic/language-reference/statements/option-infer-statement.md)   
 [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)