---
title: "&#39;&lt;membername&gt;&#39; cannot expose type &#39;&lt;typename&gt;&#39; outside the project through &lt;containertype&gt; &#39;&lt;containertypename&gt;&#39; | Microsoft Docs"
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
  - "bc30909"
  - "vbc30909"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30909"
ms.assetid: ffa7395d-e182-4087-8ce8-079810fdae54
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;membername&gt;&#39; cannot expose type &#39;&lt;typename&gt;&#39; outside the project through &lt;containertype&gt; &#39;&lt;containertypename&gt;&#39;
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Une variable, un paramètre de procédure ou un retour de fonction est exposé en dehors de son conteneur, mais il est déclaré comme un type qui ne doit pas être exposé en dehors du conteneur.  
  
 Le code squelette suivant affiche une situation qui génère cette erreur.  
  
```  
Private Class privateClass  
End Class  
Public Class mainClass  
    Public exposedVar As New privateClass  
End Class  
```  
  
 Un type qui est déclaré `Protected`, `Friend`, `Protected Friend` ou `Private` est conçu pour avoir un accès limité en dehors de son contexte de déclaration.  Son utilisation comme type de données d'une variable avec un accès moins limité nuit à cet objectif.  Dans le code squelette précédent, `exposedVar` est `Public` et expose `privateClass` au code qui ne doit pas y avoir accès.  
  
 **ID d'erreur :** BC30909  
  
### Pour corriger cette erreur  
  
-   Modifiez le niveau d'accès de la variable, du paramètre de procédure ou du retour de fonction de sorte qu'il soit au moins aussi restrictif que le niveau d'accès de son type de données.  
  
## Voir aussi  
 [Access Levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)