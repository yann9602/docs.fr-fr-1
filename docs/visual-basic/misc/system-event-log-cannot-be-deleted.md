---
title: "Impossible de supprimer le journal des &#233;v&#233;nements syst&#232;me | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
ms.assetid: 26ca8819-4ce5-49c6-98f3-27fe9e2e8e3d
caps.latest.revision: 8
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 8
---
# Impossible de supprimer le journal des &#233;v&#233;nements syst&#232;me
Une tentative de suppression du journal des événements système, qui ne peut pas être supprimé, a été effectuée. Le journal système assure le suivi des événements système tels que le démarrage du système et les défaillances de matériel.  
  
### Pour corriger cette erreur  
  
-   Songez à configurer votre application de manière à ce qu’elle écrive dans un journal d’application ou un journal personnalisé, plutôt que dans le journal des événements système.  
  
-   N’essayez pas de supprimer le journal des événements système.  
  
## Voir aussi  
 [Administering Event Logs](http://msdn.microsoft.com/fr-fr/35f53238-bdd2-417b-acd8-2fd9f7397f18)   
 [How to: Create and Remove Custom Event Logs](http://msdn.microsoft.com/fr-fr/af9b7da0-80c7-46ac-b7f7-897063ddd503)