---
title: "Marshaler par valeur | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "sérialisation binaire, marshaler par valeur"
  - "objets marshalés par valeur"
  - "sérialisation, marshaler par valeur"
ms.assetid: ee91e8f0-92e0-4732-8015-d17dee154be1
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# Marshaler par valeur
Les objets sont uniquement valides dans le domaine d'application au sein duquel ils ont été créés.Toute tentative de passer l'objet comme un paramètre ou de le retourner ensuite entraîne un échec à moins que l'objet dérive de [MarshalByRefObject](frlrfSystemMarshalByRefObjectClassTopic) ou soit marqué comme [Sérialisable](frlrfSystemSerializableAttributeClassTopic).Si l'objet est marqué comme **Sérialisable**, il est automatiquement sérialisé, transporté d'un domaine d'application à l'autre, puis désérialisé pour en générer une copie exacte dans le deuxième domaine d'application.Ce processus est en général connu sous le nom de marshaling par valeur.  
  
 Lorsqu'un objet dérive de **MarshalByRefObject**, une référence d'objet \(et non l'objet lui\-même\) est passée d'un domaine d'application à un autre.Vous pouvez également marquer un objet qui dérive de **MarshalByRefObject** comme **Serializable**.Lorsque cet objet est utilisé avec la communication à distance, le formateur responsable de la sérialisation, préconfiguré avec un sélecteur de substitut \([SurrogateSelector](frlrfSystemRuntimeSerializationSurrogateSelectorClassTopic)\), prend le contrôle du processus de sérialisation et remplace tous les objets dérivés de [MarshalByRefObject](frlrfSystemMarshalByRefObjectClassTopic) par un proxy.Si [SurrogateSelector](frlrfSystemRuntimeSerializationSurrogateSelectorClassTopic) n'est pas défini, l'architecture de sérialisation suit les règles de sérialisation standard décrites dans [Étapes du processus de sérialisation](../../../docs/framework/serialization/steps-in-the-serialization-process.md).  
  
## Voir aussi  
 [Concepts de sérialisation](../../../docs/framework/serialization/serialization-concepts.md)   
 [Remote Objects](http://msdn.microsoft.com/fr-fr/515686e6-0a8d-42f7-8188-73abede57c58)   
 [Sérialisation XML et SOAP](../../../docs/framework/serialization/xml-and-soap-serialization.md)