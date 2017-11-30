---
title: "Extensibilité des liaisons"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cabdd583-ddf5-493e-9dba-c6c31cde8f65
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 251d89af938b4bf104ddb86689b2573856386d75
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="binding-extensibility"></a>Extensibilité des liaisons

Cette section contient des exemples qui illustrent la liaison personnalisée dans [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].  
  
## <a name="in-this-section"></a>Dans cette section  
 <xref:System.ServiceModel.NetHttpBinding>  
 Montre comment implémenter une liaison qui empile <xref:System.ServiceModel.Channels.HttpTransportBindingElement> ou le <xref:System.ServiceModel.Channels.HttpsTransportBindingElement> au-dessus du <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>.  
  
 [WSStreamedHttpBinding](wsstreamedhttpbinding.md)  
 Montre comment créer une liaison conçue pour prendre en charge des scénarios de diffusion en continu lorsque le transport HTTP est utilisé.  
