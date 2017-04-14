---
title: "S&#233;rialisation | Microsoft Docs"
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
  - "sérialisation binaire"
  - "objets, sérialisation"
  - "sérialisation"
  - "sérialiser des objets"
  - "sérialisation XML, définie"
ms.assetid: 4d1111c0-9447-4231-a997-96a2b74b3453
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# S&#233;rialisation
La sérialisation correspond au processus de conversion de l'état d'un objet en un formulaire persistant ou transportable.Le complément de la sérialisation est la désérialisation, qui convertit un flux de données en un objet.Ces deux processus permettent de stocker et de transférer facilement des données.  
  
 Le .NET Framework comprend deux technologies de sérialisation :  
  
-   La sérialisation binaire préserve le respect des types, qui permet de conserver l'état d'un objet entre plusieurs appels d'une application.Par exemple, vous pouvez partager un objet entre plusieurs applications en le sérialisant dans le Presse\-papiers.Vous pouvez sérialiser un objet vers un flux, un disque, la mémoire, le réseau, et ainsi de suite.La communication à distance utilise la sérialisation pour passer des objets « par valeur » d'un ordinateur ou d'un domaine d'application à un autre.  
  
-   La sérialisation XML sérialise uniquement des propriétés et des champs publics mais ne conserve pas le respect des types.Ceci est utile lorsque vous souhaitez fournir ou consommer des données sans restreindre l'application qui les utilise.XML étant une norme ouverte, elle constitue une option intéressante pour partager des données via le Web.Le protocole SOAP est également une norme ouverte et représente, par conséquent, une option avantageuse.  
  
## Dans cette section  
 [Rubriques Comment : ... pour la sérialisation](../../../docs/framework/serialization/serialization-how-to-topics.md)  
 Répertorie les liens vers les rubriques « Comment » contenues dans cette section.  
  
 [Sérialisation binaire](../../../docs/framework/serialization/binary-serialization.md)  
 Décrit le mécanisme de sérialisation binaire inclus avec le Common Language Runtime.  
  
 [Sérialisation XML et SOAP](../../../docs/framework/serialization/xml-and-soap-serialization.md)  
 Décrit le mécanisme de sérialisation XML et SOAP inclus avec le Common Language Runtime.  
  
 [Outils de sérialisation](../../../docs/framework/serialization/serialization-tools.md)  
 Ces outils vous aident à développer le code de sérialisation.  
  
 [Exemples de sérialisation](../../../docs/framework/serialization/serialization-samples.md)  
 Les exemples montrent comment procéder à la sérialisation.  
  
## Référence  
 <xref:System.Runtime.Serialization>  
 Contient des classes qui peuvent être utilisées pour sérialiser et désérialiser des objets.  
  
 <xref:System.Xml.Serialization>  
 Contient des classes qui peuvent être utilisées pour sérialiser des objets en documents ou en flux de données au format XML.  
  
## Rubriques connexes  
 [Remote Objects](http://msdn.microsoft.com/fr-fr/515686e6-0a8d-42f7-8188-73abede57c58)  
 Décrit les différentes méthodes de communication disponibles dans le .NET Framework pour les communications distantes.  
  
 [Advanced Development Technologies](http://msdn.microsoft.com/fr-fr/c4a7e341-f0c6-4df4-a74f-223387ac6e4e)  
 Fournit des liens vers d'autres informations sur les tâches et les techniques de développement sophistiquées dans le .NET Framework.  
  
 [XML Web Services Created Using ASP.NET and XML Web Service Clients](http://msdn.microsoft.com/fr-fr/1e64af78-d705-4384-b08d-591a45f4379c)  
 Fournit des rubriques qui décrivent et expliquent comment programmer des services Web XML créés à l'aide d'ASP.NET.