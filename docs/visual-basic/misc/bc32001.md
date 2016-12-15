---
title: "&#39;&lt;mot_cl&#233;&gt;&#39; n’est pas valide dans un module | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc32001"
  - "bc32001"
helpviewer_keywords: 
  - "BC32001"
ms.assetid: b00757ac-5652-460d-9d2c-11b264d7ec7f
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;mot_cl&#233;&gt;&#39; n’est pas valide dans un module
Un mot clé lié à des instances de classe, tels que `Me` ou `MyBase`, est utilisé à l’intérieur d’un module. Or, les modules n’ont pas d’héritage ou d’instances.  
  
 **ID d’erreur :** BC32001  
  
### Pour corriger cette erreur  
  
-   Si le code utilisant le mot clé implique des instances de classe, déplacez\-le vers une implémentation de classe.  
  
-   Si le code utilisant le mot clé s’applique au module, supprimez le mot clé non valide.  
  
## Voir aussi  
 [Me](http://msdn.microsoft.com/fr-fr/a65973c7-cf06-4547-9b25-9fba885525c2)   
 [MyBase \- delete](http://msdn.microsoft.com/fr-fr/52491d06-6451-4f6f-9aa6-8fab59bbc2b9)