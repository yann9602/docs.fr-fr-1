---
title: "&#39;&lt;interfacename&gt;.&lt;membername&gt;&#39; is already implemented by the base class &#39;&lt;baseclassname&gt;&#39;. Re-implementation of &lt;type&gt; assumed | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbc42015"
  - "bc42015"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC42015"
ms.assetid: 658c070a-113e-4bd8-b294-12c243191160
caps.latest.revision: 12
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 12
---
# &#39;&lt;interfacename&gt;.&lt;membername&gt;&#39; is already implemented by the base class &#39;&lt;baseclassname&gt;&#39;. Re-implementation of &lt;type&gt; assumed
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Une propriété, une procédure ou un événement dans une classe dérivée utilise une clause `Implements` qui spécifie un membre d'interface qui est déjà implémenté dans la classe de base.  
  
 Une classe dérivée peut implémenter de nouveau un membre d'interface qui est implémenté par sa classe de base.  La substitution de l'implémentation de la classe de base est une procédure différente.  Pour plus d'informations, consultez [Implements](../../../visual-basic/language-reference/statements/implements-clause.md).  
  
 Par défaut, ce message est un avertissement.  Pour plus d'informations sur le masquage des avertissements ou le traitement des avertissements en tant qu'erreurs, consultez [Configuration d'avertissements en Visual Basic](/visual-studio/ide/configuring-warnings-in-visual-basic).  
  
 **ID d'erreur :** BC42015  
  
### Pour corriger cette erreur  
  
-   Si vous comptez implémenter de nouveau le membre d'interface, aucune mesure n'est nécessaire.  Le code de votre classe dérivée accède au membre implémenté de nouveau à moins que vous utilisiez le mot clé `MyBase` pour accéder à l'implémentation de la classe de base.  
  
-   Si vous ne comptez pas à implémenter de nouveau le membre d'interface, supprimez la clause `Implements` de la déclaration de la propriété, de la procédure ou de l'événement.  
  
## Voir aussi  
 [Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md)