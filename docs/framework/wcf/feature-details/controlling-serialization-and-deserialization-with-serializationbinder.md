---
title: "Contr&#244;le de la s&#233;rialisation et de la d&#233;s&#233;rialisation avec SerializationBinder | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ba8dcecf-acc7-467c-939d-021bbac797d4
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# Contr&#244;le de la s&#233;rialisation et de la d&#233;s&#233;rialisation avec SerializationBinder
Au cours de la sérialisation, un formateur transmet les informations requises pour créer une instance d'un objet de type et de version corrects.  Ces informations comprennent généralement le nom de type et le nom d'assembly complets de l'objet.  Par défaut, la désérialisation utilise ces informations pour créer une instance d'un objet identique.  Certains utilisateurs auront peut\-être besoin de vérifier quelle classe sérialiser et désérialiser, pour les raisons suivantes : la classe d'origine n'existe pas sur l'ordinateur qui effectue la désérialisation, la classe d'origine a été déplacée entre des assemblys ou une version différente de la classe est requise sur le serveur et le client.  [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [Usage of Serialization Binder](../../../../docs/framework/wcf/samples/usage-of-serialization-binder.md).  
  
> [!WARNING]
>  Ces fonctionnalités sont disponibles uniquement lors de l'utilisation de l'objet <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> ou <xref:System.Runtime.Serialization.NetDataContractSerializer>.  
  
## Utilisation de SerializationBinder  
 <xref:System.Runtime.Serialization.SerializationBinder> est une classe abstraite utilisée pour contrôler les types réels utilisés lors de la sérialisation et de la désérialisation.  Pour contrôler les types utilisés pendant la sérialisation et la désérialisation, dérivez une classe à partir de <xref:System.Runtime.Serialization.SerializationBinder> et substituez les méthodes <xref:System.Runtime.Serialization.SerializationBinder.BindToName%2A> System.String, System.String)?qualifyHint=False&autoUpgrade=True et <xref:System.Runtime.Serialization.SerializationBinder.BindToType%2A> System.String)?qualifyHint=False&autoUpgrade=True.  La méthode <xref:System.Runtime.Serialization.SerializationBinder.BindToName%2A> System.String, System.String)?qualifyHint=False&autoUpgrade=True prend un <xref:System.Type> et retourne un assembly et un type de nom.  La méthode <xref:System.Runtime.Serialization.SerializationBinder.BindToType%2A> System.String)?qualifyHint=False&autoUpgrade=True prend un assembly et un type de nom et retourne un <xref:System.Type>.  
  
## Voir aussi  
 [Sérialisation et désérialisation](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md)   
 [Usage of Serialization Binder](../../../../docs/framework/wcf/samples/usage-of-serialization-binder.md)