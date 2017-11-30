---
title: "Contrôle de la sérialisation et de la désérialisation avec SerializationBinder"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ba8dcecf-acc7-467c-939d-021bbac797d4
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1c3180d62824f94e27e02c80e09fdf32252f0a23
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="controlling-serialization-and-deserialization-with-serializationbinder"></a>Contrôle de la sérialisation et de la désérialisation avec SerializationBinder
Au cours de la sérialisation, un formateur transmet les informations requises pour créer une instance d'un objet de type et de version corrects. Ces informations comprennent généralement le nom de type et le nom d'assembly complets de l'objet. Par défaut, la désérialisation utilise ces informations pour créer une instance d'un objet identique. Certains utilisateurs auront peut-être besoin de vérifier quelle classe sérialiser et désérialiser, pour les raisons suivantes : la classe d’origine n’existe pas sur l’ordinateur qui effectue la désérialisation, la classe d’origine a été déplacée entre des assemblys ou une version différente de la classe est requise sur le serveur et le client. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][L’utilisation de Binder de sérialisation](../../../../docs/framework/wcf/samples/usage-of-serialization-binder.md).  
  
> [!WARNING]
>  Ces fonctionnalités sont disponibles uniquement lors de l'utilisation de l'objet <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> ou <xref:System.Runtime.Serialization.NetDataContractSerializer>.  
  
## <a name="using-serializationbinder"></a>Utilisation de SerializationBinder  
 <xref:System.Runtime.Serialization.SerializationBinder> est une classe abstraite utilisée pour contrôler les types réels utilisés lors de la sérialisation et de la désérialisation. Pour contrôler les types utilisés pendant la sérialisation et la désérialisation, dérivez une classe de <xref:System.Runtime.Serialization.SerializationBinder> et remplacez le <xref:System.Runtime.Serialization.SerializationBinder.BindToName%2A> System.String, System.String)?qualifyHint=False & mise à niveau automatique = True et <xref:System.Runtime.Serialization.SerializationBinder.BindToType%2A> System.String) ? qualifyHint = False & mise à niveau automatique = True les méthodes. Le <xref:System.Runtime.Serialization.SerializationBinder.BindToName%2A> System.String, System.String)?qualifyHint=False & mise à niveau automatique = True méthode prend un <xref:System.Type> et retourne un nom de type et l’assembly. Le <xref:System.Runtime.Serialization.SerializationBinder.BindToType%2A> System.String)?qualifyHint=False & mise à niveau automatique = True méthode prend un assembly et nom de type et retourne un <xref:System.Type>.  
  
## <a name="see-also"></a>Voir aussi  
 [Sérialisation et désérialisation](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md)  
 [Utilisation de Binder de sérialisation](../../../../docs/framework/wcf/samples/usage-of-serialization-binder.md)
