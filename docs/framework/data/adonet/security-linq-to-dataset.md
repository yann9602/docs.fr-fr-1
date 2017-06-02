---
title: "S&#233;curit&#233; (LINQ to DataSet) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6116b2b8-75f4-4d8b-aea6-c13e55cda50b
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# S&#233;curit&#233; (LINQ to DataSet)
Cette rubrique traite des questions de sécurité dans [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].  
  
## Passage d'une requête à un composant non approuvé  
 Une requête [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] peut être formulée à un point donné d'un programme et exécutée à un point différent.  Au point précis où elle est formulée, la requête peut référencer tout élément qui y est visible, comme des membres privés de la classe à laquelle appartient la méthode appelante, ou des symboles représentant les variables\/arguments locaux.  Au moment de l'exécution, la requête pourra accéder aux membres qu'elle a référencés au moment de la formulation, même si le code appelant ne les voit pas.  Le code qui exécute la requête ne peut avoir aucune visibilité arbitraire du fait qu'il ne peut pas choisir les éléments auxquels il peut accéder.  Il accède strictement aux mêmes éléments que la requête, et uniquement à travers la requête.  
  
 Pour cela, il faut qu'en passant une référence à une requête à une autre partie du code, le composant recevant la requête soit approuvé auprès de tous les membres publics et privés auxquels la requête fait référence.  En général, les requêtes [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] ne doivent pas être passées à des composants non approuvés, à moins que la requête ait été construite en prenant soin de ne pas exposer d'informations devant rester confidentielles.  
  
## Entrée externe  
 Les applications reçoivent souvent des entrées externes \(provenant d'un utilisateur ou d'un autre agent externe\) et exécutent des actions en fonction de ces entrées.  Dans le cas de [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)], l'application peut construire une requête d'une certaine manière, en fonction d'une entrée externe, ou utiliser une entrée externe dans la requête. Les requêtes [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] acceptent des paramètres partout où des littéraux sont admis.  Les développeurs d'applications devraient utiliser des requêtes paramétrées, plutôt que d'injecter des littéraux directement dans la requête à partir d'un agent externe.  
  
 Toute entrée provenant directement ou indirectement d'un utilisateur ou d'un agent externe doit avoir un contenu qui se base sur la syntaxe du langage cible afin d'exécuter des actions non autorisées.  C'est ce que l'on appelle une « attaque par injection de code SQL », terme dérivé d'un modèle d'attaque où le langage cible est Transact\-SQL.  L'entrée utilisateur injectée directement dans la requête est utilisée pour effacer une table de base de données, provoquer un déni de service, ou modifier d'une manière ou d'une autre la nature de l'opération en cours.  Bien qu'il soit possible de composer des requêtes dans [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)], cette opération est effectuée via l'API de modèle objet. Les requêtes [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] ne sont pas composées par manipulation de chaîne ou concaténation du fait qu'elles sont en Transact\-SQL et ne sont pas sujettes à des attaques par injection de code SQL au sens classique du terme.  
  
## Voir aussi  
 [Guide de programmation](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)