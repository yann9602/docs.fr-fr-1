---
title: "Migration d'applications .NET Remoting vers WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: ',NET remoting [WCF]'
ms.assetid: 24793465-65ae-4308-8c12-dce4fd12a583
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 240901f4fa04a2468d5964821680506ea117bf7f
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="migrating-net-remoting-applications-to-wcf"></a>Migration d'applications .NET Remoting vers WCF
**Cette rubrique est spécifique à une technologie héritée qui assure la compatibilité descendante avec des applications existantes et n'est pas recommandée en cas de nouveau développement. Les applications distribuées doivent maintenant être développées à l'aide de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].**  
  
 Il existe deux manière de tirer parti de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] avec les applications .NET Remoting existantes : l'intégration et la migration. L'intégration vous permet d'exécuter .Net Remoting 2.0 et [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] côte à côte et ainsi d'exposer les mêmes objets métier sur ces deux technologies simultanément sans avoir à modifier votre code .Net Remoting 2.0 existant. L'intégration requiert l'utilisation de [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 2.0 ou version ultérieure. Si vous souhaitez tirer parti des fonctionnalités [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] et que la compatibilité des câbles avec les systèmes Remoting 2.0 n'est pas nécessaire, vous pouvez migrer l'ensemble de votre service vers [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. La migration de .NET Remoting 2.0 vers [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] requiert la modification de l'interface de l'objet distant et de ses paramètres de configuration. Deux de ces rubriques sont abordés dans [à partir de la communication à distance de Windows Communication Foundation](http://go.microsoft.com/fwlink/?LinkId=74403).  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble conceptuelle](../../../../docs/framework/wcf/conceptual-overview.md)
