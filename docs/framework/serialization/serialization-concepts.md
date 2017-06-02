---
title: "Concepts de s&#233;rialisation | Microsoft Docs"
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
ms.assetid: e1ff4740-20a1-4c76-a8ad-d857db307054
caps.latest.revision: 4
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# Concepts de s&#233;rialisation
Pourquoi utiliser la sérialisation ?L'une des deux raisons majeures est que vous pouvez, d'une part, rendre persistant l'état d'un objet sur un support de stockage afin qu'une copie exacte puisse être recréée ultérieurement. D'autre part, vous pouvez envoyer cet objet par valeur d'un domaine d'application à l'autre.Par exemple, la sérialisation est utilisée pour enregistrer l'état de session dans ASP.NET et copier des objets vers le Presse\-papiers dans les Windows Forms.Elle est également utilisée par la communication à distance pour passer des objets par valeur d'un domaine d'application à un autre.  
  
## Dans cette section  
 [Stockage persistant](../../../docs/framework/serialization/persistent-storage.md)  
 Décrit le besoin de sérialiser un objet.  
  
 [Marshaler par valeur](../../../docs/framework/serialization/marshal-by-value.md)  
 Décrit le processus de marshaling par valeur.  
  
## Rubriques connexes  
 [Sérialisation binaire](../../../docs/framework/serialization/binary-serialization.md)  
 Décrit le mécanisme de sérialisation binaire inclus avec le Common Language Runtime.  
  
 [Remote Objects](http://msdn.microsoft.com/fr-fr/515686e6-0a8d-42f7-8188-73abede57c58)  
 Décrit les différentes méthodes de communication disponibles dans le .NET Framework pour les communications distantes.  
  
 [Sérialisation XML et SOAP](../../../docs/framework/serialization/xml-and-soap-serialization.md)  
 Décrit le mécanisme de sérialisation XML et SOAP inclus avec le Common Language Runtime.