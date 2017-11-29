---
title: "Type de &#39; &lt;variablename&gt;&#39; ne peut pas être déduit, car les limites de la boucle et du s’étend pas vers le même type"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30982
- vbc30982
helpviewer_keywords: BC30982
ms.assetid: 741e85d9-a747-42ad-a1e1-a3f1928aaff5
caps.latest.revision: "30"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 022e29e38a93d2880bbfa250e65a8b95b39ff140
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="type-of-39ltvariablenamegt39-cannot-be-inferred-because-the-loop-bounds-and-the-step-variable-do-not-widen-to-the-same-type"></a>Type de &#39; &lt;variablename&gt;&#39; ne peut pas être déduit, car les limites de la boucle et du s’étend pas vers le même type
Vous avez écrit une `For...Next` boucle dans laquelle le compilateur ne peut pas déduire un type de données pour la variable de contrôle de boucle, car les conditions suivantes sont remplies :  
  
-   Le type de données de la variable de contrôle de boucle n’est pas spécifié avec une clause `As` .  
  
-   Les limites de la boucle et l’incrémentation contiennent au moins deux types de données.  
  
-   Il n’existe aucune conversion standard entre les types de données.  
  
 Par conséquent, le compilateur ne peut pas déduire le type de données de variable de contrôle d’une boucle.  
  
 Dans l’exemple suivant, la variable de l’étape est un caractère et les limites de la boucle sont des entiers. Étant donné qu’aucune conversion standard entre les caractères et les entiers, cette erreur est signalée.  
  
```vb  
Dim stepVar = "1"c  
Dim m = 0  
Dim n = 20  
  
' Not valid.  
' For i = 1 To 10 Step stepVar  
    ' Loop processing  
' Next  
```  
  
 **ID d’erreur :** BC30982  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Modifier les types des limites de la boucle et selon vos besoins afin qu’au moins un d’eux est un type de la clause d’incrémentation. Dans l’exemple précédent, remplacez le type de `stepVar` à `Integer`.  
  
    ```  
    Dim stepVar = 1  
    ```  
  
     - ou -  
  
    ```  
    Dim stepVar As Integer = 1  
    ```  
  
-   Utilisez les fonctions de conversion explicite pour convertir les limites de la boucle et la variable de l’étape pour les types appropriés. Dans l’exemple précédent, appliquez le `Val` à fonction `stepVar`.  
  
    ```  
    For i = 1 To 10 Step Val(stepVar)  
        ' Loop processing  
    Next  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualBasic.Conversion.Val%2A>  
 [For...Next (instruction)](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [Conversions implicites et explicites](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [Inférence de type local](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [Option Infer (instruction)](../../../visual-basic/language-reference/statements/option-infer-statement.md)  
 [Fonctions de conversion de types](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Conversions étendues et restrictives](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
