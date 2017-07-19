---
title: "Fonctions d&#39;agr&#233;gation (Entity SQL) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: acfd3149-f519-4c6e-8fe1-b21d243a0e58
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# Fonctions d&#39;agr&#233;gation (Entity SQL)
Un agrégat est une construction de langage qui condense une collection en un scalaire dans le cadre d'une opération de groupe.  Les agrégats [!INCLUDE[esql](../../../../../../includes/esql-md.md)] se présentent sous deux formes :  
  
-   Les fonctions de collection [!INCLUDE[esql](../../../../../../includes/esql-md.md)] qui peuvent être utilisées n'importe où dans une expression. Cela inclut l'utilisation de fonctions d'agrégation dans les projections et les prédicats qui agissent sur les collections. Dans [!INCLUDE[esql](../../../../../../includes/esql-md.md)], la spécification des agrégats s'effectue de préférence par fonctions de collection.  
  
-   Les agrégats de groupe dans les expressions de requête dotées d'une clause GROUP BY.  Comme dans [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], les agrégats de groupe acceptent DISTINCT et ALL comme modificateurs de l'entrée de l'agrégat.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tente tout d'abord d'interpréter une expression comme une fonction de collection et si l'expression est dans le contexte d'une expression SELECT, il l'interprète comme un agrégat de groupe.  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] définit un opérateur d'agrégation spécial appelé [GROUPPARTITION](../../../../../../docs/framework/data/adonet/ef/language-reference/grouppartition-entity-sql.md).  Cet opérateur vous permet d'obtenir une référence au jeu de données d'entrée groupé.  Cela permet d'exécuter des requêtes de regroupement améliorées, où les résultats de la clause GROUP BY peuvent être utilisés à des emplacements autres qu'un agrégat de groupe ou des fonctions de collection.  
  
## Fonctions de collection  
 Les fonctions de collection fonctionnent sur des collections et retournent une valeur scalaire.  Par exemple, si `orders` est une collection de toutes les commandes `orders`, vous pouvez calculer la première date d'expédition grâce à l'expression suivante :  
  
 `min(select value o.ShipDate from LOB.Orders as o)`  
  
## Agrégats de groupe  
 Les agrégats de groupe sont calculés sur un résultat de groupe, tel que défini par la clause GROUP BY.  La clause GROUP BY partitionne les données en groupes.  Pour chaque groupe du résultat, la fonction d'agrégation est appliquée et un agrégat distinct est calculé en utilisant les éléments de chaque groupe comme entrées du calcul d'agrégation.  Lorsqu'une clause GROUP BY est utilisée dans une expression SELECT, seuls des noms d'expressions de regroupement, des agrégats ou des expressions constantes peuvent figurer dans la clause de projection, HAVING ou ORDER BY.  
  
 L'exemple suivant calcule la quantité moyenne commandée pour chaque produit.  
  
 `select p, avg(ol.Quantity) from LOB.OrderLines as ol`  
  
 `group by ol.Product as p`  
  
 Un agrégat de groupe peut ne pas avoir de clause GROUP BY explicite dans l'expression SELECT.  Tous les éléments seront traités comme un groupe unique, équivalent à la spécification d'un regroupement basé sur une constante.  
  
 `select avg(ol.Quantity) from LOB.OrderLines as ol`  
  
 `select avg(ol.Quantity) from LOB.OrderLines as ol group by 1`  
  
 Les expressions utilisées dans la clause GROUP BY sont évaluées à l'aide de la même étendue de résolution de noms qui serait visible pour l'expression de la clause WHERE.  
  
## Voir aussi  
 [Fonctions](../../../../../../docs/framework/data/adonet/ef/language-reference/functions-entity-sql.md)