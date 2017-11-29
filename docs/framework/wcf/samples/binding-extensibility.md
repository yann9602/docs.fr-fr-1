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
ms.openlocfilehash: 61c8ae647012c5f1fffe5cf65c63b64cde62af1b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="binding-extensibility"></a>Extensibilité des liaisons
Cette section contient des exemples qui illustrent la liaison personnalisée dans [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].  
  
## <a name="in-this-section"></a>Dans cette section  
 <xref:System.ServiceModel.NetHttpBinding>  
 Montre comment implémenter une liaison qui empile <xref:System.ServiceModel.Channels.HttpTransportBindingElement> ou le <xref:System.ServiceModel.Channels.HttpsTransportBindingElement> au-dessus du <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>.  
  
 <!--zz <xref:System.ServiceModel.WSStreamedHttpBinding> --> `System.ServiceModel.WSStreamedHttpBinding` 
 Montre comment créer une liaison conçue pour prendre en charge des scénarios de diffusion en continu lorsque le transport HTTP est utilisé.
