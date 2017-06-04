---
title: "Migration d&#39;applications .NET&#160;Remoting vers&#160;WCF | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - ", NET Remoting (WCF)"
ms.assetid: 24793465-65ae-4308-8c12-dce4fd12a583
caps.latest.revision: 12
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 12
---
# Migration d&#39;applications .NET&#160;Remoting vers&#160;WCF
**Cette rubrique est spécifique à une technologie héritée qui assure la compatibilité descendante avec des applications existantes et n'est pas recommandée en cas de nouveau développement.Les applications distribuées doivent maintenant être développées à l'aide de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].**  
  
 Il existe deux manière de tirer parti de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] avec les applications .NET Remoting existantes : l'intégration et la migration.L'intégration vous permet d'exécuter .Net Remoting 2.0 et [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] côte à côte et ainsi d'exposer les mêmes objets métier sur ces deux technologies simultanément sans avoir à modifier votre code .Net Remoting 2.0 existant.L'intégration requiert l'utilisation de [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 2.0 ou version ultérieure.Si vous souhaitez tirer parti des fonctionnalités [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] et que la compatibilité des câbles avec les systèmes Remoting 2.0 n'est pas nécessaire, vous pouvez migrer l'ensemble de votre service vers [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].La migration de .NET Remoting 2.0 vers [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] requiert la modification de l'interface de l'objet distant et de ses paramètres de configuration.Ces deux rubriques sont traitées dans [De Remoting vers Windows Communication Foundation](http://go.microsoft.com/fwlink/?LinkId=74403) \(page pouvant être en anglais\).  
  
## Voir aussi  
 [Vue d'ensemble conceptuelle](../../../../docs/framework/wcf/conceptual-overview.md)