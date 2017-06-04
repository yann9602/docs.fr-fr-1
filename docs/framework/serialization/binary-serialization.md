---
title: "S&#233;rialisation binaire | Microsoft Docs"
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
  - "sérialisation binaire, à propos de la sérialisation"
  - "désérialisation"
  - "sérialisation, à propos de la sérialisation"
ms.assetid: 2b1ea3be-1152-4032-b2b3-07794054c405
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# S&#233;rialisation binaire
La sérialisation peut être définie comme le processus de stockage de l'état d'un objet sur un support de stockage.Pendant ce processus, les champs publics et privés de l'objet et le nom de la classe, y compris l'assembly contenant la classe, sont convertis en un flux de données d'octets, écrit ensuite dans un flux de données.Lorsque l'objet est désérialisé par la suite, un clone exact de l'objet d'origine est créé.  
  
 Lorsque vous implémentez un mécanisme de sérialisation dans un environnement orienté objet, vous devez faire plusieurs compromis entre facilité d'utilisation et souplesse.Le processus peut être automatisé en grande partie, à condition que vous puissiez suffisamment le contrôler.Par exemple, dans certaines situations, la sérialisation binaire simple n'est pas suffisante ou une raison particulière peut exiger la définition des champs à sérialiser.Les sections suivantes étudient le mécanisme de sérialisation fiable fourni avec le .NET Framework et mettent en évidence plusieurs fonctionnalités importantes qui vous permettent de personnaliser le processus selon vos besoins.  
  
> [!NOTE]
>  L'état d'un objet encodé UTF\-8 ou UTF\-7 n'est pas préservé si l'objet est sérialisé et désérialisé à l'aide de différentes versions du .NET Framework.  
  
## Dans cette section  
 [Concepts de sérialisation](../../../docs/framework/serialization/serialization-concepts.md)  
 Aborde deux scénarios où la sérialisation est utile : conservation des données en stockage et passage d'objets sur des domaines d'application.  
  
 [Sérialisation de base](../../../docs/framework/serialization/basic-serialization.md)  
 Décrit comment utiliser les formateurs binaires et SOAP pour sérialiser des objets.  
  
 [Sérialisation sélective](../../../docs/framework/serialization/selective-serialization.md)  
 Décrit comment empêcher certains membres d'une classe d'être sérialisés.  
  
 [Sérialisation personnalisée](../../../docs/framework/serialization/custom-serialization.md)  
 Décrit comment personnaliser la sérialisation d'une classe en utilisant l'interface <xref:System.Runtime.Serialization.ISerializable>.  
  
 [Étapes du processus de sérialisation](../../../docs/framework/serialization/steps-in-the-serialization-process.md)  
 Décrit le plan d'action de la sérialisation lorsque la méthode <xref:System.Runtime.Serialization.Formatter.Serialize%2A> est appelée sur un formateur.  
  
 [Sérialisation avec tolérance de version](../../../docs/framework/serialization/version-tolerant-serialization.md)  
 Explique comment créer des types sérialisables qui peuvent être modifiés avec le temps sans que les applications ne lèvent d'exceptions.  
  
 [Indications concernant la sérialisation](../../../docs/framework/serialization/serialization-guidelines.md)  
 Fournit des indications générales pour décider quand sérialiser un objet.  
  
## Référence  
 <xref:System.Runtime.Serialization>  
 Contient des classes qui peuvent être utilisées pour sérialiser et désérialiser des objets.  
  
## Rubriques connexes  
 [Sérialisation XML et SOAP](../../../docs/framework/serialization/xml-and-soap-serialization.md)  
 Décrit le mécanisme de sérialisation XML inclus avec le Common Language Runtime.  
  
 [Sécurité et sérialisation](../../../docs/framework/misc/security-and-serialization.md)  
 Décrit les indications de codage sécurisé à suivre lors de l'écriture du code qui exécute la sérialisation.  
  
 [Remote Objects](http://msdn.microsoft.com/fr-fr/515686e6-0a8d-42f7-8188-73abede57c58)  
 Décrit les différentes méthodes de communication disponibles dans le .NET Framework pour les communications distantes.  
  
 [XML Web Services Created Using ASP.NET and XML Web Service Clients](http://msdn.microsoft.com/fr-fr/1e64af78-d705-4384-b08d-591a45f4379c)  
 Fournit des rubriques qui décrivent et expliquent comment programmer des services Web XML créés à l'aide d'ASP.NET.