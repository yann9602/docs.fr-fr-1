---
title: "Expression recursively calls the containing property &#39;&lt;propertyname&gt;&#39; | Microsoft Docs"
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
  - "vbc42026"
  - "BC42026"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC42026"
ms.assetid: 4fde9db6-3bf3-48dc-8e05-981bf08969da
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Expression recursively calls the containing property &#39;&lt;propertyname&gt;&#39;
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Une instruction dans la procédure `Set` d'une définition de propriété stocke une valeur dans le nom de la propriété.  
  
 L'approche recommandée pour stocker la valeur d'une propriété consiste à définir une variable `Private` dans le conteneur de la propriété et à l'utiliser dans les procédures `Get` et `Set`.  La procédure `Set` doit ensuite stocker la valeur entrante dans cette variable `Private`.  
  
 La procédure `Get` se comportant comme une procédure `Function`, elle peut assigner une valeur au nom de la propriété et retourner le contrôle en utilisant l'instruction `End Get` Toutefois, l'approche recommandée consiste à inclure la variable `Private` comme valeur dans [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md).  
  
 La procédure `Set` se comporte comme une procédure `Sub`, qui ne retourne pas de valeur.  Par conséquent, le nom de la procédure ou de la propriété n'a aucune signification particulière dans une procédure `Set`, et vous ne pouvez pas y stocker de valeur.  
  
 L'exemple suivant présente l'approche qui peut générer cette erreur, suivie de l'approche recommandée.  
  
```  
Public Class illustrateProperties  
' The code in the following property causes this error.  
    Public Property badProp() As Char  
        Get  
            Dim charValue As Char  
            ' Insert code to update charValue.  
            badProp = charValue  
        End Get  
        Set(ByVal Value As Char)  
            ' The following statement causes this error.  
            badProp = Value  
            ' The value stored in the local variable badProp  
            ' is not used by the Get procedure in this property.  
        End Set  
    End Property  
' The following code uses the recommended approach.  
    Private propValue As Char  
    Public Property goodProp() As Char  
        Get  
            ' Insert code to update propValue.  
            Return propValue  
        End Get  
        Set(ByVal Value As Char)  
            propValue = Value  
        End Set  
    End Property  
End Class  
```  
  
 Par défaut, ce message est un avertissement.  Pour plus d'informations sur le masquage des avertissements ou le traitement des avertissements en tant qu'erreurs, consultez [Configuration d'avertissements en Visual Basic](/visual-studio/ide/configuring-warnings-in-visual-basic).  
  
 **ID d'erreur :** BC42026  
  
### Pour corriger cette erreur  
  
-   Réécrivez la définition de la propriété pour utiliser l'approche recommandée, comme illustré dans l'exemple précédent.  
  
## Voir aussi  
 [Procédures de propriété](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)   
 [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md)   
 [Set Statement](../../../visual-basic/language-reference/statements/set-statement.md)