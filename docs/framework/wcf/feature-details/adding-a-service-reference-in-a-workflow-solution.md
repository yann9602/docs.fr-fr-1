---
title: "Ajout d&#39;une r&#233;f&#233;rence de service dans une solution de workflow | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 83574cf3-9803-49bc-837f-432936dc9c76
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# Ajout d&#39;une r&#233;f&#233;rence de service dans une solution de workflow
L'ajout d'une référence de service dans une application de workflow fonctionne de façon légèrement différente que dans une application WCF normale.Lorsque vous sélectionnez Ajouter une référence de service et lorsque vous spécifiez l'URL du service, les métadonnées sont téléchargées et les activités personnalisées sont générées pour vous permettre d'appeler le service WCF ou le service de workflow WCF auquel vous avez ajouté une référence.Après l'ajout d'une référence de service, régénérez la solution pour que les activités générées soient construites.Celles\-ci vont ensuite apparaître dans la boîte à outils du concepteur de workflow.Notez toutefois que cela ne fonctionne que si vous ajoutez une référence de service dans une solution de workflow.L'information diffusée sur le Web qui suit explique comment ajouter une référence de service dans d'autres types de projets : [Appel d'un service WCF à partir d'un workflow dans un projet Web](http://go.microsoft.com/fwlink/?LinkId=207725).  
  
 L'ajout de deux ou plus références de service aux services qui contiennent le même nom d'opération entraîne un problème.Les activités générées vont appeler uniquement la première opération de service.Pour contourner ce problème, il faut renommer les opérations de service avec des noms différents ou modifier le nom de la configuration de point de terminaison dans chaque activité générée.  
  
## Voir aussi  
 [Services de workflow](../../../../docs/framework/wcf/feature-details/workflow-services.md)   
 [Procédure : créer un service de workflow qui appelle un autre service de workflow](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-that-calls-another-workflow-service.md)   
 [Appel d'un service WCF à partir d'un workflow dans un projet Web](http://go.microsoft.com/fwlink/?LinkId=207725)