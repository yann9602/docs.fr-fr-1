---
title: "Bad checksum value, non hex digits or odd number of hex digits | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "bc42033"
  - "vbc42033"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC42033"
ms.assetid: 4575554d-3615-46e4-9c6a-18e9c338e4ed
caps.latest.revision: 10
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 10
---
# Bad checksum value, non hex digits or odd number of hex digits
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Une valeur de checksum contient des chiffres hexadécimaux non valides ou comporte un nombre impair de chiffres.  
  
 Quand ASP.NET génère un fichier source Visual Basic \(extension .vb\), il calcule une checksum et la place dans un fichier source masqué, identifié par `#externalchecksum`. L'utilisateur peut également générer un fichier .vb pour effectuer cela, mais il est préférable de réserver ce processus à un usage interne.  
  
 Par défaut, ce message est un avertissement. Pour plus d'informations sur le masquage des avertissements ou le traitement des avertissements en tant qu'erreurs, consultez [Configuration d'avertissements en Visual Basic](/visual-studio/ide/configuring-warnings-in-visual-basic).  
  
 **ID d'erreur :** BC42033  
  
### Pour corriger cette erreur  
  
1.  Si ASP.NET génère le fichier source Visual Basic, redémarrez la génération du projet.  
  
2.  Si l'avertissement persiste après le redémarrage, réinstallez ASP.NET, puis réessayez la génération.  
  
3.  Si l'avertissement n'est toujours pas résolu, ou si vous n'utilisez pas ASP.NET, rassemblez des informations sur ses circonstances et avertissez les services de support technique Microsoft.  
  
## Voir aussi  
 [ASP.NET Overview](../Topic/ASP.NET%20Overview.md)   
 [Nous contacter](/visual-studio/ide/talk-to-us)