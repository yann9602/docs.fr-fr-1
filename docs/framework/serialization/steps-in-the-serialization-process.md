---
title: "&#201;tapes du processus de s&#233;rialisation | Microsoft Docs"
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
  - "sérialisation binaire, étapes"
  - "sérialisation, étapes"
ms.assetid: 4bcbc883-2a91-418f-b968-6c86a25e9737
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# &#201;tapes du processus de s&#233;rialisation
Lorsque la méthode [Serialize](frlrfSystemRuntimeSerializationFormatterClassSerializeTopic) est appelée sur un [formateur](frlrfSystemRuntimeSerializationFormatterClassTopic), la sérialisation de l'objet s'effectue d'après la séquence de règles suivante :  
  
-   Un contrôle est effectué pour déterminer si le formateur possède un sélecteur de substitut.Si tel est le cas, vérifiez si le sélecteur de substitut gère des objets du type donné.Si le sélecteur gère ce type d'objet, **ISerializable.GetObjectData** est appelée sur le sélecteur de substitut.  
  
-   S'il n'y a aucun sélecteur de substitut ou s'il ne gère pas ce type d'objet, un contrôle est effectué pour déterminer si l'objet est marqué avec l'attribut [Serializable](frlrfSystemSerializableAttributeClassTopic).Si l'objet ne l'est pas, une [SerializationException](frlrfSystemRuntimeSerializationSerializationExceptionClassTopic) est levée.  
  
-   Si l'objet est marqué convenablement, vérifiez s'il implémente l'interface [ISerializable](frlrfSystemRuntimeSerializationISerializableClassTopic).Si tel est le cas, [GetObjectData](frlrfSystemRuntimeSerializationISerializableClassGetObjectDataTopic) est appelée sur l'objet.  
  
-   Si l'objet n'implémente pas **ISerializable**, la stratégie de sérialisation par défaut est utilisée. Elle permet de sérialiser tous les champs non marqués comme [NonSerialized](frlrfSystemNonSerializedAttributeClassTopic).  
  
## Voir aussi  
 [Sérialisation binaire](../../../docs/framework/serialization/binary-serialization.md)   
 [Remote Objects](http://msdn.microsoft.com/fr-fr/515686e6-0a8d-42f7-8188-73abede57c58)   
 [Sérialisation XML et SOAP](../../../docs/framework/serialization/xml-and-soap-serialization.md)