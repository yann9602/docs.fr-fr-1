---
title: "Action d&#39;ach&#232;vement de l&#39;instance | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 90cc99d2-9fef-42fd-bcbf-a56917993721
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# Action d&#39;ach&#232;vement de l&#39;instance
La propriété **Action d'achèvement de l'instance** du magasin d'instances de workflow SQL vous permet de spécifier si les données et métadonnées d'instances de workflow sont supprimées de la base de données de persistance après que les instances ont abouti.Les valeurs autorisées pour cette propriété sont **DeleteAll** et **DeleteNothing**.La liste suivante décrit ces trois options :  
  
-   **DeleteAll \(valeur par défaut\).** Si la valeur de la propriété est définie sur DeleteAll, les données et métadonnées d'instances de workflow sont supprimées de la base de données de persistance après que les instances ont abouti.  
  
-   **DeleteNothing.** Si la valeur de la propriété est définie sur DeleteNothing, les données et métadonnées d'instances de workflow sont conservées dans la base de données de persistance même après que les instances ont abouti.  
  
    > [!CAUTION]
    >  Garder les informations d'état de l'instance après que les instances ont abouti entraîne l'augmentation de la taille de la base de données de persistance.À mesure que la taille de la base de données augmente, les opérations de base de données que le sous\-système de persistance effectue prennent plus de temps pour s'exécuter, donc vous devez régulièrement vider les informations d'état de l'instance de la base de données de persistance pour optimiser l'exécution de ces services.