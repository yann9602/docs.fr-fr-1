---
title: "Property &#39;&lt;propertyname&gt;&#39; doesn&#39;t return a value on all code paths | Microsoft Docs"
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
  - "bc42107"
  - "vbc42107"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC42107"
ms.assetid: 06800966-9c3b-4844-9f13-83ac95607d32
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Property &#39;&lt;propertyname&gt;&#39; doesn&#39;t return a value on all code paths
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

La propriété '\<NomPropriété\>' ne retourne pas une valeur pour tous les chemins de code.Une exception de référence null peut se produire au moment de l'exécution lorsque le résultat est utilisé.  
  
 Une procédure `Get` de propriété contient au moins un chemin d'accès possible par l'intermédiaire de son code qui ne retourne pas de valeur.  
  
 Vous pouvez retourner la valeur d'une procédure `Get` de propriété de plusieurs façons :  
  
-   Assignez la valeur au nom de la propriété, puis exécutez une instruction `Exit Property`.  
  
-   Assignez la valeur au nom de la propriété, puis exécutez l'instruction `End Get`.  
  
-   inclure la valeur dans une instruction Return \([Return Statement](../../../visual-basic/language-reference/statements/return-statement.md)\) ;  
  
 Si le contrôle passe sur `Exit Property` ou `End Get` et si vous n'avez pas assigné une valeur au nom de la propriété, la procédure `Get` retourne la valeur par défaut du type de données de la propriété.  Pour plus d'informations, consultez « Behavior » dans [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md).  
  
 Par défaut, ce message est un avertissement.  Pour plus d'informations sur le masquage des avertissements ou le traitement des avertissements en tant qu'erreurs, consultez [Configuration d'avertissements en Visual Basic](/visual-studio/ide/configuring-warnings-in-visual-basic).  
  
 **ID d'erreur :** BC42107  
  
### Pour corriger cette erreur  
  
-   Vérifiez la logique de flux de votre contrôle et assurez\-vous que vous assignez une valeur avant chaque instruction qui provoque un retour.  
  
     Il est plus facile de garantir que chaque retour de la procédure retourne une valeur si vous utilisez toujours l'instruction `Return`.  En procédant ainsi, la dernière instruction avant `End Get` doit correspondre à une instruction `Return`.  
  
## Voir aussi  
 [Procédures de propriété](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)   
 [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md)   
 [Get Statement](../../../visual-basic/language-reference/statements/get-statement.md)