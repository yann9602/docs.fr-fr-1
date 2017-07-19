---
title: "Liste des types de suivis | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e639410b-d1d1-479c-b78e-a4701d4e4085
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# Liste des types de suivis
La page [Niveaux de source](http://go.microsoft.com/fwlink/?LinkID=94943) définit plusieurs niveaux de suivi : Critical, Error, Warning, Information et Verbose, et fournit une description de l'indicateur `ActivityTracing`, qui bascule la sortie des événements de limite de suivi et de transfert d'activité.  
  
 Vous pouvez aussi consultez [TraceEventType](http://go.microsoft.com/fwlink/?LinkId=95169) pour les types de suivis qui peuvent être envoyés par <xref:System.Diagnostics>.  
  
 Le tableau suivant répertorie les plus importants.  
  
|Type de suivi|Description|  
|-------------------|-----------------|  
|Critical|Erreur irrécupérable ou panne d'application.|  
|Erreur|Erreur récupérable.|  
|Avertissement|Message d'informations.|  
|Information|Problème non critique.|  
|Verbose|Suivi de débogage.|  
|Démarrer|Démarrage d'une unité logique de traitement.|  
|Interrompre|Interruption d'une unité logique de traitement.|  
|Reprendre|Reprise d'une unité logique de traitement.|  
|Arrêter|Arrêt d'une unité logique de traitement.|  
|Transférer|Changement d'identité de corrélation.|  
  
 Une activité est définie comme une combinaison des types de suivi ci\-dessus.  
  
 Le code suivant est une expression régulière qui définit une activité idéale dans une étendue locale \(source de suivi\).  
  
 `R = Start (Critical | Error | Warning | Information | Verbose | Transfer | (Transfer Suspend Transfer Resume) )* Stop`  
  
 Cela signifie qu'une activité doit remplir les conditions suivantes.  
  
-   Elle doit respectivement démarrer et s'arrêter avec les suivis Démarrer et Arrêter.  
  
-   Elle doit contenir un suivi Transfert immédiatement avant un suivi Interrompre ou Reprendre.  
  
-   Elle ne doit pas contenir de suivi entre les suivis Interrompre et Reprendre, s'ils existent.  
  
-   Elle peut contenir n'importe quel type de suivi Critique\/Avertissement\/Informations\/Commentaires\/Transfert, en nombre illimité, tant que les conditions précédentes sont observées.  
  
 Le code suivant est une expression régulière qui définit une activité idéale dans la portée globale,  
  
```  
R+   
```  
  
 R étant l'expression régulière d'une activité dans l'étendue locale.  Cela se traduit par :  
  
```  
[R+ = Start ( Critical | Error | Warning | Information | Verbose | Transfer | (Transfer Suspend Transfer Resume) )* Stop]+  
```