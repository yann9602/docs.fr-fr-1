---
title: "Un appel &#224; une propri&#233;t&#233; ou une m&#233;thode ne peut pas utiliser une r&#233;f&#233;rence vers un objet priv&#233;, que ce soit comme argument ou comme valeur de retour | Microsoft Docs"
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
  - "vbrID98"
dev_langs: 
  - "VB"
ms.assetid: 059b43e1-202d-4fa2-806b-7bad63c1e7ca
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Un appel &#224; une propri&#233;t&#233; ou une m&#233;thode ne peut pas utiliser une r&#233;f&#233;rence vers un objet priv&#233;, que ce soit comme argument ou comme valeur de retour
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Cette erreur peut avoir plusieurs causes, dont les suivantes :  
  
-   Un client a appelé une propriété ou méthode d’un composant hors processus et a tenté de passer une référence à un objet privé comme l’un des arguments.  
  
-   Un composant hors processus a appelé une méthode de rappel sur son client et a tenté de passer une référence à un objet privé.  
  
-   Un composant hors processus a tenté de passer une référence à un objet privé comme argument d’un événement qu’il a déclenché.  
  
-   Un client a tenté d’assigner une référence d’objet privé à un argument `ByRef` d’un événement qu’il gérait.  
  
### Pour corriger cette erreur  
  
1.  Supprimez la référence.  
  
## Voir aussi  
 [Private](../../../visual-basic/language-reference/modifiers/private.md)