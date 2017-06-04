---
title: "D&#233;termination de la dur&#233;e d&#39;une op&#233;ration de service | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e8a93a2c-2c20-48b3-8986-57e90e9aa908
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# D&#233;termination de la dur&#233;e d&#39;une op&#233;ration de service
Si le traçage analytique est activé dans une application [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)], la durée d'exécution d'une opération de service peut être déterminée facilement en examinant le journal des événements.  Cette rubrique montre comment déterminer la durée d'exécution d'une opération de service.  
  
### Détermination de la durée d'exécution d'une opération de service  
  
1.  Ouvrez l'Observateur d'événements en cliquant sur **Démarrer**, puis sur **Exécuter** et en entrant `eventvwr.exe`.  
  
2.  Si vous n'avez pas activé le traçage analytique, développez **Journaux des applications et des services**, **Microsoft**, **Windows** et **Serveur d'applications\-Applications**.  Sélectionnez **Afficher** et **Afficher les journaux d'analyse et de débogage**.  Cliquez avec le bouton droit sur **Analyse** et sélectionnez **Activer le journal**.  Laissez l'Observateur d'événements ouvert afin que les traces soient visibles après l'exécution de l'opération de service.  
  
3.  Ouvrez ensuite une application [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] qui inclut un projet de service et un projet client qui interagit avec ce service.  Vous pouvez créer une telle application en suivant le [Didacticiel de mise en route](../../../../../docs/framework/wcf/getting-started-tutorial.md).  Si les exemples [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] sont installés, vous pouvez ouvrir [Getting Started](../../../../../docs/framework/wcf/samples/getting-started-sample.md), qui contient le projet terminé créé dans le didacticiel.  
  
4.  Exécutez l'application serveur en appuyant sur **F5**.  Exécutez l'application cliente en cliquant avec le bouton droit sur le projet **Client** et en sélectionnant **Débogage**, puis **Démarrer une nouvelle instance**.  
  
5.  Dans l'Observateur d'événements, actualisez le journal Analyse et triez les événements par ID d'événement.  Recherchez les événements présentant l'ID [214 \- OperationCompleted](../../../../../docs/framework/wcf/diagnostics/etw/214-operationcompleted.md).  Ces événements affichent les opérations terminées et leur durée.  L'événement suivant affiche la durée d'une opération d'ajout.  
  
    ```Output  
  
    OperationInvoker a terminé l'appel de la méthode 'Add'.  Durée de l'appel de méthode : '3' ms.    
    ```