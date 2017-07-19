---
title: "CLR ETW Providers | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ETW, CLR providers"
  - "CLR ETW providers"
ms.assetid: 0beafad4-b2c8-47f4-b342-83411d57a51f
caps.latest.revision: 7
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 7
---
# CLR ETW Providers
Le Common Language Runtime \(CLR\) a deux fournisseurs : le fournisseur de runtime et le fournisseur d'arrêt.  
  
 Le fournisseur de runtime déclenche des événements en fonction des mots clés \(catégories d'événements\) activés.  Ainsi, vous pouvez collecter des événements de chargeur en activant le mot clé `LoaderKeyword`.  
  
 Les événements ETW \(suivi des événements Windows\) sont journalisés dans un fichier comportant l'extension .etl, qui peut être post\-traité ultérieurement dans des fichiers de valeurs séparées par des virgules \(.csv\), si nécessaire.  Pour plus d'informations sur la conversion du fichier .etl en un fichier .csv, consultez [Controlling .NET Framework Logging](../../../docs/framework/performance/controlling-logging.md).  
  
## Fournisseur de runtime  
 Le fournisseur de runtime est le principal fournisseur ETW du CLR.  
  
 Le GUID du fournisseur de runtime du CLR est e13c0d23\-ccbc\-4e12\-931b\-d9cc2eee27e4.  
  
 Pour obtenir des exemples sur la journalisation et l'affichage des événements ETW du CLR à l'aide d'outils courants, consultez [Controlling .NET Framework Logging](../../../docs/framework/performance/controlling-logging.md).  
  
 En plus des mots clés tels que `LoaderKeyword`, vous devrez éventuellement activer des mots clés pour les événements de journalisation qui se déclenchent trop fréquemment.  Les mots clés `StartEnumerationKeyword` et `EndEnumerationKeyword` activent ces événements et sont résumés dans [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).  
  
## Fournisseur d'arrêt  
 Le fournisseur d'arrêt doit être activé dans certains cas bien précis.  Toutefois, pour la plupart des utilisateurs, le fournisseur de runtime est tout à fait suffisant.  
  
 Le GUID du fournisseur d'arrêt du CLR est A669021C\-C450\-4609\-A035\-5AF59AF4DF18.  
  
 Normalement, la journalisation ETW est activée avant le lancement d'un processus et désactivée une fois ce processus arrêté.  Toutefois, si la journalisation ETW est activée pendant l'exécution du processus, des informations supplémentaires sont requises à propos de celui\-ci.  Par exemple, pour la résolution de symboles, vous devez journaliser des événements de méthode pour les méthodes qui ont été chargées avant l'activation de la journalisation.  
  
 Les événements `DCStart` et `DCEnd` capturent l'état du processus aux moments où la collecte de données a commencé et où elle s'est arrêtée. \(L'état fait référence aux informations de haut niveau, notamment les méthodes qui étaient déjà compilées juste\-à\-temps \(JIT\) et les assemblys déjà chargés.\) Ces deux événements peuvent fournir des informations sur ce qui s'est déjà produit dans le processus ; par exemple, quelles méthodes ont été compilées juste\-à\-temps \(JIT\), etc.  
  
 Seuls les événements possédant `DC`, `DCStart`, `DCEnd`ou `DCInit` dans leurs noms sont déclenchés sous le fournisseur d'arrêt.  En outre, ces événements sont déclenchés uniquement sous ce fournisseur.  
  
 En plus des filtres par mots clés d'événement, le fournisseur d'arrêt prend en charge les mots clés `StartRundownKeyword` et `EndRundownKeyword` pour permettre un filtrage ciblé.  
  
### Arrêt de début  
 Un arrêt de début est déclenché lorsque la journalisation sous le fournisseur d'arrêt est activée par le mot clé `StartRundownKeyword`.  Cela entraîne le déclenchement de l'événement `DCStart`et la capture de l'état du système.  Avant le démarrage de l'énumération, l'événement `DCStartInit` est déclenché.  À la fin de l'énumération, l'événement `DCStartComplete` est déclenché pour indiquer au contrôleur que la collecte de données s'est terminée normalement.  
  
### Arrêt de fin  
 Un arrêt de fin est déclenché lorsque la journalisation sous le fournisseur d'arrêt est activée par le mot clé `EndRundownKeyword`.  L'arrêt de fin arrête le profilage sur un processus qui continue de s'exécuter.  Les événements `DCEnd` capturent l'état du système lorsque du profilage est arrêté.  
  
 Avant le démarrage de l'énumération, l'événement `DCEndInit` est déclenché.  À la fin de l'énumération, l'événement `DCEndComplete` est déclenché pour indiquer au consommateur que la collecte de données s'est terminée normalement.  Les arrêts de début et de fin sont principalement utilisés pour la résolution de symboles managés.  L'arrêt de début peut fournir des informations sur les plages d'adresses des méthodes qui ont été compilées juste\-à\-temps \(JIT\) avant le début de la session de profilage.  L'arrêt de fin peut fournir des informations sur les plages d'adresses de toutes les méthodes qui ont été compilées juste\-à\-temps \(JIT\) lorsque le profilage était sur le point d'être désactivé.  
  
 L'arrêt de fin ne se produit pas automatiquement lorsqu'une session de profilage est arrêtée.  Un outil qui cherche à exécuter la résolution de symboles managés doit appeler explicitement une session du fournisseur d'arrêt du CLR avec le mot clé `EndRundownKeyword` activé, juste avant l'arrêt du profilage.  
  
 Bien que l'arrêt de début ou de fin puisse fournir des informations de plage d'adresses de méthodes pour la résolution de symboles managés, nous vous recommandons d'utiliser le mot clé `EndRundownKeyword` \(lequel fournit des événements `DCEnd`\) au lieu du mot clé `StartRundownKeyword` \(qui fournit des événements `DCStart`\).  `StartRundownKeyword` entraîne l'arrêt de la session de profilage, ce qui peut perturber le scénario profilé.  
  
## Collecte de données ETW à l'aide des fournisseurs de runtime et d'arrêt  
 L'exemple suivant montre comment utiliser le fournisseur d'arrêt du CLR d'une façon qui autorise la résolution des symboles des processus managés avec un impact minimal, indépendamment du fait que les processus démarrent ou se terminent à l'intérieur ou à l'extérieur de la fenêtre profilée.  
  
1.  Activez la journalisation ETW à l'aide du fournisseur de runtime du CLR :  
  
    ```  
    xperf -start clr -on e13c0d23-ccbc-4e12-931b-d9cc2eee27e4:0x1CCBD:0x5 -f clr1.etl      
    ```  
  
     Le journal sera enregistré dans le fichier clr1.etl.  
  
2.  Pour arrêter le profilage alors que le processus continue à s'exécuter, démarrez le fournisseur d'arrêt pour capturer les événements `DCEnd` :  
  
    ```  
    xperf -start clrRundown -on A669021C-C450-4609-A035-5AF59AF4DF18:0xB8:0x5 -f clr2.etl      
    ```  
  
     Cela permet à la collecte d'événements `DCEnd` de démarrer une session d'arrêt.  Vous devrez peut\-être attendre 30 à 60 secondes pour que tous les événements soient collectés.  Le journal sera enregistré dans le fichier clr1.et2.  
  
3.  Désactivez tout le profilage ETW :  
  
    ```  
    xperf -stop clrRundown   
    xperf -stop clr  
    ```  
  
4.  Fusionnez les profils pour créer un fichier journal :  
  
    ```  
    xperf -merge -d clr1.etl clr2.etl merged.etl  
    ```  
  
     Le fichier merged.etl contient les événements des sessions des fournisseurs de runtime et d'arrêt.  
  
 Un outil peut exécuter les étapes 2 et 3 \(démarrage d'une session d'arrêt, puis arrêt du profilage\) au lieu de désactiver immédiatement le profilage lorsqu'un utilisateur demande son arrêt.  Un outil peut également exécuter l'étape 4.  
  
## Voir aussi  
 [ETW Events in the Common Language Runtime](../../../docs/framework/performance/etw-events-in-the-common-language-runtime.md)