---
title: Liaisons Windows Communication Foundation
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF [WCF], bindings
- Windows Communication Foundation [WCF], bindings
- bindings [WCF]
ms.assetid: 83639133-89f7-43f0-b4ef-8d9e57c08d25
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 494869985f14dc9562b8d98a7d68cd9639cca97b
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="windows-communcation-foundation-bindings"></a>Liaisons Windows Communication Foundation
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] effectue la distinction entre la manière dont le logiciel pour une application est écrit et la manière dont il communique avec d'autres logiciels. Les liaisons sont utilisées pour spécifier le transport, l'encodage et les détails de protocole requis pour que les clients et les services puissent communiquer l'un avec l'autre. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] utilise des liaisons pour générer la représentation de câble sous-jacente du point de terminaison ; par conséquent, la plupart des détails de liaison doivent être convenus par les parties qui communiquent. Pour cela, le plus simple est que les clients d’un service utilisent la même liaison que celle utilisée par le point de terminaison du service. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]comment procéder, consultez [à l’aide de liaisons pour configurer les Services Windows Communication Foundation et les Clients](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb).  
  
 Une liaison est composée d’une collection d’éléments de liaison. Chaque élément décrit un aspect de la façon dont le point de terminaison communique avec les clients. Une liaison doit inclure au moins un élément de liaison de transport, au moins un élément de liaison d'encodage de message (que l'élément de liaison de transport peut fournir par défaut) et un nombre quelconque d'autres éléments de liaison de protocole. Le processus qui génère une exécution à partir de cette description permet à chaque élément de liaison de contribuer du code à cette exécution.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] fournit des liaisons qui contiennent des sélections courantes d'éléments de liaison. Celles-ci peuvent être utilisées avec leurs paramètres par défaut, ou vous pouvez modifier ces valeurs par défaut en fonction des besoins des utilisateurs. Ces liaisons fournies par le système ont des propriétés qui permettent de contrôler directement les éléments de liaison et leurs paramètres. Vous pouvez également facilement travailler côte à côte avec plusieurs versions différentes d’une même liaison en attribuant son propre nom à chaque version de la liaison. Pour plus d’informations, consultez [Configuring System-Provided liaisons](../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md).  
  
 Si vous avez besoin d’une collection d’éléments de liaison non fournie par l’une de ces liaisons fournies par le système, vous pouvez créer une liaison personnalisée composée de la collection d’éléments de liaison requis. Ces liaisons personnalisées sont simples à créer et ne requièrent pas de nouvelle classe, mais elles ne fournissent pas de propriétés pour contrôler les éléments de liaison ou leurs paramètres. Vous pouvez accéder aux éléments de liaison et modifier leurs paramètres par le biais de la collection qui les contient. Pour plus d’informations, consultez [liaisons personnalisées](../../../../docs/framework/wcf/extending/custom-bindings.md).  
  
## <a name="in-this-section"></a>Dans cette section  
 [Configuration des liaisons fournies par le système](../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 Décrit comment utiliser et modifier les liaisons que [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] fournit pour prendre en charge des scénarios courants.  
  
 [Utilisation de liaisons pour configurer les Clients et les Services Windows Communication Foundation](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 Décrit comment définir des liaisons [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] pour des services et des clients de manière impérative dans le code et de façon déclarative à l'aide de la configuration.  
  
 [Liaisons personnalisées](../../../../docs/framework/wcf/extending/custom-bindings.md)  
 Décrit ce qu'est un <xref:System.ServiceModel.Channels.CustomBinding> et quand il est utilisé.  
  
## <a name="reference"></a>Référence  
 <xref:System.ServiceModel.Channels.Binding>  
  
 <xref:System.ServiceModel.Channels.BindingElement>  
  
 <xref:System.ServiceModel.Channels.CustomBinding>  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Extension de liaisons](../../../../docs/framework/wcf/extending/extending-bindings.md)
